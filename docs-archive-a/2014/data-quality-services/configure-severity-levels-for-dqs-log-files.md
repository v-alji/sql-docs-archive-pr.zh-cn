---
title: 为 DQS 日志文件配置严重级别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 46fb9de1fbe1e3e59b20bb2ac7afeebe19ba2da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683075"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a><span data-ttu-id="5fa59-102">为 DQS 日志文件配置严重级别</span><span class="sxs-lookup"><span data-stu-id="5fa59-102">Configure Severity Levels for DQS Log Files</span></span>
  <span data-ttu-id="5fa59-103">本主题介绍如何通过使用 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 为 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)](DQS) 中的不同活动和模块配置严重级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-103">This topic describes how to configure severity levels for various activities and modules in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="5fa59-104">严重级别定义 DQS 中发生的事件的强度。</span><span class="sxs-lookup"><span data-stu-id="5fa59-104">Severity levels define the intensity of events that occur in DQS.</span></span> <span data-ttu-id="5fa59-105">DQS 事件具有以下严重级别，这些级别按严重程度递减列出：</span><span class="sxs-lookup"><span data-stu-id="5fa59-105">DQS events have the following severity levels, in the decreasing order of severity:</span></span>  
  
-   <span data-ttu-id="5fa59-106">**严重**：可能会导致严重/意外结果的重大的运行时错误。</span><span class="sxs-lookup"><span data-stu-id="5fa59-106">**Fatal**: Critical runtime errors that might cause severe/unexpected results.</span></span>  
  
-   <span data-ttu-id="5fa59-107">**错误**：其他运行时错误。</span><span class="sxs-lookup"><span data-stu-id="5fa59-107">**Error**: Other runtime errors.</span></span>  
  
-   <span data-ttu-id="5fa59-108">**警告**：可能会导致错误的事件的有关警告。</span><span class="sxs-lookup"><span data-stu-id="5fa59-108">**Warn**: Warning about events that might result in an error.</span></span>  
  
-   <span data-ttu-id="5fa59-109">**信息**：与一般事件有关的并非错误或警告的信息。</span><span class="sxs-lookup"><span data-stu-id="5fa59-109">**Info**: Information about general events that is not an error or a warning.</span></span> <span data-ttu-id="5fa59-110">例如，一个 DQS 过程已开始。</span><span class="sxs-lookup"><span data-stu-id="5fa59-110">For example, a DQS process has started.</span></span>  
  
-   <span data-ttu-id="5fa59-111">**调试**：有关事件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5fa59-111">**Debug**: Detailed (verbose) information about the event.</span></span>  
  
 <span data-ttu-id="5fa59-112">通过为不同的 DQS 活动和模块配置严重级别，可筛选要记入日志的信息，以及筛选要为各 DQS 活动或模块写入 DQS 日志文件的信息。</span><span class="sxs-lookup"><span data-stu-id="5fa59-112">By configuring severity levels for various DQS activities and modules, you are filtering the information that you want to be logged, and written to the DQS log file for the respective DQS activity or module.</span></span> <span data-ttu-id="5fa59-113">例如，如果您将某一 DQS 活动的严重级别设为 **“警告”**，则只有与该 DQS 活动关联的警告和更高级别严重程度的消息（错误和严重）将被记入日志。</span><span class="sxs-lookup"><span data-stu-id="5fa59-113">For example, if you set the severity level of a DQS activity to **Warn**, only warning and higher severity messages (Error and Fatal) associated with the DQS activity will be logged.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5fa59-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="5fa59-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5fa59-115">Security</span><span class="sxs-lookup"><span data-stu-id="5fa59-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5fa59-116">权限</span><span class="sxs-lookup"><span data-stu-id="5fa59-116">Permissions</span></span>  
 <span data-ttu-id="5fa59-117">您必须具有 DQS_MAIN 数据库的 dqs_administrator 角色，才能配置日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="5fa59-117">You must have the dqs_administrator role on the DQS_MAIN database to configure log severity settings.</span></span>  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a><span data-ttu-id="5fa59-118">在活动级别配置严重级别</span><span class="sxs-lookup"><span data-stu-id="5fa59-118">Configure Severity Levels at Activity Level</span></span>  
 <span data-ttu-id="5fa59-119">您可以在 DQS 中为以下活动配置日志严重性设置：域管理、知识发现、匹配策略、数据清理、数据匹配和引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="5fa59-119">You can configure log severity settings for the following activities in DQS: domain management, knowledge discovery, matching policy, data cleansing, data matching, and reference data services.</span></span> <span data-ttu-id="5fa59-120">执行此操作的步骤：</span><span class="sxs-lookup"><span data-stu-id="5fa59-120">To do so:</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="5fa59-121">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa59-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="5fa59-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="5fa59-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="5fa59-123">接下来，单击 "**日志设置**" 选项卡。列出了以下 DQS 活动，你可以为其选择严重性级别： "**域管理**"、"**知识发现**"、"**清理项目" (Ex) **、**匹配策略和匹配项目**"和" **RDS**"。</span><span class="sxs-lookup"><span data-stu-id="5fa59-123">Next, click the **Log Settings** tab. The following DQS activities are listed for which you can select a severity level: **Domain Management**, **Knowledge Discovery**, **Cleansing Project (Ex. RDS)**, **Matching Policy and Matching Project**, and **RDS**.</span></span>  
  
4.  <span data-ttu-id="5fa59-124">对于某一 DQS 活动，选择您要记入日志的严重级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-124">For a DQS activity, select the severity level that you want to be logged.</span></span> <span data-ttu-id="5fa59-125">您可以选择下列级别之一： **“严重”**、 **“错误”**、 **“警告”**、 **“信息”** 和 **“调试”**。</span><span class="sxs-lookup"><span data-stu-id="5fa59-125">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span> <span data-ttu-id="5fa59-126">例如，对于知识发现活动，如果您只希望将严重消息写入 DQS 日志文件，则在下拉列表中对 **“知识发现”** 活动选择 **“严重”** 。</span><span class="sxs-lookup"><span data-stu-id="5fa59-126">For example, if you want only fatal messages to be written to the DQS log files for the knowledge discovery activity, select **Fatal** in the drop-down list against the **Knowledge Discovery** activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5fa59-127">默认情况下，将为每个活动选择 **“错误”** 。</span><span class="sxs-lookup"><span data-stu-id="5fa59-127">By default, **Error** is selected for each of the activities.</span></span> <span data-ttu-id="5fa59-128">这意味着，默认情况下对于每个活动，错误和严重消息将写入 DQS 日志文件。</span><span class="sxs-lookup"><span data-stu-id="5fa59-128">This implies that error and fatal messages will be written to the DQS log files for each activity, by default.</span></span>  
  
5.  <span data-ttu-id="5fa59-129">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="5fa59-129">Click **Close**.</span></span>  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a><span data-ttu-id="5fa59-130">在模块级别配置严重级别 (Advanced) </span><span class="sxs-lookup"><span data-stu-id="5fa59-130">Configure Severity Levels at Module Level (Advanced)</span></span>  
 <span data-ttu-id="5fa59-131">通过 **“日志设置”** 选项卡中的 **“高级”** 部分，您可以在模块级别配置日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="5fa59-131">The **Advanced** section in the **Log Settings** tab enables you to configure log severity settings at a module level.</span></span> <span data-ttu-id="5fa59-132">模块是在 DQS 中的某一特性内实现不同功能的 DQS 系统程序集。</span><span class="sxs-lookup"><span data-stu-id="5fa59-132">Modules are DQS system assemblies that implement various functionalities within a feature in DQS.</span></span> <span data-ttu-id="5fa59-133">例如，域管理活动包含不同功能，例如定义域规则、定义规则条件、为复合域定义跨域规则等。</span><span class="sxs-lookup"><span data-stu-id="5fa59-133">For example, the domain management activity contains various functionalities such as defining domain rules, defining rule conditions, defining cross-domain rules for composite domains, and so on.</span></span>  
  
 <span data-ttu-id="5fa59-134">有时，活动级别的粒度级别是不足够的。</span><span class="sxs-lookup"><span data-stu-id="5fa59-134">At times, the granularity level at the activity level is not sufficient.</span></span> <span data-ttu-id="5fa59-135">您可能要调查某个活动内的特定模块中发生的问题。</span><span class="sxs-lookup"><span data-stu-id="5fa59-135">You might want to investigate an issue that is occurring in a particular module within an activity.</span></span> <span data-ttu-id="5fa59-136">它有助于选择在模块级别配置日志严重级别，以便更准确地隔离和跟踪问题。</span><span class="sxs-lookup"><span data-stu-id="5fa59-136">It helps to have an option to configure log severities at the module level to isolate and track the issue more precisely.</span></span>  
  
 <span data-ttu-id="5fa59-137">在活动级别指定的日志严重性设置将确定构成该活动的所有模块的日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="5fa59-137">The log severity setting specified at the activity level determines the log severity setting of all the modules that constitute the activity.</span></span> <span data-ttu-id="5fa59-138">但是，如果在活动级别和模块级别上的日志严重性设置之间存在任何冲突，则应考虑模块级别的严重性设置。</span><span class="sxs-lookup"><span data-stu-id="5fa59-138">However, if there is any conflict between the log severity settings at the activity and module levels, the severity settings at the module level are considered.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="5fa59-139">默认情况下，在 **“高级”** 部分中预先配置 **Microsoft.Ssdqs.Core.Startup** ，并且严重级别设置为 **“信息”**。</span><span class="sxs-lookup"><span data-stu-id="5fa59-139">By default, the **Microsoft.Ssdqs.Core.Startup** module is preconfigured in the **Advanced** section with the severity level set as **Info**.</span></span> <span data-ttu-id="5fa59-140">这样可使与启动和停止 DQS 服务相关的严重级别为“信息”和更高（“警告”、“错误”和“严重”）的事件记入日志。</span><span class="sxs-lookup"><span data-stu-id="5fa59-140">This is done to enable logging of events of severity Info and higher (Warn, Error, and Fatal) that are related to starting and stopping of DQS services.</span></span>  
> -   <span data-ttu-id="5fa59-141">只有在您是熟悉 DQS 系统程序集的高级 DQS 用户的情况下，才应在模块级别配置日志严重级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-141">You should configure log severity levels at the module level only if you are an advanced DQS user who is familiar with the DQS system assemblies.</span></span>  
  
 <span data-ttu-id="5fa59-142">在模块级别配置日志严重级别：</span><span class="sxs-lookup"><span data-stu-id="5fa59-142">To configure log severity levels at the module level:</span></span>  
  
1.  <span data-ttu-id="5fa59-143">在 **“日志设置”** 选项卡上，单击针对 **“高级”** 的向下箭头以便显示该区域。</span><span class="sxs-lookup"><span data-stu-id="5fa59-143">In the **Log Settings** tab, click the down arrow against **Advanced** to display the area.</span></span>  
  
2.  <span data-ttu-id="5fa59-144">在出现的网格中，在 **“模块”** 列的下拉列表中选择某一模块名称。</span><span class="sxs-lookup"><span data-stu-id="5fa59-144">In the grid that appears, select a module name from the drop-down list in the **Module** column.</span></span>  
  
3.  <span data-ttu-id="5fa59-145">接下来，从 **“严重性”** 列的下拉列表中选择该模块的严重级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-145">Next, select a severity level for the module from the drop-down list in the **Severity** column.</span></span> <span data-ttu-id="5fa59-146">您可以选择下列级别之一： **“严重”**、 **“错误”**、 **“警告”**、 **“信息”** 和 **“调试”**。</span><span class="sxs-lookup"><span data-stu-id="5fa59-146">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span>  
  
     <span data-ttu-id="5fa59-147">例如，在域管理活动内，您可以通过选择 **Microsoft.Ssdqs.DomainRules.Define** 模块，然后选择不同的日志严重级别，为域规则定义功能设置与域管理活动不同的粒度级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-147">For example, within the domain management activity, you can set a different granularity level for the domain rule definition functionality than the domain management activity by selecting the **Microsoft.Ssdqs.DomainRules.Define** module, and selecting a different log severity level.</span></span> <span data-ttu-id="5fa59-148">类似地，您可以通过选择 **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** 模块，然后选择不同的日志严重级别，为跨域规则定义功能设置不同的粒度级别。</span><span class="sxs-lookup"><span data-stu-id="5fa59-148">Similarly, you can set a different granularity level for the cross-domain rule functionality by selecting the **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** module, and selecting a different log severity level.</span></span>  
  
4.  <span data-ttu-id="5fa59-149">如果需要，为其他模块重复步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="5fa59-149">Repeat steps 2 and 3 for other modules, if required.</span></span> <span data-ttu-id="5fa59-150">您还可以通过单击 **“添加模块”** 和 **“删除模块”** 图标，向网格中添加或删除行。</span><span class="sxs-lookup"><span data-stu-id="5fa59-150">You can also add or delete rows to the grid by clicking the **Add Module** and **Remove Module** icons.</span></span>  
  
5.  <span data-ttu-id="5fa59-151">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="5fa59-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa59-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fa59-152">See Also</span></span>  
 [<span data-ttu-id="5fa59-153">为 DQS 日志文件配置高级设置</span><span class="sxs-lookup"><span data-stu-id="5fa59-153">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
