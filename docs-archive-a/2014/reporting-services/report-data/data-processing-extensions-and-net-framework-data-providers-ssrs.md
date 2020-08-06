---
title: 数据处理扩展插件和 .NET Framework 数据提供程序 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd84af68af54b165c75317280bc19bb23da53366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687519"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a><span data-ttu-id="3f25b-102">数据处理扩展插件和 .NET Framework 数据访问接口 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="3f25b-102">Data Processing Extensions and .NET Framework Data Providers (SSRS)</span></span>
  <span data-ttu-id="3f25b-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据处理扩展插件是随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]安装的组件，用于从特定类型的数据源检索数据，并提供支持报表设计和报表处理的额外功能。</span><span class="sxs-lookup"><span data-stu-id="3f25b-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension is a component installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], designed to retrieve data from a specific type of data source and to provide extra functionality to support report design and report processing.</span></span> <span data-ttu-id="3f25b-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中或第三方源提供的组件，第三方源支持可使你检索和修改来自特定类型的数据源数据的 <xref:System.Data> 接口。</span><span class="sxs-lookup"><span data-stu-id="3f25b-104">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider is a component available from [!INCLUDE[msCoName](../../includes/msconame-md.md)] or third-party sources that supports <xref:System.Data> interfaces that allow you to retrieve and to modify data from a specific type of data source.</span></span>  
  
## <a name="understanding-a-data-processing-extension"></a><span data-ttu-id="3f25b-105">了解数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="3f25b-105">Understanding a Data Processing Extension</span></span>  
 <span data-ttu-id="3f25b-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据处理扩展插件支持 <xref:System.Data> 接口的子集。</span><span class="sxs-lookup"><span data-stu-id="3f25b-106">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension supports a subset of the <xref:System.Data> interfaces.</span></span> <span data-ttu-id="3f25b-107">数据处理扩展插件要求对数据源进行只读访问，因此不实现写入接口和更新接口。</span><span class="sxs-lookup"><span data-stu-id="3f25b-107">Data processing extensions require only read-only access to a data source, so the interfaces for write and update are not implemented.</span></span> <span data-ttu-id="3f25b-108">每个数据处理扩展插件都可提供自定义功能，以支持报表处理。</span><span class="sxs-lookup"><span data-stu-id="3f25b-108">Each data processing extension can provide custom features to support report processing.</span></span> <span data-ttu-id="3f25b-109">例如，数据处理扩展插件可能会支持下列功能类型：</span><span class="sxs-lookup"><span data-stu-id="3f25b-109">For example, a data processing extension might support the following types of features:</span></span>  
  
-   <span data-ttu-id="3f25b-110">在连接字符串之外单独管理凭据</span><span class="sxs-lookup"><span data-stu-id="3f25b-110">Managing credentials separately from the connection string</span></span>  
  
-   <span data-ttu-id="3f25b-111">支持多值参数</span><span class="sxs-lookup"><span data-stu-id="3f25b-111">Supporting multivalue parameters</span></span>  
  
-   <span data-ttu-id="3f25b-112">检索对数据源计算的服务器聚合</span><span class="sxs-lookup"><span data-stu-id="3f25b-112">Retrieving server aggregates, which are calculated on the data source</span></span>  
  
-   <span data-ttu-id="3f25b-113">从数据源检索数据属性和数据值</span><span class="sxs-lookup"><span data-stu-id="3f25b-113">Retrieving data properties as well as data values from the data source</span></span>  
  
## <a name="understanding-a-data-provider"></a><span data-ttu-id="3f25b-114">了解数据访问接口</span><span class="sxs-lookup"><span data-stu-id="3f25b-114">Understanding a Data Provider</span></span>  
 <span data-ttu-id="3f25b-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序（有时称为驱动程序）支持一组用于在数据源读取、写入和更新数据的标准 <xref:System.Data> 接口。</span><span class="sxs-lookup"><span data-stu-id="3f25b-115">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider (sometimes known as a driver) supports a standard set of <xref:System.Data> interfaces for reading, writing, and updating data on a data source.</span></span> <span data-ttu-id="3f25b-116">对于特定类型的数据源，如果没有可用的数据处理扩展插件，则可以使用数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="3f25b-116">A data provider can be used when there is no data processing extension available for a specific type of data source.</span></span> <span data-ttu-id="3f25b-117">有许多第三方标准 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口可用。</span><span class="sxs-lookup"><span data-stu-id="3f25b-117">Many third-party standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers are available.</span></span>  
  
 <span data-ttu-id="3f25b-118">因为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 具有一个可扩展的数据访问接口体系结构，所以您可以创建自定义数据处理扩展插件以包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据处理扩展插件提供的额外功能。</span><span class="sxs-lookup"><span data-stu-id="3f25b-118">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has an extensible data provider architecture, you can build a custom data processing extension to include the extra functionality supplied by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="3f25b-119">有关详细信息，请参阅 [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3f25b-119">For more information, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span> <span data-ttu-id="3f25b-120">有关第三方数据处理扩展插件的信息，请参阅第三方数据处理扩展插件的随附文档。</span><span class="sxs-lookup"><span data-stu-id="3f25b-120">For third-party data processing extensions, see the documentation that comes with the third-party data processing extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f25b-121">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口或自定义数据处理扩展插件必须先行安装并注册，然后才能用于访问数据源中的数据。</span><span class="sxs-lookup"><span data-stu-id="3f25b-121">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or custom data processing extension must be installed and registered before it can be used to access data from a data source.</span></span> <span data-ttu-id="3f25b-122">必须同时在报表客户端和报表服务器安装并注册数据处理扩展插件，以便创作报表和查看已发布的报表。</span><span class="sxs-lookup"><span data-stu-id="3f25b-122">The data processing extension must be installed and registered both on the reporting client to author the report and on the report server to view the published report.</span></span> <span data-ttu-id="3f25b-123">不是所有数据访问接口都设计为在服务器环境中工作。</span><span class="sxs-lookup"><span data-stu-id="3f25b-123">Not all data providers are designed to work in a server environment.</span></span> <span data-ttu-id="3f25b-124">有关详细信息，请参阅[注册标准 .NET Framework 数据提供程序 (SSRS)](register-a-standard-net-framework-data-provider-ssrs.md) 和[部署数据处理扩展插件](../extensions/data-processing/deploying-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3f25b-124">For more information, see [Register a Standard .NET Framework Data Provider &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md).and [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f25b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f25b-125">See Also</span></span>  
 <span data-ttu-id="3f25b-126">[数据处理扩展插件概述](../extensions/data-processing/data-processing-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3f25b-126">[Data Processing Extensions Overview](../extensions/data-processing/data-processing-extensions-overview.md) </span></span>  
 [<span data-ttu-id="3f25b-127">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3f25b-127">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
