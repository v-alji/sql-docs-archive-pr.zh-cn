---
title: 资源调控器工作负荷组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c6fa8f6fe960571f10d6a8505329fbe8f400e6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689303"
---
# <a name="resource-governor-workload-group"></a><span data-ttu-id="1f3d8-102">资源调控器工作负荷组</span><span class="sxs-lookup"><span data-stu-id="1f3d8-102">Resource Governor Workload Group</span></span>
  <span data-ttu-id="1f3d8-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源调控器中，工作负荷组充当具有相似分类标准的会话请求的容器。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-103">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor, a workload group serves as a container for session requests that have similar classification criteria.</span></span> <span data-ttu-id="1f3d8-104">工作负荷允许对会话进行聚合监视，并定义会话的策略。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-104">A workload allows for aggregate monitoring of the sessions, and defines policies for the sessions.</span></span> <span data-ttu-id="1f3d8-105">每个工作负荷组均位于一个资源池中，它表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的部分物理资源。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-105">Each workload group is in a resource pool, which represents a subset of the physical resources of an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="1f3d8-106">在某个会话启动时，资源调控器分类器会将此会话分配给一个特定的工作负荷组，并且此会话必须使用分配给该工作负荷组的策略和为资源池定义的资源运行。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-106">When a session is started, the Resource Governor classifier assigns the session to a specific workload group, and the session must run using the policies assigned to the workload group and the resources defined for the resource pool.</span></span>  
  
## <a name="workload-group-concepts"></a><span data-ttu-id="1f3d8-107">工作负荷组概念</span><span class="sxs-lookup"><span data-stu-id="1f3d8-107">Workload Group Concepts</span></span>  
 <span data-ttu-id="1f3d8-108">工作负荷组是会话请求的容器，根据应用于每个请求的分类标准这些会话被认为是相似的。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-108">A workload group serves as a container for session requests that are similar according to the classification criteria that are applied to each request.</span></span> <span data-ttu-id="1f3d8-109">利用工作负荷组可对资源占用进行聚合监视并可将统一策略应用至组中的所有请求。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-109">A workload group allows the aggregate monitoring of resource consumption and the application of a uniform policy to all the requests in the group.</span></span> <span data-ttu-id="1f3d8-110">组为其成员定义策略。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-110">A group defines the policies for its members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f3d8-111">用户定义的工作负荷组可以从一个资源池移动到另一个资源池。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-111">User-defined workload groups can be moved from one resource pool to another.</span></span>  
  
 <span data-ttu-id="1f3d8-112">资源调控器预定义了两个工作负荷组：内部组和默认组。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-112">Resource Governor predefines two workload groups: the internal group and the default group.</span></span> <span data-ttu-id="1f3d8-113">用户无法更改任何已归入内部组类的请求，但可以对其进行监视。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-113">A user cannot change anything classified as an internal group, but can monitor it.</span></span> <span data-ttu-id="1f3d8-114">当满足下列条件时，请求会被归入默认组类：</span><span class="sxs-lookup"><span data-stu-id="1f3d8-114">Requests are classified into the default group when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="1f3d8-115">没有用于对请求进行分类的标准。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-115">There are no criteria to classify a request.</span></span>  
  
-   <span data-ttu-id="1f3d8-116">曾经尝试将请求归入不存在的组类。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-116">There is an attempt to classify the request into a non-existent group.</span></span>  
  
-   <span data-ttu-id="1f3d8-117">存在常规性的分类错误。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-117">There is a general classification failure.</span></span>  
  
 <span data-ttu-id="1f3d8-118">资源调控器还提供了用于创建、更改和删除工作负荷组的 DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-118">Resource Governor also provides DDL statements for creating, changing, and dropping workload groups.</span></span>  
  
## <a name="workload-group-tasks"></a><span data-ttu-id="1f3d8-119">工作负荷组任务</span><span class="sxs-lookup"><span data-stu-id="1f3d8-119">Workload Group Tasks</span></span>  
  
|<span data-ttu-id="1f3d8-120">任务说明</span><span class="sxs-lookup"><span data-stu-id="1f3d8-120">Task Description</span></span>|<span data-ttu-id="1f3d8-121">主题</span><span class="sxs-lookup"><span data-stu-id="1f3d8-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1f3d8-122">说明如何创建工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-122">Describes how to create a workload group.</span></span>|[<span data-ttu-id="1f3d8-123">创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="1f3d8-123">Create a Workload Group</span></span>](create-a-workload-group.md)|  
|<span data-ttu-id="1f3d8-124">说明如何更改工作负荷组设置。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-124">Describes how to change workload group settings.</span></span>|[<span data-ttu-id="1f3d8-125">更改工作负荷组设置</span><span class="sxs-lookup"><span data-stu-id="1f3d8-125">Change Workload Group Settings</span></span>](change-workload-group-settings.md)|  
|<span data-ttu-id="1f3d8-126">说明如何删除工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="1f3d8-126">Describes how to delete a workload group.</span></span>|[<span data-ttu-id="1f3d8-127">删除工作负荷组</span><span class="sxs-lookup"><span data-stu-id="1f3d8-127">Delete a Workload Group</span></span>](delete-a-workload-group.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1f3d8-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f3d8-128">See Also</span></span>  
 <span data-ttu-id="1f3d8-129">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1f3d8-129">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="1f3d8-130">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1f3d8-130">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="1f3d8-131">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="1f3d8-131">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="1f3d8-132">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="1f3d8-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="1f3d8-133">[使用模板配置资源调控器](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="1f3d8-133">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="1f3d8-134">查看资源调控器属性</span><span class="sxs-lookup"><span data-stu-id="1f3d8-134">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
