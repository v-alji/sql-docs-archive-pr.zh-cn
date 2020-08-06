---
title: BLOB 和 OLE 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: rothja
ms.author: jroth
ms.openlocfilehash: 15f8b4915ba9b05a5be19854a2e27a2e8ff3a346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693800"
---
# <a name="blobs-and-ole-objects"></a><span data-ttu-id="a14f6-102">BLOB 和 OLE 对象</span><span class="sxs-lookup"><span data-stu-id="a14f6-102">BLOBs and OLE Objects</span></span>
  <span data-ttu-id="a14f6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开了**ISequentialStream**接口，以支持使用者访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**、 **text**、 **image**、 \*\*varchar (max) \*\*、 \*\*nvarchar (max) \*\*、 \*\*varbinary (max) \*\*和 xml 数据类型为二进制大型对象 (blob) 。</span><span class="sxs-lookup"><span data-stu-id="a14f6-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISequentialStream** interface to support consumer access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, and xml data types as binary large objects (BLOBs).</span></span> <span data-ttu-id="a14f6-104">通过对 ISequentialStream 执行 Read 方法，使用者可以用便于管理的方式成块检索大量数据\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a14f6-104">The **Read** method on **ISequentialStream** lets the consumer retrieve much data in manageable chunks.</span></span>  
  
 <span data-ttu-id="a14f6-105">有关演示此功能的示例，请参阅[设置大型数据 (OLE DB)](../native-client-ole-db-how-to/set-large-data-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="a14f6-105">For a sample demonstrating this feature, see [Set Large Data &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).</span></span>  
  
 <span data-ttu-id="a14f6-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当使用者在访问器中提供用于数据修改的接口指针时，Native Client OLE DB 提供程序可以使用使用者实现的**IStorage**接口。</span><span class="sxs-lookup"><span data-stu-id="a14f6-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can use a consumer-implemented **IStorage** interface when the consumer provides the interface pointer in an accessor bound for data modification.</span></span>  
  
 <span data-ttu-id="a14f6-107">对于大值数据类型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序检查**IROWSET**和 DDL 接口中的类型大小假设。</span><span class="sxs-lookup"><span data-stu-id="a14f6-107">For large value data types, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks for type size assumptions in **IRowset** and DDL interfaces.</span></span> <span data-ttu-id="a14f6-108">使用最大大小设置为 "无限制" 的**varchar**、 **nvarchar**和**varbinary**数据类型的列将通过架构行集和返回列数据类型的接口表示为 ISLONG。</span><span class="sxs-lookup"><span data-stu-id="a14f6-108">Columns with **varchar**, **nvarchar**, and **varbinary** data types with max size set to unlimited will be represented as ISLONG through the schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="a14f6-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序以) 、 (和) 分别公开**varchar (max) **、 **varbinary (max DBTYPE_STR**和**nvarchar DBTYPE_BYTES 最**大 DBTYPE_WSTR 类型。</span><span class="sxs-lookup"><span data-stu-id="a14f6-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES and DBTYPE_WSTR respectively.</span></span>  
  
 <span data-ttu-id="a14f6-110">若要使用这些类型，应用程序具有以下选项：</span><span class="sxs-lookup"><span data-stu-id="a14f6-110">To work with these types an application has the following options:</span></span>  
  
-   <span data-ttu-id="a14f6-111">绑定为字节（DBTYPE_STR、DBTYPE_BYTES 和 DBTYPE_WSTR）。</span><span class="sxs-lookup"><span data-stu-id="a14f6-111">Bind as the type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR).</span></span> <span data-ttu-id="a14f6-112">如果缓冲区不够大，将发生截断，这与早期版本中的这些类型完全相同（但是现在可以使用更大的值）。</span><span class="sxs-lookup"><span data-stu-id="a14f6-112">If the buffer is not big enough truncation will occur, exactly as for these types in previous releases (although larger values are now available).</span></span>  
  
-   <span data-ttu-id="a14f6-113">绑定为字节并指定 DBTYPE_BYREF。</span><span class="sxs-lookup"><span data-stu-id="a14f6-113">Bind as the type and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="a14f6-114">绑定为 DBTYPE_IUNKNOWN 并使用流处理。</span><span class="sxs-lookup"><span data-stu-id="a14f6-114">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="a14f6-115">如果绑定为 DBTYPE_IUNKNOWN，则使用 ISequentialStream 流功能。</span><span class="sxs-lookup"><span data-stu-id="a14f6-115">If bound to DBTYPE_IUNKNOWN, ISequentialStream stream functionality is used.</span></span> <span data-ttu-id="a14f6-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持将输出参数绑定为大值数据类型的 DBTYPE_IUNKNOWN，以便于在某些情况下，存储过程将这些数据类型作为返回值返回，并将其作为 DBTYPE_IUNKNOWN 公开给客户端。</span><span class="sxs-lookup"><span data-stu-id="a14f6-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns these data types as return values which will be exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
## <a name="storage-object-limitations"></a><span data-ttu-id="a14f6-117">存储对象限制</span><span class="sxs-lookup"><span data-stu-id="a14f6-117">Storage Object Limitations</span></span>  
  
-   <span data-ttu-id="a14f6-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序只能支持一个打开的存储对象。</span><span class="sxs-lookup"><span data-stu-id="a14f6-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can support only a single open storage object.</span></span> <span data-ttu-id="a14f6-119">尝试打开多个存储对象（以获取对多个 ISequentialStream 接口指针的引用）返回 DBSTATUS_E_CANTCREATE\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a14f6-119">Attempts to open more than one storage object (to get a reference on more than one **ISequentialStream** interface pointer) return DBSTATUS_E_CANTCREATE.</span></span>  
  
-   <span data-ttu-id="a14f6-120">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序中，DBPROP_BLOCKINGSTORAGEOBJECTS 只读属性的默认值 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="a14f6-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the default value of the DBPROP_BLOCKINGSTORAGEOBJECTS read-only property is VARIANT_TRUE.</span></span> <span data-ttu-id="a14f6-121">这指示如果存储对象处于活动状态，某些方法（存储对象上的方法除外）将失败，并返回 E_UNEXPECTED。</span><span class="sxs-lookup"><span data-stu-id="a14f6-121">This indicates that if a storage object is active, some methods (other than those on the storage objects) will fail with E_UNEXPECTED.</span></span>  
  
-   <span data-ttu-id="a14f6-122">当创建引用存储对象的行访问器时，必须将由使用者实现的存储对象提供的数据的长度识别为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序。</span><span class="sxs-lookup"><span data-stu-id="a14f6-122">The length of data presented by a consumer-implemented storage object must be made known to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider when the row accessor that references the storage object is created.</span></span> <span data-ttu-id="a14f6-123">使用者必须在用于创建取值函数的 DBBINDING 结构中绑定一个长度指示符。</span><span class="sxs-lookup"><span data-stu-id="a14f6-123">The consumer must bind a length indicator in the DBBINDING structure used for accessor creation.</span></span>  
  
-   <span data-ttu-id="a14f6-124">如果行包含多个大数据值且未 DBPROPVAL_AO_RANDOM DBPROP_ACCESSORDER，则使用者必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序支持游标的行集来检索行数据或处理所有大数据值，然后再检索其他行值。</span><span class="sxs-lookup"><span data-stu-id="a14f6-124">If a row contains more than a single large data value and DBPROP_ACCESSORDER is not DBPROPVAL_AO_RANDOM, the consumer must either use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-supported rowset to retrieve row data or process all large data values before retrieving other row values.</span></span> <span data-ttu-id="a14f6-125">如果 DBPROPVAL_AO_RANDOM DBPROP_ACCESSORDER，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序会将所有 xml 数据类型缓存为 () blob 的二进制大型对象，以便可以按任意顺序访问该数据类型。</span><span class="sxs-lookup"><span data-stu-id="a14f6-125">If DBPROP_ACCESSORDER is DBPROPVAL_AO_RANDOM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider caches all the xml data types as binary large objects (BLOBs) so that it can be accessed in any order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a14f6-126">本节内容</span><span class="sxs-lookup"><span data-stu-id="a14f6-126">In This Section</span></span>  
  
-   [<span data-ttu-id="a14f6-127">获取大型数据</span><span class="sxs-lookup"><span data-stu-id="a14f6-127">Getting Large Data</span></span>](getting-large-data.md)  
  
-   [<span data-ttu-id="a14f6-128">设置大型数据</span><span class="sxs-lookup"><span data-stu-id="a14f6-128">Setting Large Data</span></span>](setting-large-data.md)  
  
-   [<span data-ttu-id="a14f6-129">BLOB 输出参数的流支持</span><span class="sxs-lookup"><span data-stu-id="a14f6-129">Streaming Support for BLOB Output Parameters</span></span>](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="a14f6-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a14f6-130">See Also</span></span>  
 <span data-ttu-id="a14f6-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="a14f6-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="a14f6-132">使用大值类型</span><span class="sxs-lookup"><span data-stu-id="a14f6-132">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
