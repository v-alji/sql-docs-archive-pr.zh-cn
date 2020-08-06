---
title: 传输作业任务编辑器 (作业 "页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591951"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a><span data-ttu-id="a25a0-102">传输作业任务编辑器（“作业”页）</span><span class="sxs-lookup"><span data-stu-id="a25a0-102">Transfer Jobs Task Editor (Jobs Page)</span></span>
  <span data-ttu-id="a25a0-103">可以使用 **“传输作业任务编辑器”** 对话框的 **“作业”** 页，指定用于将一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例复制到另一个实例的属性。</span><span class="sxs-lookup"><span data-stu-id="a25a0-103">Use the **Jobs** page of the **Transfer Jobs Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="a25a0-104">有关传输作业任务的详细信息，请参阅 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a0-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a25a0-105">若要访问源服务器上的作业，用户必须至少是该服务器上 **SQLAgentUserRole** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a25a0-105">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role on the server.</span></span> <span data-ttu-id="a25a0-106">若要在目标服务器上成功创建作业，用户必须是 **sysadmin** 固定服务器角色或某个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a25a0-106">To successfully create jobs on the destination server, the user must be a member of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles.</span></span> <span data-ttu-id="a25a0-107">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理的固定数据库角色及其权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a0-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a25a0-108">选项</span><span class="sxs-lookup"><span data-stu-id="a25a0-108">Options</span></span>  
 <span data-ttu-id="a25a0-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="a25a0-109">**SourceConnection**</span></span>  
 <span data-ttu-id="a25a0-110">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="a25a0-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="a25a0-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="a25a0-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="a25a0-112">从列表中选择一个 SMO 连接管理器，或单击“\<New connection...>”以创建到目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="a25a0-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="a25a0-113">**TransferAllJobs**</span><span class="sxs-lookup"><span data-stu-id="a25a0-113">**TransferAllJobs**</span></span>  
 <span data-ttu-id="a25a0-114">选择该任务是应将全部的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业还是仅将指定的作业从源服务器复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="a25a0-114">Select whether the task should copy all or only the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from the source to the destination server.</span></span>  
  
 <span data-ttu-id="a25a0-115">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="a25a0-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a25a0-116">值</span><span class="sxs-lookup"><span data-stu-id="a25a0-116">Value</span></span>|<span data-ttu-id="a25a0-117">说明</span><span class="sxs-lookup"><span data-stu-id="a25a0-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a25a0-118">**True**</span><span class="sxs-lookup"><span data-stu-id="a25a0-118">**True**</span></span>|<span data-ttu-id="a25a0-119">复制所有作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-119">Copy all jobs.</span></span>|  
|<span data-ttu-id="a25a0-120">**False**</span><span class="sxs-lookup"><span data-stu-id="a25a0-120">**False**</span></span>|<span data-ttu-id="a25a0-121">仅复制指定的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-121">Copy only the specified jobs.</span></span>|  
  
 <span data-ttu-id="a25a0-122">**JobsList**</span><span class="sxs-lookup"><span data-stu-id="a25a0-122">**JobsList**</span></span>  
 <span data-ttu-id="a25a0-123">单击浏览按钮 (…)，选择要复制的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-123">Click the browse button **(...)** to select the jobs to copy.</span></span> <span data-ttu-id="a25a0-124">必须至少选择一个作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-124">At least one job must be selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a25a0-125">在选择要复制的作业前，请指定 **SourceConnection** 。</span><span class="sxs-lookup"><span data-stu-id="a25a0-125">Specify the **SourceConnection** before selecting jobs to copy.</span></span>  
  
 <span data-ttu-id="a25a0-126">在 **TransferAllJobs** 设置为 **True** 时， **JobsList**选项不可用。</span><span class="sxs-lookup"><span data-stu-id="a25a0-126">The **JobsList** option is unavailable when **TransferAllJobs** is set to **True**.</span></span>  
  
 <span data-ttu-id="a25a0-127">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="a25a0-127">**IfObjectExists**</span></span>  
 <span data-ttu-id="a25a0-128">选择该任务应如何处理在目标服务器上已存在的同名作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-128">Select how the task should handle jobs of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="a25a0-129">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="a25a0-129">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a25a0-130">值</span><span class="sxs-lookup"><span data-stu-id="a25a0-130">Value</span></span>|<span data-ttu-id="a25a0-131">说明</span><span class="sxs-lookup"><span data-stu-id="a25a0-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a25a0-132">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="a25a0-132">**FailTask**</span></span>|<span data-ttu-id="a25a0-133">如果目标服务器上已存在同名的作业，则任务失败。</span><span class="sxs-lookup"><span data-stu-id="a25a0-133">Task fails if jobs of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="a25a0-134">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="a25a0-134">**Overwrite**</span></span>|<span data-ttu-id="a25a0-135">任务将覆盖目标服务器上同名的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-135">Task overwrites jobs of the same name on the destination server.</span></span>|  
|<span data-ttu-id="a25a0-136">**Skip**</span><span class="sxs-lookup"><span data-stu-id="a25a0-136">**Skip**</span></span>|<span data-ttu-id="a25a0-137">任务将跳过目标服务器上存在的同名作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-137">Task skips jobs of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="a25a0-138">**EnableJobsAtDestination**</span><span class="sxs-lookup"><span data-stu-id="a25a0-138">**EnableJobsAtDestination**</span></span>  
 <span data-ttu-id="a25a0-139">选择是否应启用复制到目标服务器上的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-139">Select whether the jobs copied to the destination server should be enabled.</span></span>  
  
 <span data-ttu-id="a25a0-140">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="a25a0-140">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a25a0-141">值</span><span class="sxs-lookup"><span data-stu-id="a25a0-141">Value</span></span>|<span data-ttu-id="a25a0-142">说明</span><span class="sxs-lookup"><span data-stu-id="a25a0-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a25a0-143">**True**</span><span class="sxs-lookup"><span data-stu-id="a25a0-143">**True**</span></span>|<span data-ttu-id="a25a0-144">启用目标服务器上的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-144">Enable jobs on destination server.</span></span>|  
|<span data-ttu-id="a25a0-145">**False**</span><span class="sxs-lookup"><span data-stu-id="a25a0-145">**False**</span></span>|<span data-ttu-id="a25a0-146">禁用目标服务器上的作业。</span><span class="sxs-lookup"><span data-stu-id="a25a0-146">Disable jobs on destination server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a25a0-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a25a0-147">See Also</span></span>  
 <span data-ttu-id="a25a0-148">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a25a0-148">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a25a0-149">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a25a0-149">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="a25a0-150">[传输作业任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="a25a0-150">[Transfer Jobs Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="a25a0-151">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="a25a0-151">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="a25a0-152">SMO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="a25a0-152">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
