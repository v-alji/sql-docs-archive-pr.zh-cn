---
title: 数据转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57b1f70c070cdf81dc0bc899ed365d048db26cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577765"
---
# <a name="data-conversion-transformation"></a><span data-ttu-id="31085-102">数据转换</span><span class="sxs-lookup"><span data-stu-id="31085-102">Data Conversion Transformation</span></span>
  <span data-ttu-id="31085-103">数据转换将输入列中的数据转换为其他数据类型，然后将其复制到新的输出列。</span><span class="sxs-lookup"><span data-stu-id="31085-103">The Data Conversion transformation converts the data in an input column to a different data type and then copies it to a new output column.</span></span> <span data-ttu-id="31085-104">例如，包可从多个源中提取数据，然后用此转换将列转换为目标数据存储所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="31085-104">For example, a package can extract data from multiple sources, and then use this transformation to convert columns to the data type required by the destination data store.</span></span> <span data-ttu-id="31085-105">可以对单个输入列应用多个转换。</span><span class="sxs-lookup"><span data-stu-id="31085-105">You can apply multiple conversions to a single input column.</span></span>  
  
 <span data-ttu-id="31085-106">使用此转换，包可以执行下列类型的数据转换：</span><span class="sxs-lookup"><span data-stu-id="31085-106">Using this transformation, a package can perform the following types of data conversions:</span></span>  
  
-   <span data-ttu-id="31085-107">更改数据类型。</span><span class="sxs-lookup"><span data-stu-id="31085-107">Change the data type.</span></span> <span data-ttu-id="31085-108">有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="31085-108">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31085-109">如果将数据转换为日期或日期时间数据类型，则输出列中的日期为 ISO 格式，即使区域设置首选项指定了不同格式时也是如此。</span><span class="sxs-lookup"><span data-stu-id="31085-109">If you are converting data to a date or a datetime data type, the date in the output column is in the ISO format, although the locale preference may specify a different format.</span></span>  
  
-   <span data-ttu-id="31085-110">设置字符串数据的列长度和数值数据的精度及小数位数。</span><span class="sxs-lookup"><span data-stu-id="31085-110">Set the column length of string data and the precision and scale on numeric data.</span></span> <span data-ttu-id="31085-111">有关详细信息，请参阅[精度、小数位数和长度 (Transact-SQL)](/sql/t-sql/data-types/precision-scale-and-length-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="31085-111">For more information, see [Precision, Scale, and Length &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).</span></span>  
  
-   <span data-ttu-id="31085-112">指定一个代码页。</span><span class="sxs-lookup"><span data-stu-id="31085-112">Specify a code page.</span></span> <span data-ttu-id="31085-113">有关详细信息，请参阅 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="31085-113">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31085-114">在包含字符串数据类型的列之间复制时，两列必须使用相同的代码页。</span><span class="sxs-lookup"><span data-stu-id="31085-114">When copying between columns with a string data type, the two columns must use the same code page.</span></span>  
  
 <span data-ttu-id="31085-115">如果字符串数据的输出列长度小于其对应的输入列长度，则输出数据将被截断。</span><span class="sxs-lookup"><span data-stu-id="31085-115">If the length of an output column of string data is shorter than the length of its corresponding input column, the output data is truncated.</span></span> <span data-ttu-id="31085-116">有关详细信息，请参阅 [数据中的错误处理](../error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="31085-116">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="31085-117">此转换有一个输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="31085-117">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="31085-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="31085-118">Related Tasks</span></span>  
 <span data-ttu-id="31085-119">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="31085-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="31085-120">有关在 SSIS 设计器中使用数据转换的信息，请参阅 [使用数据转换将数据转换为其他数据类型](data-conversion-transformation.md) 和 [数据转换编辑器](../../data-conversion-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="31085-120">For information about using the Data Conversion Transformation in the SSIS Designer, see [Convert Data to a Different Data Type by Using the Data Conversion Transformation](data-conversion-transformation.md) and [Data Conversion Transformation Editor](../../data-conversion-transformation-editor.md).</span></span> <span data-ttu-id="31085-121">有关如何以编程方式设置此转换的属性的信息，请参阅 [通用属性](../../common-properties.md) 和 [转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="31085-121">For information about setting properties of this transformation programmatically, see [Common Properties](../../common-properties.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="31085-122">相关内容</span><span class="sxs-lookup"><span data-stu-id="31085-122">Related Content</span></span>  
 <span data-ttu-id="31085-123">blogs.msdn.com 上的博客文章 [SSIS 2008 中数据类型转换技术之间的性能比较](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)。</span><span class="sxs-lookup"><span data-stu-id="31085-123">Blog entry, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31085-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31085-124">See Also</span></span>  
 <span data-ttu-id="31085-125">[快速分析](../../fast-parse.md) </span><span class="sxs-lookup"><span data-stu-id="31085-125">[Fast Parse](../../fast-parse.md) </span></span>  
 <span data-ttu-id="31085-126">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="31085-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="31085-127">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="31085-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
