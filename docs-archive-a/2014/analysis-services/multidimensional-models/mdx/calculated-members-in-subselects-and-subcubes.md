---
title: 嵌套 select 语句和子多维数据中的计算成员 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e6f4277c864b637c7fc5d93232ac6ebd8c4bb4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588111"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="483f9-102">嵌套 select 和子多维数据集中的计算成员</span><span class="sxs-lookup"><span data-stu-id="483f9-102">Calculated Members in Subselects and Subcubes</span></span>
  <span data-ttu-id="483f9-103">在以前的版本中，在嵌套 select 或子多维数据集中不允许使用计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-103">In previous releases, calculated members were not allowed in subselects or subcubes.</span></span> <span data-ttu-id="483f9-104">但从 SQL Server 2008 开始，在连接属性中允许使用和启用计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-104">However, starting with SQL Server 2008 they are allowed and enabled by a connection property.</span></span> <span data-ttu-id="483f9-105">此外，在 SQL Server 2008 R2 的嵌套 select 和子多维数据集中，还引入了针对计算成员的一个新行为。</span><span class="sxs-lookup"><span data-stu-id="483f9-105">In addition, a new behavior for calculated members, in subselects and subcubes, was introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="483f9-106">嵌套 select 和子多维数据集中的计算成员</span><span class="sxs-lookup"><span data-stu-id="483f9-106">Calculated Members in Subselects and Subcubes</span></span>  
 <span data-ttu-id="483f9-107">`SubQueries`中的连接字符串属性 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 或中 `DBPROPMSMDSUBQUERIES` 支持的[xmla 属性 &#40;xmla&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)定义计算成员或计算集对嵌套 select 语句或子多维数据的行为。</span><span class="sxs-lookup"><span data-stu-id="483f9-107">The `SubQueries` connection string property in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> or the `DBPROPMSMDSUBQUERIES` property in [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) defines the behavior or allowance of calculated members or calculated sets on subselects or subcubes.</span></span> <span data-ttu-id="483f9-108">在本文档的上下文中，如果没有特别指明，则嵌套 select 表示嵌套 select 和子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="483f9-108">In the context of this document, subselect refers to subselects and subcubes unless otherwise stated.</span></span>  
  
 <span data-ttu-id="483f9-109">SubQueries 属性允许以下值。</span><span class="sxs-lookup"><span data-stu-id="483f9-109">The SubQueries property allows the following values.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="483f9-110">值</span><span class="sxs-lookup"><span data-stu-id="483f9-110">Value</span></span>|<span data-ttu-id="483f9-111">说明</span><span class="sxs-lookup"><span data-stu-id="483f9-111">Description</span></span>|  
|<span data-ttu-id="483f9-112">0</span><span class="sxs-lookup"><span data-stu-id="483f9-112">0</span></span>|<span data-ttu-id="483f9-113">计算成员不允许在嵌套 select 或子多维数据集中使用。</span><span class="sxs-lookup"><span data-stu-id="483f9-113">Calculated members are not allowed in subselects or subcubes.</span></span><br /><br /> <span data-ttu-id="483f9-114">如果引用计算成员，则在对嵌套 select 或子多维数据集进行计算时，将引发错误。</span><span class="sxs-lookup"><span data-stu-id="483f9-114">An error is raised when evaluating the subselect or subcube if a calculated member is referenced.</span></span>|  
|<span data-ttu-id="483f9-115">1</span><span class="sxs-lookup"><span data-stu-id="483f9-115">1</span></span>|<span data-ttu-id="483f9-116">计算成员允许在嵌套 select 或子多维数据集中使用，但在返回子空间中不引入祖先成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-116">Calculated members are allowed in subselects or subcubes but no ascendant members are introduced in the returning subspace.</span></span>|  
|<span data-ttu-id="483f9-117">2</span><span class="sxs-lookup"><span data-stu-id="483f9-117">2</span></span>|<span data-ttu-id="483f9-118">计算成员允许在嵌套 select 或子多维数据集中使用，并且在返回子空间中引入祖先成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-118">Calculated members are allowed in subselects or subcubes and ascendant members are introduced in the returning subspace.</span></span> <span data-ttu-id="483f9-119">此外，在选择计算成员时允许使用混合粒度。</span><span class="sxs-lookup"><span data-stu-id="483f9-119">Also, mixed granularity is allowed in the selection of calculated members.</span></span>|  
  
 <span data-ttu-id="483f9-120">在 SubQueries 属性中使用值 1 或 2 允许计算成员用于筛选嵌套 select 的返回子空间。</span><span class="sxs-lookup"><span data-stu-id="483f9-120">Using values of 1 or 2 in the SubQueries property allows calculated members to be used to filter the returning subspace of subselects.</span></span>  
  
 <span data-ttu-id="483f9-121">将通过一个例子帮助阐明这个概念；首先，必须创建一个计算成员，然后发出一个嵌套 select 查询以便说明上述行为。</span><span class="sxs-lookup"><span data-stu-id="483f9-121">An example will help clarify the concept; first a calculated member must be created and then a subselect query issued to show the above mentioned behavior.</span></span>  
  
 <span data-ttu-id="483f9-122">下面的示例创建一个计算成员，该计算成员将 [Seattle Metro] 作为城市添加到 Washington 州下的 [Geography].[Geography] 层次结构中。</span><span class="sxs-lookup"><span data-stu-id="483f9-122">The following sample creates a calculated member that adds [Seattle Metro] as a city to the [Geography].[Geography] hierarchy under Washington state.</span></span>  
  
 <span data-ttu-id="483f9-123">为了运行该示例，连接字符串必须包含具有值 1 的 SubQueries 属性，并且所有 MDX 语句必须在同一会话中运行。</span><span class="sxs-lookup"><span data-stu-id="483f9-123">To run the example, the connection string must contain the SubQueries property with a value of 1 and all MDX statements must be run in the same session.</span></span>  
  
 <span data-ttu-id="483f9-124">首先发出以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="483f9-124">First issue the following MDX expression:</span></span>  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 <span data-ttu-id="483f9-125">然后发出以下 MDX 查询以便查看在嵌套 select 中允许的计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-125">Then issue the following MDX query to see calculated members allowed in subselects.</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="483f9-126">获得的结果如下：</span><span class="sxs-lookup"><span data-stu-id="483f9-126">The obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="483f9-127">All Periods</span><span class="sxs-lookup"><span data-stu-id="483f9-127">All Periods</span></span>|<span data-ttu-id="483f9-128">CY 2001</span><span class="sxs-lookup"><span data-stu-id="483f9-128">CY 2001</span></span>|<span data-ttu-id="483f9-129">CY 2002</span><span class="sxs-lookup"><span data-stu-id="483f9-129">CY 2002</span></span>|<span data-ttu-id="483f9-130">CY 2003</span><span class="sxs-lookup"><span data-stu-id="483f9-130">CY 2003</span></span>|<span data-ttu-id="483f9-131">CY 2004</span><span class="sxs-lookup"><span data-stu-id="483f9-131">CY 2004</span></span>|  
|<span data-ttu-id="483f9-132">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="483f9-132">Seattle Metro Agg</span></span>|<span data-ttu-id="483f9-133">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="483f9-133">$2,383,545.69</span></span>|<span data-ttu-id="483f9-134">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="483f9-134">$291,248.93</span></span>|<span data-ttu-id="483f9-135">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="483f9-135">$763,557.02</span></span>|<span data-ttu-id="483f9-136">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="483f9-136">$915,832.36</span></span>|<span data-ttu-id="483f9-137">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="483f9-137">$412,907.37</span></span>|  
  
 <span data-ttu-id="483f9-138">如前所述，在 SubQueries=1 时，[Seattle Metro] 的祖先在返回的子空间中不存在，因此，[Geography].[Geography].allmembers 仅包含计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-138">As said before, the ascendants of [Seattle Metro] do not exist in the returned subspace, when SubQueries=1, hence [Geography].[Geography].allmembers only contains the calculated member.</span></span>  
  
 <span data-ttu-id="483f9-139">如果使用 SubQueries=2 运行该示例，则在连接字符串中，获得的结果如下：</span><span class="sxs-lookup"><span data-stu-id="483f9-139">If the example is run using SubQueries=2, in the connection string, the obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="483f9-140">All Periods</span><span class="sxs-lookup"><span data-stu-id="483f9-140">All Periods</span></span>|<span data-ttu-id="483f9-141">CY 2001</span><span class="sxs-lookup"><span data-stu-id="483f9-141">CY 2001</span></span>|<span data-ttu-id="483f9-142">CY 2002</span><span class="sxs-lookup"><span data-stu-id="483f9-142">CY 2002</span></span>|<span data-ttu-id="483f9-143">CY 2003</span><span class="sxs-lookup"><span data-stu-id="483f9-143">CY 2003</span></span>|<span data-ttu-id="483f9-144">CY 2004</span><span class="sxs-lookup"><span data-stu-id="483f9-144">CY 2004</span></span>|  
|<span data-ttu-id="483f9-145">All Geographies</span><span class="sxs-lookup"><span data-stu-id="483f9-145">All Geographies</span></span>|<span data-ttu-id="483f9-146">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-146">(null)</span></span>|<span data-ttu-id="483f9-147">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-147">(null)</span></span>|<span data-ttu-id="483f9-148">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-148">(null)</span></span>|<span data-ttu-id="483f9-149">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-149">(null)</span></span>|<span data-ttu-id="483f9-150">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-150">(null)</span></span>|  
|<span data-ttu-id="483f9-151">美国</span><span class="sxs-lookup"><span data-stu-id="483f9-151">United States</span></span>|<span data-ttu-id="483f9-152">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-152">(null)</span></span>|<span data-ttu-id="483f9-153">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-153">(null)</span></span>|<span data-ttu-id="483f9-154">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-154">(null)</span></span>|<span data-ttu-id="483f9-155">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-155">(null)</span></span>|<span data-ttu-id="483f9-156">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-156">(null)</span></span>|  
|<span data-ttu-id="483f9-157">Washington</span><span class="sxs-lookup"><span data-stu-id="483f9-157">Washington</span></span>|<span data-ttu-id="483f9-158">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-158">(null)</span></span>|<span data-ttu-id="483f9-159">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-159">(null)</span></span>|<span data-ttu-id="483f9-160">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-160">(null)</span></span>|<span data-ttu-id="483f9-161">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-161">(null)</span></span>|<span data-ttu-id="483f9-162">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-162">(null)</span></span>|  
|<span data-ttu-id="483f9-163">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="483f9-163">Seattle Metro Agg</span></span>|<span data-ttu-id="483f9-164">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="483f9-164">$2,383,545.69</span></span>|<span data-ttu-id="483f9-165">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="483f9-165">$291,248.93</span></span>|<span data-ttu-id="483f9-166">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="483f9-166">$763,557.02</span></span>|<span data-ttu-id="483f9-167">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="483f9-167">$915,832.36</span></span>|<span data-ttu-id="483f9-168">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="483f9-168">$412,907.37</span></span>|  
  
 <span data-ttu-id="483f9-169">如前所述，在使用 SubQueries=2 时，[Seattle Metro] 的祖先存在于返回的子空间中，但对于这些成员不存在任何值，因为没有要为聚合提供的常规成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-169">As said before, when using SubQueries=2, the ascendants of [Seattle Metro] exist in the returned subspace but no values exist for those members because there is no regular members to provide for the aggregations.</span></span> <span data-ttu-id="483f9-170">因此，在此示例中，为计算成员的所有祖先成员提供 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="483f9-170">Therefore, NULL values are provided for all ascendant members of the calculated member in this example.</span></span>  
  
 <span data-ttu-id="483f9-171">为了理解上述行为，您需要了解的是：与常规成员不同，计算成员并不影响其父级的聚合；这意味着单独按计算成员进行筛选将导致空的祖先，因为没有常规成员影响最终生成的子空间的聚合值。</span><span class="sxs-lookup"><span data-stu-id="483f9-171">To understand the above behavior, it helps to understand that calculated members do not contribute to the aggregations of their parents as regular members do; the former implies that filtering by calculated members alone will lead to empty ascendants because there are no regular members to contribute to the aggregated values of the resulting subspace.</span></span> <span data-ttu-id="483f9-172">如果您将常规成员添加到筛选表达式，则聚合值将来自这些常规成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-172">If you add regular members to the filtering expression then the aggregated values will come from those regular members.</span></span> <span data-ttu-id="483f9-173">继续以上面的示例为例，如果 Oregon 州的 Portland 市以及 Washington 州的 Spokane 市添加到计算成员出现的同一轴中；如下一个 MDX 表达式所示：</span><span class="sxs-lookup"><span data-stu-id="483f9-173">Continuing with the above example, if the cities of Portland, in Oregon, and the city of Spokane, in Washington, are added to the same axis where the calculated member appears; as shown in the next MDX expression:</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="483f9-174">将获得以下结果。</span><span class="sxs-lookup"><span data-stu-id="483f9-174">The following results are obtained.</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="483f9-175">All Periods</span><span class="sxs-lookup"><span data-stu-id="483f9-175">All Periods</span></span>|<span data-ttu-id="483f9-176">CY 2001</span><span class="sxs-lookup"><span data-stu-id="483f9-176">CY 2001</span></span>|<span data-ttu-id="483f9-177">CY 2002</span><span class="sxs-lookup"><span data-stu-id="483f9-177">CY 2002</span></span>|<span data-ttu-id="483f9-178">CY 2003</span><span class="sxs-lookup"><span data-stu-id="483f9-178">CY 2003</span></span>|<span data-ttu-id="483f9-179">CY 2004</span><span class="sxs-lookup"><span data-stu-id="483f9-179">CY 2004</span></span>|  
|<span data-ttu-id="483f9-180">All Geographies</span><span class="sxs-lookup"><span data-stu-id="483f9-180">All Geographies</span></span>|<span data-ttu-id="483f9-181">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="483f9-181">$235,171.62</span></span>|<span data-ttu-id="483f9-182">$419.46</span><span class="sxs-lookup"><span data-stu-id="483f9-182">$419.46</span></span>|<span data-ttu-id="483f9-183">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="483f9-183">$4,996.25</span></span>|<span data-ttu-id="483f9-184">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="483f9-184">$131,788.82</span></span>|<span data-ttu-id="483f9-185">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="483f9-185">$97,967.09</span></span>|  
|<span data-ttu-id="483f9-186">美国</span><span class="sxs-lookup"><span data-stu-id="483f9-186">United States</span></span>|<span data-ttu-id="483f9-187">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="483f9-187">$235,171.62</span></span>|<span data-ttu-id="483f9-188">$419.46</span><span class="sxs-lookup"><span data-stu-id="483f9-188">$419.46</span></span>|<span data-ttu-id="483f9-189">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="483f9-189">$4,996.25</span></span>|<span data-ttu-id="483f9-190">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="483f9-190">$131,788.82</span></span>|<span data-ttu-id="483f9-191">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="483f9-191">$97,967.09</span></span>|  
|<span data-ttu-id="483f9-192">Oregon</span><span class="sxs-lookup"><span data-stu-id="483f9-192">Oregon</span></span>|<span data-ttu-id="483f9-193">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="483f9-193">$30,968.25</span></span>|<span data-ttu-id="483f9-194">$419.46</span><span class="sxs-lookup"><span data-stu-id="483f9-194">$419.46</span></span>|<span data-ttu-id="483f9-195">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="483f9-195">$4,996.25</span></span>|<span data-ttu-id="483f9-196">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="483f9-196">$17,442.97</span></span>|<span data-ttu-id="483f9-197">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="483f9-197">$8,109.56</span></span>|  
|<span data-ttu-id="483f9-198">Portland</span><span class="sxs-lookup"><span data-stu-id="483f9-198">Portland</span></span>|<span data-ttu-id="483f9-199">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="483f9-199">$30,968.25</span></span>|<span data-ttu-id="483f9-200">$419.46</span><span class="sxs-lookup"><span data-stu-id="483f9-200">$419.46</span></span>|<span data-ttu-id="483f9-201">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="483f9-201">$4,996.25</span></span>|<span data-ttu-id="483f9-202">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="483f9-202">$17,442.97</span></span>|<span data-ttu-id="483f9-203">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="483f9-203">$8,109.56</span></span>|  
|<span data-ttu-id="483f9-204">97205</span><span class="sxs-lookup"><span data-stu-id="483f9-204">97205</span></span>|<span data-ttu-id="483f9-205">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="483f9-205">$30,968.25</span></span>|<span data-ttu-id="483f9-206">$419.46</span><span class="sxs-lookup"><span data-stu-id="483f9-206">$419.46</span></span>|<span data-ttu-id="483f9-207">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="483f9-207">$4,996.25</span></span>|<span data-ttu-id="483f9-208">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="483f9-208">$17,442.97</span></span>|<span data-ttu-id="483f9-209">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="483f9-209">$8,109.56</span></span>|  
|<span data-ttu-id="483f9-210">Washington</span><span class="sxs-lookup"><span data-stu-id="483f9-210">Washington</span></span>|<span data-ttu-id="483f9-211">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="483f9-211">$204,203.37</span></span>|<span data-ttu-id="483f9-212">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-212">(null)</span></span>|<span data-ttu-id="483f9-213">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-213">(null)</span></span>|<span data-ttu-id="483f9-214">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="483f9-214">$114,345.85</span></span>|<span data-ttu-id="483f9-215">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="483f9-215">$89,857.52</span></span>|  
|<span data-ttu-id="483f9-216">Spokane</span><span class="sxs-lookup"><span data-stu-id="483f9-216">Spokane</span></span>|<span data-ttu-id="483f9-217">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="483f9-217">$204,203.37</span></span>|<span data-ttu-id="483f9-218">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-218">(null)</span></span>|<span data-ttu-id="483f9-219">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-219">(null)</span></span>|<span data-ttu-id="483f9-220">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="483f9-220">$114,345.85</span></span>|<span data-ttu-id="483f9-221">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="483f9-221">$89,857.52</span></span>|  
|<span data-ttu-id="483f9-222">99202</span><span class="sxs-lookup"><span data-stu-id="483f9-222">99202</span></span>|<span data-ttu-id="483f9-223">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="483f9-223">$204,203.37</span></span>|<span data-ttu-id="483f9-224">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-224">(null)</span></span>|<span data-ttu-id="483f9-225">(null)</span><span class="sxs-lookup"><span data-stu-id="483f9-225">(null)</span></span>|<span data-ttu-id="483f9-226">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="483f9-226">$114,345.85</span></span>|<span data-ttu-id="483f9-227">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="483f9-227">$89,857.52</span></span>|  
|<span data-ttu-id="483f9-228">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="483f9-228">Seattle Metro Agg</span></span>|<span data-ttu-id="483f9-229">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="483f9-229">$2,383,545.69</span></span>|<span data-ttu-id="483f9-230">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="483f9-230">$291,248.93</span></span>|<span data-ttu-id="483f9-231">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="483f9-231">$763,557.02</span></span>|<span data-ttu-id="483f9-232">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="483f9-232">$915,832.36</span></span>|<span data-ttu-id="483f9-233">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="483f9-233">$412,907.37</span></span>|  
  
 <span data-ttu-id="483f9-234">在上面的结果中，[All Geographies]、[United States]、[Oregon] 和 [Washington] 的聚合值来自对 &[Portland]&[OR] 和 &[Spokane]&[WA] 的后代执行的聚合。</span><span class="sxs-lookup"><span data-stu-id="483f9-234">In the above results the aggregated values for [All Geographies], [United States], [Oregon] and [Washington] come from aggregating over the descendants of &[Portland]&[OR] and &[Spokane]&[WA].</span></span> <span data-ttu-id="483f9-235">没有任何内容来自计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-235">Nothing comes from the calculated member.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="483f9-236">备注</span><span class="sxs-lookup"><span data-stu-id="483f9-236">Remarks</span></span>  
 <span data-ttu-id="483f9-237">在嵌套 select 或子多维数据集表达式中只允许全局或会话计算成员。</span><span class="sxs-lookup"><span data-stu-id="483f9-237">Only global or session calculated members are allowed in the subselect or subcube expressions.</span></span> <span data-ttu-id="483f9-238">在对嵌套 select 或子多维数据集表达式执行计算时，如果在 MDX 表达式中具有查询计算成员，将引发错误。</span><span class="sxs-lookup"><span data-stu-id="483f9-238">Having query calculated members in the MDX expression will raise an error when the subselect or subcube expression is evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483f9-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="483f9-239">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 <span data-ttu-id="483f9-240">[查询中的嵌套 select 语句](subselects-in-queries.md) </span><span class="sxs-lookup"><span data-stu-id="483f9-240">[Subselects in Queries](subselects-in-queries.md) </span></span>  
 [<span data-ttu-id="483f9-241">支持的 XMLA 属性 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="483f9-241">Supported XMLA Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
