---
title: 表值参数类型发现 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab8d837e4ddf74256e4bae70f772557ec8ff67f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690081"
---
# <a name="table-valued-parameter-type-discovery"></a><span data-ttu-id="e7aae-102">表值参数类型发现</span><span class="sxs-lookup"><span data-stu-id="e7aae-102">Table-Valued Parameter Type Discovery</span></span>
  <span data-ttu-id="e7aae-103">使用者（即使用 Native Client OLE DB 提供程序的客户端应用程序） [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以发现每个命令参数的类型（如果命令文本已提供给 OLE DB 提供程序）。</span><span class="sxs-lookup"><span data-stu-id="e7aae-103">The consumer-that is, the client application using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-can discover the type of each command parameter if the command text has been given to the OLE DB Provider.</span></span> <span data-ttu-id="e7aae-104">了解表值参数的类型之后，使用者可以发现表值参数各列的元数据信息。</span><span class="sxs-lookup"><span data-stu-id="e7aae-104">After the type of a table-valued parameter is known, the consumer can discover the metadata information for each individual column of the table-valued parameter.</span></span>  
  
 <span data-ttu-id="e7aae-105">对于多数参数类型，ICommandWithParameters::GetParameterInfo 都支持过程参数的类型信息。</span><span class="sxs-lookup"><span data-stu-id="e7aae-105">The type information of procedure parameters is supported by ICommandWithParameters::GetParameterInfo for most parameter types.</span></span> <span data-ttu-id="e7aae-106">从开始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，由于引入了用户定义的类型和 `xml` 数据类型，GetParameterInfo 方法不足以实现此目的，因为无法通过 ICommandWithParameters (名称、架构和目录) 提供用户定义的类型信息。</span><span class="sxs-lookup"><span data-stu-id="e7aae-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], with the introduction of user-defined types and the `xml` data type, the GetParameterInfo method was not sufficient for this purpose because it was not possible to provide user-defined type information (name, schema, and catalog) through ICommandWithParameters.</span></span> <span data-ttu-id="e7aae-107">因此，定义了一个新接口 ISSCommandWithParameters 来提供扩展类型信息。</span><span class="sxs-lookup"><span data-stu-id="e7aae-107">A new interface, ISSCommandWithParameters, was defined to provide extended type information.</span></span>  
  
 <span data-ttu-id="e7aae-108">对于表值参数，同样使用 ISSCommandWithParameters 接口发现详细信息。</span><span class="sxs-lookup"><span data-stu-id="e7aae-108">For table-valued parameters, you also use the ISSCommandWithParameters interface to discover detailed information.</span></span> <span data-ttu-id="e7aae-109">在准备好命令对象之后，客户端调用 ISSCommandWithParameters::GetParameterInfo。</span><span class="sxs-lookup"><span data-stu-id="e7aae-109">The client calls ISSCommandWithParameters::GetParameterInfo after preparing the command object.</span></span> <span data-ttu-id="e7aae-110">对于表值参数，访问接口将 DBPARAMINFO 结构的 wType 成员设置为 DBTYPE_TABLE\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7aae-110">For table-valued parameters, the *wType* member of the DBPARAMINFO structure is set to DBTYPE_TABLE by the provider.</span></span> <span data-ttu-id="e7aae-111">DBPARAMINFO 结构的 ulParamSize 字段的值为 ~0\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7aae-111">The *ulParamSize* field of DBPARAMINFO structure has a value of ~0.</span></span>  
  
 <span data-ttu-id="e7aae-112">使用者随后使用 ISSCommandWithParameters::GetParameterProperties 请求获取附加属性（表值参数类型目录名称、表值参数类型架构名称、表值参数类型名称、列排序和默认列）。</span><span class="sxs-lookup"><span data-stu-id="e7aae-112">The consumer would then request additional properties (table-valued parameter type catalog name, table-valued parameter type schema name, table-valued parameter type name, column ordering, and default columns) by using ISSCommandWithParameters::GetParameterProperties.</span></span>  
  
 <span data-ttu-id="e7aae-113">了解类型名称之后，要检索各个列信息，使用者必须调用 IOpenRowset::OpenRowsetor ，或者通过将表值参数类型名称指定为表名来获取 DBSCHEMA_TABLE_TYPE_COLUMNS 行集。</span><span class="sxs-lookup"><span data-stu-id="e7aae-113">After the type name is known, to retrieve the individual column information the consumer must either call IOpenRowset::OpenRowsetor obtain the DBSCHEMA_TABLE_TYPE_COLUMNS rowset by specifying the table-valued parameter type name as the table name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7aae-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7aae-114">See Also</span></span>  
 <span data-ttu-id="e7aae-115">[表值参数 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="e7aae-115">[Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="e7aae-116">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="e7aae-116">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
