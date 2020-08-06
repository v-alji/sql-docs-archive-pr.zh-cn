---
title: 逆透视转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e605dc4827a885b5dc65fbb680cce8a434b89fd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589780"
---
# <a name="unpivot-transformation"></a><span data-ttu-id="cb137-102">逆透视转换</span><span class="sxs-lookup"><span data-stu-id="cb137-102">Unpivot Transformation</span></span>
  <span data-ttu-id="cb137-103">逆透视转换将来自单个记录中多个列的值扩展为单个列中具有同样值的多个记录，使得非规范的数据集成为较规范的版本。</span><span class="sxs-lookup"><span data-stu-id="cb137-103">The Unpivot transformation makes an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column.</span></span> <span data-ttu-id="cb137-104">例如，每个客户在列出客户名的数据集中各占一行，在该行的各列中显示购买的产品和数量。</span><span class="sxs-lookup"><span data-stu-id="cb137-104">For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row.</span></span> <span data-ttu-id="cb137-105">逆透视转换将数据集规范之后，客户购买的每种产品在该数据集中各占一行。</span><span class="sxs-lookup"><span data-stu-id="cb137-105">After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.</span></span>  
  
 <span data-ttu-id="cb137-106">下面的关系图显示对 Product 列逆透视数据之前的数据集。</span><span class="sxs-lookup"><span data-stu-id="cb137-106">The following diagram shows a data set before the data is unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="cb137-107">![逆透视后的数据集](../../media/mw-dts-18.gif "逆透视后的数据集")</span><span class="sxs-lookup"><span data-stu-id="cb137-107">![Dataset after it is unpivoted](../../media/mw-dts-18.gif "Dataset after it is unpivoted")</span></span>  
  
 <span data-ttu-id="cb137-108">下面的关系图显示对 Product 列逆透视数据之后的数据集。</span><span class="sxs-lookup"><span data-stu-id="cb137-108">The following diagram shows a data set after it has been unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="cb137-109">![逆透视前的数据集](../../media/mw-dts-17.gif "逆透视前的数据集")</span><span class="sxs-lookup"><span data-stu-id="cb137-109">![Dataset before it is unpivoted](../../media/mw-dts-17.gif "Dataset before it is unpivoted")</span></span>  
  
 <span data-ttu-id="cb137-110">在某些情况下，逆透视结果可能包含具有意外值的行。</span><span class="sxs-lookup"><span data-stu-id="cb137-110">Under some circumstances, the unpivot results may contain rows with unexpected values.</span></span> <span data-ttu-id="cb137-111">例如，如果关系图中显示的要逆透视的示例数据在 Fred 的所有 Qty 列中都具有空值，则输出将只包括 Fred 的一行，而非五行。</span><span class="sxs-lookup"><span data-stu-id="cb137-111">For example, if the sample data to unpivot shown in the diagram had null values in all the Qty columns for Fred, then the output would include only one row for Fred, not five.</span></span> <span data-ttu-id="cb137-112">Qty 列将为空或包含零，具体取决于列数据类型。</span><span class="sxs-lookup"><span data-stu-id="cb137-112">The Qty column would contain either null or zero, depending on the column data type.</span></span>  
  
## <a name="configuration-of-the-unpivot-transformation"></a><span data-ttu-id="cb137-113">配置逆透视转换</span><span class="sxs-lookup"><span data-stu-id="cb137-113">Configuration of the Unpivot Transformation</span></span>  
 <span data-ttu-id="cb137-114">逆透视转换包括 `PivotKeyValue` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="cb137-114">The Unpivot transformation includes the `PivotKeyValue` custom property.</span></span> <span data-ttu-id="cb137-115">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="cb137-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="cb137-116">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cb137-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="cb137-117">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="cb137-117">This transformation has one input and one output.</span></span> <span data-ttu-id="cb137-118">它没有错误输出。</span><span class="sxs-lookup"><span data-stu-id="cb137-118">It has no error output.</span></span>  
  
 <span data-ttu-id="cb137-119">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="cb137-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cb137-120">有关可以在 **“逆透视转换编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="cb137-120">For more information about the properties that you can set in the **Unpivot Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cb137-121">“逆透视转换编辑器”</span><span class="sxs-lookup"><span data-stu-id="cb137-121">Unpivot Transformation Editor</span></span>](../../unpivot-transformation-editor.md)  
  
 <span data-ttu-id="cb137-122">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="cb137-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cb137-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cb137-123">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="cb137-124">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="cb137-124">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="cb137-125">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cb137-125">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
