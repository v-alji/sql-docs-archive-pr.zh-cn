---
title: 从模板创建单独预测查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80e853875cce349dd8623fab3c30f1ad09bfbf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578527"
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a><span data-ttu-id="1af08-102">通过模板创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="1af08-102">Create a Singleton Prediction Query from a Template</span></span>
  <span data-ttu-id="1af08-103">当您具有要用于预测的模型，但不希望将该模型映射到外部输入数据集或进行大容量预测时，单独查询很有用。</span><span class="sxs-lookup"><span data-stu-id="1af08-103">A singleton query is useful when you have a model that you want to use for prediction, but don't want to map it to an external input data set or make bulk predictions.</span></span> <span data-ttu-id="1af08-104">对于单独查询，您可以向模型提供一个或多个值，并且立即会看到预测值。</span><span class="sxs-lookup"><span data-stu-id="1af08-104">With a singleton query, you can provide a value or values to the model and instantly see the predicted value.</span></span>  
  
 <span data-ttu-id="1af08-105">例如，以下 DMX 查询表示对目标邮件模型 TM_Decision_Tree 的单独查询。</span><span class="sxs-lookup"><span data-stu-id="1af08-105">For example, the following DMX query represents a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="1af08-106">其后的过程介绍如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的模板资源管理器来快速创建此查询。</span><span class="sxs-lookup"><span data-stu-id="1af08-106">The procedure that follows describes how to use the Template Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to quickly create this query.</span></span>  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a><span data-ttu-id="1af08-107">在 SQL Server Management Studio 中打开 Analysis Services 模板</span><span class="sxs-lookup"><span data-stu-id="1af08-107">To open the Analysis Services templates in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="1af08-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“视图”  菜单上，单击“模板资源管理器” 。</span><span class="sxs-lookup"><span data-stu-id="1af08-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="1af08-109">单击多维数据集图标以打开 **Analysis Server**模板。</span><span class="sxs-lookup"><span data-stu-id="1af08-109">Click the cube icon to open the **Analysis Server**templates.</span></span>  
  
### <a name="to-open-a-prediction-query-template"></a><span data-ttu-id="1af08-110">打开预测查询模板</span><span class="sxs-lookup"><span data-stu-id="1af08-110">To open a prediction query template</span></span>  
  
1.  <span data-ttu-id="1af08-111">在“模板资源管理器”\*\*\*\* 的“Analysis Server”模板列表中，依次展开“DMX”\*\*\*\* 和“预测查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1af08-111">In **Template Explorer**, in the list of Analysis Server templates, expand **DMX**, and thenexpand **Prediction Queries**.</span></span>  
  
2.  <span data-ttu-id="1af08-112">双击“单独预测”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1af08-112">Double-click **Singleton Prediction**.</span></span>  
  
3.  <span data-ttu-id="1af08-113">在 **“连接到 Analysis Services”** 对话框中，键入服务器的名称，该服务器具有包含要查询的挖掘模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1af08-113">In the **Connect to Analysis Services** dialog box, type the name of the server that has the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining model to be queried.</span></span>  
  
4.  <span data-ttu-id="1af08-114">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="1af08-114">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="1af08-115">模板在指定的数据库中打开，同时打开的还有挖掘模型对象浏览器，其中包含数据挖掘函数和数据挖掘结构以及相关模型的列表。</span><span class="sxs-lookup"><span data-stu-id="1af08-115">The template opens in the specified database, together with a mining model Object Browser that contains data mining functions and a list of data mining structures and related models.</span></span>  
  
### <a name="to-customize-the-singleton-query-template"></a><span data-ttu-id="1af08-116">自定义单独查询模板</span><span class="sxs-lookup"><span data-stu-id="1af08-116">To customize the singleton query template</span></span>  
  
1.  <span data-ttu-id="1af08-117">在模板中，单击“可用数据库”\*\*\*\* 下拉列表，然后从列表中选择一个 Analysis Service 实例。</span><span class="sxs-lookup"><span data-stu-id="1af08-117">In the template, click the **Available Databases** drop-down list, and then select an instance of Analysis Service from the list.</span></span>  
  
2.  <span data-ttu-id="1af08-118">在 **“挖掘模型”** 列表中，选择您要查询的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1af08-118">In the **Mining Model** list, select the mining model that you want to query.</span></span>  
  
     <span data-ttu-id="1af08-119">挖掘模型中的列的列表显示在对象浏览器的 **“元数据”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="1af08-119">The list of columns in the mining model appears in the **Metadata** pane of the object browser.</span></span>  
  
3.  <span data-ttu-id="1af08-120">在 **“查询”** 菜单上，选择 **“指定模板参数的值”**。</span><span class="sxs-lookup"><span data-stu-id="1af08-120">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="1af08-121">在“选择列表”\*\*\*\* 行，键入 \* 以返回所有列，或键入以逗号分隔的列和表达式的列表以返回特定的列。</span><span class="sxs-lookup"><span data-stu-id="1af08-121">In the **select list** row, type \* to return all columns, or type a comma-delimited list of columns and expressions to return specific columns.</span></span>  
  
     <span data-ttu-id="1af08-122">如果您键入 \*，则会返回可预测列以及您在步骤 6 中为其提供新值的任何列。</span><span class="sxs-lookup"><span data-stu-id="1af08-122">If you type \*, the predictable column is returned, together with any columns for which you provide new values for in step 6.</span></span>  
  
     <span data-ttu-id="1af08-123">对于本主题开头部分显示的示例代码，“选择列表”\*\*\*\* 行设置为 \*。</span><span class="sxs-lookup"><span data-stu-id="1af08-123">For the sample code shown at the start of this topic, the **select list** row was set to \*.</span></span>  
  
5.  <span data-ttu-id="1af08-124">在 **“挖掘模型”** 行，键入显示在 **“对象资源管理器”** 中的挖掘模型列表中的挖掘模型的名称。</span><span class="sxs-lookup"><span data-stu-id="1af08-124">In the **mining model** row, type the name of the mining model from among the list of mining models that appear in **Object Explorer**.</span></span>  
  
     <span data-ttu-id="1af08-125">对于本主题开头部分显示的示例代码，"**挖掘模型**" 行设置为名称 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="1af08-125">For the sample code shown at the start of this topic, the **mining model** row was set to the name, `TM_Decision_Tree`.</span></span>  
  
6.  <span data-ttu-id="1af08-126">在 **“值”** 行中，键入您要对其进行预测的新数据值。</span><span class="sxs-lookup"><span data-stu-id="1af08-126">In the **value** row, type the new data value for which you want to make a prediction.</span></span>  
  
     <span data-ttu-id="1af08-127">对于本主题开头部分显示的示例代码，"**值**" 行设置为， `2` 以根据家里子女数预测自行车购买行为。</span><span class="sxs-lookup"><span data-stu-id="1af08-127">For the sample code shown at the start of this topic, the **value** row was set to `2` to predict bike buying behavior based on the number of children at home.</span></span>  
  
7.  <span data-ttu-id="1af08-128">在 **“列”** 行中，键入新数据映射到的挖掘模型中列的名称。</span><span class="sxs-lookup"><span data-stu-id="1af08-128">In the **column** row, type the name of the column in the mining model to which the new data should be mapped.</span></span>  
  
     <span data-ttu-id="1af08-129">对于本主题开头部分显示的示例代码，"**列**" 行设置为 `Number Children at Home` 。</span><span class="sxs-lookup"><span data-stu-id="1af08-129">For the sample code shown at the start of this topic, the **column** row was set to `Number Children at Home`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1af08-130">使用 **“指定模板参数的值”** 对话框时，不必将列名称用方括号括起来。</span><span class="sxs-lookup"><span data-stu-id="1af08-130">When you use the **Specify Values for Template Parameters** dialog box, you do not have to add square brackets around the column name.</span></span> <span data-ttu-id="1af08-131">括号会自动添加。</span><span class="sxs-lookup"><span data-stu-id="1af08-131">The brackets will automatically be added for you.</span></span>  
  
8.  <span data-ttu-id="1af08-132">将**输入别名**保留为 `t` 。</span><span class="sxs-lookup"><span data-stu-id="1af08-132">Leave the **input alias** as `t`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="1af08-133">在查询文本窗格中，查找指示语法错误的逗号和省略号下的红色波形曲线。</span><span class="sxs-lookup"><span data-stu-id="1af08-133">In the query text pane, find the red squiggle under the comma and ellipsis that indicates a syntax error.</span></span> <span data-ttu-id="1af08-134">删除省略号，并添加任何其他想要的查询条件。</span><span class="sxs-lookup"><span data-stu-id="1af08-134">Delete the ellipsis, and add any additional query condition that you want.</span></span> <span data-ttu-id="1af08-135">如果不需要添加任何其他条件，请删除逗号。</span><span class="sxs-lookup"><span data-stu-id="1af08-135">If you do not add any other conditions, delete the comma.</span></span>  
  
     <span data-ttu-id="1af08-136">对于本主题开头部分显示的示例代码，其他查询条件设置为 `'45' as [Age]`。</span><span class="sxs-lookup"><span data-stu-id="1af08-136">For the sample code shown at the start of this topic, the additional query condition was set to `'45' as [Age]`.</span></span>  
  
11. <span data-ttu-id="1af08-137">单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1af08-137">Click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af08-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1af08-138">See Also</span></span>  
 [<span data-ttu-id="1af08-139">创建预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="1af08-139">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
  
