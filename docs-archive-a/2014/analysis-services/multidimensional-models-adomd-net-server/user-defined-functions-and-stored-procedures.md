---
title: 用户定义函数和存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682431"
---
# <a name="user-defined-functions-and-stored-procedures"></a><span data-ttu-id="f5c45-102">用户定义函数和存储过程</span><span class="sxs-lookup"><span data-stu-id="f5c45-102">User Defined Functions and Stored Procedures</span></span>
  <span data-ttu-id="f5c45-103">对于 ADOMD.NET 服务器对象，您可以 (UDF) 或存储过程创建用户定义的函数，以与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器中的元数据和数据进行交互。</span><span class="sxs-lookup"><span data-stu-id="f5c45-103">With ADOMD.NET server objects, you can create user defined function (UDF) or stored procedures for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that interact with metadata and data from the server.</span></span> <span data-ttu-id="f5c45-104">这些进程内方法是通过多维表达式 (MDX) 或数据挖掘扩展插件 (DMX) 语句调用的，可以提供附加功能而不会有网络通信的延迟。</span><span class="sxs-lookup"><span data-stu-id="f5c45-104">These in-process methods are called through Multidimensional Expressions (MDX) or Data Mining Extensions (DMX) statements to provide added functionality without the latencies associated with network communications.</span></span>  
  
## <a name="udf-examples"></a><span data-ttu-id="f5c45-105">UDF 示例</span><span class="sxs-lookup"><span data-stu-id="f5c45-105">UDF Examples</span></span>  
 <span data-ttu-id="f5c45-106">UDF 是一种可在 MDX 或 DMX 语句上下文中调用的方法，可具有任意数目的参数，并可返回任意类型的数据。</span><span class="sxs-lookup"><span data-stu-id="f5c45-106">A UDF is a method that can be called in the context of an MDX or DMX statement, can take any number of parameters, and can return any type of data.</span></span>  
  
 <span data-ttu-id="f5c45-107">使用 MDX 创建的 UDF 与用 DMX 创建的 UDF 类似。</span><span class="sxs-lookup"><span data-stu-id="f5c45-107">A UDF created using MDX is similar to one created for DMX.</span></span> <span data-ttu-id="f5c45-108">主要区别在于， [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))对象的某些属性（如[AdomdServer \*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120))和 CurrentCube \* 属性）仅适用于一种脚本语言或另一种语言的属性，例如 microsoft.analysisservices.sharepoint.integration.dll \* 和 AdomdServer [\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120))属性。</span><span class="sxs-lookup"><span data-stu-id="f5c45-108">The main difference is that certain properties of the [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object, such as the [Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube\*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) and [Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) properties, are available only for one scripting language or the other.</span></span>  
  
 <span data-ttu-id="f5c45-109">下面的示例演示如何使用 UDF 返回节点说明、筛选元组并对元组应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="f5c45-109">The following examples show how to use a UDF to return a node description, filter tuples, and apply a filter to a tuple.</span></span>  
  
### <a name="returning-a-node-description"></a><span data-ttu-id="f5c45-110">返回节点说明</span><span class="sxs-lookup"><span data-stu-id="f5c45-110">Returning a Node Description</span></span>  
 <span data-ttu-id="f5c45-111">下面的示例创建一个返回指定节点的节点说明的 UDF。</span><span class="sxs-lookup"><span data-stu-id="f5c45-111">The following example creates a UDF that returns the node description for a specified node.</span></span> <span data-ttu-id="f5c45-112">该 UDF 使用它正在其中运行的当前上下文，并使用 DMX FROM 子句从当前挖掘模型检索节点。</span><span class="sxs-lookup"><span data-stu-id="f5c45-112">The UDF uses the current context in which it is being run, and uses a DMX FROM clause to retrieve the node from the current mining model.</span></span>  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 <span data-ttu-id="f5c45-113">部署后，下面的 DMX 表达式（检索最有可能的预测节点）就可以调用上面的 UDF 示例了。</span><span class="sxs-lookup"><span data-stu-id="f5c45-113">Once deployed, the previous UDF example can be called by the following DMX expression, which retrieves the most-likely prediction node.</span></span> <span data-ttu-id="f5c45-114">节点的说明包含描述组成预测节点的条件的信息。</span><span class="sxs-lookup"><span data-stu-id="f5c45-114">The description contains information that describes the conditions that make up the prediction node.</span></span>  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a><span data-ttu-id="f5c45-115">返回元组</span><span class="sxs-lookup"><span data-stu-id="f5c45-115">Returning Tuples</span></span>  
 <span data-ttu-id="f5c45-116">下面的示例使用一个集和一个返回计数，它从该集中随机检索元组，并返回一个最终子集：</span><span class="sxs-lookup"><span data-stu-id="f5c45-116">The following example takes a set and a return count, and randomly retrieves tuples from the set, returning a final subset:</span></span>  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 <span data-ttu-id="f5c45-117">下面的 MDX 示例中调用了上面的示例。</span><span class="sxs-lookup"><span data-stu-id="f5c45-117">The previous example is called in the following MDX example.</span></span> <span data-ttu-id="f5c45-118">在此 MDX 示例中，将从**艾德公司**数据库中检索五个随机状态或省/自治区。</span><span class="sxs-lookup"><span data-stu-id="f5c45-118">In this MDX example, five random states or provinces are retrieved from the **Adventure Works** database.</span></span>  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a><span data-ttu-id="f5c45-119">对元组应用筛选器</span><span class="sxs-lookup"><span data-stu-id="f5c45-119">Applying a Filter to a Tuple</span></span>  
 <span data-ttu-id="f5c45-120">下面的示例中定义了一个 UDF，该 UDF 使用一个集，并使用 Expression 对象对集中的每个元组应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="f5c45-120">In the following example, a UDF is defined that takes a set, and applies a filter to each tuple in the set, using the Expression object.</span></span> <span data-ttu-id="f5c45-121">所有符合筛选条件的元组都将被添加到返回的集中。</span><span class="sxs-lookup"><span data-stu-id="f5c45-121">Any tuples that conform to the filter will be added to a set that is returned.</span></span>  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 <span data-ttu-id="f5c45-122">下面的 MDX 示例调用了上面的示例，该 MDX 示例从集中筛选名称以“A”开头的市县。</span><span class="sxs-lookup"><span data-stu-id="f5c45-122">The previous example is called in the following MDX example, which filters the set to cities with names beginning with 'A'.</span></span>  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a><span data-ttu-id="f5c45-123">存储过程示例</span><span class="sxs-lookup"><span data-stu-id="f5c45-123">Stored Procedure Example</span></span>  
 <span data-ttu-id="f5c45-124">在下面的示例中，基于 MDX 的存储过程使用 AMO 来为 Internet 销售创建分区（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="f5c45-124">In the following example, an MDX-based stored procedure uses AMO to create partitions, if needed, for Internet Sales.</span></span>  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
