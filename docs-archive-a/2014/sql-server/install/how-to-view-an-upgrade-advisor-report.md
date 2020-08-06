---
title: 如何查看升级顾问报表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e6df35b869186a601458889c348153093ccbce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590532"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a><span data-ttu-id="7667f-102">如何查看升级顾问报表</span><span class="sxs-lookup"><span data-stu-id="7667f-102">How to: View an Upgrade Advisor Report</span></span>
  <span data-ttu-id="7667f-103">升级顾问会为选择分析的每个组件创建报表。</span><span class="sxs-lookup"><span data-stu-id="7667f-103">Upgrade Advisor creates reports for each component that you select to analyze.</span></span> <span data-ttu-id="7667f-104">本主题说明如何从升级顾问起始页中查看升级顾问报表。</span><span class="sxs-lookup"><span data-stu-id="7667f-104">This topic describes how to view an Upgrade Advisor report from the Upgrade Advisor start page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7667f-105">报表查看器基于标准文件名加载文件。</span><span class="sxs-lookup"><span data-stu-id="7667f-105">The report viewer loads files based on standard file names.</span></span> <span data-ttu-id="7667f-106">如果文件已重命名，报表查看器将不会加载这些文件。</span><span class="sxs-lookup"><span data-stu-id="7667f-106">If the files have been renamed, the report viewer will not load them.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="7667f-107">查看报表</span><span class="sxs-lookup"><span data-stu-id="7667f-107">To view a report</span></span>  
  
1.  <span data-ttu-id="7667f-108">依次单击 "**开始**"、"**所有程序**"、 **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** ，然后单击 " \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升级顾问\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7667f-108">Click **Start**, click **All Programs**, click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
2.  <span data-ttu-id="7667f-109">在升级顾问起始页上，单击 "**启动升级顾问报表查看器**"。</span><span class="sxs-lookup"><span data-stu-id="7667f-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
3.  <span data-ttu-id="7667f-110">选择位于计算机中的默认位置的报表：</span><span class="sxs-lookup"><span data-stu-id="7667f-110">To select a report in the default location on your computer:</span></span>  
  
    1.  <span data-ttu-id="7667f-111">在 "**服务器**" 列表中，选择服务器。</span><span class="sxs-lookup"><span data-stu-id="7667f-111">In the **Server** list, select a server.</span></span>  
  
    2.  <span data-ttu-id="7667f-112">在 "**实例" 或 "组件**" 列表中，选择组件或组件/实例组合。</span><span class="sxs-lookup"><span data-stu-id="7667f-112">In the **Instance or component** list, select a component or component/instance combination.</span></span>  
  
     <span data-ttu-id="7667f-113">选择其他位置上的报表：</span><span class="sxs-lookup"><span data-stu-id="7667f-113">To select a report at another location:</span></span>  
  
    1.  <span data-ttu-id="7667f-114">单击 "**打开报表**" 链接。</span><span class="sxs-lookup"><span data-stu-id="7667f-114">Click the **Open Report** link.</span></span>  
  
    2.  <span data-ttu-id="7667f-115">找到该报表位置，然后双击 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="7667f-115">Browse to the report location and then double-click the XML file.</span></span>  
  
     <span data-ttu-id="7667f-116">升级顾问存储最多五个以前的分析报表作为历史记录。</span><span class="sxs-lookup"><span data-stu-id="7667f-116">Upgrade Advisor stores up to five reports from previous analysis as history.</span></span> <span data-ttu-id="7667f-117">若要查看这些报表，请单击 "**报表**" 下拉列表框，然后选择报表。</span><span class="sxs-lookup"><span data-stu-id="7667f-117">To view these reports, click the **Report** drop-down list box, and select a report.</span></span> <span data-ttu-id="7667f-118">这些报表是按其生成时间戳列出的。</span><span class="sxs-lookup"><span data-stu-id="7667f-118">The reports are listed by the timestamp from when they were generated.</span></span>  
  
     <span data-ttu-id="7667f-119">该报表包含以下有关所有检测到的问题的详细信息：</span><span class="sxs-lookup"><span data-stu-id="7667f-119">The report contains the following details for all detected issues:</span></span>  
  
    -   <span data-ttu-id="7667f-120">**重要性**，指示修复问题的重要程度。</span><span class="sxs-lookup"><span data-stu-id="7667f-120">**Importance**, which indicates how important it is to fix the issue.</span></span>  
  
    -   <span data-ttu-id="7667f-121">**解决时间**，它指示是否应 (或必须) 在升级到之前或之后升级到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、迁移应用程序或数据之前或之后，或在任何时间之后升级到。</span><span class="sxs-lookup"><span data-stu-id="7667f-121">**When to fix**, which indicates if you should (or must) fix the issue before or after upgrading to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], before or after migrating the application or data, or anytime.</span></span>  
  
    -   <span data-ttu-id="7667f-122">对问题的简短说明。</span><span class="sxs-lookup"><span data-stu-id="7667f-122">A brief description of the issue.</span></span>  
  
4.  <span data-ttu-id="7667f-123">如果报表包含的项超过 20 个，请单击报表顶部或底部的绿色前进箭头查看下一组项。</span><span class="sxs-lookup"><span data-stu-id="7667f-123">If the report contains more than 20 items, click the green forward arrow at the top or bottom of the report to view the next set of items.</span></span> <span data-ttu-id="7667f-124">单击绿色的后退按钮可查看前 20 项。</span><span class="sxs-lookup"><span data-stu-id="7667f-124">Click the green back button to view the previous 20 items.</span></span>  
  
5.  <span data-ttu-id="7667f-125">若要对报表进行排序，请单击列标题。</span><span class="sxs-lookup"><span data-stu-id="7667f-125">To sort the report, click a column heading.</span></span>  
  
6.  <span data-ttu-id="7667f-126">若要查看特定项的详细信息，请单击该项。</span><span class="sxs-lookup"><span data-stu-id="7667f-126">To view details for a specific item, click the item.</span></span> <span data-ttu-id="7667f-127">将会出现该问题的说明以及其他选项：</span><span class="sxs-lookup"><span data-stu-id="7667f-127">A description of the issue appears, along with additional options:</span></span>  
  
    -   <span data-ttu-id="7667f-128">若要查看发现此问题的对象，请单击 "**显示受影响的对象**"。</span><span class="sxs-lookup"><span data-stu-id="7667f-128">To view the objects where this issue was found, click **Show affected objects**.</span></span>  
  
    -   <span data-ttu-id="7667f-129">若要查看有关问题的帮助，请单击 "**告诉我有关此问题的详细信息以及如何解决**"。</span><span class="sxs-lookup"><span data-stu-id="7667f-129">To view help for the issue, click **Tell me more about this issue and how to resolve it**.</span></span>  
  
    -   <span data-ttu-id="7667f-130">若要将问题标记为已解决，这会在再次查看报表时隐藏问题，请选择 "**此问题已解决**"。</span><span class="sxs-lookup"><span data-stu-id="7667f-130">To mark the issue as resolved, which hides the issue when you view the report again, select **This issue has been resolved**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7667f-131">该报表可能包含与无法检测的问题有关的项。</span><span class="sxs-lookup"><span data-stu-id="7667f-131">The report may contain an item for undetectable issues.</span></span> <span data-ttu-id="7667f-132">这些问题是那些无法检测到的问题或会产生太多的误报结果的问题。</span><span class="sxs-lookup"><span data-stu-id="7667f-132">These are issues that cannot be detected or that would generate too many false-positive results.</span></span> <span data-ttu-id="7667f-133">单击 "**告诉我有关此问题的详细信息以及如何解决此问题**" 链接，以查看组件的无法检测的问题的列表。</span><span class="sxs-lookup"><span data-stu-id="7667f-133">Click the **Tell me more about this issue and how to resolve it** link to see a list of undetectable issues for the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7667f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7667f-134">See Also</span></span>  
 <span data-ttu-id="7667f-135">[如何：导出报表](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="7667f-135">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="7667f-136">[如何：运行升级顾问分析向导](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7667f-136">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="7667f-137">[解决升级问题](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7667f-137">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="7667f-138">[升级顾问操作指南主题](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="7667f-138">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="7667f-139">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="7667f-139">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
