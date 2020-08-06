---
title: "\" (挖掘结构的错误配置\" 对话框)  (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5eb41da36400271a9b058ecf275d26bd22d3ee53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591625"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="614a8-102">错误配置（“挖掘结构”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="614a8-102">Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="614a8-103">可以使用 **SQL Server Management Studio** 中的 **“挖掘结构属性”** 对话框的 **“错误配置”** 页，设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的挖掘结构的错误配置属性。</span><span class="sxs-lookup"><span data-stu-id="614a8-103">Use the **Error Configuration** page of the **Mining Structure Properties** dialog box in **SQL Server Management Studio** to set the error configuration properties of a mining structure in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="614a8-104">选项</span><span class="sxs-lookup"><span data-stu-id="614a8-104">Options</span></span>  
 <span data-ttu-id="614a8-105">**使用默认错误配置**</span><span class="sxs-lookup"><span data-stu-id="614a8-105">**Use default error configuration**</span></span>  
 <span data-ttu-id="614a8-106">选择此选项可以在处理操作中使用对象的默认错误配置。</span><span class="sxs-lookup"><span data-stu-id="614a8-106">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-107">**键错误操作**</span><span class="sxs-lookup"><span data-stu-id="614a8-107">**Key error action**</span></span>  
 <span data-ttu-id="614a8-108">选择以下操作之一，以便在处理过程中遇到找不到的新键时执行：</span><span class="sxs-lookup"><span data-stu-id="614a8-108">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="614a8-109">**“转换为未知”** 将记录信息聚合到未知成员中。</span><span class="sxs-lookup"><span data-stu-id="614a8-109">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="614a8-110">**“放弃记录”** 将排除记录信息，以免与对象一起处理。</span><span class="sxs-lookup"><span data-stu-id="614a8-110">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="614a8-111">**忽略错误计数**</span><span class="sxs-lookup"><span data-stu-id="614a8-111">**Ignore errors count**</span></span>  
 <span data-ttu-id="614a8-112">单击此项可忽略处理过程中发生的任何错误。</span><span class="sxs-lookup"><span data-stu-id="614a8-112">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="614a8-113">**出错时停止**</span><span class="sxs-lookup"><span data-stu-id="614a8-113">**Stop on error**</span></span>  
 <span data-ttu-id="614a8-114">单击此项可在出错时停止处理。</span><span class="sxs-lookup"><span data-stu-id="614a8-114">Click to stop processing when errors occur.</span></span> <span data-ttu-id="614a8-115">此选项将启用 **“错误数”** 和 **“出错时要执行的操作”** 选项。</span><span class="sxs-lookup"><span data-stu-id="614a8-115">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="614a8-116">**错误数**</span><span class="sxs-lookup"><span data-stu-id="614a8-116">**Number of errors**</span></span>  
 <span data-ttu-id="614a8-117">键入处理停止前忽略的错误数。</span><span class="sxs-lookup"><span data-stu-id="614a8-117">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="614a8-118">**出错时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="614a8-118">**On error action**</span></span>  
 <span data-ttu-id="614a8-119">选择以下操作之一，以便在错误数超出“错误数”\*\*\*\* 中的值时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="614a8-119">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="614a8-120">**“停止处理”** 将结束处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-120">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="614a8-121">**“停止日志记录”** 将停止记录错误，但继续处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-121">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-122">**找不到键**</span><span class="sxs-lookup"><span data-stu-id="614a8-122">**Key not found**</span></span>  
 <span data-ttu-id="614a8-123">指定以下操作之一，以便在处理对象的过程中找不到键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="614a8-123">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="614a8-124">**忽略错误**忽略错误</span><span class="sxs-lookup"><span data-stu-id="614a8-124">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="614a8-125">**报告并继续**报告错误并继续处理操作</span><span class="sxs-lookup"><span data-stu-id="614a8-125">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="614a8-126">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-126">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-127">**重复键**</span><span class="sxs-lookup"><span data-stu-id="614a8-127">**Duplicate key**</span></span>  
 <span data-ttu-id="614a8-128">指定以下操作之一，以便在处理对象的过程中发现重复键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="614a8-128">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="614a8-129">**忽略错误**忽略错误</span><span class="sxs-lookup"><span data-stu-id="614a8-129">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="614a8-130">**报告并继续**报告错误并继续处理操作</span><span class="sxs-lookup"><span data-stu-id="614a8-130">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="614a8-131">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-131">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-132">**空键转换为未知键**</span><span class="sxs-lookup"><span data-stu-id="614a8-132">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="614a8-133">指定以下操作之一，以便在处理对象的过程中向未知成员添加 Null 成员键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="614a8-133">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed.</span></span>  
  
-   <span data-ttu-id="614a8-134">**忽略错误**忽略错误</span><span class="sxs-lookup"><span data-stu-id="614a8-134">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="614a8-135">**报告并继续**报告错误并继续处理操作</span><span class="sxs-lookup"><span data-stu-id="614a8-135">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="614a8-136">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-136">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-137">**不允许空键**</span><span class="sxs-lookup"><span data-stu-id="614a8-137">**Null key not allowed**</span></span>  
 <span data-ttu-id="614a8-138">指定以下操作之一，以便在处理对象的过程中发现不允许的 Null 键时执行该操作：</span><span class="sxs-lookup"><span data-stu-id="614a8-138">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed.</span></span>  
  
-   <span data-ttu-id="614a8-139">**忽略错误**忽略错误</span><span class="sxs-lookup"><span data-stu-id="614a8-139">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="614a8-140">**报告并继续**报告错误并继续处理操作</span><span class="sxs-lookup"><span data-stu-id="614a8-140">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="614a8-141">**“报告并停止”** ，报告该错误并停止处理操作。</span><span class="sxs-lookup"><span data-stu-id="614a8-141">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="614a8-142">**错误日志路径**</span><span class="sxs-lookup"><span data-stu-id="614a8-142">**Error log path**</span></span>  
 <span data-ttu-id="614a8-143">键入错误日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="614a8-143">Type the full path and file name for the error log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="614a8-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="614a8-144">See Also</span></span>  
 <span data-ttu-id="614a8-145">["挖掘结构属性" 对话框 &#40;Analysis Services 数据挖掘&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="614a8-145">[Mining Structure Properties Dialog &#40;Analysis Services - Data Mining&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="614a8-146">"常规 &#40;挖掘结构" 对话框&#41; &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="614a8-146">General &#40;Mining Structure Dialog Box&#41; &#40;Analysis Services - Data Mining&#41;</span></span>](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  
