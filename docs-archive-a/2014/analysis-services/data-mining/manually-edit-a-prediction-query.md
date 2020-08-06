---
title: 手动编辑预测查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e887e935dafcd2428859fd959cb7bc64650c660d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591652"
---
# <a name="manually-edit-a-prediction-query"></a><span data-ttu-id="f2bfb-102">手动编辑预测查询</span><span class="sxs-lookup"><span data-stu-id="f2bfb-102">Manually Edit a Prediction Query</span></span>
  <span data-ttu-id="f2bfb-103">在使用预测查询生成器设计查询后，可通过在数据挖掘设计器的 **“挖掘模型预测”** 选项卡上切换到“查询文本”视图来修改查询。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-103">After you have designed a query by using the Prediction Query Builder, you can modify the query by switching to Query Text view on the **Mining Model Prediction** tab of Data Mining Designer.</span></span> <span data-ttu-id="f2bfb-104">屏幕的底部会出现文本编辑器，显示查询生成器创建的查询。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-104">A text editor appears at the bottom of the screen to display the query that the query builder created.</span></span>  
  
 <span data-ttu-id="f2bfb-105">切换到“查询文本”视图对向查询中添加内容非常有用。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-105">Switching to Query Text view is useful for making additions to the query.</span></span> <span data-ttu-id="f2bfb-106">例如，可以添加 WHERE 子句或 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-106">For example, you can add a WHERE clause or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="f2bfb-107">使用预测查询生成器中的网格可插入对象和列的名称，并设置单个预测函数的语法，然后切换到手动编辑模式以更改参数值。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-107">Use the grid in the Prediction Query Builder to insert the names of objects and columns and set up the syntax for individual prediction functions, and then switch to manual editing mode to change parameter values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2bfb-108">如果从“查询文本”视图切换回“设计”视图，则会丢失在“查询文本”视图中所做的任何更改\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-108">If you switch back to **Design** view from **Query Text** view, any changes that you made in **Query Text** view will be lost.</span></span>  
  
### <a name="modify-a-query"></a><span data-ttu-id="f2bfb-109">修改查询</span><span class="sxs-lookup"><span data-stu-id="f2bfb-109">Modify a query</span></span>  
  
1.  <span data-ttu-id="f2bfb-110">在 **中数据挖掘设计器的** “挖掘模型预测” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡上，单击 **SQL**。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-110">On the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **SQL**.</span></span>  
  
     <span data-ttu-id="f2bfb-111">屏幕底部的网格将替换为包含查询的文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-111">The grid at the bottom of the screen is replaced by a text editor that contains the query.</span></span> <span data-ttu-id="f2bfb-112">可以在此编辑器中键入对查询的更改。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-112">You can type changes to the query in this editor.</span></span>  
  
2.  <span data-ttu-id="f2bfb-113">若要运行查询，请在 **“挖掘模型”** 菜单上选择 **“结果”**，或者单击此按钮切换到查询结果。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-113">To run the query, on the **Mining Model** menu, select **Result**, or click the button to switch to query results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f2bfb-114">如果您创建的查询无效，则“结果”窗口将不会显示错误，也不会显示任何结果。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-114">If the query that you have created is invalid, the Results window does not display an error and does not display any results.</span></span> <span data-ttu-id="f2bfb-115">单击 **“设计”** 按钮，或者从 **“挖掘模型”** 菜单中选择 **“设计”** 或 **“查询”** 以解决问题并再次运行查询。</span><span class="sxs-lookup"><span data-stu-id="f2bfb-115">Click the **Design** button, or select **Design** or **Query** from the **Mining Model** menu to correct the problem and run the query again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2bfb-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2bfb-116">See Also</span></span>  
 <span data-ttu-id="f2bfb-117">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="f2bfb-117">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="f2bfb-118">[&#40;数据挖掘的预测查询生成器&#41;](../prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f2bfb-118">[Prediction Query Builder &#40;Data Mining&#41;](../prediction-query-builder-data-mining.md) </span></span>  
 [<span data-ttu-id="f2bfb-119">第 6 课：创建和使用预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="f2bfb-119">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
