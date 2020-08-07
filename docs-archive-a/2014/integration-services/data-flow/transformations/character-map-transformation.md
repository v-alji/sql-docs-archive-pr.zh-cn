---
title: 字符映射表转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactertrans.f1
helpviewer_keywords:
- mutually exclusive mapping [Integration Services]
- mapping data [Integration Services]
- string functions
- Character Map transformation [Integration Services]
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5fc31e1a3500a7a7b023e43a968e70e5b438dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587943"
---
# <a name="character-map-transformation"></a><span data-ttu-id="94a2b-102">字符映射表转换</span><span class="sxs-lookup"><span data-stu-id="94a2b-102">Character Map Transformation</span></span>
  <span data-ttu-id="94a2b-103">字符映射表转换将字符串函数（如从小写到大写的转换）应用于字符数据。</span><span class="sxs-lookup"><span data-stu-id="94a2b-103">The Character Map transformation applies string functions, such as conversion from lowercase to uppercase, to character data.</span></span> <span data-ttu-id="94a2b-104">此转换操作只对字符串数据类型的列数据执行。</span><span class="sxs-lookup"><span data-stu-id="94a2b-104">This transformation operates only on column data with a string data type.</span></span>  
  
 <span data-ttu-id="94a2b-105">字符映射表转换可就地转换列数据，也可添加一个转换输出列，将转换后的数据放到新列中。</span><span class="sxs-lookup"><span data-stu-id="94a2b-105">The Character Map transformation can convert column data in place or add a column to the transformation output and put the converted data in the new column.</span></span> <span data-ttu-id="94a2b-106">可以对同一输入列应用一组不同的映射操作，并将结果放到不同的列中。</span><span class="sxs-lookup"><span data-stu-id="94a2b-106">You can apply different sets of mapping operations to the same input column and put the results in different columns.</span></span> <span data-ttu-id="94a2b-107">例如，可对同一列进行大写和小写转换，并将结果放到两个不同列中。</span><span class="sxs-lookup"><span data-stu-id="94a2b-107">For example, you can convert the same column to uppercase and lowercase and put the results in two different columns.</span></span>  
  
 <span data-ttu-id="94a2b-108">某些情况下，映射可能导致数据被截断。</span><span class="sxs-lookup"><span data-stu-id="94a2b-108">Mapping can, under some circumstances, cause data to be truncated.</span></span> <span data-ttu-id="94a2b-109">例如，如果将单字节字符映射到采用多字节表示形式的字符，则可能发生截断。</span><span class="sxs-lookup"><span data-stu-id="94a2b-109">For example, truncation can occur when single-byte characters are mapped to characters with a multibyte representation.</span></span> <span data-ttu-id="94a2b-110">字符映射表转换包含一个错误输出，可用于将截断的数据定向到单独的输出。</span><span class="sxs-lookup"><span data-stu-id="94a2b-110">The Character Map transformation includes an error output, which can be used to direct truncated data to separate output.</span></span> <span data-ttu-id="94a2b-111">有关详细信息，请参阅 [数据中的错误处理](../error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a2b-111">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="94a2b-112">此转换有一个输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="94a2b-112">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="mapping-operations"></a><span data-ttu-id="94a2b-113">映射操作</span><span class="sxs-lookup"><span data-stu-id="94a2b-113">Mapping Operations</span></span>  
 <span data-ttu-id="94a2b-114">下表说明了字符映射表转换支持的映射操作。</span><span class="sxs-lookup"><span data-stu-id="94a2b-114">The following table describes the mapping operations that the Character Map transformation supports.</span></span>  
  
|<span data-ttu-id="94a2b-115">Operation</span><span class="sxs-lookup"><span data-stu-id="94a2b-115">Operation</span></span>|<span data-ttu-id="94a2b-116">说明</span><span class="sxs-lookup"><span data-stu-id="94a2b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94a2b-117">Byte reversal</span><span class="sxs-lookup"><span data-stu-id="94a2b-117">Byte reversal</span></span>|<span data-ttu-id="94a2b-118">反转字节顺序。</span><span class="sxs-lookup"><span data-stu-id="94a2b-118">Reverses byte order.</span></span>|  
|<span data-ttu-id="94a2b-119">Full width</span><span class="sxs-lookup"><span data-stu-id="94a2b-119">Full width</span></span>|<span data-ttu-id="94a2b-120">将半角字符映射到全角字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-120">Maps half-width characters to full-width characters.</span></span>|  
|<span data-ttu-id="94a2b-121">Half width</span><span class="sxs-lookup"><span data-stu-id="94a2b-121">Half width</span></span>|<span data-ttu-id="94a2b-122">将全角字符映射到半角字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-122">Maps full-width characters to half-width characters.</span></span>|  
|<span data-ttu-id="94a2b-123">Hiragana</span><span class="sxs-lookup"><span data-stu-id="94a2b-123">Hiragana</span></span>|<span data-ttu-id="94a2b-124">将片假名字符映射到平假名字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-124">Maps katakana characters to hiragana characters.</span></span>|  
|<span data-ttu-id="94a2b-125">Katakana</span><span class="sxs-lookup"><span data-stu-id="94a2b-125">Katakana</span></span>|<span data-ttu-id="94a2b-126">将平假名字符映射到片假名字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-126">Maps hiragana characters to katakana characters.</span></span>|  
|<span data-ttu-id="94a2b-127">Linguistic casing</span><span class="sxs-lookup"><span data-stu-id="94a2b-127">Linguistic casing</span></span>|<span data-ttu-id="94a2b-128">应用语言中的大小写来取代系统规则。</span><span class="sxs-lookup"><span data-stu-id="94a2b-128">Applies linguistic casing instead of the system rules.</span></span> <span data-ttu-id="94a2b-129">语言中的大小写是指 Win32 API 为 Turkic 和其他区域设置的 Unicode 简单大小写映射提供的功能。</span><span class="sxs-lookup"><span data-stu-id="94a2b-129">Linguistic casing refers to functionality provided by the Win32 API for Unicode simple case mapping of Turkic and other locales.</span></span>|  
|<span data-ttu-id="94a2b-130">小写</span><span class="sxs-lookup"><span data-stu-id="94a2b-130">Lowercase</span></span>|<span data-ttu-id="94a2b-131">将字符转换为小写。</span><span class="sxs-lookup"><span data-stu-id="94a2b-131">Converts characters to lowercase.</span></span>|  
|<span data-ttu-id="94a2b-132">简体中文</span><span class="sxs-lookup"><span data-stu-id="94a2b-132">Simplified Chinese</span></span>|<span data-ttu-id="94a2b-133">将繁体中文字符映射到简体中文字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-133">Maps traditional Chinese characters to simplified Chinese characters.</span></span>|  
|<span data-ttu-id="94a2b-134">繁体中文</span><span class="sxs-lookup"><span data-stu-id="94a2b-134">Traditional Chinese</span></span>|<span data-ttu-id="94a2b-135">将简体中文字符映射到繁体中文字符。</span><span class="sxs-lookup"><span data-stu-id="94a2b-135">Maps simplified Chinese characters to traditional Chinese characters.</span></span>|  
|<span data-ttu-id="94a2b-136">大写</span><span class="sxs-lookup"><span data-stu-id="94a2b-136">Uppercase</span></span>|<span data-ttu-id="94a2b-137">将字符转换为大写。</span><span class="sxs-lookup"><span data-stu-id="94a2b-137">Converts characters to uppercase.</span></span>|  
  
## <a name="mutually-exclusive-mapping-operations"></a><span data-ttu-id="94a2b-138">互相排斥的映射操作</span><span class="sxs-lookup"><span data-stu-id="94a2b-138">Mutually Exclusive Mapping Operations</span></span>  
 <span data-ttu-id="94a2b-139">一次转换可以执行多个操作。</span><span class="sxs-lookup"><span data-stu-id="94a2b-139">More than one operation can be performed in a transformation.</span></span> <span data-ttu-id="94a2b-140">但是，有些映射操作是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="94a2b-140">However, some mapping operations are mutually exclusive.</span></span> <span data-ttu-id="94a2b-141">下表列出了对同一个列使用多个操作时适用的限制。</span><span class="sxs-lookup"><span data-stu-id="94a2b-141">The following table lists restrictions that apply when you use multiple operations on the same column.</span></span> <span data-ttu-id="94a2b-142">操作 A 列和操作 B 列中的操作是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="94a2b-142">Operations in the columns Operation A and Operation B are mutually exclusive.</span></span>  
  
|<span data-ttu-id="94a2b-143">操作 A</span><span class="sxs-lookup"><span data-stu-id="94a2b-143">Operation A</span></span>|<span data-ttu-id="94a2b-144">操作 B</span><span class="sxs-lookup"><span data-stu-id="94a2b-144">Operation B</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="94a2b-145">小写</span><span class="sxs-lookup"><span data-stu-id="94a2b-145">Lowercase</span></span>|<span data-ttu-id="94a2b-146">大写</span><span class="sxs-lookup"><span data-stu-id="94a2b-146">Uppercase</span></span>|  
|<span data-ttu-id="94a2b-147">Hiragana</span><span class="sxs-lookup"><span data-stu-id="94a2b-147">Hiragana</span></span>|<span data-ttu-id="94a2b-148">Katakana</span><span class="sxs-lookup"><span data-stu-id="94a2b-148">Katakana</span></span>|  
|<span data-ttu-id="94a2b-149">Half width</span><span class="sxs-lookup"><span data-stu-id="94a2b-149">Half width</span></span>|<span data-ttu-id="94a2b-150">Full width</span><span class="sxs-lookup"><span data-stu-id="94a2b-150">Full width</span></span>|  
|<span data-ttu-id="94a2b-151">繁体中文</span><span class="sxs-lookup"><span data-stu-id="94a2b-151">Traditional Chinese</span></span>|<span data-ttu-id="94a2b-152">简体中文</span><span class="sxs-lookup"><span data-stu-id="94a2b-152">Simplified Chinese</span></span>|  
|<span data-ttu-id="94a2b-153">小写</span><span class="sxs-lookup"><span data-stu-id="94a2b-153">Lowercase</span></span>|<span data-ttu-id="94a2b-154">Hiragana、katakana、half width、full width</span><span class="sxs-lookup"><span data-stu-id="94a2b-154">Hiragana, katakana, half width, full width</span></span>|  
|<span data-ttu-id="94a2b-155">大写</span><span class="sxs-lookup"><span data-stu-id="94a2b-155">Uppercase</span></span>|<span data-ttu-id="94a2b-156">Hiragana、katakana、half width、full width</span><span class="sxs-lookup"><span data-stu-id="94a2b-156">Hiragana, katakana, half width, full width</span></span>|  
  
## <a name="configuration-of-the-character-map-transformation"></a><span data-ttu-id="94a2b-157">配置字符映射表转换</span><span class="sxs-lookup"><span data-stu-id="94a2b-157">Configuration of the Character Map Transformation</span></span>  
 <span data-ttu-id="94a2b-158">可以采用下列方法来配置字符映射表转换：</span><span class="sxs-lookup"><span data-stu-id="94a2b-158">You configure the Character Map transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="94a2b-159">指定要转换的列。</span><span class="sxs-lookup"><span data-stu-id="94a2b-159">Specify the columns to convert.</span></span>  
  
-   <span data-ttu-id="94a2b-160">指定要应用于每一列的操作。</span><span class="sxs-lookup"><span data-stu-id="94a2b-160">Specify the operations to apply to each column.</span></span>  
  
 <span data-ttu-id="94a2b-161">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="94a2b-161">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="94a2b-162">有关可在 **“字符映射表转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Character Map Transformation Editor](../../character-map-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="94a2b-162">For more information about the properties that you can set in the **Character Map Transformation Editor** dialog box, see [Character Map Transformation Editor](../../character-map-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="94a2b-163">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="94a2b-163">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="94a2b-164">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="94a2b-164">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="94a2b-165">Common Properties</span><span class="sxs-lookup"><span data-stu-id="94a2b-165">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="94a2b-166">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="94a2b-166">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="94a2b-167">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="94a2b-167">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="94a2b-168">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="94a2b-168">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="94a2b-169">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="94a2b-169">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  
