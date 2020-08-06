---
title: 指定第一个和最后一个触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- first triggers [SQL Server]
- last triggers
- DML triggers, first or last triggers
- INSTEAD OF triggers
- AFTER triggers
ms.assetid: 9e6c7684-3dd3-46bb-b7be-523b33fae4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddb352b00dc759362c8f6ef1e861e55b6f184f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590613"
---
# <a name="specify-first-and-last-triggers"></a><span data-ttu-id="bd48f-102">指定第一个和最后一个触发器</span><span class="sxs-lookup"><span data-stu-id="bd48f-102">Specify First and Last Triggers</span></span>
  <span data-ttu-id="bd48f-103">可将与表关联的 AFTER 触发器之一指定为执行每个 INSERT、DELETE 和 UPDATE 触发操作时激发的第一个或最后一个 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-103">You can specify that one of the AFTER triggers associated with a table be either the first AFTER trigger or the last AFTER trigger that is fired for each INSERT, DELETE, and UPDATE triggering actions.</span></span> <span data-ttu-id="bd48f-104">在第一个和最后一个触发器之间激发的 AFTER 触发器将按未定义的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="bd48f-104">The AFTER triggers that are fired between the first and last triggers are executed in undefined order.</span></span>  
  
 <span data-ttu-id="bd48f-105">若要指定 AFTER 触发器的顺序，请使用 **sp_settriggerorder** 存储过程。</span><span class="sxs-lookup"><span data-stu-id="bd48f-105">To specify the order for an AFTER trigger, use the **sp_settriggerorder** stored procedure.</span></span> <span data-ttu-id="bd48f-106">**sp_settriggerorder** 有下列选项。</span><span class="sxs-lookup"><span data-stu-id="bd48f-106">**sp_settriggerorder** has the following options.</span></span>  
  
|<span data-ttu-id="bd48f-107">选项</span><span class="sxs-lookup"><span data-stu-id="bd48f-107">Option</span></span>|<span data-ttu-id="bd48f-108">说明</span><span class="sxs-lookup"><span data-stu-id="bd48f-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bd48f-109">**第一个**</span><span class="sxs-lookup"><span data-stu-id="bd48f-109">**First**</span></span>|<span data-ttu-id="bd48f-110">指定 DML 触发器是执行触发操作时激发的第一个 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-110">Specifies that the DML trigger is the first AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="bd48f-111">**上一次**</span><span class="sxs-lookup"><span data-stu-id="bd48f-111">**Last**</span></span>|<span data-ttu-id="bd48f-112">指定 DML 触发器是执行触发操作时激发的最后一个 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-112">Specifies that the DML trigger is the last AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="bd48f-113">无 </span><span class="sxs-lookup"><span data-stu-id="bd48f-113">**None**</span></span>|<span data-ttu-id="bd48f-114">指定不按特定的顺序激发 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-114">Specifies that there is no specific order in which the DML trigger should be fired.</span></span> <span data-ttu-id="bd48f-115">主要用于将某个触发器重置为第一个或最后一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-115">Used mainly to reset a trigger from being either first or last.</span></span>|  
  
 <span data-ttu-id="bd48f-116">以下示例说明如何使用 **sp_settriggerorder**：</span><span class="sxs-lookup"><span data-stu-id="bd48f-116">The following example shows using **sp_settriggerorder**:</span></span>  
  
```  
sp_settriggerorder @triggername = 'MyTrigger', @order = 'first', @stmttype = 'UPDATE'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd48f-117">第一个和最后一个触发器必须是两个不同的 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-117">The first and last triggers must be two different DML triggers.</span></span>  
  
 <span data-ttu-id="bd48f-118">可以同时为表定义 INSERT、UPDATE 和 DELETE 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-118">A table can have INSERT, UPDATE, and DELETE triggers defined on it at the same time.</span></span> <span data-ttu-id="bd48f-119">每个语句类型都可以有其自己的第一个和最后一个触发器，但它们不能是相同的触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-119">Each statement type can have its own first and last triggers, but they cannot be the same triggers.</span></span>  
  
 <span data-ttu-id="bd48f-120">如果为某个表定义的第一个或最后一个触发器不包括触发操作，如 FOR UPDATE、FOR DELETE 或 FOR INSERT，则缺少的操作将没有第一个或最后一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-120">If the first or last trigger defined for a table does not cover a triggering action, such as not covering FOR UPDATE, FOR DELETE, or FOR INSERT, there is no first or last trigger for the missing actions.</span></span>  
  
 <span data-ttu-id="bd48f-121">不能将 INSTEAD OF 触发器指定为第一个或最后一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-121">INSTEAD OF triggers cannot be specified as first or last triggers.</span></span> <span data-ttu-id="bd48f-122">在对基础表进行更新前激发 INSTEAD OF 触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-122">INSTEAD OF triggers are fired before updates are made to the underlying tables.</span></span> <span data-ttu-id="bd48f-123">如果由 INSTEAD OF 触发器对基础表进行更新，这些更新将在激发为表定义的任何 AFTER 触发器之前发生。</span><span class="sxs-lookup"><span data-stu-id="bd48f-123">If updates are made by an INSTEAD OF trigger to underlying tables, the updates occur before any AFTER triggers defined on the table are fired.</span></span> <span data-ttu-id="bd48f-124">例如，如果视图上的一个 INSTEAD OF INSERT 触发器将数据插入某个基表，而基表本身包含一个 INSTEAD OF INSERT 触发器和三个 AFTER INSERT 触发器，则会激发基表上的 INSTEAD OF INSERT 触发器而不发生插入操作，而基表上 AFTER 触发器将在执行所有插入操作后激发。</span><span class="sxs-lookup"><span data-stu-id="bd48f-124">For example, if an INSTEAD OF INSERT trigger on a view inserts data into a base table and the base table itself contains an INSTEAD OF INSERT trigger and three AFTER INSERT triggers, the INSTEAD OF INSERT trigger on the base table is fired instead of the inserting action, and the AFTER triggers on the base table are fired after any inserting action on the base table.</span></span> <span data-ttu-id="bd48f-125">有关详细信息，请参阅 [DML Triggers](dml-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="bd48f-125">For more information, see [DML Triggers](dml-triggers.md).</span></span>  
  
 <span data-ttu-id="bd48f-126">如果 ALTER TRIGGER 语句更改了第一个或最后一个触发器，则会删除 **First** 或 **Last** 属性并将顺序值设置为 **None**。</span><span class="sxs-lookup"><span data-stu-id="bd48f-126">If an ALTER TRIGGER statement changes a first or last trigger, the **First** or **Last** attribute is dropped and the order value is set to **None**.</span></span> <span data-ttu-id="bd48f-127">必须使用 **sp_settriggerorder**来重置顺序。</span><span class="sxs-lookup"><span data-stu-id="bd48f-127">The order must be reset by using **sp_settriggerorder**.</span></span>  
  
 <span data-ttu-id="bd48f-128">OBJECTPROPERTY 函数使用属性 **ExecIsFirstTrigger** 和 **ExecIsLastTrigger**来报告某个触发器是第一个还是最后一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-128">The OBJECTPROPERTY function reports whether a trigger is a first or last trigger by using the properties **ExecIsFirstTrigger** and **ExecIsLastTrigger**.</span></span>  
  
 <span data-ttu-id="bd48f-129">复制将为包含在立即更新订阅或排队更新订阅中的任意表自动生成第一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-129">Replication automatically generates a first trigger for any table that is included in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="bd48f-130">复制要求其触发器为第一个触发器。</span><span class="sxs-lookup"><span data-stu-id="bd48f-130">Replication requires that its trigger be the first trigger.</span></span> <span data-ttu-id="bd48f-131">在尝试将带有第一个触发器的表包含在立即更新订阅或排队更新订阅中时，复制将引发错误。</span><span class="sxs-lookup"><span data-stu-id="bd48f-131">Replication raises an error when you try to include a table with a first trigger in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="bd48f-132">如果在表已经包含在订阅中之后尝试使某个触发器成为第一个触发器， **sp_settriggerorder** 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="bd48f-132">If you try to make a trigger a first trigger after a table has been included in a subscription, **sp_settriggerorder** returns an error.</span></span> <span data-ttu-id="bd48f-133">如果在复制触发器上使用 ALTER，或使用 **sp_settriggerorder** 将复制触发器更改为最后一个触发器或无触发器，订阅将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="bd48f-133">If you use ALTER on the replication trigger or use **sp_settriggerorder** to change the replication trigger to a last or none trigger, the subscription will not function correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd48f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd48f-134">See Also</span></span>  
 <span data-ttu-id="bd48f-135">[OBJECTPROPERTY (Transact-SQL)](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd48f-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="bd48f-136">sp_settriggerorder (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bd48f-136">sp_settriggerorder &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql)  
  
  
