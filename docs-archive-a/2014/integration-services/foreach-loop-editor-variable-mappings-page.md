---
title: Foreach 循环编辑器 (的 "变量映射" 页) |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd37c8c6c00f18d8b5493a058239cc880ecc1f5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694527"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a><span data-ttu-id="3beca-102">Foreach 循环编辑器（“变量映射”页）</span><span class="sxs-lookup"><span data-stu-id="3beca-102">Foreach Loop Editor (Variable Mappings Page)</span></span>
  <span data-ttu-id="3beca-103">可以使用 **“Foreach 循环编辑器”** 对话框的 **“变量映射”** 页，将变量映射到集合值。</span><span class="sxs-lookup"><span data-stu-id="3beca-103">Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value.</span></span> <span data-ttu-id="3beca-104">循环每次迭代时，都会用集合值更新变量的值。</span><span class="sxs-lookup"><span data-stu-id="3beca-104">The value of the variable is updated with the collection values on each iteration of the loop.</span></span>  
  
 <span data-ttu-id="3beca-105">若要了解如何在 Integration Services 包中使用 Foreach 循环容器，请参阅 [Foreach Loop Container](control-flow/foreach-loop-container.md) 。</span><span class="sxs-lookup"><span data-stu-id="3beca-105">To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](control-flow/foreach-loop-container.md) .</span></span> <span data-ttu-id="3beca-106">若要了解如何配置该循环容器，请参阅 [配置 Foreach 循环容器](../../2014/integration-services/configure-a-foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="3beca-106">To learn about how to configure it, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="3beca-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教程“创建简单 ETL 包教程”包括一节介绍如何添加和配置 Foreach 循环的课程。</span><span class="sxs-lookup"><span data-stu-id="3beca-107">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3beca-108">选项</span><span class="sxs-lookup"><span data-stu-id="3beca-108">Options</span></span>  
 <span data-ttu-id="3beca-109">**变量**</span><span class="sxs-lookup"><span data-stu-id="3beca-109">**Variable**</span></span>  
 <span data-ttu-id="3beca-110">选择现有变量或单击 \<**New variable...**> 以创建新变量。</span><span class="sxs-lookup"><span data-stu-id="3beca-110">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3beca-111">映射一个变量之后，“变量”  列表中会自动增加一行。</span><span class="sxs-lookup"><span data-stu-id="3beca-111">After you map a variable, a new row is automatically added to the **Variable** list.</span></span>  
  
 <span data-ttu-id="3beca-112">**相关主题**：[Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="3beca-112">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="3beca-113">**Index**</span><span class="sxs-lookup"><span data-stu-id="3beca-113">**Index**</span></span>  
 <span data-ttu-id="3beca-114">如果使用的是 Foreach Item 枚举器，请指定集合值中要映射到变量的列的索引。</span><span class="sxs-lookup"><span data-stu-id="3beca-114">If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable.</span></span> <span data-ttu-id="3beca-115">对于其他枚举器类型，索引是只读的。</span><span class="sxs-lookup"><span data-stu-id="3beca-115">For other enumerator types, the index is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3beca-116">索引以 0 为基数。</span><span class="sxs-lookup"><span data-stu-id="3beca-116">The index is 0-based.</span></span>  
  
 <span data-ttu-id="3beca-117">**相关主题**： [使用 Foreach 循环容器循环遍历 Excel 文件和表](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span><span class="sxs-lookup"><span data-stu-id="3beca-117">**Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span></span>  
  
 <span data-ttu-id="3beca-118">**删除**</span><span class="sxs-lookup"><span data-stu-id="3beca-118">**Delete**</span></span>  
 <span data-ttu-id="3beca-119">选择一个变量，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="3beca-119">Select a variable, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3beca-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3beca-120">See Also</span></span>  
 <span data-ttu-id="3beca-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3beca-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3beca-122">[Foreach 循环编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3beca-122">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3beca-123">[Foreach 循环编辑器 &#40;收集页面&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span><span class="sxs-lookup"><span data-stu-id="3beca-123">[Foreach Loop Editor &#40;Collection Page&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span></span>  
 <span data-ttu-id="3beca-124">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="3beca-124">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="3beca-125">For 循环容器</span><span class="sxs-lookup"><span data-stu-id="3beca-125">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
