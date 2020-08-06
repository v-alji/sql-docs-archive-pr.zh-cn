---
title: 在数据库引擎 PowerShell 中管理身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 018a2698a43148af971622f54c8418bf23c2c781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687948"
---
# <a name="manage-authentication-in-database-engine-powershell"></a><span data-ttu-id="3ea44-102">在数据库引擎 PowerShell 中管理身份验证</span><span class="sxs-lookup"><span data-stu-id="3ea44-102">Manage Authentication in Database Engine PowerShell</span></span>
  <span data-ttu-id="3ea44-103">默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 组件在连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例时使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="3ea44-103">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components use Windows Authentication when connecting to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="3ea44-104">您可以通过定义 PowerShell 虚拟驱动器，或者通过为 `-Username` 指定 `-Password` 和 `Invoke-Sqlcmd` 参数，使用 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="3ea44-104">You can use SQL Server Authentication by either defining a PowerShell virtual drive, or by specifying the `-Username` and `-Password` parameters for `Invoke-Sqlcmd`.</span></span>  
  
1.  <span data-ttu-id="3ea44-105">**开始之前：** [权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="3ea44-105">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="3ea44-106">**若要设置身份验证，请使用：**  [虚拟驱动器](#SQLAuthVirtDrv)[Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span><span class="sxs-lookup"><span data-stu-id="3ea44-106">**To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3ea44-107">权限</span><span class="sxs-lookup"><span data-stu-id="3ea44-107">Permissions</span></span>  
 <span data-ttu-id="3ea44-108">您可以在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例中执行的所有操作都受到授予用于连接到该实例的身份验证凭据的权限的控制。</span><span class="sxs-lookup"><span data-stu-id="3ea44-108">All actions you can perform in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] are controlled by the permissions granted to the authentication credentials used to connect to the instance.</span></span> <span data-ttu-id="3ea44-109">默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 和 cmdlet 将使用其运行所基于的 Windows 帐户来建立与 [!INCLUDE[ssDE](../includes/ssde-md.md)]的 Windows 身份验证连接。</span><span class="sxs-lookup"><span data-stu-id="3ea44-109">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider and cmdlets use the Windows account under which it is running to make a Windows Authentication connection to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="3ea44-110">若要建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接，您必须提供 SQL Server 身份验证登录 ID 和密码。</span><span class="sxs-lookup"><span data-stu-id="3ea44-110">To make a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication connection you must supply a SQL Server Authentication login ID and password.</span></span> <span data-ttu-id="3ea44-111">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序时，必须将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录凭据与虚拟驱动器相关联，然后使用 "更改目录" 命令 (`cd`) 连接到该驱动器。</span><span class="sxs-lookup"><span data-stu-id="3ea44-111">When using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider, you must associate the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login credentials with a virtual drive, and then use the change directory command (`cd`) to connect to that drive.</span></span> <span data-ttu-id="3ea44-112">在 Windows PowerShell 中，安全凭据只能与虚拟驱动器关联。</span><span class="sxs-lookup"><span data-stu-id="3ea44-112">In Windows PowerShell, security credentials can only be associated with virtual drives.</span></span>  
  
##  <a name="sql-server-authentication-using-a-virtual-drive"></a><a name="SQLAuthVirtDrv"></a><span data-ttu-id="3ea44-113">使用虚拟驱动器进行 SQL Server 身份验证</span><span class="sxs-lookup"><span data-stu-id="3ea44-113">SQL Server Authentication Using a Virtual Drive</span></span>  
 <span data-ttu-id="3ea44-114">**创建与 SQL Server 身份验证登录相关联的虚拟驱动器**</span><span class="sxs-lookup"><span data-stu-id="3ea44-114">**To create a virtual drive associated with a SQL Server Authentication login**</span></span>  
  
1.  <span data-ttu-id="3ea44-115">创建一个函数，该函数：</span><span class="sxs-lookup"><span data-stu-id="3ea44-115">Create a function that:</span></span>  
  
    1.  <span data-ttu-id="3ea44-116">具有针对为虚拟驱动器提供的名称、登录 ID 以及要与虚拟驱动器相关联的提供程序路径的参数。</span><span class="sxs-lookup"><span data-stu-id="3ea44-116">Has parameters for the name to give the virtual drive, the login ID, and the provider path to associate with the virtual drive.</span></span>  
  
    2.  <span data-ttu-id="3ea44-117">使用 `read-host` 来提示用户输入密码。</span><span class="sxs-lookup"><span data-stu-id="3ea44-117">Uses `read-host` to prompt the user for the password.</span></span>  
  
    3.  <span data-ttu-id="3ea44-118">使用 `new-object` 来创建凭据对象。</span><span class="sxs-lookup"><span data-stu-id="3ea44-118">Uses `new-object` to create a credentials object.</span></span>  
  
    4.  <span data-ttu-id="3ea44-119">使用 `new-psdrive` 来创建具有提供的凭据的虚拟驱动器。</span><span class="sxs-lookup"><span data-stu-id="3ea44-119">Uses `new-psdrive` to create a virtual drive with the supplied credentials.</span></span>  
  
2.  <span data-ttu-id="3ea44-120">调用函数来创建具有提供的凭据的虚拟驱动器。</span><span class="sxs-lookup"><span data-stu-id="3ea44-120">Invoke the function to create a virtual drive with the supplied credentials.</span></span>  
  
### <a name="example-virtual-drive"></a><span data-ttu-id="3ea44-121">示例（虚拟驱动器）</span><span class="sxs-lookup"><span data-stu-id="3ea44-121">Example (Virtual Drive)</span></span>  
 <span data-ttu-id="3ea44-122">此示例创建名为 **sqldrive** 的函数，您可使用该函数来创建与指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证登录名和实例相关联的虚拟驱动器。</span><span class="sxs-lookup"><span data-stu-id="3ea44-122">This example creates a function named **sqldrive** that you can use to create a virtual drive that is associated with the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login and instance.</span></span>  
  
 <span data-ttu-id="3ea44-123">**sqldrive** 函数提示您输入登录名的密码，并在您键入密码时屏蔽密码。</span><span class="sxs-lookup"><span data-stu-id="3ea44-123">The **sqldrive** function prompts you to enter the password for your login, masking the password as you type it in.</span></span> <span data-ttu-id="3ea44-124">然后，每当你使用更改目录命令 (`cd`) 使用虚拟驱动器名称连接到路径时，所有操作都将通过使用你在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 创建驱动器时提供的身份验证登录凭据来执行。</span><span class="sxs-lookup"><span data-stu-id="3ea44-124">Then, whenever you use the change directory command (`cd`) to connect to a path by using the virtual drive name, all operations are performed by using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login credentials that you supplied when you created the drive.</span></span>  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="sql-server-authentication-using-invoke-sqlcmd"></a><a name="SQLAuthInvSqlCmd"></a><span data-ttu-id="3ea44-125">使用 Invoke 进行 SQL Server 身份验证-Sqlcmd</span><span class="sxs-lookup"><span data-stu-id="3ea44-125">SQL Server Authentication Using Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="3ea44-126">**将 Invoke-Sqlcmd 用于 SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="3ea44-126">**To use Invoke-Sqlcmd with SQL Server Authentication**</span></span>  
  
1.  <span data-ttu-id="3ea44-127">使用 `-Username` 参数可以指定一个登录 ID，以及用于指定关联密码的 `-Password` 参数。</span><span class="sxs-lookup"><span data-stu-id="3ea44-127">Use the `-Username` parameter to specify a login ID, and the `-Password` parameter to specify the associated password.</span></span>  
  
### <a name="example-invoke-sqlcmd"></a><span data-ttu-id="3ea44-128">示例 (Invoke-Sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="3ea44-128">Example (Invoke-Sqlcmd)</span></span>  
 <span data-ttu-id="3ea44-129">此示例使用 read-host cmdlet 来提示用户输入密码，然后使用 SQL Server 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="3ea44-129">This example uses the read-host cmdlet to prompt the user for a password, and then connects using SQL Server Authentication.</span></span>  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ea44-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea44-130">See Also</span></span>  
 <span data-ttu-id="3ea44-131">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="3ea44-131">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 <span data-ttu-id="3ea44-132">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="3ea44-132">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="3ea44-133">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="3ea44-133">Invoke-Sqlcmd cmdlet</span></span>](../database-engine/invoke-sqlcmd-cmdlet.md)  
