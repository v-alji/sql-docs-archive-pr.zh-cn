---
title: " (SSAS) 的多维建模 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 509df042-fdb3-4e2c-a6b8-86943ce1b0fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7348a932eccb62f2e00c0b154ca9efc8086fcd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694623"
---
# <a name="multidimensional-modeling-ssas"></a><span data-ttu-id="b07c6-102">多维建模 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b07c6-102">Multidimensional Modeling (SSAS)</span></span>
  <span data-ttu-id="b07c6-103">Analysis Services 多维解决方案使用多维数据集结构来分析多个维度之间的业务数据。</span><span class="sxs-lookup"><span data-stu-id="b07c6-103">An Analysis Services multidimensional solution uses cube structures for analyzing business data across multiple dimensions.</span></span> <span data-ttu-id="b07c6-104">多维模式是 Analysis Services 的默认服务器模式。</span><span class="sxs-lookup"><span data-stu-id="b07c6-104">Multidimensional mode is the default server mode of Analysis Services.</span></span> <span data-ttu-id="b07c6-105">它包括针对 OLAP 数据的查询和计算引擎，并且具有 MOLAP、ROLAP 和 HOLAP 存储模式以便在性能和数据可伸缩性要求之间进行权衡。</span><span class="sxs-lookup"><span data-stu-id="b07c6-105">It includes a query and calculation engine for OLAP data, with MOLAP, ROLAP, and HOLAP storage modes to balance performance with scalable data requirements.</span></span> <span data-ttu-id="b07c6-106">Analysis Services OLAP 引擎是行业领先的 OLAP 服务器，能够与多种 BI 工具很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="b07c6-106">The Analysis Services OLAP engine is an industry leading OLAP server that works well with a broad range of BI tools.</span></span> <span data-ttu-id="b07c6-107">大多数 Analysis Services 部署都作为典型的 OLAP 服务器进行安装。</span><span class="sxs-lookup"><span data-stu-id="b07c6-107">Most Analysis Services deployments are installed as classic OLAP servers.</span></span>  
  
## <a name="benefits-of-using-multidimensional-solutions"></a><span data-ttu-id="b07c6-108">使用多维解决方案所带来的好处</span><span class="sxs-lookup"><span data-stu-id="b07c6-108">Benefits of Using Multidimensional Solutions</span></span>  
 <span data-ttu-id="b07c6-109">之所以生成 Analysis Services 多维模型，主要是为了实现对业务数据的即席查询的高性能。</span><span class="sxs-lookup"><span data-stu-id="b07c6-109">The primary reason for building an Analysis Services multidimensional model is to achieve fast performance of ad hoc queries against business data.</span></span> <span data-ttu-id="b07c6-110">多维模型由多维数据集和维度组成，可对这些多维数据集和维度进行注释和扩展以支持复杂查询构造。</span><span class="sxs-lookup"><span data-stu-id="b07c6-110">A multidimensional model is composed of cubes and dimensions that can be annotated and extended to support complex query constructions.</span></span> <span data-ttu-id="b07c6-111">BI 开发人员创建多维数据集以支持快速响应，并提供单个数据源以进行业务报告。</span><span class="sxs-lookup"><span data-stu-id="b07c6-111">BI developers create cubes to support fast response times, and to provide a single data source for business reporting.</span></span> <span data-ttu-id="b07c6-112">鉴于商业智能在组织的各个层面的重要性不断提高，使用单一的分析数据源可确保将差异减到最小（如果无法完全消除差异）。</span><span class="sxs-lookup"><span data-stu-id="b07c6-112">Given the growing importance of business intelligence across all levels of an organization, having a single source of analytical data ensures that discrepancies are kept to a minimum, if not eliminated entirely.</span></span>  
  
 <span data-ttu-id="b07c6-113">使用 Analysis Services 多维数据库所带来的另一个重要好处是，可与常用的 BI 报表工具（如 Excel、Reporting Services 和 PerformancePoint）以及自定义应用程序和第三方解决方案集成。</span><span class="sxs-lookup"><span data-stu-id="b07c6-113">Another important benefit to using Analysis Services multidimensional databases is integration with commonly used BI reporting tools such as Excel, Reporting Services, and PerformancePoint, as well as custom applications and third-party solutions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b07c6-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="b07c6-114">In This Section</span></span>  
 [<span data-ttu-id="b07c6-115">多维模型解决方案 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b07c6-115">Multidimensional Model Solutions &#40;SSAS&#41;</span></span>](multidimensional-model-solutions-ssas.md)  
  
 [<span data-ttu-id="b07c6-116">多维模型数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b07c6-116">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-model-databases-ssas.md)  
  
 [<span data-ttu-id="b07c6-117">多维模型对象处理</span><span class="sxs-lookup"><span data-stu-id="b07c6-117">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="b07c6-118">角色和权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b07c6-118">Roles and Permissions &#40;Analysis Services&#41;</span></span>](roles-and-permissions-analysis-services.md)  
  
 [<span data-ttu-id="b07c6-119">用于多维模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="b07c6-119">Power View for Multidimensional Models</span></span>](power-view-for-multidimensional-models.md)  
  
 [<span data-ttu-id="b07c6-120">多维模型程序集管理</span><span class="sxs-lookup"><span data-stu-id="b07c6-120">Multidimensional Model Assemblies Management</span></span>](multidimensional-model-assemblies-management.md)  
  
  
