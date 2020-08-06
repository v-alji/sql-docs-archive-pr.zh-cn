---
title: 在 Windows PowerShell 中加载 SMO 程序集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9886d80c305dba251e6e3ab22ddb4dfb39783748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682898"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a><span data-ttu-id="68459-102">在 Windows PowerShell 中加载 SMO 程序集</span><span class="sxs-lookup"><span data-stu-id="68459-102">Load the SMO Assemblies in Windows PowerShell</span></span>
  <span data-ttu-id="68459-103">本主题介绍如何在不使用 SQL Server PowerShell 提供程序的 Windows PowerShell 脚本中加载 SQL Server 管理对象 (SMO) 程序集。</span><span class="sxs-lookup"><span data-stu-id="68459-103">This topic describes how to load the SQL Server Management Object (SMO) assemblies in Windows PowerShell scripts that do not use the SQL Server PowerShell provider.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="68459-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="68459-104">Before You Begin</span></span>  
 <span data-ttu-id="68459-105">加载 SMO 程序集的首选机制是加载 `sqlps` 模块。</span><span class="sxs-lookup"><span data-stu-id="68459-105">The preferred mechanism for loading the SMO assemblies is to load the `sqlps` module.</span></span> <span data-ttu-id="68459-106">该模块中包括的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序将自动加载 SMO 程序集，还会实现可扩展 PowerShell 脚本中的 SMO 对象的有用性的功能。</span><span class="sxs-lookup"><span data-stu-id="68459-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider included in the module automatically loads the SMO assemblies, and also implements features that extend the usefulness of the SMO objects in PowerShell scripts.</span></span>  
  
 <span data-ttu-id="68459-107">有两种情况可能需要您直接加载 SMO 程序集：</span><span class="sxs-lookup"><span data-stu-id="68459-107">There are two cases where you may need to load the SMO assemblies directly:</span></span>  
  
-   <span data-ttu-id="68459-108">脚本在从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理单元引用该提供程序或 cmdlet 的第一个命令之前引用了一个 SMO 对象。</span><span class="sxs-lookup"><span data-stu-id="68459-108">If your script references a SMO object before the first command that references the provider or cmdlets from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins.</span></span>  
  
-   <span data-ttu-id="68459-109">您需要从不使用该提供程序或 cmdlet 的另一种语言（例如 C# 或 Visual Basic）移植 SMO 代码。</span><span class="sxs-lookup"><span data-stu-id="68459-109">You want to port SMO code from another language, such as C# or Visual Basic, which does not use the provider or cmdlets.</span></span>  
  
## <a name="example-loading-the-sql-server-management-objects"></a><span data-ttu-id="68459-110">示例：加载 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="68459-110">Example: Loading the SQL Server Management Objects</span></span>  
 <span data-ttu-id="68459-111">下面的代码加载 SMO 程序集：</span><span class="sxs-lookup"><span data-stu-id="68459-111">The following code loads the SMO assemblies:</span></span>  
  
```powershell
# Loads the SQL Server Management Objects (SMO)  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
Update-FormatData -PrependPath SQLProvider.Format.ps1xml
Pop-Location  
```  
  
## <a name="see-also"></a><span data-ttu-id="68459-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68459-112">See Also</span></span>  
 [<span data-ttu-id="68459-113">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="68459-113">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
