---
title: 多平面文件连接管理器编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a7f4936f0722754b414076820eda7dcf2dc8dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578289"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a><span data-ttu-id="39c95-102">多平面文件连接管理器编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="39c95-102">Multiple Flat Files Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="39c95-103">可以使用 **“多平面文件连接管理器编辑器”** 对话框的 **“列”** 节点指定行和列的信息，以及预览选定的第一个文件。</span><span class="sxs-lookup"><span data-stu-id="39c95-103">Use the **Columns** node of the **Multiple Flat Files Connection Manager Editor** dialog box to specify the row and column information, and to preview the first selected file.</span></span>  
  
 <span data-ttu-id="39c95-104">若要了解有关多平面文件连接管理器的详细信息，请参阅 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="39c95-104">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="39c95-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="39c95-105">Static Options</span></span>  
 <span data-ttu-id="39c95-106">**连接管理器名称**</span><span class="sxs-lookup"><span data-stu-id="39c95-106">**Connection manager name**</span></span>  
 <span data-ttu-id="39c95-107">为工作流中的“多平面文件连接”提供一个唯一名称。</span><span class="sxs-lookup"><span data-stu-id="39c95-107">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="39c95-108">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="39c95-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="39c95-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="39c95-109">**Description**</span></span>  
 <span data-ttu-id="39c95-110">描述此连接。</span><span class="sxs-lookup"><span data-stu-id="39c95-110">Describe the connection.</span></span> <span data-ttu-id="39c95-111">最好按照连接的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="39c95-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="39c95-112">平面文件格式动态选项</span><span class="sxs-lookup"><span data-stu-id="39c95-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="39c95-113">格式 = 带分隔符</span><span class="sxs-lookup"><span data-stu-id="39c95-113">Format = Delimited</span></span>  
 <span data-ttu-id="39c95-114">**行分隔符**</span><span class="sxs-lookup"><span data-stu-id="39c95-114">**Row delimiter**</span></span>  
 <span data-ttu-id="39c95-115">从可用行分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="39c95-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="39c95-116">值</span><span class="sxs-lookup"><span data-stu-id="39c95-116">Value</span></span>|<span data-ttu-id="39c95-117">说明</span><span class="sxs-lookup"><span data-stu-id="39c95-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39c95-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-118">**{CR}{LF}**</span></span>|<span data-ttu-id="39c95-119">行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="39c95-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="39c95-120">**{CR}**</span></span>|<span data-ttu-id="39c95-121">行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="39c95-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-122">**{LF}**</span></span>|<span data-ttu-id="39c95-123">行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="39c95-124">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="39c95-124">**Semicolon {;}**</span></span>|<span data-ttu-id="39c95-125">行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="39c95-126">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="39c95-126">**Colon {:}**</span></span>|<span data-ttu-id="39c95-127">行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="39c95-128">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="39c95-128">**Comma {,}**</span></span>|<span data-ttu-id="39c95-129">行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="39c95-130">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="39c95-130">**Tab {t}**</span></span>|<span data-ttu-id="39c95-131">行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="39c95-132">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="39c95-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="39c95-133">行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="39c95-134">**列分隔符**</span><span class="sxs-lookup"><span data-stu-id="39c95-134">**Column delimiter**</span></span>  
 <span data-ttu-id="39c95-135">从可用列分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="39c95-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="39c95-136">值</span><span class="sxs-lookup"><span data-stu-id="39c95-136">Value</span></span>|<span data-ttu-id="39c95-137">说明</span><span class="sxs-lookup"><span data-stu-id="39c95-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39c95-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-138">**{CR}{LF}**</span></span>|<span data-ttu-id="39c95-139">列由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="39c95-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="39c95-140">**{CR}**</span></span>|<span data-ttu-id="39c95-141">列由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="39c95-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-142">**{LF}**</span></span>|<span data-ttu-id="39c95-143">列由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="39c95-144">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="39c95-144">**Semicolon {;}**</span></span>|<span data-ttu-id="39c95-145">列由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="39c95-146">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="39c95-146">**Colon {:}**</span></span>|<span data-ttu-id="39c95-147">列由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="39c95-148">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="39c95-148">**Comma {,}**</span></span>|<span data-ttu-id="39c95-149">列由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="39c95-150">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="39c95-150">**Tab {t}**</span></span>|<span data-ttu-id="39c95-151">列由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="39c95-152">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="39c95-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="39c95-153">列由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="39c95-154">**重置列**</span><span class="sxs-lookup"><span data-stu-id="39c95-154">**Reset Columns**</span></span>  
 <span data-ttu-id="39c95-155">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="39c95-155">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="39c95-156">格式 = 固定宽度</span><span class="sxs-lookup"><span data-stu-id="39c95-156">Format = Fixed Width</span></span>  
 <span data-ttu-id="39c95-157">**字体**</span><span class="sxs-lookup"><span data-stu-id="39c95-157">**Font**</span></span>  
 <span data-ttu-id="39c95-158">选择用于显示预览数据的字体。</span><span class="sxs-lookup"><span data-stu-id="39c95-158">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="39c95-159">**源数据列**</span><span class="sxs-lookup"><span data-stu-id="39c95-159">**Source data columns**</span></span>  
 <span data-ttu-id="39c95-160">通过滑动垂直的行标记可以调整行宽，通过单击预览窗口顶部的标尺可以调整列宽</span><span class="sxs-lookup"><span data-stu-id="39c95-160">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="39c95-161">**行宽**</span><span class="sxs-lookup"><span data-stu-id="39c95-161">**Row width**</span></span>  
 <span data-ttu-id="39c95-162">为各列添加分隔符之前，先指定行的长度。</span><span class="sxs-lookup"><span data-stu-id="39c95-162">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="39c95-163">或者，拖动预览窗口中的垂直线，以标记行尾。</span><span class="sxs-lookup"><span data-stu-id="39c95-163">Or, drag the vertical line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="39c95-164">行宽值将自动更新。</span><span class="sxs-lookup"><span data-stu-id="39c95-164">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="39c95-165">**重置列**</span><span class="sxs-lookup"><span data-stu-id="39c95-165">**Reset Columns**</span></span>  
 <span data-ttu-id="39c95-166">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="39c95-166">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="39c95-167">格式 = 右边未对齐</span><span class="sxs-lookup"><span data-stu-id="39c95-167">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39c95-168">右边未对齐是指文件中除最后一列之外每一列的宽度都固定。</span><span class="sxs-lookup"><span data-stu-id="39c95-168">Ragged right files are those in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="39c95-169">它由行分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-169">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="39c95-170">**字体**</span><span class="sxs-lookup"><span data-stu-id="39c95-170">**Font**</span></span>  
 <span data-ttu-id="39c95-171">选择用于显示预览数据的字体。</span><span class="sxs-lookup"><span data-stu-id="39c95-171">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="39c95-172">**源数据列**</span><span class="sxs-lookup"><span data-stu-id="39c95-172">**Source data columns**</span></span>  
 <span data-ttu-id="39c95-173">通过滑动垂直的行标记可以调整行宽，通过单击预览窗口顶部的标尺可以调整列宽</span><span class="sxs-lookup"><span data-stu-id="39c95-173">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="39c95-174">**行分隔符**</span><span class="sxs-lookup"><span data-stu-id="39c95-174">**Row delimiter**</span></span>  
 <span data-ttu-id="39c95-175">从可用行分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="39c95-175">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="39c95-176">值</span><span class="sxs-lookup"><span data-stu-id="39c95-176">Value</span></span>|<span data-ttu-id="39c95-177">说明</span><span class="sxs-lookup"><span data-stu-id="39c95-177">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39c95-178">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-178">**{CR}{LF}**</span></span>|<span data-ttu-id="39c95-179">行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-179">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="39c95-180">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="39c95-180">**{CR}**</span></span>|<span data-ttu-id="39c95-181">行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-181">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="39c95-182">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="39c95-182">**{LF}**</span></span>|<span data-ttu-id="39c95-183">行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-183">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="39c95-184">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="39c95-184">**Semicolon {;}**</span></span>|<span data-ttu-id="39c95-185">行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-185">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="39c95-186">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="39c95-186">**Colon {:}**</span></span>|<span data-ttu-id="39c95-187">行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-187">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="39c95-188">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="39c95-188">**Comma {,}**</span></span>|<span data-ttu-id="39c95-189">行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-189">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="39c95-190">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="39c95-190">**Tab {t}**</span></span>|<span data-ttu-id="39c95-191">行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-191">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="39c95-192">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="39c95-192">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="39c95-193">行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="39c95-193">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="39c95-194">**重置列**</span><span class="sxs-lookup"><span data-stu-id="39c95-194">**Reset Columns**</span></span>  
 <span data-ttu-id="39c95-195">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="39c95-195">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c95-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39c95-196">See Also</span></span>  
 <span data-ttu-id="39c95-197">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="39c95-197">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="39c95-198">[多平面文件连接管理器编辑器 &#40;常规页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="39c95-198">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="39c95-199">[多平面文件连接管理器编辑器 &#40;高级页面&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="39c95-199">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="39c95-200">多平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="39c95-200">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
