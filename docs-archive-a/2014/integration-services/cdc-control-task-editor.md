---
title: CDC 控制任务编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdccontroltask.config.f1
ms.assetid: 4f09d040-9ec8-4aaa-b684-f632d571f0a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b60f2a9126dbbda934124b39f36ccd90b4e6cc6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590330"
---
# <a name="cdc-control-task-editor"></a><span data-ttu-id="5b61d-102">CDC 控制任务编辑器</span><span class="sxs-lookup"><span data-stu-id="5b61d-102">CDC Control Task Editor</span></span>
  <span data-ttu-id="5b61d-103">使用 **“CDC 控制任务编辑器”** 对话框可以配置 CDC 控制任务。</span><span class="sxs-lookup"><span data-stu-id="5b61d-103">Use the **CDC Control Task Editor** dialog box to configure the CDC Control task.</span></span> <span data-ttu-id="5b61d-104">CDC 控制任务配置包括定义与 CDC 数据库的连接、CDC 任务操作和状态管理信息。</span><span class="sxs-lookup"><span data-stu-id="5b61d-104">The CDC Control task configuration includes defining a connection to the CDC database, the CDC task operation and the state management information.</span></span>  
  
 <span data-ttu-id="5b61d-105">若要了解有关 CDC 控制任务的详细信息，请参阅 [CDC Control Task](control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="5b61d-105">To learn more about the CDC Control task, see [CDC Control Task](control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="5b61d-106">**打开“CDC 控制任务编辑器”**</span><span class="sxs-lookup"><span data-stu-id="5b61d-106">**To open the CDC Control Task Editor**</span></span>  
  
1.  <span data-ttu-id="5b61d-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含 CDC 控制任务的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="5b61d-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC Control task.</span></span>  
  
2.  <span data-ttu-id="5b61d-108">在“控制流”\*\*\*\* 选项卡上，双击 CDC 控制任务。</span><span class="sxs-lookup"><span data-stu-id="5b61d-108">On the **Control Flow** tab, double-click the CDC Control task.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b61d-109">选项</span><span class="sxs-lookup"><span data-stu-id="5b61d-109">Options</span></span>  
 <span data-ttu-id="5b61d-110">**SQL Server CDC 数据库 ADO.NET 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="5b61d-110">**SQL Server CDC database ADO.NET connection manager**</span></span>  
 <span data-ttu-id="5b61d-111">从列表中选择现有连接管理器，或单击“新建”  创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="5b61d-111">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="5b61d-112">该连接必须是指向为 CDC 启用的并且所选更改表位于其中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="5b61d-112">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="5b61d-113">**CDC 控制操作**</span><span class="sxs-lookup"><span data-stu-id="5b61d-113">**CDC Control Operation**</span></span>  
 <span data-ttu-id="5b61d-114">选择要为此任务运行的操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-114">Select the operation to run for this task.</span></span> <span data-ttu-id="5b61d-115">所有操作都使用存储在 SSIS 包变量中的状态变量，包变量存储状态并在包的不同组件之间传递该状态。</span><span class="sxs-lookup"><span data-stu-id="5b61d-115">All operations use the state variable that is stored in an SSIS package variable that stores the state and passes it between the different components in the package.</span></span>  
  
-   <span data-ttu-id="5b61d-116">**标记初始加载开始**：在从不具有快照的活动数据库执行初始加载时使用此操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-116">**Mark initial load start**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="5b61d-117">在初始加载包的开头调用此操作，以便在初始加载包开始读取源表之前记录源数据库中的当前 LSN。</span><span class="sxs-lookup"><span data-stu-id="5b61d-117">It is invoked at the beginning of an initial-load package to record the current LSN in the source database before the initial-load package starts reading the source tables.</span></span> <span data-ttu-id="5b61d-118">此操作要求连接到源数据库。</span><span class="sxs-lookup"><span data-stu-id="5b61d-118">This requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="5b61d-119">如果你在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC（也就是说，不是 Oracle）时选择“标记初始加载开始”\*\*\*\*，则在连接管理器中指定的用户必须是 **db_owner** 或 **sysadmin**。</span><span class="sxs-lookup"><span data-stu-id="5b61d-119">If you select **Mark Initial Load Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5b61d-120">**标记初始加载结束**：在从不具有快照的活动数据库执行初始加载时使用此操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-120">**Mark initial load end**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="5b61d-121">在初始加载包的末尾调用此操作，以便在初始加载包完成读取源表之后记录源数据库中的当前 LSN。</span><span class="sxs-lookup"><span data-stu-id="5b61d-121">It is invoked at the end of an initial-load package to record the current LSN in the source database after the initial-load package finished reading the source tables.</span></span> <span data-ttu-id="5b61d-122">此 LSN 通过以下方式确定：首先记录此操作发生时的当前时间，然后在 CDC 数据库的 `cdc.lsn_time_`映射表中进行查询以便查找在该时间后发生的更改。</span><span class="sxs-lookup"><span data-stu-id="5b61d-122">This LSN is determined by recording nthe current time when this operation occurred and then querying the `cdc.lsn_time_`mapping table in the CDC database looking for a change that occurred after that time</span></span>  
  
     <span data-ttu-id="5b61d-123">如果你在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC（也就是说，不是 Oracle）上工作时选择“标记初始加载结束”\*\*\*\*，则在连接管理器中指定的用户必须是 **db_owner** 或 **sysadmin**。</span><span class="sxs-lookup"><span data-stu-id="5b61d-123">If you select **Mark Initial Load End** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5b61d-124">**标记 CDC 开始**：在从快照数据库或静默数据库执行初始加载时使用此操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-124">**Mark CDC start**: This operation is used when then the initial load is made from a snapshot database or from a quiescence database.</span></span> <span data-ttu-id="5b61d-125">在初始加载包内的任何一点都可以调用该操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-125">It is invoked at any point within the initial load package.</span></span> <span data-ttu-id="5b61d-126">该操作接受可以作为快照 LSN 的参数、快照数据库的名称（将自其自动派生快照 LSN），也可以将其保留为空（这种情况下，将当前数据库 LSN 用作更改处理包的开始 LSN）。</span><span class="sxs-lookup"><span data-stu-id="5b61d-126">The operation accepts a parameter that can be a snapshot LSN, a name of a snapshot database (from which the snapshot LSN will be derived automatically) or it can be left empty, in which case the current database LSN is used as the start LSN for the change processing package.</span></span>  
  
     <span data-ttu-id="5b61d-127">此操作可用来替代标记初始加载开始/结束操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-127">This operation is used instead of the Mark Initial Load Start/End operations.</span></span>  
  
     <span data-ttu-id="5b61d-128">如果你在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC（也就是说，不是 Oracle）上工作时选择“标记 CDC 开始”\*\*\*\*，则在连接管理器中指定的用户必须是 **db_owner** 或 **sysadmin**。</span><span class="sxs-lookup"><span data-stu-id="5b61d-128">If you select **Mark CDC Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5b61d-129">**获取处理范围**：在调用使用 CDC 源数据流的数据流之前，在更改处理包中使用此操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-129">**Get processing range**: This operation is used in a change processing package before invoking the data flow that uses the CDC Source data flow.</span></span> <span data-ttu-id="5b61d-130">此操作建立 CDC 源数据流在调用时读取的 LSN 的范围。</span><span class="sxs-lookup"><span data-stu-id="5b61d-130">It establishes a range of LSNs that the CDC Source data flow reads when invoked.</span></span> <span data-ttu-id="5b61d-131">该范围存储于一个 SSIS 包变量中，在数据流处理期间 CDC 源将使用该变量。</span><span class="sxs-lookup"><span data-stu-id="5b61d-131">The range is stored in an SSIS package variable that is used by the CDC Source during data-flow processing.</span></span>  
  
     <span data-ttu-id="5b61d-132">有关存储的可能的 CDC 状态的详细信息，请参阅 [定义状态变量](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="5b61d-132">For more information about the possible CDC states that are stored, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
-   <span data-ttu-id="5b61d-133">**标记已处理的范围**：在 CDC 运行结束时（在 CDC 数据流成功完成后）在更改处理包中使用此操作，以便记录在 CDC 运行中完全处理的上一个 LSN。</span><span class="sxs-lookup"><span data-stu-id="5b61d-133">**Mark processed range**: This operation is used in a change processing package at the end of a  CDC run (after the CDC data flow is completed successfully) to record the last LSN that was fully processed in the CDC run.</span></span> <span data-ttu-id="5b61d-134">下一次执行 `GetProcessingRange` 时，此位置确定下一处理范围的起点。</span><span class="sxs-lookup"><span data-stu-id="5b61d-134">The next time `GetProcessingRange` is executed, this position determines the start of the next processing range.</span></span>  
  
-   <span data-ttu-id="5b61d-135">**重置 CDC 状态**：此操作用于重置与当前 CDC 上下文相关联的持久 CDC 状态。</span><span class="sxs-lookup"><span data-stu-id="5b61d-135">**Reset CDC state**: This operation is used to reset the persistent CDC state associated with the current CDC context.</span></span> <span data-ttu-id="5b61d-136">在此操作运行后，来自 LSN-timestamp `sys.fn_cdc_get_max_lsn` 表的当前最大 LSN 将成为下一处理范围的起始范围。</span><span class="sxs-lookup"><span data-stu-id="5b61d-136">After this operation is run, the current maximum LSN from the LSN-timestamp `sys.fn_cdc_get_max_lsn` table becomes the start of the range for the next processing range.</span></span> <span data-ttu-id="5b61d-137">此操作要求到源数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="5b61d-137">This operation requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="5b61d-138">举例来说，当您只需处理新创建的更改记录而忽略所有旧的更改记录时，就需要使用此操作。</span><span class="sxs-lookup"><span data-stu-id="5b61d-138">An example of when this operation is used is when you want to process only the newly created change records and ignore all old change records.</span></span>  
  
 <span data-ttu-id="5b61d-139">**包含 CDC 状态的变量**</span><span class="sxs-lookup"><span data-stu-id="5b61d-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="5b61d-140">选择存储任务操作的状态信息的 SSIS 包变量。</span><span class="sxs-lookup"><span data-stu-id="5b61d-140">Select the SSIS package variable that stores the state information for the task operation.</span></span> <span data-ttu-id="5b61d-141">在开始之前，应该先定义一个变量。</span><span class="sxs-lookup"><span data-stu-id="5b61d-141">You should define a variable before you begin.</span></span> <span data-ttu-id="5b61d-142">如果您选择 **“自动状态持久性”**，将自动加载和保存状态变量。</span><span class="sxs-lookup"><span data-stu-id="5b61d-142">If you select **Automatic state persistence**, the state variable is loaded and saved automatically.</span></span>  
  
 <span data-ttu-id="5b61d-143">有关定义状态变量的详细信息，请参阅 [定义状态变量](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="5b61d-143">For more information about defining the state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="5b61d-144">**启动 CDC 的 SQL Server LSN/快照名称：**</span><span class="sxs-lookup"><span data-stu-id="5b61d-144">**SQL Server LSN to start the CDC/Snapshot name:**</span></span>  
 <span data-ttu-id="5b61d-145">键入自其开始执行初始加载的当前源数据库 LSN 或快照数据库的名称，以确定 CDC 的起点。</span><span class="sxs-lookup"><span data-stu-id="5b61d-145">Type the current source database LSN or the name of the snapshot database from which the initial load is performed to determine where the CDC starts.</span></span> <span data-ttu-id="5b61d-146">仅当 **“CDC 控制操作”** 设置为 **“标记 CDC 开始”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="5b61d-146">This is available only if the **CDC Control Operation** is set to **Mark CDC Start**.</span></span>  
  
 <span data-ttu-id="5b61d-147">有关这些操作的详细信息，请参阅 [CDC Control Task](control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="5b61d-147">For more information about these operations, see [CDC Control Task](control-flow/cdc-control-task.md)</span></span>  
  
 <span data-ttu-id="5b61d-148">**在数据库表中自动存储状态**</span><span class="sxs-lookup"><span data-stu-id="5b61d-148">**Automatically store state in a database table**</span></span>  
 <span data-ttu-id="5b61d-149">选中此复选框后，CDC 控制任务可以在指定数据库所包含的状态表中自动加载和存储 CDC 状态。</span><span class="sxs-lookup"><span data-stu-id="5b61d-149">Select this check box for the CDC Control task to automatically handle loading and storing the CDC state in a state table contained in the specified database.</span></span> <span data-ttu-id="5b61d-150">若未选中此选项，开发人员必须在包开始执行时加载 CDC 状态，并且只要 CDC 状态发生更改就要保存该状态。</span><span class="sxs-lookup"><span data-stu-id="5b61d-150">When not selected, the developer must load the CDC State when the package starts and save it whenever the CDC State changes.</span></span>  
  
 <span data-ttu-id="5b61d-151">**存储状态的数据库的连接管理器**</span><span class="sxs-lookup"><span data-stu-id="5b61d-151">**Connection manager for the database where the state is stored**</span></span>  
 <span data-ttu-id="5b61d-152">从列表中选择现有 ADO.NET 连接管理器，或单击“新建”创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="5b61d-152">Select an existing ADO.NET connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="5b61d-153">此连接指向包含状态表的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="5b61d-153">This connection is to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains the State table.</span></span> <span data-ttu-id="5b61d-154">状态表包含状态信息。</span><span class="sxs-lookup"><span data-stu-id="5b61d-154">The State table contains the State information.</span></span>  
  
 <span data-ttu-id="5b61d-155">仅当选定 **“自动状态持久性”** 时此选项才可用，并且这是一个必需的参数。</span><span class="sxs-lookup"><span data-stu-id="5b61d-155">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="5b61d-156">**用于存储状态的表**</span><span class="sxs-lookup"><span data-stu-id="5b61d-156">**Table to use for storing state**</span></span>  
 <span data-ttu-id="5b61d-157">键入要用于存储 CDC 状态的状态表的名称。</span><span class="sxs-lookup"><span data-stu-id="5b61d-157">Type the name of the state table to be used for storing the CDC state.</span></span> <span data-ttu-id="5b61d-158">指定的表必须具有名为 **name** 和 **state** 的两列，并且这两列的数据类型必须为 **varchar (256)**。</span><span class="sxs-lookup"><span data-stu-id="5b61d-158">The table specified must have two columns called **name** and **state** and both columns must be of the data type **varchar (256)**.</span></span>  
  
 <span data-ttu-id="5b61d-159">还可以选择 **“新建”** ，获取可生成具有必需列的新状态表的 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="5b61d-159">You can optionally select **New** to get an SQL script that builds a new State table with the required columns.</span></span> <span data-ttu-id="5b61d-160">如果选择 **“自动状态持久性”** ，开发人员必须根据上面列出的要求创建一个状态表。</span><span class="sxs-lookup"><span data-stu-id="5b61d-160">When **Automatic state persistence** is selected, the developer must create a state table according to the requirements listed above.</span></span>  
  
 <span data-ttu-id="5b61d-161">仅当选定 **“自动状态持久性”** 时此选项才可用，并且这是一个必需的参数。</span><span class="sxs-lookup"><span data-stu-id="5b61d-161">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="5b61d-162">**状态名称**</span><span class="sxs-lookup"><span data-stu-id="5b61d-162">**State name**</span></span>  
 <span data-ttu-id="5b61d-163">键入与持久 CDC 状态关联的名称。</span><span class="sxs-lookup"><span data-stu-id="5b61d-163">Type a name to associate with the persistent CDC state.</span></span> <span data-ttu-id="5b61d-164">使用相同 CDC 上下文的完整负载和 CDC 包将指定一个公共的状态名称。</span><span class="sxs-lookup"><span data-stu-id="5b61d-164">The full load and CDC packages that work with the same CDC context will specify a common state name.</span></span> <span data-ttu-id="5b61d-165">此名称用于查找状态表中的状态行。</span><span class="sxs-lookup"><span data-stu-id="5b61d-165">This name is used for looking up the state row in the state table</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b61d-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b61d-166">See Also</span></span>  
 [<span data-ttu-id="5b61d-167">CDC 控制任务自定义属性</span><span class="sxs-lookup"><span data-stu-id="5b61d-167">CDC Control Task Custom Properties</span></span>](control-flow/cdc-control-task-custom-properties.md)  
  
  
