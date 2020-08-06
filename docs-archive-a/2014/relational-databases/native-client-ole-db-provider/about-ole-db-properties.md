---
title: 关于 OLE DB 属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4eb80ab9c0ab90da11d8580e9a2983455b676bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688888"
---
# <a name="about-ole-db-properties"></a><span data-ttu-id="6885e-102">关于 OLE DB 属性</span><span class="sxs-lookup"><span data-stu-id="6885e-102">About OLE DB Properties</span></span>
  <span data-ttu-id="6885e-103">使用者设置属性值以请求特定的对象行为。</span><span class="sxs-lookup"><span data-stu-id="6885e-103">Consumers set property values to request specific object behavior.</span></span> <span data-ttu-id="6885e-104">例如，使用者使用属性以指定要由行集公开的接口。</span><span class="sxs-lookup"><span data-stu-id="6885e-104">For example, consumers use properties to specify the interfaces to be exposed by a rowset.</span></span> <span data-ttu-id="6885e-105">使用者获得属性值，以确定对象（比如行集、会话或数据源对象）的功能。</span><span class="sxs-lookup"><span data-stu-id="6885e-105">Consumers get the property values to determine the capabilities of an object, such as a rowset, a session, or a data source object.</span></span>  
  
 <span data-ttu-id="6885e-106">每个属性都有值、类型、说明和读/写属性，对于行集属性，还有一个用于指示是否可以逐列应用它的指示器。</span><span class="sxs-lookup"><span data-stu-id="6885e-106">Each property has a value, type, description, and read/write attribute, and for rowset properties, an indicator of whether it can be applied on a column-by-column basis.</span></span>  
  
 <span data-ttu-id="6885e-107">属性由一个 GUID 和一个表示属性 ID 的整数进行标识。</span><span class="sxs-lookup"><span data-stu-id="6885e-107">A property is identified by a GUID and an integer representing the property ID.</span></span> <span data-ttu-id="6885e-108">属性集是所有具有相同 GUID 的一组属性。</span><span class="sxs-lookup"><span data-stu-id="6885e-108">A property set is a set of all properties that share the same GUID.</span></span> <span data-ttu-id="6885e-109">除了预定义的 OLE DB 属性集以外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序还实现了特定于访问接口的属性集和属性。</span><span class="sxs-lookup"><span data-stu-id="6885e-109">In addition to the predefined OLE DB property sets, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements provider-specific property sets and properties in them.</span></span> <span data-ttu-id="6885e-110">每个属性属于一个或多个属性组。</span><span class="sxs-lookup"><span data-stu-id="6885e-110">Each property belongs to one or more property groups.</span></span> <span data-ttu-id="6885e-111">属性组是应用于特定对象的所有属性所形成的组。</span><span class="sxs-lookup"><span data-stu-id="6885e-111">A property group is the group of all properties that apply to a particular object.</span></span> <span data-ttu-id="6885e-112">属性组包括初始化属性组、数据源属性组、会话属性组、行集属性组、表属性组和列属性组等等。</span><span class="sxs-lookup"><span data-stu-id="6885e-112">Some property groups include the initialization property group, data source property group, session property group, rowset property group, table property group, and column property group.</span></span> <span data-ttu-id="6885e-113">在每个这样的属性组中都有属性。</span><span class="sxs-lookup"><span data-stu-id="6885e-113">There are properties in each of these property groups.</span></span>  
  
 <span data-ttu-id="6885e-114">设置属性值涉及：</span><span class="sxs-lookup"><span data-stu-id="6885e-114">Setting property values involves:</span></span>  
  
1.  <span data-ttu-id="6885e-115">确定要设置值的属性。</span><span class="sxs-lookup"><span data-stu-id="6885e-115">Determining the properties for which to set values.</span></span>  
  
2.  <span data-ttu-id="6885e-116">确定包含所标识属性的属性集。</span><span class="sxs-lookup"><span data-stu-id="6885e-116">Determining the property sets that contain the identified properties.</span></span>  
  
3.  <span data-ttu-id="6885e-117">分配 DBPROPSET 结构数组，每个标识的属性集一个。</span><span class="sxs-lookup"><span data-stu-id="6885e-117">Allocating an array of DBPROPSET structures, one for each identified property set.</span></span>  
  
4.  <span data-ttu-id="6885e-118">为每个属性集分配 DBPROP 结构数组。</span><span class="sxs-lookup"><span data-stu-id="6885e-118">Allocating an array of DBPROP structures for each property set.</span></span> <span data-ttu-id="6885e-119">每个数组中的元素个数是属于该属性集的属性（在步骤 1 中标识）的个数。</span><span class="sxs-lookup"><span data-stu-id="6885e-119">The number of elements in each array is the number of properties (identified in Step 1) that belong to that property set.</span></span>  
  
5.  <span data-ttu-id="6885e-120">填充每个属性的 DBPROP 结构。</span><span class="sxs-lookup"><span data-stu-id="6885e-120">Filling in the DBPROP structure for each property.</span></span>  
  
6.  <span data-ttu-id="6885e-121">在每个属性集的 DBPROPSET 结构中，填充信息（属性集 GUID、元素的计数以及对应的 DBPROP 数组的指针）。</span><span class="sxs-lookup"><span data-stu-id="6885e-121">Filling in information (property set GUID, count of number of elements, and a pointer to the corresponding DBPROP array) in the DBPROPSET structure for each property set.</span></span>  
  
7.  <span data-ttu-id="6885e-122">调用方法以设置属性，并传递 DBPROPSET 结构的计数和数组。</span><span class="sxs-lookup"><span data-stu-id="6885e-122">Calling a method to set properties and passing the count and the array of DBPROPSET structures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6885e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6885e-123">See Also</span></span>  
 <span data-ttu-id="6885e-124">[创建 SQL Server Native Client OLE DB 提供程序应用程序](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="6885e-124">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="6885e-125">属性 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="6885e-125">Properties (OLE DB)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
