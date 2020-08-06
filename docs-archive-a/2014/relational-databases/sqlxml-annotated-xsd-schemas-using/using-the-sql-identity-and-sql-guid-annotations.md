---
title: 使用 sql： identity 和 sql： guid 批注 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc5c08f158911edb0a1a0638fc4bcee1e05a248c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586603"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a><span data-ttu-id="78c8f-102">使用 sql:identity 和 sql:guid 批注</span><span class="sxs-lookup"><span data-stu-id="78c8f-102">Using the sql:identity and sql:guid Annotations</span></span>
  <span data-ttu-id="78c8f-103">您可以在 `sql:identity` `sql:guid` 映射到中的数据库列的任何节点上的 XSD 架构中指定和批注 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="78c8f-103">You can specify the `sql:identity` and `sql:guid` annotations in an XSD schema on any node that maps to a database column in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="78c8f-104">updategram 格式支持 `updg:at-identity` 和 `updg:guid` 属性，而 DiffGram 格式不支持这些属性。</span><span class="sxs-lookup"><span data-stu-id="78c8f-104">Whereas the updategram format supports the `updg:at-identity` and `updg:guid` attributes, the DiffGram format does not.</span></span> <span data-ttu-id="78c8f-105">`updg:at-identity` 属性定义在更新 IDENTITY 类型列时的行为。</span><span class="sxs-lookup"><span data-stu-id="78c8f-105">The `updg:at-identity` attribute defines the behavior in updating an IDENTITY-type column.</span></span> <span data-ttu-id="78c8f-106">`updg:guid` 属性使您可以获取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 GUID 值，并将其用于 updategram 中。</span><span class="sxs-lookup"><span data-stu-id="78c8f-106">The `updg:guid` attribute allows you to obtain a GUID value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and use it in the updategram.</span></span> <span data-ttu-id="78c8f-107">有关详细信息和工作示例，请参阅[使用 XML Updategram 插入数据 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="78c8f-107">For more information and working samples, see [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="78c8f-108">`sql:identity` 和 `sql:guid` 批注将此功能扩展至 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="78c8f-108">The `sql:identity` and `sql:guid` annotations extend this functionality to DiffGrams.</span></span>  
  
 <span data-ttu-id="78c8f-109">执行 DiffGram 时，应首先将其转换为 updategram，然后再执行该 updategram。</span><span class="sxs-lookup"><span data-stu-id="78c8f-109">When you execute a DiffGram, it is first converted to an updategram, and then the updategram is executed.</span></span> <span data-ttu-id="78c8f-110">通过在 XSD 架构中指定 `sql:identity` 和 `sql:guid` 批注，您实际上正在定义 updategram 的行为。</span><span class="sxs-lookup"><span data-stu-id="78c8f-110">By specifying the `sql:identity` and `sql:guid` annotations in the XSD schema, you are in fact defining the behavior of an updategram.</span></span> <span data-ttu-id="78c8f-111">因此，所有批注都在 updategram 的上下文中进行描述。</span><span class="sxs-lookup"><span data-stu-id="78c8f-111">Therefore, all the annotations are described in the context of an updategram.</span></span> <span data-ttu-id="78c8f-112">这些批注可用于 DiffGram 和 updategram；但是，updategram 已提供了一种更强大的处理标识和 GUID 值的方式。</span><span class="sxs-lookup"><span data-stu-id="78c8f-112">The annotations can be used both for DiffGrams and updategrams; however, updategrams already provide a more powerful way of handling identity and GUID values.</span></span>  
  
 <span data-ttu-id="78c8f-113">可以针对复杂内容元素定义 `sql:identity` 和 `sql:guid` 批注。</span><span class="sxs-lookup"><span data-stu-id="78c8f-113">The `sql:identity` and `sql:guid` annotations can be defined on a complex content element.</span></span>  
  
## <a name="sqlidentity-annotation"></a><span data-ttu-id="78c8f-114">sql:identity 批注</span><span class="sxs-lookup"><span data-stu-id="78c8f-114">sql:identity Annotation</span></span>  
 <span data-ttu-id="78c8f-115">您可以在映射到 IDENTITY 类型的数据库列的任何节点上的 XSD 架构中指定 `sql:identity` 批注。</span><span class="sxs-lookup"><span data-stu-id="78c8f-115">You can specify the `sql:identity` annotation in the XSD schema on any node that maps to an IDENTITY-type database column.</span></span> <span data-ttu-id="78c8f-116">为此批注指定的值定义了如何通过使用 updategram 中提供的值来修改列或通过忽略值（在这种情况下，为) 使用生成的值）来 (更新 IDENTITY 类型的列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="78c8f-116">The value specified for this annotation defines how the IDENTITY-type column is updated (either by using the value provided in the updategram to modify the column or by ignoring the value, in which case a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generated value is used for this column).</span></span>  
  
 <span data-ttu-id="78c8f-117">可以为 `sql:identity` 批注分配两个值：</span><span class="sxs-lookup"><span data-stu-id="78c8f-117">The `sql:identity` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="78c8f-118">ignore</span><span class="sxs-lookup"><span data-stu-id="78c8f-118">ignore</span></span>  
 <span data-ttu-id="78c8f-119">指示 updategram 忽略在其中为该列提供的任何值，并依赖于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成标识值。</span><span class="sxs-lookup"><span data-stu-id="78c8f-119">Directs the updategram to ignore any value that is provided in the updategram for that column and to rely on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate the identity value.</span></span>  
  
 <span data-ttu-id="78c8f-120">useValue</span><span class="sxs-lookup"><span data-stu-id="78c8f-120">useValue</span></span>  
 <span data-ttu-id="78c8f-121">指示 updategram 使用在其中提供的值来更新 IDENTITY 类型的列。</span><span class="sxs-lookup"><span data-stu-id="78c8f-121">Directs the updategram to use the value that is provided in the updategram to update the IDENTITY-type column.</span></span> <span data-ttu-id="78c8f-122">updategram 不会检查列是否为标识值。</span><span class="sxs-lookup"><span data-stu-id="78c8f-122">An updategram does not check whether the column is an identity value or not.</span></span>  
  
 <span data-ttu-id="78c8f-123">如果 updategram 已为 IDENTITY 类型的列指定值，必须在该架构中指定 `sql:identity="useValue"`。</span><span class="sxs-lookup"><span data-stu-id="78c8f-123">If the updategram specifies a value for the IDENTITY-type column, the `sql:identity="useValue"` must be specified in the schema.</span></span>  
  
## <a name="sqlguid-annotation"></a><span data-ttu-id="78c8f-124">sql:guid 批注</span><span class="sxs-lookup"><span data-stu-id="78c8f-124">sql:guid Annotation</span></span>  
 <span data-ttu-id="78c8f-125">updategram 可以使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成一个 GUID 值，并将此值用于该 updategram 中。</span><span class="sxs-lookup"><span data-stu-id="78c8f-125">An updategram can have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generate a GUID value and then use this value in the updategram.</span></span> <span data-ttu-id="78c8f-126">在 DiffGram 上下文中，您可以使用 `sql:guid` 批注指定是使用由 SQL Server 生成的 GUID 值还是使用在 updategram 中为该列提供的值。</span><span class="sxs-lookup"><span data-stu-id="78c8f-126">In the context of DiffGrams, you can use the `sql:guid` annotation to specify whether to use a GUID value that is generated by SQL Server or use the value that is provided in the updategram for that column.</span></span>  
  
 <span data-ttu-id="78c8f-127">可以为 `sql:guid` 批注分配两个值：</span><span class="sxs-lookup"><span data-stu-id="78c8f-127">The `sql:guid` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="78c8f-128">generate</span><span class="sxs-lookup"><span data-stu-id="78c8f-128">generate</span></span>  
 <span data-ttu-id="78c8f-129">指定应在更新操作中使用由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成的该列的 GUID。</span><span class="sxs-lookup"><span data-stu-id="78c8f-129">Specifies that the GUID generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] be used for that column in the update operation.</span></span>  
  
 <span data-ttu-id="78c8f-130">useValue</span><span class="sxs-lookup"><span data-stu-id="78c8f-130">useValue</span></span>  
 <span data-ttu-id="78c8f-131">指定在 updategram 中指定的值可以用于该列。</span><span class="sxs-lookup"><span data-stu-id="78c8f-131">Specifies that the value specified in the updategram be used for the column.</span></span> <span data-ttu-id="78c8f-132">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="78c8f-132">This is the default value.</span></span>  
  
  
