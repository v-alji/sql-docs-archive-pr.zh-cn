---
title: ODBC 源 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.f1
ms.assetid: abcf34eb-9140-4100-82e6-b85bccd22abe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 792557839d60f34bdf944dab150959d4df7cb8cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579675"
---
# <a name="odbc-source"></a><span data-ttu-id="f12b1-102">ODBC 源</span><span class="sxs-lookup"><span data-stu-id="f12b1-102">ODBC Source</span></span>
  <span data-ttu-id="f12b1-103">ODBC 源通过使用数据库表、视图或 SQL 语句，从支持 ODBC 的数据库中提取数据。</span><span class="sxs-lookup"><span data-stu-id="f12b1-103">The ODBC source extracts data from ODBC-supported database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="f12b1-104">ODBC 源具有以下数据访问模式用于提取数据：</span><span class="sxs-lookup"><span data-stu-id="f12b1-104">The ODBC source has the following data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="f12b1-105">表或视图。</span><span class="sxs-lookup"><span data-stu-id="f12b1-105">A table or view.</span></span>  
  
-   <span data-ttu-id="f12b1-106">SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="f12b1-106">The results of an SQL statement.</span></span>  
  
 <span data-ttu-id="f12b1-107">源使用 ODBC 连接管理器，它指定要使用的访问接口。</span><span class="sxs-lookup"><span data-stu-id="f12b1-107">The source uses an ODBC connection manager, which specifies the provider to use.</span></span>  
  
 <span data-ttu-id="f12b1-108">ODBC 源包含源数据输出列。</span><span class="sxs-lookup"><span data-stu-id="f12b1-108">An ODBC source includes the source data output columns.</span></span> <span data-ttu-id="f12b1-109">当 ODBC 目标中的输出列映射到目标列中时，如果没有任何输出列映射到目标列，可能会出现错误。</span><span class="sxs-lookup"><span data-stu-id="f12b1-109">When output columns are mapped in the ODBC destination to the destination columns, errors may occur if no output columns are mapped to the destination columns.</span></span> <span data-ttu-id="f12b1-110">可以映射不同类型的列，但是，如果输出数据与目标不兼容，则在运行时会出现错误。</span><span class="sxs-lookup"><span data-stu-id="f12b1-110">Columns of different types can be mapped, however if the output data is not compatible for the destination then an error occurs at runtime.</span></span> <span data-ttu-id="f12b1-111">根据错误行为，将忽略对错误的设置，并且导致失败，或者行将发送到错误输出。</span><span class="sxs-lookup"><span data-stu-id="f12b1-111">Depending on the error behavior, setting the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="f12b1-112">ODBC 源有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="f12b1-112">The ODBC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="f12b1-113">错误处理</span><span class="sxs-lookup"><span data-stu-id="f12b1-113">Error Handling</span></span>  
 <span data-ttu-id="f12b1-114">ODBC 源有一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="f12b1-114">The ODBC source has an error output.</span></span> <span data-ttu-id="f12b1-115">组件的错误输出包括以下输出列：</span><span class="sxs-lookup"><span data-stu-id="f12b1-115">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="f12b1-116">**错误代码**：与当前错误相对应的编号。</span><span class="sxs-lookup"><span data-stu-id="f12b1-116">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="f12b1-117">有关错误的列表，请参阅您正在使用的支持 ODBC 的数据库文档。</span><span class="sxs-lookup"><span data-stu-id="f12b1-117">See the documentation for the ODBC-supported database you are using for a list of errors.</span></span> <span data-ttu-id="f12b1-118">有关 SSIS 错误代码的列表，请参阅 SSIS 错误代码和消息参考。</span><span class="sxs-lookup"><span data-stu-id="f12b1-118">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="f12b1-119">**错误列**：导致错误（针对转换错误）的源列。</span><span class="sxs-lookup"><span data-stu-id="f12b1-119">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="f12b1-120">标准的输出数据列。</span><span class="sxs-lookup"><span data-stu-id="f12b1-120">The standard output data columns.</span></span>  
  
 <span data-ttu-id="f12b1-121">根据错误行为设置，CDC 源支持在错误输出中返回在提取过程中发生的错误（数据转换、截断）。</span><span class="sxs-lookup"><span data-stu-id="f12b1-121">Depending on the error behavior setting, the ODBC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="f12b1-122">有关详细信息，请参阅 [ODBC 目标编辑器（“连接管理器”页）](../odbc-destination-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="f12b1-122">For more information, see [ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="f12b1-123">数据类型支持</span><span class="sxs-lookup"><span data-stu-id="f12b1-123">Data Type Support</span></span>  
 <span data-ttu-id="f12b1-124">有关 ODBC 源支持的数据类型的信息，请参阅 Connector for Open Database Connectivity (ODBC) by Attunity。</span><span class="sxs-lookup"><span data-stu-id="f12b1-124">For information about the data types supported by the ODBC source, see Connector for Open Database Connectivity (ODBC) by Attunity.</span></span>  
  
## <a name="extract-options"></a><span data-ttu-id="f12b1-125">提取选项</span><span class="sxs-lookup"><span data-stu-id="f12b1-125">Extract Options</span></span>  
 <span data-ttu-id="f12b1-126">ODBC 源在“批处理”  或“逐行”  模式下操作。</span><span class="sxs-lookup"><span data-stu-id="f12b1-126">The ODBC source operates in either **Batch** or **Row-by-Row** mode.</span></span> <span data-ttu-id="f12b1-127">使用的模式由 **FetchMethod** 属性确定。</span><span class="sxs-lookup"><span data-stu-id="f12b1-127">The mode used is determined by the **FetchMethod** property.</span></span> <span data-ttu-id="f12b1-128">下表对这些模式进行了说明。</span><span class="sxs-lookup"><span data-stu-id="f12b1-128">The following list describes the modes.</span></span>  
  
-   <span data-ttu-id="f12b1-129">**批处理**：组件将基于发现的 ODBC 访问接口功能尝试使用最高效的提取方法。</span><span class="sxs-lookup"><span data-stu-id="f12b1-129">**Batch**: The component attempts to use the most efficient fetch method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="f12b1-130">对于大多数现今的 ODBC 提供程序，这是具有数组绑定的 SQLFetchScroll（其中，数组大小由 **BatchSize** 属性确定）。</span><span class="sxs-lookup"><span data-stu-id="f12b1-130">For most modern ODBC providers, this is SQLFetchScroll with array binding (where the array size is determined by the **BatchSize** property).</span></span> <span data-ttu-id="f12b1-131">如果选择“批处理”  并且提供程序不支持此方法，则 ODBC 目标将自动切换到“逐行”  模式。</span><span class="sxs-lookup"><span data-stu-id="f12b1-131">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="f12b1-132">**逐行**：组件使用 SQLFetch 来一次一行的检索行。</span><span class="sxs-lookup"><span data-stu-id="f12b1-132">**Row-by Row**: The component uses SQLFetch to retrieve the rows one at a time.</span></span>  
  
 <span data-ttu-id="f12b1-133">有关 **FetchMethod** 属性的详细信息，请参阅 [ODBC Source Custom Properties](odbc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f12b1-133">For more information about the **FetchMethod** property, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="f12b1-134">并行度</span><span class="sxs-lookup"><span data-stu-id="f12b1-134">Parallelism</span></span>  
 <span data-ttu-id="f12b1-135">对于可对同一台计算机或不同计算机（并非一般的全局会话限制）上的相同表或不同表并行运行的 ODBC 源组件的数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="f12b1-135">There is no limitation on the number of ODBC source components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="f12b1-136">但是，要使用的 ODBC 访问接口的限制可能会限制通过该访问接口的同时连接的数目。</span><span class="sxs-lookup"><span data-stu-id="f12b1-136">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="f12b1-137">这些限制将会限制 ODBC 源可能支持的并行实例的数目。</span><span class="sxs-lookup"><span data-stu-id="f12b1-137">These limitations limit the number of supported parallel instances possible for the ODBC source.</span></span> <span data-ttu-id="f12b1-138">SSIS 开发人员必须知道要使用的任何 ODBC 访问接口的限制并且在生成 SSIS 包时将这些限制元素考虑进去。</span><span class="sxs-lookup"><span data-stu-id="f12b1-138">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
## <a name="troubleshooting-the-odbc-source"></a><span data-ttu-id="f12b1-139">ODBC 源故障排除</span><span class="sxs-lookup"><span data-stu-id="f12b1-139">Troubleshooting the ODBC Source</span></span>  
 <span data-ttu-id="f12b1-140">可以记录 ODBC 源对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="f12b1-140">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="f12b1-141">利用此日志记录功能，可以对 ODBC 源执行的从外部数据源加载数据的操作进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="f12b1-141">You can use this logging capability to troubleshoot the loading of data from external data sources that the ODBC source performs.</span></span> <span data-ttu-id="f12b1-142">若要记录 ODBC 源对外部数据访问接口进行的调用，请启用 ODBC 驱动程序管理器跟踪。</span><span class="sxs-lookup"><span data-stu-id="f12b1-142">To log the calls that the ODBC source makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="f12b1-143">有关详细信息，请参阅 Microsoft 文档 *数据源管理员如何使用 ODBC 生成 ODBC 跟踪*。</span><span class="sxs-lookup"><span data-stu-id="f12b1-143">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator.*</span></span>  
  
## <a name="configuring-the-odbc-source"></a><span data-ttu-id="f12b1-144">配置 ODBC 源</span><span class="sxs-lookup"><span data-stu-id="f12b1-144">Configuring the ODBC Source</span></span>  
 <span data-ttu-id="f12b1-145">您可以通过编程方式或者通过 SSIS 设计器配置 ODBC 源。</span><span class="sxs-lookup"><span data-stu-id="f12b1-145">You can configure the ODBC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="f12b1-146">有关详细信息，请参阅下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="f12b1-146">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f12b1-147">ODBC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-147">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="f12b1-148">ODBC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-148">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="f12b1-149">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-149">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="f12b1-150">**“高级编辑器”** 对话框包含可通过编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="f12b1-150">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="f12b1-151">打开 **“高级编辑器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="f12b1-151">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="f12b1-152">在您的 **项目的** “数据流” [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 屏幕上，右键单击 ODBC 源，然后选择 **“显示高级编辑器”**。</span><span class="sxs-lookup"><span data-stu-id="f12b1-152">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="f12b1-153">有关可在“高级编辑器”对话框中设置的属性的详细信息，请参阅 [ODBC Source Custom Properties](odbc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f12b1-153">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f12b1-154">本节内容</span><span class="sxs-lookup"><span data-stu-id="f12b1-154">In This Section</span></span>  
  
-   [<span data-ttu-id="f12b1-155">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-155">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="f12b1-156">ODBC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-156">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="f12b1-157">ODBC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f12b1-157">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="f12b1-158">使用 ODBC 源提取数据</span><span class="sxs-lookup"><span data-stu-id="f12b1-158">Extract Data by Using the ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="f12b1-159">ODBC Source Custom Properties</span><span class="sxs-lookup"><span data-stu-id="f12b1-159">ODBC Source Custom Properties</span></span>](odbc-source-custom-properties.md)  
  
  
