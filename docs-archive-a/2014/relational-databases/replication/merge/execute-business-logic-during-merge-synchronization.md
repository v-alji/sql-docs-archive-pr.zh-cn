---
title: 在合并同步期间执行业务逻辑 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom error resolution [SQL Server replication]
- custom change handling [SQL Server replication]
- errors [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1e082cbbb46ceae712cd39925c28fe89988a3793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576698"
---
# <a name="execute-business-logic-during-merge-synchronization"></a><span data-ttu-id="514c5-102">在合并同步期间执行业务逻辑</span><span class="sxs-lookup"><span data-stu-id="514c5-102">Execute Business Logic During Merge Synchronization</span></span>
  <span data-ttu-id="514c5-103">通过使用业务逻辑处理程序框架，您可以编写合并同步过程中调用的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="514c5-103">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="514c5-104">程序集包括可以响应同步过程中的许多状况的业务逻辑：数据更改、冲突和错误。</span><span class="sxs-lookup"><span data-stu-id="514c5-104">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="514c5-105">业务逻辑处理程序框架提供了一个简单的编程模型，且合并进程提供给程序集的数据的形式是 ADO.NET 数据集，因此可以充分利用了解的 ADO.NET 知识，而不必学习专有接口。</span><span class="sxs-lookup"><span data-stu-id="514c5-105">The business logic handler framework provides a simple programming model, and the data that the merge process provides to your assembly is in the form of an ADO.NET data set, so you can leverage knowledge of ADO.NET rather than learning a proprietary interface.</span></span> <span data-ttu-id="514c5-106">有关如何对业务逻辑处理程序进行编程的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="514c5-106">For more information on programming business logic handlers, see:</span></span>  
  
-   <span data-ttu-id="514c5-107">应用程序编程接口 (API) 引用： <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span><span class="sxs-lookup"><span data-stu-id="514c5-107">The application programming interface (API) reference: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span></span>  
  
-   <span data-ttu-id="514c5-108">有关如何实现业务逻辑处理程序的说明：[实现合并项目的业务逻辑处理程序](../implement-a-business-logic-handler-for-a-merge-article.md)</span><span class="sxs-lookup"><span data-stu-id="514c5-108">Instructions on how to implement a business logic handler: [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md)</span></span>  
  
## <a name="uses-for-business-logic-handlers"></a><span data-ttu-id="514c5-109">业务逻辑处理程序用途</span><span class="sxs-lookup"><span data-stu-id="514c5-109">Uses for Business Logic Handlers</span></span>  
 <span data-ttu-id="514c5-110">合并同步进程可以调用业务逻辑处理程序来执行：</span><span class="sxs-lookup"><span data-stu-id="514c5-110">The merge synchronization process can invoke business logic handlers to perform:</span></span>  
  
-   <span data-ttu-id="514c5-111">自定义更改处理</span><span class="sxs-lookup"><span data-stu-id="514c5-111">Custom change handling</span></span>  
  
-   <span data-ttu-id="514c5-112">自定义冲突解决</span><span class="sxs-lookup"><span data-stu-id="514c5-112">Custom conflict resolution</span></span>  
  
-   <span data-ttu-id="514c5-113">自定义错误分析</span><span class="sxs-lookup"><span data-stu-id="514c5-113">Custom error resolution</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="514c5-114">指定的业务逻辑处理程序是针对每个同步的行来执行的，</span><span class="sxs-lookup"><span data-stu-id="514c5-114">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="514c5-115">因此复杂的逻辑以及对其他应用程序或网络服务的调用都可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="514c5-115">Complex logic and calls to other applications or network services can impact performance.</span></span>  
  
### <a name="custom-change-handling"></a><span data-ttu-id="514c5-116">自定义更改处理</span><span class="sxs-lookup"><span data-stu-id="514c5-116">Custom Change Handling</span></span>  
 <span data-ttu-id="514c5-117">在处理非冲突数据更改期间可以调用业务逻辑处理程序，它可以执行下列三种操作之一：</span><span class="sxs-lookup"><span data-stu-id="514c5-117">The business logic handler can be invoked during the processing of non-conflicting data changes and can perform one of three actions:</span></span>  
  
-   <span data-ttu-id="514c5-118">拒绝数据</span><span class="sxs-lookup"><span data-stu-id="514c5-118">Reject the data</span></span>  
  
     <span data-ttu-id="514c5-119">如果应用程序不希望在与给定订阅服务器之间传播更改，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-119">This is useful for applications that do not want changes propagated to or from a given Subscriber.</span></span> <span data-ttu-id="514c5-120">例如，管理员可能会筛选掉不属于订阅服务器分区中的插入操作，也可能拒绝订阅服务器上执行的删除操作。</span><span class="sxs-lookup"><span data-stu-id="514c5-120">For example, an administrator could filter out inserts that do not belong in the Subscriber's partition, or possibly reject deletes performed at a Subscriber.</span></span> <span data-ttu-id="514c5-121">再如，应用程序可能因库存已不再可用而拒绝订阅服务器上输入的订单。</span><span class="sxs-lookup"><span data-stu-id="514c5-121">As another example, an application could reject an order entered at a Subscriber because the inventory is no longer available.</span></span>  
  
-   <span data-ttu-id="514c5-122">接受数据</span><span class="sxs-lookup"><span data-stu-id="514c5-122">Accept the data</span></span>  
  
     <span data-ttu-id="514c5-123">如果应用程序需要先对发布服务器或订阅服务器上所做数据更改进行查看然后再进行传播，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-123">This is useful for applications in which it is necessary to review data changes made at either the Publisher or Subscriber before allowing them to be propagated.</span></span> <span data-ttu-id="514c5-124">例如，中间层应用程序可能检查从字段输入的新订单，然后与中间层的采购工作流进程集成。</span><span class="sxs-lookup"><span data-stu-id="514c5-124">For example, a mid-tier application could examine new orders coming in from the field and integrate with a procurement workflow process in the mid-tier.</span></span>  
  
-   <span data-ttu-id="514c5-125">应用自定义数据</span><span class="sxs-lookup"><span data-stu-id="514c5-125">Apply custom data</span></span>  
  
     <span data-ttu-id="514c5-126">如果应用程序需要覆盖特定数据值或操作，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-126">This is useful for applications that need to override specific data values or operations.</span></span> <span data-ttu-id="514c5-127">例如，应用程序可能将行删除操作转换为一个特殊的更新操作，将行中 **status** 列的值设置为“已删除”，然后跟踪执行删除操作的客户端的标识。</span><span class="sxs-lookup"><span data-stu-id="514c5-127">For example, an application could transform a row delete into a special update that sets a **status** column in the row to a value of "deleted" and then tracks the identity of the client performing the delete.</span></span> <span data-ttu-id="514c5-128">这对于审核或工作流可能比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-128">This might be useful for auditing or workflow purposes.</span></span>  
  
### <a name="custom-conflict-resolution"></a><span data-ttu-id="514c5-129">自定义冲突解决</span><span class="sxs-lookup"><span data-stu-id="514c5-129">Custom Conflict Resolution</span></span>  
 <span data-ttu-id="514c5-130">合并复制提供了冲突检测和冲突解决选项，从而允许针对冲突接受默认的解决策略或选择自定义解决。</span><span class="sxs-lookup"><span data-stu-id="514c5-130">Merge replication provides conflict detection and resolution, allowing you to accept a default resolution strategy or choose custom resolution for conflicts.</span></span> <span data-ttu-id="514c5-131">有关详细信息，请参阅 [高级合并复制冲突的检测和解决](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="514c5-131">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="514c5-132">在处理冲突数据更改期间可以调用业务逻辑处理程序，它可以执行下列两种操作之一：</span><span class="sxs-lookup"><span data-stu-id="514c5-132">The business logic handler can be invoked during the processing of conflicting data changes and can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="514c5-133">接受默认解决</span><span class="sxs-lookup"><span data-stu-id="514c5-133">Accept default resolution</span></span>  
  
     <span data-ttu-id="514c5-134">如果应用程序可能需要查看冲突、执行其他操作及可能记录自定义冲突日志消息，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-134">This is useful for applications that might need to review the conflict, perform additional actions, and possibly log a custom conflict log message.</span></span>  
  
-   <span data-ttu-id="514c5-135">执行自定义解决</span><span class="sxs-lookup"><span data-stu-id="514c5-135">Perform custom resolution</span></span>  
  
     <span data-ttu-id="514c5-136">如果应用程序可能需要选择特定于其业务逻辑的数据值，并需要为同步处理提供此自定义数据集，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-136">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="514c5-137">例如，应用程序可能通过合并来自发布服务器和订阅服务器数据集的值来提供新版本的入选行。</span><span class="sxs-lookup"><span data-stu-id="514c5-137">For example, an application could provide a new version of the winning row by combining values from the Publisher and Subscriber data sets.</span></span>  
  
### <a name="custom-error-resolution"></a><span data-ttu-id="514c5-138">自定义错误分析</span><span class="sxs-lookup"><span data-stu-id="514c5-138">Custom Error Resolution</span></span>  
 <span data-ttu-id="514c5-139">可以在传播导致出现错误的更改期间调用自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="514c5-139">Custom logic can be invoked during the propagation of changes that result in errors.</span></span> <span data-ttu-id="514c5-140">逻辑可以执行下列两种操作之一：</span><span class="sxs-lookup"><span data-stu-id="514c5-140">The logic can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="514c5-141">接受默认错误分析</span><span class="sxs-lookup"><span data-stu-id="514c5-141">Accept default error resolution</span></span>  
  
     <span data-ttu-id="514c5-142">如果应用程序可能需要查看错误、执行其他操作及可能记录自定义错误日志消息，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-142">This is useful for applications that might need to review the error and perform additional action and possibly log a custom error log message.</span></span>  
  
-   <span data-ttu-id="514c5-143">接受自定义错误分析</span><span class="sxs-lookup"><span data-stu-id="514c5-143">Accept custom error resolution</span></span>  
  
     <span data-ttu-id="514c5-144">如果应用程序可能需要选择特定于其业务逻辑的数据值，并需要为同步处理提供此自定义数据集，这比较有用。</span><span class="sxs-lookup"><span data-stu-id="514c5-144">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="514c5-145">例如，如果复制过程遇到重复键冲突，业务逻辑处理程序可提供新版本的数据更改，这样就不会再有键冲突。</span><span class="sxs-lookup"><span data-stu-id="514c5-145">For example, if the replication process encounters a duplicate key violation, the business logic handler could provide a new version of the data change in which the key will no longer conflict.</span></span> <span data-ttu-id="514c5-146">在发布服务器和订阅服务器上所做的更改就可以保留在数据库中，而复制过程也不必通过删除操作来弥补失败的插入操作。</span><span class="sxs-lookup"><span data-stu-id="514c5-146">Changes made at the Publisher and Subscriber can then persist in the database, and the replication process doesn't have to compensate for the failed insert with a delete.</span></span>  
  
## <a name="deployment-scenarios-for-business-logic-handlers"></a><span data-ttu-id="514c5-147">业务逻辑处理程序的部署方案</span><span class="sxs-lookup"><span data-stu-id="514c5-147">Deployment Scenarios for Business Logic Handlers</span></span>  
 <span data-ttu-id="514c5-148">可以将业务逻辑处理程序部署于：</span><span class="sxs-lookup"><span data-stu-id="514c5-148">Business logic handlers can be deployed at:</span></span>  
  
-   <span data-ttu-id="514c5-149">分发服务器。</span><span class="sxs-lookup"><span data-stu-id="514c5-149">The Distributor.</span></span> <span data-ttu-id="514c5-150">使用推送订阅，在分发服务器上执行业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="514c5-150">Use a push subscription so that business logic is executed at the Distributor.</span></span>  
  
-   <span data-ttu-id="514c5-151">订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="514c5-151">The Subscriber.</span></span> <span data-ttu-id="514c5-152">使用请求订阅，在订阅服务器上执行业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="514c5-152">Use a pull subscription so that business logic is executed at the Subscriber.</span></span>  
  
-   <span data-ttu-id="514c5-153">Internet 信息服务 (IIS) 服务器（如果使用 Web 同步）。</span><span class="sxs-lookup"><span data-stu-id="514c5-153">An Internet Information Services (IIS) server if Web synchronization is used.</span></span> <span data-ttu-id="514c5-154">使用通过 Web 同步来同步的请求订阅，在 IIS 服务器上执行业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="514c5-154">Use a pull subscription synchronized with Web synchronization, and the business logic handler will execute at the IIS Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514c5-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="514c5-155">See Also</span></span>  
 <span data-ttu-id="514c5-156">[合并复制](merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="514c5-156">[Merge Replication](merge-replication.md) </span></span>  
 <span data-ttu-id="514c5-157">[Subscribe to Publications](../subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="514c5-157">[Subscribe to Publications](../subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="514c5-158">[同步数据](../synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="514c5-158">[Synchronize Data](../synchronize-data.md) </span></span>  
 [<span data-ttu-id="514c5-159">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="514c5-159">Web Synchronization for Merge Replication</span></span>](../web-synchronization-for-merge-replication.md)  
  
  
