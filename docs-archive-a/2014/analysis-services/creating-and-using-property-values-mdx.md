---
title: " (MDX) 创建和使用属性值 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- property values [MDX]
- queries [MDX], property values
- MDX [Analysis Services], property values
- Multidimensional Expressions [Analysis Services], property values
ms.assetid: 0cafb269-03c8-4183-b6e9-220f071e4ef2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67eadc6bc2f0bf6f318f20ad42a5cc9e7a5afa5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587644"
---
# <a name="creating-and-using-property-values-mdx"></a><span data-ttu-id="11c80-102">创建和使用属性值 (MDX)</span><span class="sxs-lookup"><span data-stu-id="11c80-102">Creating and Using Property Values (MDX)</span></span>
  <span data-ttu-id="11c80-103">多维表达式 (MDX) 支持维度、级别、成员和单元的内部属性以及用户定义属性。</span><span class="sxs-lookup"><span data-stu-id="11c80-103">Multidimensional Expressions (MDX) supports intrinsic and user-defined properties for dimensions, levels, members, and cells.</span></span> <span data-ttu-id="11c80-104">内部属性为各个单元提供唯一的名称、标题甚至格式和字体大小。</span><span class="sxs-lookup"><span data-stu-id="11c80-104">The intrinsic properties provide unique names, captions, and even formatting and font sizes for individual cells.</span></span> <span data-ttu-id="11c80-105">而用户定义属性可以为成员提供几乎所有类型的其他特性。</span><span class="sxs-lookup"><span data-stu-id="11c80-105">User-defined properties, on the other hand, can provide almost any kind of additional attribute to members.</span></span>  
  
 <span data-ttu-id="11c80-106">存在下列级别的内部属性和用户定义属性：</span><span class="sxs-lookup"><span data-stu-id="11c80-106">Intrinsic and user-defined properties are available at the following levels:</span></span>  
  
 <span data-ttu-id="11c80-107">**成员属性**</span><span class="sxs-lookup"><span data-stu-id="11c80-107">**Member properties**</span></span>  
 <span data-ttu-id="11c80-108">成员属性提供有关各个元组中的每个成员的基本信息。</span><span class="sxs-lookup"><span data-stu-id="11c80-108">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="11c80-109">此基本信息包括成员名、父级别、子成员数目等等。</span><span class="sxs-lookup"><span data-stu-id="11c80-109">This basic information includes the member name, parent level, the number of children, and so on.</span></span>  
  
 <span data-ttu-id="11c80-110">有关成员属性及其用法的信息，请参阅[使用成员属性 (MDX)](multidimensional-models/mdx/mdx-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="11c80-110">For information about member properties and how to use them, see [Using Member Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
 <span data-ttu-id="11c80-111">**单元属性**</span><span class="sxs-lookup"><span data-stu-id="11c80-111">**Cell properties**</span></span>  
 <span data-ttu-id="11c80-112">单元属性包含有关多维数据源（如多维数据集）中单元的内容和格式的信息。</span><span class="sxs-lookup"><span data-stu-id="11c80-112">Cell properties contain information about the content and format of cells in a multidimensional data source, such as a cube.</span></span>  
  
 <span data-ttu-id="11c80-113">有关单元属性及其用法的详细信息，请参阅[使用单元属性 (MDX)](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="11c80-113">For more information about cell properties and how to use them, see [Using Cell Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c80-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11c80-114">See Also</span></span>  
 [<span data-ttu-id="11c80-115">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="11c80-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
