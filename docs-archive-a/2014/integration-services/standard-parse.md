---
title: 标准分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- standard parse [Integration Services]
- locales [Integration Services]
ms.assetid: dfe835b1-ea52-4e18-a23a-5188c5b6f013
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cacff710870d372d6bbf8345e05397857c13a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690727"
---
# <a name="standard-parse"></a><span data-ttu-id="315e9-102">Standard Parse</span><span class="sxs-lookup"><span data-stu-id="315e9-102">Standard Parse</span></span>
  <span data-ttu-id="315e9-103">标准分析是一组受区域设置影响的分析例程，这些例程支持 Oleaut32.dll 和 Ole2dsip.dll 中可用的自动数据类型转换 API 所提供的全部数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="315e9-103">Standard parse is a locale-sensitive set of parsing routines that support all the data type conversions provided by the Automation data type conversion APIs that are available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="315e9-104">标准分析相当于 OLE DB 分析 API。</span><span class="sxs-lookup"><span data-stu-id="315e9-104">Standard parse is equivalent to the OLE DB parsing APIs.</span></span>  
  
 <span data-ttu-id="315e9-105">标准分析支持国际数据的数据类型转换，且快速分析不支持数据格式时应使用标准分析。</span><span class="sxs-lookup"><span data-stu-id="315e9-105">Standard parse provides support for data type conversion of international data, and it should be used if the data format is not supported by Fast parse.</span></span> <span data-ttu-id="315e9-106">有关自动化数据类型转换 API 的详细信息，请参阅 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427)中的“Data Type Conversion APIs”（数据类型转换 API）。</span><span class="sxs-lookup"><span data-stu-id="315e9-106">For more information about the Automation data type conversion API, see "Data Type Conversion APIs" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315e9-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="315e9-107">See Also</span></span>  
 [<span data-ttu-id="315e9-108">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="315e9-108">Fast Parse</span></span>](../../2014/integration-services/fast-parse.md)  
  
  
