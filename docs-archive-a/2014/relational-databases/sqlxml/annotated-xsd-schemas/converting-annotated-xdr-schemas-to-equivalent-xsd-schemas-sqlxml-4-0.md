---
title: " (SQLXML 4.0) ，将带批注的 XDR 架构转换为等效的 XSD 架构 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: rothja
ms.author: jroth
ms.openlocfilehash: c36eb17aacb61a47fad0f389de9a3c216202827d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588426"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a><span data-ttu-id="aeddf-102">将带批注的 XDR 架构转换为等效的 XSD 架构 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="aeddf-102">Converting Annotated XDR Schemas to Equivalent XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="aeddf-103">XML 架构定义 (XSD) 语言是精简 XML 数据 (XDR) 架构定义语言的后继版本。</span><span class="sxs-lookup"><span data-stu-id="aeddf-103">The XML Schema Definition (XSD) language is the successor to the XML-Data Reduced (XDR) schema definition language.</span></span> <span data-ttu-id="aeddf-104">随着在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中引入对 XSD 的支持，它假定新的带批注的架构是使用 XSD 创建的。</span><span class="sxs-lookup"><span data-stu-id="aeddf-104">With the introduction of XSD support in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, it is assumed that new annotated schemas are created using XSD.</span></span> <span data-ttu-id="aeddf-105">SQLXML 4.0 包括一个 XDR 到 XSD 转换器工具，此工具旨在帮助您将现有带批注的 XDR 架构转换为等效的 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="aeddf-105">SQLXML 4.0 includes an XDR to XSD converter tool that is designed to help you convert your existing annotated XDR schemas to equivalent XSD schemas.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aeddf-106">仅当要将带批注的 XDR 架构转换为 XSD 以与 SQLXML 4.0 一起使用时才应使用此工具。</span><span class="sxs-lookup"><span data-stu-id="aeddf-106">Use this tool only when you want to convert annotated XDR schemas to XSD for use with SQLXML 4.0.</span></span> <span data-ttu-id="aeddf-107">这并不是通用 XDR 到 XSD 转换器工具。</span><span class="sxs-lookup"><span data-stu-id="aeddf-107">This is not a general purpose XDR to XSD converter tool.</span></span> <span data-ttu-id="aeddf-108">在其他环境中使用转换的 XSD 架构时，其行为可能与原始 XDR 架构的行为有所不同。</span><span class="sxs-lookup"><span data-stu-id="aeddf-108">The converted XSD schemas may not behave the same as the original XDR schemas when used in other environments.</span></span>  
  
 <span data-ttu-id="aeddf-109">如果输入 XDR 文件在 XML 声明中指定了编码，这将成为生成的 XSD 输出文件的编码。</span><span class="sxs-lookup"><span data-stu-id="aeddf-109">If the input XDR file specifies the encoding within the XML declaration, this becomes the encoding of the XSD output file that is generated.</span></span>  
  
 <span data-ttu-id="aeddf-110">转换器工具 (Cvtschema.exe) 安装在 Program Files\SQLXML 4.0\bin 文件夹中，并在命令提示符下执行。</span><span class="sxs-lookup"><span data-stu-id="aeddf-110">The converter tool (Cvtschema.exe) is installed in the Program Files\SQLXML 4.0\bin folder and is executed at the command prompt.</span></span>  
  
 <span data-ttu-id="aeddf-111">常规语法如下：</span><span class="sxs-lookup"><span data-stu-id="aeddf-111">This is the general syntax:</span></span>  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 <span data-ttu-id="aeddf-112">其中：</span><span class="sxs-lookup"><span data-stu-id="aeddf-112">Where:</span></span>  
  
 <span data-ttu-id="aeddf-113">XDRFileName</span><span class="sxs-lookup"><span data-stu-id="aeddf-113">XDRFileName</span></span>  
 <span data-ttu-id="aeddf-114">为要转换为 XSD 的 XDR 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="aeddf-114">Is the name of the XDR file that is to be converted to XSD.</span></span> <span data-ttu-id="aeddf-115">此工具将读取输入 XDR 文件，并在当前工作目录中创建 XSD 输出文件。</span><span class="sxs-lookup"><span data-stu-id="aeddf-115">The tool reads the input XDR file and creates an XSD output file in the current working directory.</span></span> <span data-ttu-id="aeddf-116">如果输入文件具有 .xdr 或 .xml 扩展名，则将使用相同的名称但使用 .xsd 扩展名创建输出 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="aeddf-116">If the input file has an .xdr or .xml extension, the output XSD file is created with the same name but with an .xsd extension.</span></span> <span data-ttu-id="aeddf-117">如果输入文件扩展名不是 .xml 或 .xdr（或者缺少扩展名），则将使用相同的名称创建输出文件，并将 .xsd 扩展名追加到输入文件名。</span><span class="sxs-lookup"><span data-stu-id="aeddf-117">If the input file extension is other than .xml or .xdr (or if the extension is missing), the output file is created with the same name and the .xsd extension is appended to the input file name.</span></span> <span data-ttu-id="aeddf-118">例如，如果输入 XDR 文件名为 SampleFile.abc，则生成的 XSD 将保存为 SampleFile.abc.xsd。</span><span class="sxs-lookup"><span data-stu-id="aeddf-118">For example, if the input XDR file name is SampleFile.abc, the resulting XSD is saved as SampleFile.abc.xsd.</span></span>  
  
 <span data-ttu-id="aeddf-119">-y</span><span class="sxs-lookup"><span data-stu-id="aeddf-119">-y</span></span>  
 <span data-ttu-id="aeddf-120">（可选）用转换器工具生成的 XSD 文件覆盖现有 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="aeddf-120">(Optional) Overwrites the existing XSD file with the XSD file that is generated by the converter tool.</span></span> <span data-ttu-id="aeddf-121">如果未指定此标志，则此工具将提示您指定是否要覆盖现有 XSD 文件，并且您可以选择更改输出文件名。</span><span class="sxs-lookup"><span data-stu-id="aeddf-121">If the flag is not specified, the tool prompts you to specify whether you want to overwrite the existing XSD file and gives you the option to change the output file name.</span></span>  
  
 <span data-ttu-id="aeddf-122">-w</span><span class="sxs-lookup"><span data-stu-id="aeddf-122">-w</span></span>  
 <span data-ttu-id="aeddf-123">（可选）返回在转换过程中由此工具生成的一般警告。</span><span class="sxs-lookup"><span data-stu-id="aeddf-123">(Optional) Returns nonfatal warnings that are generated in the conversion process by the tool.</span></span> <span data-ttu-id="aeddf-124">默认情况下，此工具仅为致命错误显示消息。</span><span class="sxs-lookup"><span data-stu-id="aeddf-124">By default, the tool displays messages only for fatal errors.</span></span>  
  
 <span data-ttu-id="aeddf-125">-?</span><span class="sxs-lookup"><span data-stu-id="aeddf-125">-?</span></span>  
 <span data-ttu-id="aeddf-126">返回可以随 `cvtschema` 指定的选项列表以及解释。</span><span class="sxs-lookup"><span data-stu-id="aeddf-126">Returns a list of options that you can specify with `cvtschema`, along with an explanation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeddf-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aeddf-127">See Also</span></span>  
 <span data-ttu-id="aeddf-128">[将 XSD 数据类型映射到 XPath 数据类型 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="aeddf-128">[Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="aeddf-129">SQLXML 4.0 &#40;的 XSD 批注&#41;</span><span class="sxs-lookup"><span data-stu-id="aeddf-129">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
