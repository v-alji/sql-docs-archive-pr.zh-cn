---
title: 指定如何传播事务项目的更改 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
ms.assetid: a10c5001-22cc-4667-8f0b-3d0818dca2e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72d377ba89f1d393eab48bd9c918012b0f503f9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689324"
---
# <a name="specify-how-changes-are-propagated-for-transactional-articles"></a><span data-ttu-id="00ae2-102">指定如何传播事务项目的更改</span><span class="sxs-lookup"><span data-stu-id="00ae2-102">Specify How Changes Are Propagated for Transactional Articles</span></span>
  <span data-ttu-id="00ae2-103">通过使用事务复制，可以指定如何将数据更改从发布服务器传播到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="00ae2-103">Transactional replication allows you to specify how data changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="00ae2-104">对于每个已发布表，可以指定下列四种方法之一，将每项操作（INSERT、UPDATE 或 DELETE）传播到订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="00ae2-104">For each published table, you can specify one of four ways that each operation (INSERT, UPDATE, or DELETE) should be propagated to the Subscriber:</span></span>  
  
-   <span data-ttu-id="00ae2-105">指定事务复制应编写出脚本，并随后调用存储过程以将更改传播到订阅服务器（默认方法）。</span><span class="sxs-lookup"><span data-stu-id="00ae2-105">Specify that transactional replication should script out and subsequently call a stored procedure to propagate changes to Subscribers (the default).</span></span>  
  
-   <span data-ttu-id="00ae2-106">指定使用 INSERT、UPDATE 或 DELETE 语句传播更改（对于非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器的默认方法）。</span><span class="sxs-lookup"><span data-stu-id="00ae2-106">Specify that the change should be propagated using an INSERT, UPDATE, or DELETE statement (the default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers).</span></span>  
  
-   <span data-ttu-id="00ae2-107">指定应使用自定义存储过程。</span><span class="sxs-lookup"><span data-stu-id="00ae2-107">Specify that a custom stored procedure should be used.</span></span>  
  
-   <span data-ttu-id="00ae2-108">指定不应在任何订阅服务器上执行此操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-108">Specify that this action should not be performed at any Subscriber.</span></span> <span data-ttu-id="00ae2-109">不复制这种类型的事务。</span><span class="sxs-lookup"><span data-stu-id="00ae2-109">Transactions of that type are not replicated.</span></span>  
  
 <span data-ttu-id="00ae2-110">默认情况下，事务复制通过安装在每个订阅服务器上的一组存储过程，将更改传播到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="00ae2-110">By default, transactional replication propagates changes to Subscribers through a set of stored procedures that are installed on each Subscriber.</span></span> <span data-ttu-id="00ae2-111">当发布服务器的表上出现插入、更新或删除操作时，该操作转换为调用订阅服务器上的存储过程。</span><span class="sxs-lookup"><span data-stu-id="00ae2-111">When an insert, update or delete occurs on a table at the Publisher, the operation is translated into a call to a stored procedure at the Subscriber.</span></span> <span data-ttu-id="00ae2-112">存储过程接受映射到表中列的参数，从而可以在订阅服务器上对这些列进行更改。</span><span class="sxs-lookup"><span data-stu-id="00ae2-112">The stored procedure accepts parameters that map to the columns in the table, allowing those columns to be changed at the Subscriber.</span></span>  
  
 <span data-ttu-id="00ae2-113">若要为事务项目的数据更改设置传播方法，请参阅 [为事务项目的数据更改设置传播方法](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="00ae2-113">To set the propagation method for data changes to transactional articles, see [Set the Propagation Method for Data Changes to Transactional Articles](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md).</span></span>  
  
## <a name="default-and-custom-stored-procedures"></a><span data-ttu-id="00ae2-114">默认和自定义存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-114">Default and custom stored procedures</span></span>  
 <span data-ttu-id="00ae2-115">默认情况下，复制为每个表项目创建的三个过程为：</span><span class="sxs-lookup"><span data-stu-id="00ae2-115">The three procedures that replication creates by default for each table article are:</span></span>  
  
-   <span data-ttu-id="00ae2-116">sp_MSins_\<** *tablename* **>，用于处理插入。</span><span class="sxs-lookup"><span data-stu-id="00ae2-116">**sp_MSins_\<** *tablename* **>**, which handles inserts.</span></span>  
  
-   <span data-ttu-id="00ae2-117">sp_MSupd_\<** *tablename* **>，用于处理更新。</span><span class="sxs-lookup"><span data-stu-id="00ae2-117">**sp_MSupd_\<** *tablename* **>**, which handles updates.</span></span>  
  
-   <span data-ttu-id="00ae2-118">sp_MSdel_\<** *tablename* **>，用于处理删除。</span><span class="sxs-lookup"><span data-stu-id="00ae2-118">**sp_MSdel_\<** *tablename* **>**, which handles deletes.</span></span>  
  
 <span data-ttu-id="00ae2-119">过程中使用的 \<***tablename***> 取决于如何将项目添加到发布中，以及订阅数据库是否包含名称相同但所有者不同的表。</span><span class="sxs-lookup"><span data-stu-id="00ae2-119">The **\<***tablename***>** used in the procedure depends on how the article was added to the publication and whether the subscription database contains a table of the same name with a different owner.</span></span>  
  
 <span data-ttu-id="00ae2-120">所有这些过程都可以替换为在将项目添加到发布中时指定的自定义过程。</span><span class="sxs-lookup"><span data-stu-id="00ae2-120">Any of these procedures can be replaced with a custom procedure that you specify when adding an article to a publication.</span></span> <span data-ttu-id="00ae2-121">自定义过程用于应用程序需要自定义逻辑的情况，例如在订阅服务器上更新行时将数据插入审核表。</span><span class="sxs-lookup"><span data-stu-id="00ae2-121">Custom procedures are used if an application requires custom logic, such as inserting data into an audit table when a row is updated at a Subscriber.</span></span> <span data-ttu-id="00ae2-122">有关指定自定义存储过程的详细信息，请参阅上面列出的“如何”主题。</span><span class="sxs-lookup"><span data-stu-id="00ae2-122">For more information about specifying custom stored procedures, see the how to topics listed above.</span></span>  
  
 <span data-ttu-id="00ae2-123">如果指定默认复制过程或自定义过程，还要为每个过程指定调用语法（如果使用默认过程，则复制选择默认语法）。</span><span class="sxs-lookup"><span data-stu-id="00ae2-123">If you specify the default replication procedures or custom procedures, you also specify call syntax for each procedure (replication selects defaults if you use the default procedures).</span></span> <span data-ttu-id="00ae2-124">调用语法确定提供给过程的参数的结构以及对于每次数据更改向订阅服务器发送多少信息。</span><span class="sxs-lookup"><span data-stu-id="00ae2-124">The call syntax determines the structure of the parameters provided to the procedure and how much information is sent to the Subscriber with each data change.</span></span> <span data-ttu-id="00ae2-125">有关详细信息，请参阅本主题中的“存储过程的调用语法”部分。</span><span class="sxs-lookup"><span data-stu-id="00ae2-125">For more information, see the section "Call Syntax for Stored Procedures" in this topic.</span></span>  
  
### <a name="considerations-for-using-custom-stored-procedures"></a><span data-ttu-id="00ae2-126">使用自定义存储过程的注意事项</span><span class="sxs-lookup"><span data-stu-id="00ae2-126">Considerations for Using Custom Stored Procedures</span></span>  
 <span data-ttu-id="00ae2-127">请在使用自定义存储过程时注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="00ae2-127">Keep the following considerations in mind when using custom stored procedures:</span></span>  
  
-   <span data-ttu-id="00ae2-128">必须支持存储过程中的逻辑； [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 不支持自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="00ae2-128">You must support the logic in the stored procedure; [!INCLUDE[msCoName](../../../includes/msconame-md.md)] does not provide support for custom logic.</span></span>  
  
-   <span data-ttu-id="00ae2-129">为了避免与复制所用的事务产生冲突，不应在自定义过程中使用显式事务。</span><span class="sxs-lookup"><span data-stu-id="00ae2-129">In order to avoid conflicts with the transactions used by replication, explicit transactions should not be used in custom procedures.</span></span>  
  
-   <span data-ttu-id="00ae2-130">订阅服务器的架构通常与发布服务器的架构相同，但如果使用了列筛选，则订阅服务器的架构也可以是发布服务器架构的子集。</span><span class="sxs-lookup"><span data-stu-id="00ae2-130">The schema at the Subscriber is typically identical to the schema at the Publisher, but can also be a subset of the Publisher schema if column filtering is used.</span></span> <span data-ttu-id="00ae2-131">但是，如果需要在移动数据时转换架构以使订阅服务器架构不是发布服务器架构的子集，则建议使用 [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] 这种解决方案。</span><span class="sxs-lookup"><span data-stu-id="00ae2-131">However, if you need to transform the schema as the data is moved such that the schema on the Subscriber is not a subset of the schema on the Publisher, [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] is the recommended solution.</span></span> <span data-ttu-id="00ae2-132">有关详细信息，请参阅 [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="00ae2-132">For more information, see [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md).</span></span>  
  
-   <span data-ttu-id="00ae2-133">如果对已发布表进行架构更改，则必须重新生成自定义过程。</span><span class="sxs-lookup"><span data-stu-id="00ae2-133">If you make schema changes to a published table, the custom procedures must be regenerated.</span></span> <span data-ttu-id="00ae2-134">有关详细信息，请参阅[重新生成自定义事务过程以反映架构更改](transactional-articles-regenerate-to-reflect-schema-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="00ae2-134">For more information, see [Regenerate Custom Transactional Procedures to Reflect Schema Changes](transactional-articles-regenerate-to-reflect-schema-changes.md).</span></span>  
  
-   <span data-ttu-id="00ae2-135">如果将大于 1 的值用于分发代理的 **-SubscriptionStreams** 参数，则必须确保成功更新主键列。</span><span class="sxs-lookup"><span data-stu-id="00ae2-135">If you use a value greater than 1 for **-SubscriptionStreams** parameter of the Distribution Agent, you must ensure that updates to primary key columns are successful.</span></span> <span data-ttu-id="00ae2-136">例如：</span><span class="sxs-lookup"><span data-stu-id="00ae2-136">For example:</span></span>  
  
    ```  
    update ... set pk = 2 where pk = 1 -- update 1  
    update ... set pk = 3 where pk = 2 -- update 2  
    ```  
  
     <span data-ttu-id="00ae2-137">如果分发代理使用多个连接，则这两次更新可能会通过不同连接进行复制。</span><span class="sxs-lookup"><span data-stu-id="00ae2-137">If the Distribution Agent uses more than one connection, these two updates might be replicated over different connections.</span></span> <span data-ttu-id="00ae2-138">如果首先应用更新 1，则不会出现问题；如果首先应用更新 2，就会由于更新 1 尚未执行而返回“0 行受影响”。</span><span class="sxs-lookup"><span data-stu-id="00ae2-138">If update 1 is applied first, there is no problem; if update 2 is applied first it will return '0 rows affected' because update 1 has not yet occurred.</span></span> <span data-ttu-id="00ae2-139">在默认程序中，这种情况的处理方法是：如果更新未影响任何行，则产生一个错误：</span><span class="sxs-lookup"><span data-stu-id="00ae2-139">This situation is handled in the default procedures by raising an error if no rows are affected on an update:</span></span>  
  
    ```  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sys.sp_MSreplraiserror 20598  
    ```  
  
     <span data-ttu-id="00ae2-140">产生错误后，会强制分发代理通过单连接重试更新，这样更新就会成功。</span><span class="sxs-lookup"><span data-stu-id="00ae2-140">Raising the error forces the Distribution Agent to retry the updates over a single connection, which will succeed.</span></span> <span data-ttu-id="00ae2-141">自定义存储过程必须包括相似的逻辑。</span><span class="sxs-lookup"><span data-stu-id="00ae2-141">Custom stored procedures must include similar logic.</span></span>  
  
### <a name="call-syntax-for-stored-procedures"></a><span data-ttu-id="00ae2-142">存储过程的调用语法</span><span class="sxs-lookup"><span data-stu-id="00ae2-142">Call syntax for stored procedures</span></span>  
 <span data-ttu-id="00ae2-143">用于调用事务复制所用过程的语法有五种：</span><span class="sxs-lookup"><span data-stu-id="00ae2-143">There are five options for the syntax used to call the procedures used by transactional replication:</span></span>  
  
-   <span data-ttu-id="00ae2-144">CALL 语法。</span><span class="sxs-lookup"><span data-stu-id="00ae2-144">CALL syntax.</span></span> <span data-ttu-id="00ae2-145">可用于插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-145">Can be used for inserts, updates, and deletes.</span></span> <span data-ttu-id="00ae2-146">默认情况下，复制将此语法用于插入和删除操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-146">By default, replication uses this syntax for inserts and deletes.</span></span>  
  
-   <span data-ttu-id="00ae2-147">SCALL 语法。</span><span class="sxs-lookup"><span data-stu-id="00ae2-147">SCALL syntax.</span></span> <span data-ttu-id="00ae2-148">只能用于更新操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-148">Can be used for updates only.</span></span> <span data-ttu-id="00ae2-149">默认情况下，复制将此语法用于更新操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-149">By default, replication uses this syntax for updates.</span></span>  
  
-   <span data-ttu-id="00ae2-150">MCALL 语法。</span><span class="sxs-lookup"><span data-stu-id="00ae2-150">MCALL syntax.</span></span> <span data-ttu-id="00ae2-151">只能用于更新操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-151">Can be used for updates only.</span></span>  
  
-   <span data-ttu-id="00ae2-152">XCALL 语法。</span><span class="sxs-lookup"><span data-stu-id="00ae2-152">XCALL syntax.</span></span> <span data-ttu-id="00ae2-153">可用于更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="00ae2-153">Can be used for updates and deletes.</span></span>  
  
-   <span data-ttu-id="00ae2-154">VCALL。</span><span class="sxs-lookup"><span data-stu-id="00ae2-154">VCALL.</span></span> <span data-ttu-id="00ae2-155">用于可更新的订阅。</span><span class="sxs-lookup"><span data-stu-id="00ae2-155">Used for updatable subscriptions.</span></span> <span data-ttu-id="00ae2-156">仅限内部使用。</span><span class="sxs-lookup"><span data-stu-id="00ae2-156">Internal use only.</span></span>  
  
 <span data-ttu-id="00ae2-157">各方法传播到订阅服务器的数据量不同。</span><span class="sxs-lookup"><span data-stu-id="00ae2-157">Each method differs in the amount of data that is propagated to the Subscriber.</span></span> <span data-ttu-id="00ae2-158">例如，SCALL 仅涉及更新实际影响的列的值。</span><span class="sxs-lookup"><span data-stu-id="00ae2-158">For example, SCALL passes in values only for the columns that are actually affected by an update.</span></span> <span data-ttu-id="00ae2-159">而 XCALL 则涉及到所有列（无论更新是否影响）以及每个列的所有旧数据值。</span><span class="sxs-lookup"><span data-stu-id="00ae2-159">XCALL, by contrast, requires all columns (whether affected by an update or not) and all the old data values for each column.</span></span> <span data-ttu-id="00ae2-160">在很多情况下，SCALL 适用于更新，但如果应用程序在更新过程中涉及到所有数据值，则使用 XCALL。</span><span class="sxs-lookup"><span data-stu-id="00ae2-160">In many cases, SCALL is appropriate for updates, but if your application requires all the data values during an update, XCALL allows for this.</span></span>  
  
#### <a name="call-syntax"></a><span data-ttu-id="00ae2-161">CALL 语法</span><span class="sxs-lookup"><span data-stu-id="00ae2-161">CALL Syntax</span></span>  
 <span data-ttu-id="00ae2-162">INSERT 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-162">INSERT stored procedures</span></span>  
 <span data-ttu-id="00ae2-163">处理 INSERT 语句的存储过程将传递所有列的插入值：</span><span class="sxs-lookup"><span data-stu-id="00ae2-163">Stored procedures handling INSERT statements will be passed the inserted values for all columns:</span></span>  
  
```  
c1, c2, c3,... cn  
```  
  
 <span data-ttu-id="00ae2-164">UPDATE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-164">UPDATE stored procedures</span></span>  
 <span data-ttu-id="00ae2-165">处理 UPDATE 语句的存储过程将传递在项目中定义的所有列的已更新值，后跟主键列的原始值（不尝试确定更改了哪些列。）：</span><span class="sxs-lookup"><span data-stu-id="00ae2-165">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns (no attempt is made to determine which columns were changed.):</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn  
```  
  
 <span data-ttu-id="00ae2-166">DELETE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-166">DELETE stored procedures</span></span>  
 <span data-ttu-id="00ae2-167">处理 DELETE 语句的存储过程将传递主键列的值：</span><span class="sxs-lookup"><span data-stu-id="00ae2-167">Stored procedures handling DELETE statements will be passed values for the primary key columns:</span></span>  
  
```  
pkc1, pkc2, pkc3,... pkcn  
```  
  
#### <a name="scall-syntax"></a><span data-ttu-id="00ae2-168">SCALL 语法</span><span class="sxs-lookup"><span data-stu-id="00ae2-168">SCALL Syntax</span></span>  
 <span data-ttu-id="00ae2-169">UPDATE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-169">UPDATE stored procedures</span></span>  
 <span data-ttu-id="00ae2-170">处理 UPDATE 语句的存储过程将只传递已更改的那些列的更新值，后面依次是主键列的原始值和一个指明已更改列的位掩码 (`binary(n)`) 参数。</span><span class="sxs-lookup"><span data-stu-id="00ae2-170">Stored procedures handling UPDATE statements will be passed the updated values only for those columns that have changed, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns.</span></span> <span data-ttu-id="00ae2-171">在下面的示例中，列 2 (c2) 未更改：</span><span class="sxs-lookup"><span data-stu-id="00ae2-171">In the following example, column 2 (c2) has not changed:</span></span>  
  
```  
c1, , c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="mcall-syntax"></a><span data-ttu-id="00ae2-172">MCALL 语法</span><span class="sxs-lookup"><span data-stu-id="00ae2-172">MCALL Syntax</span></span>  
 <span data-ttu-id="00ae2-173">UPDATE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-173">UPDATE stored procedures</span></span>  
 <span data-ttu-id="00ae2-174">处理 UPDATE 语句的存储过程将传递在项目中定义的所有列的更新值，后面依次跟主键列的原始值和一个指示已更改列的位掩码 (`binary(n)`) 参数：</span><span class="sxs-lookup"><span data-stu-id="00ae2-174">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns:</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="xcall-syntax"></a><span data-ttu-id="00ae2-175">XCALL 语法</span><span class="sxs-lookup"><span data-stu-id="00ae2-175">XCALL Syntax</span></span>  
 <span data-ttu-id="00ae2-176">UPDATE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-176">UPDATE stored procedures</span></span>  
 <span data-ttu-id="00ae2-177">处理 UPDATE 语句的存储过程将传递在项目中定义的所有列的原始值（前像），后跟在项目中定义的所有列的更新值（后像）：</span><span class="sxs-lookup"><span data-stu-id="00ae2-177">Stored procedures handling UPDATE statements will be passed the original values (the before image) for all columns defined in the article, followed by the updated values (the after image) for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn, c1, c2, c3,... cn,  
```  
  
 <span data-ttu-id="00ae2-178">DELETE 存储过程</span><span class="sxs-lookup"><span data-stu-id="00ae2-178">DELETE stored procedures</span></span>  
 <span data-ttu-id="00ae2-179">处理 DELETE 语句的存储过程将传递在项目中定义的所有列的原始值（前像）：</span><span class="sxs-lookup"><span data-stu-id="00ae2-179">Stored procedures handling DELETE statements will be passed the original (the before image) values for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn  
```  
  
> [!NOTE]  
>  <span data-ttu-id="00ae2-180">使用 XCALL 时， **text** 列和 **image** 列的前像值应为 NULL。</span><span class="sxs-lookup"><span data-stu-id="00ae2-180">When using XCALL, the before image values for **text** and **image** columns are expected to be NULL.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="00ae2-181">示例</span><span class="sxs-lookup"><span data-stu-id="00ae2-181">Examples</span></span>  
 <span data-ttu-id="00ae2-182">下列过程是为 `Vendor Table` 示例数据库中的 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 创建的默认过程。</span><span class="sxs-lookup"><span data-stu-id="00ae2-182">The following procedures are the default procedures created for the `Vendor Table` in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database.</span></span>  
  
```  
--INSERT procedure using CALL syntax  
create procedure [sp_MSins_PurchasingVendor]   
  @c1 int,@c2 nvarchar(15),@c3 nvarchar(50),@c4 tinyint,@c5 bit,@c6 bit,@c7 nvarchar(1024),@c8 datetime  
as   
begin   
insert into [Purchasing].[Vendor]([VendorID]  
,[AccountNumber]  
,[Name]  
,[CreditRating]  
,[PreferredVendorStatus]  
,[ActiveFlag]  
,[PurchasingWebServiceURL]  
,[ModifiedDate])  
values (   
 @c1  
,@c2  
,@c3  
,@c4  
,@c5  
,@c6  
,@c7  
,@c8  
 )   
end  
go  
  
--UPDATE procedure using SCALL syntax  
create procedure [sp_MSupd_PurchasingVendor]   
 @c1 int = null,@c2 nvarchar(15) = null,@c3 nvarchar(50) = null,@c4 tinyint = null,@c5 bit = null,@c6 bit = null,@c7 nvarchar(1024) = null,@c8 datetime = null,@pkc1 int  
,@bitmap binary(2)  
as  
begin  
update [Purchasing].[Vendor] set   
 [AccountNumber] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [AccountNumber] end  
,[Name] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [Name] end  
,[CreditRating] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [CreditRating] end  
,[PreferredVendorStatus] = case substring(@bitmap,1,1) & 16 when 16 then @c5 else [PreferredVendorStatus] end  
,[ActiveFlag] = case substring(@bitmap,1,1) & 32 when 32 then @c6 else [ActiveFlag] end  
,[PurchasingWebServiceURL] = case substring(@bitmap,1,1) & 64 when 64 then @c7 else [PurchasingWebServiceURL] end  
,[ModifiedDate] = case substring(@bitmap,1,1) & 128 when 128 then @c8 else [ModifiedDate] end  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end  
go  
  
--DELETE procedure using CALL syntax  
create procedure [sp_MSdel_PurchasingVendor]   
  @pkc1 int  
as   
begin   
delete [Purchasing].[Vendor]  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end   
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="00ae2-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00ae2-183">See Also</span></span>  
 [<span data-ttu-id="00ae2-184">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="00ae2-184">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
