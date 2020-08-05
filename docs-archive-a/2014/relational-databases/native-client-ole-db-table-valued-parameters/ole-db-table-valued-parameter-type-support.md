---
title: OLE DB 表值参数类型支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: rothja
ms.author: jroth
ms.openlocfilehash: 48d5fd780b2eaa2fc18e39071d3b10fde897b82c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580217"
---
# <a name="ole-db-table-valued-parameter-type-support"></a><span data-ttu-id="8fe75-102">OLE DB 表值参数类型支持</span><span class="sxs-lookup"><span data-stu-id="8fe75-102">OLE DB Table-Valued Parameter Type Support</span></span>
  <span data-ttu-id="8fe75-103">本主题介绍了表值参数的 OLE DB 类型支持。</span><span class="sxs-lookup"><span data-stu-id="8fe75-103">This topic describes OLE DB type support for table-value parameters.</span></span>  
  
## <a name="table-valued-parameter-rowset-object"></a><span data-ttu-id="8fe75-104">表值参数行集对象</span><span class="sxs-lookup"><span data-stu-id="8fe75-104">Table-Valued Parameter Rowset Object</span></span>  
 <span data-ttu-id="8fe75-105">您可以创建表值参数的专用行集对象。</span><span class="sxs-lookup"><span data-stu-id="8fe75-105">You can create a specialized rowset object for table-valued parameters.</span></span> <span data-ttu-id="8fe75-106">使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 或 IOpenRowset::OpenRowset 创建表值参数行集对象。</span><span class="sxs-lookup"><span data-stu-id="8fe75-106">You create the table-valued parameter rowset object by using ITableDefinitionWithConstraints::CreateTableWithConstraints or IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="8fe75-107">为此，请将 pTableID 参数的 eKind 成员设置为 DBKIND_GUID_NAME，并提供 CLSID_ROWSET_INMEMORY 作为 guid 成员\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fe75-107">To do this, set the *eKind* member of the *pTableID* parameter to DBKIND_GUID_NAME, and provide the CLSID_ROWSET_INMEMORY as the *guid* member.</span></span> <span data-ttu-id="8fe75-108">使用 IOpenRowset::OpenRowset 时，必须在 pTableID\*\* 的 pwszName\*\* 成员中指定表值参数的服务器类型名称。</span><span class="sxs-lookup"><span data-stu-id="8fe75-108">The server type name for the table-valued parameter must be specified in the *pwszName* member of *pTableID* when using IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="8fe75-109">表值参数行集对象行为与常规 SQL Server Native Client OLE DB Provider 对象类似。</span><span class="sxs-lookup"><span data-stu-id="8fe75-109">The table-valued parameter rowset object behaves like a regular SQL Server Native Client OLE DB Provider object.</span></span>  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a><span data-ttu-id="8fe75-110">DBTYPE_TABLE</span><span class="sxs-lookup"><span data-stu-id="8fe75-110">DBTYPE_TABLE</span></span>  
 <span data-ttu-id="8fe75-111">新类型 DBTYPE_TABLE 表示表类型。</span><span class="sxs-lookup"><span data-stu-id="8fe75-111">A new type, DBTYPE_TABLE, represents a table type.</span></span> <span data-ttu-id="8fe75-112">该类型在需要 DBTYPE 的多个 OLE DB 接口中指定了表值参数。</span><span class="sxs-lookup"><span data-stu-id="8fe75-112">This type specifies table-valued parameters in various OLE DB interfaces where a DBTYPE is required.</span></span>  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 <span data-ttu-id="8fe75-113">DBTYPE_TABLE 具有与 DBTYPE_IUNKNOWN 相同的格式。</span><span class="sxs-lookup"><span data-stu-id="8fe75-113">DBTYPE_TABLE has the same format as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="8fe75-114">它是指向数据缓冲区中某个对象的指针。</span><span class="sxs-lookup"><span data-stu-id="8fe75-114">It is a pointer to an object in the data buffer.</span></span> <span data-ttu-id="8fe75-115">为完成绑定中的规范，使用者应填充 DBOBJECT 缓冲区，并将 iid 设置为某个行集对象接口 (IID_IRowset)\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fe75-115">For complete specification in the bindings, the consumer fills up the DBOBJECT buffer, with *iid* set to one of the rowset object interfaces (IID_IRowset).</span></span> <span data-ttu-id="8fe75-116">如果绑定中未指定 DBOBJECT，则将假定为 IID_IRowset。</span><span class="sxs-lookup"><span data-stu-id="8fe75-116">If no DBOBJECT is specified in the bindings, IID_IRowset will be assumed.</span></span>  
  
 <span data-ttu-id="8fe75-117">不支持任何其他类型转换为 DBTYPE_TABLE 或从 DBTYPE_TABLE 转换为任何其他类型。</span><span class="sxs-lookup"><span data-stu-id="8fe75-117">Conversions to and from DBTYPE_TABLE for any other types are not supported.</span></span> <span data-ttu-id="8fe75-118">针对 DBTYPE_TABLE 到 DBTYPE_TABLE 的转换以外的任何请求，IConvertType::CanConvert 将对不支持的转换返回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="8fe75-118">IConvertType::CanConvert will return S_FALSE for unsupported conversion for any request other than DBTYPE_TABLE to DBTYPE_TABLE conversion.</span></span> <span data-ttu-id="8fe75-119">这将假定对 Command 对象进行 DBCONVERTFLAGS_PARAMETER 转换。</span><span class="sxs-lookup"><span data-stu-id="8fe75-119">This assumes DBCONVERTFLAGS_PARAMETER on the Command object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fe75-120">方法</span><span class="sxs-lookup"><span data-stu-id="8fe75-120">Methods</span></span>  
 <span data-ttu-id="8fe75-121">若要了解支持表值参数的 OLE DB 方法，请参阅 [OLE DB 表值参数类型支持（方法）](ole-db-table-valued-parameter-type-support-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="8fe75-121">For information about OLE DB methods that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;](ole-db-table-valued-parameter-type-support-methods.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8fe75-122">属性</span><span class="sxs-lookup"><span data-stu-id="8fe75-122">Properties</span></span>  
 <span data-ttu-id="8fe75-123">若要了解支持表值参数的 OLE DB 属性，请参阅 [OLE DB 表值参数类型支持（属性）](ole-db-table-valued-parameter-type-support-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8fe75-123">For information about OLE DB properties that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;](ole-db-table-valued-parameter-type-support-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe75-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fe75-124">See Also</span></span>  
 <span data-ttu-id="8fe75-125">[表值参数 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="8fe75-125">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="8fe75-126">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="8fe75-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
