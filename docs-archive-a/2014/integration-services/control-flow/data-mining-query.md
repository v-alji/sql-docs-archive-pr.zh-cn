---
title: 数据挖掘查询 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 657e4e173815fa25458e296f7eadb3d4d0696a02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587553"
---
# <a name="data-mining-query"></a><span data-ttu-id="7e3d5-102">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="7e3d5-102">Data Mining Query</span></span>
  <span data-ttu-id="7e3d5-103">设计窗格包含数据挖掘预测查询生成器，可用于生成数据挖掘预测查询。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-103">The design pane contains the data mining prediction query builder, which you can use to build data mining prediction queries.</span></span> <span data-ttu-id="7e3d5-104">您可以基于输入表设计预测查询，也可以设计单独预测查询。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-104">You can design either prediction queries based on input tables, or singleton prediction queries.</span></span> <span data-ttu-id="7e3d5-105">切换到结果视图可运行查询并查看结果。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-105">Switch to the result view to run the query and view the results.</span></span> <span data-ttu-id="7e3d5-106">查询视图将显示由预测查询生成器创建的数据挖掘扩展插件 (DMX) 查询。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-106">The query view displays the Data Mining Extensions (DMX) query created by the prediction query builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e3d5-107">选项</span><span class="sxs-lookup"><span data-stu-id="7e3d5-107">Options</span></span>  
 <span data-ttu-id="7e3d5-108">“切换视图”按钮</span><span class="sxs-lookup"><span data-stu-id="7e3d5-108">Switch view button</span></span>  
 <span data-ttu-id="7e3d5-109">单击图标可以在设计窗格和查询窗格之间切换。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-109">Click an icon to switch between the design and query pane.</span></span> <span data-ttu-id="7e3d5-110">默认情况下，设计窗格处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-110">By default, the design pane is open.</span></span>  
  
 <span data-ttu-id="7e3d5-111">要切换到设计窗格，请单击![设计图标](../media/ssis-designicon.gif "设计图标")图标。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-111">To switch to the design pane, click the ![Design icon](../media/ssis-designicon.gif "Design icon") icon.</span></span>  
  
 <span data-ttu-id="7e3d5-112">要切换到查询窗格，请单击 ![SQL 图标](../media/ssis-queryicon.gif "SQL 图标")。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-112">To switch to the query pane, click the ![SQL icon](../media/ssis-queryicon.gif "SQL icon") icon.</span></span>  
  
 <span data-ttu-id="7e3d5-113">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-113">**Mining Model**</span></span>  
 <span data-ttu-id="7e3d5-114">显示所选的挖掘模型，您希望利用该模型来进行预测。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-114">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="7e3d5-115">**选择模型**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-115">**Select Model**</span></span>  
 <span data-ttu-id="7e3d5-116">打开“选择挖掘模型”  对话框。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-116">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="7e3d5-117">**输入列**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-117">**Input Columns**</span></span>  
 <span data-ttu-id="7e3d5-118">显示用于生成预测的所选输入列。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-118">Displays the selected input columns used to generate the predictions.</span></span>  
  
 <span data-ttu-id="7e3d5-119">**数据源**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-119">**Source**</span></span>  
 <span data-ttu-id="7e3d5-120">从下拉列表中选择包含要用于列的字段的源。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-120">Select the source containing the field that you will use for the column from the dropdown list.</span></span> <span data-ttu-id="7e3d5-121">可以使用“挖掘模型”  表中所选的挖掘模型、“选择输入表”  表中所选的输入表、预测函数或自定义表达式。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-121">You can either use the mining model selected in the **Mining Model** table, the input table(s) selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="7e3d5-122">可以将列从包含挖掘模型的表和输入列中拖动到单元。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-122">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
 <span data-ttu-id="7e3d5-123">**字段**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-123">**Field**</span></span>  
 <span data-ttu-id="7e3d5-124">从派生自源表的列的列表中选择列。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-124">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="7e3d5-125">如果在“源”中选择了“预测函数”，则此单元将包含对所选挖掘模型可用的预测函数的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-125">If you selected **Prediction Function** in **Source**, this cell contains a drop-down list of the prediction functions available for the selected mining model.</span></span>  
  
 <span data-ttu-id="7e3d5-126">**Alias**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-126">**Alias**</span></span>  
 <span data-ttu-id="7e3d5-127">服务器返回的列的名称。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-127">The name of the column returned by the server.</span></span>  
  
 <span data-ttu-id="7e3d5-128">**显示**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-128">**Show**</span></span>  
 <span data-ttu-id="7e3d5-129">选择此项将返回列或只使用 WHERE 子句中的列。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-129">Select to return the column or to only use the column in the WHERE clause.</span></span>  
  
 <span data-ttu-id="7e3d5-130">**分组**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-130">**Group**</span></span>  
 <span data-ttu-id="7e3d5-131">与“和/或”  列一起使用，将表达式组合到一起。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-131">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="7e3d5-132">例如，(expr1 OR expr2) AND expr3。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-132">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="7e3d5-133">**和/或**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-133">**And/Or**</span></span>  
 <span data-ttu-id="7e3d5-134">用于创建逻辑查询。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-134">Use to create a logical query.</span></span> <span data-ttu-id="7e3d5-135">例如，(expr1 OR expr2) AND expr3。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-135">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="7e3d5-136">**条件/参数**</span><span class="sxs-lookup"><span data-stu-id="7e3d5-136">**Criteria/Argument**</span></span>  
 <span data-ttu-id="7e3d5-137">指定应用于该列的条件表达式或用户表达式。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-137">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="7e3d5-138">可以将列从包含挖掘模型的表和输入列中拖动到单元。</span><span class="sxs-lookup"><span data-stu-id="7e3d5-138">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3d5-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e3d5-139">See Also</span></span>  
 <span data-ttu-id="7e3d5-140">[数据挖掘查询接口](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span><span class="sxs-lookup"><span data-stu-id="7e3d5-140">[Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span></span>  
 [<span data-ttu-id="7e3d5-141">数据挖掘扩展插件 (DMX) 语句引用</span><span class="sxs-lookup"><span data-stu-id="7e3d5-141">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
