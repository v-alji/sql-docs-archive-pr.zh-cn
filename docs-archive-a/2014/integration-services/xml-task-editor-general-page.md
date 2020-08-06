---
title: XML 任务编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f73681a818d80c4e8b2755086e653e5c7e682f01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691777"
---
# <a name="xml-task-editor-general-page"></a><span data-ttu-id="d7eca-102">XML 任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="d7eca-102">XML Task Editor (General Page)</span></span>
  <span data-ttu-id="d7eca-103">可以使用 **“XML 任务编辑器”** 对话框的 **“常规节点”** ，指定操作类型以及配置操作。</span><span class="sxs-lookup"><span data-stu-id="d7eca-103">Use the **General Node** of the **XML Task Editor** dialog box to specify the operation type and configure the operation.</span></span>  
  
 <span data-ttu-id="d7eca-104">若要了解此任务，请参阅 [XML Task](control-flow/xml-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-104">To learn about this task, see [XML Task](control-flow/xml-task.md).</span></span> <span data-ttu-id="d7eca-105">有关使用 XML 文档和数据的信息，请参阅 MSDN Library 中的“[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)”。</span><span class="sxs-lookup"><span data-stu-id="d7eca-105">For information about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="d7eca-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="d7eca-106">Static Options</span></span>  
 <span data-ttu-id="d7eca-107">**OperationType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-107">**OperationType**</span></span>  
 <span data-ttu-id="d7eca-108">从列表中选择操作类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-108">Select the operation type from the list.</span></span> <span data-ttu-id="d7eca-109">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-109">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-110">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-110">Value</span></span>|<span data-ttu-id="d7eca-111">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-112">**验证**</span><span class="sxs-lookup"><span data-stu-id="d7eca-112">**Validate**</span></span>|<span data-ttu-id="d7eca-113">根据文档类型定义 (DTD) 或 XML 架构定义 (XSD) 架构验证 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-113">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="d7eca-114">选择此选项将在 **Validate**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-114">Selecting this option displays the dynamic options in section, **Validate**.</span></span>|  
|<span data-ttu-id="d7eca-115">**XSLT**</span><span class="sxs-lookup"><span data-stu-id="d7eca-115">**XSLT**</span></span>|<span data-ttu-id="d7eca-116">对 XML 文档执行 XSL 转换。</span><span class="sxs-lookup"><span data-stu-id="d7eca-116">Performs XSL transformations on XML documents.</span></span> <span data-ttu-id="d7eca-117">选择此选项将在 **XSLT**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-117">Selecting this option displays the dynamic options in section, **XSLT**.</span></span>|  
|<span data-ttu-id="d7eca-118">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="d7eca-118">**XPATH**</span></span>|<span data-ttu-id="d7eca-119">执行 XPath 查询和计算。</span><span class="sxs-lookup"><span data-stu-id="d7eca-119">Performs XPath queries and evaluations.</span></span> <span data-ttu-id="d7eca-120">选择此选项将在 **XPATH**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-120">Selecting this option displays the dynamic options in section, **XPATH**.</span></span>|  
|<span data-ttu-id="d7eca-121">**合并**</span><span class="sxs-lookup"><span data-stu-id="d7eca-121">**Merge**</span></span>|<span data-ttu-id="d7eca-122">合并两个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-122">Merges two XML documents.</span></span> <span data-ttu-id="d7eca-123">选择此选项将在 **Merge**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-123">Selecting this option displays the dynamic options in section, **Merge**.</span></span>|  
|<span data-ttu-id="d7eca-124">**差异**</span><span class="sxs-lookup"><span data-stu-id="d7eca-124">**Diff**</span></span>|<span data-ttu-id="d7eca-125">比较两个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-125">Compares two XML documents.</span></span> <span data-ttu-id="d7eca-126">选择此选项将在 **Diff**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-126">Selecting this option displays the dynamic options in section, **Diff**.</span></span>|  
|<span data-ttu-id="d7eca-127">**Patch**</span><span class="sxs-lookup"><span data-stu-id="d7eca-127">**Patch**</span></span>|<span data-ttu-id="d7eca-128">应用 Diff 运算的输出以创建新文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-128">Applies the output from the Diff operation to create a new document.</span></span> <span data-ttu-id="d7eca-129">选择此选项将在 **Patch**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-129">Selecting this option displays the dynamic options in section, **Patch**.</span></span>|  
  
 <span data-ttu-id="d7eca-130">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-130">**SourceType**</span></span>  
 <span data-ttu-id="d7eca-131">选择 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-131">Select the source type of the XML document.</span></span> <span data-ttu-id="d7eca-132">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-133">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-133">Value</span></span>|<span data-ttu-id="d7eca-134">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-135">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-135">**Direct input**</span></span>|<span data-ttu-id="d7eca-136">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-136">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-137">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-137">**File connection**</span></span>|<span data-ttu-id="d7eca-138">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-138">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-139">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-139">**Variable**</span></span>|<span data-ttu-id="d7eca-140">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-140">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-141">**数据源**</span><span class="sxs-lookup"><span data-stu-id="d7eca-141">**Source**</span></span>  
 <span data-ttu-id="d7eca-142">如果将“源”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“文档源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-142">If **Source** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-143">如果将“源”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**>，创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-143">If **Source** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-144">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-145">如果将“源”设置为“变量”，请选择现有变量，或单击 \<New variable...> 以创建新的变量  。</span><span class="sxs-lookup"><span data-stu-id="d7eca-145">If **Source** is set to **Variable**, select an existing variable, or click **\<New variable...>** to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-146">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-146">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
## <a name="operationtype-dynamic-options"></a><span data-ttu-id="d7eca-147">OperationType 动态选项</span><span class="sxs-lookup"><span data-stu-id="d7eca-147">OperationType Dynamic Options</span></span>  
  
### <a name="operationtype--validate"></a><span data-ttu-id="d7eca-148">OperationType = Validate</span><span class="sxs-lookup"><span data-stu-id="d7eca-148">OperationType = Validate</span></span>  
 <span data-ttu-id="d7eca-149">指定验证操作的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-149">Specify options for the Validate operation.</span></span>  
  
 <span data-ttu-id="d7eca-150">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-150">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-151">指定 XML 任务是否保存验证操作的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-151">Specify whether the XML task saves the output of the Validate operation.</span></span>  
  
 <span data-ttu-id="d7eca-152">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-152">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-153">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-153">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-154">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-154">**Destination**</span></span>  
 <span data-ttu-id="d7eca-155">选择现有文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d7eca-155">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-156">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-156">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-157">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-157">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-158">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-158">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-159">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-159">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-160">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-160">Value</span></span>|<span data-ttu-id="d7eca-161">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-161">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-162">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-162">**File connection**</span></span>|<span data-ttu-id="d7eca-163">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-163">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-164">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-164">**Variable**</span></span>|<span data-ttu-id="d7eca-165">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-165">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-166">**ValidationType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-166">**ValidationType**</span></span>  
 <span data-ttu-id="d7eca-167">选择验证类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-167">Select the validation type.</span></span> <span data-ttu-id="d7eca-168">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-168">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-169">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-169">Value</span></span>|<span data-ttu-id="d7eca-170">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-171">**DTD**</span><span class="sxs-lookup"><span data-stu-id="d7eca-171">**DTD**</span></span>|<span data-ttu-id="d7eca-172">使用文档类型定义 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-172">Use a Document Type Definition (DTD).</span></span>|  
|<span data-ttu-id="d7eca-173">**XSD**</span><span class="sxs-lookup"><span data-stu-id="d7eca-173">**XSD**</span></span>|<span data-ttu-id="d7eca-174">使用 XML 架构定义 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="d7eca-174">Use an XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="d7eca-175">选择此选项将在 **ValidationType**部分中显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-175">Selecting this option displays the dynamic options in section, **ValidationType**.</span></span>|  
  
 <span data-ttu-id="d7eca-176">**FailOnValidationFail**</span><span class="sxs-lookup"><span data-stu-id="d7eca-176">**FailOnValidationFail**</span></span>  
 <span data-ttu-id="d7eca-177">指定在文档验证失败时操作是否失败。</span><span class="sxs-lookup"><span data-stu-id="d7eca-177">Specify whether the operation fails if the document fails to validate.</span></span>  
  
 <span data-ttu-id="d7eca-178">**ValidationDetails**</span><span class="sxs-lookup"><span data-stu-id="d7eca-178">**ValidationDetails**</span></span>  
 <span data-ttu-id="d7eca-179">当此属性的值为 true 时会提供大量错误输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-179">Provides rich error output when the value of this property is true.</span></span> <span data-ttu-id="d7eca-180">有关详细信息，请参阅 [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-180">For more info, see [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).</span></span>  
  
### <a name="validationtype-dynamic-options"></a><span data-ttu-id="d7eca-181">ValidationType 动态选项</span><span class="sxs-lookup"><span data-stu-id="d7eca-181">ValidationType Dynamic Options</span></span>  
  
#### <a name="validationtype--xsd"></a><span data-ttu-id="d7eca-182">ValidationType = XSD</span><span class="sxs-lookup"><span data-stu-id="d7eca-182">ValidationType = XSD</span></span>  
 <span data-ttu-id="d7eca-183">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-183">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-184">选择第二个 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-184">Select the source type of the second XML document.</span></span> <span data-ttu-id="d7eca-185">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-185">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-186">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-186">Value</span></span>|<span data-ttu-id="d7eca-187">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-188">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-188">**Direct input**</span></span>|<span data-ttu-id="d7eca-189">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-189">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-190">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-190">**File connection**</span></span>|<span data-ttu-id="d7eca-191">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-191">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-192">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-192">**Variable**</span></span>|<span data-ttu-id="d7eca-193">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-193">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-194">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-194">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-195">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-195">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-196">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-196">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-197">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-197">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-198">如果将“XPathStringSourceType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-198">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-199">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-199">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xslt"></a><span data-ttu-id="d7eca-200">OperationType = XSLT</span><span class="sxs-lookup"><span data-stu-id="d7eca-200">OperationType = XSLT</span></span>  
 <span data-ttu-id="d7eca-201">指定 XSLT 操作的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-201">Specify options for the XSLT operation.</span></span>  
  
 <span data-ttu-id="d7eca-202">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-202">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-203">指定 XML 任务是否保存 XSLT 操作的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-203">Specify whether the XML task saves the output of the XSLT operation.</span></span>  
  
 <span data-ttu-id="d7eca-204">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-204">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-205">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-205">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-206">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-206">**Destination**</span></span>  
 <span data-ttu-id="d7eca-207">如果将“DestinationType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-207">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-208">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-208">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-209">如果将“DestinationType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-209">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-210">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-210">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-211">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-211">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-212">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-212">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-213">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-213">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-214">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-214">Value</span></span>|<span data-ttu-id="d7eca-215">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-215">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-216">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-216">**File connection**</span></span>|<span data-ttu-id="d7eca-217">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-217">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-218">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-218">**Variable**</span></span>|<span data-ttu-id="d7eca-219">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-219">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-220">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-220">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-221">选择第二个 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-221">Select the source type of the second XML document.</span></span> <span data-ttu-id="d7eca-222">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-222">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-223">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-223">Value</span></span>|<span data-ttu-id="d7eca-224">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-225">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-225">**Direct input**</span></span>|<span data-ttu-id="d7eca-226">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-226">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-227">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-227">**File connection**</span></span>|<span data-ttu-id="d7eca-228">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-228">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-229">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-229">**Variable**</span></span>|<span data-ttu-id="d7eca-230">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-230">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-231">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-231">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-232">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-232">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-233">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-233">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-234">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-234">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-235">如果将“XPathStringSourceType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-235">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-236">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-236">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xpath"></a><span data-ttu-id="d7eca-237">OperationType = XPATH</span><span class="sxs-lookup"><span data-stu-id="d7eca-237">OperationType = XPATH</span></span>  
 <span data-ttu-id="d7eca-238">指定 XPath 操作的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-238">Specify options for the XPath operation.</span></span>  
  
 <span data-ttu-id="d7eca-239">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-239">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-240">指定 XML 任务是否保存 XPath 操作的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-240">Specify whether the XML task saves the output of the XPath operation.</span></span>  
  
 <span data-ttu-id="d7eca-241">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-241">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-242">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-242">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-243">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-243">**Destination**</span></span>  
 <span data-ttu-id="d7eca-244">如果将“DestinationType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-244">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-245">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-245">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-246">如果将“DestinationType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-246">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-247">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-247">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-248">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-248">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-249">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-249">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-250">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-250">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-251">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-251">Value</span></span>|<span data-ttu-id="d7eca-252">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-252">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-253">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-253">**File connection**</span></span>|<span data-ttu-id="d7eca-254">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-254">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-255">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-255">**Variable**</span></span>|<span data-ttu-id="d7eca-256">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-256">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-257">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-257">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-258">选择第二个 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-258">Select the source type of the second XML document.</span></span> <span data-ttu-id="d7eca-259">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-259">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-260">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-260">Value</span></span>|<span data-ttu-id="d7eca-261">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-261">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-262">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-262">**Direct input**</span></span>|<span data-ttu-id="d7eca-263">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-263">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-264">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-264">**File connection**</span></span>|<span data-ttu-id="d7eca-265">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-265">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-266">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-266">**Variable**</span></span>|<span data-ttu-id="d7eca-267">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-267">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-268">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-268">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-269">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-269">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-270">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-270">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-271">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-271">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-272">如果将“XPathStringSourceType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-272">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-273">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-273">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-274">**PutResultInOneNode**</span><span class="sxs-lookup"><span data-stu-id="d7eca-274">**PutResultInOneNode**</span></span>  
 <span data-ttu-id="d7eca-275">指定是否将结果写入单个节点。</span><span class="sxs-lookup"><span data-stu-id="d7eca-275">Specify whether the result is written to a single node.</span></span>  
  
 <span data-ttu-id="d7eca-276">**XPathOperation**</span><span class="sxs-lookup"><span data-stu-id="d7eca-276">**XPathOperation**</span></span>  
 <span data-ttu-id="d7eca-277">选择 XPath 结果类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-277">Select the XPath result type.</span></span> <span data-ttu-id="d7eca-278">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-278">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-279">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-279">Value</span></span>|<span data-ttu-id="d7eca-280">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-280">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-281">**Evaluation**</span><span class="sxs-lookup"><span data-stu-id="d7eca-281">**Evaluation**</span></span>|<span data-ttu-id="d7eca-282">返回 XPath 函数的结果。</span><span class="sxs-lookup"><span data-stu-id="d7eca-282">Returns the results of an XPath function.</span></span>|  
|<span data-ttu-id="d7eca-283">**Node list**</span><span class="sxs-lookup"><span data-stu-id="d7eca-283">**Node list**</span></span>|<span data-ttu-id="d7eca-284">将所选节点返回为 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="d7eca-284">Return the selected nodes as an XML fragment.</span></span>|  
|<span data-ttu-id="d7eca-285">**值**</span><span class="sxs-lookup"><span data-stu-id="d7eca-285">**Values**</span></span>|<span data-ttu-id="d7eca-286">返回所有所选节点的内部文本值，将其连接为字符串。</span><span class="sxs-lookup"><span data-stu-id="d7eca-286">Return the inner text value of all selected nodes, concatenated into a string.</span></span>|  
  
### <a name="operationtype--merge"></a><span data-ttu-id="d7eca-287">OperationType = Merge</span><span class="sxs-lookup"><span data-stu-id="d7eca-287">OperationType = Merge</span></span>  
 <span data-ttu-id="d7eca-288">指定合并操作的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-288">Specify options for the Merge operation.</span></span>  
  
 <span data-ttu-id="d7eca-289">**XPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-289">**XPathStringSourceType**</span></span>  
 <span data-ttu-id="d7eca-290">选择 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-290">Select the source type of the XML document.</span></span> <span data-ttu-id="d7eca-291">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-291">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-292">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-292">Value</span></span>|<span data-ttu-id="d7eca-293">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-293">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-294">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-294">**Direct input**</span></span>|<span data-ttu-id="d7eca-295">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-295">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-296">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-296">**File connection**</span></span>|<span data-ttu-id="d7eca-297">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-297">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-298">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-298">**Variable**</span></span>|<span data-ttu-id="d7eca-299">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-299">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-300">**XPathStringSource**</span><span class="sxs-lookup"><span data-stu-id="d7eca-300">**XPathStringSource**</span></span>  
 <span data-ttu-id="d7eca-301">如果将“XPathStringSourceType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“文档源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-301">If **XPathStringSourceType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-302">如果将“XPathStringSourceType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-302">If **XPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-303">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-303">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-304">如果将“XPathStringSourceType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-304">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-305">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-305">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="d7eca-306">使用 XPath 语句标识源文档中的合并位置时，此语句应返回一个节点。</span><span class="sxs-lookup"><span data-stu-id="d7eca-306">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="d7eca-307">如果该语句返回多个节点，则仅使用第一个节点。</span><span class="sxs-lookup"><span data-stu-id="d7eca-307">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="d7eca-308">第二个文档的内容在 XPath 查询返回的第一个节点下合并。</span><span class="sxs-lookup"><span data-stu-id="d7eca-308">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
 <span data-ttu-id="d7eca-309">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-309">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-310">指定 XML 任务是否保存合并操作的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-310">Specify whether the XML task saves the output of the Merge operation.</span></span>  
  
 <span data-ttu-id="d7eca-311">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-311">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-312">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-312">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-313">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-313">**Destination**</span></span>  
 <span data-ttu-id="d7eca-314">如果将“DestinationType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-314">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-315">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-315">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-316">如果将“DestinationType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-316">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-317">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-317">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-318">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-318">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-319">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-319">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-320">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-320">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-321">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-321">Value</span></span>|<span data-ttu-id="d7eca-322">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-322">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-323">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-323">**File connection**</span></span>|<span data-ttu-id="d7eca-324">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-324">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-325">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-325">**Variable**</span></span>|<span data-ttu-id="d7eca-326">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-326">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-327">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-327">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-328">选择第二个 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-328">Select the destination type of the second XML document.</span></span> <span data-ttu-id="d7eca-329">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-329">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-330">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-330">Value</span></span>|<span data-ttu-id="d7eca-331">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-331">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-332">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-332">**Direct input**</span></span>|<span data-ttu-id="d7eca-333">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-333">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-334">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-334">**File connection**</span></span>|<span data-ttu-id="d7eca-335">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-335">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-336">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-336">**Variable**</span></span>|<span data-ttu-id="d7eca-337">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-337">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-338">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-338">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-339">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“文档源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-339">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-340">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-340">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-341">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-341">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-342">如果将“SecondOperandType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-342">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-343">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-343">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--diff"></a><span data-ttu-id="d7eca-344">OperationType = Diff</span><span class="sxs-lookup"><span data-stu-id="d7eca-344">OperationType = Diff</span></span>  
 <span data-ttu-id="d7eca-345">指定 Diff 运算的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-345">Specify options for the Diff operation.</span></span>  
  
 <span data-ttu-id="d7eca-346">**DiffAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="d7eca-346">**DiffAlgorithm**</span></span>  
 <span data-ttu-id="d7eca-347">选择在比较文档时要使用的 Diff 算法。</span><span class="sxs-lookup"><span data-stu-id="d7eca-347">Select the Diff algorithm to use when comparing documents.</span></span> <span data-ttu-id="d7eca-348">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-348">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-349">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-349">Value</span></span>|<span data-ttu-id="d7eca-350">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-350">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-351">**Auto**</span><span class="sxs-lookup"><span data-stu-id="d7eca-351">**Auto**</span></span>|<span data-ttu-id="d7eca-352">由 XML 任务确定是使用快速算法还是使用精确算法。</span><span class="sxs-lookup"><span data-stu-id="d7eca-352">Let the XML task determine whether to use the fast or precise algorithm.</span></span>|  
|<span data-ttu-id="d7eca-353">**Fast**</span><span class="sxs-lookup"><span data-stu-id="d7eca-353">**Fast**</span></span>|<span data-ttu-id="d7eca-354">使用快速但精确度较低的 Diff 算法。</span><span class="sxs-lookup"><span data-stu-id="d7eca-354">Use a fast, but less precise Diff algorithm.</span></span>|  
|<span data-ttu-id="d7eca-355">**Precise**</span><span class="sxs-lookup"><span data-stu-id="d7eca-355">**Precise**</span></span>|<span data-ttu-id="d7eca-356">使用精确的 Diff 算法。</span><span class="sxs-lookup"><span data-stu-id="d7eca-356">Use a precise Diff algorithm.</span></span>|  
  
 <span data-ttu-id="d7eca-357">**Diff 选项**</span><span class="sxs-lookup"><span data-stu-id="d7eca-357">**Diff Options**</span></span>  
 <span data-ttu-id="d7eca-358">将 Diff 选项设置为应用于 Diff 运算。</span><span class="sxs-lookup"><span data-stu-id="d7eca-358">Set the Diff options to apply to the Diff operation.</span></span> <span data-ttu-id="d7eca-359">下表中列出了这些选项：</span><span class="sxs-lookup"><span data-stu-id="d7eca-359">The options are listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-360">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-360">Value</span></span>|<span data-ttu-id="d7eca-361">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-361">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-362">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="d7eca-362">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="d7eca-363">指定是否比较 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="d7eca-363">Specify whether to compare the XML declaration.</span></span>|  
|<span data-ttu-id="d7eca-364">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="d7eca-364">**IgnoreDTD**</span></span>|<span data-ttu-id="d7eca-365">指定是否忽略文档类型定义 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-365">Specify whether to ignore the document type definition (DTD).</span></span>|  
|<span data-ttu-id="d7eca-366">**IgnoreWhite Spaces**</span><span class="sxs-lookup"><span data-stu-id="d7eca-366">**IgnoreWhite Spaces**</span></span>|<span data-ttu-id="d7eca-367">指定比较文档时是否忽略空格数量的不同。</span><span class="sxs-lookup"><span data-stu-id="d7eca-367">Specify whether to ignore differences in the amount of white space when comparing documents.</span></span>|  
|<span data-ttu-id="d7eca-368">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="d7eca-368">**IgnoreNamespaces**</span></span>|<span data-ttu-id="d7eca-369">指定是否比较元素及其属性名称的命名空间统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-369">Specify whether to compare the namespace uniform resource identifier (URI) of an element and its attribute names.</span></span><br /><br /> <span data-ttu-id="d7eca-370">注意：如果将此选项设置为 `True`，则本地名称相同但命名空间不同的两个元素将被视为同一元素。</span><span class="sxs-lookup"><span data-stu-id="d7eca-370">Note: If this option is set to `True`, two elements that have the same local name but different namespaces are considered identical.</span></span>|  
|<span data-ttu-id="d7eca-371">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="d7eca-371">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="d7eca-372">指定是否比较处理指令。</span><span class="sxs-lookup"><span data-stu-id="d7eca-372">Specify whether to compare processing instructions.</span></span>|  
|<span data-ttu-id="d7eca-373">**IgnoreOrderOf ChildElements**</span><span class="sxs-lookup"><span data-stu-id="d7eca-373">**IgnoreOrderOf ChildElements**</span></span>|<span data-ttu-id="d7eca-374">指定是否比较子元素的顺序。</span><span class="sxs-lookup"><span data-stu-id="d7eca-374">Specify whether to compare the order of child elements.</span></span><br /><br /> <span data-ttu-id="d7eca-375">注意：如果将此选项设置为 `True`，同级列表中仅位置不同的子元素将被视为同一子元素。</span><span class="sxs-lookup"><span data-stu-id="d7eca-375">Note: If this option is set to `True`, child elements that differ only in their position in a list of siblings are considered identical.</span></span>|  
|<span data-ttu-id="d7eca-376">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="d7eca-376">**IgnoreComments**</span></span>|<span data-ttu-id="d7eca-377">指定是否比较注释节点。</span><span class="sxs-lookup"><span data-stu-id="d7eca-377">Specify whether to compare comment nodes.</span></span>|  
|<span data-ttu-id="d7eca-378">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="d7eca-378">**IgnorePrefixes**</span></span>|<span data-ttu-id="d7eca-379">指定是否比较元素及属性名称的前缀。</span><span class="sxs-lookup"><span data-stu-id="d7eca-379">Specify whether to compare prefixes of element and attribute names.</span></span><br /><br /> <span data-ttu-id="d7eca-380">注意：如果将此选项设置为 `True`，则本地名称相同但命名空间 URI 和前缀不同的两个元素将被视为同一元素。</span><span class="sxs-lookup"><span data-stu-id="d7eca-380">Note: If you set this option to `True`, two elements that have the same local name, but different namespace URIs and prefixes, are considered identical.</span></span>|  
  
 <span data-ttu-id="d7eca-381">**FailOnDifference**</span><span class="sxs-lookup"><span data-stu-id="d7eca-381">**FailOnDifference**</span></span>  
 <span data-ttu-id="d7eca-382">指定在 Diff 运算失败时任务是否失败。</span><span class="sxs-lookup"><span data-stu-id="d7eca-382">Specify whether the task fails if the Diff operation fails.</span></span>  
  
 <span data-ttu-id="d7eca-383">**SaveDiffGram**</span><span class="sxs-lookup"><span data-stu-id="d7eca-383">**SaveDiffGram**</span></span>  
 <span data-ttu-id="d7eca-384">指定是否保存比较结果，即 DiffGram 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-384">Specify whether to save the comparison result, a DiffGram document.</span></span>  
  
 <span data-ttu-id="d7eca-385">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-385">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-386">指定 XML 任务是否保存 Diff 运算的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-386">Specify whether the XML task saves the output of the Diff operation.</span></span>  
  
 <span data-ttu-id="d7eca-387">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-387">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-388">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-388">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-389">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-389">**Destination**</span></span>  
 <span data-ttu-id="d7eca-390">如果将“DestinationType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-390">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-391">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-391">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-392">如果将“DestinationType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-392">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-393">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-393">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-394">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-394">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-395">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-395">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-396">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-396">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-397">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-397">Value</span></span>|<span data-ttu-id="d7eca-398">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-398">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-399">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-399">**File connection**</span></span>|<span data-ttu-id="d7eca-400">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-400">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-401">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-401">**Variable**</span></span>|<span data-ttu-id="d7eca-402">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-402">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-403">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-403">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-404">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-404">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-405">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-405">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-406">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-406">Value</span></span>|<span data-ttu-id="d7eca-407">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-407">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-408">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-408">**Direct input**</span></span>|<span data-ttu-id="d7eca-409">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-409">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-410">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-410">**File connection**</span></span>|<span data-ttu-id="d7eca-411">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-411">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-412">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-412">**Variable**</span></span>|<span data-ttu-id="d7eca-413">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-413">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-414">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-414">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-415">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“文档源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-415">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-416">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-416">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-417">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-417">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-418">如果将“SecondOperandType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-418">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-419">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-419">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--patch"></a><span data-ttu-id="d7eca-420">OperationType = Patch</span><span class="sxs-lookup"><span data-stu-id="d7eca-420">OperationType = Patch</span></span>  
 <span data-ttu-id="d7eca-421">指定修补操作的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-421">Specify options for the Patch operation.</span></span>  
  
 <span data-ttu-id="d7eca-422">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="d7eca-422">**SaveOperationResult**</span></span>  
 <span data-ttu-id="d7eca-423">指定 XML 任务是否保存修补操作的输出。</span><span class="sxs-lookup"><span data-stu-id="d7eca-423">Specify whether the XML task saves the output of the Patch operation.</span></span>  
  
 <span data-ttu-id="d7eca-424">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d7eca-424">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d7eca-425">指定是否覆盖目标文件或变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-425">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="d7eca-426">**目标**</span><span class="sxs-lookup"><span data-stu-id="d7eca-426">**Destination**</span></span>  
 <span data-ttu-id="d7eca-427">如果将“DestinationType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-427">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-428">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-428">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-429">如果将“DestinationType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-429">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-430">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eca-430">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="d7eca-431">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="d7eca-431">**DestinationType**</span></span>  
 <span data-ttu-id="d7eca-432">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-432">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-433">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-433">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-434">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-434">Value</span></span>|<span data-ttu-id="d7eca-435">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-435">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-436">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-436">**File connection**</span></span>|<span data-ttu-id="d7eca-437">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-437">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-438">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-438">**Variable**</span></span>|<span data-ttu-id="d7eca-439">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-439">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-440">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="d7eca-440">**SecondOperandType**</span></span>  
 <span data-ttu-id="d7eca-441">选择 XML 文档的目标类型。</span><span class="sxs-lookup"><span data-stu-id="d7eca-441">Select the destination type of the XML document.</span></span> <span data-ttu-id="d7eca-442">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="d7eca-442">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d7eca-443">值</span><span class="sxs-lookup"><span data-stu-id="d7eca-443">Value</span></span>|<span data-ttu-id="d7eca-444">说明</span><span class="sxs-lookup"><span data-stu-id="d7eca-444">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7eca-445">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="d7eca-445">**Direct input**</span></span>|<span data-ttu-id="d7eca-446">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d7eca-446">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="d7eca-447">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="d7eca-447">**File connection**</span></span>|<span data-ttu-id="d7eca-448">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="d7eca-448">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="d7eca-449">**变量**</span><span class="sxs-lookup"><span data-stu-id="d7eca-449">**Variable**</span></span>|<span data-ttu-id="d7eca-450">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="d7eca-450">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="d7eca-451">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="d7eca-451">**SecondOperand**</span></span>  
 <span data-ttu-id="d7eca-452">如果将“SecondOperandType”设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…)，再使用“文档源编辑器”对话框提供 XML 代码     。</span><span class="sxs-lookup"><span data-stu-id="d7eca-452">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d7eca-453">如果将“SecondOperandType”设置为“文件连接”，请选择文件连接管理器，或单击 \<**New connection...**> 以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-453">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d7eca-454">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-454">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d7eca-455">如果将“SecondOperandType”设置为“变量”，请选择现有变量，或单击 \<**New variable...**> 以创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="d7eca-455">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d7eca-456">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d7eca-456">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7eca-457">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7eca-457">See Also</span></span>  
 <span data-ttu-id="d7eca-458">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d7eca-458">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="d7eca-459">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="d7eca-459">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
