---
title: 使用 Windows PowerShell 的 PowerPivot 配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b42da3e676a291bb021c02ee52e9a810207397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589898"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a><span data-ttu-id="8fe5d-102">使用 Windows PowerShell 配置 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="8fe5d-102">PowerPivot Configuration using Windows PowerShell</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="8fe5d-103">提供 Windows PowerShell cmdlet，您可以使用这些 cmdlet 配置安装的 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-103">includes Windows PowerShell cmdlets that you can use to configure an installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span> <span data-ttu-id="8fe5d-104">使用 PowerShell 完全配置已安装的软件需要使用 SharePoint cmdlet 和 PowerPivot for SharePoint cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-104">To fully configure an installation with PowerShell requires the use of both SharePoint cmdlets and PowerPivot for SharePoint cmdlets.</span></span> <span data-ttu-id="8fe5d-105">大多数配置可使用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工具之一来完成。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-105">A majority of configuration can be completed using one of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] tools.</span></span> <span data-ttu-id="8fe5d-106">有关这些工具的详细信息，请参阅[PowerPivot 配置工具](power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-106">For more information on the tools, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8fe5d-107">对于 SharePoint 2010 场，必须首先安装 SharePoint 2010 SP1，然后您才能配置 PowerPivot for SharePoint 或使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 数据库服务器的 SharePoint 场。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-107">For a SharePoint 2010 farm, SharePoint 2010 SP1 must be installed before you can configure either PowerPivot for SharePoint, or a SharePoint farm that uses a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database server.</span></span> <span data-ttu-id="8fe5d-108">如果您尚未安装 Service Pack，则应首先安装 Service Pack，然后再开始配置服务器。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-108">If you have not yet installed the service pack, install it before you begin configuring the server.</span></span>  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a><span data-ttu-id="8fe5d-109">使用 PowerShell 配置 PowerPivot for SharePoint 的好处</span><span class="sxs-lookup"><span data-stu-id="8fe5d-109">Benefits of Configuring PowerPivot for SharePoint Using PowerShell</span></span>  
 <span data-ttu-id="8fe5d-110">可以生成 Windows PowerShell 脚本 (.ps1) 文件来自动执行配置任务。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-110">You can build Windows PowerShell script (.ps1) files to automate configuration tasks.</span></span> <span data-ttu-id="8fe5d-111">如果您需要可以在任何服务器上运行的脚本化的安装和配置步骤，则推荐使用上述做法。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-111">This approach is recommended if you require scripted installation and configuration steps that you can run on any server.</span></span> <span data-ttu-id="8fe5d-112">您可能需要这样一个脚本，将其纳入出现硬件故障时用来重新构建服务器的灾难恢复计划。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-112">You might require such a script as part of a disaster recovery plan for rebuilding a server in the event of a hardware failure.</span></span>  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="8fe5d-113">查看服务器上 PowerPivot Cmdlet 的列表</span><span class="sxs-lookup"><span data-stu-id="8fe5d-113">View a list of the PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="8fe5d-114">若要查看 cmdlet 的内容和示例 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ，请参阅[PowerShell 参考了解 PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-114">To see content and examples of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cmdlets, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
 <span data-ttu-id="8fe5d-115">使用 PowerShell 查看 PowerPivot cmdlet 列表：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-115">To use PowerShell to view a list of the PowerPivot cmdlets:</span></span>  
  
1.  <span data-ttu-id="8fe5d-116">使用 **“以管理员身份运行”** 选项打开 SharePoint Management Shell。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-116">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="8fe5d-117">输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-117">Enter the following command:</span></span>  
  
    ```powershell
    Get-Help *powerpivot*  
    ```  
  
     <span data-ttu-id="8fe5d-118">您应该看到 cmdlet 名称中包含 PowerPivot 的 cmdlet 的列表。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-118">You should see a list of cmdlets that include PowerPivot in the cmdlet name.</span></span> <span data-ttu-id="8fe5d-119">例如 `Get-PowerPivotServiceApplication`。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-119">For example `Get-PowerPivotServiceApplication`.</span></span> <span data-ttu-id="8fe5d-120">可用的 cmdlet 数量取决于您使用的 Analysis Services 版本。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-120">The number of cmdlets available depends on the version of Analysis Services you are using.</span></span>  
  
    -   <span data-ttu-id="8fe5d-121">10 个 cmdlet 以及在 SharePoint 模式下配置的 SQL Server 2012 SP1 Analysis Services 服务器，以及 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-121">10 cmdlets with SQL Server 2012 SP1 Analysis Services server configured in SharePoint mode, and SharePoint 2013.</span></span> <span data-ttu-id="8fe5d-122">2012 SP1 版本利用了一个新的体系结构，允许 Analysis Server 在 SharePoint 场之外运行，所需的管理 Windows PowerShell cmdlet 更少。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-122">The 2012 SP1 version utilizes a new architecture that allows the Analysis Server to run outside the SharePoint farm and requires fewer management Windows PowerShell cmdlets.</span></span>  
  
    -   <span data-ttu-id="8fe5d-123">17 个 cmdlet 以及在 SharePoint 模式下配置的 SQL Server 2012 Analysis Services 服务器，以及 SharePoint 2010。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-123">17 cmdlets with SQL Server 2012 Analysis Services server configured in SharePoint mode, and SharePoint 2010.</span></span>  
  
     <span data-ttu-id="8fe5d-124">如果列表中未返回任何命令或者您看到类似于 "" 的错误消息 `get-help could not find *powerpivot* in a help file in this session.` ，请参阅本主题的下一节，了解有关如何在服务器上启用 PowerPivot cmdlet 的说明。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-124">If no commands are returned in the list or you see an error message similar to "`get-help could not find *powerpivot* in a help file in this session.`", see the next section in this topic for instructions on how to enable the PowerPivot cmdlets on the server.</span></span>  
  
     <span data-ttu-id="8fe5d-125">所有 cmdlet 都有联机帮助。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-125">All cmdlets have online help.</span></span> <span data-ttu-id="8fe5d-126">下面的示例显示如何查看 `New-PowerPivotServiceApplication` cmdlet 的联机帮助：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-126">The following example shows how to view the online help for the `New-PowerPivotServiceApplication` cmdlet:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Full  
    ```  
  
     <span data-ttu-id="8fe5d-127">或者，若仅查看示例，使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-127">Alternatively, to view just the examples, use the following syntax:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="8fe5d-128">在服务器上启用 PowerPivot Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8fe5d-128">Enable PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="8fe5d-129">在安装 PowerPivot for SharePoint 并部署场解决方案后，即可使用 PowerPivot cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-129">PowerPivot cmdlets are available after you install PowerPivot for SharePoint and deploy the farm solution.</span></span> <span data-ttu-id="8fe5d-130">在您运行 PowerPivot 配置工具时部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-130">The solutions are deployed when you ran the PowerPivot Configuration tool.</span></span> <span data-ttu-id="8fe5d-131">请按照以下步骤启用 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-131">Follow these steps to enable the use of cmdlets:</span></span>  
  
1.  <span data-ttu-id="8fe5d-132">使用 **“以管理员身份运行”** 选项打开 SharePoint Management Shell。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-132">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="8fe5d-133">运行第一个 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-133">Run the first cmdlet:</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="8fe5d-134">该 cmdlet 返回解决方案的名称、其解决方案 ID 和 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-134">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="8fe5d-135">在下一步骤中，您将部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-135">In the next step, you deploy the solution.</span></span>  
  
3.  <span data-ttu-id="8fe5d-136">运行第二个 cmdlet 以便部署解决方案：</span><span class="sxs-lookup"><span data-stu-id="8fe5d-136">Run the second cmdlet to deploy the solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  <span data-ttu-id="8fe5d-137">关闭“服务” 窗口。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-137">Close the window.</span></span> <span data-ttu-id="8fe5d-138">使用 **“以管理员身份运行”** 选项重新打开该窗口。</span><span class="sxs-lookup"><span data-stu-id="8fe5d-138">Reopen it, again using the **Run as Administrator** option.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="8fe5d-139">相关内容</span><span class="sxs-lookup"><span data-stu-id="8fe5d-139">Related Content</span></span>  
 [<span data-ttu-id="8fe5d-140">在管理中心中管理和配置 PowerPivot 服务器</span><span class="sxs-lookup"><span data-stu-id="8fe5d-140">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="8fe5d-141">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="8fe5d-141">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="8fe5d-142">针对 PowerPivot for SharePoint 的 PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="8fe5d-142">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
