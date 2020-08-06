---
title: ODBC 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.f1
ms.assetid: bffa63e0-c737-4b54-b4ea-495a400ffcf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: beb29c511af62ba69ca0b9e2c595f61c57edab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589822"
---
# <a name="odbc-destination"></a><span data-ttu-id="99cc0-102">ODBC 目标</span><span class="sxs-lookup"><span data-stu-id="99cc0-102">ODBC Destination</span></span>
  <span data-ttu-id="99cc0-103">ODBC 目标可以将数据大容量加载到支持 ODBC 的数据库表中。</span><span class="sxs-lookup"><span data-stu-id="99cc0-103">The ODBC destination bulk loads data into ODBC-supported database tables.</span></span> <span data-ttu-id="99cc0-104">ODBC 目标使用 ODBC DB 连接管理器来连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="99cc0-104">The ODBC destination uses an ODBC connection manager to connect to the data source.</span></span>  
  
 <span data-ttu-id="99cc0-105">ODBC 目标包括输入列和目标数据源中的列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="99cc0-105">An ODBC destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="99cc0-106">您不必将输入列映射到所有目标列，但有时如果没有将输入列映射到目标列可能会出错，具体取决于目标列的属性。</span><span class="sxs-lookup"><span data-stu-id="99cc0-106">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors may occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="99cc0-107">例如，如果目标列不允许出现 Null 值，则必须将输入列映射到该列。</span><span class="sxs-lookup"><span data-stu-id="99cc0-107">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="99cc0-108">此外，可以映射不同类型的列，但是，如果输入数据与目标列类型不兼容，则在运行时会出现错误。</span><span class="sxs-lookup"><span data-stu-id="99cc0-108">In addition, columns of different types can be mapped, however if the input data is not compatible for the destination column type, an error occurs at runtime.</span></span> <span data-ttu-id="99cc0-109">根据错误行为设置，将忽略该错误，并且导致失败，或者行将发送到错误输出。</span><span class="sxs-lookup"><span data-stu-id="99cc0-109">Depending on the error behavior setting, the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="99cc0-110">ODBC 目标具有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="99cc0-110">The ODBC destination has one regular output and one error output.</span></span>  
  
##  <a name="load-options"></a><a name="BKMK_odbcdestination_loadoptions"></a> <span data-ttu-id="99cc0-111">加载选项</span><span class="sxs-lookup"><span data-stu-id="99cc0-111">Load Options</span></span>  
 <span data-ttu-id="99cc0-112">ODBC 目标可以使用两个访问加载模块之一。</span><span class="sxs-lookup"><span data-stu-id="99cc0-112">The ODBC destination can use one of two access load modules.</span></span> <span data-ttu-id="99cc0-113">在 [ODBC 源编辑器（“连接管理器”页）](../odbc-source-editor-connection-manager-page.md)中设置模式。</span><span class="sxs-lookup"><span data-stu-id="99cc0-113">You set the mode in the [ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md).</span></span> <span data-ttu-id="99cc0-114">这两种模式是：</span><span class="sxs-lookup"><span data-stu-id="99cc0-114">The two modes are:</span></span>  
  
-   <span data-ttu-id="99cc0-115">**批处理**：在此模式中，ODBC 目标将基于发现的 ODBC 访问接口功能尝试使用最高效的插入方法。</span><span class="sxs-lookup"><span data-stu-id="99cc0-115">**Batch**: In this mode the ODBC destination attempts to use the most efficient insertion method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="99cc0-116">对于大多数现今的 ODBC 访问接口，这意味着准备具有参数的 INSERT 语句，然后使用按行数组参数绑定（其中，数组大小由 **BatchSize** 属性控制）。</span><span class="sxs-lookup"><span data-stu-id="99cc0-116">For most modern ODBC providers, this would mean preparing an INSERT statement with parameters and then using a row-wise array parameter binding (where the array size is controlled by the **BatchSize** property).</span></span> <span data-ttu-id="99cc0-117">如果选择“批处理”  并且提供程序不支持此方法，则 ODBC 目标将自动切换到“逐行”  模式。</span><span class="sxs-lookup"><span data-stu-id="99cc0-117">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="99cc0-118">**逐行**：在此模式中，ODBC 目标准备具有参数的 INSERT 语句并且使用“SQL 执行”  来一次一行地插入行。</span><span class="sxs-lookup"><span data-stu-id="99cc0-118">**Row-by-row**: In this mode, the ODBC destination prepares an INSERT statement with parameters and uses **SQL Execute** to insert rows one at a time.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="99cc0-119">错误处理</span><span class="sxs-lookup"><span data-stu-id="99cc0-119">Error Handling</span></span>  
 <span data-ttu-id="99cc0-120">ODBC 目标有一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="99cc0-120">The ODBC destination has an error output.</span></span> <span data-ttu-id="99cc0-121">组件的错误输出包括以下输出列：</span><span class="sxs-lookup"><span data-stu-id="99cc0-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="99cc0-122">**错误代码**：与当前错误相对应的编号。</span><span class="sxs-lookup"><span data-stu-id="99cc0-122">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="99cc0-123">有关错误的列表，请参阅源数据库的文档。</span><span class="sxs-lookup"><span data-stu-id="99cc0-123">See the documentation for your source database for a list of errors.</span></span> <span data-ttu-id="99cc0-124">有关 SSIS 错误代码的列表，请参阅 SSIS 错误代码和消息参考。</span><span class="sxs-lookup"><span data-stu-id="99cc0-124">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="99cc0-125">**错误列**：导致错误（针对转换错误）的源列。</span><span class="sxs-lookup"><span data-stu-id="99cc0-125">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="99cc0-126">标准的输出数据列。</span><span class="sxs-lookup"><span data-stu-id="99cc0-126">The standard output data columns.</span></span>  
  
 <span data-ttu-id="99cc0-127">根据错误行为设置，CDC 目标支持在错误输出中返回在提取过程中发生的错误（数据转换、截断）。</span><span class="sxs-lookup"><span data-stu-id="99cc0-127">Depending on the error behavior setting, the ODBC destination supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="99cc0-128">有关详细信息，请参阅 [ODBC 源编辑器（“错误输出”页）](../odbc-source-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="99cc0-128">For more information, see [ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="99cc0-129">并行度</span><span class="sxs-lookup"><span data-stu-id="99cc0-129">Parallelism</span></span>  
 <span data-ttu-id="99cc0-130">对于可对同一台计算机或不同计算机（并非一般的全局会话限制）上的相同表或不同表并行运行的 ODBC 目标组件的数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="99cc0-130">There is no limitation on the number of ODBC destination components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="99cc0-131">但是，要使用的 ODBC 访问接口的限制可能会限制通过该访问接口的同时连接的数目。</span><span class="sxs-lookup"><span data-stu-id="99cc0-131">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="99cc0-132">这些限制将会限制 ODBC 目标可能支持的并行实例的数目。</span><span class="sxs-lookup"><span data-stu-id="99cc0-132">These limitations limit the number of supported parallel instances possible for the ODBC destination.</span></span> <span data-ttu-id="99cc0-133">SSIS 开发人员必须知道要使用的任何 ODBC 访问接口的限制并且在生成 SSIS 包时将这些限制元素考虑进去。</span><span class="sxs-lookup"><span data-stu-id="99cc0-133">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
 <span data-ttu-id="99cc0-134">您还必须知道，同时加载到同一个表中可能会由于标准记录锁定而降低性能。</span><span class="sxs-lookup"><span data-stu-id="99cc0-134">You must also be aware that concurrently loading into the same table may reduce performance because of standard record locking.</span></span> <span data-ttu-id="99cc0-135">这取决于要加载的数据和表的组织结构。</span><span class="sxs-lookup"><span data-stu-id="99cc0-135">This depends on the data being loaded and on the table organization.</span></span>  
  
## <a name="troubleshooting-the-odbc-destination"></a><span data-ttu-id="99cc0-136">ODBC 目标故障排除</span><span class="sxs-lookup"><span data-stu-id="99cc0-136">Troubleshooting the ODBC Destination</span></span>  
 <span data-ttu-id="99cc0-137">可以记录 ODBC 源对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="99cc0-137">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="99cc0-138">利用此日志记录功能，可以排除 ODBC 目标执行将数据保存到外部数据源的操作过程中发生的故障。</span><span class="sxs-lookup"><span data-stu-id="99cc0-138">You can use this logging capability to troubleshoot the saving of data to external data sources that the ODBC destination performs.</span></span> <span data-ttu-id="99cc0-139">若要记录 ODBC 目标对外部数据访问接口进行的调用，请启用 ODBC 驱动程序管理器跟踪。</span><span class="sxs-lookup"><span data-stu-id="99cc0-139">To log the calls that the ODBC destination makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="99cc0-140">有关详细信息，请参阅 Microsoft 文档 *数据源管理员如何使用 ODBC 生成 ODBC 跟踪*。</span><span class="sxs-lookup"><span data-stu-id="99cc0-140">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator*.</span></span>  
  
## <a name="configuring-the-odbc-destination"></a><span data-ttu-id="99cc0-141">配置 ODBC 目标</span><span class="sxs-lookup"><span data-stu-id="99cc0-141">Configuring the ODBC Destination</span></span>  
 <span data-ttu-id="99cc0-142">您可以通过编程方式或者通过 SSIS 设计器配置 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="99cc0-142">You can configure the ODBC destination programatically or through the SSIS Designer</span></span>  
  
 <span data-ttu-id="99cc0-143">有关详细信息，请参阅下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="99cc0-143">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="99cc0-144">ODBC 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-144">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="99cc0-145">ODBC 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-145">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="99cc0-146">ODBC 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-146">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="99cc0-147">**“高级编辑器”** 对话框包含可通过编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="99cc0-147">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="99cc0-148">打开 **“高级编辑器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="99cc0-148">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="99cc0-149">在您的 **项目的** “数据流” [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 屏幕上，右键单击 ODBC 目标，然后选择 **“显示高级编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="99cc0-149">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC destination and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="99cc0-150">有关可在“高级编辑器”对话框中设置的属性的详细信息，请参阅 [ODBC Destination Custom Properties](odbc-destination-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="99cc0-150">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Destination Custom Properties](odbc-destination-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99cc0-151">本节内容</span><span class="sxs-lookup"><span data-stu-id="99cc0-151">In This Section</span></span>  
  
-   [<span data-ttu-id="99cc0-152">ODBC 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-152">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="99cc0-153">ODBC 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-153">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="99cc0-154">ODBC 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="99cc0-154">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="99cc0-155">通过使用 ODBC 目标来加载数据</span><span class="sxs-lookup"><span data-stu-id="99cc0-155">Load Data by Using the ODBC Destination</span></span>](odbc-destination.md)  
  
-   [<span data-ttu-id="99cc0-156">ODBC 目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="99cc0-156">ODBC Destination Custom Properties</span></span>](odbc-destination-custom-properties.md)  
  
  
