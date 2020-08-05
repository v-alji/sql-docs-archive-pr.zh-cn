---
title: 数据驱动订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b59d5cc447191bef526d4cf4399a841d68932886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580562"
---
# <a name="data-driven-subscriptions"></a><span data-ttu-id="c0495-102">数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="c0495-102">Data-Driven Subscriptions</span></span>
  <span data-ttu-id="c0495-103">数据驱动订阅提供了一种使用动态订阅数据的方式，这些数据是在运行时从外部数据源中检索的。</span><span class="sxs-lookup"><span data-stu-id="c0495-103">A data-driven subscription provides a way to use dynamic subscription data that is retrieved from an external data source at run time.</span></span> <span data-ttu-id="c0495-104">数据驱动订阅还可以使用定义订阅时指定的静态文本和默认值。</span><span class="sxs-lookup"><span data-stu-id="c0495-104">A data-driven subscription can also use static text and default values that you specify when the subscription is defined.</span></span> <span data-ttu-id="c0495-105">可以使用数据驱动订阅来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c0495-105">You can use data-driven subscriptions to do the following:</span></span>  
  
-   <span data-ttu-id="c0495-106">向可以变动的订阅方列表分发报表。</span><span class="sxs-lookup"><span data-stu-id="c0495-106">Distribute a report to a fluctuating list of subscribers.</span></span> <span data-ttu-id="c0495-107">例如，您可以使用数据驱动订阅在订阅方会逐月变化的大型单位中分发报表，也可以使用其他条件在一组现有用户中确定组成员身份。</span><span class="sxs-lookup"><span data-stu-id="c0495-107">For example, you can use data-driven subscriptions to distribute a report throughout a large organization where subscribers vary from one month to the next, or use other criteria that determines group membership from an existing set of users.</span></span>  
  
-   <span data-ttu-id="c0495-108">使用在运行时检索的报表参数值筛选报表输出。</span><span class="sxs-lookup"><span data-stu-id="c0495-108">Filter the report output using report parameter values that are retrieved at run time.</span></span>  
  
-   <span data-ttu-id="c0495-109">更改报表输出格式和每个报表传递的传递选项。</span><span class="sxs-lookup"><span data-stu-id="c0495-109">Vary report output formats and delivery options for each report delivery.</span></span>  
  
 <span data-ttu-id="c0495-110">数据驱动订阅由多个部分组成。</span><span class="sxs-lookup"><span data-stu-id="c0495-110">A data-driven subscription is composed of multiple parts.</span></span> <span data-ttu-id="c0495-111">数据驱动订阅所涉及的固定方面是在创建订阅时定义的，其中包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="c0495-111">The fixed aspects of a data-driven subscription are defined when you create the subscription, and these include the following:</span></span>  
  
-   <span data-ttu-id="c0495-112">为其定义订阅的报表（订阅始终与单个报表相关联）。</span><span class="sxs-lookup"><span data-stu-id="c0495-112">The report for which the subscription is defined (a subscription is always associated with a single report).</span></span>  
  
-   <span data-ttu-id="c0495-113">用于分发报表的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0495-113">The delivery extension used to distribute the report.</span></span> <span data-ttu-id="c0495-114">可以指定报表服务器电子邮件传递、文件共享传递、用于预加载缓存的 Null 传递提供程序或自定义传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0495-114">You can specify report server e-mail delivery, file share delivery, the null delivery provider used for preloading the cache, or a custom delivery extension.</span></span> <span data-ttu-id="c0495-115">不能在单个订阅中指定多个传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0495-115">You cannot specify multiple delivery extensions within a single subscription.</span></span>  
  
-   <span data-ttu-id="c0495-116">订阅方数据源。</span><span class="sxs-lookup"><span data-stu-id="c0495-116">The subscriber data source.</span></span> <span data-ttu-id="c0495-117">定义订阅时，您必须为包含订阅方数据的数据源指定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="c0495-117">You must specify a connection string to the data source that contains subscriber data when you define the subscription.</span></span> <span data-ttu-id="c0495-118">不能在运行时动态指定订阅方数据源。</span><span class="sxs-lookup"><span data-stu-id="c0495-118">The subscriber data source cannot be specified dynamically at run time.</span></span>  
  
-   <span data-ttu-id="c0495-119">定义订阅时必须指定用于选择订阅方数据的查询。</span><span class="sxs-lookup"><span data-stu-id="c0495-119">The query that you use to select subscriber data must be specified when you define the subscription.</span></span> <span data-ttu-id="c0495-120">不能在运行时更改该查询。</span><span class="sxs-lookup"><span data-stu-id="c0495-120">You cannot change the query at run time.</span></span>  
  
 <span data-ttu-id="c0495-121">数据驱动订阅中使用的动态值是在处理订阅时获取的。</span><span class="sxs-lookup"><span data-stu-id="c0495-121">Dynamic values used in a data-driven subscription are obtained when the subscription is processed.</span></span> <span data-ttu-id="c0495-122">在订阅中可能使用的变量数据示例包括订阅方名称、电子邮件地址、首选的报表输出格式或任何对报表参数有效的值。</span><span class="sxs-lookup"><span data-stu-id="c0495-122">Examples of variable data that you might use in a subscription include the subscriber name, e-mail address, preferred report output format, or any value that is valid for a report parameter.</span></span> <span data-ttu-id="c0495-123">若要在数据驱动订阅中使用动态值，可以在查询中为特定传递选项和报表参数返回的字段之间定义映射。</span><span class="sxs-lookup"><span data-stu-id="c0495-123">To use dynamic values in a data-driven subscription, you define a mapping between the fields that are returned in the query to specific delivery options and to report parameters.</span></span> <span data-ttu-id="c0495-124">每次处理订阅时，都将从订阅方数据源中检索变量数据。</span><span class="sxs-lookup"><span data-stu-id="c0495-124">Variable data is retrieved from a subscriber data source each time the subscription is processed.</span></span>  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a><span data-ttu-id="c0495-125">使用数据驱动订阅的要求</span><span class="sxs-lookup"><span data-stu-id="c0495-125">Requirements for using Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="c0495-126">数据驱动订阅功能并不是在所有的版本中都可用。</span><span class="sxs-lookup"><span data-stu-id="c0495-126">Data-driven subscription functionality is not available in all editions.</span></span> <span data-ttu-id="c0495-127">对于在运行时可用于检索订阅数据的数据源种类还有一些限制。</span><span class="sxs-lookup"><span data-stu-id="c0495-127">There are also limitations on the kinds of data sources that you can use to retrieve subscription data at run time.</span></span> <span data-ttu-id="c0495-128">以下列表提供了有关这些要求的详细信息：</span><span class="sxs-lookup"><span data-stu-id="c0495-128">The following list provides more information about the requirements:</span></span>  
  
-   <span data-ttu-id="c0495-129">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持数据驱动订阅功能的版本的详细信息，请参阅 SQL Server 2012 (的各个[版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="c0495-129">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Data-driven subscription functionality, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="c0495-130">对于订阅数据，请选择可为报表服务器提供架构信息的数据源。</span><span class="sxs-lookup"><span data-stu-id="c0495-130">For subscription data, choose a data source that can provide schema information to the report server.</span></span> <span data-ttu-id="c0495-131">支持的数据源类型的示例包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 关系数据、Oracle、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包数据、ODBC 数据源以及 OLE DB 数据源。</span><span class="sxs-lookup"><span data-stu-id="c0495-131">Examples of supported data source types include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational data, Oracle, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package data, ODBC data sources, and OLE DB data sources.</span></span> <span data-ttu-id="c0495-132">有关订阅方数据源要求的详细信息，请参阅 [使用外部数据源提供订阅方数据（数据驱动订阅）](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c0495-132">For more information about subscriber data source requirements, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
## <a name="working-with-data-driven-subscriptions"></a><span data-ttu-id="c0495-133">处理数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="c0495-133">Working with Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="c0495-134">以下主题介绍有关数据驱动订阅的详细信息：</span><span class="sxs-lookup"><span data-stu-id="c0495-134">The following topics provide more information about data-driven subscriptions.</span></span>  
  
|<span data-ttu-id="c0495-135">主题</span><span class="sxs-lookup"><span data-stu-id="c0495-135">Topics</span></span>|<span data-ttu-id="c0495-136">说明</span><span class="sxs-lookup"><span data-stu-id="c0495-136">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0495-137">Create, Modify, and Delete a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="c0495-137">Create, Modify, and Delete a Data-Driven Subscription</span></span>](data-driven-subscriptions.md)|<span data-ttu-id="c0495-138">介绍如何创建、修改和删除数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="c0495-138">Explains how to create, modify, or delete a data-driven subscription.</span></span>|  
|[<span data-ttu-id="c0495-139">使用外部数据源提供订阅方数据（数据驱动订阅）</span><span class="sxs-lookup"><span data-stu-id="c0495-139">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|<span data-ttu-id="c0495-140">介绍有关可用于数据驱动订阅的数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="c0495-140">Provides information about the data sources that you can use for a data-driven subscription.</span></span>|  
|[<span data-ttu-id="c0495-141">创建数据驱动订阅（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="c0495-141">Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;</span></span>](../create-a-data-driven-subscription-ssrs-tutorial.md)|<span data-ttu-id="c0495-142">逐步介绍如何创建数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="c0495-142">Provides step-by-step instruction for learning how to create a data-driven subscription.</span></span>|  
|[<span data-ttu-id="c0495-143">缓存报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="c0495-143">Caching Reports &#40;SSRS&#41;</span></span>](../report-server/caching-reports-ssrs.md)|<span data-ttu-id="c0495-144">介绍如何对数据驱动订阅使用 Null 传递提供程序来预先加载缓存。</span><span class="sxs-lookup"><span data-stu-id="c0495-144">Describes how to use the Null Delivery Provider with a data-driven subscription to preload the cache.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0495-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0495-145">See Also</span></span>  
 <span data-ttu-id="c0495-146">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c0495-146">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="c0495-147">[创建数据驱动订阅页 &#40;报表管理器&#41;](../create-data-driven-subscription-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c0495-147">[Create Data-driven Subscription Page &#40;Report Manager&#41;](../create-data-driven-subscription-page-report-manager.md) </span></span>  
 [<span data-ttu-id="c0495-148">预加载缓存（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="c0495-148">Preload the Cache &#40;Report Manager&#41;</span></span>](../report-server/preload-the-cache-report-manager.md)  
  
  
