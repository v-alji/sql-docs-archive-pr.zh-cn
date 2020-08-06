---
title: 逆透视转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c3b93370b34440b73b4c9c78dc7d19fa4095275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578934"
---
# <a name="unpivot-transformation-editor"></a><span data-ttu-id="3249c-102">“逆透视转换编辑器”</span><span class="sxs-lookup"><span data-stu-id="3249c-102">Unpivot Transformation Editor</span></span>
  <span data-ttu-id="3249c-103">可以使用 **“逆透视转换编辑器”** 对话框，选择要透视到行中的列以及指定数据列和新的透视值输出列。</span><span class="sxs-lookup"><span data-stu-id="3249c-103">Use the **Unpivot Transformation Editor** dialog box to select the columns to pivot into rows, and to specify the data column and the new pivot value output column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3249c-104"> 本主题围绕 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) 中所述的“逆透视”应用场景，举例说明各选项的使用方法。</span><span class="sxs-lookup"><span data-stu-id="3249c-104">This topic relies on the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) to illustrate the use of the options.</span></span>  
  
 <span data-ttu-id="3249c-105">若要了解有关逆透视转换的详细信息，请参阅 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="3249c-105">To learn more about the Unpivot transformation, see [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3249c-106">选项</span><span class="sxs-lookup"><span data-stu-id="3249c-106">Options</span></span>  
 <span data-ttu-id="3249c-107">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="3249c-107">**Available Input Columns**</span></span>  
 <span data-ttu-id="3249c-108">使用复选框指定要透视到行中的列。</span><span class="sxs-lookup"><span data-stu-id="3249c-108">Using the check boxes, specify the columns to pivot into rows.</span></span>  
  
 <span data-ttu-id="3249c-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="3249c-109">**Name**</span></span>  
 <span data-ttu-id="3249c-110">查看可用输入列的名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-110">View the name of the available input column.</span></span>  
  
 <span data-ttu-id="3249c-111">**传递**</span><span class="sxs-lookup"><span data-stu-id="3249c-111">**Pass Through**</span></span>  
 <span data-ttu-id="3249c-112">指示是否在逆透视的输出中包括该列。</span><span class="sxs-lookup"><span data-stu-id="3249c-112">Indicate whether to include the column in the unpivoted output.</span></span>  
  
 <span data-ttu-id="3249c-113">**输入列**</span><span class="sxs-lookup"><span data-stu-id="3249c-113">**Input Column**</span></span>  
 <span data-ttu-id="3249c-114">从每行的可用输入列的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="3249c-114">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="3249c-115">通过选中 **“可用输入列”** 表中的复选框来选择列。</span><span class="sxs-lookup"><span data-stu-id="3249c-115">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="3249c-116">在 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)所述的“逆透视”应用场景中，输入列为 **Ham**, **Soda**, **Milk**, **Beer**和 **Chips** 列。</span><span class="sxs-lookup"><span data-stu-id="3249c-116">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Input Columns are the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns.</span></span>  
  
 <span data-ttu-id="3249c-117">**目标列**</span><span class="sxs-lookup"><span data-stu-id="3249c-117">**Destination Column**</span></span>  
 <span data-ttu-id="3249c-118">提供数据列的名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-118">Provide a name for the data column.</span></span>  
  
 <span data-ttu-id="3249c-119">在 [逆透视转换](data-flow/transformations/unpivot-transformation.md)所述的“逆透视”应用场景中，目标列为数量 (**Qty**) 列。</span><span class="sxs-lookup"><span data-stu-id="3249c-119">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Destination Column is the quantity (**Qty**) column.</span></span>  
  
 <span data-ttu-id="3249c-120">**透视键值**</span><span class="sxs-lookup"><span data-stu-id="3249c-120">**Pivot Key Value**</span></span>  
 <span data-ttu-id="3249c-121">提供透视值的名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-121">Provide a name for the pivot value.</span></span> <span data-ttu-id="3249c-122">默认值为输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-122">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="3249c-123">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="3249c-123">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="3249c-124">在 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)所述的“逆透视”应用场景中，透视值将显示为由 **“透视键值列名”** 选项指定的新 Product 列中的文本值，即 **Ham**, **Soda**, **Milk**, **Beer**和 **Chips**。</span><span class="sxs-lookup"><span data-stu-id="3249c-124">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Values will appear in the new Product column designated by the **Pivot Key Value Column Name** option, as the text values **Ham**, **Soda**, **Milk**, **Beer**, and **Chips**.</span></span>  
  
 <span data-ttu-id="3249c-125">**“透视键值列名”**</span><span class="sxs-lookup"><span data-stu-id="3249c-125">**Pivot Key Value Column Name**</span></span>  
 <span data-ttu-id="3249c-126">提供透视值列的名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-126">Provide a name for the pivot value column.</span></span> <span data-ttu-id="3249c-127">默认名称为“Pivot Key Value”；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="3249c-127">The default is "Pivot Key Value"; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="3249c-128">在 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)所述的“逆透视”应用场景中，“透视键值列名”为 **Product** ，并指定新的 **Product** 列， **Ham**, **Soda**, **Milk**, **Beer**和 **Chips** 列将逆向透视到该列。</span><span class="sxs-lookup"><span data-stu-id="3249c-128">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Key Value Column Name is **Product** and designates the new **Product** column into which the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns are unpivoted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3249c-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3249c-129">See Also</span></span>  
 <span data-ttu-id="3249c-130">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3249c-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="3249c-131">透视转换</span><span class="sxs-lookup"><span data-stu-id="3249c-131">Pivot Transformation</span></span>](data-flow/transformations/pivot-transformation.md)  
  
  
