---
title: 定义状态变量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45d66152-883a-49a7-a877-2e8ab45f8f79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5214b3512ea0113d1abace61a76033e5531ac99f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694068"
---
# <a name="define-a-state-variable"></a><span data-ttu-id="ed986-102">定义状态变量</span><span class="sxs-lookup"><span data-stu-id="ed986-102">Define a State Variable</span></span>
  <span data-ttu-id="ed986-103">本过程介绍如何定义用于存储 CDC 状态的包变量。</span><span class="sxs-lookup"><span data-stu-id="ed986-103">This procedure describes how to define a package variable where the CDC state is stored.</span></span>  
  
 <span data-ttu-id="ed986-104">该 CDC 状态变量由 CDC 控制任务加载、初始化和更新，并且由 CDC 源数据流组件用于确定针对更改记录的当前处理范围。</span><span class="sxs-lookup"><span data-stu-id="ed986-104">The CDC state variable is loaded, initialized, and updated by the CDC Control task and is used by the CDC Source data flow component to determine the current processing range for change records.</span></span> <span data-ttu-id="ed986-105">可对 CDC 控制任务和 CDC 源所共有的任何容器定义该 CDC 状态变量。</span><span class="sxs-lookup"><span data-stu-id="ed986-105">The CDC state variable can be defined on any container common to the CDC Control task and the CDC source.</span></span> <span data-ttu-id="ed986-106">此操作可在包级别进行，但也可以对循环容器之类的其他容器进行。</span><span class="sxs-lookup"><span data-stu-id="ed986-106">This may be at the package level but may also be on other containers such as a loop container.</span></span>  
  
 <span data-ttu-id="ed986-107">不建议手动修改 CDC 状态变量值，但是，了解其内容可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="ed986-107">Manually modifying the CDC state variable value is not recommended, however it can be useful to understand its contents.</span></span>  
  
 <span data-ttu-id="ed986-108">下表提供了 CDC 状态变量值的组分的详细说明。</span><span class="sxs-lookup"><span data-stu-id="ed986-108">The following table provides a high-level description of the components of the CDC state variable value.</span></span>  
  
|<span data-ttu-id="ed986-109">组件</span><span class="sxs-lookup"><span data-stu-id="ed986-109">Component</span></span>|<span data-ttu-id="ed986-110">说明</span><span class="sxs-lookup"><span data-stu-id="ed986-110">Description</span></span>|  
|---------------|-----------------|  
|`<state-name>`|<span data-ttu-id="ed986-111">这是当前 CDC 状态的名称。</span><span class="sxs-lookup"><span data-stu-id="ed986-111">This is the name of the current CDC state.</span></span>|  
|`CS`|<span data-ttu-id="ed986-112">这标记当前处理范围开始点（当前开始）。</span><span class="sxs-lookup"><span data-stu-id="ed986-112">This marks the current processing range start point (Current Start).</span></span>|  
|`<cs-lsn>`|<span data-ttu-id="ed986-113">这是上一次 CDC 运行中处理的最后一个（日志序列号）LSN。</span><span class="sxs-lookup"><span data-stu-id="ed986-113">This is the last (Log Sequence Number) LSN processed in the previous CDC run.</span></span>|  
|`CE`|<span data-ttu-id="ed986-114">这标记当前处理范围结束点（当前结束）。</span><span class="sxs-lookup"><span data-stu-id="ed986-114">This marks the current processing range end point (Current End).</span></span> <span data-ttu-id="ed986-115">CDC 状态中的 CE 组分表示 CDC 包当前正在处理或 CDC 包在完全处理其 CDC 处理范围前失败。</span><span class="sxs-lookup"><span data-stu-id="ed986-115">The presence of the CE component in the CDC state is an indication that either a CDC package is currently processing or that a CDC package failed before fully processing its CDC processing range.</span></span>|  
|`<ce-lsn>`|<span data-ttu-id="ed986-116">这是当前运行的 CDC 中要处理的最后一个 LSN。</span><span class="sxs-lookup"><span data-stu-id="ed986-116">This is the last LSN to be processed in the current CDC Run.</span></span> <span data-ttu-id="ed986-117">始终假定要处理的最后一个序列号为最大值 (0xFFF…)。</span><span class="sxs-lookup"><span data-stu-id="ed986-117">It is always assumed that the last sequence number to be processed is the maximum (0xFFF...).</span></span>|  
|`IR`|<span data-ttu-id="ed986-118">这标记初始处理范围。</span><span class="sxs-lookup"><span data-stu-id="ed986-118">This marks the initial processing range.</span></span>|  
|`<ir-start>`|<span data-ttu-id="ed986-119">这是初始加载开始之前的最后一个更改 LSN。</span><span class="sxs-lookup"><span data-stu-id="ed986-119">This is an LSN of a change just before the initial load began.</span></span>|  
|`<ir-end>`|<span data-ttu-id="ed986-120">这是初始加载结束之后的第一个更改 LSN。</span><span class="sxs-lookup"><span data-stu-id="ed986-120">This is an LSN of a change just after the initial load ended.</span></span>|  
|`TS`|<span data-ttu-id="ed986-121">这标记最后一个 CDC 状态更新的时间戳。</span><span class="sxs-lookup"><span data-stu-id="ed986-121">This marks the timestamp for the last CDC state update.</span></span>|  
|**\<timestamp>**|<span data-ttu-id="ed986-122">这是 64 位 System.DateTime.UtcNow 属性的十进制表示法。</span><span class="sxs-lookup"><span data-stu-id="ed986-122">This is a decimal representation of the 64-bit, System.DateTime.UtcNow property.</span></span>|  
|`ER`|<span data-ttu-id="ed986-123">当最后一个操作失败且包括错误原因的简短说明时显示它。</span><span class="sxs-lookup"><span data-stu-id="ed986-123">This appears when the last operation failed and includes a short description of the cause of the error.</span></span> <span data-ttu-id="ed986-124">如果存在该组分，则它始终最后一个显示。</span><span class="sxs-lookup"><span data-stu-id="ed986-124">If this component is present, it will always appear last.</span></span>|  
|`<short-error-text>`|<span data-ttu-id="ed986-125">这是简短的错误说明。</span><span class="sxs-lookup"><span data-stu-id="ed986-125">This is the short error description.</span></span>|  
  
 <span data-ttu-id="ed986-126">LSN 和序列号每个都作为一个十六进制的字符串编码，该字符串最多包含 20 位数字，表示 Binary(10) 的 LSN 值。</span><span class="sxs-lookup"><span data-stu-id="ed986-126">The LSNs and sequence numbers are each encoded as a hexadecimal string of up to 20 digits representing the LSN value of Binary(10).</span></span>  
  
 <span data-ttu-id="ed986-127">下表对可能的CDC 状态值进行了说明：</span><span class="sxs-lookup"><span data-stu-id="ed986-127">The following table describes the possible CDC state values.</span></span>  
  
|<span data-ttu-id="ed986-128">状态</span><span class="sxs-lookup"><span data-stu-id="ed986-128">State</span></span>|<span data-ttu-id="ed986-129">说明</span><span class="sxs-lookup"><span data-stu-id="ed986-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed986-130">(INITIAL)</span><span class="sxs-lookup"><span data-stu-id="ed986-130">(INITIAL)</span></span>|<span data-ttu-id="ed986-131">这是在当前 CDC 组上运行任何包之前的初始状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-131">This is the initial state before the any package was run on the current CDC group.</span></span> <span data-ttu-id="ed986-132">这也是 CDC 状态为空时的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-132">This is also the state when the CDC state is empty.</span></span>|  
|<span data-ttu-id="ed986-133">ILSTART（初始加载已开始）</span><span class="sxs-lookup"><span data-stu-id="ed986-133">ILSTART (Initial Load Started)</span></span>|<span data-ttu-id="ed986-134">这是初始加载包已开始、`MarkInitialLoadStart` 操作调用 CDC 控制任务后时的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-134">This is the state when the initial load package starts, after the `MarkInitialLoadStart` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="ed986-135">ILEND（初始加载已结束）</span><span class="sxs-lookup"><span data-stu-id="ed986-135">ILEND (Initial Load Ended)</span></span>|<span data-ttu-id="ed986-136">这是初始加载包已成功结束、`MarkInitialLoadEnd` 操作调用 CDC 控制任务后时的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-136">This is the state when the initial load package ends successfully, after the `MarkInitialLoadEnd` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="ed986-137">ILUPDATE（初始加载更新）</span><span class="sxs-lookup"><span data-stu-id="ed986-137">ILUPDATE (Initial Load Update)</span></span>|<span data-ttu-id="ed986-138">这是在初始加载后仍在处理初始处理范围期间运行滴送更新包时的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-138">This is the state on the runs of the trickle feed update package following the initial load, while still processing the initial processing range.</span></span> <span data-ttu-id="ed986-139">这是 `GetProcessingRange` 操作调用 CDC 控制任务后的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-139">This is after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="ed986-140">如果使用 _$reprocessing 列，该列设置为 1，指示该包可能在重新处理目标上已存在的行。</span><span class="sxs-lookup"><span data-stu-id="ed986-140">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="ed986-141">TFEND（滴送更新已结束）</span><span class="sxs-lookup"><span data-stu-id="ed986-141">TFEND (Trickle-Feed Update Ended)</span></span>|<span data-ttu-id="ed986-142">这是常规 CDC 运行应该出现的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-142">This is the state expected for regular CDC runs.</span></span> <span data-ttu-id="ed986-143">它指示前一次运行已成功完成，可以开始具有新的处理范围的新一轮运行。</span><span class="sxs-lookup"><span data-stu-id="ed986-143">It indicates that the previous run completed successfully and that a new run with a new processing range can be started.</span></span>|  
|<span data-ttu-id="ed986-144">TFSTART</span><span class="sxs-lookup"><span data-stu-id="ed986-144">TFSTART</span></span>|<span data-ttu-id="ed986-145">这是在非初始运行滴送更新包时、`GetProcessingRange` 操作调用 CDC 控制任务后的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-145">This is the state on a non-initial run of the trickle feed update package, after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="ed986-146">这指示已启动常规 CDC 运行，但运行未完成或未完全结束 (`MarkProcessedRange`)。</span><span class="sxs-lookup"><span data-stu-id="ed986-146">This indicates that a regular CDC run is started but has not finished or has not yet finished, cleanly (`MarkProcessedRange`).</span></span>|  
|<span data-ttu-id="ed986-147">TFREDO（重新处理滴送更新）</span><span class="sxs-lookup"><span data-stu-id="ed986-147">TFREDO (Reprocessing Trickle-Feed Updates)</span></span>|<span data-ttu-id="ed986-148">这是在 TFSTART 之后执行 `GetProcessingRange` 时的状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-148">This is the state on a `GetProcessingRange` that occurs after TFSTART.</span></span> <span data-ttu-id="ed986-149">这指示上次运行未成功完成。</span><span class="sxs-lookup"><span data-stu-id="ed986-149">This indicates that the previous run did not complete successfully.</span></span><br /><br /> <span data-ttu-id="ed986-150">如果使用 _$reprocessing 列，该列设置为 1，指示该包可能在重新处理目标上已存在的行。</span><span class="sxs-lookup"><span data-stu-id="ed986-150">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="ed986-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="ed986-151">ERROR</span></span>|<span data-ttu-id="ed986-152">CDC 组处于 ERROR 状态。</span><span class="sxs-lookup"><span data-stu-id="ed986-152">The CDC group is in an ERROR state.</span></span>|  
  
 <span data-ttu-id="ed986-153">下面是 CDC 状态变量值的示例。</span><span class="sxs-lookup"><span data-stu-id="ed986-153">The following are examples of CDC state variable values.</span></span>  
  
-   <span data-ttu-id="ed986-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="ed986-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="ed986-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="ed986-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="ed986-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span><span class="sxs-lookup"><span data-stu-id="ed986-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span></span>  
  
-   <span data-ttu-id="ed986-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span><span class="sxs-lookup"><span data-stu-id="ed986-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span></span>  
  
-   <span data-ttu-id="ed986-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span><span class="sxs-lookup"><span data-stu-id="ed986-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span></span>  
  
### <a name="to-define-a-cdc-state-variable"></a><span data-ttu-id="ed986-159">定义 CDC 状态变量</span><span class="sxs-lookup"><span data-stu-id="ed986-159">To define a CDC state variable</span></span>  
  
1.  <span data-ttu-id="ed986-160">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，打开具有您需要定义变量的 CDC 流的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="ed986-160">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package that has the CDC flow where you need to define the variable.</span></span>  
  
2.  <span data-ttu-id="ed986-161">单击 **“包资源管理器”** 选项卡并添加新变量。</span><span class="sxs-lookup"><span data-stu-id="ed986-161">Click the **Package Explorer** tab, and add a new variable.</span></span>  
  
3.  <span data-ttu-id="ed986-162">为该变量赋予一个可作为状态变量识别的名称。</span><span class="sxs-lookup"><span data-stu-id="ed986-162">Give the variable a name that you can recognize as your state variable.</span></span>  
  
4.  <span data-ttu-id="ed986-163">为该变量赋予 **“字符串”** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed986-163">Give the variable a **String** data type.</span></span>  
  
 <span data-ttu-id="ed986-164">不要向该变量赋予值来作为其定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed986-164">Do not give the variable a value as part of its definition.</span></span> <span data-ttu-id="ed986-165">该值必须由 CDC 控制任务设置。</span><span class="sxs-lookup"><span data-stu-id="ed986-165">The value must be set by the CDC Control task.</span></span>  
  
 <span data-ttu-id="ed986-166">如果您计划将该 CDC 控制任务用于 **“自动状态持久化”** ，则该 CDC 状态变量将从您指定的数据库状态表中读取并且在其值更改时将更新回该相同的表。</span><span class="sxs-lookup"><span data-stu-id="ed986-166">If you plan to use the CDC Control task with **Automatic State Persistence**, the CDC State variable will be read from the database state table you specify and will be updated back to that same table when its value changes.</span></span> <span data-ttu-id="ed986-167">有关状态表的详细信息，请参阅 [CDC Control Task](../control-flow/cdc-control-task.md)和 [CDC Control Task Editor](../cdc-control-task-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ed986-167">For more information about the State table, see [CDC Control Task](../control-flow/cdc-control-task.md)and [CDC Control Task Editor](../cdc-control-task-editor.md).</span></span>  
  
 <span data-ttu-id="ed986-168">如果您不将该 CDC 控制任务用于“自动状态持久化”，则必须从持久性存储区中加载该变量值，在该持久性存储区中，在上次包运行时保存了该变量值并且在当前处理范围完成后该变量值将写回持久性存储区。</span><span class="sxs-lookup"><span data-stu-id="ed986-168">If you are not using the CDC Control task with Automatic State Persistence then you must load the variable value from persistent storage where its value was saved the last time the package ran and to write it back to the persistent storage when the processing of the current processing range was completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed986-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed986-169">See Also</span></span>  
 <span data-ttu-id="ed986-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span><span class="sxs-lookup"><span data-stu-id="ed986-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span></span>  
 [<span data-ttu-id="ed986-171">CDC 控制任务编辑器</span><span class="sxs-lookup"><span data-stu-id="ed986-171">CDC Control Task Editor</span></span>](../cdc-control-task-editor.md)  
  
  
