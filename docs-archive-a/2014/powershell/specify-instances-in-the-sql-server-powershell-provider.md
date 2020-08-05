---
title: 在 SQL Server PowerShell 提供程序中指定实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc04bacc1ff36b0b5ce526a377fcdb750ad134a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581336"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a><span data-ttu-id="302dd-102">在 SQL Server PowerShell 提供程序中指定实例</span><span class="sxs-lookup"><span data-stu-id="302dd-102">Specify Instances in the SQL Server PowerShell Provider</span></span>
  <span data-ttu-id="302dd-103">为 SQL Server PowerShell 提供程序指定的路径必须标识它运行时所在的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例和计算机。</span><span class="sxs-lookup"><span data-stu-id="302dd-103">The paths specified for the SQL Server PowerShell provider must identify the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] and the computer it is running on.</span></span> <span data-ttu-id="302dd-104">用于指定计算机和实例的语法必须同时符合 SQL Server 标识符和 Windows PowerShell 路径的规则。</span><span class="sxs-lookup"><span data-stu-id="302dd-104">The syntax for specifying the computer and the instance must comply with both the rules for SQL Server identifiers and Windows PowerShell paths.</span></span>  
  
1.  <span data-ttu-id="302dd-105">**开始之前：**  [限制和局限](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="302dd-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="302dd-106">**指定实例：**  [示例](#Examples)</span><span class="sxs-lookup"><span data-stu-id="302dd-106">**To specify an instance:**  [Examples](#Examples)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="302dd-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="302dd-107">Before You Begin</span></span>  
 <span data-ttu-id="302dd-108">SQL Server 提供程序中的 SQLSERVER:\SQL 后的第一个节点是运行 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例的计算机的名称；例如：</span><span class="sxs-lookup"><span data-stu-id="302dd-108">The first node following the SQLSERVER:\SQL in a SQL Server provider path is the name of the computer that is running the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 <span data-ttu-id="302dd-109">如果在运行 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例的同一计算机上运行 Windows PowerShell，则可使用 localhost 或 (local)，而不使用计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="302dd-109">If you are running Windows PowerShell on the same computer as the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], you can use either localhost or (local) instead of the name of the computer.</span></span> <span data-ttu-id="302dd-110">使用 localhost 或 (local) 的脚本可在任何计算机上运行，而无需进行更改来反映不同计算机名称。</span><span class="sxs-lookup"><span data-stu-id="302dd-110">Scripts that use localhost or (local) can be run on any computer without having to be changed to reflect the different computer names.</span></span>  
  
 <span data-ttu-id="302dd-111">可以在同一台计算机上运行 [!INCLUDE[ssDE](../includes/ssde-md.md)] 可执行程序的多个实例。</span><span class="sxs-lookup"><span data-stu-id="302dd-111">You can run multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] executable program on the same computer.</span></span> <span data-ttu-id="302dd-112">SQL Server 提供程序路径中的计算机名称后的节点用于标识实例；例如：</span><span class="sxs-lookup"><span data-stu-id="302dd-112">The node following the computer name in a SQL Server provider path identifies the instance; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 <span data-ttu-id="302dd-113">每台计算机都有一个默认的 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="302dd-113">Each computer can have one default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="302dd-114">在安装默认实例时，无需为它指定名称。</span><span class="sxs-lookup"><span data-stu-id="302dd-114">You do not specify a name for the default instance when you install it.</span></span> <span data-ttu-id="302dd-115">如果在连接字符串中仅指定了计算机名称，则会连接到该计算机上的默认实例。</span><span class="sxs-lookup"><span data-stu-id="302dd-115">If you specify only a computer name in a connection string, you are connected to the default instance on that computer.</span></span> <span data-ttu-id="302dd-116">该计算机上的所有其他实例都必须是命名实例。</span><span class="sxs-lookup"><span data-stu-id="302dd-116">All other instances on the computer must be named instances.</span></span> <span data-ttu-id="302dd-117">如果在安装过程中指定了实例名称，则必须在连接字符串中同时指定计算机名称和实例名称。</span><span class="sxs-lookup"><span data-stu-id="302dd-117">You specify the instance name during setup, and connection strings must specify both the computer name and the instance name.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="302dd-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="302dd-118">Limitations and Restrictions</span></span>  
 <span data-ttu-id="302dd-119">您不能使用句点 (.) 在 PowerShell 脚本中指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="302dd-119">You cannot use a period (.) to specify the local computer in PowerShell scripts.</span></span> <span data-ttu-id="302dd-120">由于 PowerShell 会将句点解释为一个命令，因此不支持句点。</span><span class="sxs-lookup"><span data-stu-id="302dd-120">The period is not supported because the period is interpreted as a command by PowerShell.</span></span>  
  
 <span data-ttu-id="302dd-121">Windows PowerShell 通常会将 (local) 中的括号字符作为命令处理。</span><span class="sxs-lookup"><span data-stu-id="302dd-121">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="302dd-122">您必须对这些字符进行编码或转义才能在路径中使用它们，或用双引号将路径引起来。</span><span class="sxs-lookup"><span data-stu-id="302dd-122">You must either encode them or escape them for use in a path, or enclose the path in double-quotation marks.</span></span> <span data-ttu-id="302dd-123">有关详细信息，请参阅“SQL Server 标识符的编码和解码”。</span><span class="sxs-lookup"><span data-stu-id="302dd-123">For more information, see Encode and Decode SQL Server Identifiers.</span></span>  
  
 <span data-ttu-id="302dd-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序要求您始终指定实例名称。</span><span class="sxs-lookup"><span data-stu-id="302dd-124">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider requires that you always specify an instance name.</span></span> <span data-ttu-id="302dd-125">对于默认实例，必须将实例名称指定为 DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="302dd-125">For default instances, you must specify an instance name of DEFAULT.</span></span>  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a> <span data-ttu-id="302dd-126">示例：计算机名称和实例名称</span><span class="sxs-lookup"><span data-stu-id="302dd-126">Examples; Computer and Instance Names</span></span>  
 <span data-ttu-id="302dd-127">此示例使用 localhost 和 DEFAULT 来指定本地计算机上的默认实例：</span><span class="sxs-lookup"><span data-stu-id="302dd-127">This example uses localhost and DEFAULT to specify the default instance on the local computer:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 <span data-ttu-id="302dd-128">Windows PowerShell 通常会将 (local) 中的括号字符作为命令处理。</span><span class="sxs-lookup"><span data-stu-id="302dd-128">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="302dd-129">您必须：</span><span class="sxs-lookup"><span data-stu-id="302dd-129">You must either:</span></span>  
  
-   <span data-ttu-id="302dd-130">将路径字符串用引号引起来：</span><span class="sxs-lookup"><span data-stu-id="302dd-130">Enclose the path string in quotes:</span></span>  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   <span data-ttu-id="302dd-131">使用反引号字符 (\`) 对括号进行转义：</span><span class="sxs-lookup"><span data-stu-id="302dd-131">Escape the parenthesis using the back tick character (\`):</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   <span data-ttu-id="302dd-132">使用十六进制表示形式对括号进行编码：</span><span class="sxs-lookup"><span data-stu-id="302dd-132">Encode the parenthesis using their hexadecimal representation:</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="302dd-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="302dd-133">See Also</span></span>  
 <span data-ttu-id="302dd-134">[SQL Server PowerShell 中的标识符](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="302dd-134">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="302dd-135">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="302dd-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="302dd-136">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="302dd-136">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
