---
title: 使用 CDC 源提取更改数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ef981a22e286f519c9b93b3181b47df43321548b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694059"
---
# <a name="extract-change-data-using-the-cdc-source"></a><span data-ttu-id="804a1-102">使用 CDC 源提取更改数据</span><span class="sxs-lookup"><span data-stu-id="804a1-102">Extract Change Data Using the CDC Source</span></span>
  <span data-ttu-id="804a1-103">若要添加并配置 CDC 源，则包必须已包含至少一个数据流任务和一个 CDC 控制任务。</span><span class="sxs-lookup"><span data-stu-id="804a1-103">To add and configure a CDC source, the package must already include at least one Data Flow task and a CDC Control task.</span></span>  
  
 <span data-ttu-id="804a1-104">有关 CDC 控制任务的详细信息，请参阅 [CDC Control Task](../control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="804a1-104">For more information about the CDC Control task, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="804a1-105">有关 CDC 源的详细信息，请参阅 [CDC Source](cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="804a1-105">For more information about the CDC source, see [CDC Source](cdc-source.md).</span></span>  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a><span data-ttu-id="804a1-106">使用 CDC 源提取更改数据</span><span class="sxs-lookup"><span data-stu-id="804a1-106">To extract change data using a CDC source</span></span>  
  
1.  <span data-ttu-id="804a1-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，打开包含所需包的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="804a1-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="804a1-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="804a1-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="804a1-109">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 把 CDC 源拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="804a1-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC source to the design surface.</span></span>  
  
4.  <span data-ttu-id="804a1-110">双击此 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="804a1-110">Double-click the CDC source.</span></span>  
  
5.  <span data-ttu-id="804a1-111">在 **“CDC 源编辑器”** 对话框中的 **“连接管理器”** 页上，从列表中选择现有的 ADO.NET 连接管理器，或单击 **“新建”** 创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="804a1-111">In the **CDC Source Editor** dialog box, on the **Connection Manager** page, select an existing ADO.NET connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="804a1-112">该连接应该是与包含要读取的更改表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="804a1-112">The connection should be to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the change tables to read.</span></span>  
  
6.  <span data-ttu-id="804a1-113">选择要处理更改的 **“CDC 表”** 。</span><span class="sxs-lookup"><span data-stu-id="804a1-113">Select the **CDC table** where you want to process changes.</span></span>  
  
7.  <span data-ttu-id="804a1-114">选择或键入具有要读取的 CDC 表的 **“CDC 捕获实例”** 的名称。</span><span class="sxs-lookup"><span data-stu-id="804a1-114">Select or type in the name of the **CDC capture instance** with the CDC table to be read.</span></span>  
  
     <span data-ttu-id="804a1-115">一个捕获源表可具有一个或两个捕获实例，以便通过架构更改处理表定义的无缝转换。</span><span class="sxs-lookup"><span data-stu-id="804a1-115">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="804a1-116">如果为要捕获的源表定义了一个捕获实例，则选择要在此处使用的捕获实例。</span><span class="sxs-lookup"><span data-stu-id="804a1-116">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="804a1-117">表 [schema].[table] 的默认捕获实例名称为 \<schema>_\<table>，但使用的实际捕获实例名称可能会不同。</span><span class="sxs-lookup"><span data-stu-id="804a1-117">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="804a1-118">读取的实际表是 CDC 表 cdc .\<capture-instance>_CT。</span><span class="sxs-lookup"><span data-stu-id="804a1-118">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
8.  <span data-ttu-id="804a1-119">选择可以最好地满足您的处理需要的处理模式。</span><span class="sxs-lookup"><span data-stu-id="804a1-119">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="804a1-120">可能的选项包括：</span><span class="sxs-lookup"><span data-stu-id="804a1-120">The possible options are:</span></span>  
  
    -   <span data-ttu-id="804a1-121">**所有**：返回当前 CDC 范围中的更改，但没有 **“更新前”** 值。</span><span class="sxs-lookup"><span data-stu-id="804a1-121">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
    -   <span data-ttu-id="804a1-122">**全部且具有旧值**：返回当前 CDC 处理范围中的更改，包括旧值（“更新前”  ）。</span><span class="sxs-lookup"><span data-stu-id="804a1-122">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="804a1-123">对于每个更新操作将会有两行，一个针对更新前值，一个针对更新后值。</span><span class="sxs-lookup"><span data-stu-id="804a1-123">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
    -   <span data-ttu-id="804a1-124">**净值**：对于当前 CDC 处理范围中修改的每个源行，仅返回一个更改行。</span><span class="sxs-lookup"><span data-stu-id="804a1-124">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="804a1-125">如果某一源行更新了多次，将生成合并的更改（例如，插入+更新作为单个更新生成，更新+删除作为单个删除生成）。</span><span class="sxs-lookup"><span data-stu-id="804a1-125">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="804a1-126">在净更改处理模式下工作时，可以拆分对删除、插入和更新输出的更改并且并行处理它们，因为单个源行出现多次。</span><span class="sxs-lookup"><span data-stu-id="804a1-126">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
    -   <span data-ttu-id="804a1-127">**具有更新掩码的净值**：此模式类似于一般的净值模式，但它还添加了命名模式为 __$\<column-name>\__Changed 的布尔值列（指示当前更改行中已更改的列）。</span><span class="sxs-lookup"><span data-stu-id="804a1-127">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
    -   <span data-ttu-id="804a1-128">**净值且具有合并**：此模式类似于一般的净值模式，但具有合并到单个合并操作中的插入和更新操作 (UPSERT)。</span><span class="sxs-lookup"><span data-stu-id="804a1-128">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
9. <span data-ttu-id="804a1-129">选择为当前 CDC 上下文维护 CDC 状态的 SSIS 字符串包变量。</span><span class="sxs-lookup"><span data-stu-id="804a1-129">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="804a1-130">有关 CDC 状态变量的详细信息，请参阅 [定义状态变量](define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="804a1-130">For more information about the CDC state variable, see [Define a State Variable](define-a-state-variable.md).</span></span>  
  
10. <span data-ttu-id="804a1-131">选中“包括重新处理指示器列”  复选框可以创建称作 **__$reprocessing** 的特殊输出列。</span><span class="sxs-lookup"><span data-stu-id="804a1-131">Select the **Include reprocessing indicator column** check box to create a special output column called **__$reprocessing**.</span></span> <span data-ttu-id="804a1-132">在 CDC 处理范围与初始处理范围（与初始加载期间相对应的 LSN 的范围）重叠时，或者在之前的运行存在错误后重新处理某一 CDC 处理范围时，该列具有值 **true** 。</span><span class="sxs-lookup"><span data-stu-id="804a1-132">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="804a1-133">通过此指示器列，SSIS 开发人员可以在重新处理更改时以不同方式处理错误（例如，可忽略删除不存在的行和插入在重复键上失败之类的操作）。</span><span class="sxs-lookup"><span data-stu-id="804a1-133">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
     <span data-ttu-id="804a1-134">有关详细信息，请参阅 [CDC Source Custom Properties](cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="804a1-134">For more information, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
11. <span data-ttu-id="804a1-135">若要更新外部列和输出列之间的映射，请单击 **“列”** ，并在 **“外部列”** 列表中选择其他列。</span><span class="sxs-lookup"><span data-stu-id="804a1-135">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
12. <span data-ttu-id="804a1-136">也可以通过删除 **“输出列”** 列表中的值来更新输出列的值。</span><span class="sxs-lookup"><span data-stu-id="804a1-136">Optionally update the values of the output columns by deleting values in the **Output Column** list.</span></span>  
  
13. <span data-ttu-id="804a1-137">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="804a1-137">To configure the error output, click **Error Output**.</span></span>  
  
14. <span data-ttu-id="804a1-138">可以单击 **“预览”** ，查看最多 200 行 CDC 源所提取的数据。</span><span class="sxs-lookup"><span data-stu-id="804a1-138">You can click **Preview** to view up to 200 rows of data extracted by the CDC source.</span></span>  
  
15. <span data-ttu-id="804a1-139">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="804a1-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804a1-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="804a1-140">See Also</span></span>  
 <span data-ttu-id="804a1-141">[CDC 源编辑器（“连接管理器”页）](../cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="804a1-141">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="804a1-142">[CDC 源编辑器（“列”页）](../cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="804a1-142">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="804a1-143">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="804a1-143">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
  
