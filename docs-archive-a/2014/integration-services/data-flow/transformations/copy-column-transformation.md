---
title: 复制列转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd2745070a92ab71e89f3bfa9edd8673b676632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587937"
---
# <a name="copy-column-transformation"></a><span data-ttu-id="cf4e2-102">复制列转换</span><span class="sxs-lookup"><span data-stu-id="cf4e2-102">Copy Column Transformation</span></span>
  <span data-ttu-id="cf4e2-103">复制列转换通过复制输入列并将新列添加到转换输出来创建新列。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-103">The Copy Column transformation creates new columns by copying input columns and adding the new columns to the transformation output.</span></span> <span data-ttu-id="cf4e2-104">以后在数据流中，可将不同的转换应用到列副本。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-104">Later in the data flow, different transformations can be applied to the column copies.</span></span> <span data-ttu-id="cf4e2-105">例如，您可以使用复制列转换来创建列的副本，然后使用字符映射表转换将复制的数据转换为大写字符，或使用聚合转换将聚合应用到此新列。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-105">For example, you can use the Copy Column transformation to create a copy of a column and then convert the copied data to uppercase characters by using the Character Map transformation, or apply aggregations to the new column by using the Aggregate transformation.</span></span>  
  
## <a name="configuration-of-the-copy-column-transformation"></a><span data-ttu-id="cf4e2-106">复制列转换的配置</span><span class="sxs-lookup"><span data-stu-id="cf4e2-106">Configuration of the Copy Column Transformation</span></span>  
 <span data-ttu-id="cf4e2-107">可以通过指定要复制的输入列来配置复制列转换。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-107">You configure the Copy Column transformation by specifying the input columns to copy.</span></span> <span data-ttu-id="cf4e2-108">可以在一个操作中创建一列的多个副本，或创建多个列的副本。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-108">You can create multiple copies of a column, or create copies of multiple columns in one operation.</span></span>  
  
 <span data-ttu-id="cf4e2-109">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-109">This transformation has one input and one output.</span></span> <span data-ttu-id="cf4e2-110">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="cf4e2-111">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-111">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cf4e2-112">有关可以在 **“复制列转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Copy Column Transformation Editor](../../copy-column-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-112">For more information about the properties that you can set in the **Copy Column Transformation Editor** dialog box, see [Copy Column Transformation Editor](../../copy-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="cf4e2-113">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="cf4e2-114">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="cf4e2-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cf4e2-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cf4e2-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="cf4e2-116">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="cf4e2-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="cf4e2-117">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4e2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf4e2-118">See Also</span></span>  
 <span data-ttu-id="cf4e2-119">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="cf4e2-119">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="cf4e2-120">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="cf4e2-120">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
