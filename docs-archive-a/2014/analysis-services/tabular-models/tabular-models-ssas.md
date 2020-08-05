---
title: " (SSAS 表格) 的表格建模 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44f358f0f36e84ad903a0a4fcb0203291019e7aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579803"
---
# <a name="tabular-modeling-ssas-tabular"></a><span data-ttu-id="294ee-102">表格建模（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="294ee-102">Tabular Modeling (SSAS Tabular)</span></span>
  <span data-ttu-id="294ee-103">表格模型是 Analysis Services 中的内存中数据库。</span><span class="sxs-lookup"><span data-stu-id="294ee-103">Tabular models are in-memory databases in Analysis Services.</span></span> <span data-ttu-id="294ee-104">使用最先进的压缩算法和多线程查询处理器，xVelocity 内存中分析引擎 (VertiPaq) 可通过报表客户端应用程序（如 Microsoft Excel 和 Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]）来快速访问表格模型对象和数据。</span><span class="sxs-lookup"><span data-stu-id="294ee-104">Using state-of-the-art compression algorithms and multi-threaded query processor, the xVelocity in-memory analytics engine (VertiPaq) delivers fast access to tabular model objects and data by reporting client applications such as Microsoft Excel and Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
 <span data-ttu-id="294ee-105">表格模型通过两种模式支持数据访问：缓存模式和 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="294ee-105">Tabular models support data access through two modes: Cached mode and DirectQuery mode.</span></span> <span data-ttu-id="294ee-106">在缓存模式中，可以集成多个源的数据，包括关系数据库、数据馈送和平面文本文件。</span><span class="sxs-lookup"><span data-stu-id="294ee-106">In cached mode, you can integrate data from multiple sources including relational databases, data feeds, and flat text files.</span></span> <span data-ttu-id="294ee-107">在 DirectQuery 模式中，可以绕开内存中模型，允许客户端应用程序直接在（SQL Server 关系）源上查询数据。</span><span class="sxs-lookup"><span data-stu-id="294ee-107">In DirectQuery mode, you can bypass the in-memory model, allowing client applications to query data directly at the (SQL Server relational) source.</span></span>  
  
 <span data-ttu-id="294ee-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中使用新的表格模型项目模板创建表格模型。</span><span class="sxs-lookup"><span data-stu-id="294ee-108">Tabular models are authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] using new tabular model project templates.</span></span> <span data-ttu-id="294ee-109">您可以从多个源导入数据，然后通过添加关系、计算列、度量值、KPI 和层次结构来丰富模型。</span><span class="sxs-lookup"><span data-stu-id="294ee-109">You can import data from multiple sources, and then enrich the model by adding relationships, calculated columns, measures, KPIs, and hierarchies.</span></span> <span data-ttu-id="294ee-110">然后可以将模型部署到客户端报告应用程序可以连接到的 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="294ee-110">Models can then be deployed to an instance of Analysis Services where client reporting applications can connect to them.</span></span> <span data-ttu-id="294ee-111">可以在 SQL Server Management Studio 中管理已部署的模型，就像管理多维模型一样。</span><span class="sxs-lookup"><span data-stu-id="294ee-111">Deployed models can be managed in SQL Server Management Studio just like multidimensional models.</span></span> <span data-ttu-id="294ee-112">还可以对它们进行分区以便优化处理，并使用基于角色的安全性保护行级数据安全。</span><span class="sxs-lookup"><span data-stu-id="294ee-112">They can also be partitioned for optimized processing and secured to the row-level by using role based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="294ee-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="294ee-113">In This Section</span></span>  
 [<span data-ttu-id="294ee-114">表格模型解决方案（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="294ee-114">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
 [<span data-ttu-id="294ee-115">表格模型数据库（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="294ee-115">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-model-databases-ssas-tabular.md)  
  
 [<span data-ttu-id="294ee-116">表格模型数据访问</span><span class="sxs-lookup"><span data-stu-id="294ee-116">Tabular Model Data Access</span></span>](tabular-model-data-access.md)  
  
  
