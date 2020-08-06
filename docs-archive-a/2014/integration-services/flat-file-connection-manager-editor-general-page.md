---
title: 平面文件连接管理器编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 478c7bcf56e300b47af93862bf66409a3c94b5f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578349"
---
# <a name="flat-file-connection-manager-editor-general-page"></a><span data-ttu-id="ee450-102">平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="ee450-102">Flat File Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="ee450-103">可以使用 **“平面文件连接管理器编辑器”** 对话框的 **“常规”** 页选择文件和数据格式。</span><span class="sxs-lookup"><span data-stu-id="ee450-103">Use the **General** page of the **Flat File Connection Manager Editor** dialog box to select a file and data format.</span></span> <span data-ttu-id="ee450-104">使用平面文件连接可以将包连接到文本文件。</span><span class="sxs-lookup"><span data-stu-id="ee450-104">A flat file connection enables a package to connect to a text file.</span></span>  
  
 <span data-ttu-id="ee450-105">若要了解有关平面文件连接管理器的详细信息，请参阅 [Flat File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ee450-105">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee450-106">选项</span><span class="sxs-lookup"><span data-stu-id="ee450-106">Options</span></span>  
 <span data-ttu-id="ee450-107">**连接管理器名称**</span><span class="sxs-lookup"><span data-stu-id="ee450-107">**Connection manager name**</span></span>  
 <span data-ttu-id="ee450-108">为工作流中的平面文件连接提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="ee450-108">Provide a unique name for the flat file connection in the workflow.</span></span> <span data-ttu-id="ee450-109">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="ee450-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="ee450-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="ee450-110">**Description**</span></span>  
 <span data-ttu-id="ee450-111">描述此连接。</span><span class="sxs-lookup"><span data-stu-id="ee450-111">Describe the connection.</span></span> <span data-ttu-id="ee450-112">最好按照连接的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="ee450-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="ee450-113">**文件名**</span><span class="sxs-lookup"><span data-stu-id="ee450-113">**File name**</span></span>  
 <span data-ttu-id="ee450-114">键入要在平面文件连接中使用的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="ee450-114">Type the path and file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="ee450-115">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="ee450-115">**Browse**</span></span>  
 <span data-ttu-id="ee450-116">定位要在平面文件连接中使用的文件名。</span><span class="sxs-lookup"><span data-stu-id="ee450-116">Locate the file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="ee450-117">**区域设置**</span><span class="sxs-lookup"><span data-stu-id="ee450-117">**Locale**</span></span>  
 <span data-ttu-id="ee450-118">指定区域设置，以便为排序以及日期和时间格式提供语言特定的信息。</span><span class="sxs-lookup"><span data-stu-id="ee450-118">Specify the locale to provide language-specific information for ordering and for date and time formats.</span></span>  
  
 <span data-ttu-id="ee450-119">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="ee450-119">**Unicode**</span></span>  
 <span data-ttu-id="ee450-120">指示是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="ee450-120">Indicate whether to use Unicode.</span></span> <span data-ttu-id="ee450-121">如果使用 Unicode，则不能指定代码页。</span><span class="sxs-lookup"><span data-stu-id="ee450-121">If you use Unicode, you cannot specify a code page.</span></span>  
  
 <span data-ttu-id="ee450-122">**代码页**</span><span class="sxs-lookup"><span data-stu-id="ee450-122">**Code page**</span></span>  
 <span data-ttu-id="ee450-123">指定非 Unicode 文本的代码页。</span><span class="sxs-lookup"><span data-stu-id="ee450-123">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="ee450-124">**格式**</span><span class="sxs-lookup"><span data-stu-id="ee450-124">**Format**</span></span>  
 <span data-ttu-id="ee450-125">指示文件是否使用带分隔符、固定宽度或右边未对齐的格式。</span><span class="sxs-lookup"><span data-stu-id="ee450-125">Indicate whether the file uses delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="ee450-126">值</span><span class="sxs-lookup"><span data-stu-id="ee450-126">Value</span></span>|<span data-ttu-id="ee450-127">说明</span><span class="sxs-lookup"><span data-stu-id="ee450-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee450-128">带分隔符</span><span class="sxs-lookup"><span data-stu-id="ee450-128">Delimited</span></span>|<span data-ttu-id="ee450-129">各列之间由在 **“列”** 页上指定的分隔符隔开。</span><span class="sxs-lookup"><span data-stu-id="ee450-129">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="ee450-130">固定宽度</span><span class="sxs-lookup"><span data-stu-id="ee450-130">Fixed width</span></span>|<span data-ttu-id="ee450-131">列的宽度固定。</span><span class="sxs-lookup"><span data-stu-id="ee450-131">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="ee450-132">右边未对齐</span><span class="sxs-lookup"><span data-stu-id="ee450-132">Ragged right</span></span>|<span data-ttu-id="ee450-133">在右边未对齐的文件中，除最后一列之外的每一列的宽度都固定。</span><span class="sxs-lookup"><span data-stu-id="ee450-133">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="ee450-134">它由行分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-134">It is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="ee450-135">**文本限定符**</span><span class="sxs-lookup"><span data-stu-id="ee450-135">**Text qualifier**</span></span>  
 <span data-ttu-id="ee450-136">指定要使用的文本限定符。</span><span class="sxs-lookup"><span data-stu-id="ee450-136">Specify the text qualifier to use.</span></span> <span data-ttu-id="ee450-137">例如，可以指定文本字段必须用引号括起来。</span><span class="sxs-lookup"><span data-stu-id="ee450-137">For example, you can specify that text fields are enclosed in quotation marks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee450-138">选择文本限定符之后，不能重新选择“无”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="ee450-138">After you select a text qualifier, you cannot re-select the **None** option.</span></span> <span data-ttu-id="ee450-139">键入 **None** 以取消选择文本限定符。</span><span class="sxs-lookup"><span data-stu-id="ee450-139">Type **None** to de-select the text qualifier.</span></span>  
  
 <span data-ttu-id="ee450-140">**标题行分隔符**</span><span class="sxs-lookup"><span data-stu-id="ee450-140">**Header row delimiter**</span></span>  
 <span data-ttu-id="ee450-141">从标题行的分隔符列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="ee450-141">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="ee450-142">值</span><span class="sxs-lookup"><span data-stu-id="ee450-142">Value</span></span>|<span data-ttu-id="ee450-143">说明</span><span class="sxs-lookup"><span data-stu-id="ee450-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee450-144">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="ee450-144">**{CR}{LF}**</span></span>|<span data-ttu-id="ee450-145">标题行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-145">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="ee450-146">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="ee450-146">**{CR}**</span></span>|<span data-ttu-id="ee450-147">标题行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-147">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="ee450-148">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="ee450-148">**{LF}**</span></span>|<span data-ttu-id="ee450-149">标题行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-149">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="ee450-150">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="ee450-150">**Semicolon {;}**</span></span>|<span data-ttu-id="ee450-151">标题行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-151">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="ee450-152">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="ee450-152">**Colon {:}**</span></span>|<span data-ttu-id="ee450-153">标题行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-153">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="ee450-154">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="ee450-154">**Comma {,}**</span></span>|<span data-ttu-id="ee450-155">标题行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-155">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="ee450-156">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="ee450-156">**Tab {t}**</span></span>|<span data-ttu-id="ee450-157">标题行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-157">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="ee450-158">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="ee450-158">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="ee450-159">标题行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="ee450-159">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="ee450-160">**要跳过的标题行数**</span><span class="sxs-lookup"><span data-stu-id="ee450-160">**Header rows to skip**</span></span>  
 <span data-ttu-id="ee450-161">指定要跳过的标题行数或初始数据行数（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="ee450-161">Specify the number of header rows or initial data rows to skip, if any.</span></span>  
  
 <span data-ttu-id="ee450-162">**第一个数据行中的列名称**</span><span class="sxs-lookup"><span data-stu-id="ee450-162">**Column names in the first data row**</span></span>  
 <span data-ttu-id="ee450-163">指示在第一个数据行中是否要求列名或提供列名。</span><span class="sxs-lookup"><span data-stu-id="ee450-163">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee450-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee450-164">See Also</span></span>  
 <span data-ttu-id="ee450-165">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ee450-165">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ee450-166">[平面文件连接管理器编辑器 &#40;列 "页&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="ee450-166">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="ee450-167">["平面文件连接管理器编辑器" &#40;"高级" 页&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="ee450-167">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="ee450-168">平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="ee450-168">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
