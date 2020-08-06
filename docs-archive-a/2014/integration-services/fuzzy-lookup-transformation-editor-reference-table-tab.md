---
title: 模糊查找转换编辑器 (引用表选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce51dd64c9c5807ab23ac645694cfec29a36d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578324"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="01e61-102">模糊查找转换编辑器（“引用表”选项卡）</span><span class="sxs-lookup"><span data-stu-id="01e61-102">Fuzzy Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="01e61-103">使用 **“模糊查找转换编辑器”** 对话框的 **“引用表”** 选项卡可以指定用于查找的源表和索引。</span><span class="sxs-lookup"><span data-stu-id="01e61-103">Use the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor** dialog box to specify the source table and the index to use for the lookup.</span></span> <span data-ttu-id="01e61-104">引用数据源必须是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="01e61-104">The reference data source must be a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01e61-105">模糊查找转换将创建引用表的工作副本。</span><span class="sxs-lookup"><span data-stu-id="01e61-105">The Fuzzy Lookup transformation creates a working copy of the reference table.</span></span> <span data-ttu-id="01e61-106">下面描述的索引是通过使用特殊的表对此工作表创建的，它们不是普通的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 索引。</span><span class="sxs-lookup"><span data-stu-id="01e61-106">The indexes described below are created on this working table by using a special table, not an ordinary [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] index.</span></span> <span data-ttu-id="01e61-107">除非选择了 **“维护存储的索引”**，否则转换不会修改现有的源表。</span><span class="sxs-lookup"><span data-stu-id="01e61-107">The transformation does not modify the existing source tables unless you select **Maintain stored index**.</span></span> <span data-ttu-id="01e61-108">在这种情况下，转换将对引用表创建一个触发器，此触发器将基于对引用表所做的更改来更新工作表和查找索引表。</span><span class="sxs-lookup"><span data-stu-id="01e61-108">In this case, it creates a trigger on the reference table that updates the working table and the lookup index table based on changes to the reference table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01e61-109">`Exhaustive`模糊查找转换的和 `MaxMemoryUsage` 属性在 "**模糊查找转换编辑器**" 中不可用，但可以使用 "**高级编辑器**" 进行设置。</span><span class="sxs-lookup"><span data-stu-id="01e61-109">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Lookup transformation are not available in the **Fuzzy Lookup Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="01e61-110">此外，只能 `MaxOutputMatchesPerInput` 在**高级编辑器**中指定大于100的值。</span><span class="sxs-lookup"><span data-stu-id="01e61-110">In addition, a value greater than 100 for `MaxOutputMatchesPerInput` can be specified only in the **Advanced Editor**.</span></span> <span data-ttu-id="01e61-111">有关这些属性的详细信息，请参阅 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)的“模糊查找转换”部分。</span><span class="sxs-lookup"><span data-stu-id="01e61-111">For more information on these properties, see the Fuzzy Lookup Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="01e61-112">若要了解有关模糊查找转换的详细信息，请参阅 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="01e61-112">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="01e61-113">选项</span><span class="sxs-lookup"><span data-stu-id="01e61-113">Options</span></span>  
 <span data-ttu-id="01e61-114">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="01e61-114">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="01e61-115">从列表中选择现有的 OLE DB 连接管理器，或通过单击“新建”\*\*\*\* 创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="01e61-115">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="01e61-116">**新建**</span><span class="sxs-lookup"><span data-stu-id="01e61-116">**New**</span></span>  
 <span data-ttu-id="01e61-117">通过使用“配置 OLE DB 连接管理器”  对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="01e61-117">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="01e61-118">**生成新索引**</span><span class="sxs-lookup"><span data-stu-id="01e61-118">**Generate new index**</span></span>  
 <span data-ttu-id="01e61-119">指定转换应创建新的索引以用于查找。</span><span class="sxs-lookup"><span data-stu-id="01e61-119">Specify that the transformation should create a new index to use for the lookup.</span></span>  
  
 <span data-ttu-id="01e61-120">**引用表的名称**</span><span class="sxs-lookup"><span data-stu-id="01e61-120">**Reference table name**</span></span>  
 <span data-ttu-id="01e61-121">选择要用作引用（查找）表的现有表。</span><span class="sxs-lookup"><span data-stu-id="01e61-121">Select the existing table to use as the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="01e61-122">**存储新索引**</span><span class="sxs-lookup"><span data-stu-id="01e61-122">**Store new index**</span></span>  
 <span data-ttu-id="01e61-123">如果希望保存新的查找索引，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="01e61-123">Select this option if you want to save the new lookup index.</span></span>  
  
 <span data-ttu-id="01e61-124">**新索引名称**</span><span class="sxs-lookup"><span data-stu-id="01e61-124">**New index name**</span></span>  
 <span data-ttu-id="01e61-125">如果已选择保存新的查找索引，请为其键入描述性名称。</span><span class="sxs-lookup"><span data-stu-id="01e61-125">If you have chosen to save the new lookup index, type a descriptive name for the index.</span></span>  
  
 <span data-ttu-id="01e61-126">**“维护存储的索引”**</span><span class="sxs-lookup"><span data-stu-id="01e61-126">**Maintain stored index**</span></span>  
 <span data-ttu-id="01e61-127">如果已选择保存新的查找索引，请指定是否还希望 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 维护该索引。</span><span class="sxs-lookup"><span data-stu-id="01e61-127">If you have chosen to save the new lookup index, specify whether you also want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to maintain the index.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01e61-128">如果在 **“模糊查找转换编辑器”** 的 **“引用表”** 选项卡中选择 **“维护存储的索引”**，则转换将使用托管存储过程维护索引。</span><span class="sxs-lookup"><span data-stu-id="01e61-128">When you select **Maintain stored index** on the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor**, the transformation uses managed stored procedures to maintain the index.</span></span> <span data-ttu-id="01e61-129">这些托管存储过程使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的公共语言运行时 (CLR) 集成功能。</span><span class="sxs-lookup"><span data-stu-id="01e61-129">These managed stored procedures use the common language runtime (CLR) integration feature in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="01e61-130">默认情况下，不启用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="01e61-130">By default, CLR integration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not enabled.</span></span> <span data-ttu-id="01e61-131">若要使用 **“维护存储的索引”** 功能，必须启用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="01e61-131">To use the **Maintain stored index** functionality, you must enable CLR integration.</span></span> <span data-ttu-id="01e61-132">有关详细信息，请参阅 [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="01e61-132">For more information, see [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md).</span></span>  
>   
>  <span data-ttu-id="01e61-133">由于 **“维护存储的索引”** 选项需要 CLR 集成，所以只有在选择已启用 CLR 集成的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例上的引用表时，此功能才能发挥作用。</span><span class="sxs-lookup"><span data-stu-id="01e61-133">Because the **Maintain stored index** option requires CLR integration, this feature works only when you select a reference table on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where CLR integration is enabled.</span></span>  
  
 <span data-ttu-id="01e61-134">**使用现有索引**</span><span class="sxs-lookup"><span data-stu-id="01e61-134">**Use existing index**</span></span>  
 <span data-ttu-id="01e61-135">指定转换应使用现有索引来执行查找。</span><span class="sxs-lookup"><span data-stu-id="01e61-135">Specify that the transformation should use an existing index for the lookup.</span></span>  
  
 <span data-ttu-id="01e61-136">**现有索引的名称**</span><span class="sxs-lookup"><span data-stu-id="01e61-136">**Name of an existing index**</span></span>  
 <span data-ttu-id="01e61-137">从列表中选择以前创建的查找索引。</span><span class="sxs-lookup"><span data-stu-id="01e61-137">Select a previously created lookup index from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e61-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01e61-138">See Also</span></span>  
 <span data-ttu-id="01e61-139">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="01e61-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="01e61-140">[模糊查找转换编辑器 &#40;列 "选项卡&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="01e61-140">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 [<span data-ttu-id="01e61-141">模糊查找转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="01e61-141">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
