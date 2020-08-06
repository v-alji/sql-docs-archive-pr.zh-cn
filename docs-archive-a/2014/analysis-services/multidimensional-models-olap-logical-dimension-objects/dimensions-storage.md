---
title: 维度存储 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa68ebcfa8f4136bcd4a131842c852665ee9851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687315"
---
# <a name="dimension-storage"></a><span data-ttu-id="94d32-102">维度存储</span><span class="sxs-lookup"><span data-stu-id="94d32-102">Dimension Storage</span></span>
  <span data-ttu-id="94d32-103">中的维度 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支持两种存储模式：</span><span class="sxs-lookup"><span data-stu-id="94d32-103">Dimensions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support two storage modes:</span></span>  
  
-   <span data-ttu-id="94d32-104">关系 OLAP (ROLAP)</span><span class="sxs-lookup"><span data-stu-id="94d32-104">Relational OLAP (ROLAP)</span></span>  
  
-   <span data-ttu-id="94d32-105">多维 OLAP (MOLAP)</span><span class="sxs-lookup"><span data-stu-id="94d32-105">Multidimensional OLAP (MOLAP)</span></span>  
  
 <span data-ttu-id="94d32-106">存储模式将确定维度数据的位置和形式。</span><span class="sxs-lookup"><span data-stu-id="94d32-106">The storage mode determines the location and form of a dimension's data.</span></span> <span data-ttu-id="94d32-107">维度的默认存储模式为 MOLAP。</span><span class="sxs-lookup"><span data-stu-id="94d32-107">MOLAP is the default storage mode for dimensions.</span></span> <span data-ttu-id="94d32-108">**相关主题：**[分区存储模式和处理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span><span class="sxs-lookup"><span data-stu-id="94d32-108">**Related topics:**[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span></span>  
  
## <a name="molap"></a><span data-ttu-id="94d32-109">MOLAP</span><span class="sxs-lookup"><span data-stu-id="94d32-109">MOLAP</span></span>  
 <span data-ttu-id="94d32-110">使用 MOLAP 的维度的数据存储在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中的多维结构中。</span><span class="sxs-lookup"><span data-stu-id="94d32-110">Data for a dimension that uses MOLAP is stored in a multidimensional structure in the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="94d32-111">该多维结构是在处理维度时创建和填充的。</span><span class="sxs-lookup"><span data-stu-id="94d32-111">This multidimensional structure is created and populated when the dimension is processed.</span></span> <span data-ttu-id="94d32-112">MOLAP 维度提供的查询性能比 ROLAP 维度更好。</span><span class="sxs-lookup"><span data-stu-id="94d32-112">MOLAP dimensions provide better query performance than ROLAP dimensions.</span></span>  
  
## <a name="rolap"></a><span data-ttu-id="94d32-113">ROLAP</span><span class="sxs-lookup"><span data-stu-id="94d32-113">ROLAP</span></span>  
 <span data-ttu-id="94d32-114">使用 ROLAP 的维度的数据实际上存储在用于定义维度的表中。</span><span class="sxs-lookup"><span data-stu-id="94d32-114">Data for a dimension that uses ROLAP is actually stored in the tables used to define the dimension.</span></span> <span data-ttu-id="94d32-115">ROLAP 存储模式无需复制大量数据就可用来支持大型维度，但会降低查询性能。</span><span class="sxs-lookup"><span data-stu-id="94d32-115">The ROLAP storage mode can be used to support large dimensions without duplicating large amounts of data, but at the expense of query performance.</span></span> <span data-ttu-id="94d32-116">维度直接依赖于数据源视图中用于定义维度的表，因此 ROLAP 存储模式还可支持实时 OLAP。</span><span class="sxs-lookup"><span data-stu-id="94d32-116">Because the dimension relies directly on the tables in the data source view used to define the dimension, the ROLAP storage mode also supports real-time OLAP.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="94d32-117">如果维度使用 ROLAP 存储模式并且此维度包括在使用 MOLAP 存储的多维数据集中，则对其源表进行架构更改之后，必须立即进行多维数据集处理。</span><span class="sxs-lookup"><span data-stu-id="94d32-117">If a dimension uses the ROLAP storage mode and the dimension is included in a cube that uses MOLAP storage, any schema changes to its source table must be followed by immediate processing of the cube.</span></span> <span data-ttu-id="94d32-118">如果执行此操作失败，则可能会导致对多维数据集进行查询时得到不一致的结果。</span><span class="sxs-lookup"><span data-stu-id="94d32-118">Failure to do this may result in inconsistent results when querying the cube.</span></span> <span data-ttu-id="94d32-119">**相关主题：**[通过 SSIS 自动 Analysis Services 管理任务](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="94d32-119">**Related topic:**[Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d32-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94d32-120">See Also</span></span>  
 [<span data-ttu-id="94d32-121">分区存储模式和处理</span><span class="sxs-lookup"><span data-stu-id="94d32-121">Partition Storage Modes and Processing</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
