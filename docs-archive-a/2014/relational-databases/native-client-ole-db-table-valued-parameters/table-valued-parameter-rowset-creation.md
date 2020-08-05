---
title: 创建表值参数行集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
ms.assetid: ffe213ca-cc0e-465e-b31c-a8272324c4fe
author: rothja
ms.author: jroth
ms.openlocfilehash: a22ccbd583d95c41daa0a113363985828cf1e9d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580216"
---
# <a name="table-valued-parameter-rowset-creation"></a><span data-ttu-id="ea550-102">创建表值参数行集</span><span class="sxs-lookup"><span data-stu-id="ea550-102">Table-Valued Parameter Rowset Creation</span></span>
  <span data-ttu-id="ea550-103">尽管使用者可以为表值参数提供任意行集对象，但是典型的行集对象要针对后端数据存储来实现，因此提供有限的性能。</span><span class="sxs-lookup"><span data-stu-id="ea550-103">Although consumers can provide any rowset object for table-valued parameters, typical rowset objects are implemented against back-end data stores, and therefore provide limited performance.</span></span> <span data-ttu-id="ea550-104">有鉴于此，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持使用者在内存中的数据之上创建专用行集对象。</span><span class="sxs-lookup"><span data-stu-id="ea550-104">For this reason, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider enables consumers to create a specialized rowset object on top of in-memory data.</span></span> <span data-ttu-id="ea550-105">此特殊的内存中行集对象是一个名为表值参数行集的新 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="ea550-105">This special, in-memory rowset object is a new COM object called a table-valued parameter rowset .</span></span> <span data-ttu-id="ea550-106">它提供与参数集相似的功能。</span><span class="sxs-lookup"><span data-stu-id="ea550-106">It provides functionality similar to parameter sets.</span></span>  
  
 <span data-ttu-id="ea550-107">表值参数行集对象由使用者通过多个会话级接口为输入参数显式创建。</span><span class="sxs-lookup"><span data-stu-id="ea550-107">Table-valued parameter rowset objects are created explicitly by the consumer for input parameters through multiple session-level interfaces.</span></span> <span data-ttu-id="ea550-108">每个表值参数对应一个表值参数行集对象实例。</span><span class="sxs-lookup"><span data-stu-id="ea550-108">There is one instance of a table-valued parameter rowset object per table-valued parameter.</span></span> <span data-ttu-id="ea550-109">使用者可以通过以下两种方法之一创建表值参数行集对象：提供已知的元数据信息（静态方案）；或者通过访问接口发现元数据信息（动态方案）。</span><span class="sxs-lookup"><span data-stu-id="ea550-109">The consumer can create the table-valued parameter rowset objects either by providing metadata information that is already known (static scenario), or by discovering it through provider interfaces (dynamic scenario).</span></span> <span data-ttu-id="ea550-110">以下各节介绍这两种方案。</span><span class="sxs-lookup"><span data-stu-id="ea550-110">The following sections describe these two scenarios.</span></span>  
  
## <a name="static-scenario"></a><span data-ttu-id="ea550-111">静态方案</span><span class="sxs-lookup"><span data-stu-id="ea550-111">Static Scenario</span></span>  
 <span data-ttu-id="ea550-112">如果类型信息已知，使用者使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 对与表值参数对应的表值参数行集对象进行实例化。</span><span class="sxs-lookup"><span data-stu-id="ea550-112">When the type information is known, the consumer uses ITableDefinitionWithConstraints::CreateTableWithConstraints to instantiate a table-valued parameter rowset object that corresponds to a table-valued parameter.</span></span>  
  
 <span data-ttu-id="ea550-113">guid\*\* 字段（pTableID\*\* 参数）包含特殊 GUID (CLSID_ROWSET_TVP)。</span><span class="sxs-lookup"><span data-stu-id="ea550-113">The *guid* field (*pTableID* parameter) contains the special GUID (CLSID_ROWSET_TVP).</span></span> <span data-ttu-id="ea550-114">pwszName 成员包含使用者要实例化的表值参数类型的名称\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea550-114">The *pwszName* member contains the name of the table-valued parameter type that the consumer wants to instantiate.</span></span> <span data-ttu-id="ea550-115">eKind 字段将设置为 DBKIND_GUID_NAME\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea550-115">The *eKind* field will be set to DBKIND_GUID_NAME.</span></span> <span data-ttu-id="ea550-116">此名称在使用特殊 SQL 语句时是必需的，在使用过程调用时是可选的。</span><span class="sxs-lookup"><span data-stu-id="ea550-116">This name is required when the statement is ad hoc SQL; the name is optional if it is a procedure call.</span></span>  
  
 <span data-ttu-id="ea550-117">对于聚合，使用者传递 pUnkOuter\*\* 参数（带有控制的 IUnknown）。</span><span class="sxs-lookup"><span data-stu-id="ea550-117">For aggregation, the consumer passes the *pUnkOuter* parameter with the controlling IUnknown.</span></span>  
  
 <span data-ttu-id="ea550-118">表值参数行集对象属性是只读的，因此，使用者不应在*rgPropertySets*中设置任何属性。</span><span class="sxs-lookup"><span data-stu-id="ea550-118">The table-valued parameter rowset object properties are read only, so the consumer is not expected to set any properties in *rgPropertySets*.</span></span>  
  
 <span data-ttu-id="ea550-119">对于每个 DBCOLUMNDESC 结构中的 rgPropertySets 成员，使用者可为每列指定附加属性\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea550-119">For the *rgPropertySets* member of each DBCOLUMNDESC structure, the consumer can specify additional properties for each column.</span></span> <span data-ttu-id="ea550-120">这些属性属于 DBPROPSET_SQLSERVERCOLUMN 属性集。</span><span class="sxs-lookup"><span data-stu-id="ea550-120">These properties belong to the DBPROPSET_SQLSERVERCOLUMN property set.</span></span> <span data-ttu-id="ea550-121">它们支持您为每一列指定计算设置和默认设置。</span><span class="sxs-lookup"><span data-stu-id="ea550-121">They enable you to specify computed and default settings for each column.</span></span> <span data-ttu-id="ea550-122">它们还支持现有列属性，如为空性和标识。</span><span class="sxs-lookup"><span data-stu-id="ea550-122">They also support existing column properties, such as nullability and identity.</span></span>  
  
 <span data-ttu-id="ea550-123">要从表值参数行集对象中检索相应的信息，使用者应使用 IRowsetInfo::GetProperties。</span><span class="sxs-lookup"><span data-stu-id="ea550-123">To retrieve corresponding information from a table-valued parameter rowset object, the consumer uses IRowsetInfo::GetProperties.</span></span>  
  
 <span data-ttu-id="ea550-124">若要检索有关每个列的 null、唯一、计算和更新状态的信息，使用者使用 IColumnsRowset：： GetColumnsRowset 或 IColumnsInfo：： GetColumnInfo。</span><span class="sxs-lookup"><span data-stu-id="ea550-124">To retrieve information about the null, unique, computed, and update status of each column, the consumer use IColumnsRowset::GetColumnsRowset or IColumnsInfo::GetColumnInfo.</span></span> <span data-ttu-id="ea550-125">以下方法提供有关每个表值参数行集列的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ea550-125">These methods provide detailed information about each table-valued parameter rowset column.</span></span>  
  
 <span data-ttu-id="ea550-126">使用者指定表值参数每一列的类型。</span><span class="sxs-lookup"><span data-stu-id="ea550-126">The consumer specifies the type of each column of the table-valued parameter.</span></span> <span data-ttu-id="ea550-127">这类似于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建表时指定列的方式。</span><span class="sxs-lookup"><span data-stu-id="ea550-127">This is similar to how columns are specified when a table is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ea550-128">使用者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过*ppRowset* output 参数从 Native Client OLE DB 提供程序获取表值参数行集对象。</span><span class="sxs-lookup"><span data-stu-id="ea550-128">The consumer obtains a table-valued parameter rowset object from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider through the *ppRowset* output parameter.</span></span>  
  
## <a name="dynamic-scenario"></a><span data-ttu-id="ea550-129">动态方案</span><span class="sxs-lookup"><span data-stu-id="ea550-129">Dynamic Scenario</span></span>  
 <span data-ttu-id="ea550-130">当使用者不具有类型信息时，它应使用 IOpenRowset：： OpenRowset 来实例化表值参数行集对象。</span><span class="sxs-lookup"><span data-stu-id="ea550-130">When the consumer does not have type information, it should use IOpenRowset::OpenRowset to instantiate table-valued parameter rowset objects.</span></span> <span data-ttu-id="ea550-131">使用者只需向访问接口提供类型名称。</span><span class="sxs-lookup"><span data-stu-id="ea550-131">All the consumer has to provide to the provider is the type name.</span></span>  
  
 <span data-ttu-id="ea550-132">在此方案中，访问接口代表使用者从服务器获取有关表值参数行集对象的类型信息。</span><span class="sxs-lookup"><span data-stu-id="ea550-132">In this scenario, the provider obtains type information about a table-valued parameter rowset object from the server on behalf of the consumer.</span></span>  
  
 <span data-ttu-id="ea550-133">应按照静态方案的设置对 pTableID\*\* 和 pUnkOuter\*\* 参数进行设置。</span><span class="sxs-lookup"><span data-stu-id="ea550-133">The *pTableID* and *pUnkOuter* parameters should be set as in the static scenario.</span></span> <span data-ttu-id="ea550-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]然后，Native Client OLE DB 提供程序从服务器获取) 列信息和约束 (类型信息，并通过*ppRowset*参数返回表值参数行集对象。</span><span class="sxs-lookup"><span data-stu-id="ea550-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider then obtains the type information (column information and constraints) from the server, and return a table-valued parameter rowset object through the *ppRowset* parameter.</span></span> <span data-ttu-id="ea550-135">此操作要求与服务器通信，因此性能不如静态方案。</span><span class="sxs-lookup"><span data-stu-id="ea550-135">This operation requires communication with the server, and therefore does not perform as well as the static scenario.</span></span> <span data-ttu-id="ea550-136">动态方案仅适用于参数化过程调用。</span><span class="sxs-lookup"><span data-stu-id="ea550-136">The dynamic scenario works only with parameterized procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea550-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea550-137">See Also</span></span>  
 <span data-ttu-id="ea550-138">[表值参数 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ea550-138">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="ea550-139">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ea550-139">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
