---
title: "\"保存数据挖掘查询结果\" 对话框 (\"挖掘模型预测\" 视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0838c90f0797a0db9c8a66cd8c5f877aaecdad0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579117"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a><span data-ttu-id="71014-102">“保存数据挖掘查询结果”对话框（“挖掘模型预测”视图）</span><span class="sxs-lookup"><span data-stu-id="71014-102">Save Data Mining Query Result Dialog Box (Mining Model Prediction View)</span></span>
  <span data-ttu-id="71014-103">使用 **“保存数据挖掘查询结果”** 对话框，可将数据挖掘查询的结果保存到新表中。</span><span class="sxs-lookup"><span data-stu-id="71014-103">Use the **Save Data Mining Query Result** dialog box to save the results of a data mining query to a new table.</span></span>  
  
 <span data-ttu-id="71014-104">该新表将在数据源定义的数据库中创建。</span><span class="sxs-lookup"><span data-stu-id="71014-104">The new table will be created in the database defined by the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71014-105">选项</span><span class="sxs-lookup"><span data-stu-id="71014-105">Options</span></span>  
 <span data-ttu-id="71014-106">**数据源**</span><span class="sxs-lookup"><span data-stu-id="71014-106">**Data Source**</span></span>  
 <span data-ttu-id="71014-107">从当前项目中选择数据源。</span><span class="sxs-lookup"><span data-stu-id="71014-107">Select a data source from the current project.</span></span> <span data-ttu-id="71014-108">如果不存在正确的数据源，请单击 **“新建”** 以创建一个新的数据源。</span><span class="sxs-lookup"><span data-stu-id="71014-108">If the correct data source does not exist, click **New** to create a new data source.</span></span>  
  
 <span data-ttu-id="71014-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="71014-109">**New**</span></span>  
 <span data-ttu-id="71014-110">打开“数据源向导”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="71014-110">Opens the **Data Source Wizard**.</span></span>  
  
 <span data-ttu-id="71014-111">**表名**</span><span class="sxs-lookup"><span data-stu-id="71014-111">**Table Name**</span></span>  
 <span data-ttu-id="71014-112">键入新表的名称。</span><span class="sxs-lookup"><span data-stu-id="71014-112">Type a name for the new table.</span></span>  
  
 <span data-ttu-id="71014-113">**如果已存在，则覆盖**</span><span class="sxs-lookup"><span data-stu-id="71014-113">**Overwrite if exists**</span></span>  
 <span data-ttu-id="71014-114">若要覆盖具有相同名称的现有表，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="71014-114">Select this option if you want to overwrite an existing table with the same name.</span></span>  
  
 <span data-ttu-id="71014-115">如果下列任一条件成立，则需要覆盖现有表：</span><span class="sxs-lookup"><span data-stu-id="71014-115">Overwriting the existing table is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="71014-116">您已向预测查询添加了列。</span><span class="sxs-lookup"><span data-stu-id="71014-116">You added columns to the prediction query.</span></span>  
  
-   <span data-ttu-id="71014-117">您更改了预测查询中任何列的名称或数据类型。</span><span class="sxs-lookup"><span data-stu-id="71014-117">You changed the names or data types of any columns in the prediction query.</span></span>  
  
-   <span data-ttu-id="71014-118">您对目标表运行了 ALTER 语句。</span><span class="sxs-lookup"><span data-stu-id="71014-118">You ran an ALTER statement on the destination table.</span></span>  
  
 <span data-ttu-id="71014-119">如果多个列具有相同的名称（例如多个派生列可能具有默认的列名 **Expression**），你必须为具有重复名称的每个列创建一个别名。</span><span class="sxs-lookup"><span data-stu-id="71014-119">If multiple columns have the same name (for example, several derived columns might have the default column name **Expression**), you must create an alias for each column with a duplicate name.</span></span> <span data-ttu-id="71014-120">如果这些列没有唯一名称，则当设计器尝试将结果保存到 SQL Server 时将出错，因为表中的列必须要有唯一名称。</span><span class="sxs-lookup"><span data-stu-id="71014-120">If the columns do not have unique names, an error will be raised when the designer tries to save the results to SQL Server, because columns in a table must have unique names.</span></span>  
  
 <span data-ttu-id="71014-121">**添加到数据源视图**</span><span class="sxs-lookup"><span data-stu-id="71014-121">**Add to DSV**</span></span>  
 <span data-ttu-id="71014-122">（可选）如果希望将表添加到现有数据源中，请选择项目中包含的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="71014-122">(Optional) Select a data source view contained in the project if you want to add the table to an existing data source.</span></span>  
  
 <span data-ttu-id="71014-123">如果您想要在同一数据源中保留模型的所有相关表（如定型数据、预测源数据和查询结果），此选项很有用。</span><span class="sxs-lookup"><span data-stu-id="71014-123">This option is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71014-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71014-124">See Also</span></span>  
 <span data-ttu-id="71014-125">[&#40;数据挖掘的预测查询生成器&#41;](prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="71014-125">[Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md) </span></span>  
 <span data-ttu-id="71014-126">[数据挖掘查询接口](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="71014-126">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="71014-127">数据挖掘扩展插件 (DMX) 语句引用</span><span class="sxs-lookup"><span data-stu-id="71014-127">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
