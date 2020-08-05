---
title: "\"更改设置\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2649195e3aff4e17d378e54c4b1d656361dfe3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579900"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="9c70a-102">“更改设置”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="9c70a-102">Change Settings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="9c70a-103">使用 **和** 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] “更改设置” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框，可以更改对 **“处理”** 对话框中所列对象的处理进行控制的设置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-103">Use the **Change Settings** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to change the settings that govern the processing of objects listed in the **Process** dialog box.</span></span> <span data-ttu-id="9c70a-104">单击 **“处理”** 对话框中的 **“更改设置”** ，将显示 **“更改设置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9c70a-104">You can display the **Change Settings** dialog box by clicking **Change Settings** on the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c70a-105">此对话框中指定的设置将覆盖从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库继承的“处理”\*\*\*\* 对话框中所列对象的默认设置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-105">Settings specified in this dialog box override default settings inherited from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database for the objects listed in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9c70a-106">选项</span><span class="sxs-lookup"><span data-stu-id="9c70a-106">Options</span></span>  
 <span data-ttu-id="9c70a-107">**处理选项**</span><span class="sxs-lookup"><span data-stu-id="9c70a-107">**Processing options**</span></span>  
 <span data-ttu-id="9c70a-108">使用此选项卡可以修改与处理顺序、写回表和受处理操作影响的对象相关的设置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-108">Use this tab to modify settings related to the processing order, writeback table, and affected objects for the processing operation.</span></span> <span data-ttu-id="9c70a-109">该选项卡包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="9c70a-109">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="9c70a-110">**Parallel**</span><span class="sxs-lookup"><span data-stu-id="9c70a-110">**Parallel**</span></span>  
 <span data-ttu-id="9c70a-111">单击此项可并行处理对象。</span><span class="sxs-lookup"><span data-stu-id="9c70a-111">Click to process the objects in parallel.</span></span>  
  
 <span data-ttu-id="9c70a-112">**最大并行任务数**</span><span class="sxs-lookup"><span data-stu-id="9c70a-112">**Maximum parallel tasks**</span></span>  
 <span data-ttu-id="9c70a-113">选择处理操作并行执行的最大任务数，或选择“让服务器决定”\*\*\*\* 以允许 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 选择并行任务的最佳数量。</span><span class="sxs-lookup"><span data-stu-id="9c70a-113">Select the maximum number of tasks to execute in parallel by the processing operation, or choose **Let the server decide** to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to select an optimal number of parallel tasks.</span></span>  
  
 <span data-ttu-id="9c70a-114">**顺序程序**</span><span class="sxs-lookup"><span data-stu-id="9c70a-114">**Sequential**</span></span>  
 <span data-ttu-id="9c70a-115">单击此项可按顺序处理对象。</span><span class="sxs-lookup"><span data-stu-id="9c70a-115">Click to process the objects sequentially.</span></span>  
  
 <span data-ttu-id="9c70a-116">**事务模式**</span><span class="sxs-lookup"><span data-stu-id="9c70a-116">**Transaction mode**</span></span>  
 <span data-ttu-id="9c70a-117">选择用于按顺序处理对象时使用的事务模式：</span><span class="sxs-lookup"><span data-stu-id="9c70a-117">Choose the transaction mode that is used when objects are processed in sequential order:</span></span>  
  
-   <span data-ttu-id="9c70a-118">**“一项事务”** 在同一个事务中处理所有对象。</span><span class="sxs-lookup"><span data-stu-id="9c70a-118">**One Transaction** processes all objects in the same transaction.</span></span>  
  
-   <span data-ttu-id="9c70a-119">**“单独的事务”** 在单独的事务中处理所有对象（包括依赖对象）。</span><span class="sxs-lookup"><span data-stu-id="9c70a-119">**Separate Transactions** processes all objects, including dependent objects, in separate transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c70a-120">只有在选择了“按顺序”\*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="9c70a-120">This option is enabled only if **Sequential** is selected.</span></span>  
  
 <span data-ttu-id="9c70a-121">**写回表选项**</span><span class="sxs-lookup"><span data-stu-id="9c70a-121">**Writeback table option**</span></span>  
 <span data-ttu-id="9c70a-122">选择用于管理写回表的选项：</span><span class="sxs-lookup"><span data-stu-id="9c70a-122">Choose the option used to manage a writeback table:</span></span>  
  
-   <span data-ttu-id="9c70a-123">如果写回表不存在，选择 **“创建”** 将创建一个写回表；</span><span class="sxs-lookup"><span data-stu-id="9c70a-123">**Create** creates a writeback table if it does not exist.</span></span> <span data-ttu-id="9c70a-124">如果写回表已存在，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-124">An error occurs if a writeback table already exists.</span></span>  
  
-   <span data-ttu-id="9c70a-125">如果写回表不存在，选择 **“始终创建”** 将创建一个写回表；如果写回表已存在，选择此项将会覆盖现有写回表。</span><span class="sxs-lookup"><span data-stu-id="9c70a-125">**Create always** creates a writeback table if it does not exist, or overwrites the existing writeback table if it does exist.</span></span>  
  
-   <span data-ttu-id="9c70a-126">如果写回表已存在，选择 **“使用现有的”** 将使用现有写回表；</span><span class="sxs-lookup"><span data-stu-id="9c70a-126">**Use existing** uses the existing writeback table if it exists.</span></span> <span data-ttu-id="9c70a-127">如果写回表不存在，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-127">An error occurs if a writeback table does not exist.</span></span>  
  
 <span data-ttu-id="9c70a-128">**处理受影响的对象**</span><span class="sxs-lookup"><span data-stu-id="9c70a-128">**Process affected objects**</span></span>  
 <span data-ttu-id="9c70a-129">选择此选项可以包括并处理特定的对象，这些对象依赖于处理操作中所包括的对象。</span><span class="sxs-lookup"><span data-stu-id="9c70a-129">Select to include and process objects that depend on objects included in the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-130">**维度键错误**</span><span class="sxs-lookup"><span data-stu-id="9c70a-130">**Dimension key errors**</span></span>  
 <span data-ttu-id="9c70a-131">使用此选项卡可以修改与处理操作的错误配置相关的设置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-131">Use this tab to modify settings related to the error configuration for the processing operation.</span></span> <span data-ttu-id="9c70a-132">该选项卡包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="9c70a-132">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="9c70a-133">**使用默认错误配置**</span><span class="sxs-lookup"><span data-stu-id="9c70a-133">**Use default error configuration**</span></span>  
 <span data-ttu-id="9c70a-134">选择此选项可以在处理操作中使用对象的默认错误配置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-134">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-135">**使用自定义错误配置**</span><span class="sxs-lookup"><span data-stu-id="9c70a-135">**Use custom error configuration**</span></span>  
 <span data-ttu-id="9c70a-136">选择此选项可以为处理操作中的对象定义错误配置。</span><span class="sxs-lookup"><span data-stu-id="9c70a-136">Select to define the error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-137">**键错误操作**</span><span class="sxs-lookup"><span data-stu-id="9c70a-137">**Key error action**</span></span>  
 <span data-ttu-id="9c70a-138">选择以下操作之一，以便在处理过程中遇到找不到的新键时执行：</span><span class="sxs-lookup"><span data-stu-id="9c70a-138">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="9c70a-139">**“转换为未知”** 将记录信息聚合到未知成员中。</span><span class="sxs-lookup"><span data-stu-id="9c70a-139">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="9c70a-140">**“放弃记录”** 将排除记录信息，以免与对象一起处理。</span><span class="sxs-lookup"><span data-stu-id="9c70a-140">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="9c70a-141">**忽略错误计数**</span><span class="sxs-lookup"><span data-stu-id="9c70a-141">**Ignore errors count**</span></span>  
 <span data-ttu-id="9c70a-142">单击此项可忽略处理过程中发生的任何错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-142">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="9c70a-143">**出错时停止**</span><span class="sxs-lookup"><span data-stu-id="9c70a-143">**Stop on error**</span></span>  
 <span data-ttu-id="9c70a-144">单击此项可在出错时停止处理。</span><span class="sxs-lookup"><span data-stu-id="9c70a-144">Click to stop processing when errors occur.</span></span> <span data-ttu-id="9c70a-145">此选项将启用 **“错误数”** 和 **“出错时要执行的操作”** 选项。</span><span class="sxs-lookup"><span data-stu-id="9c70a-145">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="9c70a-146">**错误数**</span><span class="sxs-lookup"><span data-stu-id="9c70a-146">**Number of errors**</span></span>  
 <span data-ttu-id="9c70a-147">键入处理停止前忽略的错误数。</span><span class="sxs-lookup"><span data-stu-id="9c70a-147">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="9c70a-148">**出错时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="9c70a-148">**On error action**</span></span>  
 <span data-ttu-id="9c70a-149">选择以下操作之一，以便在错误数超出“错误数”\*\*\*\* 中的值时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="9c70a-149">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="9c70a-150">**“停止处理”** 将结束处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-150">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="9c70a-151">**“停止日志记录”** 将停止记录错误，但继续处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-151">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-152">**找不到键**</span><span class="sxs-lookup"><span data-stu-id="9c70a-152">**Key not found**</span></span>  
 <span data-ttu-id="9c70a-153">指定以下操作之一，以便在处理对象的过程中找不到键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="9c70a-153">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="9c70a-154">**“忽略错误”** 将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-154">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="9c70a-155">**“报告并继续”** 将报告错误，并继续该处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-155">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="9c70a-156">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-156">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-157">**重复键**</span><span class="sxs-lookup"><span data-stu-id="9c70a-157">**Duplicate key**</span></span>  
 <span data-ttu-id="9c70a-158">指定以下操作之一，以便在处理对象的过程中发现重复键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="9c70a-158">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="9c70a-159">**“忽略错误”** 将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-159">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="9c70a-160">**“报告并继续”** 将报告错误，并继续该处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-160">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="9c70a-161">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-161">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-162">**空键转换为未知键**</span><span class="sxs-lookup"><span data-stu-id="9c70a-162">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="9c70a-163">指定以下操作之一，以便在处理对象过程中向未知成员添加了空成员键时将执行该操作：</span><span class="sxs-lookup"><span data-stu-id="9c70a-163">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed:</span></span>  
  
-   <span data-ttu-id="9c70a-164">**“忽略错误”** 将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-164">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="9c70a-165">**“报告并继续”** 将报告错误，并继续该处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-165">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="9c70a-166">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-166">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-167">**不允许空键**</span><span class="sxs-lookup"><span data-stu-id="9c70a-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="9c70a-168">指定以下操作之一，以便在处理对象过程中发现了不允许的空键时将执行该操作：</span><span class="sxs-lookup"><span data-stu-id="9c70a-168">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed:</span></span>  
  
-   <span data-ttu-id="9c70a-169">**“忽略错误”** 将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="9c70a-169">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="9c70a-170">**“报告并继续”** 将报告错误，并继续该处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-170">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="9c70a-171">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="9c70a-171">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="9c70a-172">**错误日志路径**</span><span class="sxs-lookup"><span data-stu-id="9c70a-172">**Error log path**</span></span>  
 <span data-ttu-id="9c70a-173">键入错误日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9c70a-173">Type the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="9c70a-174">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="9c70a-174">**Browse**</span></span>  
 <span data-ttu-id="9c70a-175">单击此项以打开“打开”\*\*\*\* 对话框，然后选择错误日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9c70a-175">Click to open the **Open** dialog box and select the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="9c70a-176">**处理受影响的对象**</span><span class="sxs-lookup"><span data-stu-id="9c70a-176">**Process affected objects**</span></span>  
 <span data-ttu-id="9c70a-177">单击此项可处理与“处理”\*\*\*\* 对话框中的所选对象存在依赖关系的对象。</span><span class="sxs-lookup"><span data-stu-id="9c70a-177">Click to process the objects that have a dependency on the objects selected in the **Process** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c70a-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c70a-178">See Also</span></span>  
 <span data-ttu-id="9c70a-179">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="9c70a-179">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="9c70a-180">"处理" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="9c70a-180">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
