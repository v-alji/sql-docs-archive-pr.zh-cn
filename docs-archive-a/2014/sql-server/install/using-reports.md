---
title: 使用报表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694216"
---
# <a name="using-reports"></a><span data-ttu-id="ba73a-102">使用报表</span><span class="sxs-lookup"><span data-stu-id="ba73a-102">Using Reports</span></span>
  <span data-ttu-id="ba73a-103">系统会针对每个组件生成单独的报表，并且必要时会为升级顾问分析向导在服务器上分析的每个实例生成单独的报表。</span><span class="sxs-lookup"><span data-stu-id="ba73a-103">A separate report is generated for each component, and, where necessary, each instance, that the Upgrade Advisor Analysis Wizard analyzes on a server.</span></span> <span data-ttu-id="ba73a-104">报表用于提供有关影响升级的已知问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ba73a-104">The report provides details about known issues that affect an upgrade.</span></span> <span data-ttu-id="ba73a-105">它还提供指向信息的链接，并提供用于解决确定的问题的建议操作。</span><span class="sxs-lookup"><span data-stu-id="ba73a-105">It also provides links to information and suggested actions for addressing the identified issues.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba73a-106">如果升级顾问报表查看器在默认报表目录中找不到任何报表，则可以使用 "**打开报表**" 链接从其他目录加载报表。</span><span class="sxs-lookup"><span data-stu-id="ba73a-106">If the Upgrade Advisor Report Viewer does not find any reports in the default reports directory, you can load a report from a different directory by using the **Open Report** link.</span></span>  
  
## <a name="viewing-reports"></a><span data-ttu-id="ba73a-107">查看报表</span><span class="sxs-lookup"><span data-stu-id="ba73a-107">Viewing Reports</span></span>  
 <span data-ttu-id="ba73a-108">可以使用升级顾问报表查看器来查看升级顾问报表。</span><span class="sxs-lookup"><span data-stu-id="ba73a-108">You use the Upgrade Advisor Report Viewer to view Upgrade Advisor reports.</span></span> <span data-ttu-id="ba73a-109">若要查看报表，请在升级顾问起始页上，单击 "**启动升级顾问报表查看器**"。</span><span class="sxs-lookup"><span data-stu-id="ba73a-109">To view reports, on the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
 <span data-ttu-id="ba73a-110">为服务器加载报表后，可选择要查看其升级问题的组件。</span><span class="sxs-lookup"><span data-stu-id="ba73a-110">After you load a report for a server, you can select a component for which you want to see upgrade issues.</span></span> <span data-ttu-id="ba73a-111">你可以从 "**筛选依据**" 框中应用筛选器以查看以下内容：</span><span class="sxs-lookup"><span data-stu-id="ba73a-111">You can apply a filter from the **Filter By** box to see the following:</span></span>  
  
-   <span data-ttu-id="ba73a-112">所有问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-112">All issues</span></span>  
  
-   <span data-ttu-id="ba73a-113">所有升级问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-113">All upgrade issues</span></span>  
  
-   <span data-ttu-id="ba73a-114">升级前的问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-114">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="ba73a-115">所有迁移问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-115">All migration issues</span></span>  
  
-   <span data-ttu-id="ba73a-116">已解决的问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-116">Resolved issues</span></span>  
  
-   <span data-ttu-id="ba73a-117">未解决的问题</span><span class="sxs-lookup"><span data-stu-id="ba73a-117">Unresolved issues</span></span>  
  
 <span data-ttu-id="ba73a-118">如果报表的问题超过20个，可通过单击问题列表顶部或底部的 "**后 20**个" 或 "**前 20**个"，移到下一个或上一组问题。</span><span class="sxs-lookup"><span data-stu-id="ba73a-118">If your report has more than 20 issues, you can move to the next or previous group of issues by clicking **Next 20** or **Previous 20** at the top or bottom of the issues list.</span></span>  
  
 <span data-ttu-id="ba73a-119">通过从 "**报表**" 下拉列表框中选择报表，可以查看最多五个已保存的报表。</span><span class="sxs-lookup"><span data-stu-id="ba73a-119">You can view up to five saved reports by selecting the reports from the **Report** drop-down list box.</span></span> <span data-ttu-id="ba73a-120">这些报表是按其生成时间戳列出的。</span><span class="sxs-lookup"><span data-stu-id="ba73a-120">The reports are listed by the timestamp from when they were generated.</span></span>  
  
## <a name="report-format"></a><span data-ttu-id="ba73a-121">报表格式</span><span class="sxs-lookup"><span data-stu-id="ba73a-121">Report Format</span></span>  
 <span data-ttu-id="ba73a-122">报表查看器分三列显示报表问题。</span><span class="sxs-lookup"><span data-stu-id="ba73a-122">The report viewer displays report issues in three columns.</span></span> <span data-ttu-id="ba73a-123">每个问题均可折叠，以便您能够隐藏说明并仅查看关键信息。</span><span class="sxs-lookup"><span data-stu-id="ba73a-123">Each issue is collapsible so that you can hide the description and view only the key information.</span></span>  
  
 <span data-ttu-id="ba73a-124">第一列是**重要性**列。</span><span class="sxs-lookup"><span data-stu-id="ba73a-124">The first column is the **Importance** column.</span></span> <span data-ttu-id="ba73a-125">图标指示的是每一问题的重要性，对于阻塞问题或重要问题，显示带 X 的红色圆圈，而对于警告问题和供参考的信息，则显示带感叹号的黄色三角形。</span><span class="sxs-lookup"><span data-stu-id="ba73a-125">Icons indicate the importance for each issue by displaying either a red circle with an X for blocking or important issues or a yellow triangle with an exclamation mark for Warning and Information issues.</span></span> <span data-ttu-id="ba73a-126">第二列是**修复的时间**，指示何时必须解决问题。</span><span class="sxs-lookup"><span data-stu-id="ba73a-126">The second column, **When to fix**, indicates when you must resolve the issue.</span></span> <span data-ttu-id="ba73a-127">您可以对报表的**重要性**或**修改时间**进行排序。</span><span class="sxs-lookup"><span data-stu-id="ba73a-127">You can sort the report on either the **Importance** or **When to fix** column.</span></span> <span data-ttu-id="ba73a-128">第三列 "**说明**" 列出了问题的标题。</span><span class="sxs-lookup"><span data-stu-id="ba73a-128">The third column, **Description**, lists the title of the issue.</span></span>  
  
 <span data-ttu-id="ba73a-129">展开某一问题后，可显示相应的附加信息、指向有关如何解决该问题的详细信息的链接以及指向显示问题详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="ba73a-129">You can expand an issue to display additional information, a link to detailed information about resolving the issue, and a link to show issue details.</span></span> <span data-ttu-id="ba73a-130">在单击用以获取该问题的详细信息的链接后，将会显示一个帮助主题，其中显示有关该问题的信息以及有关如何解决该问题的信息。</span><span class="sxs-lookup"><span data-stu-id="ba73a-130">When you click the link to get detailed information for the issue, a Help topic with information about the issue and instructions for addressing the issue is displayed.</span></span> <span data-ttu-id="ba73a-131">解决问题或管理操作项后，可以通过选中 "**此问题已解决**" 复选框，将问题标记为完成。</span><span class="sxs-lookup"><span data-stu-id="ba73a-131">After you have fixed an issue, or to manage your action items, you can mark issues as complete by selecting the **This issue has been resolved** check box.</span></span> <span data-ttu-id="ba73a-132">如果要从升级问题列表中删除已解决的问题，请单击 "**刷新**"。</span><span class="sxs-lookup"><span data-stu-id="ba73a-132">If you want to remove the resolved issues from the list of upgrade issues, click **Refresh**.</span></span> <span data-ttu-id="ba73a-133">在对同一组件运行升级顾问分析向导或从 "**筛选依据**" 选项应用 "**已解决的问题**" 筛选器之前，不会再次显示此问题。</span><span class="sxs-lookup"><span data-stu-id="ba73a-133">The issue is not displayed again until you either run the Upgrade Advisor Analysis Wizard against the same component or apply the **Resolved Issues** filter from the **Filter By** option.</span></span>  
  
## <a name="report-files"></a><span data-ttu-id="ba73a-134">报表文件</span><span class="sxs-lookup"><span data-stu-id="ba73a-134">Report Files</span></span>  
 <span data-ttu-id="ba73a-135">升级顾问分析向导会在 My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports 目录中创建报告，并为您分析的每个服务器创建一个子目录。</span><span class="sxs-lookup"><span data-stu-id="ba73a-135">The Upgrade Advisor Analysis Wizard creates reports in the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports directory and creates a subdirectory for each server that you analyze.</span></span> <span data-ttu-id="ba73a-136">报表文件为遵循特定的命名约定的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="ba73a-136">The report files are XML files that follow a specific naming convention.</span></span> <span data-ttu-id="ba73a-137">启动升级顾问报表查看器后，将显示默认目录中的报表文件。</span><span class="sxs-lookup"><span data-stu-id="ba73a-137">When you launch the Upgrade Advisor Report Viewer, the report files in the default directory are displayed.</span></span> <span data-ttu-id="ba73a-138">如果要将报表文件复制到此文件夹，则报表文件必须遵循相应的命名约定，否则报表查看器不会自动显示这些报表文件。</span><span class="sxs-lookup"><span data-stu-id="ba73a-138">If you copy report files into this folder, they must adhere to the naming convention or the report viewer will not display them automatically.</span></span>  
  
 <span data-ttu-id="ba73a-139">如果您希望与他人共享信息，可向他们发送 XML 报表。</span><span class="sxs-lookup"><span data-stu-id="ba73a-139">If you want to share the information with other people, you can send them the XML report.</span></span> <span data-ttu-id="ba73a-140">或者，如果您希望使用其他应用程序，可将报表导出为可用于创建电子表格、文本文件或电子邮件的逗号分隔值文件。</span><span class="sxs-lookup"><span data-stu-id="ba73a-140">Or, if you want to use another application, you can export the report into a comma-separated value file that you can use to create a spreadsheet, text file, or e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba73a-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba73a-141">See Also</span></span>  
 <span data-ttu-id="ba73a-142">[如何查看升级顾问报表](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span><span class="sxs-lookup"><span data-stu-id="ba73a-142">[How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span></span>  
 <span data-ttu-id="ba73a-143">[如何：导出报表](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ba73a-143">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="ba73a-144">[如何：筛选报表](../../../2014/sql-server/install/how-to-filter-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ba73a-144">[How to: Filter Reports](../../../2014/sql-server/install/how-to-filter-reports.md) </span></span>  
 <span data-ttu-id="ba73a-145">[解决升级问题](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ba73a-145">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ba73a-146">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="ba73a-146">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
