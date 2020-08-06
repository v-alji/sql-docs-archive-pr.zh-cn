---
title: CDC 源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590321"
---
# <a name="cdc-source"></a><span data-ttu-id="3fda8-102">CDC 源</span><span class="sxs-lookup"><span data-stu-id="3fda8-102">CDC Source</span></span>
  <span data-ttu-id="3fda8-103">CDC 源从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 更改表中读取某一范围的更改数据并且将更改向下传递给其他 SSIS 组件。</span><span class="sxs-lookup"><span data-stu-id="3fda8-103">The CDC source reads a range of change data from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables and delivers the changes downstream to other SSIS components.</span></span>  
  
 <span data-ttu-id="3fda8-104">由 CDC 源读取的更改数据的范围称作 CDC 处理范围并且由在当前数据流开始前执行的 CDC 控制任务确定。</span><span class="sxs-lookup"><span data-stu-id="3fda8-104">The range of change data read by the CDC source is called the CDC Processing Range and is determine by the CDC Control task that is executed before the current data flow starts.</span></span> <span data-ttu-id="3fda8-105">该 CDC 处理范围是从维护一组表的 CDC 处理状态的包变量的值派生的。</span><span class="sxs-lookup"><span data-stu-id="3fda8-105">The CDC Processing Range is derived from the value of a package variable that maintains the state of the CDC processing for a group of tables.</span></span>  
  
 <span data-ttu-id="3fda8-106">CDC 源通过使用数据库表、视图或 SQL 语句，从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中提取数据。</span><span class="sxs-lookup"><span data-stu-id="3fda8-106">The CDC source extracts data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="3fda8-107">CDC 源使用以下配置：</span><span class="sxs-lookup"><span data-stu-id="3fda8-107">The CDC source uses the following configurations:</span></span>  
  
-   <span data-ttu-id="3fda8-108">用于访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="3fda8-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET connection manager to access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database.</span></span> <span data-ttu-id="3fda8-109">有关配置 CDC 源连接的详细信息，请参阅 [CDC 源编辑器（“连接管理器”页）](../cdc-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="3fda8-109">For more information about configuring the CDC source connection, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
-   <span data-ttu-id="3fda8-110">为 CDC 启用的表。</span><span class="sxs-lookup"><span data-stu-id="3fda8-110">A table enabled for CDC.</span></span>  
  
-   <span data-ttu-id="3fda8-111">所选表（如果存在多个）的捕获实例的名称。</span><span class="sxs-lookup"><span data-stu-id="3fda8-111">The name of the capture instance of the selected table (if more-than-one exists).</span></span>  
  
-   <span data-ttu-id="3fda8-112">更改处理模式。</span><span class="sxs-lookup"><span data-stu-id="3fda8-112">The change processing mode.</span></span>  
  
-   <span data-ttu-id="3fda8-113">基于所确定的 CDC 处理范围的 CDC 状态包变量的名称。</span><span class="sxs-lookup"><span data-stu-id="3fda8-113">The name of the CDC state package variable based on which the CDC Processing range is determined.</span></span> <span data-ttu-id="3fda8-114">CDC 源不修改该变量。</span><span class="sxs-lookup"><span data-stu-id="3fda8-114">The CDC source does not modify that variable.</span></span>  
  
 <span data-ttu-id="3fda8-115">CDC 源返回的数据与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 函数 cdc.fn_cdc_get_all_changes_\<capture-instance-name> 或 cdc.fn_cdc_get_net_changes_\<capture-instance-name>（在可用时）返回的数据相同 。</span><span class="sxs-lookup"><span data-stu-id="3fda8-115">The data returned by the CDC Source is the same as that returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC functions **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** or **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (when available).</span></span> <span data-ttu-id="3fda8-116">唯一可选的添加是列 **__$initial_processing** ，它指示当前处理范围是否可与表的初始加载重叠。</span><span class="sxs-lookup"><span data-stu-id="3fda8-116">The only optional addition is the column, **__$initial_processing** that indicates whether the current processing range can overlap with an initial load of the table.</span></span> <span data-ttu-id="3fda8-117">有关初始处理的详细信息，请参阅 [CDC Control Task](../control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3fda8-117">For more information about initial processing, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="3fda8-118">CDC 源有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="3fda8-118">The CDC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="3fda8-119">错误处理</span><span class="sxs-lookup"><span data-stu-id="3fda8-119">Error Handling</span></span>  
 <span data-ttu-id="3fda8-120">CDC 源有一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="3fda8-120">The CDC source has an error output.</span></span> <span data-ttu-id="3fda8-121">组件的错误输出包括以下输出列：</span><span class="sxs-lookup"><span data-stu-id="3fda8-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="3fda8-122">**错误代码**：值始终为 -1。</span><span class="sxs-lookup"><span data-stu-id="3fda8-122">**Error Code**: The value is always -1.</span></span>  
  
-   <span data-ttu-id="3fda8-123">**错误列**：导致错误（针对转换错误）的源列。</span><span class="sxs-lookup"><span data-stu-id="3fda8-123">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="3fda8-124">**错误行列**：导致了错误的记录数据。</span><span class="sxs-lookup"><span data-stu-id="3fda8-124">**Error Row Columns**: The record data that causes the error.</span></span>  
  
 <span data-ttu-id="3fda8-125">根据错误行为设置，CDC 源支持在错误输出中返回在提取过程中发生的错误（数据转换、截断）。</span><span class="sxs-lookup"><span data-stu-id="3fda8-125">Depending on the error behavior setting, the CDC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="3fda8-126">有关详细信息，请参阅 [CDC 源编辑器（“错误输出”页）](../cdc-source-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="3fda8-126">For more information, see [CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="3fda8-127">数据类型支持</span><span class="sxs-lookup"><span data-stu-id="3fda8-127">Data Type Support</span></span>  
 <span data-ttu-id="3fda8-128">Microsoft 的 CDC 源组件支持所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，这些数据类型映射到正确的 SSIS 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3fda8-128">The CDC source component for Microsoft supports all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, which are mapped to the correct SSIS data types.</span></span>  
  
## <a name="troubleshooting-the-cdc-source"></a><span data-ttu-id="3fda8-129">CDC 源故障排除</span><span class="sxs-lookup"><span data-stu-id="3fda8-129">Troubleshooting the CDC Source</span></span>  
 <span data-ttu-id="3fda8-130">下面包含与排除 CDC 源问题有关的信息。</span><span class="sxs-lookup"><span data-stu-id="3fda8-130">The following contains information on troubleshooting the CDC source.</span></span>  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a><span data-ttu-id="3fda8-131">使用此脚本可以确定问题并且在 SQL Server Management Studio 中复现这些问题</span><span class="sxs-lookup"><span data-stu-id="3fda8-131">Use this script to isolate problems and reproduce them in SQL Server Management Studio</span></span>  
 <span data-ttu-id="3fda8-132">CDC 源操作受到在调用 CDC 源之前执行的 CDC 控制任务操作的约束。</span><span class="sxs-lookup"><span data-stu-id="3fda8-132">The CDC source operation is governed by the operation of the CDC Control task executed before invoking the CDC source.</span></span> <span data-ttu-id="3fda8-133">CDC 控制任务准备 CDC 状态包变量的值以便包含开始和结束 LSN。</span><span class="sxs-lookup"><span data-stu-id="3fda8-133">The CDC Control task prepares the value of the CDC state package variable to contain the start and end LSNs.</span></span> <span data-ttu-id="3fda8-134">它执行与下面的脚本等效的函数：</span><span class="sxs-lookup"><span data-stu-id="3fda8-134">It performs function equivalent to the following script:</span></span>  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 <span data-ttu-id="3fda8-135">其中：</span><span class="sxs-lookup"><span data-stu-id="3fda8-135">where:</span></span>  
  
-   <span data-ttu-id="3fda8-136">\<cdc-enabled-database-name> 是包含更改表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3fda8-136">\<cdc-enabled-database-name> is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database containing the change tables.</span></span>  
  
-   <span data-ttu-id="3fda8-137">\<value-from-state-cs> 是在 CDC 状态变量中以 CS/\<value-from-state-cs>/（CS 表示 Current-processing-range-Start）形式出现的值。</span><span class="sxs-lookup"><span data-stu-id="3fda8-137">\<value-from-state-cs> is the value that appears in the CDC state variable as CS/\<value-from-state-cs>/ (CS stands for Current-processing-range-Start).</span></span>  
  
-   <span data-ttu-id="3fda8-138">\<value-from-state-ce> 是在 CDC 状态变量中以 CE/\<value-from-state-cs>/（CE 表示 Current-processing-range-End）形式出现的值。</span><span class="sxs-lookup"><span data-stu-id="3fda8-138">\<value-from-state-ce> is the value that appears in the CDC state variable as CE/\<value-from-state-cs>/ (CE stands for Current-processing-range-End).</span></span>  
  
-   <span data-ttu-id="3fda8-139">\<mode> 是 CDC 处理模式。</span><span class="sxs-lookup"><span data-stu-id="3fda8-139">\<mode> are the CDC processing modes.</span></span> <span data-ttu-id="3fda8-140">处理模式具有以下值之一： **“全部”** 、 **“全部且具有旧值”** 、 **“净值”** 、 **“具有更新掩码的净值”** 和 **“净值且具有合并”** 。</span><span class="sxs-lookup"><span data-stu-id="3fda8-140">The processing modes have one of the following values **All**, **All with Old Values**, **Net**, **Net with Update Mask**, **Net with Merge**.</span></span>  
  
 <span data-ttu-id="3fda8-141">此脚本可通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中复现问题（在其中可以轻松地复现和标识错误），有助于标识问题。</span><span class="sxs-lookup"><span data-stu-id="3fda8-141">This script helps isolate problems by reproducing them in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], where it is easy to reproduce and identify errors.</span></span>  
  
#### <a name="sql-server-error-message"></a><span data-ttu-id="3fda8-142">SQL Server 错误消息</span><span class="sxs-lookup"><span data-stu-id="3fda8-142">SQL Server Error Message</span></span>  
 <span data-ttu-id="3fda8-143">下面是可以由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返回的消息：</span><span class="sxs-lookup"><span data-stu-id="3fda8-143">The following message may be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="3fda8-144">为过程或函数 cdc.fn_cdc_get_net_changes_\<..> 提供的参数数目不足。</span><span class="sxs-lookup"><span data-stu-id="3fda8-144">**An insufficient number of arguments were supplied for the procedure or function cdc.fn_cdc_get_net_changes_\<..>.**</span></span>  
  
 <span data-ttu-id="3fda8-145">此错误并不表示缺少参数。</span><span class="sxs-lookup"><span data-stu-id="3fda8-145">This error does not indicate that an argument is missing.</span></span> <span data-ttu-id="3fda8-146">这意味着 CDC 状态变量中的开始或结束 LSN 值无效。</span><span class="sxs-lookup"><span data-stu-id="3fda8-146">It means that the start or end LSN values in the CDC state variable are invalid.</span></span>  
  
## <a name="configuring-the-cdc-source"></a><span data-ttu-id="3fda8-147">配置 CDC 源</span><span class="sxs-lookup"><span data-stu-id="3fda8-147">Configuring the CDC Source</span></span>  
 <span data-ttu-id="3fda8-148">您可以通过编程方式或者通过 SSIS 设计器配置 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="3fda8-148">You can configure the CDC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="3fda8-149">有关详细信息，请参阅下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="3fda8-149">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3fda8-150">CDC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-150">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="3fda8-151">CDC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-151">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="3fda8-152">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-152">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="3fda8-153">**“高级编辑器”** 对话框包含可通过编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="3fda8-153">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="3fda8-154">打开 **“高级编辑器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="3fda8-154">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="3fda8-155">在您的 **项目的** “数据流” [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 屏幕上，右键单击 CDC 源，然后选择 **“显示高级编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="3fda8-155">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="3fda8-156">有关可在 **“高级编辑器”** 对话框中设置的属性的详细信息，请参阅 [CDC Source Custom Properties](cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3fda8-156">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fda8-157">本节内容</span><span class="sxs-lookup"><span data-stu-id="3fda8-157">In This Section</span></span>  
  
-   [<span data-ttu-id="3fda8-158">CDC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-158">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="3fda8-159">CDC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-159">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="3fda8-160">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="3fda8-160">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="3fda8-161">CDC 源自定义属性</span><span class="sxs-lookup"><span data-stu-id="3fda8-161">CDC Source Custom Properties</span></span>](cdc-source-custom-properties.md)  
  
-   [<span data-ttu-id="3fda8-162">使用 CDC 源提取更改数据</span><span class="sxs-lookup"><span data-stu-id="3fda8-162">Extract Change Data Using the CDC Source</span></span>](cdc-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="3fda8-163">相关内容</span><span class="sxs-lookup"><span data-stu-id="3fda8-163">Related Content</span></span>  
  
-   <span data-ttu-id="3fda8-164">mattmasson.com 上的博客文章 [CDC 源的处理模式](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/)。</span><span class="sxs-lookup"><span data-stu-id="3fda8-164">Blog entry, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/), on mattmasson.com.</span></span>  
  
  
