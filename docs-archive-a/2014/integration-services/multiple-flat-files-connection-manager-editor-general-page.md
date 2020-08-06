---
title: 多平面文件连接管理器编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.general.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f30a422794723f216d30e05f0750fb1e974e0920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691788"
---
# <a name="multiple-flat-files-connection-manager-editor-general-page"></a><span data-ttu-id="dcfbe-102">多平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="dcfbe-102">Multiple Flat Files Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="dcfbe-103">可以使用 **“多平面文件连接管理器编辑器”** 对话框的 **“常规”** 页，选择一组具有相同数据格式的文件并指定其数据格式。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-103">Use the **General** page of the **Multiple Flat Files Connection Manager Editor** dialog box to select a group of files that have the same data format, and to specify their data format.</span></span> <span data-ttu-id="dcfbe-104">多平面文件连接使得数据包可以连接到具有相同格式的一组文本文件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-104">A multiple flat files connection enables a package to connect to a group of text files that have the same format.</span></span>  
  
 <span data-ttu-id="dcfbe-105">若要了解有关多平面文件连接管理器的详细信息，请参阅 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-105">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcfbe-106">选项</span><span class="sxs-lookup"><span data-stu-id="dcfbe-106">Options</span></span>  
 <span data-ttu-id="dcfbe-107">**连接管理器名称**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-107">**Connection manager name**</span></span>  
 <span data-ttu-id="dcfbe-108">为工作流中的“多平面文件连接”提供一个唯一名称。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-108">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="dcfbe-109">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="dcfbe-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-110">**Description**</span></span>  
 <span data-ttu-id="dcfbe-111">描述此连接。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-111">Describe the connection.</span></span> <span data-ttu-id="dcfbe-112">最好按照连接的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="dcfbe-113">**文件名**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-113">**File names**</span></span>  
 <span data-ttu-id="dcfbe-114">键入要在“多平面文件连接”中使用的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-114">Type the path and file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="dcfbe-115">可以通过使用通配符指定多个文件，如示例“C:\\*.txt”中一样，也可以通过使用竖线 (|) 来分隔多个文件名。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-115">You can specify multiple files by using wildcard characters, as in the example "C:\\*.txt", or by using the vertical pipe character (|) to separate multiple file names.</span></span> <span data-ttu-id="dcfbe-116">所有文件的数据格式必须相同。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-116">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="dcfbe-117">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-117">**Browse**</span></span>  
 <span data-ttu-id="dcfbe-118">通过定位文件来指定要在“多平面文件连接”中使用的文件名。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-118">Browse the file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="dcfbe-119">您可以选择多个文件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-119">You can select multiple files.</span></span> <span data-ttu-id="dcfbe-120">所有文件的数据格式必须相同。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-120">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="dcfbe-121">**区域设置**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-121">**Locale**</span></span>  
 <span data-ttu-id="dcfbe-122">指定与排序以及日期和时间转换设置相关的区域设置。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-122">Specify the location to provide information for ordering and for date and time conversion.</span></span>  
  
 <span data-ttu-id="dcfbe-123">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-123">**Unicode**</span></span>  
 <span data-ttu-id="dcfbe-124">指示是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-124">Indicate whether to use Unicode.</span></span> <span data-ttu-id="dcfbe-125">如果使用 Unicode，将不能指定代码页。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-125">Using Unicode precludes specifying a code page.</span></span>  
  
 <span data-ttu-id="dcfbe-126">**代码页**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-126">**Code page**</span></span>  
 <span data-ttu-id="dcfbe-127">指定非 Unicode 文本的代码页。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-127">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="dcfbe-128">**格式**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-128">**Format**</span></span>  
 <span data-ttu-id="dcfbe-129">指示是否使用带分隔符、固定宽度或右边未对齐的格式。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-129">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span> <span data-ttu-id="dcfbe-130">所有文件的数据格式必须相同。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-130">All files must have the same data format.</span></span>  
  
|<span data-ttu-id="dcfbe-131">值</span><span class="sxs-lookup"><span data-stu-id="dcfbe-131">Value</span></span>|<span data-ttu-id="dcfbe-132">说明</span><span class="sxs-lookup"><span data-stu-id="dcfbe-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dcfbe-133">带分隔符</span><span class="sxs-lookup"><span data-stu-id="dcfbe-133">Delimited</span></span>|<span data-ttu-id="dcfbe-134">各列之间由在 **“列”** 页上指定的分隔符隔开。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-134">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="dcfbe-135">固定宽度</span><span class="sxs-lookup"><span data-stu-id="dcfbe-135">Fixed width</span></span>|<span data-ttu-id="dcfbe-136">列的宽度固定，通过在 **“列”** 页上拖动标记线即可指定列的宽度。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-136">Columns have a fixed width, specified by dragging marker lines on the **Columns** page.</span></span>|  
|<span data-ttu-id="dcfbe-137">右边未对齐</span><span class="sxs-lookup"><span data-stu-id="dcfbe-137">Ragged right</span></span>|<span data-ttu-id="dcfbe-138">在右边未对齐的文件中，除最后一列之外的每一列的宽度都固定，而最后一列由 **“列”** 页上指定的行分隔符进行分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-138">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter, specified on the **Columns** page.</span></span>|  
  
 <span data-ttu-id="dcfbe-139">**文本限定符**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-139">**Text qualifier**</span></span>  
 <span data-ttu-id="dcfbe-140">指定要使用的文本限定符。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-140">Specify the text qualifier to use.</span></span> <span data-ttu-id="dcfbe-141">例如，您可以指定将文本包含在引号中。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-141">For example, you can specify to enclose text with quotation marks.</span></span>  
  
 <span data-ttu-id="dcfbe-142">**标题行分隔符**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-142">**Header row delimiter**</span></span>  
 <span data-ttu-id="dcfbe-143">从标题行的分隔符列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-143">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="dcfbe-144">值</span><span class="sxs-lookup"><span data-stu-id="dcfbe-144">Value</span></span>|<span data-ttu-id="dcfbe-145">说明</span><span class="sxs-lookup"><span data-stu-id="dcfbe-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dcfbe-146">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-146">**{CR}{LF}**</span></span>|<span data-ttu-id="dcfbe-147">标题行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-147">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="dcfbe-148">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-148">**{CR}**</span></span>|<span data-ttu-id="dcfbe-149">标题行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-149">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="dcfbe-150">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-150">**{LF}**</span></span>|<span data-ttu-id="dcfbe-151">标题行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-151">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="dcfbe-152">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-152">**Semicolon {;}**</span></span>|<span data-ttu-id="dcfbe-153">标题行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-153">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="dcfbe-154">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-154">**Colon {:}**</span></span>|<span data-ttu-id="dcfbe-155">标题行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-155">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="dcfbe-156">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-156">**Comma {,}**</span></span>|<span data-ttu-id="dcfbe-157">标题行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-157">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="dcfbe-158">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-158">**Tab {t}**</span></span>|<span data-ttu-id="dcfbe-159">标题行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-159">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="dcfbe-160">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-160">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="dcfbe-161">标题行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-161">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="dcfbe-162">**要跳过的标题行数**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-162">**Header rows to skip**</span></span>  
 <span data-ttu-id="dcfbe-163">指定要跳过的标题行数（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-163">Specify the number of header rows to skip, if any.</span></span>  
  
 <span data-ttu-id="dcfbe-164">**第一个数据行中的列名称**</span><span class="sxs-lookup"><span data-stu-id="dcfbe-164">**Column names in the first data row**</span></span>  
 <span data-ttu-id="dcfbe-165">指示在第一个数据行中是否要求列名或提供列名。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-165">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfbe-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcfbe-166">See Also</span></span>  
 <span data-ttu-id="dcfbe-167">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbe-167">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dcfbe-168">[多平面文件连接管理器编辑器 &#40;列 "页&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbe-168">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="dcfbe-169">[多平面文件连接管理器编辑器 &#40;高级页面&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbe-169">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="dcfbe-170">多平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="dcfbe-170">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
