---
title: 查看和保存预测查询的结果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6da4b515c4280969f665dba2cf5bee5281df0a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581014"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a><span data-ttu-id="32477-102">查看和保存预测查询的结果</span><span class="sxs-lookup"><span data-stu-id="32477-102">View and Save the Results of a Prediction Query</span></span>
  <span data-ttu-id="32477-103">使用预测查询生成器在中定义查询后 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，可通过切换到查询结果视图来运行查询并查看结果。</span><span class="sxs-lookup"><span data-stu-id="32477-103">After you have defined a query in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using Prediction Query Builder, you can run the query and view the results by switching to the query result view.</span></span>  
  
 <span data-ttu-id="32477-104">您可以将预测查询的结果保存到项目中定义的任何数据源中的表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="32477-104">You can save the results of a prediction query to a table in any data source that is defined in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="32477-105">可以创建新的表，也可以将查询结果保存到现有表中。</span><span class="sxs-lookup"><span data-stu-id="32477-105">You can either create a new table or save the query results to an existing table.</span></span> <span data-ttu-id="32477-106">如果将结果保存到现有表中，可以选择覆盖表中当前存储的数据；否则，查询结果将追加到表中现有数据的末尾。</span><span class="sxs-lookup"><span data-stu-id="32477-106">If you save the results to an existing table, you can choose to overwrite the data that is currently stored in the table; otherwise, the query results are appended to the existing data in the table.</span></span>  
  
### <a name="run-a-query-and-view-the-results"></a><span data-ttu-id="32477-107">运行查询并查看结果</span><span class="sxs-lookup"><span data-stu-id="32477-107">Run a query and view the results</span></span>  
  
1.  <span data-ttu-id="32477-108">在 **的数据挖掘设计器中，单击** “挖掘模型预测” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡工具栏上的 **“结果”** 。</span><span class="sxs-lookup"><span data-stu-id="32477-108">On the toolbar of the **Mining Model Prediction** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Result** .</span></span>  
  
     <span data-ttu-id="32477-109">此时将打开查询结果视图并运行查询。</span><span class="sxs-lookup"><span data-stu-id="32477-109">The query results view opens and runs the query.</span></span> <span data-ttu-id="32477-110">结果显示在查看器的网格中。</span><span class="sxs-lookup"><span data-stu-id="32477-110">The results are displayed in a grid in the viewer.</span></span>  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a><span data-ttu-id="32477-111">将预测查询的结果保存到表</span><span class="sxs-lookup"><span data-stu-id="32477-111">Save the results of a prediction query to a table</span></span>  
  
1.  <span data-ttu-id="32477-112">在数据挖掘设计器中，同 **“挖掘模型预测”** 选项卡工具栏上的 **“保存查询结果”**。</span><span class="sxs-lookup"><span data-stu-id="32477-112">On the toolbar of the **Mining Model Prediction** tab in Data Mining Designer, click **Save query result**.</span></span>  
  
     <span data-ttu-id="32477-113">此时将打开 **“保存数据挖掘查询结果”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="32477-113">The **Save Data Mining Query Result** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="32477-114">从 **“数据源”** 列表中选择数据源，或单击 **“新建”** 创建新的数据源。</span><span class="sxs-lookup"><span data-stu-id="32477-114">Select a data source from the **Data Source** list, or click **New** to create a new data source.</span></span>  
  
3.  <span data-ttu-id="32477-115">在 **“表名称”** 框中，输入表的名称。</span><span class="sxs-lookup"><span data-stu-id="32477-115">In the **Table Name** box, enter the name of the table.</span></span> <span data-ttu-id="32477-116">如果表已经存在，选择 **“如果已存在，则覆盖”** ，则可用查询结果替换表的内容。</span><span class="sxs-lookup"><span data-stu-id="32477-116">If the table already exists, select **Overwrite if exists** to replace the contents of the table with the query results.</span></span> <span data-ttu-id="32477-117">如果不希望覆盖表的内容，请不要选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="32477-117">If you do not want to overwrite the contents of the table, do not select this check box.</span></span> <span data-ttu-id="32477-118">新的查询结果将追加到表中现有数据的末尾。</span><span class="sxs-lookup"><span data-stu-id="32477-118">The new query results will be appended to the existing data in the table.</span></span>  
  
4.  <span data-ttu-id="32477-119">如果希望将表添加到数据源视图中，请从 **“添加到数据源视图”** 中选择数据源视图。</span><span class="sxs-lookup"><span data-stu-id="32477-119">Select a data source view from **Add to DSV** if you want to add the table to a data source view.</span></span>  
  
5.  <span data-ttu-id="32477-120">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="32477-120">Click **Save**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="32477-121">如果目标不支持分层行集，则可以向结果中添加 FALTTENED 关键字以另存为平面表。</span><span class="sxs-lookup"><span data-stu-id="32477-121">If the destination does not support hierarchical rowsets, you can add the FALTTENED keyword to the results to save as a flat table.</span></span>  
  
  
