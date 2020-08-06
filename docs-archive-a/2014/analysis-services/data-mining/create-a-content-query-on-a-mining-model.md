---
title: 对挖掘模型创建内容查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: a0ce837a-89ed-46cf-9ce1-801ccb75fa04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26af1100d6ba80185c1cc4de18548df0e387824c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682450"
---
# <a name="create-a-content-query-on-a-mining-model"></a><span data-ttu-id="98262-102">针对挖掘模型创建内容查询</span><span class="sxs-lookup"><span data-stu-id="98262-102">Create a Content Query on a Mining Model</span></span>
  <span data-ttu-id="98262-103">使用 AMO 或 XML/A 可以采用编程方式查询挖掘模型内容，但是使用 DMX 创建查询更简单。</span><span class="sxs-lookup"><span data-stu-id="98262-103">You can query the mining model content programmatically by using AMO or XML/A, but it is easier to create queries by using DMX.</span></span> <span data-ttu-id="98262-104">您还可以通过建立与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的连接并使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的 DMV 创建查询，来针对数据挖掘架构行集创建查询。</span><span class="sxs-lookup"><span data-stu-id="98262-104">You can also create queries against the data mining schema rowsets by establishing a connection to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and creating a query using the DMVs provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="98262-105">下面的过程介绍如何使用 DMX 针对挖掘模型创建查询以及如何查询数据挖掘架构行集。</span><span class="sxs-lookup"><span data-stu-id="98262-105">The following procedures demonstrate how to create queries against a mining model by using DMX, and how to query the data mining schema rowsets.</span></span>  
  
 <span data-ttu-id="98262-106">有关如何使用 XML/A 创建类似查询的示例，请参阅 [使用 XMLA 创建数据挖掘查询](create-a-data-mining-query-by-using-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="98262-106">For an example of how to create a similar query by using XML/A, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a><span data-ttu-id="98262-107">使用 DMX 查询数据挖掘模型的内容</span><span class="sxs-lookup"><span data-stu-id="98262-107">Querying Data Mining Model Content by Using DMX</span></span>  
  
#### <a name="to-create-a-dmx-model-content-query"></a><span data-ttu-id="98262-108">创建 DMX 模型内容查询</span><span class="sxs-lookup"><span data-stu-id="98262-108">To create a DMX model content query</span></span>  
  
1.  <span data-ttu-id="98262-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“视图”  菜单上，单击“模板资源管理器” 。</span><span class="sxs-lookup"><span data-stu-id="98262-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="98262-110">在 **“模板资源管理器”** 窗格中，单击四方体图标，以更改列表并显示 Analysis Services 模板。</span><span class="sxs-lookup"><span data-stu-id="98262-110">In the **Template Explorer** pane, click the cube icon to change the list and display Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="98262-111">在模板类别列表中，展开“DMX”，再展开“模型内容”，然后双击“内容查询”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98262-111">In the list of template categories, expand **DMX**, expand **Model Content**, and double-click **Content Query**.</span></span>  
  
4.  <span data-ttu-id="98262-112">在 **“连接到 Analysis Services”** 对话框中，选择包含要查询的挖掘模型的实例，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="98262-112">In the **Connect to Analysis Services** dialog box, select the instance that contains the mining model you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="98262-113">此时将在相应代码编辑器中打开 **“内容查询”** 模板。</span><span class="sxs-lookup"><span data-stu-id="98262-113">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="98262-114">元数据窗格列出了当前数据库中的可用模型。</span><span class="sxs-lookup"><span data-stu-id="98262-114">The metadata pane lists the models that are available in the current database.</span></span> <span data-ttu-id="98262-115">若要更改数据库，请从 **“可用数据库”** 列表中选择不同的数据库。</span><span class="sxs-lookup"><span data-stu-id="98262-115">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
5.  <span data-ttu-id="98262-116">在 [] 行中输入挖掘模型的名称 `FROM` *\<mining model, name, MyModel>* `.CONTENT` 。</span><span class="sxs-lookup"><span data-stu-id="98262-116">Enter the name of a mining model in the line, `FROM` [*\<mining model, name, MyModel>*]`.CONTENT`.</span></span> <span data-ttu-id="98262-117">如果挖掘模型的名称包含空格，则必须用方括号将该名称括起来。</span><span class="sxs-lookup"><span data-stu-id="98262-117">If the mining model name contains spaces, you must enclose the name in brackets.</span></span>  
  
     <span data-ttu-id="98262-118">如果不希望键入名称，则可以在 **对象资源管理器** 中选择某个挖掘模型，并将其拖放到模板中。</span><span class="sxs-lookup"><span data-stu-id="98262-118">If you don't want to type the name, you can select a mining model in **Object Explorer** and drag it into the template.</span></span>  
  
6.  <span data-ttu-id="98262-119">在行中 `SELECT` *\<select list, expr list, \*>* ，键入挖掘模型内容架构行集中的列的名称。</span><span class="sxs-lookup"><span data-stu-id="98262-119">In the line, `SELECT`*\<select list, expr list, \*>*, type the names of columns in the mining model content schema rowset.</span></span>  
  
     <span data-ttu-id="98262-120">若要查看可在挖掘模型内容查询中返回的列的列表，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)提供的 DMV 创建查询，来针对数据挖掘架构行集创建查询。</span><span class="sxs-lookup"><span data-stu-id="98262-120">To view a list of columns that you can return in mining model content queries, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
7.  <span data-ttu-id="98262-121">或者，您也可以在模板的 WHERE 子句中键入条件，以将返回的行限制为特定的节点或值。</span><span class="sxs-lookup"><span data-stu-id="98262-121">Optionally, type a condition in the WHERE clause of the template to restrict the rows returned to specific nodes or values.</span></span>  
  
8.  <span data-ttu-id="98262-122">单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="98262-122">Click **Execute**.</span></span>  
  
## <a name="querying-the-data-mining-schema-rowsets"></a><span data-ttu-id="98262-123">查询数据挖掘架构行集</span><span class="sxs-lookup"><span data-stu-id="98262-123">Querying the Data Mining Schema Rowsets</span></span>  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a><span data-ttu-id="98262-124">对数据挖掘架构行集创建查询</span><span class="sxs-lookup"><span data-stu-id="98262-124">To create a query against the data mining schema rowset</span></span>  
  
1.  <span data-ttu-id="98262-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **“新建查询”** 工具栏中，单击 **“Analysis Services DMX 查询”** 或 **“Analysis Services MDX 查询”**。</span><span class="sxs-lookup"><span data-stu-id="98262-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **New Query** toolbar, click **Analysis Services DMX Query**, or **Analysis Services MDX query**.</span></span>  
  
2.  <span data-ttu-id="98262-126">在 **“连接到 Analysis Services”** 对话框中，选择包含要查询的对象的实例，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="98262-126">In the **Connect to Analysis Services** dialog box, select the instance that contains the objects you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="98262-127">此时将在相应代码编辑器中打开 **“内容查询”** 模板。</span><span class="sxs-lookup"><span data-stu-id="98262-127">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="98262-128">元数据窗格列出了当前数据库中的可用对象。</span><span class="sxs-lookup"><span data-stu-id="98262-128">The metadata pane lists the objects that are available in the current database.</span></span> <span data-ttu-id="98262-129">若要更改数据库，请从 **“可用数据库”** 列表中选择不同的数据库。</span><span class="sxs-lookup"><span data-stu-id="98262-129">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
3.  <span data-ttu-id="98262-130">在查询编辑器中，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="98262-130">In the query editor, type the following:</span></span>  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  <span data-ttu-id="98262-131">单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="98262-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="98262-132">“结果”窗格将显示模型的内容。</span><span class="sxs-lookup"><span data-stu-id="98262-132">The Results pane displays the contents of the model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98262-133">若要查看当前实例上可查询的所有架构行集的列表，请使用以下查询： `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS。</span><span class="sxs-lookup"><span data-stu-id="98262-133">To view a list of all the schema rowsets that you can query on the current instance, use this query: `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS.</span></span> <span data-ttu-id="98262-134">或者，若要查看特定于数据挖掘的架构行集的列表，请参阅 [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)。</span><span class="sxs-lookup"><span data-stu-id="98262-134">Or, for a list of schema rowsets specific to data mining, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98262-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98262-135">See Also</span></span>  
 <span data-ttu-id="98262-136">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="98262-136">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="98262-137">Data Mining Schema Rowsets</span><span class="sxs-lookup"><span data-stu-id="98262-137">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
