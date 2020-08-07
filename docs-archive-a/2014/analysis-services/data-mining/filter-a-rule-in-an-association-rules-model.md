---
title: 筛选关联规则模型中的规则 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filtering rules [Analysis Services]
- Mining Model Viewer [Analysis Services], rules
- Rules Viewer
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c904713acc6eaf132e7cb1195186165f21d971a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588150"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a><span data-ttu-id="a47bc-102">筛选关联规则模型中的规则</span><span class="sxs-lookup"><span data-stu-id="a47bc-102">Filter a Rule in an Association Rules Model</span></span>
  <span data-ttu-id="a47bc-103">您可以将筛选与关联模型一起使用来限制结果，使其仅包含您感兴趣的关联。</span><span class="sxs-lookup"><span data-stu-id="a47bc-103">You can use filtering with association models to restrict the results to just the associations that interest you.</span></span> <span data-ttu-id="a47bc-104">例如，您可以筛选规则，以便仅显示包含特定产品的规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-104">For example, you might filter the rules to show only those that include a specific product.</span></span>  
  
 <span data-ttu-id="a47bc-105">在数据挖掘设计器中，可使用 \*\*\*\*[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则查看器的“规则”选项卡上的控件来筛选所显示的规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-105">In Data Mining Designer, you use the controls on the **Rules** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer to filter the rules that are displayed.</span></span>  <span data-ttu-id="a47bc-106">你还可以创建一个基于模型的查询，只查看包含特定值的项集。</span><span class="sxs-lookup"><span data-stu-id="a47bc-106">You can also create a query on the model to see only itemset that contains a particular value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a47bc-107">此选项仅可用于使用 Microsoft 关联算法创建的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a47bc-107">This option is available only for mining models that have been created by using the Microsoft Association Algorithm.</span></span>  
  
### <a name="filter-a-rule-in-an-association-model"></a><span data-ttu-id="a47bc-108">筛选关联模型中的规则</span><span class="sxs-lookup"><span data-stu-id="a47bc-108">Filter a rule in an association model</span></span>  
  
1.  <span data-ttu-id="a47bc-109">使用 **“关联规则查看器”** 打开挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a47bc-109">Open the mining model by using the **Association Rules Viewer**.</span></span> <span data-ttu-id="a47bc-110">若要在 SQL Server Management Studio 中执行此操作，右键单击模型名称，然后选择 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="a47bc-110">To do this in SQL Server Management Studio, right click the model name and select **Browse**.</span></span> <span data-ttu-id="a47bc-111">若要在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中执行此操作，请双击包含该模型的挖掘结构，然后单击“数据挖掘设计器”的“挖掘模型查看器”选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a47bc-111">To do this in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the model, and then click the **Mining Model Viewer** tab of **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="a47bc-112">单击 **“关联规则查看器”** 的 **“规则”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a47bc-112">Click the **Rules** tab of the **Association Rules Viewer**.</span></span>  
  
3.  <span data-ttu-id="a47bc-113">在 **“筛选规则”** 框中键入规则条件。</span><span class="sxs-lookup"><span data-stu-id="a47bc-113">Type a rule condition into the **Filter Rule** box.</span></span> <span data-ttu-id="a47bc-114">例如，规则条件可以为“Bike Stand”，该条件还可以返回“Bike Stands”。</span><span class="sxs-lookup"><span data-stu-id="a47bc-114">For example, a rule condition might be "Bike Stand", which also returns "Bike Stands".</span></span>  
  
     <span data-ttu-id="a47bc-115">**“筛选规则”** 文本框支持用 .NET 语言定义的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="a47bc-115">The **Filter Rule** text box supports regular expressions as defined by the .NET language.</span></span> <span data-ttu-id="a47bc-116">因此，可使用如下所示的表达式： `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`。</span><span class="sxs-lookup"><span data-stu-id="a47bc-116">Therefore, you can use expressions such as the following: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`.</span></span> <span data-ttu-id="a47bc-117">此表达式将返回特定项集，其中包括的属性具有以各种顺序显示的词语“Helmets”和“Fenders”。</span><span class="sxs-lookup"><span data-stu-id="a47bc-117">This expression would return any itemsets that include attributes with the words Helmets and Fenders, in any order.</span></span>  
  
4.  <span data-ttu-id="a47bc-118">对于 **“最小概率”**，增大概率值以查看较少的规则，减小概率值以查看较多的规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-118">For **Minimum probability**, increase the value of probability to see fewer rules, or decrease the value to see more rules.</span></span>  
  
5.  <span data-ttu-id="a47bc-119">对于 **“最低重要性”**，增大重要性的值以查看较少的规则，减小该值以查看较多的规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-119">For **Minimum importance**, increase the value of importance to see fewer rules, or decrease the value to see more rules.</span></span>  
  
6.  <span data-ttu-id="a47bc-120">对于 **“显示”**，选择以下选项之一： **“显示属性名称和值”**、 **“仅显示属性名称”** 或 **“仅显示属性值”**。</span><span class="sxs-lookup"><span data-stu-id="a47bc-120">For **Show**, select one of the following options: **Show attribute name and value**, **Show attribute name only**, or **Show attribute value only**.</span></span>  
  
7.  <span data-ttu-id="a47bc-121">对于 **“最大行数”**，增大该值以增加符合指定条件的规则的总数，减小该值以限制返回的规则数。</span><span class="sxs-lookup"><span data-stu-id="a47bc-121">For **Maximum rows**, increase the value to increase the total number of rules that meet the specified conditions, or decrease the value to limit the number of rules returned.</span></span> <span data-ttu-id="a47bc-122">规则按概率排序，所以您可以消除符合指定的概率或重要性条件的其他规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-122">Rules are ordered by probability, so you might eliminate additional rules that meet the specified conditions for probability or importance.</span></span>  
  
8.  <span data-ttu-id="a47bc-123">选中或取消选中 **“显示长名称”** 复选框以切换规则名称的显示方式。</span><span class="sxs-lookup"><span data-stu-id="a47bc-123">Select or deselect the **Show long name** check box to toggle the way that the rules names are displayed.</span></span>  
  
     <span data-ttu-id="a47bc-124">现在筛选过的规则将仅显示包含所指项的那些规则。</span><span class="sxs-lookup"><span data-stu-id="a47bc-124">The rules are now filtered to only display rules that contain the indicated item.</span></span> <span data-ttu-id="a47bc-125">筛选条件可应用到属性值中的规则分隔符“->”之前或之后。</span><span class="sxs-lookup"><span data-stu-id="a47bc-125">The filter condition applies to attribute values either before or after the rule delimiter, "->".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a47bc-126">查看器基于挖掘模型的查询对规则的初始列表进行缓存；除非您通过设置最大行数、概率、重要性或长名称的显示方式来更改查询条件，否则查看器不刷新规则列表。</span><span class="sxs-lookup"><span data-stu-id="a47bc-126">The viewer caches the initial list of rules, based on a query to the mining model, and does not refresh the list of rules unless you change the conditions of the query by setting the maximum rows, the probability, importance, or the display of long names.</span></span> <span data-ttu-id="a47bc-127">因此，如果键入了某一条件而显示并未立即刷新，则可以通过先选中再取消选中 **“显示长名称”** 复选框强制查看器刷新数据。</span><span class="sxs-lookup"><span data-stu-id="a47bc-127">Therefore, if you type a condition and the display does not immediately refresh, you can force the viewer to refresh the data by selecting and then deselecting the **Show long names** check box.</span></span>  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a><span data-ttu-id="a47bc-128">针对关联模型中的项集创建查询</span><span class="sxs-lookup"><span data-stu-id="a47bc-128">Create a query on the itemsets in an association model</span></span>  
  
-   [<span data-ttu-id="a47bc-129">关联模型查询示例</span><span class="sxs-lookup"><span data-stu-id="a47bc-129">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
## <a name="see-also"></a><span data-ttu-id="a47bc-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a47bc-130">See Also</span></span>  
 <span data-ttu-id="a47bc-131">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a47bc-131">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a47bc-132">[使用 Microsoft 关联规则查看器浏览模型](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="a47bc-132">[Browse a Model Using the Microsoft Association Rules Viewer](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span></span>  
 [<span data-ttu-id="a47bc-133">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="a47bc-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
