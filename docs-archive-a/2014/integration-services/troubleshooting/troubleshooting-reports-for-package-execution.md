---
title: 包执行的疑难解答报告 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fc476ac-bd69-434e-9636-70776e0b3b6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b20d9c9c02af3f3df96e2ef46a7b25251793fa55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588600"
---
# <a name="troubleshooting-reports-for-package-execution"></a><span data-ttu-id="db3d1-102">对包执行进行故障排除的报告</span><span class="sxs-lookup"><span data-stu-id="db3d1-102">Troubleshooting Reports for Package Execution</span></span>
  <span data-ttu-id="db3d1-103">在当前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了标准报告，可帮助您监视部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包并排除其问题。</span><span class="sxs-lookup"><span data-stu-id="db3d1-103">In the current release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], standard reports are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to help you monitor and troubleshoot [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that have been deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span> <span data-ttu-id="db3d1-104">这些包报告中有两个报告尤其有助您查看包的执行状态，并确定执行失败的原因。</span><span class="sxs-lookup"><span data-stu-id="db3d1-104">Two of these package reports in particular help you to view package execution status and identify the cause of execution failures.</span></span>  
  
-   <span data-ttu-id="db3d1-105">**Integration Services** 面板 - 此报告提供过去 24 小时内 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上所有包执行情况的概览。</span><span class="sxs-lookup"><span data-stu-id="db3d1-105">**Integration Services Dashboard** - This report provides an overview of all the package executions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance in the past 24 hours.</span></span> <span data-ttu-id="db3d1-106">该报告显示每个包的状态、操作类型、包名称之类的信息。</span><span class="sxs-lookup"><span data-stu-id="db3d1-106">The report displays information such as Status, Operation Type, Package Name, etc., for each package.</span></span>  
  
     <span data-ttu-id="db3d1-107">开始时间、结束时间和持续时间可以解释如下：</span><span class="sxs-lookup"><span data-stu-id="db3d1-107">The Start Time, End Time, and Duration can be interpreted as follows:</span></span>  
  
    -   <span data-ttu-id="db3d1-108">如果包仍在运行，则持续时间 = 当前时间 - 开始时间</span><span class="sxs-lookup"><span data-stu-id="db3d1-108">If the package is still running, then Duration = current time - Start Time</span></span>  
  
    -   <span data-ttu-id="db3d1-109">如果包已完成操作，则持续时间 = 结束时间 - 开始时间</span><span class="sxs-lookup"><span data-stu-id="db3d1-109">If the package has completed, then Duration = End Time - Start Time</span></span>  
  
     <span data-ttu-id="db3d1-110">对于已在服务器上运行的每个包，该面板允许您“放大”以便查找有关可能已发生的包执行错误的具体细节。</span><span class="sxs-lookup"><span data-stu-id="db3d1-110">For each package that has run on the server, the dashboard allows you to "zoom in" to find specific details on package execution errors that may have occurred.</span></span> <span data-ttu-id="db3d1-111">例如，单击“概述”  可以显示执行中各任务的状态的高级概览，或者选择“所有消息”  可以显示作为包执行的一部分捕获的详细消息。</span><span class="sxs-lookup"><span data-stu-id="db3d1-111">For example, click **Overview** to display a high-level overview of the status of the tasks in the execution, or **All Messages** to display the detailed messages that were captured as part of the package execution.</span></span>  
  
     <span data-ttu-id="db3d1-112">您可以通过单击 **“筛选器”** ，然后在 **“筛选设置”** 对话框中选择条件，对在任何页上显示的表进行筛选。</span><span class="sxs-lookup"><span data-stu-id="db3d1-112">You can filter the table displayed on any page by clicking **Filter** and then selecting criteria in the **Filter Settings** dialog.</span></span> <span data-ttu-id="db3d1-113">可用的筛选条件依赖于要显示的数据。</span><span class="sxs-lookup"><span data-stu-id="db3d1-113">The filter criteria available depends on the data being displayed.</span></span> <span data-ttu-id="db3d1-114">您可以通过在 **“筛选设置”** 对话框中单击排序图标，更改报告的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="db3d1-114">You can change the sort order of the report by clicking the sort icon in the **Filter Settings** dialog.</span></span>  
  
-   <span data-ttu-id="db3d1-115">**“活动 - 所有执行”报告** - 此报告显示已在服务器上执行的所有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 执行的摘要。</span><span class="sxs-lookup"><span data-stu-id="db3d1-115">**Activity - All Executions Report** - This report displays a summary of all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] executions that have been performed on the server.</span></span> <span data-ttu-id="db3d1-116">摘要中显示每次执行的信息，如状态、开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="db3d1-116">The summary displays information for each execution such as status, start time, and end time.</span></span> <span data-ttu-id="db3d1-117">每个摘要条目都包含指向有关执行的详细信息的连接，包括在执行期间生成的消息和性能数据。</span><span class="sxs-lookup"><span data-stu-id="db3d1-117">Each summary entry includes links to more information about the execution including messages generated during execution and performance data.</span></span> <span data-ttu-id="db3d1-118">与 Integration Services 面板一样，您可以将筛选器应用于表，以便缩小显示的信息的范围。</span><span class="sxs-lookup"><span data-stu-id="db3d1-118">As with the Integration Services Dashboard, you can apply a filter to the table to narrow down the information displayed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="db3d1-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="db3d1-119">Related Tasks</span></span>  
 [<span data-ttu-id="db3d1-120">查看 Integration Services 服务器的报告</span><span class="sxs-lookup"><span data-stu-id="db3d1-120">View Reports for the Integration Services Server</span></span>](../view-reports-for-the-integration-services-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="db3d1-121">相关内容</span><span class="sxs-lookup"><span data-stu-id="db3d1-121">Related Content</span></span>  
 [<span data-ttu-id="db3d1-122">Integration Services 服务器的报表</span><span class="sxs-lookup"><span data-stu-id="db3d1-122">Reports for the Integration Services Server</span></span>](../reports-for-the-integration-services-server.md)  
  
 [<span data-ttu-id="db3d1-123">包执行的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="db3d1-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  
