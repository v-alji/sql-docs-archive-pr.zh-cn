---
title: 升级顾问概述 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d787f41eba97314986ec77df4cfcff580ae9915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586115"
---
# <a name="upgrade-advisor-overview"></a><span data-ttu-id="bf229-102">升级顾问概述</span><span class="sxs-lookup"><span data-stu-id="bf229-102">Upgrade Advisor Overview</span></span>
  <span data-ttu-id="bf229-103">升级顾问提供了一个中央控制台，可分析 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 组件，以及查看包含分析结果相关信息的报告。</span><span class="sxs-lookup"><span data-stu-id="bf229-103">Upgrade Advisor provides a central console to analyze [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] components, and to view reports that contain information about the results of the analysis.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="bf229-104">升级顾问如何工作</span><span class="sxs-lookup"><span data-stu-id="bf229-104">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="bf229-105">运行升级顾问时，将显示升级顾问起始页。</span><span class="sxs-lookup"><span data-stu-id="bf229-105">When you run Upgrade Advisor, the Upgrade Advisor start page appears.</span></span> <span data-ttu-id="bf229-106">升级顾问起始页是以下程序的启动点：</span><span class="sxs-lookup"><span data-stu-id="bf229-106">The Upgrade Advisor start page is the launching point for the following:</span></span>  
  
-   <span data-ttu-id="bf229-107">升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="bf229-107">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="bf229-108">升级顾问报表查看器</span><span class="sxs-lookup"><span data-stu-id="bf229-108">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="bf229-109">升级顾问帮助</span><span class="sxs-lookup"><span data-stu-id="bf229-109">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="bf229-110">第一次使用升级顾问时，应运行升级顾问分析向导来分析服务器。</span><span class="sxs-lookup"><span data-stu-id="bf229-110">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze a server.</span></span> <span data-ttu-id="bf229-111">向导完成分析后，请单击向导中的 "**启动报表**" 或返回到升级顾问起始页。</span><span class="sxs-lookup"><span data-stu-id="bf229-111">When the wizard completes the analysis, click **Launch Report** from the wizard or return to the Upgrade Advisor start page.</span></span> <span data-ttu-id="bf229-112">从该起始页中，运行升级顾问报表查看器查看报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-112">From there, run the Upgrade Advisor Report Viewer to view the report.</span></span> <span data-ttu-id="bf229-113">报表提供的链接内容包含有助于解决已知问题的信息。</span><span class="sxs-lookup"><span data-stu-id="bf229-113">The report provides links to information that will help you resolve known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis-wizard"></a><span data-ttu-id="bf229-114">升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="bf229-114">Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="bf229-115">若要执行分析，请单击升级顾问起始页上的 "**启动升级顾问分析向导**"。</span><span class="sxs-lookup"><span data-stu-id="bf229-115">To perform an analysis, click **Launch Upgrade Advisor Analysis Wizard** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="bf229-116">升级顾问分析向导收集与计算机、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件以及要分析的跟踪文件有关的信息。</span><span class="sxs-lookup"><span data-stu-id="bf229-116">The Upgrade Advisor Analysis Wizard gathers information about the computer, instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, and trace files that you want to analyze.</span></span> <span data-ttu-id="bf229-117">收集并确认所有信息之后，升级顾问分析向导会分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="bf229-117">After all the information has been gathered and confirmed, the Upgrade Advisor Analysis Wizard analyzes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf229-118">每次运行升级顾问分析向导时，都会生成一个独立的报表，而不会覆盖选定组件的现有报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-118">Each time you run the Upgrade Advisor Analysis Wizard, a separate report is generated, and existing reports for the selected components are not overwritten.</span></span> <span data-ttu-id="bf229-119">但是，报表查看器只显示最近的五个报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-119">However, the report viewer displays only the five latest reports.</span></span>  
  
 <span data-ttu-id="bf229-120">当升级顾问分析向导完成分析之后，将分别为分析过程中包括的每个组件创建一个 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="bf229-120">When the Upgrade Advisor Analysis Wizard finishes its analysis, it creates an XML file for each component that you have included in the analysis.</span></span> <span data-ttu-id="bf229-121">XML 文件包含在每个组件中发现的项和问题。</span><span class="sxs-lookup"><span data-stu-id="bf229-121">The XML files contain the items and issues discovered in each component.</span></span>  
  
### <a name="what-upgrade-advisor-analyzes"></a><span data-ttu-id="bf229-122">升级顾问的分析内容</span><span class="sxs-lookup"><span data-stu-id="bf229-122">What Upgrade Advisor Analyzes</span></span>  
 <span data-ttu-id="bf229-123">在每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的升级顾问的上下文中都运行有专用分析器。</span><span class="sxs-lookup"><span data-stu-id="bf229-123">A dedicated analyzer runs in the context of Upgrade Advisor for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span> <span data-ttu-id="bf229-124">每个分析器的输出均为针对该组件的 XML 报告。</span><span class="sxs-lookup"><span data-stu-id="bf229-124">The output of each analyzer is an XML report for that component.</span></span>  
  
 <span data-ttu-id="bf229-125">升级顾问查询以下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件：</span><span class="sxs-lookup"><span data-stu-id="bf229-125">Upgrade Advisor queries the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="bf229-126">数据库服务器（[!INCLUDE[ssDE](../../includes/ssde-md.md)] 联机丛书中也称为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]），它包括 Replication、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、全文搜索和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="bf229-126">Database Server (also referred to as the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online), which includes Replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Full-Text Search, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="bf229-127">在分析过程中，每个分析器都创建一个日志文件。</span><span class="sxs-lookup"><span data-stu-id="bf229-127">During analysis, each analyzer creates a log file.</span></span> <span data-ttu-id="bf229-128">可以使用这些日志文件来排除分析故障。</span><span class="sxs-lookup"><span data-stu-id="bf229-128">You can use these log files to troubleshoot the analysis.</span></span> <span data-ttu-id="bf229-129">例如，如果升级顾问运行缓慢，可以查看日志文件确定造成拖延的原因。</span><span class="sxs-lookup"><span data-stu-id="bf229-129">For example, if Upgrade Advisor is running slowly, you can view the log files to determine the cause of the delay.</span></span>  
  
### <a name="upgrade-advisor-limitations"></a><span data-ttu-id="bf229-130">升级顾问的局限性</span><span class="sxs-lookup"><span data-stu-id="bf229-130">Upgrade Advisor Limitations</span></span>  
 <span data-ttu-id="bf229-131">升级顾问无法检测出可能影响升级的每个问题。</span><span class="sxs-lookup"><span data-stu-id="bf229-131">Upgrade Advisor cannot detect every issue that might affect an upgrade.</span></span> <span data-ttu-id="bf229-132">例如，如果您在运行于最终用户桌面的客户端应用程序中嵌入了 SQL 代码，则升级顾问将无法分析此应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf229-132">For example, if you have embedded SQL code in a client application that runs on end-user desktops, it will not be possible for Upgrade Advisor to analyze the applications.</span></span> <span data-ttu-id="bf229-133">对于这些项，仍必须考虑这些问题并按安装中的要求升级、迁移或修改信息。</span><span class="sxs-lookup"><span data-stu-id="bf229-133">For these items, you still must consider the issues and upgrade, migrate, or modify the information as required in your installation.</span></span>  
  
 <span data-ttu-id="bf229-134">升级顾问不分析加密的存储过程、扩展存储过程中的代码以及使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 以外的语言编写的源代码。</span><span class="sxs-lookup"><span data-stu-id="bf229-134">Upgrade Advisor does not analyze encrypted stored procedures, code in extended stored procedures, and source code in languages other than [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="upgrade-advisor-report-viewer"></a><span data-ttu-id="bf229-135">升级顾问报表查看器</span><span class="sxs-lookup"><span data-stu-id="bf229-135">Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="bf229-136">若要查看升级顾问报表，请单击升级顾问起始页上的 "**启动升级顾问报表查看器**"。</span><span class="sxs-lookup"><span data-stu-id="bf229-136">To view an Upgrade Advisor report, click **Launch Upgrade Advisor Report Viewer** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="bf229-137">升级顾问报表查看器启动时，将加载默认目录中的报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-137">When the Upgrade Advisor Report Viewer starts, the reports in the default directory are loaded.</span></span> <span data-ttu-id="bf229-138">如果升级顾问报表查看器在默认目录中未找到任何报表，则不会显示报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-138">Reports are not displayed if the Upgrade Advisor Report Viewer does not find any reports in the default directory.</span></span> <span data-ttu-id="bf229-139">如果默认目录中没有报表，可以运行升级顾问分析向导来创建报表或从其他服务器或子目录中加载现有报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-139">If there are no reports in the default directory, you can either run the Upgrade Advisor Analysis Wizard to create a report or load an existing report from another server or from a subdirectory.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="bf229-140">升级顾问不会覆盖现有报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-140">Upgrade Advisor does not overwrite existing reports.</span></span> <span data-ttu-id="bf229-141">但是，报表查看器只显示最近的五个报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-141">However, the report viewer displays only the five latest reports.</span></span> <span data-ttu-id="bf229-142">若要查看以前的报表，请从 "**报表**" 下拉列表框中选择该报表。</span><span class="sxs-lookup"><span data-stu-id="bf229-142">To view an earlier report, select the report from the **Report** drop-down list box.</span></span> <span data-ttu-id="bf229-143">时间戳指示生成报表的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="bf229-143">The timestamp indicates the date and time the report was generated.</span></span>  
  
 <span data-ttu-id="bf229-144">将升级顾问分析向导生成的 XML 文件加载到升级顾问报表查看器中后，将为每个组件显示一个报告。</span><span class="sxs-lookup"><span data-stu-id="bf229-144">When XML files from the Upgrade Advisor Analysis Wizard are loaded into the Upgrade Advisor Report Viewer, a report for each component is displayed.</span></span> <span data-ttu-id="bf229-145">该报表包含需要解决的所有已知问题（包括可检测到的问题和无法检测到的问题）。</span><span class="sxs-lookup"><span data-stu-id="bf229-145">The report contains all the known issues, both detectable and undetectable, that you need to address.</span></span> <span data-ttu-id="bf229-146">每个问题都有指示重要性的图标、通知何时必须解决此问题的标签和一个简要说明。</span><span class="sxs-lookup"><span data-stu-id="bf229-146">For each issue there is an icon indicating importance, a label informing you when the issue must be fixed, and a short description.</span></span> <span data-ttu-id="bf229-147">展开问题时，您将看到更详细的说明、问题详细信息链接和帮助文件链接。</span><span class="sxs-lookup"><span data-stu-id="bf229-147">When you expand an issue, you will see a longer description, a link to issue details, and a link to the Help file.</span></span> <span data-ttu-id="bf229-148">每个问题的信息都旨在为您提供充足的信息以便解决此问题。</span><span class="sxs-lookup"><span data-stu-id="bf229-148">The information for each issue is designed to provide enough information for you to fix the issue.</span></span>  
  
 <span data-ttu-id="bf229-149">大多数组件都存在无法检测到的问题。</span><span class="sxs-lookup"><span data-stu-id="bf229-149">Most components have issues that cannot be detected.</span></span> <span data-ttu-id="bf229-150">若要查看这些问题，请展开组件的 "**其他升级问题**" 项，然后单击链接以查看有关文档中的问题的其他信息。</span><span class="sxs-lookup"><span data-stu-id="bf229-150">To view these issues, expand the **Other Upgrade Issues** item for the component, and then click the link to view additional information about the issues in the documentation.</span></span> <span data-ttu-id="bf229-151">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 向后兼容问题的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="bf229-151">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backward compatibility issues, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf229-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf229-152">See Also</span></span>  
 [<span data-ttu-id="bf229-153">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="bf229-153">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
