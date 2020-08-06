---
title: 维度处理目标编辑器 (高级页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5be80cbbfb6871594d7481ccc0f9444d014885e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590300"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a><span data-ttu-id="dbd38-102">维度处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="dbd38-102">Dimension Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="dbd38-103">可以使用 **“维度处理目标编辑器”** 对话框中的 **“高级”** 页配置错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="dbd38-103">Use the **Advanced** page of the **Dimension Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="dbd38-104">若要了解有关维度处理目标的详细信息，请参阅 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd38-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dbd38-105">选项</span><span class="sxs-lookup"><span data-stu-id="dbd38-105">Options</span></span>  
 <span data-ttu-id="dbd38-106">**使用默认错误配置**</span><span class="sxs-lookup"><span data-stu-id="dbd38-106">**Use default error configuration.**</span></span>  
 <span data-ttu-id="dbd38-107">指定是否使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的默认错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="dbd38-107">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="dbd38-108">此值默认为 `True`。</span><span class="sxs-lookup"><span data-stu-id="dbd38-108">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="dbd38-109">**键错误操作**</span><span class="sxs-lookup"><span data-stu-id="dbd38-109">**Key error action**</span></span>  
 <span data-ttu-id="dbd38-110">指定如何处理包含不可接受的键值的记录。</span><span class="sxs-lookup"><span data-stu-id="dbd38-110">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="dbd38-111">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-111">Value</span></span>|<span data-ttu-id="dbd38-112">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-113">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="dbd38-113">**ConvertToUnknown**</span></span>|<span data-ttu-id="dbd38-114">将不适用的键值转换为 `UnknownMember` 值。</span><span class="sxs-lookup"><span data-stu-id="dbd38-114">Convert the unacceptable key value to the `UnknownMember` value.</span></span>|  
|<span data-ttu-id="dbd38-115">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="dbd38-115">**DiscardRecord**</span></span>|<span data-ttu-id="dbd38-116">放弃记录。</span><span class="sxs-lookup"><span data-stu-id="dbd38-116">Discard the record.</span></span>|  
  
 <span data-ttu-id="dbd38-117">**忽略错误**</span><span class="sxs-lookup"><span data-stu-id="dbd38-117">**Ignore errors**</span></span>  
 <span data-ttu-id="dbd38-118">指定将忽略错误。</span><span class="sxs-lookup"><span data-stu-id="dbd38-118">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="dbd38-119">**出错时停止**</span><span class="sxs-lookup"><span data-stu-id="dbd38-119">**Stop on error**</span></span>  
 <span data-ttu-id="dbd38-120">指定在出现错误时应停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-120">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="dbd38-121">**错误数**</span><span class="sxs-lookup"><span data-stu-id="dbd38-121">**Number of errors**</span></span>  
 <span data-ttu-id="dbd38-122">指定应停止处理的错误阈值（如果选择了“出错时停止”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="dbd38-122">Specify the error threshold at which processing should stop, if you have selected **Stop on errors**.</span></span>  
  
 <span data-ttu-id="dbd38-123">**出错时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="dbd38-123">**On error action**</span></span>  
 <span data-ttu-id="dbd38-124">指定在达到错误阈值时执行的操作（如果选择了“出错时停止”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="dbd38-124">Specify the action to take when the error threshold is reached, if you have selected **Stop on errors**.</span></span>  
  
|<span data-ttu-id="dbd38-125">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-125">Value</span></span>|<span data-ttu-id="dbd38-126">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-127">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="dbd38-127">**StopProcessing**</span></span>|<span data-ttu-id="dbd38-128">停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-128">Stop processing.</span></span>|  
|<span data-ttu-id="dbd38-129">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="dbd38-129">**StopLogging**</span></span>|<span data-ttu-id="dbd38-130">停止记录错误。</span><span class="sxs-lookup"><span data-stu-id="dbd38-130">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="dbd38-131">**找不到键**</span><span class="sxs-lookup"><span data-stu-id="dbd38-131">**Key not found**</span></span>  
 <span data-ttu-id="dbd38-132">指定在出现“找不到键”错误时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="dbd38-132">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="dbd38-133">默认情况下，此值为 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="dbd38-133">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="dbd38-134">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-134">Value</span></span>|<span data-ttu-id="dbd38-135">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-136">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="dbd38-136">**IgnoreError**</span></span>|<span data-ttu-id="dbd38-137">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-137">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-138">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="dbd38-138">**ReportAndContinue**</span></span>|<span data-ttu-id="dbd38-139">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-139">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-140">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="dbd38-140">**ReportAndStop**</span></span>|<span data-ttu-id="dbd38-141">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-141">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="dbd38-142">**重复键**</span><span class="sxs-lookup"><span data-stu-id="dbd38-142">**Duplicate key**</span></span>  
 <span data-ttu-id="dbd38-143">指定在出现“重复键”错误时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="dbd38-143">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="dbd38-144">默认情况下，此值为 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="dbd38-144">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="dbd38-145">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-145">Value</span></span>|<span data-ttu-id="dbd38-146">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-147">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="dbd38-147">**IgnoreError**</span></span>|<span data-ttu-id="dbd38-148">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-148">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-149">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="dbd38-149">**ReportAndContinue**</span></span>|<span data-ttu-id="dbd38-150">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-150">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-151">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="dbd38-151">**ReportAndStop**</span></span>|<span data-ttu-id="dbd38-152">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-152">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="dbd38-153">**空键转换为未知键**</span><span class="sxs-lookup"><span data-stu-id="dbd38-153">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="dbd38-154">指定在将空键转换为 `UnknownMember` 值后所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="dbd38-154">Specify the action to take when a null key has been converted to the `UnknownMember` value.</span></span> <span data-ttu-id="dbd38-155">默认情况下，此值为 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="dbd38-155">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="dbd38-156">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-156">Value</span></span>|<span data-ttu-id="dbd38-157">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-158">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="dbd38-158">**IgnoreError**</span></span>|<span data-ttu-id="dbd38-159">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-159">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-160">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="dbd38-160">**ReportAndContinue**</span></span>|<span data-ttu-id="dbd38-161">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-161">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-162">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="dbd38-162">**ReportAndStop**</span></span>|<span data-ttu-id="dbd38-163">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-163">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="dbd38-164">**不允许空键**</span><span class="sxs-lookup"><span data-stu-id="dbd38-164">**Null key not allowed**</span></span>  
 <span data-ttu-id="dbd38-165">指定在不允许空键而又遇到空键时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="dbd38-165">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="dbd38-166">默认情况下，此值为 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="dbd38-166">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="dbd38-167">值</span><span class="sxs-lookup"><span data-stu-id="dbd38-167">Value</span></span>|<span data-ttu-id="dbd38-168">说明</span><span class="sxs-lookup"><span data-stu-id="dbd38-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbd38-169">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="dbd38-169">**IgnoreError**</span></span>|<span data-ttu-id="dbd38-170">忽略错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-170">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-171">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="dbd38-171">**ReportAndContinue**</span></span>|<span data-ttu-id="dbd38-172">报告错误并继续处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-172">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="dbd38-173">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="dbd38-173">**ReportAndStop**</span></span>|<span data-ttu-id="dbd38-174">报告错误并停止处理。</span><span class="sxs-lookup"><span data-stu-id="dbd38-174">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="dbd38-175">**错误日志路径**</span><span class="sxs-lookup"><span data-stu-id="dbd38-175">**Error log path**</span></span>  
 <span data-ttu-id="dbd38-176">键入错误日志的路径，或单击浏览 (...) 按钮以选择目标\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbd38-176">Type the path of the error log, or click the **browse(...)** button to select a destination.</span></span>  
  
 <span data-ttu-id="dbd38-177">**浏览(...)**</span><span class="sxs-lookup"><span data-stu-id="dbd38-177">**Browse (...)**</span></span>  
 <span data-ttu-id="dbd38-178">选择错误日志的路径。</span><span class="sxs-lookup"><span data-stu-id="dbd38-178">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd38-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbd38-179">See Also</span></span>  
 <span data-ttu-id="dbd38-180">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dbd38-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dbd38-181">[维度处理目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="dbd38-181">[Dimension Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="dbd38-182">维度处理目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="dbd38-182">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  
