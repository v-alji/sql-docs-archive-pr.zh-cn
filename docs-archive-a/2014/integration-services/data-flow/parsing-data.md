---
title: 分析数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bd34cd83351e31313ae96ff5709ec999a60f2f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579670"
---
# <a name="parsing-data"></a><span data-ttu-id="9d533-102">分析数据</span><span class="sxs-lookup"><span data-stu-id="9d533-102">Parsing Data</span></span>
  <span data-ttu-id="9d533-103">包中的数据流在异类数据存储区之间提取和加载数据，这些存储区可能使用多种标准数据类型和自定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d533-103">Data flows in packages extract and load data between heterogeneous data stores, which may use a variety of standard and custom data types.</span></span> <span data-ttu-id="9d533-104">在数据流中， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源完成提取数据、分析字符串数据以及将数据转换成 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型的工作。</span><span class="sxs-lookup"><span data-stu-id="9d533-104">In a data flow, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources do the work of extracting data, parsing string data, and converting data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="9d533-105">后续转换可以分析数据，以将其转换为不同的数据类型，或者创建不同数据类型的列副本。</span><span class="sxs-lookup"><span data-stu-id="9d533-105">Subsequent transformations may parse data to convert it to a different data type, or create column copies with different data types.</span></span> <span data-ttu-id="9d533-106">在组件中使用的表达式还可以将参数和操作数转换为不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d533-106">Expressions used in components may also cast arguments and operands to different data types.</span></span> <span data-ttu-id="9d533-107">最后，在将数据加载到数据存储区时，目标可以分析该数据，以将其转换为目标所使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d533-107">Finally, when the data is loaded into a data store, the destination may parse the data to convert it to a data type that the destination uses.</span></span> <span data-ttu-id="9d533-108">有关详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9d533-108">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="types-of-parsing"></a><span data-ttu-id="9d533-109">分析类型</span><span class="sxs-lookup"><span data-stu-id="9d533-109">Types of Parsing</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9d533-110">提供了两种用于转换数据的分析类型：快速分析和标准分析。</span><span class="sxs-lookup"><span data-stu-id="9d533-110">provides two types of parsing for converting data: Fast parse and Standard parse.</span></span>  
  
-   <span data-ttu-id="9d533-111">快速分析是一组简单快捷的分析例程，不支持区域设置特定的数据类型转换，仅支持最常用的日期和时间格式。</span><span class="sxs-lookup"><span data-stu-id="9d533-111">Fast parse is a fast, simple set of parsing routines that does not support locale-specific data type conversions, and supports only the most frequently used date and time formats.</span></span> <span data-ttu-id="9d533-112">有关详细信息，请参阅 [Fast Parse](../fast-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="9d533-112">For more information, see [Fast Parse](../fast-parse.md).</span></span>  
  
-   <span data-ttu-id="9d533-113">标准分析是一组功能齐全的分析例程，支持可在 Oleaut32.dll 和 Ole2dsip.dll 中使用的自动数据类型转换 API 所提供的所有数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="9d533-113">Standard parse is a rich set of parsing routines that supports all the data type conversions that are provided by the Automation data type conversion APIs available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="9d533-114">有关详细信息，请参阅 [Standard Parse](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="9d533-114">For more information, see [Standard Parse](../standard-parse.md).</span></span>  
  
  
