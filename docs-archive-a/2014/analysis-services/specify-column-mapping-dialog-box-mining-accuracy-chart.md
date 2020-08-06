---
title: "\"指定列映射\" 对话框 (挖掘准确性图表) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ede835567f678f4152b3d1944f3c2c7160c6837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589264"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="d5554-102">“指定列映射”对话框（挖掘准确性图表）</span><span class="sxs-lookup"><span data-stu-id="d5554-102">Specify Column Mapping Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="d5554-103">可以使用 **“指定列映射”** 选项卡，从外部数据源中选择表以及将列映射到数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d5554-103">Use the **Specify Column Mapping** tab to select tables from an external data source and map the columns to a data mining model.</span></span> <span data-ttu-id="d5554-104">随后即可使用外部数据测试挖掘模型的准确性并在准确性图表中显示结果。</span><span class="sxs-lookup"><span data-stu-id="d5554-104">You can then use the external data to test the accuracy of a mining model and displays the results in the accuracy chart.</span></span>  
  
 <span data-ttu-id="d5554-105">**有关详细信息，请参阅** [测试和验证（数据挖掘）](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="d5554-105">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="d5554-106">选项</span><span class="sxs-lookup"><span data-stu-id="d5554-106">Options</span></span>  
 <span data-ttu-id="d5554-107">**挖掘结构**</span><span class="sxs-lookup"><span data-stu-id="d5554-107">**Mining Structure**</span></span>  
 <span data-ttu-id="d5554-108">显示包含要测试的模型的所选挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="d5554-108">Displays the selected mining structure that contains the model that you will test.</span></span>  
  
 <span data-ttu-id="d5554-109">**选择结构**</span><span class="sxs-lookup"><span data-stu-id="d5554-109">**Select Structure**</span></span>  
 <span data-ttu-id="d5554-110">单击此项将打开“选择挖掘结构”\*\*\*\* 对话框，在其中可选择不同的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="d5554-110">Click to open the **Select Mining Structure** dialog box and select a different mining structure.</span></span>  
  
 <span data-ttu-id="d5554-111">**选择输入表**</span><span class="sxs-lookup"><span data-stu-id="d5554-111">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="d5554-112">显示用于生成提升图的所选输入表。</span><span class="sxs-lookup"><span data-stu-id="d5554-112">Displays the selected input tables that are used to generate the lift chart.</span></span> <span data-ttu-id="d5554-113">选择包含将用于测试模型准确性的测试数据的表。</span><span class="sxs-lookup"><span data-stu-id="d5554-113">Select the table that contains the test data that you will use to test the accuracy of the models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5554-114">如果该窗格中未包含任何表，请单击“选择事例表”\*\*\*\* 以从数据源视图中添加表。</span><span class="sxs-lookup"><span data-stu-id="d5554-114">If the pane does not contain any tables, click **Select Case Table** to add tables from a data source view.</span></span>  
  
 <span data-ttu-id="d5554-115">**删除表**</span><span class="sxs-lookup"><span data-stu-id="d5554-115">**Remove Table**</span></span>  
 <span data-ttu-id="d5554-116">删除所选表。</span><span class="sxs-lookup"><span data-stu-id="d5554-116">Removes the selected table.</span></span> <span data-ttu-id="d5554-117">如果未选择表或者 **“选择输入表”** 列表中未显示表，则禁用此按钮。</span><span class="sxs-lookup"><span data-stu-id="d5554-117">This button is disabled if a table has not been selected or if no tables are displayed in the **Select Input Tables** list.</span></span>  
  
 <span data-ttu-id="d5554-118">**选择事例表**</span><span class="sxs-lookup"><span data-stu-id="d5554-118">**Select Case Table**</span></span>  
 <span data-ttu-id="d5554-119">单击此项将打开“选择表”\*\*\*\* 对话框，在其中可选择数据源视图。</span><span class="sxs-lookup"><span data-stu-id="d5554-119">Click to open the **Select Table** dialog box and select a data source view.</span></span>  
  
 <span data-ttu-id="d5554-120">**注意** 只有在尚未选择事例表时，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="d5554-120">**Note** This button appears only if a case table has not been selected.</span></span> <span data-ttu-id="d5554-121">若要启用该按钮以便可以选择其他事例表，请选择所有现有表并单击 **“删除表”**，以清除该列表。</span><span class="sxs-lookup"><span data-stu-id="d5554-121">To enable the button so that you can select a different case table, clear the list by selecting all existing tables and then clicking **Remove Table**.</span></span>  
  
 <span data-ttu-id="d5554-122">**选择嵌套表**</span><span class="sxs-lookup"><span data-stu-id="d5554-122">**Select Nested Table**</span></span>  
 <span data-ttu-id="d5554-123">打开“选择表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="d5554-123">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="d5554-124">只有在已选择事例表的情况下，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="d5554-124">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="d5554-125">如果关联的挖掘结构不包含嵌套表，则禁用此按钮。</span><span class="sxs-lookup"><span data-stu-id="d5554-125">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="d5554-126">**修改联接**</span><span class="sxs-lookup"><span data-stu-id="d5554-126">**Modify Join**</span></span>  
 <span data-ttu-id="d5554-127">打开“指定嵌套联接”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="d5554-127">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="d5554-128">只有在已选择嵌套表的情况下，此按钮才处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d5554-128">This button is active only if the nested table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5554-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5554-129">See Also</span></span>  
 <span data-ttu-id="d5554-130">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d5554-130">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="d5554-131">挖掘准确性图表设计器 &#40;数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="d5554-131">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
