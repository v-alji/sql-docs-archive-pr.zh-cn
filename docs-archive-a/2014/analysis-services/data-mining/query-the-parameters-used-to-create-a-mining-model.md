---
title: 查询用于创建挖掘模型的参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a3802a0d70579f613accbe6abd310da909751b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690237"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a><span data-ttu-id="5021c-102">查询用于创建挖掘模型的参数</span><span class="sxs-lookup"><span data-stu-id="5021c-102">Query the Parameters Used to Create a Mining Model</span></span>
  <span data-ttu-id="5021c-103">挖掘模型的构成不仅受到定型事例的影响，还会受到在创建模型时设置的参数的影响。</span><span class="sxs-lookup"><span data-stu-id="5021c-103">The composition of a mining model is affected not only by the training cases, but by the parameters that were set when the model was created.</span></span> <span data-ttu-id="5021c-104">因此，检索现有模型的参数设置以便更好地理解模型的行为可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="5021c-104">Therefore, you might find it useful to retrieve the parameter settings of an existing model to better understand the behavior of the model.</span></span> <span data-ttu-id="5021c-105">在归档该模型的特定版本时检索参数可能也很有用。</span><span class="sxs-lookup"><span data-stu-id="5021c-105">Retrieving parameters is also useful when documenting a particular version of that model.</span></span>  
  
 <span data-ttu-id="5021c-106">若要查找在创建模型时使用的参数，应针对某个挖掘模型架构行集创建查询。</span><span class="sxs-lookup"><span data-stu-id="5021c-106">To find the parameters that were used when the model was created, you create a query against one of the mining model schema rowsets.</span></span> <span data-ttu-id="5021c-107">在 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]中，这些架构行集将作为可使用 Transact-SQL 语法轻松查询的一组系统视图公开。</span><span class="sxs-lookup"><span data-stu-id="5021c-107">In [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], these schema rowsets are exposed as a set of system views that you can query easily by using Transact-SQL syntax.</span></span> <span data-ttu-id="5021c-108">下面的过程介绍如何创建返回用于创建指定挖掘模型的参数的查询。</span><span class="sxs-lookup"><span data-stu-id="5021c-108">This procedure describes how to create a query that returns the parameters that were used to create the specified mining model.</span></span>  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a><span data-ttu-id="5021c-109">打开架构行集查询的“查询”窗口</span><span class="sxs-lookup"><span data-stu-id="5021c-109">To open a Query window for a schema rowset query</span></span>  
  
1.  <span data-ttu-id="5021c-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开包含要查询的模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="5021c-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the model you want to query.</span></span>  
  
2.  <span data-ttu-id="5021c-111">右键单击实例名称，选择“新建查询”\*\*\*\*，然后选择“DMX”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5021c-111">Right-click the instance name, select **New Query**, and then select **DMX**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5021c-112"> 还可以通过使用 **MDX** 模板来针对数据挖掘模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="5021c-112">You can also create a query against a data mining model by using the **MDX** template.</span></span>  
  
3.  <span data-ttu-id="5021c-113">如果实例包含多个数据库，应从工具栏中的 **“可用数据库”** 列表中选择包含要查询的模型的数据库。</span><span class="sxs-lookup"><span data-stu-id="5021c-113">If the instance contains multiple databases, select the database that contains the model you want to query from the **Available Databases** list in the toolbar.</span></span>  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a><span data-ttu-id="5021c-114">从现有挖掘模型中返回模型参数</span><span class="sxs-lookup"><span data-stu-id="5021c-114">To return model parameters for an existing mining model</span></span>  
  
1.  <span data-ttu-id="5021c-115">在 DMX 查询窗格中，键入或粘贴以下文本：</span><span class="sxs-lookup"><span data-stu-id="5021c-115">In the DMX query pane, type or paste the following text:</span></span>  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  <span data-ttu-id="5021c-116">在对象资源管理器中，选择需要的挖掘模型，然后将它拖到 DMX 查询窗格中的单引号之间。</span><span class="sxs-lookup"><span data-stu-id="5021c-116">In Object Explorer, select the mining model you want, and then drag it into the DMX Query pane, between the single quotation marks.</span></span>  
  
3.  <span data-ttu-id="5021c-117">按 F5，或单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="5021c-117">Press F5, or click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5021c-118">示例</span><span class="sxs-lookup"><span data-stu-id="5021c-118">Example</span></span>  
 <span data-ttu-id="5021c-119">下面的代码返回用于创建在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中生成的挖掘模型的参数列表。</span><span class="sxs-lookup"><span data-stu-id="5021c-119">The following code returns a list of the parameters that were used to create the mining model that you build in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="5021c-120">这些参数包括服务器上的提供程序中可用的挖掘服务所使用的任何默认参数的显式值。</span><span class="sxs-lookup"><span data-stu-id="5021c-120">These parameters include the explicit values for any defaults used by the mining services available from providers on the server.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 <span data-ttu-id="5021c-121">代码示例返回聚类分析模型的下列参数：</span><span class="sxs-lookup"><span data-stu-id="5021c-121">The code example returns the following parameters for the clustering model:</span></span>  
  
 <span data-ttu-id="5021c-122">示例结果：</span><span class="sxs-lookup"><span data-stu-id="5021c-122">eExample Results:</span></span>  
  
 <span data-ttu-id="5021c-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5021c-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="5021c-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="5021c-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5021c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5021c-125">See Also</span></span>  
 <span data-ttu-id="5021c-126">[数据挖掘查询任务和操作指南](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="5021c-126">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="5021c-127">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="5021c-127">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
