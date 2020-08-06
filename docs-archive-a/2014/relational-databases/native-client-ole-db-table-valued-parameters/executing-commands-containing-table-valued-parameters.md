---
title: 执行包含表值参数的命令 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
author: rothja
ms.author: jroth
ms.openlocfilehash: e3f616b2b9f95ae558e444bcbdae50eae123fa4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579564"
---
# <a name="executing-commands-containing-table-valued-parameters"></a><span data-ttu-id="19261-102">执行包含表值参数的命令</span><span class="sxs-lookup"><span data-stu-id="19261-102">Executing Commands Containing Table-Valued Parameters</span></span>
  <span data-ttu-id="19261-103">执行包含表值参数的命令需要两个阶段：</span><span class="sxs-lookup"><span data-stu-id="19261-103">Executing a command that contains table-valued parameters requires two phases:</span></span>  
  
1.  <span data-ttu-id="19261-104">指定参数类型。</span><span class="sxs-lookup"><span data-stu-id="19261-104">Specify the parameter types.</span></span>  
  
2.  <span data-ttu-id="19261-105">绑定参数数据。</span><span class="sxs-lookup"><span data-stu-id="19261-105">Bind the parameter data.</span></span>  
  
## <a name="table-valued-parameter-specification"></a><span data-ttu-id="19261-106">指定表值参数</span><span class="sxs-lookup"><span data-stu-id="19261-106">Table-Valued Parameter Specification</span></span>  
 <span data-ttu-id="19261-107">使用者可以指定表值参数的类型。</span><span class="sxs-lookup"><span data-stu-id="19261-107">The consumer can specify the type of the table-valued parameter.</span></span> <span data-ttu-id="19261-108">此信息包括表值参数的类型名称。</span><span class="sxs-lookup"><span data-stu-id="19261-108">This information includes the table-valued parameter type name.</span></span> <span data-ttu-id="19261-109">如果连接的当前默认架构中不存在该表值参数的用户定义表类型，则它还包括架构名称。</span><span class="sxs-lookup"><span data-stu-id="19261-109">It also includes the schema name, if the user-defined table type for the table-valued parameter is not in the current default schema for the connection.</span></span> <span data-ttu-id="19261-110">根据服务器的支持情况，使用者还可以指定可选的元数据信息（如列的排序），以及指定特定列的所有行都具有默认值。</span><span class="sxs-lookup"><span data-stu-id="19261-110">Depending on server support, the consumer can also specify optional metadata information, such as ordering of columns, and can specify that all rows for particular columns have the default values.</span></span>  
  
 <span data-ttu-id="19261-111">要指定表值参数，使用者需要调用 ISSCommandWithParameter::SetParameterInfo，也可以选择调用 ISSCommandWithParameters::SetParameterProperties。</span><span class="sxs-lookup"><span data-stu-id="19261-111">To specify a table-valued parameter, the consumer calls ISSCommandWithParameter::SetParameterInfo, and optionally calls ISSCommandWithParameters::SetParameterProperties.</span></span> <span data-ttu-id="19261-112">对于表值参数，DBPARAMBINDINFO 结构中 pwszDataSourceType 字段的值为 DBTYPE_TABLE\*\*。</span><span class="sxs-lookup"><span data-stu-id="19261-112">For a table-valued parameter, the *pwszDataSourceType* field in the DBPARAMBINDINFO structure has a value of DBTYPE_TABLE.</span></span> <span data-ttu-id="19261-113">ulParamSize 字段设为 ~0 以指示长度是未知的\*\*。</span><span class="sxs-lookup"><span data-stu-id="19261-113">The *ulParamSize* field is set to ~0 to indicate that length is unknown.</span></span> <span data-ttu-id="19261-114">表值参数的特定属性（如架构名称、类型名称、列顺序和默认列）可以通过 ISSCommandWithParameters::SetParameterProperties 进行设置。</span><span class="sxs-lookup"><span data-stu-id="19261-114">Particular properties for table-valued parameters, such as schema name, type name, column order, and default columns, can be set through ISSCommandWithParameters::SetParameterProperties.</span></span>  
  
## <a name="table-valued-parameter-binding"></a><span data-ttu-id="19261-115">绑定表值参数</span><span class="sxs-lookup"><span data-stu-id="19261-115">Table-Valued Parameter Binding</span></span>  
 <span data-ttu-id="19261-116">表值参数可以是任意行集对象。</span><span class="sxs-lookup"><span data-stu-id="19261-116">A table-valued parameter can be any rowset object.</span></span> <span data-ttu-id="19261-117">访问接口在执行期间从该对象中读取数据并将表值参数发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="19261-117">The provider reads from this object while sending table-valued parameters to the server during execution.</span></span>  
  
 <span data-ttu-id="19261-118">若要绑定表值参数，使用者可调用 IAccessor::CreateAccessor。</span><span class="sxs-lookup"><span data-stu-id="19261-118">To bind the table-valued parameter, the consumer calls IAccessor::CreateAccessor.</span></span> <span data-ttu-id="19261-119">表值参数的 DBBINDING 结构的 wType 字段设置为 DBTYPE_TABLE\*\*。</span><span class="sxs-lookup"><span data-stu-id="19261-119">The *wType* field of the DBBINDING structure for the table-valued parameter is set to DBTYPE_TABLE.</span></span> <span data-ttu-id="19261-120">DBBINDING 结构的 pObject 成员为非 NULL 类型，并且 IID 的 pObject 成员设置为 IID_IRowset 或其他任何表值参数行集对象接口\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19261-120">The *pObject* member of the DBBINDING structure is non-NULL, and the *pObject*'s *iid* member is set to IID_IRowset or any other table-valued parameter rowset object interfaces.</span></span> <span data-ttu-id="19261-121">DBBINDING 结构中其余字段的设置方式应与流式 BLOB 的对应字段的设置方式相同。</span><span class="sxs-lookup"><span data-stu-id="19261-121">The remaining fields in the DBBINDING structure should be set the same way they are set for streamed BLOBs.</span></span>  
  
 <span data-ttu-id="19261-122">对于表值参数以及与表值参数关联的行集对象的绑定，存在如下限制：</span><span class="sxs-lookup"><span data-stu-id="19261-122">In the bindings for the table-valued parameter and the rowset object associated with a table-valued parameter, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="19261-123">对于表值参数行集列数据，允许使用的状态值只有 DBSTATUS_S_ISNULL 和 DBSTATUS_S_OK。</span><span class="sxs-lookup"><span data-stu-id="19261-123">The only status values allowed for table-valued parameter rowset column data are DBSTATUS_S_ISNULL and DBSTATUS_S_OK.</span></span> <span data-ttu-id="19261-124">DBSTATUS_S_DEFAULT 将导致失败，并且绑定的状态值将设置为 DBSTATUS_E_BADSTATUS。</span><span class="sxs-lookup"><span data-stu-id="19261-124">DBSTATUS_S_DEFAULT will result in a failure, and the bound status value will be set to DBSTATUS_E_BADSTATUS.</span></span>  
  
-   <span data-ttu-id="19261-125">可以使用状态 DBSTATUS_S_DEFAULT 标记表值参数。</span><span class="sxs-lookup"><span data-stu-id="19261-125">A table-valued parameter can be marked with the status DBSTATUS_S_DEFAULT.</span></span> <span data-ttu-id="19261-126">有效值只有 DBSTATUS_S_DEFAULT 和 DBSTATUS_S_OK。</span><span class="sxs-lookup"><span data-stu-id="19261-126">The only valid values are DBSTATUS_S_DEFAULT and DBSTATUS_S_OK.</span></span> <span data-ttu-id="19261-127">当状态设置为 DBSTATUS_S_DEFAULT 时，表值参数的值将对应一个空表。</span><span class="sxs-lookup"><span data-stu-id="19261-127">When the status is set to DBSTATUS_S_DEFAULT, the value of the table-valued parameter corresponds to an empty table.</span></span>  
  
-   <span data-ttu-id="19261-128">必须使用 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 属性将表值参数中的只读列（标识列或计算列）标记为采用默认值。</span><span class="sxs-lookup"><span data-stu-id="19261-128">Read-only columns in table-valued parameters (identity or computed columns) must be marked as default by using the SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property.</span></span> <span data-ttu-id="19261-129">此外，还必须通过 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 属性，将包含默认值的列标记为默认列，以便默认值可用于列的特定表值参数的数据值。</span><span class="sxs-lookup"><span data-stu-id="19261-129">Columns that have a default value must also be marked as default through SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property to allow the default value to be used for the column's data values for a particular table-valued parameter.</span></span> <span data-ttu-id="19261-130">访问接口将忽略为标记为采用默认值的列绑定的数据值。</span><span class="sxs-lookup"><span data-stu-id="19261-130">The provider will ignore the data values bound for the columns marked as default.</span></span>  
  
-   <span data-ttu-id="19261-131">对于具有 DBPROP_COL_AUTOINCREMENT 或 SSPROP_COL_COMPUTED 的列，数据将发送到服务器，除非还设置了 SSPROP_PARAM_TABLE_DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="19261-131">Data will be sent to the server for columns with DBPROP_COL_AUTOINCREMENT or SSPROP_COL_COMPUTED, unless SSPROP_PARAM_TABLE_DEFAULT is also set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19261-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19261-132">See Also</span></span>  
 <span data-ttu-id="19261-133">[表值参数 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="19261-133">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="19261-134">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="19261-134">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
