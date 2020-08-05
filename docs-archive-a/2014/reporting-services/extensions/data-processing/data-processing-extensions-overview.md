---
title: 数据处理扩展插件概述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e589d3a4e090aee52d2590c0b2ccff435c2321a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581136"
---
# <a name="data-processing-extensions-overview"></a><span data-ttu-id="a6955-102">数据处理扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="a6955-102">Data Processing Extensions Overview</span></span>
  <span data-ttu-id="a6955-103">借助于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的数据处理扩展插件，您可以连接到数据源并检索数据。</span><span class="sxs-lookup"><span data-stu-id="a6955-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="a6955-104">它们还可以充当数据源和数据集之间的桥梁。</span><span class="sxs-lookup"><span data-stu-id="a6955-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a6955-105">数据处理扩展插件是模仿 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据提供程序接口的子集创建的。</span><span class="sxs-lookup"><span data-stu-id="a6955-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>

 <span data-ttu-id="a6955-106">下表列出 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 随附的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a6955-106">The following table lists the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

|<span data-ttu-id="a6955-107">数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="a6955-107">Data processing extension</span></span>|<span data-ttu-id="a6955-108">说明</span><span class="sxs-lookup"><span data-stu-id="a6955-108">Description</span></span>|
|-------------------------------|-----------------|
|<span data-ttu-id="a6955-109">用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="a6955-109">Data processing extension for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="a6955-110">使用用于 SQL Server 的 .NET Framework 数据提供程序可以连接到 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 和从其检索数据。</span><span class="sxs-lookup"><span data-stu-id="a6955-110">Uses the .NET Framework Data Provider for SQL Server to connect to and retrieve data from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>|
|<span data-ttu-id="a6955-111">用于 OLE DB 的数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="a6955-111">Data processing extension for OLE DB</span></span>|<span data-ttu-id="a6955-112">使用用于 OLE DB 的 .NET Framework 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="a6955-112">Uses the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="a6955-113">使用此扩展插件，报表服务器可以查询具有 OLE DB 访问接口的任何数据源。</span><span class="sxs-lookup"><span data-stu-id="a6955-113">With this extension, the report server can query any data source that has an OLE DB provider.</span></span>|
|<span data-ttu-id="a6955-114">用于 Oracle 的数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="a6955-114">Data processing extension for Oracle</span></span>|<span data-ttu-id="a6955-115">使用用于 Oracle 的 .NET Framework 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="a6955-115">Uses the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="a6955-116">使用此扩展插件，报表服务器可以通过 Oracle 客户端连接软件访问 Oracle 数据源。</span><span class="sxs-lookup"><span data-stu-id="a6955-116">With this extension, the report server can access Oracle data sources through Oracle client connectivity software.</span></span>|
|<span data-ttu-id="a6955-117">用于 ODBC 的数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="a6955-117">Data processing extension for ODBC</span></span>|<span data-ttu-id="a6955-118">使用用于 ODBC 的 .NET Framework 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="a6955-118">Uses the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="a6955-119">使用此扩展插件，报表服务器可以访问存在有关 ODBC 驱动程序的任何数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="a6955-119">With this extension, the report server can access data in any database for which there is an ODBC driver.</span></span>|

 <span data-ttu-id="a6955-120">可以使用 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理 API 向您的报表服务器添加自定义数据处理。</span><span class="sxs-lookup"><span data-stu-id="a6955-120">You can use the [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing API to add custom data processing to your report server.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a6955-121">具有对 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的数据访问接口的固有支持。</span><span class="sxs-lookup"><span data-stu-id="a6955-121">has built-in support for data providers in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="a6955-122">如果您已实现了完整的数据访问接口，则无需实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a6955-122">If you have already implemented a full data provider, you do not need to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="a6955-123">不过，您应该考虑扩展数据访问接口，以便包括特定于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 的功能，这包括安全连接凭据和服务器端聚合。</span><span class="sxs-lookup"><span data-stu-id="a6955-123">However, you should consider extending your data provider to include functionality specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005, which includes secure connection credentials and server-side aggregates.</span></span>

 <span data-ttu-id="a6955-124">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中包括的每个数据处理扩展插件都使用一组通用的接口。</span><span class="sxs-lookup"><span data-stu-id="a6955-124">Each of the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a common set of interfaces.</span></span> <span data-ttu-id="a6955-125">这确保每个扩展插件都实现类似的功能。</span><span class="sxs-lookup"><span data-stu-id="a6955-125">This ensures that each extension implements comparable functionality.</span></span>

 <span data-ttu-id="a6955-126">您可为自己的数据源开发数据处理扩展插件，或者可以使用接口向公共数据库基础结构添加用于数据处理的附加层。</span><span class="sxs-lookup"><span data-stu-id="a6955-126">You can develop data processing extensions for your own data sources, or you can use the interfaces to add an additional layer of data processing to common database infrastructures.</span></span> <span data-ttu-id="a6955-127">您可以部署自定义数据处理扩展插件，实现数据与组织中的现有报表服务器的无缝集成。</span><span class="sxs-lookup"><span data-stu-id="a6955-127">You can deploy your custom data processing extensions to enable seamless integration of data into the existing report servers in your organization.</span></span> <span data-ttu-id="a6955-128">还可以将它们用作提供给您的使用者的自定义报表套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6955-128">You can also use them as part of a custom reporting suite that you provide to your consumers.</span></span>

 <span data-ttu-id="a6955-129">![数据处理扩展插件体系结构](../../media/bk-dataprocess-extensions.gif "数据处理扩展插件体系结构")Reporting Services 数据处理扩展插件体系结构</span><span class="sxs-lookup"><span data-stu-id="a6955-129">![Data processing extension architecture](../../media/bk-dataprocess-extensions.gif "Data processing extension architecture") Reporting Services data processing extension architecture</span></span>

 <span data-ttu-id="a6955-130">实现自定义 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件的好处包括：</span><span class="sxs-lookup"><span data-stu-id="a6955-130">The advantages to implementing a custom [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension include:</span></span>

-   <span data-ttu-id="a6955-131">简化的数据访问体系结构，通常具有更好的可维护性和改进的性能。</span><span class="sxs-lookup"><span data-stu-id="a6955-131">A simplified data access architecture, often with better maintainability and improved performance.</span></span>

-   <span data-ttu-id="a6955-132">能够直接将特定于扩展插件的功能公开给使用者。</span><span class="sxs-lookup"><span data-stu-id="a6955-132">The ability to directly expose extension-specific functionality to consumers.</span></span>

-   <span data-ttu-id="a6955-133">可供您的使用者访问 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 内的数据源的特定接口。</span><span class="sxs-lookup"><span data-stu-id="a6955-133">A specific interface for your consumers to access your data source within [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="data-extension-process-flow"></a><span data-ttu-id="a6955-134">数据扩展插件处理流程</span><span class="sxs-lookup"><span data-stu-id="a6955-134">Data Extension Process Flow</span></span>
 <span data-ttu-id="a6955-135">在开发自定义数据扩展插件前，您应该理解报表服务器是如何使用数据扩展插件处理数据的。</span><span class="sxs-lookup"><span data-stu-id="a6955-135">Before developing your custom data extension, you should understand how the report server uses data extensions to process data.</span></span> <span data-ttu-id="a6955-136">还应理解报表服务器调用的构造函数和方法。</span><span class="sxs-lookup"><span data-stu-id="a6955-136">You should also understand the constructors and methods that are called by the report server.</span></span>

 <span data-ttu-id="a6955-137">![数据处理扩展插件的处理](../../media/bk-ext-01.gif "数据处理扩展插件的处理流程")流程Report Server 调用的数据扩展插件的分步处理流程</span><span class="sxs-lookup"><span data-stu-id="a6955-137">![Process flow for data processing extension](../../media/bk-ext-01.gif "Process flow for data processing extension") The step-by-step process flow of a data extension that is called by the report server</span></span>

 <span data-ttu-id="a6955-138">该图说明下列事件序列：</span><span class="sxs-lookup"><span data-stu-id="a6955-138">The illustration shows the following sequence of events:</span></span>

1.  <span data-ttu-id="a6955-139">报表服务器创建一个连接对象并传递到与报表相关联的连接字符串和凭据中。</span><span class="sxs-lookup"><span data-stu-id="a6955-139">The report server creates a connection object and passes in the connection string and credentials associated with the report.</span></span>

2.  <span data-ttu-id="a6955-140">用于创建命令对象的报表的命令文本。</span><span class="sxs-lookup"><span data-stu-id="a6955-140">The command text of the report is used to create a command object.</span></span> <span data-ttu-id="a6955-141">在该过程中，数据处理扩展插件可包括用于分析命令文本和创建命令参数的代码。</span><span class="sxs-lookup"><span data-stu-id="a6955-141">In the process, the data processing extension may include code that parses the command text and creates any parameters for the command.</span></span>

3.  <span data-ttu-id="a6955-142">一旦处理了命令对象和参数后，就将生成一个数据读取器，它返回结果集并使报表服务器能够将报表数据与报表布局相关联。</span><span class="sxs-lookup"><span data-stu-id="a6955-142">Once the command object and any parameters are processed, a data reader is generated that returns a result set and enables the report server to associate the report data with the report layout.</span></span>

## <a name="developer-requirements"></a><span data-ttu-id="a6955-143">开发人员要求</span><span class="sxs-lookup"><span data-stu-id="a6955-143">Developer Requirements</span></span>
 <span data-ttu-id="a6955-144">开发 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件要求您具备：</span><span class="sxs-lookup"><span data-stu-id="a6955-144">Developing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension requires you to have:</span></span>

-   <span data-ttu-id="a6955-145">一台安装了报表设计器或报表服务器的部署计算机。</span><span class="sxs-lookup"><span data-stu-id="a6955-145">A deployment computer with Report Designer or a report server installed.</span></span>

-   <span data-ttu-id="a6955-146">[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]安装了或更高版本或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 软件开发工具包 (SDK) 的开发计算机。</span><span class="sxs-lookup"><span data-stu-id="a6955-146">A development computer with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] or above, or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installed.</span></span>

-   <span data-ttu-id="a6955-147">深入理解 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a6955-147">An in-depth understanding of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>

-   <span data-ttu-id="a6955-148">深入了解 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 体系结构、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据提供程序、ADO.NET 数据集对象和公共 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接口。</span><span class="sxs-lookup"><span data-stu-id="a6955-148">An in-depth understanding of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] architecture, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data providers, ADO.NET DataSet objects, and the common [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] interfaces.</span></span>

-   <span data-ttu-id="a6955-149">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]语言（如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c # 或 .net）的开发体验 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6955-149">Development experience in a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] language such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6955-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6955-150">See Also</span></span>
 <span data-ttu-id="a6955-151">[扩展插件 Reporting Services](../reporting-services-extension-library.md) [Reporting Services 扩展](../reporting-services-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="a6955-151">[Reporting Services Extensions](../reporting-services-extensions.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


