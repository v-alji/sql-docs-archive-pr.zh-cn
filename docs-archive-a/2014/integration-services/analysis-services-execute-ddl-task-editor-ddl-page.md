---
title: Analysis Services (DDL 页上执行 DDL 任务编辑器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d207afe666e582c44f1014a6c80f4f4984fd5410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579716"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a><span data-ttu-id="27ee4-102">Analysis Services 执行 DDL 任务编辑器（DDL 页）</span><span class="sxs-lookup"><span data-stu-id="27ee4-102">Analysis Services Execute DDL Task Editor (DDL Page)</span></span>
  <span data-ttu-id="27ee4-103">可以使用“Analysis Services 执行 DDL 任务编辑器”对话框的 **DDL** 页指定与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库的连接，以及提供有关数据定义语言 (DDL) 语句的源的信息。</span><span class="sxs-lookup"><span data-stu-id="27ee4-103">Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and to provide information about the source of data definition language (DDL) statements.</span></span>  
  
 <span data-ttu-id="27ee4-104">若要了解此任务，请参阅 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)。</span><span class="sxs-lookup"><span data-stu-id="27ee4-104">To learn about this task, see [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="27ee4-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="27ee4-105">Static Options</span></span>  
 <span data-ttu-id="27ee4-106">**Connection**</span><span class="sxs-lookup"><span data-stu-id="27ee4-106">**Connection**</span></span>  
 <span data-ttu-id="27ee4-107">在列表中选择 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 连接管理器，或者单击“\<**New connection...**>”并使用“添加 Analysis Services 连接管理器”对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="27ee4-107">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list, or click \<**New connection...**> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="27ee4-108">**相关主题：** [“添加 Analysis Services 连接管理器”对话框 UI 参考](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)、[Analysis Services 连接管理器](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="27ee4-108">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="27ee4-109">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="27ee4-109">**SourceType**</span></span>  
 <span data-ttu-id="27ee4-110">指定 DDL 语句的源类型。</span><span class="sxs-lookup"><span data-stu-id="27ee4-110">Specify the source type of the DDL statements.</span></span> <span data-ttu-id="27ee4-111">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="27ee4-111">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="27ee4-112">值</span><span class="sxs-lookup"><span data-stu-id="27ee4-112">Value</span></span>|<span data-ttu-id="27ee4-113">说明</span><span class="sxs-lookup"><span data-stu-id="27ee4-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27ee4-114">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="27ee4-114">**Direct Input**</span></span>|<span data-ttu-id="27ee4-115">将源设置为 **SourceDirect** 文本框中存储的 DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="27ee4-115">Set the source to the DDL statement stored in the **SourceDirect** text box.</span></span> <span data-ttu-id="27ee4-116">选择此值将显示以下部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="27ee4-116">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="27ee4-117">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="27ee4-117">**File Connection**</span></span>|<span data-ttu-id="27ee4-118">将源设置为包含 DDL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="27ee4-118">Set the source to a file that contains the DDL statement.</span></span> <span data-ttu-id="27ee4-119">选择此值将显示以下部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="27ee4-119">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="27ee4-120">**变量**</span><span class="sxs-lookup"><span data-stu-id="27ee4-120">**Variable**</span></span>|<span data-ttu-id="27ee4-121">将源设置为变量。</span><span class="sxs-lookup"><span data-stu-id="27ee4-121">Set the source to a variable.</span></span> <span data-ttu-id="27ee4-122">选择此值将显示以下部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="27ee4-122">Selecting this value displays the dynamic options in the following section.</span></span>|  
  
## <a name="dynamic-options"></a><span data-ttu-id="27ee4-123">动态选项</span><span class="sxs-lookup"><span data-stu-id="27ee4-123">Dynamic Options</span></span>  
  
### <a name="sourcetype--direct-input"></a><span data-ttu-id="27ee4-124">SourceType = 直接输入</span><span class="sxs-lookup"><span data-stu-id="27ee4-124">SourceType = Direct Input</span></span>  
 <span data-ttu-id="27ee4-125">**数据源**</span><span class="sxs-lookup"><span data-stu-id="27ee4-125">**Source**</span></span>  
 <span data-ttu-id="27ee4-126">键入 DDL 语句，或单击省略号 (…)，然后在“DDL 语句”对话框中键入语句   。</span><span class="sxs-lookup"><span data-stu-id="27ee4-126">Type the DDL statements or click the ellipsis **(...)** and then type the statements in the **DDL Statements** dialog box.</span></span>  
  
### <a name="sourcetype--file-connection"></a><span data-ttu-id="27ee4-127">SourceType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="27ee4-127">SourceType = File Connection</span></span>  
 <span data-ttu-id="27ee4-128">**数据源**</span><span class="sxs-lookup"><span data-stu-id="27ee4-128">**Source**</span></span>  
 <span data-ttu-id="27ee4-129">在列表中选择“文件连接”，或单击“\<**New connection...**>”并使用“文件连接管理器”对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="27ee4-129">Select a File connection in the list, or click \<**New connection...**> and use the **File Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="27ee4-130">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="27ee4-130">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
### <a name="sourcetype--variable"></a><span data-ttu-id="27ee4-131">SourceType = 变量</span><span class="sxs-lookup"><span data-stu-id="27ee4-131">SourceType = Variable</span></span>  
 <span data-ttu-id="27ee4-132">**数据源**</span><span class="sxs-lookup"><span data-stu-id="27ee4-132">**Source**</span></span>  
 <span data-ttu-id="27ee4-133">在列表中选择一个变量，或单击“\<**New variable...**>”并使用“添加变量”对话框创建新的变量。</span><span class="sxs-lookup"><span data-stu-id="27ee4-133">Select a variable in the list, or click \<**New variable...**> and use the **Add Variable** dialog box to create a new variable.</span></span>  
  
 <span data-ttu-id="27ee4-134">**相关主题：** [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="27ee4-134">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ee4-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27ee4-135">See Also</span></span>  
 <span data-ttu-id="27ee4-136">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="27ee4-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="27ee4-137">[Analysis Services 在 "常规" 页上执行 DDL 任务编辑器 &#40;&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="27ee4-137">[Analysis Services Execute DDL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="27ee4-138">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="27ee4-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="27ee4-139">[控制流](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="27ee4-139">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="27ee4-140">[Analysis Services 脚本语言 &#40;ASSL&#41; 参考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span><span class="sxs-lookup"><span data-stu-id="27ee4-140">[Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span></span>  
 [<span data-ttu-id="27ee4-141">XML for Analysis (XMLA) 参考</span><span class="sxs-lookup"><span data-stu-id="27ee4-141">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
