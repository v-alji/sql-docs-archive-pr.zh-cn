---
title: " (基本数据挖掘教程) 指定数据类型和内容类型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 73ff61dbe439b9f2fb50f3a8004f4e7bcad8369a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691377"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a><span data-ttu-id="876e2-102">指定数据类型和内容类型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="876e2-102">Specifying the Data Type and Content Type (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="876e2-103">您已选择了用于生成结构和为模型定型的列，现在可以对向导设置的默认数据类型和内容类型进行任何必要的更改。</span><span class="sxs-lookup"><span data-stu-id="876e2-103">Now that you have selected which columns to use for building your structure and training your models, make any necessary changes to the default data and content types that are set by the wizard.</span></span>  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a><span data-ttu-id="876e2-104">检查和修改每列的内容类型和数据类型</span><span class="sxs-lookup"><span data-stu-id="876e2-104">Review and modify content type and data type for each column</span></span>  
  
1.  <span data-ttu-id="876e2-105">在 "**指定列的内容和数据类型"** 页上，单击 "**检测**" 运行确定每个列的默认数据和内容类型的算法。</span><span class="sxs-lookup"><span data-stu-id="876e2-105">On the **Specify Columns' Content and Data Type** page, click **Detect** to run an algorithm that determines the default data and content types for each column.</span></span>  
  
2.  <span data-ttu-id="876e2-106">查看 "**内容类型**" 和 "**数据类型**" 列中的条目，并根据需要对其进行更改，以确保设置与下表中列出的设置相同。</span><span class="sxs-lookup"><span data-stu-id="876e2-106">Review the entries in the **Content Type** and **Data Type** columns and change them if necessary, to make sure that the settings are the same as those listed in the following table.</span></span>  
  
     <span data-ttu-id="876e2-107">通常，向导会检测数值，并分配相应的数值数据类型；但有些情况下，您可能想要将数值作为文本处理。</span><span class="sxs-lookup"><span data-stu-id="876e2-107">Typically, the wizard will detect numbers and assign an appropriate numeric data type, but there are many scenarios where you might want to handle a number as text instead.</span></span> <span data-ttu-id="876e2-108">例如， **GeographyKey**应作为文本处理，因为它不适合对此标识符执行数学运算。</span><span class="sxs-lookup"><span data-stu-id="876e2-108">For example, the **GeographyKey** should be handled as text, because it would be inappropriate to perform mathematical operations on this identifier.</span></span>  
  
    |<span data-ttu-id="876e2-109">列</span><span class="sxs-lookup"><span data-stu-id="876e2-109">Column</span></span>|<span data-ttu-id="876e2-110">内容类型</span><span class="sxs-lookup"><span data-stu-id="876e2-110">Content Type</span></span>|<span data-ttu-id="876e2-111">数据类型</span><span class="sxs-lookup"><span data-stu-id="876e2-111">Data Type</span></span>|  
    |------------|------------------|---------------|  
    |<span data-ttu-id="876e2-112">**地址 Line1**</span><span class="sxs-lookup"><span data-stu-id="876e2-112">**Address Line1**</span></span>|<span data-ttu-id="876e2-113">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-113">**Discrete**</span></span>|<span data-ttu-id="876e2-114">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-114">**Text**</span></span>|  
    |<span data-ttu-id="876e2-115">**地址第二行**</span><span class="sxs-lookup"><span data-stu-id="876e2-115">**Address Line2**</span></span>|<span data-ttu-id="876e2-116">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-116">**Discrete**</span></span>|<span data-ttu-id="876e2-117">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-117">**Text**</span></span>|  
    |<span data-ttu-id="876e2-118">**年限**</span><span class="sxs-lookup"><span data-stu-id="876e2-118">**Age**</span></span>|<span data-ttu-id="876e2-119">**持续**</span><span class="sxs-lookup"><span data-stu-id="876e2-119">**Continuous**</span></span>|<span data-ttu-id="876e2-120">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-120">**Long**</span></span>|  
    |<span data-ttu-id="876e2-121">**Bike Buyer**</span><span class="sxs-lookup"><span data-stu-id="876e2-121">**Bike Buyer**</span></span>|<span data-ttu-id="876e2-122">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-122">**Discrete**</span></span>|<span data-ttu-id="876e2-123">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-123">**Long**</span></span>|  
    |<span data-ttu-id="876e2-124">**上下班路程**</span><span class="sxs-lookup"><span data-stu-id="876e2-124">**Commute Distance**</span></span>|<span data-ttu-id="876e2-125">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-125">**Discrete**</span></span>|<span data-ttu-id="876e2-126">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-126">**Text**</span></span>|  
    |<span data-ttu-id="876e2-127">**CustomerKey**</span><span class="sxs-lookup"><span data-stu-id="876e2-127">**CustomerKey**</span></span>|<span data-ttu-id="876e2-128">**Key**</span><span class="sxs-lookup"><span data-stu-id="876e2-128">**Key**</span></span>|<span data-ttu-id="876e2-129">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-129">**Long**</span></span>|  
    |<span data-ttu-id="876e2-130">**DateLastPurchase**</span><span class="sxs-lookup"><span data-stu-id="876e2-130">**DateLastPurchase**</span></span>|<span data-ttu-id="876e2-131">**持续**</span><span class="sxs-lookup"><span data-stu-id="876e2-131">**Continuous**</span></span>|<span data-ttu-id="876e2-132">**日期**</span><span class="sxs-lookup"><span data-stu-id="876e2-132">**Date**</span></span>|  
    |<span data-ttu-id="876e2-133">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="876e2-133">**Email Address**</span></span>|<span data-ttu-id="876e2-134">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-134">**Discrete**</span></span>|<span data-ttu-id="876e2-135">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-135">**Text**</span></span>|  
    |<span data-ttu-id="876e2-136">**English Education**</span><span class="sxs-lookup"><span data-stu-id="876e2-136">**English Education**</span></span>|<span data-ttu-id="876e2-137">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-137">**Discrete**</span></span>|<span data-ttu-id="876e2-138">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-138">**Text**</span></span>|  
    |<span data-ttu-id="876e2-139">**English Occupation**</span><span class="sxs-lookup"><span data-stu-id="876e2-139">**English Occupation**</span></span>|<span data-ttu-id="876e2-140">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-140">**Discrete**</span></span>|<span data-ttu-id="876e2-141">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-141">**Text**</span></span>|  
    |<span data-ttu-id="876e2-142">**名字**</span><span class="sxs-lookup"><span data-stu-id="876e2-142">**FirstName**</span></span>|<span data-ttu-id="876e2-143">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-143">**Discrete**</span></span>|<span data-ttu-id="876e2-144">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-144">**Text**</span></span>|  
    |<span data-ttu-id="876e2-145">**性别**</span><span class="sxs-lookup"><span data-stu-id="876e2-145">**Gender**</span></span>|<span data-ttu-id="876e2-146">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-146">**Discrete**</span></span>|<span data-ttu-id="876e2-147">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-147">**Text**</span></span>|  
    |<span data-ttu-id="876e2-148">**Geography Key**</span><span class="sxs-lookup"><span data-stu-id="876e2-148">**Geography Key**</span></span>|<span data-ttu-id="876e2-149">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-149">**Discrete**</span></span>|<span data-ttu-id="876e2-150">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-150">**Text**</span></span>|  
    |<span data-ttu-id="876e2-151">**House Owner Flag**</span><span class="sxs-lookup"><span data-stu-id="876e2-151">**House Owner Flag**</span></span>|<span data-ttu-id="876e2-152">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-152">**Discrete**</span></span>|<span data-ttu-id="876e2-153">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-153">**Text**</span></span>|  
    |<span data-ttu-id="876e2-154">**姓氏**</span><span class="sxs-lookup"><span data-stu-id="876e2-154">**Last Name**</span></span>|<span data-ttu-id="876e2-155">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-155">**Discrete**</span></span>|<span data-ttu-id="876e2-156">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-156">**Text**</span></span>|  
    |<span data-ttu-id="876e2-157">**婚姻状况**</span><span class="sxs-lookup"><span data-stu-id="876e2-157">**Marital Status**</span></span>|<span data-ttu-id="876e2-158">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-158">**Discrete**</span></span>|<span data-ttu-id="876e2-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-159">**Text**</span></span>|  
    |<span data-ttu-id="876e2-160">**Number Cars Owned**</span><span class="sxs-lookup"><span data-stu-id="876e2-160">**Number Cars Owned**</span></span>|<span data-ttu-id="876e2-161">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-161">**Discrete**</span></span>|<span data-ttu-id="876e2-162">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-162">**Long**</span></span>|  
    |<span data-ttu-id="876e2-163">**在家子女数**</span><span class="sxs-lookup"><span data-stu-id="876e2-163">**Number Children At Home**</span></span>|<span data-ttu-id="876e2-164">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-164">**Discrete**</span></span>|<span data-ttu-id="876e2-165">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-165">**Long**</span></span>|  
    |<span data-ttu-id="876e2-166">**区域**</span><span class="sxs-lookup"><span data-stu-id="876e2-166">**Region**</span></span>|<span data-ttu-id="876e2-167">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-167">**Discrete**</span></span>|<span data-ttu-id="876e2-168">**Text**</span><span class="sxs-lookup"><span data-stu-id="876e2-168">**Text**</span></span>|  
    |<span data-ttu-id="876e2-169">**Total Children**</span><span class="sxs-lookup"><span data-stu-id="876e2-169">**Total Children**</span></span>|<span data-ttu-id="876e2-170">**离散**</span><span class="sxs-lookup"><span data-stu-id="876e2-170">**Discrete**</span></span>|<span data-ttu-id="876e2-171">**Long**</span><span class="sxs-lookup"><span data-stu-id="876e2-171">**Long**</span></span>|  
    |<span data-ttu-id="876e2-172">**Yearly Income**</span><span class="sxs-lookup"><span data-stu-id="876e2-172">**Yearly Income**</span></span>|<span data-ttu-id="876e2-173">**持续**</span><span class="sxs-lookup"><span data-stu-id="876e2-173">**Continuous**</span></span>|<span data-ttu-id="876e2-174">**双精度**</span><span class="sxs-lookup"><span data-stu-id="876e2-174">**Double**</span></span>|  
  
3.  <span data-ttu-id="876e2-175">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="876e2-175">Click **Next**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="876e2-176">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="876e2-176">Next Task in Lesson</span></span>  
 [<span data-ttu-id="876e2-177">为结构指定测试数据集 &#40;数据挖掘基础教程&#41;</span><span class="sxs-lookup"><span data-stu-id="876e2-177">Specifying a Testing Data Set for the Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="876e2-178">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="876e2-178">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="876e2-179">创建目标邮件挖掘模型结构 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="876e2-179">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="876e2-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="876e2-180">See Also</span></span>  
 <span data-ttu-id="876e2-181">[内容类型 &#40;数据挖掘&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="876e2-181">[Content Types &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md) </span></span>  
 [<span data-ttu-id="876e2-182">数据类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="876e2-182">Data Types &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
