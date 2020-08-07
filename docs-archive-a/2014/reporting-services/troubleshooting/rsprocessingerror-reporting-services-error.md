---
title: rsProcessingError - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsProcessingError
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca98c5532db080ab1e146e2aaa81e24fcb25579b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588907"
---
# <a name="rsprocessingerror---reporting-services-error"></a><span data-ttu-id="5c982-102">rsProcessingError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="5c982-102">rsProcessingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="5c982-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5c982-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c982-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5c982-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="5c982-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5c982-105">Event ID</span></span>|<span data-ttu-id="5c982-106">rsProcessingError</span><span class="sxs-lookup"><span data-stu-id="5c982-106">rsProcessingError</span></span>|  
|<span data-ttu-id="5c982-107">事件源</span><span class="sxs-lookup"><span data-stu-id="5c982-107">Event Source</span></span>|<span data-ttu-id="5c982-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span><span class="sxs-lookup"><span data-stu-id="5c982-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span></span>|  
|<span data-ttu-id="5c982-109">组件</span><span class="sxs-lookup"><span data-stu-id="5c982-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="5c982-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="5c982-110">Message Text</span></span>|<span data-ttu-id="5c982-111">处理报表时出错。</span><span class="sxs-lookup"><span data-stu-id="5c982-111">Errors have occurred in report processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5c982-112">说明</span><span class="sxs-lookup"><span data-stu-id="5c982-112">Explanation</span></span>  
 <span data-ttu-id="5c982-113">在发布、处理、本地预览、从报表服务器中查看或者为报表创建订阅时，遇到了一个或多个错误。</span><span class="sxs-lookup"><span data-stu-id="5c982-113">One or more errors were encountered while publishing, processing, previewing locally, viewing from the report server, or creating a subscription for a report.</span></span> <span data-ttu-id="5c982-114">此错误消息表示至少检测到了一个错误。</span><span class="sxs-lookup"><span data-stu-id="5c982-114">This error message indicates at least one error was detected.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="5c982-115">可能的原因</span><span class="sxs-lookup"><span data-stu-id="5c982-115">Possible Causes</span></span>  
 <span data-ttu-id="5c982-116">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="5c982-116">Possible causes include:</span></span>  
  
-   <span data-ttu-id="5c982-117">报表服务器上发生处理错误。</span><span class="sxs-lookup"><span data-stu-id="5c982-117">A processing error occurred on the report server.</span></span>  
  
-   <span data-ttu-id="5c982-118">预览报表时，在本地报表处理期间发生处理错误。</span><span class="sxs-lookup"><span data-stu-id="5c982-118">A processing error occurred during local report processing when previewing a report.</span></span>  
  
-   <span data-ttu-id="5c982-119">组表达式的计算结果为错误的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5c982-119">A group expression evaluated to an incorrect data type.</span></span>  
  
-   <span data-ttu-id="5c982-120">筛选器定义指定了两个表达式，它们的计算结果为无法比较的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5c982-120">A filter definition specified two expressions that evaluated to data types that could not be compared.</span></span>  
  
-   <span data-ttu-id="5c982-121">表达式引用的字段在字段集合中不存在。</span><span class="sxs-lookup"><span data-stu-id="5c982-121">An expression referenced a non-existing field in the Fields collection.</span></span>  
  
-   <span data-ttu-id="5c982-122">表达式包含的聚合函数调用具有无效或有冲突的作用域。</span><span class="sxs-lookup"><span data-stu-id="5c982-122">An expression included an aggregate function call with an invalid or conflicting scope.</span></span>  
  
-   <span data-ttu-id="5c982-123">表达式引用的参数在报表参数集合中不存在。</span><span class="sxs-lookup"><span data-stu-id="5c982-123">An expression referenced a non-existing parameter in the Report Parameters collection.</span></span>  
  
-   <span data-ttu-id="5c982-124">无法加载未正确部署的自定义程序集或 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 程序集。</span><span class="sxs-lookup"><span data-stu-id="5c982-124">A custom assembly or a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] assembly that was incorrectly deployed failed to load.</span></span>  
  
-   <span data-ttu-id="5c982-125">将可为 Null 的属性设置为的参数 `False` 在参数中检测到 null 值。</span><span class="sxs-lookup"><span data-stu-id="5c982-125">A parameter that has the Nullable property set to `False` has detected a null value in the parameter.</span></span>  
  
-   <span data-ttu-id="5c982-126">数据区域的 Hidden 属性的表达式包含以下错误：“对象引用未设置为某个对象的实例”。</span><span class="sxs-lookup"><span data-stu-id="5c982-126">An expression for the Hidden property of a data region contains an error: Object reference not set to an instance of an object.</span></span>  
  
-   <span data-ttu-id="5c982-127">表达式包含的函数调用无效或有语法错误。</span><span class="sxs-lookup"><span data-stu-id="5c982-127">An expression included an invalid function call or syntax error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c982-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="5c982-128">User Action</span></span>  
  
### <a name="finding-more-information"></a><span data-ttu-id="5c982-129">查找详细信息</span><span class="sxs-lookup"><span data-stu-id="5c982-129">Finding More Information</span></span>  
 <span data-ttu-id="5c982-130">执行下列一种或多种操作：</span><span class="sxs-lookup"><span data-stu-id="5c982-130">Do one or more of the following actions:</span></span>  
  
-   <span data-ttu-id="5c982-131">如果是从报表服务器查看报表或将报表视为订阅，请查看错误消息的全文。</span><span class="sxs-lookup"><span data-stu-id="5c982-131">If you are viewing the report from the report server or if you are viewing the report as a subscription, look at the entire text of the error message.</span></span> <span data-ttu-id="5c982-132">扩充文本中提供了详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-132">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="5c982-133">如果在报表设计器中创作报表，并在预览或发布报表时出现该错误，则会在“错误列表”窗口中提供其他信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-133">If you are authoring a report in Report Designer and see this error when you preview or publish the report, additional information is provided in the Error List window.</span></span>  
  
-   <span data-ttu-id="5c982-134">如果在报表设计器预览中创作报表，请查看完整的错误消息文本。</span><span class="sxs-lookup"><span data-stu-id="5c982-134">If you are authoring a report in Report Designer Preview, look at the entire text of the error message.</span></span> <span data-ttu-id="5c982-135">扩充文本中提供了详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-135">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="5c982-136">如果在报表服务器上查看报表，并且以报表服务器上的本地管理员身份运行，则可以通过右键单击页并选择“查看源”来查看调用堆栈  。</span><span class="sxs-lookup"><span data-stu-id="5c982-136">If you are viewing a report on the report server, and if you are running as local administrator on the report server, you can view the call stack if you right-click the page and select **View Source**.</span></span> <span data-ttu-id="5c982-137">调用堆栈中提供了详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-137">Additional information is provided in the call stack.</span></span>  
  
-   <span data-ttu-id="5c982-138">如果以本地管理员身份在报表服务器上运行，请在日志文件中搜索 `ReportProcessingException`。</span><span class="sxs-lookup"><span data-stu-id="5c982-138">If you are running as local administrator on the report server, search the log file for `ReportProcessingException`.</span></span> <span data-ttu-id="5c982-139">日志项包含详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-139">Log entries contain more information.</span></span> <span data-ttu-id="5c982-140">Report Server 日志文件通常位于 \<*drive*> ： \Program FILES\MICROSOFT SQL Server\MSRS12。MSSQLSERVER\Reporting Services\LogFiles\ ReportServerService__*datetimestamp*。</span><span class="sxs-lookup"><span data-stu-id="5c982-140">The report server log file is typically located at \<*drive*>:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*.log.</span></span> <span data-ttu-id="5c982-141">有关详细信息，请参阅 [Reporting Services 日志文件和源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-141">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
### <a name="failed-to-load-expression-host-assembly"></a><span data-ttu-id="5c982-142">无法加载表达式宿主程序集。</span><span class="sxs-lookup"><span data-stu-id="5c982-142">Failed to Load Expression Host Assembly</span></span>  
 <span data-ttu-id="5c982-143">自定义程序集必须设置了强名称签名和 AllowPartiallyTrustedCallers 属性。</span><span class="sxs-lookup"><span data-stu-id="5c982-143">Custom assemblies must have strong name signing and the attribute AllowPartiallyTrustedCallers set.</span></span> <span data-ttu-id="5c982-144">有关详细信息，请参阅 [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) 和 [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-144">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) and [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md).</span></span>  
  
### <a name="a-built-in-global-name-does-not-exist"></a><span data-ttu-id="5c982-145">内置全局名称不存在</span><span class="sxs-lookup"><span data-stu-id="5c982-145">A Built-in Global Name Does Not Exist</span></span>  
 <span data-ttu-id="5c982-146">检查表达式的拼写。</span><span class="sxs-lookup"><span data-stu-id="5c982-146">Check the spelling in expressions.</span></span> <span data-ttu-id="5c982-147">内置全局名称、参数名称和字段名称均区分大小写。</span><span class="sxs-lookup"><span data-stu-id="5c982-147">Built-in globals, parameters, and field names are case-sensitive.</span></span> <span data-ttu-id="5c982-148">在导致错误的表达式中，检查该名称在报表中是否实际存在以及拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="5c982-148">In the expression causing the error, check that the name actually exists in the report and that it is spelled correctly.</span></span> <span data-ttu-id="5c982-149">有关详细信息，请参阅[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-149">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="parameter-properties-and-null"></a><span data-ttu-id="5c982-150">参数属性和 Null</span><span class="sxs-lookup"><span data-stu-id="5c982-150">Parameter Properties and Null</span></span>  
 <span data-ttu-id="5c982-151">多值参数不能为 Null。</span><span class="sxs-lookup"><span data-stu-id="5c982-151">A multivalue parameter cannot be Null.</span></span> <span data-ttu-id="5c982-152">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c982-152">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="main-report-with-subreport-could-not-be-processed"></a><span data-ttu-id="5c982-153">无法处理包含子报表的主报表</span><span class="sxs-lookup"><span data-stu-id="5c982-153">Main Report with Subreport Could Not Be Processed</span></span>  
 <span data-ttu-id="5c982-154">必须使用相同版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表处理器来处理包含子报表的报表。</span><span class="sxs-lookup"><span data-stu-id="5c982-154">A report with subreports must be processed by the same version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report processor.</span></span> <span data-ttu-id="5c982-155">将报表升级到报表定义架构的当前版本时，可能会同时更新主报表和子报表，也可能不会。</span><span class="sxs-lookup"><span data-stu-id="5c982-155">When upgrading reports to the current version of the report definition schema, the main report and the subreports may or may not be updated at the same time.</span></span> <span data-ttu-id="5c982-156">如果报表与其子报表的版本不兼容，则会出现以下消息：“无法处理子报表”。</span><span class="sxs-lookup"><span data-stu-id="5c982-156">If the version is not compatible between a report and its subreports, the following message is displayed: "Subreport could not be processed."</span></span>  
  
 <span data-ttu-id="5c982-157">必须更改主报表或子报表，以便使用相同版本的报表处理器来处理所有报表。</span><span class="sxs-lookup"><span data-stu-id="5c982-157">You must change either the main report or the subreports so that all the reports can be processed by the same version of the report processor.</span></span> <span data-ttu-id="5c982-158">有关报表为何无法进行升级的信息，请参阅 [升级报表](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-158">For information about why a report fails to upgrade, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="verify-function-calls-are-visual-basic-and-not-sql"></a><span data-ttu-id="5c982-159">验证函数调用为 Visual Basic 而不是 SQL</span><span class="sxs-lookup"><span data-stu-id="5c982-159">Verify Function Calls are Visual Basic and Not SQL</span></span>  
 <span data-ttu-id="5c982-160">可以在针对关系数据库的查询文本中使用 SQL 函数。</span><span class="sxs-lookup"><span data-stu-id="5c982-160">You can use SQL functions in query text on a relational database.</span></span> <span data-ttu-id="5c982-161">不能在查询文本中使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数。</span><span class="sxs-lookup"><span data-stu-id="5c982-161">You cannot use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions in query text.</span></span>  
  
 <span data-ttu-id="5c982-162">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，表达式可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数、System.Math 或 System.String 函数、完全限定的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 函数或自定义函数（以自定义代码或自定义程序集形式提供）。</span><span class="sxs-lookup"><span data-stu-id="5c982-162">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], expressions can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions, System.Math or System.String functions, fully qualified [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] functions, or custom functions that you provide in custom code or a custom assembly.</span></span> <span data-ttu-id="5c982-163">不能在表达式中使用 SQL 函数。</span><span class="sxs-lookup"><span data-stu-id="5c982-163">You cannot use SQL functions in an expression.</span></span>  
  
 <span data-ttu-id="5c982-164">验证查询和表达式中进行的函数调用是否有效。</span><span class="sxs-lookup"><span data-stu-id="5c982-164">Verify that the function calls made in the query and in the expressions are valid.</span></span>  
  
### <a name="cannot-compare-data-types-for-a-filter"></a><span data-ttu-id="5c982-165">无法比较筛选器的数据类型</span><span class="sxs-lookup"><span data-stu-id="5c982-165">Cannot Compare Data Types for a Filter</span></span>  
 <span data-ttu-id="5c982-166">在筛选器公式中，定义筛选内容的筛选器表达式和筛选器值必须为相同数据类型才能进行比较。</span><span class="sxs-lookup"><span data-stu-id="5c982-166">In a filter equation, the filter expression that defines what to filter on and the filter value must be the same data type in order to be compared.</span></span> <span data-ttu-id="5c982-167">如果出现以下错误之一，请修改字段表达式或筛选器值以使数据类型匹配：</span><span class="sxs-lookup"><span data-stu-id="5c982-167">If you see one of the following errors, modify the field expression or the filter value so that the data types match:</span></span>  
  
-   <span data-ttu-id="5c982-168">无法对的 *\<report item type>* 进行处理 *\<report item name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-168">The processing of *\<report item type>* for the *\<report item name>* cannot be performed.</span></span> <span data-ttu-id="5c982-169">无法比较类型和的 *\<type>* 数据 *\<type>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-169">Cannot compare data of types *\<type>* and *\<type>*.</span></span> <span data-ttu-id="5c982-170">请检查返回的数据类型 *\<report item name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-170">Please check the data type returned by the *\<report item name>*.</span></span>  
  
-   <span data-ttu-id="5c982-171">无法计算 *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-171">Failed to evaluate the *\<property name>*.</span></span>  
  
-   <span data-ttu-id="5c982-172">无法计算 *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-172">Failed to evaluate the *\<property name>*.</span></span> <span data-ttu-id="5c982-173">它引用的数据集字段包含错误： *\<error string>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-173">It references a dataset field which has an error: *\<error string>*.</span></span>  
  
 <span data-ttu-id="5c982-174">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-174">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
### <a name="invalid-or-conflicting-scope-specification-in-an-aggregate-function-call"></a><span data-ttu-id="5c982-175">聚合函数调用中指定的作用域无效或有冲突</span><span class="sxs-lookup"><span data-stu-id="5c982-175">Invalid or Conflicting Scope Specification in an Aggregate Function Call</span></span>  
 <span data-ttu-id="5c982-176">如果 Tablix 单元中包含对表达式的聚合函数调用，报表处理器将使用单元所属的最内部组的作用域来计算表达式。</span><span class="sxs-lookup"><span data-stu-id="5c982-176">When you include aggregate function calls to an expression in a Tablix cell, the report processor evaluates the expression in the scope of the innermost groups to which the cell belongs.</span></span>  
  
 <span data-ttu-id="5c982-177">也可以将特定作用域的名称传递给聚合函数。</span><span class="sxs-lookup"><span data-stu-id="5c982-177">You can also pass the name of a specific scope to an aggregate function.</span></span> <span data-ttu-id="5c982-178">作用域可以引用数据集和数据区域的名称，也可以引用位于数据层次结构中较高位置的作用域的名称。</span><span class="sxs-lookup"><span data-stu-id="5c982-178">Scope can refer to the name of a dataset, a data region, or the name of a scope higher on the data hierarchy.</span></span> <span data-ttu-id="5c982-179">这适用于以下消息：</span><span class="sxs-lookup"><span data-stu-id="5c982-179">This applies to the following messages:</span></span>  
  
-   <span data-ttu-id="5c982-180">*\<report item type>*" *\<report item name>* " 具有无效的作用域 " *\<scope name>* "。</span><span class="sxs-lookup"><span data-stu-id="5c982-180">The *\<report item type>* '*\<report item name>*' has an invalid scope "*\<scope name>*".</span></span> <span data-ttu-id="5c982-181">该作用域必须是当前作用域或包含在当前作用域内。</span><span class="sxs-lookup"><span data-stu-id="5c982-181">The scope must be the current scope, or contained within the current scope.</span></span>  
  
-   <span data-ttu-id="5c982-182">*\<property name>*"" 的表达式 *\<report item type>* 包含的 *\<report item name>* 作用域参数对聚合函数无效。</span><span class="sxs-lookup"><span data-stu-id="5c982-182">The *\<property name>* expression for the *\<report item type>* '*\<report item name>*' has a scope parameter that is not valid for an aggregate function.</span></span> <span data-ttu-id="5c982-183">作用域参数必须设置为字符串常量，该常量可以等于所包含组的名称、所包含数据区域的名称或数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="5c982-183">The scope parameter must be set to a string constant that is equal to either the name of a containing group, the name of a containing data region, or the name of a dataset.</span></span>  
  
 <span data-ttu-id="5c982-184">对于计算运行总计的聚合函数（`Previous`、`RunningValue` 或 `RowNumber`），可以将作用域参数指定为行组名称或列组名称，但不能同时指定二者。</span><span class="sxs-lookup"><span data-stu-id="5c982-184">For aggregate functions that calculate running totals (`Previous`, `RunningValue`, or `RowNumber`), you can specify a scope parameter that is either a row group name or a column group name, but not both.</span></span> <span data-ttu-id="5c982-185">这适用于以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="5c982-185">This applies to the following error message:</span></span>  
  
-   <span data-ttu-id="5c982-186">`Previous``RunningValue`或 `RowNumber` 在 "" 的数据单元中使用的聚合 *\<report item type>* 函数 *\<report item name>* 引用的列和行中的分组作用域 *\<report item type>* 。</span><span class="sxs-lookup"><span data-stu-id="5c982-186">`Previous`, `RunningValue` or `RowNumber` aggregate functions used in the data cells of the *\<report item type>* '*\<report item name>*' refer to grouping scopes in both the columns and rows of the *\<report item type>*.</span></span> <span data-ttu-id="5c982-187">`Previous`中所有、和聚合函数的作用域参数 `RunningValue` `RowNumber` *\<report item type>* 可以引用行分组或数据列分组，但不能同时引用两者。</span><span class="sxs-lookup"><span data-stu-id="5c982-187">The scope parameters of all `Previous`, `RunningValue` and `RowNumber` aggregate functions within a *\<report item type>* can refer to row groupings or data column groupings, but not both.</span></span>  
  
 <span data-ttu-id="5c982-188">有关详细信息，请参阅[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)和[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5c982-188">For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) and [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="default-dataset-scope-for-a-top-level-text-box"></a><span data-ttu-id="5c982-189">顶级文本框的默认数据集作用域</span><span class="sxs-lookup"><span data-stu-id="5c982-189">Default Dataset Scope for a Top Level Text Box</span></span>  
 <span data-ttu-id="5c982-190">如果报表包含多个数据集，请勿使用添加到报表设计图面上的文本框的默认作用域。</span><span class="sxs-lookup"><span data-stu-id="5c982-190">Do not use a default scope for a text box added to the report design surface when the report has more than one dataset.</span></span> <span data-ttu-id="5c982-191">应使用一个表达式，其中包含数据集名称（作为作用域）和聚合函数。</span><span class="sxs-lookup"><span data-stu-id="5c982-191">Use an expression that includes the name of the dataset as the scope, and an aggregate function.</span></span> <span data-ttu-id="5c982-192">例如，`=First(Fields!FieldName.Value, "DataSet2")` 。</span><span class="sxs-lookup"><span data-stu-id="5c982-192">For example, `=First(Fields!FieldName.Value, "DataSet2")`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c982-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c982-193">See Also</span></span>  
 <span data-ttu-id="5c982-194">[表达式（报表生成器和 SSRS）](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-194">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c982-195">[聚合函数引用（报表生成器和 SSRS）](../report-design/report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-195">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="5c982-196">[表达式示例（报表生成器和 SSRS）](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-196">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c982-197">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-197">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="5c982-198">[常用筛选器（报表生成器和 SSRS）](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-198">[Commonly Used Filters &#40;Report Builder and SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c982-199">[数据集字段集合（报表生成器和 SSRS）](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-199">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c982-200">[报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c982-200">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 [<span data-ttu-id="5c982-201">Parameters 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5c982-201">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](../report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
