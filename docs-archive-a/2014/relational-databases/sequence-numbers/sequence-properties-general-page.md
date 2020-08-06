---
title: 序列属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sequence.general.f1
ms.assetid: 0187f413-cdf0-48a2-b2e6-9b3578cd5811
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc969dc09663da8150461529ad1e1f1fb094539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693679"
---
# <a name="sequence-properties-general-page"></a><span data-ttu-id="e5dae-102">序列属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="e5dae-102">Sequence Properties (General Page)</span></span>
  <span data-ttu-id="e5dae-103">创建一个序列对象并指定其属性。</span><span class="sxs-lookup"><span data-stu-id="e5dae-103">Creates a sequence object and specifies its properties.</span></span> <span data-ttu-id="e5dae-104">序列是用户定义的绑定到架构的对象，该对象可根据创建序列所依据的规范来生成数值序列。</span><span class="sxs-lookup"><span data-stu-id="e5dae-104">A sequence is a user-defined schema bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="e5dae-105">这组数值以定义的间隔按升序或降序生成，并且可配置为用尽时重新启动（循环）。</span><span class="sxs-lookup"><span data-stu-id="e5dae-105">The sequence of numeric values is generated in an ascending or descending order at a defined interval and can be configured to restart (cycle) when exhausted.</span></span> <span data-ttu-id="e5dae-106">序列不与特定表相关联，这一点与标识列不同。</span><span class="sxs-lookup"><span data-stu-id="e5dae-106">Sequences, unlike identity columns, are not associated with specific tables.</span></span> <span data-ttu-id="e5dae-107">应用程序将引用某一序列对象以便检索其下一个值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-107">Applications refer to a sequence object to retrieve its next value.</span></span> <span data-ttu-id="e5dae-108">序列与表之间的关系由应用程序控制。</span><span class="sxs-lookup"><span data-stu-id="e5dae-108">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="e5dae-109">用户应用程序可以引用一个序列对象，并跨多个行和表协调值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-109">User applications can reference a sequence object and coordinate the values across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="e5dae-110">与在插入时生成的标识列值不同，应用程序可以获得下一个序列号，而不必通过调用 [NEXT VALUE FOR 函数](/sql/t-sql/functions/next-value-for-transact-sql)来插入行。</span><span class="sxs-lookup"><span data-stu-id="e5dae-110">Unlike identity columns values which are generated at the time of insert, an application can obtain the next sequence number without inserting the row by calling the [NEXT VALUE FOR function](/sql/t-sql/functions/next-value-for-transact-sql).</span></span> <span data-ttu-id="e5dae-111">使用 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 同时获取多个序列号。</span><span class="sxs-lookup"><span data-stu-id="e5dae-111">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="e5dae-112">有关同时使用 **CREATE SEQUENCE** 和 **NEXT VALUE FOR** 函数的信息，请参阅 [序列号](sequence-numbers.md)。</span><span class="sxs-lookup"><span data-stu-id="e5dae-112">For information and scenarios that use both **CREATE SEQUENCE** and the **NEXT VALUE FOR** function, see [Sequence Numbers](sequence-numbers.md).</span></span>  
  
 <span data-ttu-id="e5dae-113">访问此页的方法有如下两种：在对象资源管理器中右键单击“序列”  ，再单击“新建序列”  ，或者右键单击现有序列，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e5dae-113">This page is accessed in two ways: either by right-clicking **Sequences** in Object Explorer and clicking **New Sequence**, or by right-clicking an existing sequence and clicking **Properties**.</span></span> <span data-ttu-id="e5dae-114">如果右键单击现有序列，再单击“属性”  ，则以下某些选项是不可编辑的。</span><span class="sxs-lookup"><span data-stu-id="e5dae-114">When you right-click an existing sequence and click **Properties**, the options are not editable.</span></span> <span data-ttu-id="e5dae-115">要更改序列选项，请使用 [ALTER SEQUENCE (Transact-SQL)](/sql/t-sql/statements/alter-sequence-transact-sql) 语句，或删除并重新创建序列对象。</span><span class="sxs-lookup"><span data-stu-id="e5dae-115">To change the sequence options use the [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) statement or drop and recreate the sequence object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e5dae-116">选项</span><span class="sxs-lookup"><span data-stu-id="e5dae-116">Options</span></span>  
 <span data-ttu-id="e5dae-117">**序列名称**</span><span class="sxs-lookup"><span data-stu-id="e5dae-117">**Sequence name**</span></span>  
 <span data-ttu-id="e5dae-118">在此处输入序列名称。</span><span class="sxs-lookup"><span data-stu-id="e5dae-118">Enter the sequence name here.</span></span>  
  
 <span data-ttu-id="e5dae-119">**序列架构**</span><span class="sxs-lookup"><span data-stu-id="e5dae-119">**Sequence schema**</span></span>  
 <span data-ttu-id="e5dae-120">指定将拥有此序列的架构。</span><span class="sxs-lookup"><span data-stu-id="e5dae-120">Specify the schema that will own this sequence.</span></span>  
  
 <span data-ttu-id="e5dae-121">**Data type**</span><span class="sxs-lookup"><span data-stu-id="e5dae-121">**Data type**</span></span>  
 <span data-ttu-id="e5dae-122">序列可定义为任何整数类型。</span><span class="sxs-lookup"><span data-stu-id="e5dae-122">A sequence can be defined as any integer type.</span></span> <span data-ttu-id="e5dae-123">这包括：</span><span class="sxs-lookup"><span data-stu-id="e5dae-123">This includes:</span></span>  
  
|<span data-ttu-id="e5dae-124">数据类型</span><span class="sxs-lookup"><span data-stu-id="e5dae-124">Data type</span></span>|<span data-ttu-id="e5dae-125">范围</span><span class="sxs-lookup"><span data-stu-id="e5dae-125">Range</span></span>|  
|---------------|-----------|  
|`tinyint`|<span data-ttu-id="e5dae-126">0 到 255</span><span class="sxs-lookup"><span data-stu-id="e5dae-126">0 to 255</span></span>|  
|`smallint`|<span data-ttu-id="e5dae-127">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="e5dae-127">-32,768 to 32,767</span></span>|  
|`int`|<span data-ttu-id="e5dae-128">-2,147,483,648 到 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="e5dae-128">-2,147,483,648 to 2,147,483,647</span></span>|  
|`bigint`|<span data-ttu-id="e5dae-129">-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="e5dae-129">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|  
  
-   <span data-ttu-id="e5dae-130">`decimal` 或 `numeric`，小数位数为 0。</span><span class="sxs-lookup"><span data-stu-id="e5dae-130">`decimal` or `numeric` with a scale of 0.</span></span>  
  
-   <span data-ttu-id="e5dae-131">基于这些类型之一的任何用户定义数据类型（别名类型）。</span><span class="sxs-lookup"><span data-stu-id="e5dae-131">Any user-defined data type (alias type) that is based on one of these types.</span></span>  
  
 <span data-ttu-id="e5dae-132">**精度**</span><span class="sxs-lookup"><span data-stu-id="e5dae-132">**Precision**</span></span>  
 <span data-ttu-id="e5dae-133">对于 `decimal` 或 `numeric` 数据类型，指定精度。</span><span class="sxs-lookup"><span data-stu-id="e5dae-133">For `decimal` or `numeric` data types, specify the precision.</span></span> <span data-ttu-id="e5dae-134">（小数位数始终为 0。）</span><span class="sxs-lookup"><span data-stu-id="e5dae-134">(The scale is always 0.)</span></span>  
  
 <span data-ttu-id="e5dae-135">**起始值**</span><span class="sxs-lookup"><span data-stu-id="e5dae-135">**Start with value**</span></span>  
 <span data-ttu-id="e5dae-136">将由序列对象返回的第一个值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-136">The first value that will be returned by the sequence object.</span></span> <span data-ttu-id="e5dae-137">**START** 值必须是小于或等于序列对象的最大值并大于或等于其最小值的值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-137">The **START** value must be a value that is less than or equal to the maximum and greater than or equal to the minimum value of the sequence object.</span></span> <span data-ttu-id="e5dae-138">新序列对象的默认起始值是升序序列对象的最小值和降序序列对象的最大值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-138">The default start value for a new sequence object is the minimum value for an ascending sequence object and the maximum value for a descending sequence object.</span></span>  
  
 <span data-ttu-id="e5dae-139">**增量**</span><span class="sxs-lookup"><span data-stu-id="e5dae-139">**Increment by**</span></span>  
 <span data-ttu-id="e5dae-140">用于在每次调用 **NEXT VALUE FOR** 函数时递增（如果为负数，则为递减）序列对象的值的值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-140">The value that is used to increment (or decrement if negative) the value of the sequence object for each call to the **NEXT VALUE FOR** function.</span></span> <span data-ttu-id="e5dae-141">如果增量是负值，则序列对象为降序，否则为升序。</span><span class="sxs-lookup"><span data-stu-id="e5dae-141">If the increment is a negative value the sequence object is descending, otherwise, it is ascending.</span></span> <span data-ttu-id="e5dae-142">增量不能为 0。</span><span class="sxs-lookup"><span data-stu-id="e5dae-142">The increment cannot be 0.</span></span>  
  
 <span data-ttu-id="e5dae-143">**最小值**</span><span class="sxs-lookup"><span data-stu-id="e5dae-143">**Minimum value**</span></span>  
 <span data-ttu-id="e5dae-144">指定序列对象的边界。</span><span class="sxs-lookup"><span data-stu-id="e5dae-144">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="e5dae-145">一个新序列对象的默认最小值是该序列对象的数据类型的最小值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-145">The default minimum value for a new sequence object is the minimum value of the data type of the sequence object.</span></span> <span data-ttu-id="e5dae-146">对于 `tinyint` 数据类型，此值为零，对于所有其他数据类型则为负数。</span><span class="sxs-lookup"><span data-stu-id="e5dae-146">This is zero for the `tinyint` data type and a negative number for all other data types.</span></span>  
  
 <span data-ttu-id="e5dae-147">**最大值**</span><span class="sxs-lookup"><span data-stu-id="e5dae-147">**Maximum value**</span></span>  
 <span data-ttu-id="e5dae-148">指定序列对象的边界。</span><span class="sxs-lookup"><span data-stu-id="e5dae-148">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="e5dae-149">一个新序列对象的默认最大值是该序列对象的数据类型的最大值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-149">The default maximum value for a new sequence object is the maximum value of the data type of the sequence object.</span></span>  
  
 <span data-ttu-id="e5dae-150">**在达到限制时，循环序列将重新开始**</span><span class="sxs-lookup"><span data-stu-id="e5dae-150">**Cycle-sequence will restart on reaching limit**</span></span>  
 <span data-ttu-id="e5dae-151">选择此选项，则当超过序列对象的最小值或最大值时，允许序列对象从最小值（或对于降序顺序对象，则为最大值）重新开始。</span><span class="sxs-lookup"><span data-stu-id="e5dae-151">Select to allow the sequence object to restart from the minimum value (or maximum for descending sequence objects) when its minimum or maximum value is exceeded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5dae-152">循环不从起始值重新开始，而是从最小值/最大值重新开始。</span><span class="sxs-lookup"><span data-stu-id="e5dae-152">Cycling does not restart from the start value but rather from the minimum/maximum value.</span></span>  
  
 <span data-ttu-id="e5dae-153">**高速缓存选项**</span><span class="sxs-lookup"><span data-stu-id="e5dae-153">**Cache options**</span></span>  
 <span data-ttu-id="e5dae-154">创建序列值的缓存可以通过最大限度地减少创建序列号所需的磁盘 IO 数来提高使用序列对象的应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="e5dae-154">Creating a cache of sequence values can increase performance for applications that use sequence objects by minimizing the number of disk IOs that are required to create sequence numbers.</span></span>  
  
-   <span data-ttu-id="e5dae-155">默认缓存大小 - [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将选择一个大小，然而，用户不应依赖于所选择的大小来确保一致。</span><span class="sxs-lookup"><span data-stu-id="e5dae-155">Default cache size - The [!INCLUDE[ssDE](../../includes/ssde-md.md)] will select a size, however users should not rely upon the selection being consistent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e5dae-156">可能会更改计算缓存大小的方法而不另行通知。</span><span class="sxs-lookup"><span data-stu-id="e5dae-156">might change the method of calculating the cache size without notice.</span></span>  
  
-   <span data-ttu-id="e5dae-157">无缓存 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将不缓存序列号。</span><span class="sxs-lookup"><span data-stu-id="e5dae-157">No cache - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will not cache sequence numbers.</span></span>  
  
-   <span data-ttu-id="e5dae-158">缓存大小 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将缓存序列值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-158">Cache with size - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will cache sequence values.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e5dae-159">将保持跟踪当前值和缓存中留下的值数量。</span><span class="sxs-lookup"><span data-stu-id="e5dae-159">keeps track of the current value and the number of values left in the cache.</span></span> <span data-ttu-id="e5dae-160">因此，存储缓存所需的内存量始终为序列对象的数据类型的两个实例。</span><span class="sxs-lookup"><span data-stu-id="e5dae-160">Therefore, the amount of memory that is required to store the cache is always two instances of the data type of the sequence object</span></span>  
  
 <span data-ttu-id="e5dae-161">当使用 CACHE 选项创建时，意外关机（如电源故障）可能导致缓存中的序列号丢失。</span><span class="sxs-lookup"><span data-stu-id="e5dae-161">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="e5dae-162">有关创建序列选项的其他信息，请参阅 [CREATE SEQUENCE (Transact-SQL)](/sql/t-sql/statements/create-sequence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e5dae-162">For additional information about the create sequence options, see [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="e5dae-163">权限</span><span class="sxs-lookup"><span data-stu-id="e5dae-163">Permissions</span></span>  
 <span data-ttu-id="e5dae-164">要求对 SCHEMA 拥有 **CREATE SEQUENCE**、 **ALTER**或 **CONTROL** 权限。</span><span class="sxs-lookup"><span data-stu-id="e5dae-164">Requires **CREATE SEQUENCE**, **ALTER**, or **CONTROL** permission on the SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dae-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5dae-165">See Also</span></span>  
 [<span data-ttu-id="e5dae-166">sys.sequences (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e5dae-166">sys.sequences &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)  
  
  
