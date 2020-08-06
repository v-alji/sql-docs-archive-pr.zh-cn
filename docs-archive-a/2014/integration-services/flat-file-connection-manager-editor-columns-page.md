---
title: 平面文件连接管理器编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ce579f73922d2eaa2c48e98a98f52cd5836f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578347"
---
# <a name="flat-file-connection-manager-editor-columns-page"></a><span data-ttu-id="cd19d-102">平面文件连接管理器编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="cd19d-102">Flat File Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="cd19d-103">可以使用 **“平面文件连接管理器编辑器”** 对话框的 **“列”** 页，指定行和列的信息以及预览相应的文件。</span><span class="sxs-lookup"><span data-stu-id="cd19d-103">Use the **Columns** page of the **Flat File Connection Manager Editor** dialog box to specify the row and column information, and to preview the file.</span></span>  
  
 <span data-ttu-id="cd19d-104">若要了解有关平面文件连接管理器的详细信息，请参阅 [Flat File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cd19d-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="cd19d-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="cd19d-105">Static Options</span></span>  
 <span data-ttu-id="cd19d-106">**连接管理器名称**</span><span class="sxs-lookup"><span data-stu-id="cd19d-106">**Connection manager name**</span></span>  
 <span data-ttu-id="cd19d-107">为工作流中的平面文件连接提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="cd19d-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="cd19d-108">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="cd19d-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="cd19d-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="cd19d-109">**Description**</span></span>  
 <span data-ttu-id="cd19d-110">描述此连接。</span><span class="sxs-lookup"><span data-stu-id="cd19d-110">Describe the connection.</span></span> <span data-ttu-id="cd19d-111">最好按照连接的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="cd19d-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="cd19d-112">平面文件格式动态选项</span><span class="sxs-lookup"><span data-stu-id="cd19d-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="cd19d-113">格式 = 带分隔符</span><span class="sxs-lookup"><span data-stu-id="cd19d-113">Format = Delimited</span></span>  
 <span data-ttu-id="cd19d-114">**行分隔符**</span><span class="sxs-lookup"><span data-stu-id="cd19d-114">**Row delimiter**</span></span>  
 <span data-ttu-id="cd19d-115">从可用行分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="cd19d-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="cd19d-116">值</span><span class="sxs-lookup"><span data-stu-id="cd19d-116">Value</span></span>|<span data-ttu-id="cd19d-117">说明</span><span class="sxs-lookup"><span data-stu-id="cd19d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd19d-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-118">**{CR}{LF}**</span></span>|<span data-ttu-id="cd19d-119">行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="cd19d-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-120">**{CR}**</span></span>|<span data-ttu-id="cd19d-121">行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="cd19d-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-122">**{LF}**</span></span>|<span data-ttu-id="cd19d-123">行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="cd19d-124">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-124">**Semicolon {;}**</span></span>|<span data-ttu-id="cd19d-125">行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="cd19d-126">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-126">**Colon {:}**</span></span>|<span data-ttu-id="cd19d-127">行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="cd19d-128">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-128">**Comma {,}**</span></span>|<span data-ttu-id="cd19d-129">行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="cd19d-130">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-130">**Tab {t}**</span></span>|<span data-ttu-id="cd19d-131">行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="cd19d-132">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="cd19d-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="cd19d-133">行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="cd19d-134">**列分隔符**</span><span class="sxs-lookup"><span data-stu-id="cd19d-134">**Column delimiter**</span></span>  
 <span data-ttu-id="cd19d-135">从可用列分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="cd19d-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="cd19d-136">值</span><span class="sxs-lookup"><span data-stu-id="cd19d-136">Value</span></span>|<span data-ttu-id="cd19d-137">说明</span><span class="sxs-lookup"><span data-stu-id="cd19d-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd19d-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-138">**{CR}{LF}**</span></span>|<span data-ttu-id="cd19d-139">列由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="cd19d-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-140">**{CR}**</span></span>|<span data-ttu-id="cd19d-141">列由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="cd19d-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-142">**{LF}**</span></span>|<span data-ttu-id="cd19d-143">列由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="cd19d-144">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-144">**Semicolon {;}**</span></span>|<span data-ttu-id="cd19d-145">列由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="cd19d-146">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-146">**Colon {:}**</span></span>|<span data-ttu-id="cd19d-147">列由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="cd19d-148">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-148">**Comma {,}**</span></span>|<span data-ttu-id="cd19d-149">列由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="cd19d-150">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-150">**Tab {t}**</span></span>|<span data-ttu-id="cd19d-151">列由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="cd19d-152">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="cd19d-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="cd19d-153">列由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="cd19d-154">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="cd19d-154">**Refresh**</span></span>  
 <span data-ttu-id="cd19d-155">通过单击“刷新”\*\*\*\* 查看更改要跳过的分隔符后的效果。</span><span class="sxs-lookup"><span data-stu-id="cd19d-155">View the effect of changing the delimiters to skip by clicking **Refresh**.</span></span> <span data-ttu-id="cd19d-156">只有在更改其他连接选项之后，此按钮才可见。</span><span class="sxs-lookup"><span data-stu-id="cd19d-156">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="cd19d-157">**预览行**</span><span class="sxs-lookup"><span data-stu-id="cd19d-157">**Preview rows**</span></span>  
 <span data-ttu-id="cd19d-158">查看平面文件中的示例数据，这些数据已按所选的选项划分为列和行。</span><span class="sxs-lookup"><span data-stu-id="cd19d-158">View sample data in the flat file, divided into columns and rows by using the options selected.</span></span>  
  
 <span data-ttu-id="cd19d-159">**重置列**</span><span class="sxs-lookup"><span data-stu-id="cd19d-159">**Reset Columns**</span></span>  
 <span data-ttu-id="cd19d-160">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="cd19d-160">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="cd19d-161">格式 = 固定宽度</span><span class="sxs-lookup"><span data-stu-id="cd19d-161">Format = Fixed Width</span></span>  
 <span data-ttu-id="cd19d-162">**字体**</span><span class="sxs-lookup"><span data-stu-id="cd19d-162">**Font**</span></span>  
 <span data-ttu-id="cd19d-163">选择用于显示预览数据的字体。</span><span class="sxs-lookup"><span data-stu-id="cd19d-163">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="cd19d-164">**源数据列**</span><span class="sxs-lookup"><span data-stu-id="cd19d-164">**Source data columns**</span></span>  
 <span data-ttu-id="cd19d-165">通过滑动垂直的红色行标记可以调整行宽，通过单击预览窗口顶部的标尺可以调整列宽。</span><span class="sxs-lookup"><span data-stu-id="cd19d-165">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="cd19d-166">**行宽**</span><span class="sxs-lookup"><span data-stu-id="cd19d-166">**Row width**</span></span>  
 <span data-ttu-id="cd19d-167">为各列添加分隔符之前，先指定行的长度。</span><span class="sxs-lookup"><span data-stu-id="cd19d-167">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="cd19d-168">或者，拖动预览窗口中的垂直红线，以标记行尾。</span><span class="sxs-lookup"><span data-stu-id="cd19d-168">Or, drag the vertical red line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="cd19d-169">行宽值将自动更新。</span><span class="sxs-lookup"><span data-stu-id="cd19d-169">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="cd19d-170">**重置列**</span><span class="sxs-lookup"><span data-stu-id="cd19d-170">**Reset Columns**</span></span>  
 <span data-ttu-id="cd19d-171">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="cd19d-171">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="cd19d-172">格式 = 右边未对齐</span><span class="sxs-lookup"><span data-stu-id="cd19d-172">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd19d-173">在右边未对齐的文件中，除最后一列之外的每一列的宽度都固定。</span><span class="sxs-lookup"><span data-stu-id="cd19d-173">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="cd19d-174">它由行分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-174">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="cd19d-175">**字体**</span><span class="sxs-lookup"><span data-stu-id="cd19d-175">**Font**</span></span>  
 <span data-ttu-id="cd19d-176">选择用于显示预览数据的字体。</span><span class="sxs-lookup"><span data-stu-id="cd19d-176">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="cd19d-177">**源数据列**</span><span class="sxs-lookup"><span data-stu-id="cd19d-177">**Source data columns**</span></span>  
 <span data-ttu-id="cd19d-178">通过滑动垂直的红色行标记可以调整行宽，通过单击预览窗口顶部的标尺可以调整列宽。</span><span class="sxs-lookup"><span data-stu-id="cd19d-178">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="cd19d-179">**行分隔符**</span><span class="sxs-lookup"><span data-stu-id="cd19d-179">**Row delimiter**</span></span>  
 <span data-ttu-id="cd19d-180">从可用行分隔符的列表中选择，或输入分隔符文本。</span><span class="sxs-lookup"><span data-stu-id="cd19d-180">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="cd19d-181">值</span><span class="sxs-lookup"><span data-stu-id="cd19d-181">Value</span></span>|<span data-ttu-id="cd19d-182">说明</span><span class="sxs-lookup"><span data-stu-id="cd19d-182">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd19d-183">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-183">**{CR}{LF}**</span></span>|<span data-ttu-id="cd19d-184">行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-184">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="cd19d-185">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-185">**{CR}**</span></span>|<span data-ttu-id="cd19d-186">行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-186">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="cd19d-187">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-187">**{LF}**</span></span>|<span data-ttu-id="cd19d-188">行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-188">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="cd19d-189">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-189">**Semicolon {;}**</span></span>|<span data-ttu-id="cd19d-190">行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-190">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="cd19d-191">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-191">**Colon {:}**</span></span>|<span data-ttu-id="cd19d-192">行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-192">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="cd19d-193">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-193">**Comma {,}**</span></span>|<span data-ttu-id="cd19d-194">行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-194">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="cd19d-195">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="cd19d-195">**Tab {t}**</span></span>|<span data-ttu-id="cd19d-196">行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-196">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="cd19d-197">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="cd19d-197">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="cd19d-198">行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="cd19d-198">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="cd19d-199">**重置列**</span><span class="sxs-lookup"><span data-stu-id="cd19d-199">**Reset Columns**</span></span>  
 <span data-ttu-id="cd19d-200">通过单击“重置列”可以删除除原始列之外的所有列。</span><span class="sxs-lookup"><span data-stu-id="cd19d-200">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd19d-201">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd19d-201">See Also</span></span>  
 <span data-ttu-id="cd19d-202">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cd19d-202">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cd19d-203">[平面文件连接管理器编辑器 &#40;"常规" 页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cd19d-203">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="cd19d-204">["平面文件连接管理器编辑器" &#40;"高级" 页&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd19d-204">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="cd19d-205">平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="cd19d-205">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
