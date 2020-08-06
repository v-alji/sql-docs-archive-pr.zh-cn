---
title: 分区处理目标编辑器 (高级页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12845ecd644eabd949ea37fbb18ba6cc9cf342f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578291"
---
# <a name="partition-processing-destination-editor-advanced-page"></a><span data-ttu-id="a8ce8-102">分区处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="a8ce8-102">Partition Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="a8ce8-103">可以使用 **“分区处理目标编辑器”** 对话框的 **“高级”** 页配置错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-103">Use the **Advanced** page of the **Partition Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="a8ce8-104">若要了解有关分区处理目标的详细信息，请参阅 [Partition Processing Destination](data-flow/partition-processing-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-104">To learn more about the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8ce8-105">此处所述的任何不适用于 Analysis Services 表格模型。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="a8ce8-106">你无法将输入列映射到表格模型的分区列。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="a8ce8-107">您可以改用 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 处理分区。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a8ce8-108">选项</span><span class="sxs-lookup"><span data-stu-id="a8ce8-108">Options</span></span>  
 <span data-ttu-id="a8ce8-109">**使用默认错误配置**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-109">**Use default error configuration.**</span></span>  
 <span data-ttu-id="a8ce8-110">指定是否使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的默认错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-110">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="a8ce8-111">此值默认为 `True`。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-111">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="a8ce8-112">**键错误操作**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-112">**Key error action**</span></span>  
 <span data-ttu-id="a8ce8-113">指定如何处理包含不可接受的键值的记录。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-113">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="a8ce8-114">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-114">Value</span></span>|<span data-ttu-id="a8ce8-115">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-116">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-116">**ConvertToUnknown**</span></span>|<span data-ttu-id="a8ce8-117">将无法接受的键值转换为 Unknown 值。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-117">Convert the unacceptable key value to the Unknown value.</span></span>|  
|<span data-ttu-id="a8ce8-118">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-118">**DiscardRecord**</span></span>|<span data-ttu-id="a8ce8-119">放弃记录。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-119">Discard the record.</span></span>|  
  
 <span data-ttu-id="a8ce8-120">**忽略错误**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-120">**Ignore errors**</span></span>  
 <span data-ttu-id="a8ce8-121">指定将忽略错误。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-121">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="a8ce8-122">**出错时停止**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-122">**Stop on error**</span></span>  
 <span data-ttu-id="a8ce8-123">指定在出现错误时应停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-123">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="a8ce8-124">**错误数**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-124">**Number of errors**</span></span>  
 <span data-ttu-id="a8ce8-125">如果选择了“出错时停止”\*\*\*\*，请指定应停止处理的错误阈值。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-125">Specify the error threshold at which processing should stop, if you have selected **Stop on error**.</span></span>  
  
 <span data-ttu-id="a8ce8-126">**出错时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-126">**On error action**</span></span>  
 <span data-ttu-id="a8ce8-127">如果选择了“出错时停止”\*\*\*\*，请指定在达到错误阈值时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-127">Specify the action to take when the error threshold is reached, if you have selected **Stop on error**.</span></span>  
  
|<span data-ttu-id="a8ce8-128">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-128">Value</span></span>|<span data-ttu-id="a8ce8-129">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-130">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-130">**StopProcessing**</span></span>|<span data-ttu-id="a8ce8-131">停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-131">Stop processing.</span></span>|  
|<span data-ttu-id="a8ce8-132">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-132">**StopLogging**</span></span>|<span data-ttu-id="a8ce8-133">停止记录错误。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-133">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="a8ce8-134">**找不到键**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-134">**Key not found**</span></span>  
 <span data-ttu-id="a8ce8-135">指定在出现“找不到键”错误时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-135">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="a8ce8-136">默认情况下，此值为 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-136">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="a8ce8-137">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-137">Value</span></span>|<span data-ttu-id="a8ce8-138">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-139">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-139">**IgnoreError**</span></span>|<span data-ttu-id="a8ce8-140">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-140">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-141">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-141">**ReportAndContinue**</span></span>|<span data-ttu-id="a8ce8-142">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-142">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-143">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-143">**ReportAndStop**</span></span>|<span data-ttu-id="a8ce8-144">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-144">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="a8ce8-145">**重复键**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-145">**Duplicate key**</span></span>  
 <span data-ttu-id="a8ce8-146">指定在出现“重复键”错误时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-146">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="a8ce8-147">默认情况下，此值为 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-147">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="a8ce8-148">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-148">Value</span></span>|<span data-ttu-id="a8ce8-149">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-150">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-150">**IgnoreError**</span></span>|<span data-ttu-id="a8ce8-151">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-151">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-152">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-152">**ReportAndContinue**</span></span>|<span data-ttu-id="a8ce8-153">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-153">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-154">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-154">**ReportAndStop**</span></span>|<span data-ttu-id="a8ce8-155">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-155">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="a8ce8-156">**空键转换为未知键**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-156">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="a8ce8-157">指定在将空键转换为 Unknown 值后所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-157">Specify the action to take when a null key has been converted to the Unknown value.</span></span> <span data-ttu-id="a8ce8-158">默认情况下，此值为 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-158">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="a8ce8-159">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-159">Value</span></span>|<span data-ttu-id="a8ce8-160">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-161">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-161">**IgnoreError**</span></span>|<span data-ttu-id="a8ce8-162">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-162">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-163">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-163">**ReportAndContinue**</span></span>|<span data-ttu-id="a8ce8-164">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-164">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-165">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-165">**ReportAndStop**</span></span>|<span data-ttu-id="a8ce8-166">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-166">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="a8ce8-167">**不允许空键**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="a8ce8-168">指定在不允许空键而又遇到空键时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-168">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="a8ce8-169">默认情况下，此值为 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-169">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="a8ce8-170">值</span><span class="sxs-lookup"><span data-stu-id="a8ce8-170">Value</span></span>|<span data-ttu-id="a8ce8-171">说明</span><span class="sxs-lookup"><span data-stu-id="a8ce8-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ce8-172">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-172">**IgnoreError**</span></span>|<span data-ttu-id="a8ce8-173">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-173">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-174">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-174">**ReportAndContinue**</span></span>|<span data-ttu-id="a8ce8-175">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-175">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="a8ce8-176">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-176">**ReportAndStop**</span></span>|<span data-ttu-id="a8ce8-177">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-177">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="a8ce8-178">**错误日志路径**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-178">**Error log path**</span></span>  
 <span data-ttu-id="a8ce8-179">键入错误日志的路径，或者使用浏览按钮 **(...)** 选择目标。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-179">Type the path for the error log, or select a destination by using the browse **(...)** button.</span></span>  
  
 <span data-ttu-id="a8ce8-180">**浏览(...)**</span><span class="sxs-lookup"><span data-stu-id="a8ce8-180">**Browse (...)**</span></span>  
 <span data-ttu-id="a8ce8-181">选择错误日志的路径。</span><span class="sxs-lookup"><span data-stu-id="a8ce8-181">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ce8-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8ce8-182">See Also</span></span>  
 <span data-ttu-id="a8ce8-183">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a8ce8-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="a8ce8-184">分区处理目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="a8ce8-184">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
