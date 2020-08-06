---
title: Analysis Services OLE DB Provider (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services OLE DB Provider
ms.assetid: cdeecd50-1d91-4162-a4a2-01c7799b02a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c0348a23a6def4c3cdbd083354083947ce1390b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591644"
---
# <a name="analysis-services-ole-db-provider-analysis-services---multidimensional-data"></a><span data-ttu-id="c9e2d-102">Analysis Services OLE DB 访问接口（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c9e2d-102">Analysis Services OLE DB Provider (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c9e2d-103">Analysis Services OLE DB Provider 是与交互的应用程序的接口 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-103">The Analysis Services OLE DB Provider is an interface for applications interacting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c9e2d-104">它用于生成与多维数据进行交互的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-104">It is used to build client applications that interact with multidimensional data.</span></span> <span data-ttu-id="c9e2d-105">此访问接口还提供对多维数据和关系数据进行联机或脱机数据挖掘分析的方法，且为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-105">This provider also provides methods for online and offline data mining analysis of multidimensional data and relational data, and is included as part of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c9e2d-106">它可由第三方客户端应用程序进行再分发。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-106">It can be redistributed by third-party client applications.</span></span>  
  
 <span data-ttu-id="c9e2d-107">Analysis Services OLE DB 访问接口是用于与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进行交互以完成以下任务的主要方法：连接到多维数据集或数据挖掘模型、查询多维数据集或数据挖掘模型，以及检索架构信息。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-107">The Analysis Services OLE DB Provider is the primary method for interacting with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in order to accomplish such tasks as connecting to a cube or data mining model, querying a cube or data mining model, and retrieving schema information.</span></span>  
  
 <span data-ttu-id="c9e2d-108">Analysis Services OLE DB 访问接口是一种独立的访问接口，通过该访问接口，客户端应用程序可以借助关系源和多维源创建本地多维数据集文件和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-108">As a stand-alone provider, the Analysis Services OLE DB Provider provides client applications with the ability to create local cube files and mining models from relational and multidimensional sources.</span></span> <span data-ttu-id="c9e2d-109">客户端应用程序可以连接到本地多维数据集，并使用多维表达式 (MDX) 执行查询，而不用与运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的全功能服务器进行交互。</span><span class="sxs-lookup"><span data-stu-id="c9e2d-109">Client applications can connect to a local cube and execute queries using Multidimensional Expressions (MDX) without interacting with the full-scale server running the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e2d-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9e2d-110">See Also</span></span>  
 [<span data-ttu-id="c9e2d-111">多维模型数据访问 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e2d-111">Multidimensional Model Data Access &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
