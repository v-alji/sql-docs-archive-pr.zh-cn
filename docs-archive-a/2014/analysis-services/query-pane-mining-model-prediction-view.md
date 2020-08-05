---
title: 查询窗格 (挖掘模型预测视图) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e17a27190891ea9e00be21d5013d0767d61ac148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580440"
---
# <a name="query-pane-mining-model-prediction-view"></a><span data-ttu-id="aed10-102">“查询”窗格（“挖掘模型预测”视图）</span><span class="sxs-lookup"><span data-stu-id="aed10-102">Query Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="aed10-103">“查询”\*\*\*\* 窗格显示预测查询生成器创建的数据挖掘表达式 (DMX) 语句。</span><span class="sxs-lookup"><span data-stu-id="aed10-103">The **Query** pane displays the Data Mining Expressions (DMX) statements created by Prediction Query Builder.</span></span> <span data-ttu-id="aed10-104">您可以修改这些语句，再单击 **“切换到查询结果视图”** 按钮以返回结果。</span><span class="sxs-lookup"><span data-stu-id="aed10-104">You can modify the statements and then click the **Switch to query result view** button to return the results.</span></span> <span data-ttu-id="aed10-105">如果切换回 **“设计”** 视图，则对语句所做的所有更改都将丢失。</span><span class="sxs-lookup"><span data-stu-id="aed10-105">If you switch back to the **Design** view, any changes you made to the statement will be lost.</span></span>  
  
 <span data-ttu-id="aed10-106">**有关详细信息，请参阅** [数据挖掘扩展插件（数据操作语句）](/sql/dmx/dmx-statements-data-manipulation)、[在 SQL Server Management Studio 中创建一个 DMX 查询](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="aed10-106">**For More Information:** [Data Mining Extensions &#40;DMX&#41; Data Manipulation Statements](/sql/dmx/dmx-statements-data-manipulation), [Create a DMX Query in SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="aed10-107">选项</span><span class="sxs-lookup"><span data-stu-id="aed10-107">Options</span></span>  
 <span data-ttu-id="aed10-108">**切换到查询结果视图**</span><span class="sxs-lookup"><span data-stu-id="aed10-108">**Switch to query result view**</span></span>  
 <span data-ttu-id="aed10-109">单击此项可以在“设计”\*\*\*\*、“查询”\*\*\*\* 和“结果”\*\*\*\* 窗格之间切换。</span><span class="sxs-lookup"><span data-stu-id="aed10-109">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="aed10-110">切换到 **“结果”** 窗格可以运行查询。</span><span class="sxs-lookup"><span data-stu-id="aed10-110">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="aed10-111">**保存查询结果**</span><span class="sxs-lookup"><span data-stu-id="aed10-111">**Save the query result**</span></span>  
 <span data-ttu-id="aed10-112">打开“保存数据挖掘查询结果”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="aed10-112">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="aed10-113">**单独查询**</span><span class="sxs-lookup"><span data-stu-id="aed10-113">**Singleton query**</span></span>  
 <span data-ttu-id="aed10-114">使用此选项，您可以创建单独查询，在其中您可以直接为查询提供输入数据，而无需提供对输入值的表的引用。</span><span class="sxs-lookup"><span data-stu-id="aed10-114">Lets you create a singleton query, in which you provide the input data directly in your query instead of providing a reference to a table of input values.</span></span> <span data-ttu-id="aed10-115">“选择输入表”\*\*\*\* 表由“单独查询输入”\*\*\*\* 表替换。</span><span class="sxs-lookup"><span data-stu-id="aed10-115">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span> <span data-ttu-id="aed10-116">如果切换到单独查询，则当前的预测查询将会丢失。</span><span class="sxs-lookup"><span data-stu-id="aed10-116">The current prediction query will be lost if you switch to a singleton query.</span></span>  
  
 <span data-ttu-id="aed10-117">**刷新查询结果**</span><span class="sxs-lookup"><span data-stu-id="aed10-117">**Refresh query results**</span></span>  
 <span data-ttu-id="aed10-118">重新处理预测查询。</span><span class="sxs-lookup"><span data-stu-id="aed10-118">Reprocesses the prediction query.</span></span> <span data-ttu-id="aed10-119">此选项仅在 **“结果”** 窗格中启用。</span><span class="sxs-lookup"><span data-stu-id="aed10-119">This is enabled only in the **Result** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed10-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aed10-120">See Also</span></span>  
 <span data-ttu-id="aed10-121">[数据挖掘查询接口](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aed10-121">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 <span data-ttu-id="aed10-122">[数据挖掘扩展插件 &#40;DMX&#41; 语句参考](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="aed10-122">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 [<span data-ttu-id="aed10-123">预测查询生成器（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="aed10-123">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
