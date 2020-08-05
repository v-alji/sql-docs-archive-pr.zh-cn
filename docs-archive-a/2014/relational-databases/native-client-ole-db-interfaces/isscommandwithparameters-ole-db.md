---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
ms.openlocfilehash: 295026497a97b4ce13d1a1a68de48079809390ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580232"
---
# <a name="isscommandwithparameters-ole-db"></a><span data-ttu-id="ccb5d-102">ISSCommandWithParameters (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ccb5d-102">ISSCommandWithParameters (OLE DB)</span></span>
  <span data-ttu-id="ccb5d-103">**ISSCommandWithParameters**公开对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 和用户定义类型 (UDT) 的支持。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-103">**ISSCommandWithParameters** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT).</span></span> <span data-ttu-id="ccb5d-104">这是一个可选接口，它继承自 core OLE DB interface **ICommandWithParameters**。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-104">This is an optional interface that inherits from the core OLE DB interface **ICommandWithParameters**.</span></span> <span data-ttu-id="ccb5d-105">除了从**ICommandWithParameters**继承的三个方法;**GetParameterInfo**、 **MapParameterNames**和**SetParameterInfo**;**ISSCommandWithParameters**提供了两种新方法用于处理特定于服务器的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-105">In addition to the three methods inherited from **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, and **SetParameterInfo**; **ISSCommandWithParameters** provides two new methods that are used to handle server specific data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccb5d-106">使用服务组件时，可以使用**ISSCommandWithParameters**接口，但服务组件本身将不会使用此接口。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-106">The **ISSCommandWithParameters** interface can be used when Service Components are used, but the Service Components themselves will not use this interface.</span></span>  
  
|<span data-ttu-id="ccb5d-107">方法</span><span class="sxs-lookup"><span data-stu-id="ccb5d-107">Method</span></span>|<span data-ttu-id="ccb5d-108">说明</span><span class="sxs-lookup"><span data-stu-id="ccb5d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccb5d-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb5d-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-getparameterproperties-ole-db.md)|<span data-ttu-id="ccb5d-110">对传递到该命令的每个 UDT 或 XML 参数返回数组中的一个 SSPARAMPROPS 属性集结构，但是对于其他类型的参数，不会返回任何内容\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-110">Returns one **SSPARAMPROPS** property set structure in the array for each UDT or XML parameter passed to the command, but none is returned for other types of parameters.</span></span>|  
|[<span data-ttu-id="ccb5d-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb5d-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-setparameterproperties-ole-db.md)|<span data-ttu-id="ccb5d-112">按照序号基于每个参数设置参数属性，或者通过指定 SSPARAMPROPS 结构数组来设置大容量参数属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccb5d-112">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of **SSPARAMPROPS** structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccb5d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccb5d-113">See Also</span></span>  
 <span data-ttu-id="ccb5d-114">[接口 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ccb5d-114">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="ccb5d-115">[使用 XML 数据类型](../native-client/features/using-xml-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ccb5d-115">[Using XML Data Types](../native-client/features/using-xml-data-types.md) </span></span>  
 [<span data-ttu-id="ccb5d-116">使用用户定义类型</span><span class="sxs-lookup"><span data-stu-id="ccb5d-116">Using User-Defined Types</span></span>](../native-client/features/using-user-defined-types.md)  
  
  
