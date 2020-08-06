---
title: " (XMLA) 来定义和标识对象 |Microsoft Docs"
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2fd3263a2f8050c36747a81ab3473f5b405ef21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589932"
---
# <a name="defining-and-identifying-objects-xmla"></a><span data-ttu-id="93a6c-102">定义和标识对象 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="93a6c-102">Defining and Identifying Objects (XMLA)</span></span>
  <span data-ttu-id="93a6c-103">在 XML for Analysis (XMLA) 命令中，将使用对象标识符和对象引用标识对象，并使用 Analysis Services 脚本语言 (ASSL) 元素 XMLA 命令定义对象。</span><span class="sxs-lookup"><span data-stu-id="93a6c-103">Objects are identified in XML for Analysis (XMLA) commands by using object identifiers and object references, and are defined by using Analysis Services Scripting Language (ASSL) elements XMLA commands.</span></span>  
  
## <a name="object-identifiers"></a><span data-ttu-id="93a6c-104">对象标识符</span><span class="sxs-lookup"><span data-stu-id="93a6c-104">Object Identifiers</span></span>  
 <span data-ttu-id="93a6c-105">对象通过使用在的实例上定义的对象的唯一标识符进行标识 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="93a6c-105">An object is identified by using the unique identifier of the object as defined on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="93a6c-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 创建对象时，可以显式指定对象标识符，也可以由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例确定。</span><span class="sxs-lookup"><span data-stu-id="93a6c-106">Object identifiers can either be explicitly specified or determined by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] creates the object.</span></span> <span data-ttu-id="93a6c-107">可以使用[发现](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)方法检索对象标识符，以便 `Discover` 执行后续或[执行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法调用。</span><span class="sxs-lookup"><span data-stu-id="93a6c-107">You can use the [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method to retrieve object identifiers for subsequent `Discover` or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method calls.</span></span>  
  
## <a name="object-references"></a><span data-ttu-id="93a6c-108">对象引用</span><span class="sxs-lookup"><span data-stu-id="93a6c-108">Object References</span></span>  
 <span data-ttu-id="93a6c-109">一些 XMLA 命令（如[删除](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla)或[处理](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)）使用对象引用以明确的方式引用对象。</span><span class="sxs-lookup"><span data-stu-id="93a6c-109">Several XMLA commands, such as [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) or [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), use an object reference to refer to an object in an unambiguous manner.</span></span> <span data-ttu-id="93a6c-110">对象引用包含要对其执行命令的对象的对象标识符以及该对象的祖先的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="93a6c-110">An object reference contains the object identifier of the object on which a command is executed and the object identifiers of the ancestors for that object.</span></span> <span data-ttu-id="93a6c-111">例如，分区的对象引用包含分区的对象标识符，以及该分区的父度量值组、多维数据集和数据库的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="93a6c-111">For example, the object reference for a partition contains the object identifier of the partition, as well as the object identifiers of that partition's parent measure group, cube, and database.</span></span>  
  
## <a name="object-definitions"></a><span data-ttu-id="93a6c-112">对象定义</span><span class="sxs-lookup"><span data-stu-id="93a6c-112">Object Definitions</span></span>  
 <span data-ttu-id="93a6c-113">XMLA 中的[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)和[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)命令分别创建或更改实例上的对象 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="93a6c-113">The [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) and [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) commands in XMLA create or alter, respectively, objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="93a6c-114">这些对象的定义由包含 ASSL 元素的[ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)元素表示。</span><span class="sxs-lookup"><span data-stu-id="93a6c-114">The definitions for those objects are represented by an [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element that contains elements from ASSL.</span></span> <span data-ttu-id="93a6c-115">可以通过使用[ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)元素为所有主要和多个次要对象显式指定对象标识符。</span><span class="sxs-lookup"><span data-stu-id="93a6c-115">Object identifiers can be explicitly specified for all major and many minor objects by using the [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) element.</span></span> <span data-ttu-id="93a6c-116">如果不使用 `ID` 元素，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例将提供一个唯一标识符，其命名约定取决于要标识的对象。</span><span class="sxs-lookup"><span data-stu-id="93a6c-116">If the `ID` element is not used, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance provides a unique identifier, with a naming convention that depends on the object to be identified.</span></span> <span data-ttu-id="93a6c-117">有关如何使用 `Create` 和 `Alter` 命令定义对象的详细信息，请参阅[&#40;XMLA&#41;创建和更改对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="93a6c-117">For more information about how to use the `Create` and `Alter` commands to define objects, see [Creating and Altering Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a6c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93a6c-118">See Also</span></span>  
 <span data-ttu-id="93a6c-119">[&#40;XMLA&#41;的对象元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="93a6c-119">[Object Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span></span>  
 <span data-ttu-id="93a6c-120">[&#40;XMLA&#41;的 ParentObject 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="93a6c-120">[ParentObject Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span></span>  
 <span data-ttu-id="93a6c-121">[&#40;XMLA&#41;源元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="93a6c-121">[Source Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) </span></span>  
 <span data-ttu-id="93a6c-122">[&#40;XMLA&#41;的目标元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="93a6c-122">[Target Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) </span></span>  
 [<span data-ttu-id="93a6c-123">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="93a6c-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
