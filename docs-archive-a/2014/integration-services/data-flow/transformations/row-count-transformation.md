---
title: 行计数转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b0940d608aeaa96b7ec43fa4486944ce0f887e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694544"
---
# <a name="row-count-transformation"></a><span data-ttu-id="47e8c-102">行计数转换</span><span class="sxs-lookup"><span data-stu-id="47e8c-102">Row Count Transformation</span></span>
  <span data-ttu-id="47e8c-103">行计数转换在行通过数据流时对行进行计数，并将最终计数结果存储在一个变量中。</span><span class="sxs-lookup"><span data-stu-id="47e8c-103">The Row Count transformation counts rows as they pass through a data flow and stores the final count in a variable.</span></span>  
  
 <span data-ttu-id="47e8c-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包可使用行计数来更新脚本、表达式和属性表达式中使用的变量。</span><span class="sxs-lookup"><span data-stu-id="47e8c-104">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can use row counts to update the variables used in scripts, expressions, and property expressions.</span></span> <span data-ttu-id="47e8c-105">（例如，存储行计数的变量可更新电子邮件中的消息正文，以便包含行数。）行计数转换使用的变量必须已经存在，并且必须在带有行计数转换的数据流所属的数据流任务作用域内。</span><span class="sxs-lookup"><span data-stu-id="47e8c-105">(For example, the variable that stores the row count can update the message text in an e-mail message to include the number of rows.) The variable that the Row Count transformation uses must already exist, and it must be in the scope of the Data Flow task to which the data flow with the Row Count transformation belongs.</span></span>  
  
 <span data-ttu-id="47e8c-106">只有在最后一行已通过转换后，转换才会在变量中存储行计数值。</span><span class="sxs-lookup"><span data-stu-id="47e8c-106">The transformation stores the row count value in the variable only after the last row has passed through the transformation.</span></span> <span data-ttu-id="47e8c-107">因此，该变量值并不即时更新以在包含行计数转换的数据流中使用更新值。</span><span class="sxs-lookup"><span data-stu-id="47e8c-107">Therefore, the value of the variable is not updated in time to use the updated value in the data flow that contains the Row Count transformation.</span></span> <span data-ttu-id="47e8c-108">您可以在单独的数据流中使用更新的变量。</span><span class="sxs-lookup"><span data-stu-id="47e8c-108">You can use the updated variable in a separate data flow.</span></span>  
  
 <span data-ttu-id="47e8c-109">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="47e8c-109">This transformation has one input and one output.</span></span> <span data-ttu-id="47e8c-110">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="47e8c-110">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-row-count-transformation"></a><span data-ttu-id="47e8c-111">行计数转换的配置</span><span class="sxs-lookup"><span data-stu-id="47e8c-111">Configuration of the Row Count Transformation</span></span>  
 <span data-ttu-id="47e8c-112">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="47e8c-112">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="47e8c-113">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="47e8c-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="47e8c-114">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="47e8c-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="47e8c-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="47e8c-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="47e8c-116">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="47e8c-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="47e8c-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="47e8c-117">Related Tasks</span></span>  
 <span data-ttu-id="47e8c-118">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="47e8c-118">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e8c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47e8c-119">See Also</span></span>  
 <span data-ttu-id="47e8c-120">[Integration Services (SSIS) 变量](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="47e8c-120">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="47e8c-121">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="47e8c-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="47e8c-122">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="47e8c-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
