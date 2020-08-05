---
title: 设置同步作用域（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3efbb7774d5116c9b3a18457291434f2a05aac7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577278"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a><span data-ttu-id="f2322-102">设置同步作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f2322-102">Set Synchronization Scope (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f2322-103">指示器通过同步指定范围内指示器值的范围，提供数据值。</span><span class="sxs-lookup"><span data-stu-id="f2322-103">Indicators convey data values by synchronizing across the range of indicator values within a specified scope.</span></span> <span data-ttu-id="f2322-104">默认情况下，作用域是指示器的父容器，例如包含指示器的表或矩阵。</span><span class="sxs-lookup"><span data-stu-id="f2322-104">By default, the scope is the parent container of the indicator such as the table or matrix that contains the indicator.</span></span> <span data-ttu-id="f2322-105">您可以根据报表的布局，更改指示器的同步。</span><span class="sxs-lookup"><span data-stu-id="f2322-105">You can change the synchronization of the indicator depending on the layout of your report.</span></span> <span data-ttu-id="f2322-106">例如，如果表之类的数据区域具有某一行组，则您可以将该组指定为指示器作用域。</span><span class="sxs-lookup"><span data-stu-id="f2322-106">For example, if a data region such as a table has a row group, you can specify the group as the indicator scope.</span></span> <span data-ttu-id="f2322-107">指示器还可以忽略同步。</span><span class="sxs-lookup"><span data-stu-id="f2322-107">The indicator can also omit synchronization.</span></span>  
  
 <span data-ttu-id="f2322-108">可以通过使用表达式设置度量单位之类的选项。</span><span class="sxs-lookup"><span data-stu-id="f2322-108">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="f2322-109">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2322-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f2322-110">有关了解和设置报表作用域的常规信息，请参阅[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="f2322-110">For general information about understanding and setting scope within reports, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a><span data-ttu-id="f2322-111">更改指示器的同步作用域</span><span class="sxs-lookup"><span data-stu-id="f2322-111">To change the synchronization scope of an indicator</span></span>  
  
1.  <span data-ttu-id="f2322-112">右键单击要更改的指示器，然后单击 **“指示器属性”**。</span><span class="sxs-lookup"><span data-stu-id="f2322-112">Right click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="f2322-113">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="f2322-113">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="f2322-114">在 **“同步作用域”** 列表中，单击要应用的作用域。</span><span class="sxs-lookup"><span data-stu-id="f2322-114">In the **Synchronization scope** list, click the scope that you want to apply.</span></span>  
  
     <span data-ttu-id="f2322-115">从指示器中删除同步作用域的“(无)”选项始终可用  。</span><span class="sxs-lookup"><span data-stu-id="f2322-115">The **(None)** option, which removes synchronization scope from the indicator, is always available.</span></span> <span data-ttu-id="f2322-116">其他选项取决于您的报表布局。</span><span class="sxs-lookup"><span data-stu-id="f2322-116">Other options depend on the layout of your report.</span></span>  
  
     <span data-ttu-id="f2322-117">或者，单击“表达式”(fx) 按钮以编辑设置作用域的表达式   。</span><span class="sxs-lookup"><span data-stu-id="f2322-117">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the scope.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2322-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2322-118">See Also</span></span>  
 [<span data-ttu-id="f2322-119">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f2322-119">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
