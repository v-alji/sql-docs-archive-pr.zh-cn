---
title: MDX 脚本编写基础 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f7638339d8fc366ee384d453f6df683f3bd41f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589310"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a><span data-ttu-id="ec60c-102">MDX 脚本编写基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ec60c-102">MDX Scripting Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="ec60c-103">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中，多维表达式 (MDX) 脚本由一个或多个 MDX 表达式或语句构成，这些表达式或语句使用计算结果填充多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ec60c-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.</span></span>  
  
 <span data-ttu-id="ec60c-104">MDX 脚本定义多维数据集的计算过程。</span><span class="sxs-lookup"><span data-stu-id="ec60c-104">An MDX script defines the calculation process for a cube.</span></span> <span data-ttu-id="ec60c-105">MDX 脚本也被视为多维数据集的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec60c-105">An MDX script is also considered part of the cube itself.</span></span> <span data-ttu-id="ec60c-106">因此，更改与多维数据集相关联的 MDX 脚本将会立即更改多维数据集的计算过程。</span><span class="sxs-lookup"><span data-stu-id="ec60c-106">Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.</span></span>  
  
 <span data-ttu-id="ec60c-107">要创建 MDX 脚本，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的“多维数据集设计器”。</span><span class="sxs-lookup"><span data-stu-id="ec60c-107">To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ec60c-108">有关详细信息，请参阅 [定义赋值和其他脚本命令](../define-assignments-and-other-script-commands.md) 和 [Microsoft SQL Server 2005 中的 MDX 脚本简介](https://go.microsoft.com/fwlink/?LinkId=81892)。</span><span class="sxs-lookup"><span data-stu-id="ec60c-108">For more information, see [Define Assignments and Other Script Commands](../define-assignments-and-other-script-commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span>  
  
 <span data-ttu-id="ec60c-109">有关与 MDX 查询和计算相关的性能问题，请参阅 [SQL Server Analysis Services 性能指南](https://go.microsoft.com/fwlink/p/?LinkId=399050)的“MDX 优化”部分。</span><span class="sxs-lookup"><span data-stu-id="ec60c-109">For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec60c-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="ec60c-110">In This Section</span></span>  
  
|<span data-ttu-id="ec60c-111">主题</span><span class="sxs-lookup"><span data-stu-id="ec60c-111">Topic</span></span>|<span data-ttu-id="ec60c-112">说明</span><span class="sxs-lookup"><span data-stu-id="ec60c-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ec60c-113">基本 MDX 脚本 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-113">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)|<span data-ttu-id="ec60c-114">详细介绍了基本 MDX 脚本（包括每个多维数据集中提供的默认 MDX 脚本），以及 MDX 脚本通常如何在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中的多维数据集内运行。</span><span class="sxs-lookup"><span data-stu-id="ec60c-114">Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="ec60c-115">管理作用域和上下文 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-115">Managing Scope and Context &#40;MDX&#41;</span></span>](managing-scope-and-context-mdx.md)|<span data-ttu-id="ec60c-116">介绍如何使用 [CALCULATE](/sql/mdx/mdx-scripting-calculate) 语句、 [SCOPE](/sql/mdx/mdx-scripting-scope) 语句以及 [This](/sql/mdx/this-mdx) 函数管理 MDX 脚本中的上下文和作用域。</span><span class="sxs-lookup"><span data-stu-id="ec60c-116">Describes how to use the [CALCULATE](/sql/mdx/mdx-scripting-calculate) statement, the [SCOPE](/sql/mdx/mdx-scripting-scope) statement, and the [This](/sql/mdx/this-mdx) function to manage context and scope within an MDX script.</span></span>|  
|[<span data-ttu-id="ec60c-117">使用变量和参数 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-117">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="ec60c-118">介绍如何在 MDX 脚本中使用变量和参数。</span><span class="sxs-lookup"><span data-stu-id="ec60c-118">Describes how to use variables and parameters in an MDX script.</span></span>|  
|[<span data-ttu-id="ec60c-119">错误处理 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-119">Error Handling &#40;MDX&#41;</span></span>](error-handling-mdx.md)|<span data-ttu-id="ec60c-120">介绍 MDX 脚本中的错误处理。</span><span class="sxs-lookup"><span data-stu-id="ec60c-120">Explains error handling within an MDX script.</span></span>|  
|[<span data-ttu-id="ec60c-121">支持的 MDX (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-121">Supported MDX &#40;MDX&#41;</span></span>](supported-mdx-mdx.md)|<span data-ttu-id="ec60c-122">提供 MDX 脚本中支持的 MDX 运算符、语句和函数的列表。</span><span class="sxs-lookup"><span data-stu-id="ec60c-122">Provides a list of supported MDX operators, statements, and functions within an MDX script.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec60c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec60c-123">See Also</span></span>  
 [<span data-ttu-id="ec60c-124">MDX 语言参考 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ec60c-124">MDX Language Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-language-reference-mdx)  
  
  
