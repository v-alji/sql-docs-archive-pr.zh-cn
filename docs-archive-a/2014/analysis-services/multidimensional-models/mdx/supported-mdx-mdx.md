---
title: 支持的 MDX (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], statements
- MDX [Analysis Services], functions
ms.assetid: 308bc0b3-4fd6-4435-972b-5e40d9e3c99b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e8df6a2aa6da6b88a07a2abdef99d6ea03d8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691955"
---
# <a name="supported-mdx-mdx"></a><span data-ttu-id="3d968-102">支持的 MDX (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-102">Supported MDX (MDX)</span></span>
  <span data-ttu-id="3d968-103">支持在多维表达式 (MDX) 脚本中使用下列语句和函数：</span><span class="sxs-lookup"><span data-stu-id="3d968-103">The following statements and functions are supported within Multidimensional Expressions (MDX) Script:</span></span>  
  
 [<span data-ttu-id="3d968-104">（注释）(MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-104">&#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="3d968-105">--（注释）(MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-105">-- &#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="3d968-106">注释 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-106">Comment &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="3d968-107">ALTER CUBE 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-107">ALTER CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-alter-cube)  
  
> [!NOTE]  
>  <span data-ttu-id="3d968-108">MDX 脚本仅支持更改默认成员。</span><span class="sxs-lookup"><span data-stu-id="3d968-108">Only altering the default member is supported in MDX Scripting.</span></span>  
  
 [<span data-ttu-id="3d968-109">CALCULATE 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-109">CALCULATE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
 [<span data-ttu-id="3d968-110">CASE 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-110">CASE Statement &#40;MDX&#41;</span></span>](/sql/mdx/case-statement-mdx)  
  
 [<span data-ttu-id="3d968-111">CREATE CELL CALCULATION 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-111">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
 [<span data-ttu-id="3d968-112">CREATE MEMBER 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-112">CREATE MEMBER Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-member)  
  
 [<span data-ttu-id="3d968-113">CREATE SET 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-113">CREATE SET Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-set)  
  
 [<span data-ttu-id="3d968-114">EXISTING 关键字 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-114">EXISTING Keyword &#40;MDX&#41;</span></span>](mdx-query-existing-keyword.md)  
  
 [<span data-ttu-id="3d968-115">FREEZE 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-115">FREEZE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
 [<span data-ttu-id="3d968-116">IF 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-116">IF Statement  &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-if)  
  
 [<span data-ttu-id="3d968-117">此 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-117">This &#40;MDX&#41;</span></span>](/sql/mdx/this-mdx)  
  
> [!NOTE]  
>  <span data-ttu-id="3d968-118">MDX 支持为下列单元属性赋值：`BACK_COLOR`、`FORE_COLOR`、`FORMAT_STRING`、`FONT_FLAGS`、`FONT_NAME` 和 `FONT_SIZE`。</span><span class="sxs-lookup"><span data-stu-id="3d968-118">MDX supports assignment to the following cell properties: `BACK_COLOR`, `FORE_COLOR`, `FORMAT_STRING`, `FONT_FLAGS`, `FONT_NAME`, and `FONT_SIZE`.</span></span> <span data-ttu-id="3d968-119">有关详细信息，请参阅[使用单元属性 (MDX)](mdx-cell-properties-using-cell-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3d968-119">For more information, see [Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md).</span></span> <span data-ttu-id="3d968-120">MDX 还支持为 `NON_EMPTY_BEHAVIOR` [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member)语句的属性赋值。</span><span class="sxs-lookup"><span data-stu-id="3d968-120">MDX also supports assignment to the `NON_EMPTY_BEHAVIOR` property of the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span>  
  
 [<span data-ttu-id="3d968-121">SCOPE 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-121">SCOPE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-scope)  
  
## <a name="see-also"></a><span data-ttu-id="3d968-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d968-122">See Also</span></span>  
 [<span data-ttu-id="3d968-123">基本 MDX 脚本 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3d968-123">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)  
  
  
