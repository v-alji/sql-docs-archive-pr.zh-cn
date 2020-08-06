---
title: 使用外部数据源提供订阅方数据（数据驱动订阅）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriber data sources [Reporting Services]
- subscriptions [Reporting Services], external data sources
- query-based subscriptions [Reporting Services]
- external data sources [Reporting Services]
- data-driven subscriptions
- data sources [Reporting Services], subscriptions
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e23da709289ffb6ca345bb6211f40388877a1a87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692640"
---
# <a name="use-an-external-data-source-for-subscriber-data-data-driven-subscription"></a><span data-ttu-id="c59c7-102">使用外部数据源提供订阅方数据（数据驱动订阅）</span><span class="sxs-lookup"><span data-stu-id="c59c7-102">Use an External Data Source for Subscriber Data (Data-Driven Subscription)</span></span>
  <span data-ttu-id="c59c7-103">在数据驱动订阅中，动态订阅数据是由从外部数据源检索数据的查询或命令提供的。</span><span class="sxs-lookup"><span data-stu-id="c59c7-103">In a data-driven subscription, dynamic subscription data is provided by a query or command that retrieves data from an external data source.</span></span> <span data-ttu-id="c59c7-104">可以从满足数据驱动订阅处理要求的任何支持数据源中检索订阅数据。</span><span class="sxs-lookup"><span data-stu-id="c59c7-104">Subscription data can be retrieved from any supported data source that meets the requirements for data-driven subscription processing.</span></span> <span data-ttu-id="c59c7-105">查询或命令语法必须对随报表服务器安装的数据处理扩展插件有效。</span><span class="sxs-lookup"><span data-stu-id="c59c7-105">The query or command syntax must be valid for a data processing extension installed with your report server.</span></span>  
  
## <a name="data-processing-requirements"></a><span data-ttu-id="c59c7-106">数据处理要求</span><span class="sxs-lookup"><span data-stu-id="c59c7-106">Data Processing Requirements</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c59c7-107">使用数据处理扩展插件检索订阅数据。</span><span class="sxs-lookup"><span data-stu-id="c59c7-107">uses data processing extensions to retrieve subscription data.</span></span> <span data-ttu-id="c59c7-108">建议的数据源类型包括以下各项：</span><span class="sxs-lookup"><span data-stu-id="c59c7-108">Recommended data source types include the following:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c59c7-109">关系数据库</span><span class="sxs-lookup"><span data-stu-id="c59c7-109">relational databases</span></span>  
  
-   <span data-ttu-id="c59c7-110">Oracle 数据库</span><span class="sxs-lookup"><span data-stu-id="c59c7-110">Oracle databases</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c59c7-111">多维和数据挖掘数据源</span><span class="sxs-lookup"><span data-stu-id="c59c7-111">multidimensional and data mining data sources</span></span>  
  
-   <span data-ttu-id="c59c7-112">XML 数据源</span><span class="sxs-lookup"><span data-stu-id="c59c7-112">XML data sources</span></span>  
  
     <span data-ttu-id="c59c7-113">使用 XML 数据处理扩展插件处理订阅服务器数据时，请确保在订阅中增加查询超时设置。</span><span class="sxs-lookup"><span data-stu-id="c59c7-113">When using the XML data processing extension for subscriber data, be sure to increase the query timeout settings in the subscription.</span></span> <span data-ttu-id="c59c7-114">XML 数据处理扩展插件使用毫秒（而不是秒）来表示查询超时值。</span><span class="sxs-lookup"><span data-stu-id="c59c7-114">The XML data processing extension uses milliseconds rather than seconds for query timeout values.</span></span> <span data-ttu-id="c59c7-115">如果您没有增加超时值，则订阅可能会因处理时间不足而失败。</span><span class="sxs-lookup"><span data-stu-id="c59c7-115">If you do not increase the timeout value, the subscription might fail due to insufficient processing time.</span></span>  
  
     <span data-ttu-id="c59c7-116">配置与订阅服务器数据源的连接时，应避免使用 **“不需要凭据”** 选项。</span><span class="sxs-lookup"><span data-stu-id="c59c7-116">Avoid using the **Credentials are not required** option when configuring the connection to the subscriber data source.</span></span> <span data-ttu-id="c59c7-117">在运行时使用 XML 数据处理扩展插件检索订阅数据时，建议使用存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="c59c7-117">Stored credentials are recommended when using the XML data processing extension to retrieve subscription data at run time.</span></span>  
  
 <span data-ttu-id="c59c7-118">您可能可以使用其他支持的数据源类型，但并不能保证所有的数据源类型都能正常发挥作用。</span><span class="sxs-lookup"><span data-stu-id="c59c7-118">You might be able to use other supported data source types, but not all of them are guaranteed to work.</span></span> <span data-ttu-id="c59c7-119">例如，以下数据源类型不能用于订阅服务器数据：</span><span class="sxs-lookup"><span data-stu-id="c59c7-119">For example, the following data source types cannot be used for subscriber data:</span></span>  
  
-   <span data-ttu-id="c59c7-120">SAP Netweaver BI 数据源</span><span class="sxs-lookup"><span data-stu-id="c59c7-120">SAP Netweaver BI databases</span></span>  
  
-   <span data-ttu-id="c59c7-121">报表模型</span><span class="sxs-lookup"><span data-stu-id="c59c7-121">report models</span></span>  
  
 <span data-ttu-id="c59c7-122">如果你有要在数据驱动订阅中使用的自定义数据处理扩展插件，则它必须实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 接口。</span><span class="sxs-lookup"><span data-stu-id="c59c7-122">If you have a custom data processing extension that you want to use in data-driven subscriptions, it must implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> and the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interfaces.</span></span> <span data-ttu-id="c59c7-123">数据处理扩展插件必须支持仅限架构的查询执行。</span><span class="sxs-lookup"><span data-stu-id="c59c7-123">The data processing extension must support a schema-only query execution.</span></span> <span data-ttu-id="c59c7-124">此查询用于在设计时检索列元数据，以使用户可以将列映射到订阅定义中的传递选项和报表参数。</span><span class="sxs-lookup"><span data-stu-id="c59c7-124">This query is used to retrieve column metadata at design-time so that users can map columns to delivery options and report parameters in the subscription definition.</span></span> <span data-ttu-id="c59c7-125">仅限架构的查询执行发生在用户定义订阅的初期阶段。</span><span class="sxs-lookup"><span data-stu-id="c59c7-125">Schema-only query execution occurs at an early stage when the user is defining the subscription.</span></span>  
  
## <a name="query-requirements"></a><span data-ttu-id="c59c7-126">查询要求</span><span class="sxs-lookup"><span data-stu-id="c59c7-126">Query Requirements</span></span>  
 <span data-ttu-id="c59c7-127">创建用于检索订阅数据的查询时，请牢记以下要点：</span><span class="sxs-lookup"><span data-stu-id="c59c7-127">When creating query that retrieves subscription data, keep the following points in mind:</span></span>  
  
-   <span data-ttu-id="c59c7-128">只能为订阅创建一个查询。</span><span class="sxs-lookup"><span data-stu-id="c59c7-128">You can only create one query for the subscription.</span></span>  
  
-   <span data-ttu-id="c59c7-129">查询必须返回所有要用于传递选项和用于指定报表参数的值。</span><span class="sxs-lookup"><span data-stu-id="c59c7-129">The query must return all of the values that you want to use for delivery options and for specifying report parameters.</span></span>  
  
-   <span data-ttu-id="c59c7-130">报表服务器将为结果集中的每一行都创建一个报表传递。</span><span class="sxs-lookup"><span data-stu-id="c59c7-130">The report server will create a report delivery for every row in the result set.</span></span> <span data-ttu-id="c59c7-131">如果结果集包含三百多行，则报表服务器将尝试传递三百个报表。</span><span class="sxs-lookup"><span data-stu-id="c59c7-131">If the result set consists of three hundred rows, the report server will attempt to deliver three hundred reports.</span></span>  
  
## <a name="setting-delivery-options-using-variable-data-from-a-subscriber-database"></a><span data-ttu-id="c59c7-132">使用订阅服务器数据库中的变量数据设置传递选项</span><span class="sxs-lookup"><span data-stu-id="c59c7-132">Setting Delivery Options Using Variable Data from a Subscriber Database</span></span>  
 <span data-ttu-id="c59c7-133">可以使用订阅服务器数据库中的数据为每个接收者自定义传递选项。</span><span class="sxs-lookup"><span data-stu-id="c59c7-133">You can use data in the subscriber database to customize delivery options for each recipient.</span></span> <span data-ttu-id="c59c7-134">您所使用的传递扩展插件的类型将确定哪些选项是可用的。</span><span class="sxs-lookup"><span data-stu-id="c59c7-134">The kind of delivery extension you are using determines which options are available.</span></span> <span data-ttu-id="c59c7-135">如果正在使用报表服务器电子邮件传递扩展插件，则该查询应包含每个订阅方的电子邮件别名。</span><span class="sxs-lookup"><span data-stu-id="c59c7-135">If you are using the report server e-mail delivery extension, the query should contain an e-mail alias for each subscriber.</span></span> <span data-ttu-id="c59c7-136">如果正在使用文件共享传递，则订阅方数据应包含可用于创建订阅方特定的报表文件或提供传递目标的值。</span><span class="sxs-lookup"><span data-stu-id="c59c7-136">If you are using file share delivery, the subscriber data should include values that can be used to create subscriber-specific report files or to provide a destination for the delivery.</span></span> <span data-ttu-id="c59c7-137">有关详细信息，请参阅[中的文件共享传递 Reporting Services](file-share-delivery-in-reporting-services.md)和[Reporting Services 中的电子邮件传递](e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c59c7-137">For more information, see [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) and [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
## <a name="passing-parameter-values-from-the-subscriber-database-to-the-report"></a><span data-ttu-id="c59c7-138">将参数值从订阅服务器数据库传递到报表</span><span class="sxs-lookup"><span data-stu-id="c59c7-138">Passing Parameter Values from the Subscriber Database to the Report</span></span>  
 <span data-ttu-id="c59c7-139">如果要为参数化报表创建数据驱动订阅，则可以使用变量参数值来自定义每个报表的输出。</span><span class="sxs-lookup"><span data-stu-id="c59c7-139">If you are creating a data-driven subscription for a parameterized report, you can use variable parameter values to customize the output of each report.</span></span> <span data-ttu-id="c59c7-140">例如，订阅服务器数据库可能包含雇员标识号、雇用日期、职务和办公地点信息，这些信息可用来筛选报表数据。</span><span class="sxs-lookup"><span data-stu-id="c59c7-140">For example, the subscriber database might contain employee identification numbers, hire dates, job titles, and office location information that can be used to filter report data.</span></span> <span data-ttu-id="c59c7-141">如果报表接受基于这些数据或其他可用列数据的参数，则可以将参数映射到相应的列。</span><span class="sxs-lookup"><span data-stu-id="c59c7-141">If the report accepts parameters that are based on these or other available column data, you can map the parameter to the appropriate column.</span></span>  
  
 <span data-ttu-id="c59c7-142">将订阅方字段映射到报表参数时，请确保数据类型和列长度相符。</span><span class="sxs-lookup"><span data-stu-id="c59c7-142">When mapping subscriber fields to report parameters, make sure that the data types and column lengths are compatible.</span></span> <span data-ttu-id="c59c7-143">如果数据类型不匹配，则在订阅处理过程中将会出现错误。</span><span class="sxs-lookup"><span data-stu-id="c59c7-143">If there is a data type mismatch, an error will occur during subscription processing.</span></span> <span data-ttu-id="c59c7-144">若要了解有关使用参数化报表中订阅方数据的详细信息，请参阅[创建数据驱动订阅（SSRS 教程）](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="c59c7-144">To learn more about using subscriber data in a parameterized report, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
## <a name="modifying-the-subscriber-data-source"></a><span data-ttu-id="c59c7-145">修改订阅方数据源</span><span class="sxs-lookup"><span data-stu-id="c59c7-145">Modifying the Subscriber Data Source</span></span>  
 <span data-ttu-id="c59c7-146">对订阅方数据源进行以下修改将会阻止订阅运行：</span><span class="sxs-lookup"><span data-stu-id="c59c7-146">The following modifications to the subscriber data source can prevent the subscription from running:</span></span>  
  
-   <span data-ttu-id="c59c7-147">删除订阅中引用的列。</span><span class="sxs-lookup"><span data-stu-id="c59c7-147">Removing columns that are referenced in the subscription.</span></span>  
  
-   <span data-ttu-id="c59c7-148">修改数据源的表结构。</span><span class="sxs-lookup"><span data-stu-id="c59c7-148">Modifying the table structure of the data source.</span></span>  
  
-   <span data-ttu-id="c59c7-149">更改数据类型和其他列属性。</span><span class="sxs-lookup"><span data-stu-id="c59c7-149">Changing data type and other column properties.</span></span>  
  
 <span data-ttu-id="c59c7-150">如果执行了上述任何更改，则必须更新订阅。</span><span class="sxs-lookup"><span data-stu-id="c59c7-150">If you make any of these changes, you must update the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c59c7-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c59c7-151">See Also</span></span>  
 <span data-ttu-id="c59c7-152">[创建、修改和删除数据驱动订阅](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="c59c7-152">[Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="c59c7-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="c59c7-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="c59c7-154">订阅和传递 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="c59c7-154">Subscriptions and Delivery &#40;Reporting Services&#41;</span></span>](subscriptions-and-delivery-reporting-services.md)  
  
  
