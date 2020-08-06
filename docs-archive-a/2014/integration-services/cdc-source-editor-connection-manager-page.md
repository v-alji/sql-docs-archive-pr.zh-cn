---
title: CDC 源编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b0ed4792f13006bb9013771c69053b04539bc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590328"
---
# <a name="cdc-source-editor-connection-manager-page"></a><span data-ttu-id="f5821-102">CDC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f5821-102">CDC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f5821-103">可以使用“CDC 源编辑器”对话框的“连接管理器”页，为 CDC 源从其中读取更改行的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库（CDC 数据库）选择 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f5821-103">Use the **Connection Manager** page of the **CDC Source Editor** dialog box to select the ADO.NET connection manager for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database that the CDC source reads change rows from (the CDC database).</span></span> <span data-ttu-id="f5821-104">一旦选择了 CDC 数据库，则需要选择该数据库中的一个捕获表。</span><span class="sxs-lookup"><span data-stu-id="f5821-104">Once the CDC database is selected you need to select a captured table in the database.</span></span>  
  
 <span data-ttu-id="f5821-105">有关 CDC 源的详细信息，请参阅 [CDC Source](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f5821-105">For more information about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f5821-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="f5821-106">Task List</span></span>  
 <span data-ttu-id="f5821-107">**打开“CDC 源编辑器”的“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="f5821-107">**To open the CDC Source Editor Connection Manager Page**</span></span>  
  
1.  <span data-ttu-id="f5821-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开具有 CDC 源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="f5821-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="f5821-109">在“数据流”  选项卡上，双击 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="f5821-109">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="f5821-110">在 **“CDC 源编辑器”** 中，单击 **“连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="f5821-110">In the **CDC Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5821-111">选项</span><span class="sxs-lookup"><span data-stu-id="f5821-111">Options</span></span>  
 <span data-ttu-id="f5821-112">**ADO.NET 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="f5821-112">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="f5821-113">从列表中选择现有连接管理器，或单击“新建”  创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="f5821-113">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="f5821-114">该连接必须是指向为 CDC 启用的并且所选更改表位于其中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="f5821-114">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="f5821-115">**新建**</span><span class="sxs-lookup"><span data-stu-id="f5821-115">**New**</span></span>  
 <span data-ttu-id="f5821-116">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="f5821-116">Click **New**.</span></span> <span data-ttu-id="f5821-117">**“配置 ADO.NET 连接管理器编辑器”** 对话框打开，可在其中创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f5821-117">The **Configure ADO.NET Connection Manager Editor** dialog box opens where you can create a new connection manager</span></span>  
  
 <span data-ttu-id="f5821-118">**CDC 表**</span><span class="sxs-lookup"><span data-stu-id="f5821-118">**CDC Table**</span></span>  
 <span data-ttu-id="f5821-119">选择您要读取并馈送到下游 SSIS 组件以便处理的捕获更改所在的 CDC 源表。</span><span class="sxs-lookup"><span data-stu-id="f5821-119">Select the CDC source table that contains the captured changes that you want read and feed to downstream SSIS components for processing.</span></span>  
  
 <span data-ttu-id="f5821-120">**捕获实例**</span><span class="sxs-lookup"><span data-stu-id="f5821-120">**Capture instance**</span></span>  
 <span data-ttu-id="f5821-121">选择或键入具有要读取的 CDC 表的“CDC 捕获实例”的名称。</span><span class="sxs-lookup"><span data-stu-id="f5821-121">Select or type in the name of the CDC capture instance with the CDC table to be read.</span></span>  
  
 <span data-ttu-id="f5821-122">一个捕获源表可具有一个或两个捕获实例，以便通过架构更改处理表定义的无缝转换。</span><span class="sxs-lookup"><span data-stu-id="f5821-122">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="f5821-123">如果为要捕获的源表定义了一个捕获实例，则选择要在此处使用的捕获实例。</span><span class="sxs-lookup"><span data-stu-id="f5821-123">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="f5821-124">表 [schema].[table] 的默认捕获实例名称为 \<schema>_\<table>，但使用的实际捕获实例名称可能会不同。</span><span class="sxs-lookup"><span data-stu-id="f5821-124">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="f5821-125">读取的实际表是 CDC 表 cdc .\<capture-instance>_CT。</span><span class="sxs-lookup"><span data-stu-id="f5821-125">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
 <span data-ttu-id="f5821-126">**CDC 处理模式**</span><span class="sxs-lookup"><span data-stu-id="f5821-126">**CDC Processing Mode**</span></span>  
 <span data-ttu-id="f5821-127">选择可以最好地满足您的处理需要的处理模式。</span><span class="sxs-lookup"><span data-stu-id="f5821-127">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="f5821-128">可能的选项包括：</span><span class="sxs-lookup"><span data-stu-id="f5821-128">The possible options are:</span></span>  
  
-   <span data-ttu-id="f5821-129">**所有**：返回当前 CDC 范围中的更改，但没有 **“更新前”** 值。</span><span class="sxs-lookup"><span data-stu-id="f5821-129">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
-   <span data-ttu-id="f5821-130">**全部且具有旧值**：返回当前 CDC 处理范围中的更改，包括旧值（“更新前”  ）。</span><span class="sxs-lookup"><span data-stu-id="f5821-130">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="f5821-131">对于每个更新操作将会有两行，一个针对更新前值，一个针对更新后值。</span><span class="sxs-lookup"><span data-stu-id="f5821-131">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
-   <span data-ttu-id="f5821-132">**净值**：对于当前 CDC 处理范围中修改的每个源行，仅返回一个更改行。</span><span class="sxs-lookup"><span data-stu-id="f5821-132">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="f5821-133">如果某一源行更新了多次，将生成合并的更改（例如，插入+更新作为单个更新生成，更新+删除作为单个删除生成）。</span><span class="sxs-lookup"><span data-stu-id="f5821-133">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="f5821-134">在净更改处理模式下工作时，可以拆分对删除、插入和更新输出的更改并且并行处理它们，因为单个源行出现多次。</span><span class="sxs-lookup"><span data-stu-id="f5821-134">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
-   <span data-ttu-id="f5821-135">**具有更新掩码的净值**：此模式类似于一般的净值模式，但它还添加了命名模式为 __$\<column-name>\_ 的布尔值列（指示当前更改行中已更改的列）。</span><span class="sxs-lookup"><span data-stu-id="f5821-135">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
-   <span data-ttu-id="f5821-136">**净值且具有合并**：此模式类似于一般的净值模式，但具有合并到单个合并操作中的插入和更新操作 (UPSERT)。</span><span class="sxs-lookup"><span data-stu-id="f5821-136">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5821-137">对于所有净更改选项，源表必须具有主键或唯一索引。</span><span class="sxs-lookup"><span data-stu-id="f5821-137">For all Net change options, the source table must have a primary key or unique index.</span></span> <span data-ttu-id="f5821-138">对于不具有主键或唯一索引的表，您必须选择 **“全部”** 选项。</span><span class="sxs-lookup"><span data-stu-id="f5821-138">For tables without a primary key or unique indes, you must yse the **All** option.</span></span>  
  
 <span data-ttu-id="f5821-139">**包含 CDC 状态的变量**</span><span class="sxs-lookup"><span data-stu-id="f5821-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="f5821-140">选择为当前 CDC 上下文维护 CDC 状态的 SSIS 字符串包变量。</span><span class="sxs-lookup"><span data-stu-id="f5821-140">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="f5821-141">有关 CDC 状态变量的详细信息，请参阅 [定义状态变量](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="f5821-141">For more information about the CDC state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="f5821-142">**包括重新处理指示器列**</span><span class="sxs-lookup"><span data-stu-id="f5821-142">**Include reprocessing indicator column**</span></span>  
 <span data-ttu-id="f5821-143">选中此复选框可以创建称作 **__$reprocessing**的特殊输出列。</span><span class="sxs-lookup"><span data-stu-id="f5821-143">Select this check box to create a special output column called **__$reprocessing**.</span></span>  
  
 <span data-ttu-id="f5821-144">在 CDC 处理范围与初始处理范围（与初始加载期间相对应的 LSN 的范围）重叠时，或者在之前的运行存在错误后重新处理某一 CDC 处理范围时，该列具有值 **true** 。</span><span class="sxs-lookup"><span data-stu-id="f5821-144">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="f5821-145">通过此指示器列，SSIS 开发人员可以在重新处理更改时以不同方式处理错误（例如，可忽略删除不存在的行和插入在重复键上失败之类的操作）。</span><span class="sxs-lookup"><span data-stu-id="f5821-145">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
 <span data-ttu-id="f5821-146">有关详细信息，请参阅 [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f5821-146">For more information, see [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5821-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5821-147">See Also</span></span>  
 <span data-ttu-id="f5821-148">[CDC 源编辑器（“列”页）](../../2014/integration-services/cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f5821-148">[CDC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="f5821-149">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="f5821-149">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
