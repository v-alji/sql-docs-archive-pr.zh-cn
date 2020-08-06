---
title: 监视包执行和其他操作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 628b62d9c8e01d0dc0bf641551de67c3838a4504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591474"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a><span data-ttu-id="63570-102">监视包执行和其他操作</span><span class="sxs-lookup"><span data-stu-id="63570-102">Monitoring for Package Executions and Other Operations</span></span>
  <span data-ttu-id="63570-103">您可以使用以下一个或多个工具监视 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包执行、项目验证和其他操作。</span><span class="sxs-lookup"><span data-stu-id="63570-103">You can monitor [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package executions, project validations, and other operations by using one of more of the following tools.</span></span> <span data-ttu-id="63570-104">某些工具（如数据分流）只适用于部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的项目。</span><span class="sxs-lookup"><span data-stu-id="63570-104">Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="63570-105">日志</span><span class="sxs-lookup"><span data-stu-id="63570-105">Logs</span></span>  
  
     <span data-ttu-id="63570-106">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="63570-106">For more information, see [Integration Services &#40;SSIS&#41; Logging](integration-services-ssis-logging.md).</span></span>  
  
-   <span data-ttu-id="63570-107">报表</span><span class="sxs-lookup"><span data-stu-id="63570-107">Reports</span></span>  
  
     <span data-ttu-id="63570-108">有关详细信息，请参阅 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="63570-108">For more information, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
-   <span data-ttu-id="63570-109">视图</span><span class="sxs-lookup"><span data-stu-id="63570-109">Views</span></span>  
  
     <span data-ttu-id="63570-110">有关详细信息，请参阅[视图（Integration Services 目录）](/sql/integration-services/system-views/views-integration-services-catalog)。</span><span class="sxs-lookup"><span data-stu-id="63570-110">For more information, see [Views &#40;Integration Services Catalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog).</span></span>  
  
-   <span data-ttu-id="63570-111">性能计数器</span><span class="sxs-lookup"><span data-stu-id="63570-111">Performance counters</span></span>  
  
     <span data-ttu-id="63570-112">有关详细信息，请参阅 [性能计时器](performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="63570-112">For more information, see [Performance Counters](performance-counters.md).</span></span>  
  
-   <span data-ttu-id="63570-113">数据分流</span><span class="sxs-lookup"><span data-stu-id="63570-113">Data taps</span></span>  
  
## <a name="operation-types"></a><span data-ttu-id="63570-114">操作类型</span><span class="sxs-lookup"><span data-stu-id="63570-114">Operation Types</span></span>  
 <span data-ttu-id="63570-115">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的 `SSISDB` 目录中监视几种不同的操作类型。</span><span class="sxs-lookup"><span data-stu-id="63570-115">Several different types of operations are monitored in the `SSISDB` catalog, on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="63570-116">每个操作可以具有多个与其关联的消息。</span><span class="sxs-lookup"><span data-stu-id="63570-116">Each operation can have multiple messages associated with it.</span></span> <span data-ttu-id="63570-117">每个消息可划分为若干不同类型之一。</span><span class="sxs-lookup"><span data-stu-id="63570-117">Each message can be classified into one of several different types.</span></span> <span data-ttu-id="63570-118">例如，消息可以是信息、警告或错误类型。</span><span class="sxs-lookup"><span data-stu-id="63570-118">For example, a message can be of type Information, Warning, or Error.</span></span> <span data-ttu-id="63570-119">有关消息类型的完整列表，请参阅针对 Transact-SQL [catalog.operation_messages（SSISDB 数据库）](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database)视图的文档。</span><span class="sxs-lookup"><span data-stu-id="63570-119">For the full list of message types, see the documentation for the Transact-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) view.</span></span> <span data-ttu-id="63570-120">有关操作类型的完整列表，请参阅 [catalog.operations（SSISDB 数据库）](/sql/integration-services/system-views/catalog-operations-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="63570-120">For a full list of the operations types, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).</span></span>  
  
 <span data-ttu-id="63570-121">使用九种不同的状态类型来指示操作的状态。</span><span class="sxs-lookup"><span data-stu-id="63570-121">Nine different status types are used to indicate the status of an operation.</span></span> <span data-ttu-id="63570-122">有关状态类型的完整列表，请参阅 [catalog.operations（SSISDB 数据库）](/sql/integration-services/system-views/catalog-operations-ssisdb-database)视图。</span><span class="sxs-lookup"><span data-stu-id="63570-122">For a full list of the status types, see the [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="63570-123">相关内容</span><span class="sxs-lookup"><span data-stu-id="63570-123">Related Content</span></span>  
 <span data-ttu-id="63570-124">blogs.msdn.com 上的博客文章 [SSIS T-SQL API 概述](https://go.microsoft.com/fwlink/?LinkId=249051)。</span><span class="sxs-lookup"><span data-stu-id="63570-124">Blog entry, [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.</span></span>  
  
  
