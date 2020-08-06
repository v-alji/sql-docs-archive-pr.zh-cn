---
title: 发布信息、警告 (快照发布、SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3ae662a339e1e211ce4f46a588f4d7de65bf5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690530"
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="a7a1a-102">发布信息，警告（快照发布，SQL Server 2005 及更高版本）</span><span class="sxs-lookup"><span data-stu-id="a7a1a-102">Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="a7a1a-103">**“警告”** 选项卡适用于运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本的分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="a7a1a-104">使用 **“警告”** 选项卡可以为所选发布执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="a7a1a-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="a7a1a-105">启用警告。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="a7a1a-106">指定与警告关联的阈值。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="a7a1a-107">定义与警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="a7a1a-108">警告、阈值和警报</span><span class="sxs-lookup"><span data-stu-id="a7a1a-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="a7a1a-109">默认情况下，复制监视器会为未初始化的订阅显示警告：在包含订阅信息的页的 **“状态”** 列中，显示 **“未初始化的订阅”** 状态作为警告。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="a7a1a-110">对于快照发布，您也可以通过设置选项 **“如果订阅将在阈值内过期，则发出警告”** ，指定在订阅即将过期时发出警告。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-110">For snapshot publications, you can also specify that imminent subscription expiration results in a warning by setting the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="a7a1a-111">如果达到或超过指定的阈值，订阅状态将显示为 **“即将过期/已过期”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-111">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="a7a1a-112">除了在复制监视器中显示警告之外，达到阈值也可以触发警报。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-112">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="a7a1a-113">通过单击 **“配置警报”** 并在 **“配置复制警报”** 对话框中提供信息，可以定义警报。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-113">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7a1a-114">选项</span><span class="sxs-lookup"><span data-stu-id="a7a1a-114">Options</span></span>  
 <span data-ttu-id="a7a1a-115">**已启用**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-115">**Enabled**</span></span>  
 <span data-ttu-id="a7a1a-116">选择此项可以启用警告并指定阈值。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-116">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="a7a1a-117">**警告**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-117">**Warning**</span></span>  
 <span data-ttu-id="a7a1a-118">与阈值关联的警告的说明。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-118">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="a7a1a-119">**阈值**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-119">**Threshold**</span></span>  
 <span data-ttu-id="a7a1a-120">指定阈值的值。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-120">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="a7a1a-121">**“配置警报”**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-121">**Configure Alerts**</span></span>  
 <span data-ttu-id="a7a1a-122">从 **“警告”** 网格中选择行，再单击 **“配置警报”** 可启动 **“配置复制警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-122">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="a7a1a-123">使用该对话框，可以定义与所选阈值和警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-123">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="a7a1a-124">**放弃更改**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-124">**Discard Changes**</span></span>  
 <span data-ttu-id="a7a1a-125">单击此项可放弃对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-125">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7a1a-126">单击 **“放弃更改”** 不会影响在 **“配置复制警报”** 对话框中定义的警报。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-126">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="a7a1a-127">**保存更改**</span><span class="sxs-lookup"><span data-stu-id="a7a1a-127">**Save Changes**</span></span>  
 <span data-ttu-id="a7a1a-128">单击此项可保存对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="a7a1a-128">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a1a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7a1a-129">See Also</span></span>  
 <span data-ttu-id="a7a1a-130">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a7a1a-130">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="a7a1a-131">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a7a1a-131">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="a7a1a-132">监视复制</span><span class="sxs-lookup"><span data-stu-id="a7a1a-132">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
