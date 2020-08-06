---
title: " (XMLA) 执行批处理操作 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69899077cf534482879accbf10640f6295e3866a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578506"
---
# <a name="performing-batch-operations-xmla"></a><span data-ttu-id="4a948-102">执行批处理操作 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="4a948-102">Performing Batch Operations (XMLA)</span></span>
  <span data-ttu-id="4a948-103">您可以使用 XML for Analysis (XMLA) 中的[批处理](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)命令，使用单个 xmla [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法运行多个 xmla 命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-103">You can use the [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command in XML for Analysis (XMLA) to run multiple XMLA commands using a single XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span> <span data-ttu-id="4a948-104">可以作为单个事务或者每个命令为一个事务，以串行或并行方式运行 `Batch` 命令中包含的多个命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-104">You can run multiple commands contained in the `Batch` command either as a single transaction or in individual transactions for each command, in serial or in parallel.</span></span> <span data-ttu-id="4a948-105">你还可以在 `Batch` 用于处理多个对象的命令中指定连线外绑定和其他属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4a948-105">You can also specify out-of-line bindings and other properties in the `Batch` command for processing multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a><span data-ttu-id="4a948-106">运行事务性和非事务性 Batch 命令</span><span class="sxs-lookup"><span data-stu-id="4a948-106">Running Transactional and Nontransactional Batch Commands</span></span>  
 <span data-ttu-id="4a948-107">`Batch` 以下列两种方式之一执行命令：</span><span class="sxs-lookup"><span data-stu-id="4a948-107">The `Batch` command executes commands in one of two ways:</span></span>  
  
 <span data-ttu-id="4a948-108">**事务性**</span><span class="sxs-lookup"><span data-stu-id="4a948-108">**Transactional**</span></span>  
 <span data-ttu-id="4a948-109">如果 `Transaction` 将命令的属性 `Batch` 设置为 true，则命令将命令 `Batch` 中包含的所有命令都包含 `Batch` 在一个事务中。 *transactional*</span><span class="sxs-lookup"><span data-stu-id="4a948-109">If the `Transaction` attribute of the `Batch` command is set to true, the `Batch` command run commands all of the commands contained by the `Batch` command in a single transaction-a *transactional* batch.</span></span>  
  
 <span data-ttu-id="4a948-110">如果事务批次中有任何命令失败，则回滚命令中运行的命令，该命令将在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Batch` 失败的命令之前运行，并且该命令会 `Batch` 立即结束。</span><span class="sxs-lookup"><span data-stu-id="4a948-110">If any command fails in a transactional batch, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back any command in the `Batch` command that ran before the command that failed and the `Batch` command immediately ends.</span></span> <span data-ttu-id="4a948-111">`Batch` 命令中尚未运行的任何命令都不再执行。</span><span class="sxs-lookup"><span data-stu-id="4a948-111">Any commands in the `Batch` command that have not yet run are not executed.</span></span> <span data-ttu-id="4a948-112">`Batch` 命令结束后，`Batch` 命令将报告失败命令发生的所有错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-112">After the `Batch` command ends, the `Batch` command reports any errors that occurred for the failed command.</span></span>  
  
 <span data-ttu-id="4a948-113">**处理**</span><span class="sxs-lookup"><span data-stu-id="4a948-113">**Nontransactional**</span></span>  
 <span data-ttu-id="4a948-114">如果该 `Transaction` 特性设置为 false，则该 `Batch` 命令将在单独的事务中运行该命令所包含的每个命令 `Batch` -非*事务性*批处理。</span><span class="sxs-lookup"><span data-stu-id="4a948-114">If the `Transaction` attribute is set to false, the `Batch` command runs each command contained by the `Batch` command in a separate transaction-a *nontransactional* batch.</span></span> <span data-ttu-id="4a948-115">如果非事务性批处理中的任一命令失败，`Batch` 命令会继续执行失败命令后的命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-115">If any command fails in a nontransactional batch, the `Batch` command continues to run commands after the command which failed.</span></span> <span data-ttu-id="4a948-116">`Batch` 命令尝试运行 `Batch` 命令包含的所有命令后，`Batch` 命令将报告发生的所有错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-116">After the `Batch` command tries to run all the commands that the `Batch` command contains, the `Batch` command reports any errors that occurred.</span></span>  
  
 <span data-ttu-id="4a948-117">`Batch` 命令中包含的各命令返回的所有结果以这些命令包含在 `Batch` 命令中的顺序返回。</span><span class="sxs-lookup"><span data-stu-id="4a948-117">All results returned by commands contained in a `Batch` command are returned in the same order in which the commands are contained in the `Batch` command.</span></span> <span data-ttu-id="4a948-118">`Batch` 命令返回的结果根据 `Batch` 命令是事务性的还是非事务性的而不同。</span><span class="sxs-lookup"><span data-stu-id="4a948-118">The results returned by a `Batch` command vary based on whether the `Batch` command is transactional or nontransactional.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a948-119">如果 `Batch` 命令包含不返回输出的命令（如[Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)命令），并且该命令成功运行，则该 `Batch` 命令将返回 results 元素中的空[根](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="4a948-119">If a `Batch` command contains a command that does not return output, such as the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) command, and that command successfully runs, the `Batch` command returns an empty [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element within the results element.</span></span> <span data-ttu-id="4a948-120">空的 `root` 元素可确保 `Batch` 命令中包含的每个命令都与该命令的结果的相应 `root` 元素匹配。</span><span class="sxs-lookup"><span data-stu-id="4a948-120">The empty `root` element ensures that each command contained in a `Batch` command can be matched with the appropriate `root` element for that command's results.</span></span>  
  
### <a name="returning-results-from-transactional-batch-results"></a><span data-ttu-id="4a948-121">从事务性批处理结果返回结果</span><span class="sxs-lookup"><span data-stu-id="4a948-121">Returning Results from Transactional Batch Results</span></span>  
 <span data-ttu-id="4a948-122">只有在整个 `Batch` 命令全部完成之后，才会从事务性批处理中运行的命令返回结果。</span><span class="sxs-lookup"><span data-stu-id="4a948-122">Results from commands run within a transactional batch are not returned until the entire `Batch` command is completed.</span></span> <span data-ttu-id="4a948-123">由于事务性批处理中任一命令失败将导致整个 `Batch` 命令及其包含的所有命令都回滚，因此不在每个命令运行后返回结果。</span><span class="sxs-lookup"><span data-stu-id="4a948-123">The results are not returned after each command runs because any command that fails within a transactional batch would cause the entire `Batch` command and all containing commands to be rolled back.</span></span> <span data-ttu-id="4a948-124">如果所有命令都成功启动并运行，则由命令的方法返回的[ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse)元素的[return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla)元素 `Execute` `Batch` 包含一个[results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla)元素，该元素 `root` 为命令中包含的每个成功运行的命令包含一个元素 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-124">If all commands start and run successfully, the [return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) element of the [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) element returned by the `Execute` method for the `Batch` command contains one [results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) element, which in turn contains one `root` element for each successfully run command contained in the `Batch` command.</span></span> <span data-ttu-id="4a948-125">如果 `Batch` 命令中的任一命令无法启动或完成，`Execute` 方法将为 `Batch` 命令返回一个 SOAP 错误，其中包含失败命令的错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-125">If any command in the `Batch` command cannot be started or fails to complete, the `Execute` method returns a SOAP fault for the `Batch` command that contains the error of the command that failed.</span></span>  
  
### <a name="returning-results-from-nontransactional-batch-results"></a><span data-ttu-id="4a948-126">从非事务性批处理结果返回结果</span><span class="sxs-lookup"><span data-stu-id="4a948-126">Returning Results from Nontransactional Batch Results</span></span>  
 <span data-ttu-id="4a948-127">从非事务性批处理中运行的命令返回的结果以这些命令在 `Batch` 命令中的顺序返回，并且在每个命令返回结果时即将该结果返回。</span><span class="sxs-lookup"><span data-stu-id="4a948-127">Results from commands run within a nontransactional batch are returned in the order in which the commands are contained within the `Batch` command and as they are returned by each command.</span></span> <span data-ttu-id="4a948-128">如果 `Batch` 命令中包含的命令都无法成功启动，`Execute` 方法将返回包含 `Batch` 命令的错误的 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-128">If no command contained in the `Batch` command can be successfully started, the `Execute` method returns a SOAP fault that contains an error for the `Batch` command.</span></span> <span data-ttu-id="4a948-129">如果至少一个命令成功启动，则由 `return` 命令的 `ExecuteResponse` 方法返回的 `Execute` 元素的 `Batch` 元素将包含一个 `results` 元素，该元素为 `root` 命令中包含的每个命令包含一个 `Batch` 元素。</span><span class="sxs-lookup"><span data-stu-id="4a948-129">If at least one command is successfully started, the `return` element of the `ExecuteResponse` element returned by the `Execute` method for the `Batch` command contains one `results` element, which in turn contains one `root` element for each command contained in the `Batch` command.</span></span> <span data-ttu-id="4a948-130">如果非事务性批处理中的一个或多个命令无法启动或无法完成，则 `root` 该失败命令的元素包含描述错误的[错误](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="4a948-130">If one or more commands in a nontransactional batch cannot be started or fails to complete, the `root` element for that failed command contains an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) element describing the error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a948-131">只要非事务性批处理中至少有一个命令能够启动，就认为该非事务性批处理成功运行，即使该非事务性批处理中包含的每个命令都在 `Batch` 命令的结果中返回错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-131">As long as at least one command in a nontransactional batch can be started, the nontransactional batch is considered to have successfully run, even if every command contained in the nontransactional batch returns an error in the results of the `Batch` command.</span></span>  
  
## <a name="using-serial-and-parallel-execution"></a><span data-ttu-id="4a948-132">使用串行和并行执行</span><span class="sxs-lookup"><span data-stu-id="4a948-132">Using Serial and Parallel Execution</span></span>  
 <span data-ttu-id="4a948-133">可以使用 `Batch` 命令以串行或并行方式运行所包含的命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-133">You can use the `Batch` command to run included commands in serial or in parallel.</span></span> <span data-ttu-id="4a948-134">以串行方式运行命令时，`Batch` 命令中包含的下一个命令必须等 `Batch` 命令中当前运行的命令完成后才能启动。</span><span class="sxs-lookup"><span data-stu-id="4a948-134">When the commands are run in serial, the next command included in the `Batch` command cannot start until the currently running command in the `Batch` command is completed.</span></span> <span data-ttu-id="4a948-135">以并行方式运行命令时，`Batch` 命令可以同时执行多个命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-135">When the commands are run in parallel, multiple commands can be executed simultaneously by the `Batch` command.</span></span>  
  
 <span data-ttu-id="4a948-136">若要以并行方式运行命令，请添加要以并行方式运行命令的[并行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla)属性的命令 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-136">To run commands in parallel, you add the commands to be run in parallel to the [Parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) property of the `Batch` command.</span></span> <span data-ttu-id="4a948-137">目前，只能 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 并行运行连续的顺序[过程](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-137">Currently, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] can run only contiguous, sequential [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) commands in parallel.</span></span> <span data-ttu-id="4a948-138">属性中包含的任何其他 XMLA 命令（如[Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)或[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)） `Parallel` 都将按顺序运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-138">Any other XMLA command, such as [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) or [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), included in the `Parallel` property is run serially.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="4a948-139">尝试以并行方式运行包含在 `Process` 属性中的所有 `Parallel` 命令，但是不保证包含的所有 `Process` 命令都能以并行方式运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-139">tries to run all `Process` commands included in the `Parallel` property in parallel, but cannot guarantee that all included `Process` commands can be run in parallel.</span></span> <span data-ttu-id="4a948-140">实例会分析每个 `Process` 命令，如果实例确定命令不能以并行方式执行，则 `Process` 命令将以串行方式执行。</span><span class="sxs-lookup"><span data-stu-id="4a948-140">The instance analyzes each `Process` command and, if the instance determines that the command cannot be run in parallel, the `Process` command is run in serial.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a948-141">若要以并行方式执行命令，`Transaction` 命令的 `Batch` 属性必须设置为 true，因为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 仅支持每个连接一个活动事务且非事务性批处理在单独的事务中执行每个命令。</span><span class="sxs-lookup"><span data-stu-id="4a948-141">To run commands in parallel, the `Transaction` attribute of the `Batch` command must be set to true because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports only one active transaction per connection and nontransactional batches run each command in a separate transaction.</span></span> <span data-ttu-id="4a948-142">如果在非事务性批处理中包含 `Parallel` 属性，则将出现错误。</span><span class="sxs-lookup"><span data-stu-id="4a948-142">If you include the `Parallel` property in a nontransactional batch, an error occurs.</span></span>  
  
### <a name="limiting-parallel-execution"></a><span data-ttu-id="4a948-143">限制并行执行</span><span class="sxs-lookup"><span data-stu-id="4a948-143">Limiting Parallel Execution</span></span>  
 <span data-ttu-id="4a948-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例并行运行尽可能多的 `Process` 命令，直到达到运行实例的计算机的限制。</span><span class="sxs-lookup"><span data-stu-id="4a948-144">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance tries to run as many `Process` commands in parallel as possible, up to the limits of the computer on which the instance runs.</span></span> <span data-ttu-id="4a948-145">将 `Process` 属性的 `maxParallel` 特性设为指示可并发执行的最大 `Parallel` 命令数，可限制同时执行的 `Process` 命令数。</span><span class="sxs-lookup"><span data-stu-id="4a948-145">You can limit the number of concurrently executing `Process` commands by setting the `maxParallel` attribute of the `Parallel` property to a value indicating the maximum number of `Process` commands that can be run in parallel.</span></span>  
  
 <span data-ttu-id="4a948-146">例如，`Parallel` 属性按列出的顺序包含以下命令：</span><span class="sxs-lookup"><span data-stu-id="4a948-146">For example, a `Parallel` property contains the following commands in the sequence listed:</span></span>  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 <span data-ttu-id="4a948-147">此 `maxParalle` 属性的 `Parallel`l 特性设置为 2。</span><span class="sxs-lookup"><span data-stu-id="4a948-147">The `maxParalle`l attribute of this `Parallel` property is set to 2.</span></span> <span data-ttu-id="4a948-148">因此，实例按照以下列表中所述，运行前面列表中的命令：</span><span class="sxs-lookup"><span data-stu-id="4a948-148">Therefore, the instance runs the previous lists of commands as described in the following list:</span></span>  
  
-   <span data-ttu-id="4a948-149">命令 1 以串行方式运行，因为命令 1 是 `Create` 命令，而只有 `Process` 命令能以并行方式运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-149">Command 1 runs serially because command 1 is a `Create` command and only `Process` commands can be run in parallel.</span></span>  
  
-   <span data-ttu-id="4a948-150">命令2在命令1完成后连续运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-150">Command 2 runs serially after command 1 is completed.</span></span>  
  
-   <span data-ttu-id="4a948-151">命令3在命令2完成后连续运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-151">Command 3 runs serially after command 2 is completed.</span></span>  
  
-   <span data-ttu-id="4a948-152">在命令3完成后，4和5命令将并行运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-152">Commands 4 and 5 run in parallel after command 3 is completed.</span></span> <span data-ttu-id="4a948-153">虽然命令 6 也是 `Process` 命令，但是命令 6 不能与命令 4 和 5 并行运行，因为 `maxParallel` 属性设置为 2。</span><span class="sxs-lookup"><span data-stu-id="4a948-153">Although command 6 is also a `Process` command, command 6 cannot run in parallel with commands 4 and 5 because the `maxParallel` property is set to 2.</span></span>  
  
-   <span data-ttu-id="4a948-154">命令 6 以串行方式在命令 4 和 5 都完成后运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-154">Command 6 runs serially after both commands 4 and 5 are completed.</span></span>  
  
-   <span data-ttu-id="4a948-155">命令 7 以串行方式在命令 6 完成后运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-155">Command 7 runs serially after command 6 is completed.</span></span>  
  
-   <span data-ttu-id="4a948-156">命令 8 和 9 以并行方式在命令 7 完成后运行。</span><span class="sxs-lookup"><span data-stu-id="4a948-156">Commands 8 and 9 run in parallel after command 7 is completed.</span></span>  
  
## <a name="using-the-batch-command-to-process-objects"></a><span data-ttu-id="4a948-157">使用 Batch 命令处理对象</span><span class="sxs-lookup"><span data-stu-id="4a948-157">Using the Batch Command to Process Objects</span></span>  
 <span data-ttu-id="4a948-158">`Batch` 命令包含多个专门用于支持处理多个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的可选属性和特性：</span><span class="sxs-lookup"><span data-stu-id="4a948-158">The `Batch` command contains several optional properties and attributes specifically included to support processing multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects:</span></span>  
  
-   <span data-ttu-id="4a948-159">`ProcessAffectedObjects` 命令的 `Batch` 特性指示实例是否还应对作为 `Process` 命令中包含的处理特定对象的 `Batch` 命令的结果而需要重新处理的所有对象进行处理。</span><span class="sxs-lookup"><span data-stu-id="4a948-159">The `ProcessAffectedObjects` attribute of the `Batch` command indicates whether the instance should also process any object that requires reprocessing as a result of a `Process` command included in the `Batch` command processing a specified object.</span></span>  
  
-   <span data-ttu-id="4a948-160">[Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)属性包含命令中的所有命令所使用的一系列外绑定 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-160">The [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) property contains a collection of out-of-line bindings used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="4a948-161">[DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)属性包含命令中的所有命令所使用的数据源的外绑定 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-161">The [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property contains an out-of-line binding for a data source used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="4a948-162">[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)属性包含命令中的所有命令所使用的数据源视图的外绑定 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-162">The [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) property contains an out-of-line binding for a data source view used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="4a948-163">[ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)属性指定该 `Batch` 命令处理 `Process` 命令中包含的所有命令所遇到的错误的方式 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="4a948-163">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property specifies the way in which the `Batch` command handles errors encountered by all `Process` commands contained in the `Batch` command.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a948-164">如果 `Process` 命令包含在 `Bindings` 命令中，则 `DataSource` 命令不能包含 `DataSourceView`、`ErrorConfiguration`、`Process` 或 `Batch` 属性。</span><span class="sxs-lookup"><span data-stu-id="4a948-164">A `Process` command cannot include the `Bindings`, `DataSource`, `DataSourceView`, or `ErrorConfiguration` properties, if the `Process` command is contained in a `Batch` command.</span></span> <span data-ttu-id="4a948-165">如果必须为 `Process` 命令指定这些属性，请在包含 `Batch` 命令的 `Process` 命令的相应属性中提供必要的信息。</span><span class="sxs-lookup"><span data-stu-id="4a948-165">If you must specify these properties for a `Process` command, provide the necessary information in the corresponding properties of the `Batch` command that contains the `Process` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a948-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a948-166">See Also</span></span>  
 <span data-ttu-id="4a948-167">[&#40;XMLA&#41;的批处理元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="4a948-167">[Batch Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span></span>  
 <span data-ttu-id="4a948-168">[XMLA &#40;处理元素&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="4a948-168">[Process Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span></span>  
 <span data-ttu-id="4a948-169">[多维模型对象处理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="4a948-169">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="4a948-170">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="4a948-170">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
