---
title: 准备实现数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- data processing extensions [Reporting Services], implementing
ms.assetid: 698817e4-33da-4eb5-9407-4103e1c35247
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3588aea825233631cb4ad7752919ad88bb4dbf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693629"
---
# <a name="preparing-to-implement-a-data-processing-extension"></a><span data-ttu-id="11386-102">准备实现数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="11386-102">Preparing to Implement a Data Processing Extension</span></span>
  <span data-ttu-id="11386-103">在实现 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件之前，应定义要实现的接口。</span><span class="sxs-lookup"><span data-stu-id="11386-103">Before you implement your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="11386-104">你可能要提供整个接口组的特定于扩展插件的实现，或者只是要针对某一子集（例如 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 接口）提供实现，客户端在其中主要与作为 DataReader 对象的结果集交互，并且使用 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理扩展插件作为结果集和数据源之间的桥梁。</span><span class="sxs-lookup"><span data-stu-id="11386-104">You may want to provide extension-specific implementations of the entire set of interfaces, or you may simply want to focus your implementation on a subset, such as the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> interfaces in which clients would interact primarily with a result set as a **DataReader** object and would use your [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extension as a bridge between the result set and your data source.</span></span>  
  
 <span data-ttu-id="11386-105">然后，您可以通过以下两种方式之一实现数据处理扩展插件：</span><span class="sxs-lookup"><span data-stu-id="11386-105">You can implement data processing extensions in one of two ways:</span></span>  
  
-   <span data-ttu-id="11386-106">数据处理扩展插件类可以实现 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据提供程序接口，并且可以选择实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的扩展数据处理扩展插件接口。</span><span class="sxs-lookup"><span data-stu-id="11386-106">Your data processing extension classes can implement the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces and optionally the extended data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="11386-107">您的数据处理扩展插件类可以实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的数据处理扩展插件接口，并且可以选择实现扩展数据处理扩展插件接口。</span><span class="sxs-lookup"><span data-stu-id="11386-107">Your data processing extension classes can implement the data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and optionally the extended data processing extension interfaces.</span></span>  
  
 <span data-ttu-id="11386-108">如果您的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件将不支持某一特定的属性或方法，则将该属性或方法作为无操作实现。</span><span class="sxs-lookup"><span data-stu-id="11386-108">If your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension will not support a particular property or method, implement the property or method as no-operation.</span></span> <span data-ttu-id="11386-109">如果某一客户端期望特定的行为，则引发 NotSupportedException 异常  。</span><span class="sxs-lookup"><span data-stu-id="11386-109">If a client expects a particular behavior, throw a **NotSupportedException** exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11386-110">某一属性或方法的无操作实现只应用于您选择实现的那些接口的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="11386-110">A no-operation implementation of a property or method only applies to the properties and methods of those interfaces that you choose to implement.</span></span> <span data-ttu-id="11386-111">您选择不实现的可选接口应排除在您的数据处理扩展插件程序集之外。</span><span class="sxs-lookup"><span data-stu-id="11386-111">Optional interfaces that you choose not to implement should be left out of your data processing extension assembly.</span></span> <span data-ttu-id="11386-112">有关某一接口是必需接口还是可选接口的详细信息，请参阅本节后面的表。</span><span class="sxs-lookup"><span data-stu-id="11386-112">For more information about whether an interface is required or optional, see the table later in this section.</span></span>  
  
## <a name="required-extension-functionality"></a><span data-ttu-id="11386-113">必需的扩展插件功能</span><span class="sxs-lookup"><span data-stu-id="11386-113">Required Extension Functionality</span></span>  
 <span data-ttu-id="11386-114">每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件都必须提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="11386-114">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="11386-115">打开与数据源之间的连接。</span><span class="sxs-lookup"><span data-stu-id="11386-115">Open a connection to a data source.</span></span>  
  
-   <span data-ttu-id="11386-116">分析查询并返回结果集的字段名的列表。</span><span class="sxs-lookup"><span data-stu-id="11386-116">Analyze a query and return a list of field names for the result set.</span></span>  
  
-   <span data-ttu-id="11386-117">对数据源执行查询，并返回行集。</span><span class="sxs-lookup"><span data-stu-id="11386-117">Execute a query against the data source and return a row set.</span></span>  
  
-   <span data-ttu-id="11386-118">将单值参数传递到查询。</span><span class="sxs-lookup"><span data-stu-id="11386-118">Pass single-valued parameters to the query.</span></span>  
  
-   <span data-ttu-id="11386-119">遍历行集中的行，并检索数据。</span><span class="sxs-lookup"><span data-stu-id="11386-119">Iterate through rows in the row set and retrieve data.</span></span>  
  
 <span data-ttu-id="11386-120">可以扩展每个数据处理扩展插件以包含以下功能：</span><span class="sxs-lookup"><span data-stu-id="11386-120">Each data processing extension can be extended to include the following functionality:</span></span>  
  
-   <span data-ttu-id="11386-121">分析某一查询，并返回该查询中所使用的参数名称的列表。</span><span class="sxs-lookup"><span data-stu-id="11386-121">Analyze a query and return a list of parameter names used in the query.</span></span>  
  
-   <span data-ttu-id="11386-122">分析某一查询，并返回按该查询分组的字段的列表。</span><span class="sxs-lookup"><span data-stu-id="11386-122">Analyze a query and return the list of fields by which the query is grouped.</span></span>  
  
-   <span data-ttu-id="11386-123">分析某一查询，并返回按该查询排序的字段的列表。</span><span class="sxs-lookup"><span data-stu-id="11386-123">Analyze a query and return the list of fields by which the query is sorted.</span></span>  
  
-   <span data-ttu-id="11386-124">提供用户名和密码以连接到独立于连接字符串的数据源。</span><span class="sxs-lookup"><span data-stu-id="11386-124">Provide a user name and password to connect to the data source that is independent of the connection string.</span></span>  
  
-   <span data-ttu-id="11386-125">遍历行集中的行，并检索与数据值有关的辅助元数据。</span><span class="sxs-lookup"><span data-stu-id="11386-125">Iterate through rows in the row set and retrieve auxiliary metadata about the data values.</span></span>  
  
-   <span data-ttu-id="11386-126">在服务器聚合数据。</span><span class="sxs-lookup"><span data-stu-id="11386-126">Aggregate data at the server.</span></span>  
  
## <a name="available-extension-interfaces"></a><span data-ttu-id="11386-127">可用的扩展插件接口</span><span class="sxs-lookup"><span data-stu-id="11386-127">Available Extension Interfaces</span></span>  
 <span data-ttu-id="11386-128">下表介绍可用接口以及实现是必需的还是可选的。</span><span class="sxs-lookup"><span data-stu-id="11386-128">The following table describes the available interfaces and whether implementation is required or optional.</span></span>  
  
|<span data-ttu-id="11386-129">接口</span><span class="sxs-lookup"><span data-stu-id="11386-129">Interface</span></span>|<span data-ttu-id="11386-130">说明</span><span class="sxs-lookup"><span data-stu-id="11386-130">Description</span></span>|<span data-ttu-id="11386-131">实现</span><span class="sxs-lookup"><span data-stu-id="11386-131">Implementation</span></span>|  
|---------------|-----------------|--------------------|  
|<span data-ttu-id="11386-132">IDbConnection</span><span class="sxs-lookup"><span data-stu-id="11386-132">IDbConnection</span></span>|<span data-ttu-id="11386-133">表示与某一数据源的唯一会话。</span><span class="sxs-lookup"><span data-stu-id="11386-133">Represents a unique session with a data source.</span></span> <span data-ttu-id="11386-134">在客户端/服务器数据库系统的情况下，该会话可等效于到服务器的一个网络连接。</span><span class="sxs-lookup"><span data-stu-id="11386-134">In the case of a client/server database system, the session may be equivalent to a network connection to the server.</span></span>|<span data-ttu-id="11386-135">必选</span><span class="sxs-lookup"><span data-stu-id="11386-135">Required</span></span>|  
|<span data-ttu-id="11386-136">IDbConnectionExtension</span><span class="sxs-lookup"><span data-stu-id="11386-136">IDbConnectionExtension</span></span>|<span data-ttu-id="11386-137">表示可由 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理扩展插件针对安全性和身份验证实现的附加连接属性。</span><span class="sxs-lookup"><span data-stu-id="11386-137">Represents additional connection properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions regarding security and authentication.</span></span>|<span data-ttu-id="11386-138">可选</span><span class="sxs-lookup"><span data-stu-id="11386-138">Optional</span></span>|  
|<span data-ttu-id="11386-139">IDbTransaction</span><span class="sxs-lookup"><span data-stu-id="11386-139">IDbTransaction</span></span>|<span data-ttu-id="11386-140">表示本地事务。</span><span class="sxs-lookup"><span data-stu-id="11386-140">Represents a local transaction.</span></span>|<span data-ttu-id="11386-141">必选</span><span class="sxs-lookup"><span data-stu-id="11386-141">Required</span></span>|  
|<span data-ttu-id="11386-142">IDbTransactionExtension</span><span class="sxs-lookup"><span data-stu-id="11386-142">IDbTransactionExtension</span></span>|<span data-ttu-id="11386-143">表示可由 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理扩展插件实现的附加事务属性。</span><span class="sxs-lookup"><span data-stu-id="11386-143">Represents additional transaction properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions.</span></span>|<span data-ttu-id="11386-144">可选</span><span class="sxs-lookup"><span data-stu-id="11386-144">Optional</span></span>|  
|<span data-ttu-id="11386-145">IDbCommand</span><span class="sxs-lookup"><span data-stu-id="11386-145">IDbCommand</span></span>|<span data-ttu-id="11386-146">表示在连接到数据源时使用的查询或命令。</span><span class="sxs-lookup"><span data-stu-id="11386-146">Represents a query or command that is used when connected to a data source.</span></span>|<span data-ttu-id="11386-147">必选</span><span class="sxs-lookup"><span data-stu-id="11386-147">Required</span></span>|  
|<span data-ttu-id="11386-148">IDbCommandAnalysis</span><span class="sxs-lookup"><span data-stu-id="11386-148">IDbCommandAnalysis</span></span>|<span data-ttu-id="11386-149">表示用于分析某一查询并返回在该查询中使用的参数名称列表的附加命令信息。</span><span class="sxs-lookup"><span data-stu-id="11386-149">Represents additional command information for analyzing a query and returning a list of parameter names used in the query.</span></span>|<span data-ttu-id="11386-150">可选</span><span class="sxs-lookup"><span data-stu-id="11386-150">Optional</span></span>|  
|<span data-ttu-id="11386-151">IDataParameter</span><span class="sxs-lookup"><span data-stu-id="11386-151">IDataParameter</span></span>|<span data-ttu-id="11386-152">表示传递到命令或查询的参数或名称/值对。</span><span class="sxs-lookup"><span data-stu-id="11386-152">Represents a parameter or name/value pair that is passed to a command or query.</span></span>|<span data-ttu-id="11386-153">必选</span><span class="sxs-lookup"><span data-stu-id="11386-153">Required</span></span>|  
|<span data-ttu-id="11386-154">IDataParameterCollection</span><span class="sxs-lookup"><span data-stu-id="11386-154">IDataParameterCollection</span></span>|<span data-ttu-id="11386-155">表示与某一命令或查询相关的所有参数的集合。</span><span class="sxs-lookup"><span data-stu-id="11386-155">Represents a collection of all parameters relevant to a command or query.</span></span>|<span data-ttu-id="11386-156">必选</span><span class="sxs-lookup"><span data-stu-id="11386-156">Required</span></span>|  
|<span data-ttu-id="11386-157">IDataReader</span><span class="sxs-lookup"><span data-stu-id="11386-157">IDataReader</span></span>|<span data-ttu-id="11386-158">提供从数据源读取数据的只进、只读流的方法。</span><span class="sxs-lookup"><span data-stu-id="11386-158">Provides a method of reading a forward-only, read-only stream of data from your data source.</span></span>|<span data-ttu-id="11386-159">必选</span><span class="sxs-lookup"><span data-stu-id="11386-159">Required</span></span>|  
|<span data-ttu-id="11386-160">IDataReaderExtension</span><span class="sxs-lookup"><span data-stu-id="11386-160">IDataReaderExtension</span></span>|<span data-ttu-id="11386-161">提供一种方法来读取一个或多个通过在数据源执行命令所获得的只进结果集流。</span><span class="sxs-lookup"><span data-stu-id="11386-161">Provides a method of reading one or more forward-only streams of result sets, obtained by executing a command at a data source.</span></span> <span data-ttu-id="11386-162">此接口为字段聚合提供附加支持。</span><span class="sxs-lookup"><span data-stu-id="11386-162">This interface provides additional support for field aggregates.</span></span>|<span data-ttu-id="11386-163">可选</span><span class="sxs-lookup"><span data-stu-id="11386-163">Optional</span></span>|  
|<span data-ttu-id="11386-164">IExtension</span><span class="sxs-lookup"><span data-stu-id="11386-164">IExtension</span></span>|<span data-ttu-id="11386-165">为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件提供基类。</span><span class="sxs-lookup"><span data-stu-id="11386-165">Provides the base class for a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="11386-166">还使实现者可为扩展插件包括本地化的名称并将配置设置从配置文件传递到扩展插件。</span><span class="sxs-lookup"><span data-stu-id="11386-166">Also enables an implementer to include a localized name for the extension and to pass configuration settings from the configuration file to the extension.</span></span>|<span data-ttu-id="11386-167">必选</span><span class="sxs-lookup"><span data-stu-id="11386-167">Required</span></span>|  
  
 <span data-ttu-id="11386-168">数据处理扩展插件接口将尽可能与 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据访问接口、方法和属性的子集完全相同。</span><span class="sxs-lookup"><span data-stu-id="11386-168">The data processing extension interfaces are identical to a subset of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces, methods, and properties whenever possible.</span></span> <span data-ttu-id="11386-169">有关实现完整 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据访问接口的详细信息，请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 软件开发包 (SDK) 文档中的“实现 .NET Framework 数据访问接口”。</span><span class="sxs-lookup"><span data-stu-id="11386-169">For more information about implementing a full [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider, see "Implementing a .NET Framework Data Provider" in your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11386-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11386-170">See Also</span></span>  
 <span data-ttu-id="11386-171">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="11386-171">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="11386-172">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="11386-172">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="11386-173">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="11386-173">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
