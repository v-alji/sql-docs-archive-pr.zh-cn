---
title: " (用户界面) 运行升级顾问 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a5e47ef2b8183823dff884e114adc420e371adf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591085"
---
# <a name="running-upgrade-advisor-user-interface"></a><span data-ttu-id="39633-102">运行升级顾问（用户界面）</span><span class="sxs-lookup"><span data-stu-id="39633-102">Running Upgrade Advisor (User Interface)</span></span>
  <span data-ttu-id="39633-103">在升级计划期间，可运行升级顾问来分析本地或远程组件。</span><span class="sxs-lookup"><span data-stu-id="39633-103">You can run Upgrade Advisor to analyze local or remote components during upgrade planning.</span></span> <span data-ttu-id="39633-104">升级顾问为分析的每个组件和实例生成一个报表。</span><span class="sxs-lookup"><span data-stu-id="39633-104">Upgrade Advisor produces a report for each component and instance that is analyzed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39633-105">升级顾问不分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的远程实例。</span><span class="sxs-lookup"><span data-stu-id="39633-105">Upgrade Advisor does not analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="39633-106">若要分析 [!INCLUDE[ssRS](../../includes/ssrs.md)] 实例，升级顾问必须安装在安装 [!INCLUDE[ssRS](../../includes/ssrs.md)] 的计算机上。</span><span class="sxs-lookup"><span data-stu-id="39633-106">To analyze an instance of [!INCLUDE[ssRS](../../includes/ssrs.md)], Upgrade Advisor must be installed on the computer where [!INCLUDE[ssRS](../../includes/ssrs.md)] is installed.</span></span>  
>   
>  <span data-ttu-id="39633-107">若要分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services，必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 同一台计算机上安装并安装。</span><span class="sxs-lookup"><span data-stu-id="39633-107">To analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, you must have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] installed and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed on the same computer.</span></span>  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="39633-108">运行升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="39633-108">Running the Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="39633-109">运行升级顾问分析向导的过程包含以下六个步骤：</span><span class="sxs-lookup"><span data-stu-id="39633-109">Running the Upgrade Advisor Analysis Wizard has six steps:</span></span>  
  
1.  <span data-ttu-id="39633-110">从升级顾问的起始页启动向导。</span><span class="sxs-lookup"><span data-stu-id="39633-110">Launch the wizard from the Upgrade Advisor start page.</span></span>  
  
2.  <span data-ttu-id="39633-111">标识要分析的服务器和组件。</span><span class="sxs-lookup"><span data-stu-id="39633-111">Identify server and components to analyze.</span></span>  
  
3.  <span data-ttu-id="39633-112">收集身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="39633-112">Gather authentication information.</span></span>  
  
4.  <span data-ttu-id="39633-113">基于组件类型收集其他参数。</span><span class="sxs-lookup"><span data-stu-id="39633-113">Gather additional parameters based on component type.</span></span>  
  
5.  <span data-ttu-id="39633-114">分析所选的组件。</span><span class="sxs-lookup"><span data-stu-id="39633-114">Analyze selected components.</span></span>  
  
6.  <span data-ttu-id="39633-115">生成升级问题的报告。</span><span class="sxs-lookup"><span data-stu-id="39633-115">Generate report of upgrade issues.</span></span>  
  
 <span data-ttu-id="39633-116">有关升级顾问分析向导的详细信息，请参阅[如何：运行升级顾问分析向导](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="39633-116">For more information about the Upgrade Advisor Analysis Wizard, see [How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).</span></span>  
  
 <span data-ttu-id="39633-117">有关每个步骤所需的特定信息，请参阅[升级顾问用户界面参考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="39633-117">For specific information that is required for each step, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a><span data-ttu-id="39633-118">运行升级顾问报表查看器</span><span class="sxs-lookup"><span data-stu-id="39633-118">Running the Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="39633-119">您可以使用升级顾问报表查看器来查看升级顾问分析向导生成的报表。</span><span class="sxs-lookup"><span data-stu-id="39633-119">You use the Upgrade Advisor Report Viewer to view reports generated by the Upgrade Advisor Analysis Wizard.</span></span> <span data-ttu-id="39633-120">加载该报表后，可按照以下条件筛选报表内容：</span><span class="sxs-lookup"><span data-stu-id="39633-120">When the report is loaded, you can filter the components of the report by the following factors:</span></span>  
  
-   <span data-ttu-id="39633-121">所有问题</span><span class="sxs-lookup"><span data-stu-id="39633-121">All issues</span></span>  
  
-   <span data-ttu-id="39633-122">所有升级问题</span><span class="sxs-lookup"><span data-stu-id="39633-122">All upgrade issues</span></span>  
  
-   <span data-ttu-id="39633-123">升级前的问题</span><span class="sxs-lookup"><span data-stu-id="39633-123">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="39633-124">所有迁移问题</span><span class="sxs-lookup"><span data-stu-id="39633-124">All migration issues</span></span>  
  
-   <span data-ttu-id="39633-125">已解决的问题</span><span class="sxs-lookup"><span data-stu-id="39633-125">Resolved issues</span></span>  
  
-   <span data-ttu-id="39633-126">未解决的问题</span><span class="sxs-lookup"><span data-stu-id="39633-126">Unresolved issues</span></span>  
  
 <span data-ttu-id="39633-127">有关使用报表查看器的分步说明，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="39633-127">For step-by-step instructions for using the report viewer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="39633-128">如何查看升级顾问报表</span><span class="sxs-lookup"><span data-stu-id="39633-128">How to: View an Upgrade Advisor Report</span></span>](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [<span data-ttu-id="39633-129">如何筛选报表</span><span class="sxs-lookup"><span data-stu-id="39633-129">How to: Filter Reports</span></span>](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [<span data-ttu-id="39633-130">如何导出报表</span><span class="sxs-lookup"><span data-stu-id="39633-130">How to: Export Reports</span></span>](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="39633-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39633-131">See Also</span></span>  
 <span data-ttu-id="39633-132">[如何：运行升级顾问分析向导](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="39633-132">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="39633-133">[升级顾问用户界面参考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="39633-133">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 <span data-ttu-id="39633-134">[解决升级问题](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="39633-134">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="39633-135">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="39633-135">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
