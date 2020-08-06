---
title: XML 源编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e40ca6ef2d8fbcd10b756a2ce15f33730c367d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590904"
---
# <a name="xml-source-editor-connection-manager-page"></a><span data-ttu-id="f6c36-102">XML 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f6c36-102">XML Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f6c36-103">可以使用 **“XML 源编辑器”** 的 **“连接管理器”** 页指定 XML 文件和转换 XML 数据的 XSD。</span><span class="sxs-lookup"><span data-stu-id="f6c36-103">Use the **Connection Manager** page of the **XML Source Editor** to specify an XML file and the XSD that transforms the XML data.</span></span>  
  
 <span data-ttu-id="f6c36-104">有关 XML 源的详细信息，请参阅 [XML Source](data-flow/xml-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f6c36-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f6c36-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="f6c36-105">Static Options</span></span>  
 <span data-ttu-id="f6c36-106">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="f6c36-106">**Data access mode**</span></span>  
 <span data-ttu-id="f6c36-107">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="f6c36-107">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="f6c36-108">值</span><span class="sxs-lookup"><span data-stu-id="f6c36-108">Value</span></span>|<span data-ttu-id="f6c36-109">说明</span><span class="sxs-lookup"><span data-stu-id="f6c36-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6c36-110">XML 文件位置</span><span class="sxs-lookup"><span data-stu-id="f6c36-110">XML file location</span></span>|<span data-ttu-id="f6c36-111">从 XML 文件检索数据。</span><span class="sxs-lookup"><span data-stu-id="f6c36-111">Retrieve data from an XML file.</span></span>|  
|<span data-ttu-id="f6c36-112">来自变量的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="f6c36-112">XML file from variable</span></span>|<span data-ttu-id="f6c36-113">在变量中指定 XML 文件名。</span><span class="sxs-lookup"><span data-stu-id="f6c36-113">Specify the XML file name in a variable.</span></span><br /><br /> <span data-ttu-id="f6c36-114">**相关信息**：[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="f6c36-114">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="f6c36-115">来自变量的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="f6c36-115">XML data from variable</span></span>|<span data-ttu-id="f6c36-116">从变量检索 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="f6c36-116">Retrieve XML data from a variable.</span></span>|  
  
 <span data-ttu-id="f6c36-117">**使用内联架构**</span><span class="sxs-lookup"><span data-stu-id="f6c36-117">**Use inline schema**</span></span>  
 <span data-ttu-id="f6c36-118">指定 XML 源数据本身是否包含 XSD 架构（用于定义和验证 XML 源数据的结构和数据）。</span><span class="sxs-lookup"><span data-stu-id="f6c36-118">Specify whether the XML source data itself contains the XSD schema that defines and validates its structure and data.</span></span>  
  
 <span data-ttu-id="f6c36-119">**XSD 位置**</span><span class="sxs-lookup"><span data-stu-id="f6c36-119">**XSD location**</span></span>  
 <span data-ttu-id="f6c36-120">键入 XSD 架构文件的路径和文件名，或者可以单击“浏览”\*\*\*\* 定位该文件。</span><span class="sxs-lookup"><span data-stu-id="f6c36-120">Type the path and file name of the XSD schema file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f6c36-121">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="f6c36-121">**Browse**</span></span>  
 <span data-ttu-id="f6c36-122">使用“打开”\*\*\*\* 对话框定位到 XSD 架构文件。</span><span class="sxs-lookup"><span data-stu-id="f6c36-122">Use the **Open** dialog box to locate the XSD schema file.</span></span>  
  
 <span data-ttu-id="f6c36-123">**生成 XSD**</span><span class="sxs-lookup"><span data-stu-id="f6c36-123">**Generate XSD**</span></span>  
 <span data-ttu-id="f6c36-124">使用“另存为”\*\*\*\* 对话框可以为自动生成的 XSD 架构文件选择位置。</span><span class="sxs-lookup"><span data-stu-id="f6c36-124">Use the **Save As** dialog box to select a location for the auto-generated XSD schema file.</span></span> <span data-ttu-id="f6c36-125">编辑器将根据 XML 数据的结构来推断架构。</span><span class="sxs-lookup"><span data-stu-id="f6c36-125">The editor infers the schema from the structure of the XML data.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="f6c36-126">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="f6c36-126">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--xml-file-location"></a><span data-ttu-id="f6c36-127">数据访问模式 = XML 文件位置</span><span class="sxs-lookup"><span data-stu-id="f6c36-127">Data access mode = XML file location</span></span>  
 <span data-ttu-id="f6c36-128">**XML 位置**</span><span class="sxs-lookup"><span data-stu-id="f6c36-128">**XML location**</span></span>  
 <span data-ttu-id="f6c36-129">键入 XML 数据文件的路径和文件名，或者通过单击“浏览”\*\*\*\* 查找文件。</span><span class="sxs-lookup"><span data-stu-id="f6c36-129">Type the path and file name of the XML data file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f6c36-130">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="f6c36-130">**Browse**</span></span>  
 <span data-ttu-id="f6c36-131">使用“打开”\*\*\*\* 对话框定位到 XML 数据文件。</span><span class="sxs-lookup"><span data-stu-id="f6c36-131">Use the **Open** dialog box to locate the XML data file.</span></span>  
  
### <a name="data-access-mode--xml-file-from-variable"></a><span data-ttu-id="f6c36-132">数据访问模式 = 来自变量的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="f6c36-132">Data access mode = XML file from variable</span></span>  
 <span data-ttu-id="f6c36-133">**变量名**</span><span class="sxs-lookup"><span data-stu-id="f6c36-133">**Variable name**</span></span>  
 <span data-ttu-id="f6c36-134">选择包含 XML 文件的路径和文件名的变量。</span><span class="sxs-lookup"><span data-stu-id="f6c36-134">Select the variable that contains the path and file name of the XML file.</span></span>  
  
### <a name="data-access-mode--xml-data-from-variable"></a><span data-ttu-id="f6c36-135">数据访问模式 = 来自变量的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="f6c36-135">Data access mode = XML data from variable</span></span>  
 <span data-ttu-id="f6c36-136">**变量名**</span><span class="sxs-lookup"><span data-stu-id="f6c36-136">**Variable name**</span></span>  
 <span data-ttu-id="f6c36-137">选择包含 XML 数据的变量。</span><span class="sxs-lookup"><span data-stu-id="f6c36-137">Select the variable that contains the XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c36-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6c36-138">See Also</span></span>  
 <span data-ttu-id="f6c36-139">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f6c36-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f6c36-140">[XML 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f6c36-140">[XML Source Editor &#40;Columns Page&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="f6c36-141">[XML 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f6c36-141">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="f6c36-142">使用 XML 源提取数据</span><span class="sxs-lookup"><span data-stu-id="f6c36-142">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
