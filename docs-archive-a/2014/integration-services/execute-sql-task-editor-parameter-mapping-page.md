---
title: 执行 SQL 任务编辑器 (参数映射页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580317"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a><span data-ttu-id="46bbf-102">执行 SQL 任务编辑器（“参数映射”页）</span><span class="sxs-lookup"><span data-stu-id="46bbf-102">Execute SQL Task Editor (Parameter Mapping Page)</span></span>
  <span data-ttu-id="46bbf-103">可以使用 **“执行 SQL 任务编辑器”** 对话框的 **“参数映射”** 页，将变量映射到 SQL 语句中的参数。</span><span class="sxs-lookup"><span data-stu-id="46bbf-103">Use the **Parameter Mapping** page of the **Execute SQL Task Editor** dialog box to map variables to parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="46bbf-104">若要了解此任务，请参阅 [执行 SQL 任务](control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="46bbf-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="46bbf-105">选项</span><span class="sxs-lookup"><span data-stu-id="46bbf-105">Options</span></span>  
 <span data-ttu-id="46bbf-106">**“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="46bbf-106">**Variable Name**</span></span>  
 <span data-ttu-id="46bbf-107">单击“添加”添加了参数映射后，请从列表中选择系统变量或用户定义的变量，或单击“\<**New variable...**>”以使用“添加变量”对话框添加新变量 。</span><span class="sxs-lookup"><span data-stu-id="46bbf-107">After you have added a parameter mapping by clicking **Add**, select a system or user-defined variable from the list or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="46bbf-108">**相关主题：** [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="46bbf-108">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
 <span data-ttu-id="46bbf-109">**方向**</span><span class="sxs-lookup"><span data-stu-id="46bbf-109">**Direction**</span></span>  
 <span data-ttu-id="46bbf-110">选择参数的方向。</span><span class="sxs-lookup"><span data-stu-id="46bbf-110">Select the direction of the parameter.</span></span> <span data-ttu-id="46bbf-111">将每个变量映射到输入参数、输出参数或返回代码。</span><span class="sxs-lookup"><span data-stu-id="46bbf-111">Map each variable to an input parameter, output parameter, or a return code.</span></span>  
  
 <span data-ttu-id="46bbf-112">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="46bbf-112">**Data Type**</span></span>  
 <span data-ttu-id="46bbf-113">选择参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="46bbf-113">Select the data type of the parameter.</span></span> <span data-ttu-id="46bbf-114">可用数据类型的列表取决于您为任务所用的连接管理器选择的访问接口。</span><span class="sxs-lookup"><span data-stu-id="46bbf-114">The list of available data types is specific to the provider selected in the connection manager used by the task.</span></span>  
  
 <span data-ttu-id="46bbf-115">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="46bbf-115">**Parameter Name**</span></span>  
 <span data-ttu-id="46bbf-116">提供参数名称。</span><span class="sxs-lookup"><span data-stu-id="46bbf-116">Provide a parameter name.</span></span>  
  
 <span data-ttu-id="46bbf-117">必须使用数值还是参数名称取决于任务所用的连接管理器类型。</span><span class="sxs-lookup"><span data-stu-id="46bbf-117">Depending on the connection manager type that the task uses, you must use numbers or parameter names.</span></span> <span data-ttu-id="46bbf-118">一些连接管理器类型要求，参数名的首字符必须为 \@ 符号（如 \@Param1 等特定名称），或将列名用作参数名。</span><span class="sxs-lookup"><span data-stu-id="46bbf-118">Some connection manager types require that the first character of the parameter name is the \@ sign , specific names like \@Param1, or column names as parameter names.</span></span>  
  
 <span data-ttu-id="46bbf-119">**相关主题：** [执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="46bbf-119">**Related Topics:** [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="46bbf-120">**参数大小**</span><span class="sxs-lookup"><span data-stu-id="46bbf-120">**Parameter Size**</span></span>  
 <span data-ttu-id="46bbf-121">提供具有可变长度的参数的大小，如字符串和二进制字段。</span><span class="sxs-lookup"><span data-stu-id="46bbf-121">Provide the size of parameters that have variable length, such as strings and binary fields.</span></span>  
  
 <span data-ttu-id="46bbf-122">此设置可确保访问接口为长度可变的参数值分配足够的空间。</span><span class="sxs-lookup"><span data-stu-id="46bbf-122">This setting ensures that the provider allocates sufficient space for variable-length parameter values.</span></span>  
  
 <span data-ttu-id="46bbf-123">**添加**</span><span class="sxs-lookup"><span data-stu-id="46bbf-123">**Add**</span></span>  
 <span data-ttu-id="46bbf-124">单击此项可添加参数映射。</span><span class="sxs-lookup"><span data-stu-id="46bbf-124">Click to add a parameter mapping.</span></span>  
  
 <span data-ttu-id="46bbf-125">**删除**</span><span class="sxs-lookup"><span data-stu-id="46bbf-125">**Remove**</span></span>  
 <span data-ttu-id="46bbf-126">选择列表中的参数映射，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="46bbf-126">Select a parameter mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bbf-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46bbf-127">See Also</span></span>  
 <span data-ttu-id="46bbf-128">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="46bbf-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="46bbf-129">[&#40;"常规" 页上执行 SQL 任务编辑器&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="46bbf-129">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="46bbf-130">[&#40;"结果集" 页上执行 SQL 任务编辑器&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span><span class="sxs-lookup"><span data-stu-id="46bbf-130">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span></span>  
 [<span data-ttu-id="46bbf-131">Transact-SQL 参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="46bbf-131">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
