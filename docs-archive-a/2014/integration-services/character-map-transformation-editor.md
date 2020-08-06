---
title: 字符映射表转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6cdcdba448dafc6ccf03774d4f611dee704b823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579700"
---
# <a name="character-map-transformation-editor"></a><span data-ttu-id="024cf-102">字符映射表转换编辑器</span><span class="sxs-lookup"><span data-stu-id="024cf-102">Character Map Transformation Editor</span></span>
  <span data-ttu-id="024cf-103">可以使用“字符映射表转换编辑器”\*\*\*\* 对话框，选择要应用到列数据的字符串函数，以及指定映射是就地更改还是添加为新列。</span><span class="sxs-lookup"><span data-stu-id="024cf-103">Use the **Character Map Transformation Editor** dialog box to select the string functions to apply to column data and to specify whether mapping is an in-place change or added as a new column.</span></span>  
  
 <span data-ttu-id="024cf-104">若要了解有关字符映射表转换的详细信息，请参阅 [Character Map Transformation](data-flow/transformations/character-map-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="024cf-104">To learn more about the Character Map transformation, see [Character Map Transformation](data-flow/transformations/character-map-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="024cf-105">选项</span><span class="sxs-lookup"><span data-stu-id="024cf-105">Options</span></span>  
 <span data-ttu-id="024cf-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="024cf-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="024cf-107">使用该复选框可以选择通过字符串函数转换的列。</span><span class="sxs-lookup"><span data-stu-id="024cf-107">Use the check boxes to select the columns to transform using string functions.</span></span> <span data-ttu-id="024cf-108">您的选择将显示在下表中。</span><span class="sxs-lookup"><span data-stu-id="024cf-108">Your selections appear in the table below.</span></span>  
  
 <span data-ttu-id="024cf-109">**输入列**</span><span class="sxs-lookup"><span data-stu-id="024cf-109">**Input Column**</span></span>  
 <span data-ttu-id="024cf-110">查看从上表中选择的输入列。</span><span class="sxs-lookup"><span data-stu-id="024cf-110">View input columns selected from the table above.</span></span> <span data-ttu-id="024cf-111">您也可使用可用输入列的列表更改或删除选项。</span><span class="sxs-lookup"><span data-stu-id="024cf-111">You can also change or remove a selection by using the list of available input columns.</span></span>  
  
 <span data-ttu-id="024cf-112">**目标**</span><span class="sxs-lookup"><span data-stu-id="024cf-112">**Destination**</span></span>  
 <span data-ttu-id="024cf-113">指定是否就地保存字符串运算结果、使用现有列或将已修改的数据作为新列保存。</span><span class="sxs-lookup"><span data-stu-id="024cf-113">Specify whether to save the results of the string operations in place, using the existing column, or to save the modified data as a new column.</span></span>  
  
|<span data-ttu-id="024cf-114">值</span><span class="sxs-lookup"><span data-stu-id="024cf-114">Value</span></span>|<span data-ttu-id="024cf-115">说明</span><span class="sxs-lookup"><span data-stu-id="024cf-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="024cf-116">新列</span><span class="sxs-lookup"><span data-stu-id="024cf-116">New column</span></span>|<span data-ttu-id="024cf-117">将数据保存在新列中。</span><span class="sxs-lookup"><span data-stu-id="024cf-117">Save the data in a new column.</span></span> <span data-ttu-id="024cf-118">在 **“输出别名”** 下分配列名。</span><span class="sxs-lookup"><span data-stu-id="024cf-118">Assign the column name under **Output Alias**.</span></span>|  
|<span data-ttu-id="024cf-119">就地更改</span><span class="sxs-lookup"><span data-stu-id="024cf-119">In-place change</span></span>|<span data-ttu-id="024cf-120">将已修改的数据保存在现有的列中。</span><span class="sxs-lookup"><span data-stu-id="024cf-120">Save the modified data in the existing column.</span></span>|  
  
 <span data-ttu-id="024cf-121">**操作**</span><span class="sxs-lookup"><span data-stu-id="024cf-121">**Operation**</span></span>  
 <span data-ttu-id="024cf-122">从列表中选择要应用于列数据的字符串函数。</span><span class="sxs-lookup"><span data-stu-id="024cf-122">Select from the list the string functions to apply to column data.</span></span>  
  
|<span data-ttu-id="024cf-123">值</span><span class="sxs-lookup"><span data-stu-id="024cf-123">Value</span></span>|<span data-ttu-id="024cf-124">说明</span><span class="sxs-lookup"><span data-stu-id="024cf-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="024cf-125">小写</span><span class="sxs-lookup"><span data-stu-id="024cf-125">Lowercase</span></span>|<span data-ttu-id="024cf-126">转换为小写字母。</span><span class="sxs-lookup"><span data-stu-id="024cf-126">Convert to lower case.</span></span>|  
|<span data-ttu-id="024cf-127">大写</span><span class="sxs-lookup"><span data-stu-id="024cf-127">Uppercase</span></span>|<span data-ttu-id="024cf-128">转换为大写字母。</span><span class="sxs-lookup"><span data-stu-id="024cf-128">Convert to upper case.</span></span>|  
|<span data-ttu-id="024cf-129">Byte reversal</span><span class="sxs-lookup"><span data-stu-id="024cf-129">Byte reversal</span></span>|<span data-ttu-id="024cf-130">通过反转字节顺序进行转换。</span><span class="sxs-lookup"><span data-stu-id="024cf-130">Convert by reversing byte order.</span></span>|  
|<span data-ttu-id="024cf-131">Hiragana</span><span class="sxs-lookup"><span data-stu-id="024cf-131">Hiragana</span></span>|<span data-ttu-id="024cf-132">将日语的片假名字符转换为平假名字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-132">Convert Japanese katakana characters to hiragana.</span></span>|  
|<span data-ttu-id="024cf-133">Katakana</span><span class="sxs-lookup"><span data-stu-id="024cf-133">Katakana</span></span>|<span data-ttu-id="024cf-134">将日语的平假名字符转换为片假名字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-134">Convert Japanese hiragana characters to katakana.</span></span>|  
|<span data-ttu-id="024cf-135">Half width</span><span class="sxs-lookup"><span data-stu-id="024cf-135">Half width</span></span>|<span data-ttu-id="024cf-136">将全角字符转换为半角字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-136">Convert full-width characters to half width.</span></span>|  
|<span data-ttu-id="024cf-137">Full width</span><span class="sxs-lookup"><span data-stu-id="024cf-137">Full width</span></span>|<span data-ttu-id="024cf-138">将半角字符转换为全角字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-138">Convert half-width characters to full width.</span></span>|  
|<span data-ttu-id="024cf-139">Linguistic casing</span><span class="sxs-lookup"><span data-stu-id="024cf-139">Linguistic casing</span></span>|<span data-ttu-id="024cf-140">应用大小写语言规则（为土耳其语和其他区域语言设置的 Unicode 简单大小写映射）而不是系统规则。</span><span class="sxs-lookup"><span data-stu-id="024cf-140">Apply linguistic rules of casing (Unicode simple case mapping for Turkic and other locales) instead of the system rules.</span></span>|  
|<span data-ttu-id="024cf-141">简体中文</span><span class="sxs-lookup"><span data-stu-id="024cf-141">Simplified Chinese</span></span>|<span data-ttu-id="024cf-142">将繁体中文字符转换为简体中文字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-142">Convert traditional Chinese characters to simplified Chinese.</span></span>|  
|<span data-ttu-id="024cf-143">繁体中文</span><span class="sxs-lookup"><span data-stu-id="024cf-143">Traditional Chinese</span></span>|<span data-ttu-id="024cf-144">将简体中文字符转换为繁体中文字符。</span><span class="sxs-lookup"><span data-stu-id="024cf-144">Convert simplified Chinese characters to traditional Chinese.</span></span>|  
  
 <span data-ttu-id="024cf-145">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="024cf-145">**Output Alias**</span></span>  
 <span data-ttu-id="024cf-146">为每个输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="024cf-146">Type an alias for each output column.</span></span> <span data-ttu-id="024cf-147">默认为 **Copy of** 后接输入列名。不过，你也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="024cf-147">The default is **Copy of** followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="024cf-148">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="024cf-148">**Configure Error Output**</span></span>  
 <span data-ttu-id="024cf-149">使用[“配置错误输出” ](../../2014/integration-services/configure-error-output.md) 对话框可以为此转换指定错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="024cf-149">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024cf-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="024cf-150">See Also</span></span>  
 [<span data-ttu-id="024cf-151">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="024cf-151">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
