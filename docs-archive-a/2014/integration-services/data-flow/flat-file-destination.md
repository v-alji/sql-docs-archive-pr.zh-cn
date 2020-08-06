---
title: 平面文件目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a961b7528b13a4eaa3297343e91f1deaf2fa3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694047"
---
# <a name="flat-file-destination"></a><span data-ttu-id="ae0d6-102">平面文件目标</span><span class="sxs-lookup"><span data-stu-id="ae0d6-102">Flat File Destination</span></span>
  <span data-ttu-id="ae0d6-103">平面文件目标将数据写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-103">The Flat File destination writes data to a text file.</span></span> <span data-ttu-id="ae0d6-104">文本文件可以为带分隔符格式、固定宽度格式、固定宽度并使用行分隔符格式或右边未对齐格式。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-104">The text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="ae0d6-105">可以按照下列方式配置平面文件目标：</span><span class="sxs-lookup"><span data-stu-id="ae0d6-105">You can configure the Flat File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="ae0d6-106">提供在写入任何数据之前插入到文件的文本块。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-106">Provide a block of text that is inserted in the file before any data is written.</span></span> <span data-ttu-id="ae0d6-107">该文本可以提供列标题之类信息。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-107">The text can provide information such as column headings.</span></span>  
  
-   <span data-ttu-id="ae0d6-108">指定是否覆盖同名目标文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-108">Specify whether to overwrite a data in a destination file that has the same name.</span></span>  
  
 <span data-ttu-id="ae0d6-109">此目标用平面文件连接管理器访问文本文件。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-109">This destination uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="ae0d6-110">通过设置平面文件目标所用平面文件连接管理器的属性，可以指定平面文件目标如何格式化和写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-110">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="ae0d6-111">配置平面文件连接管理器时，请指定有关文件以及文件中每一列的信息。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-111">When you configure the Flat File connection manager, you specify information about the file and about each column in the file.</span></span> <span data-ttu-id="ae0d6-112">例如，指定在文件中分隔列和行的字符，而且指定每列的数据类型和长度。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-112">For example, you specify the characters that delimit columns and rows in the file, and you specify the data type and the length of each column.</span></span> <span data-ttu-id="ae0d6-113">有关详细信息，请参阅 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-113">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ae0d6-114">平面文件目标包括 Header 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-114">The Flat File destination includes the Header custom property.</span></span> <span data-ttu-id="ae0d6-115">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="ae0d6-116">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../expressions/use-property-expressions-in-packages.md)和[平面文件自定义属性](flat-file-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [Flat File Custom Properties](flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="ae0d6-117">此目标具有一个输出。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-117">This destination has one output.</span></span> <span data-ttu-id="ae0d6-118">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-destination"></a><span data-ttu-id="ae0d6-119">配置平面文件目标</span><span class="sxs-lookup"><span data-stu-id="ae0d6-119">Configuration of the Flat File Destination</span></span>  
 <span data-ttu-id="ae0d6-120">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ae0d6-121">有关可在 **“平面文件源编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ae0d6-121">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ae0d6-122">平面文件目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="ae0d6-122">Flat File Destination Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="ae0d6-123">平面文件目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="ae0d6-123">Flat File Destination Editor &#40;Mappings Page&#41;</span></span>](../flat-file-destination-editor-mappings-page.md)  
  
 <span data-ttu-id="ae0d6-124">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-124">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="ae0d6-125">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ae0d6-125">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ae0d6-126">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ae0d6-126">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ae0d6-127">平面文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="ae0d6-127">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="ae0d6-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ae0d6-128">Related Tasks</span></span>  
 <span data-ttu-id="ae0d6-129">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0d6-129">For information about how to set the properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0d6-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae0d6-130">See Also</span></span>  
 <span data-ttu-id="ae0d6-131">[平面文件源](flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="ae0d6-131">[Flat File Source](flat-file-source.md) </span></span>  
 [<span data-ttu-id="ae0d6-132">数据流</span><span class="sxs-lookup"><span data-stu-id="ae0d6-132">Data Flow</span></span>](data-flow.md)  
  
  
