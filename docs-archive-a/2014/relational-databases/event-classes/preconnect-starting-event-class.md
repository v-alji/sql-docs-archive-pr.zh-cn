---
title: PreConnect:Starting 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b642d369c73cc144af31f835786613766045f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588508"
---
# <a name="preconnectstarting-event-class"></a><span data-ttu-id="c3956-102">PreConnect:Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="c3956-102">PreConnect:Starting Event Class</span></span>
  <span data-ttu-id="c3956-103">PreConnect:Starting事件类指示 LOGON 触发器或资源调控器分类器函数开始执行的时间。</span><span class="sxs-lookup"><span data-stu-id="c3956-103">The PreConnect:Starting event class indicates when a LOGON trigger or the Resource Governor classifier function starts execution.</span></span>  
  
## <a name="preconnectstarting-event-class-data-columns"></a><span data-ttu-id="c3956-104">PreConnect:Starting 事件类数据列</span><span class="sxs-lookup"><span data-stu-id="c3956-104">PreConnect:Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="c3956-105">数据列名称</span><span class="sxs-lookup"><span data-stu-id="c3956-105">Data column name</span></span>|<span data-ttu-id="c3956-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="c3956-106">Data type</span></span>|<span data-ttu-id="c3956-107">说明</span><span class="sxs-lookup"><span data-stu-id="c3956-107">Description</span></span>|<span data-ttu-id="c3956-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="c3956-108">Column ID</span></span>|<span data-ttu-id="c3956-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="c3956-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="c3956-110">EventClass</span><span class="sxs-lookup"><span data-stu-id="c3956-110">EventClass</span></span>|`int`|<span data-ttu-id="c3956-111">215</span><span class="sxs-lookup"><span data-stu-id="c3956-111">215</span></span>|<span data-ttu-id="c3956-112">27</span><span class="sxs-lookup"><span data-stu-id="c3956-112">27</span></span>|<span data-ttu-id="c3956-113">否</span><span class="sxs-lookup"><span data-stu-id="c3956-113">No</span></span>|  
|<span data-ttu-id="c3956-114">SPID</span><span class="sxs-lookup"><span data-stu-id="c3956-114">SPID</span></span>|`int`|<span data-ttu-id="c3956-115">激发此事件的服务器进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="c3956-115">The ID of server process that fires this event.</span></span>|<span data-ttu-id="c3956-116">12</span><span class="sxs-lookup"><span data-stu-id="c3956-116">12</span></span>|<span data-ttu-id="c3956-117">是</span><span class="sxs-lookup"><span data-stu-id="c3956-117">Yes</span></span>|  
|<span data-ttu-id="c3956-118">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="c3956-118">EventSubClass</span></span>|`int`|<span data-ttu-id="c3956-119">1 表示用户定义的分类器函数。</span><span class="sxs-lookup"><span data-stu-id="c3956-119">1 for the user-defined classifier function.</span></span>|<span data-ttu-id="c3956-120">21</span><span class="sxs-lookup"><span data-stu-id="c3956-120">21</span></span>|<span data-ttu-id="c3956-121">是</span><span class="sxs-lookup"><span data-stu-id="c3956-121">Yes</span></span>|  
|<span data-ttu-id="c3956-122">StartTime</span><span class="sxs-lookup"><span data-stu-id="c3956-122">StartTime</span></span>|`datetime`|<span data-ttu-id="c3956-123">用户定义的分类器函数开始时间。</span><span class="sxs-lookup"><span data-stu-id="c3956-123">The time when the user-defined classifier function starts.</span></span>|<span data-ttu-id="c3956-124">14</span><span class="sxs-lookup"><span data-stu-id="c3956-124">14</span></span>|<span data-ttu-id="c3956-125">是</span><span class="sxs-lookup"><span data-stu-id="c3956-125">Yes</span></span>|  
|<span data-ttu-id="c3956-126">ObjectID</span><span class="sxs-lookup"><span data-stu-id="c3956-126">ObjectID</span></span>|`int`|<span data-ttu-id="c3956-127">用户定义的分类器对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="c3956-127">The ID of the user-defined classifier object.</span></span>|<span data-ttu-id="c3956-128">22</span><span class="sxs-lookup"><span data-stu-id="c3956-128">22</span></span>|<span data-ttu-id="c3956-129">是</span><span class="sxs-lookup"><span data-stu-id="c3956-129">Yes</span></span>|  
|<span data-ttu-id="c3956-130">ObjectName</span><span class="sxs-lookup"><span data-stu-id="c3956-130">ObjectName</span></span>|`nvarchar(256)`|<span data-ttu-id="c3956-131">用户定义的分类器函数的两部分名称。</span><span class="sxs-lookup"><span data-stu-id="c3956-131">The two-part name of the classifier user-defined function.</span></span> <span data-ttu-id="c3956-132">例如，dbo.classifier。</span><span class="sxs-lookup"><span data-stu-id="c3956-132">For example, dbo.classifier.</span></span>|<span data-ttu-id="c3956-133">34</span><span class="sxs-lookup"><span data-stu-id="c3956-133">34</span></span>|<span data-ttu-id="c3956-134">是</span><span class="sxs-lookup"><span data-stu-id="c3956-134">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3956-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3956-135">See Also</span></span>  
 <span data-ttu-id="c3956-136">[扩展事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="c3956-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="c3956-137">[PreConnect： Completed 事件类](preconnect-completed-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="c3956-137">[PreConnect:Completed Event Class](preconnect-completed-event-class.md) </span></span>  
 [<span data-ttu-id="c3956-138">资源调控器</span><span class="sxs-lookup"><span data-stu-id="c3956-138">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
