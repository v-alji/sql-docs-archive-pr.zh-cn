---
title: .NET Framework 更新后升级 SQLCLR 程序集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45d60db413e11828f26bd03e1c8f350645838d12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587615"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a><span data-ttu-id="58af8-102">.NET Framework 更新后升级 SQLCLR 程序集</span><span class="sxs-lookup"><span data-stu-id="58af8-102">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="58af8-103">(DQS) 是引用 Microsoft .NET Framework 4 程序集的 SQL 公共语言运行时 (SQLCR) 例程的集合。</span><span class="sxs-lookup"><span data-stu-id="58af8-103">(DQS) is a collection of SQL Common Language Runtime (SQLCR) routines that reference Microsoft .NET Framework 4 assemblies.</span></span> <span data-ttu-id="58af8-104">如果在计算机上安装的任何 .NET Framework 更新影响任何此类引用的 .NET Framework 程序集，则将导致全局程序集缓存 (GAC) 中的程序集的模块版本 ID (MVID) 发生更改。</span><span class="sxs-lookup"><span data-stu-id="58af8-104">When you install any .NET Framework updates on your computer that affect any such referenced .NET Framework assembly, it leads to a change in the Module Version ID (MVID) of the assembly in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="58af8-105">这样会导致 GAC 中的引用程序集与 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的程序集之间的 MVID 不匹配。</span><span class="sxs-lookup"><span data-stu-id="58af8-105">This causes a mismatch between the MVIDs of the referenced assembly in GAC and the assembly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="58af8-106">如果 .NET Framework 更新要求您重新启动 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机，则受到影响的 SQLCLR 程序集将自动升级，以便修复在重新启动 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机时产生的 MVID 不匹配问题。</span><span class="sxs-lookup"><span data-stu-id="58af8-106">If the .NET Framework update requires you to restart the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, the affected SQLCLR assemblies are upgraded automatically to fix the MVID mismatch issue on restarting the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span> <span data-ttu-id="58af8-107">但是，对于不要求您重新启动 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机的 .NET Framework 更新，由于在您尝试使用 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 连接到 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]时程序集的 MVID 中的不匹配，将出现错误：</span><span class="sxs-lookup"><span data-stu-id="58af8-107">However, for .NET Framework updates that do not require you to restart your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, an error occurs due to the mismatch in the MVIDs of the assemblies when you try to connect to a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] using a [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:</span></span>  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 <span data-ttu-id="58af8-108">若要修复此问题，必须升级 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中受影响的 SQLCLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="58af8-108">To fix this issue, the affected SQLCLR assemblies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be upgraded.</span></span> <span data-ttu-id="58af8-109">为此，您可以使用 **upgradedlls** 命令行参数运行 DQSInstaller.exe 文件，以跳过重新创建 DQS 数据库，而只升级受影响的程序集。</span><span class="sxs-lookup"><span data-stu-id="58af8-109">You can do so by running the DQSInstaller.exe file with the **upgradedlls** command line parameter to skip recreating the DQS databases, and just upgrade the affected assemblies.</span></span> <span data-ttu-id="58af8-110">这样可确保保留您的知识库、数据质量项目以及 DQS 中的任何其他数据。</span><span class="sxs-lookup"><span data-stu-id="58af8-110">This ensures that your knowledge bases, data quality projects, and any other data in DQS are preserved.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="58af8-111">必备条件</span><span class="sxs-lookup"><span data-stu-id="58af8-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="58af8-112">您必须作为 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机上 Administrators 组的成员登录。</span><span class="sxs-lookup"><span data-stu-id="58af8-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="58af8-113">您的 Windows 用户帐户必须是安装了 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的 SQL Server 实例中 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="58af8-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-sqlclr-assemblies"></a><span data-ttu-id="58af8-114">升级 SQLCLR 程序集</span><span class="sxs-lookup"><span data-stu-id="58af8-114">To upgrade SQLCLR Assemblies</span></span>  
  
1.  <span data-ttu-id="58af8-115">启动命令提示符。</span><span class="sxs-lookup"><span data-stu-id="58af8-115">Start Command Prompt.</span></span>  
  
2.  <span data-ttu-id="58af8-116">在命令提示符下，将目录更改为 DQSInstaller.exe 出现的位置。</span><span class="sxs-lookup"><span data-stu-id="58af8-116">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="58af8-117">如果您安装了 SQL Server 的默认实例，则 DQSInstaller.exe 文件将出现在 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn 下：</span><span class="sxs-lookup"><span data-stu-id="58af8-117">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  <span data-ttu-id="58af8-118">在命令提示符下，键入以下命令，再按 Enter：</span><span class="sxs-lookup"><span data-stu-id="58af8-118">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  <span data-ttu-id="58af8-119">剩下的步骤与 [运行 DQSInstaller.exe 以便完成数据质量服务器安装](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) 中 [从“开始”屏幕、“开始”菜单或 Windows 资源管理器运行 DQSInstaller.exe](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)部分中的步骤 2-6 相同。</span><span class="sxs-lookup"><span data-stu-id="58af8-119">Rest of the steps are same as steps 2-6 in the [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) section in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58af8-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58af8-120">See Also</span></span>  
 <span data-ttu-id="58af8-121">[安装 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="58af8-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="58af8-122">在安装 SQL Server 更新后升级 DQS 数据库架构</span><span class="sxs-lookup"><span data-stu-id="58af8-122">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>](upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
