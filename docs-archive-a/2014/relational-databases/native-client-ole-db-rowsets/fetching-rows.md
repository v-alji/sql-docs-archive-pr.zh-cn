---
title: 提取行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
author: rothja
ms.author: jroth
ms.openlocfilehash: 435e1d705091814b2544c75772f20882caddf942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578861"
---
# <a name="fetching-rows"></a><span data-ttu-id="9e8c3-102">提取行</span><span class="sxs-lookup"><span data-stu-id="9e8c3-102">Fetching Rows</span></span>
  <span data-ttu-id="9e8c3-103">IRowset 接口是基础行集接口\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-103">The **IRowset** interface is the base rowset interface.</span></span> <span data-ttu-id="9e8c3-104">IRowset 接口提供了用于按顺序提取行、从这些行中获得数据以及管理行的方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-104">The **IRowset** interface provides methods for fetching rows sequentially, getting the data from those rows, and managing rows.</span></span> <span data-ttu-id="9e8c3-105">使用者使用 IRowset 中的这些方法执行所有基本行集操作\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-105">Consumers use the methods in **IRowset** for all basic rowset operations.</span></span> <span data-ttu-id="9e8c3-106">这包括提取和释放行以及获得列值。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-106">This includes fetching and releasing rows and getting column values.</span></span>  
  
 <span data-ttu-id="9e8c3-107">使用者获得行集的接口指针时，第一步通常是使用 IRowsetInfo::GetProperties 方法确定行集的功能\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-107">When a consumer obtains an interface pointer on a rowset, the first step is ordinarily to determine the capabilities of the rowset by using the **IRowsetInfo::GetProperties** method.</span></span> <span data-ttu-id="9e8c3-108">这将返回行集所公开的接口的相关信息，以及未显示为非重复接口的行集的功能，例如最大活动行数和可以同时有挂起更新的行数。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-108">This returns information about the interfaces exposed by the rowset and also capabilities of the rowset that do not show up as distinct interfaces, such as the maximum number of active rows and the number of rows that can have pending updates at the same time.</span></span>  
  
 <span data-ttu-id="9e8c3-109">使用者的下一步是确定行集中列的特征（即元数据）。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-109">The next step for consumers is to determine the characteristics, or metadata, of the columns in the rowset.</span></span> <span data-ttu-id="9e8c3-110">对于该步骤，它们对简单列信息使用 IColumnsInfo 方法，或对扩展列信息使用 IColumnsRowset 方法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-110">For this they use the **IColumnsInfo** method for simple column information or the **IColumnsRowset** method for extended column information.</span></span> <span data-ttu-id="9e8c3-111">GetColumnInfo 方法返回以下信息\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="9e8c3-111">The **GetColumnInfo** method returns the following information:</span></span>  
  
-   <span data-ttu-id="9e8c3-112">结果集中的列数。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-112">The number of columns in the result set.</span></span>  
  
-   <span data-ttu-id="9e8c3-113">DBCOLUMNINFO 结构的数组，每列一个。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-113">An array of DBCOLUMNINFO structures, one per column.</span></span>  
  
     <span data-ttu-id="9e8c3-114">结构的顺序是列在行集中出现的顺序。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-114">The order of the structures is the order in which the columns appear in the rowset.</span></span> <span data-ttu-id="9e8c3-115">每个 DBCOLUMNINFO 结构都包括列元数据，例如列名称、列的序号、列值的最大可能长度、列的数据类型、精度和长度。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-115">Each DBCOLUMNINFO structure includes column metadata, such as column name, ordinal of the column, maximum possible length of a value in the column, data type of the column, precision, and length.</span></span>  
  
-   <span data-ttu-id="9e8c3-116">指向单个分配块中的所有字符串值的存储区的指针。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-116">The pointer to a storage for all string values within a single allocation block.</span></span>  
  
 <span data-ttu-id="9e8c3-117">使用者通过元数据或基于生成该行集的文本命令来确定它需要哪些列。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-117">The consumer determines which columns it needs either from the metadata or based on the text command that generated the rowset.</span></span> <span data-ttu-id="9e8c3-118">它通过对 IColumnsInfo 返回的列信息进行排序，或通过 IColumnsRowset 返回的列元数据行集中的序号，确定所需列的序号\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-118">It determines the ordinals of the needed columns from the ordering of the column information returned by **IColumnsInfo** or from the ordinals in the column metadata rowset returned by **IColumnsRowset**.</span></span>  
  
 <span data-ttu-id="9e8c3-119">IColumnsInfo 和 IColumnsRowset 接口用于提取行集中有关列的信息\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-119">The **IColumnsInfo** and **IColumnsRowset** interfaces are used to extract information about the columns in the rowset.</span></span> <span data-ttu-id="9e8c3-120">IColumnsInfo 接口返回一组有限的信息，而 IColumnsRowset 提供所有元数据\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-120">The **IColumnsInfo** interface returns a limited set of information, whereas **IColumnsRowset** provides all the metadata.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8c3-121">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 7.0 和更早版本中，IColumnsInfo::GetColumnsInfo 所返回的可选元数据列 DBCOLUMN_COMPUTEMODE 会返回 DBSTATUS_S_ISNULL（而不是用于描述该列是否为计算列的值），因为无法确定基础列是否为计算列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and earlier, the optional metadata column DBCOLUMN_COMPUTEMODE returned by **IColumnsInfo::GetColumnsInfo** returns DBSTATUS_S_ISNULL (instead of the values describing whether the column is computed) because it cannot be determined whether the underlying column is computed.</span></span>  
  
 <span data-ttu-id="9e8c3-122">序号用于指定到列的绑定。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-122">The ordinals are used to specify a binding to a column.</span></span> <span data-ttu-id="9e8c3-123">绑定是将使用者的结构元素与列进行关联的结构。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-123">A binding is a structure that associates an element of the consumer's structure with a column.</span></span> <span data-ttu-id="9e8c3-124">绑定可以是对列的数据值、长度和状态值的绑定。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-124">The binding can bind the data value, length, and status value of the column.</span></span>  
  
 <span data-ttu-id="9e8c3-125">在取值函数中可收集一组绑定。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-125">A set of bindings is gathered together in an accessor.</span></span> <span data-ttu-id="9e8c3-126">此函数可通过 IAccessor::CreateAccessor 方法创建\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-126">This is created by using the **IAccessor::CreateAccessor** method.</span></span> <span data-ttu-id="9e8c3-127">取值函数可以包含多个绑定，以便可以在单个调用中检索或设置多个列的数据。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-127">An accessor can contain multiple bindings so that the data for multiple columns can be retrieved or set in a single call.</span></span> <span data-ttu-id="9e8c3-128">使用者可以创建多个取值函数，以便在应用程序的不同部分匹配不同的使用模式。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-128">The consumer can create several accessors to match different usage patterns in different parts of the application.</span></span> <span data-ttu-id="9e8c3-129">它可以在行集仍然存在时创建和释放取值函数。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-129">It can create and release accessors while the rowset remains in existence.</span></span>  
  
 <span data-ttu-id="9e8c3-130">若要从数据库提取行，使用者可调用某个方法，例如 IRowset::GetNextRows 或 IRowsetLocate::GetRowsAt\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-130">To fetch rows from the database, the consumer calls a method, such as **IRowset::GetNextRows** or **IRowsetLocate::GetRowsAt**.</span></span> <span data-ttu-id="9e8c3-131">这些提取操作将行数据从服务器放入提供程序的行缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-131">These fetch operations put row data from the server into the row buffer of the provider.</span></span> <span data-ttu-id="9e8c3-132">使用者不能直接访问提供程序的行缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-132">The consumer does not have direct access to the row buffer of the provider.</span></span> <span data-ttu-id="9e8c3-133">使用者使用 IRowset::GetData 从提供程序的缓冲区将数据复制到使用者缓冲区，并使用 IRowsetChange::SetData 将数据更改从使用者缓冲区复制到提供程序缓冲区\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-133">The consumer uses **IRowset::GetData** to copy data from the buffer of the provider to the consumer buffer and **IRowsetChange::SetData** to copy data changes from the consumer buffer to the provider buffer.</span></span>  
  
 <span data-ttu-id="9e8c3-134">使用者调用 GetData 方法，并传递行的句柄、取值函数的句柄和使用者分配的缓冲区的指针\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-134">The consumer calls the **GetData** method and passes the handle to a row, the handle to an accessor, and a pointer to a consumer-allocated buffer.</span></span> <span data-ttu-id="9e8c3-135">GetData 转换数据，并返回在用于创建取值函数的绑定中指定的列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-135">**GetData** converts the data and returns the columns as specified in the bindings used to create the accessor.</span></span> <span data-ttu-id="9e8c3-136">使用者可以使用不同取值函数和缓冲区对某行多次调用 GetData，因此使用者可以获得相同数据的多个副本\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-136">The consumer can call **GetData** more than one time for a row, using different accessors and buffers and therefore the consumer can obtain multiple copies of the same data.</span></span>  
  
 <span data-ttu-id="9e8c3-137">可以采用多种方式处理来自变长列的数据。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-137">Data from variable-length columns can be treated several ways.</span></span> <span data-ttu-id="9e8c3-138">首先，可以将这样的列绑定到使用者的结构的有限部分。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-138">First, such columns can be bound to a finite section of the consumer's structure.</span></span> <span data-ttu-id="9e8c3-139">这将导致当数据的长度超过缓冲区的长度时发生截断。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-139">This causes truncation when the length of the data exceeds the length of the buffer.</span></span> <span data-ttu-id="9e8c3-140">通过检查状态是否为 DBSTATUS_S_TRUNCATED，使用者可以确定是否已发生截断。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-140">The consumer can determine that truncation has occurred by checking for the status DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="9e8c3-141">返回的长度始终是真实的字节长度，因此使用者还可以确定有多少数据被截断。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-141">The returned length is always the true length in bytes, so that the consumer also can determine how much data was truncated.</span></span>  
  
 <span data-ttu-id="9e8c3-142">使用者完成提取或更新行后，它将用 ReleaseRows 方法释放它们\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-142">When the consumer has finished fetching or updating rows, it releases them with the **ReleaseRows** method.</span></span> <span data-ttu-id="9e8c3-143">这将释放行集中行的副本所占的资源，并为新行腾出空间。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-143">This releases resources from the copy of the rows in the rowset and makes room for new rows.</span></span> <span data-ttu-id="9e8c3-144">然后，使用者可以重复其提取或创建行并访问其中数据的循环。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-144">The consumer can then repeat its cycle of fetching or creating rows and accessing the data in them.</span></span>  
  
 <span data-ttu-id="9e8c3-145">当使用者完成对行集的处理时，它将调用 IAccessor::ReleaseAccessor 方法释放所有取值函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-145">When the consumer is finished with the rowset, it calls the **IAccessor::ReleaseAccessor** method to release any accessor.</span></span> <span data-ttu-id="9e8c3-146">它将对行集所公开的所有接口调用 IUnknown::Release 方法，以释放行集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-146">It calls the **IUnknown::Release** method on all interfaces exposed by the rowset to release the rowset.</span></span> <span data-ttu-id="9e8c3-147">释放行集时，它将强制释放使用者可能持有的任何剩余的行或取值函数。</span><span class="sxs-lookup"><span data-stu-id="9e8c3-147">When the rowset is released, it forces the release of any remaining rows or accessors the consumer may hold.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e8c3-148">本节内容</span><span class="sxs-lookup"><span data-stu-id="9e8c3-148">In This Section</span></span>  
  
-   [<span data-ttu-id="9e8c3-149">下次提取位置</span><span class="sxs-lookup"><span data-stu-id="9e8c3-149">Next Fetch Position</span></span>](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e8c3-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e8c3-150">See Also</span></span>  
 [<span data-ttu-id="9e8c3-151">行集</span><span class="sxs-lookup"><span data-stu-id="9e8c3-151">Rowsets</span></span>](rowsets.md)  
  
  
