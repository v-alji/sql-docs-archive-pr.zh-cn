---
title: 数据流中的数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a073db65768c413b6cbe648c757ad75d80bd318e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693414"
---
# <a name="data-in-data-flows"></a><span data-ttu-id="c2998-102">数据流中的数据</span><span class="sxs-lookup"><span data-stu-id="c2998-102">Data in Data Flows</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="c2998-103">提供了用于数据流中的一组数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2998-103">provides a set of data types that are used in data flows.</span></span>  
  
## <a name="data-type-conversion"></a><span data-ttu-id="c2998-104">数据类型转换</span><span class="sxs-lookup"><span data-stu-id="c2998-104">Data Type Conversion</span></span>  
 <span data-ttu-id="c2998-105">添加到数据流的源将源数据转换为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2998-105">The source that you add to a data flow converts the source data to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="c2998-106">后续转换可能将数据转换为不同的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型，而且根据数据加载于其上的数据存储区的类型，目标可能将最终的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型转换成目标数据存储区所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2998-106">Subsequent transformations may convert the data to different [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, and depending on the type of data store into which data is loaded, destinations may convert the final [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the data type required by the destination data store.</span></span> <span data-ttu-id="c2998-107">有关详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c2998-107">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="c2998-108">为将数据转换为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型，数据流组件对数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="c2998-108">To convert the data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type, a data flow component parses the data.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="c2998-109">提供两种类型的数据分析：快速分析和标准分析。</span><span class="sxs-lookup"><span data-stu-id="c2998-109">provides two types of data parsing: fast parse and standard parse.</span></span> <span data-ttu-id="c2998-110">大多数数据流组件只能使用标准分析；但是，平面文件源和数据转换既可以使用快速分析，也可以使用标准分析。</span><span class="sxs-lookup"><span data-stu-id="c2998-110">Most data flow components can use only standard parsing; however, the Flat File source and the Data Conversion transformation can use either fast parse or standard parse.</span></span> <span data-ttu-id="c2998-111">有关详细信息，请参阅 [Parsing Data](parsing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c2998-111">For more information, see [Parsing Data](parsing-data.md).</span></span>  
  
## <a name="data-type-comparison"></a><span data-ttu-id="c2998-112">数据类型比较</span><span class="sxs-lookup"><span data-stu-id="c2998-112">Data Type Comparison</span></span>  
 <span data-ttu-id="c2998-113">很多转换都对数据值进行比较。</span><span class="sxs-lookup"><span data-stu-id="c2998-113">Many transformations compare data values.</span></span> <span data-ttu-id="c2998-114">例如，聚合转换对值进行比较是为了聚合一组数据行中的值，排序转换对值进行比较是为了对值进行排序，而查找转换将值与单独的引用表中的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="c2998-114">For example, the Aggregate transformation compares values for the purpose of aggregating values across a set of data rows, the Sort transformation compares values in order to sort them, and the Lookup transformation compares values against values in a separate reference table.</span></span> <span data-ttu-id="c2998-115">为指定应如何比较字符串，转换包括了一组比较选项，如是否忽略区分大小写、如何处理日语文本中的假名类型以及是否忽略字符串中的空格字符。</span><span class="sxs-lookup"><span data-stu-id="c2998-115">To specify how strings should be compared, the transformation includes a set of comparison options such as whether to ignore case sensitivity, how to handle kana types in Japanese text, and whether to ignore white-space characters in the string.</span></span> <span data-ttu-id="c2998-116">有关详细信息，请参阅 [Comparing String Data](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c2998-116">For more information, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="c2998-117">表达式计算器在计算变量、优先约束和转换使用的表达式时，也对数据值进行比较。</span><span class="sxs-lookup"><span data-stu-id="c2998-117">The expression evaluator also compares data values when it evaluates the expressions that variables, precedence constraints, and transformations use.</span></span>  
  
## <a name="data-flow-troubleshooting"></a><span data-ttu-id="c2998-118">数据流故障排除</span><span class="sxs-lookup"><span data-stu-id="c2998-118">Data Flow Troubleshooting</span></span>  
 <span data-ttu-id="c2998-119">将包部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录后，您可以在执行期间对包中的数据流进行分析，以检查性能或查找其他问题。</span><span class="sxs-lookup"><span data-stu-id="c2998-119">Once you have deployed a package to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog, you can analyze the data flow in the package during execution to check performance or look for other issues.</span></span> <span data-ttu-id="c2998-120">通过提供的标准报表，您可以查看包状态和历史记录，并查询提供了有关包执行的详细信息的数据库视图。</span><span class="sxs-lookup"><span data-stu-id="c2998-120">Standard reports are available that allow you to view package status and history, and you can query database views that provide detailed information about package execution.</span></span> <span data-ttu-id="c2998-121">您还可以在执行期间动态添加和删除分流点以面向包的特定组件。</span><span class="sxs-lookup"><span data-stu-id="c2998-121">You also can dynamically add and remove data taps during execution to target specific components of your package.</span></span> <span data-ttu-id="c2998-122">有关详细信息，请参阅 [数据流分析](data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="c2998-122">For more information, see [Analysis of Data Flow](data-flow.md).</span></span>  
  
  
