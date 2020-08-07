---
title: 升级顾问进度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b504b8f1c8392ad2cf55837dc65bbb2f019d6f48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586110"
---
# <a name="upgrade-advisor-progress"></a><span data-ttu-id="0ad1c-102">升级顾问进度</span><span class="sxs-lookup"><span data-stu-id="0ad1c-102">Upgrade Advisor Progress</span></span>
  <span data-ttu-id="0ad1c-103">升级顾问分析从对选定的各个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件执行分析的专用分析器开始。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-103">Upgrade Advisor analysis starts with a dedicated analyzer that performs an analysis of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that you selected.</span></span> <span data-ttu-id="0ad1c-104">分析组件时，将在 "**进度**" 对话框中报告进度。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-104">As components are analyzed, progress is reported in the **Progress** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ad1c-105">选项</span><span class="sxs-lookup"><span data-stu-id="0ad1c-105">Options</span></span>  
 <span data-ttu-id="0ad1c-106">**Action**</span><span class="sxs-lookup"><span data-stu-id="0ad1c-106">**Action**</span></span>  
 <span data-ttu-id="0ad1c-107">指定选择来分析的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-107">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that is selected for analysis.</span></span>  
  
 <span data-ttu-id="0ad1c-108">**Status**</span><span class="sxs-lookup"><span data-stu-id="0ad1c-108">**Status**</span></span>  
 <span data-ttu-id="0ad1c-109">显示从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件进度界面返回的状态值。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-109">Displays the status value returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component progress interface.</span></span>  
  
 <span data-ttu-id="0ad1c-110">**Message**</span><span class="sxs-lookup"><span data-stu-id="0ad1c-110">**Message**</span></span>  
 <span data-ttu-id="0ad1c-111">显示从各个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分析器返回的错误消息、失败消息或成功消息。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-111">Displays error, failure, or success messages returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] individual analyzer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ad1c-112">如果分析时间过长，则可以停止分析，退出升级顾问分析向导，然后重新运行该向导。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-112">If the analysis is taking too long, you can stop the analysis, exit the Upgrade Advisor Analysis Wizard, and then rerun the wizard.</span></span> <span data-ttu-id="0ad1c-113">若要缩短分析时间，请少选择一些组件来扫描。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-113">To reduce analysis time, select fewer components to scan.</span></span>  
  
 <span data-ttu-id="0ad1c-114">分析完成后，报表将写入文件。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-114">When analysis is complete, the report is written to a file.</span></span> <span data-ttu-id="0ad1c-115">您可以通过单击 "**启动报表**" 从此页启动报表查看器来查看报表。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-115">You can view the report by clicking **Launch Report** to launch the report viewer from this page.</span></span> <span data-ttu-id="0ad1c-116">如果以后要查看报表，可以从升级顾问起始页打开**升级顾问报表查看器**。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-116">If you want to view the report later, you can open the **Upgrade Advisor Report Viewer** from the Upgrade Advisor start page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ad1c-117">每次分析服务器后，都会保存先前的报表。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-117">Previous reports are saved every time you analyze a server.</span></span> <span data-ttu-id="0ad1c-118">这些报表使用时间戳作为文件名进行保存。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-118">The reports are saved using the timestamp for the file name.</span></span> <span data-ttu-id="0ad1c-119">报表查看器显示最近保存的五个报表。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-119">The report viewer displays the latest five saved reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad1c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ad1c-120">See Also</span></span>  
 <span data-ttu-id="0ad1c-121">[如何启动升级顾问](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="0ad1c-121">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="0ad1c-122">[如何：运行升级顾问分析向导](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0ad1c-122">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="0ad1c-123">[SQL Server 组件](../../../2014/sql-server/install/sql-server-components.md) </span><span class="sxs-lookup"><span data-stu-id="0ad1c-123">[SQL Server Components](../../../2014/sql-server/install/sql-server-components.md) </span></span>  
 <span data-ttu-id="0ad1c-124">[升级顾问用户界面参考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0ad1c-124">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 [<span data-ttu-id="0ad1c-125">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="0ad1c-125">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
