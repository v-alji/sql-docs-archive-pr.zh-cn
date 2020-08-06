---
title: 标识执行状态 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe53254a5da39c4e7d003ba37d5812ad130293e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590035"
---
# <a name="identifying-execution-state"></a><span data-ttu-id="e0a84-102">标识执行状态</span><span class="sxs-lookup"><span data-stu-id="e0a84-102">Identifying Execution State</span></span>
  <span data-ttu-id="e0a84-103">超文本传输协议 (HTTP) 是一个无连接且无状态协议，这意味着它不自动指示不同请求是否来自同一个客户端，甚至也不指示单个浏览器实例是否仍在查看页面或站点。</span><span class="sxs-lookup"><span data-stu-id="e0a84-103">Hypertext Transfer Protocol (HTTP) is a connectionless and stateless protocol, which means that it does not automatically indicate whether different requests come from the same client or even whether a single browser instance is still actively viewing a page or site.</span></span> <span data-ttu-id="e0a84-104">会话创建逻辑连接，以通过 HTTP 在服务器与客户端之间维护状态。</span><span class="sxs-lookup"><span data-stu-id="e0a84-104">Sessions create a logical connection to maintain state between server and client over HTTP.</span></span> <span data-ttu-id="e0a84-105">与特定会话相关的用户特定的信息称为会话状态。</span><span class="sxs-lookup"><span data-stu-id="e0a84-105">The user-specific information relevant to a particular session is known as the session state.</span></span>

 <span data-ttu-id="e0a84-106">会话管理涉及将 HTTP 请求与从同一个会话生成的其他先前请求相关。</span><span class="sxs-lookup"><span data-stu-id="e0a84-106">Session management involves correlating an HTTP request with other previous requests generated from the same session.</span></span> <span data-ttu-id="e0a84-107">如果没有会话管理，则由于 HTTP 协议的无连接和无状态性质，因此这些请求将与报表服务器 Web 服务无关。</span><span class="sxs-lookup"><span data-stu-id="e0a84-107">Without session management, these requests appear unrelated to the Report Server Web service because of the connectionless and stateless nature of the HTTP protocol.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e0a84-108">不公开会话状态的总体概念，例如，由 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 公开的这类概念。</span><span class="sxs-lookup"><span data-stu-id="e0a84-108">does not expose a holistic concept of session state such as that exposed by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="e0a84-109">然而，当执行报表时，报表服务器以 execution 的形式维护方法调用之间的状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0a84-109">However, when executing reports, the report server maintains state between method calls in the form of an **execution**.</span></span> <span data-ttu-id="e0a84-110">执行允许用户通过多种方式与报表交互 - 包括从报表服务器加载报表，为报表设置凭据和参数，以及呈现报表。</span><span class="sxs-lookup"><span data-stu-id="e0a84-110">An execution allows the user to interact with the report in several ways - including loading the report from the report server, setting credentials and parameters for the report, and rendering the report.</span></span>

 <span data-ttu-id="e0a84-111">当客户端与报表服务器通信时，它们使用执行来管理报表查看和用户在报表中导航到其他页的过程，以及显示或隐藏报表的各个部分。</span><span class="sxs-lookup"><span data-stu-id="e0a84-111">While they are communicating to a report server, clients use the execution to manage report viewing and user navigation to other pages in a report, and to show or hide sections of a report.</span></span> <span data-ttu-id="e0a84-112">对于客户端应用程序正在运行的每个报表，都存在一个唯一执行。</span><span class="sxs-lookup"><span data-stu-id="e0a84-112">A unique execution exists for each report the client application is running.</span></span>

 <span data-ttu-id="e0a84-113">通常，当用户导航到浏览器或客户端应用程序并选择要查看的报表时，执行的生存期开始。</span><span class="sxs-lookup"><span data-stu-id="e0a84-113">In general, the lifetime of an execution starts when a user navigates to a browser or client application and selects a report to view.</span></span> <span data-ttu-id="e0a84-114">在收到最后一个执行请求后的很短超时时段（默认超时值为 20 分钟）之后，将放弃执行。</span><span class="sxs-lookup"><span data-stu-id="e0a84-114">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="e0a84-115">从 Web 服务角度来看，当调用报表服务器 Web 服务 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>、<xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 或 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法时，生存期开始。</span><span class="sxs-lookup"><span data-stu-id="e0a84-115">From a Web service perspective, the lifetime starts when the Report Server Web service <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>, or <xref:ReportExecution2005.ReportExecutionService.Render%2A> methods are called.</span></span> <span data-ttu-id="e0a84-116">应用程序可以使用其他方法来控制处于活动状态的执行（例如，设置参数和设置数据源）。</span><span class="sxs-lookup"><span data-stu-id="e0a84-116">The application can use other methods to manipulate the active execution (for example, setting parameters and setting data sources).</span></span> <span data-ttu-id="e0a84-117">在收到最后一个执行请求后的很短超时时段（默认超时值为 20 分钟）之后，将放弃执行。</span><span class="sxs-lookup"><span data-stu-id="e0a84-117">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="e0a84-118">应用程序通过保存 <xref:ReportExecution2005.ReportExecutionService.Render%2A>（从 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 和 <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A> 方法的 SOAP 标头中返回），对针对 Web 服务 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 和 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 方法的调用之间的多个处于活动状态的执行保持跟踪。</span><span class="sxs-lookup"><span data-stu-id="e0a84-118">An application keep track of multiple active executions between calls to the Web service <xref:ReportExecution2005.ReportExecutionService.Render%2A> and <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> methods by saving the <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>, which is returned in the SOAP header from the <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> and <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> methods.</span></span>

 <span data-ttu-id="e0a84-119">下图显示报表的处理和呈现路径。</span><span class="sxs-lookup"><span data-stu-id="e0a84-119">The following diagram shows the processing and rendering path for reports.</span></span>

 <span data-ttu-id="e0a84-120">![报表处理/呈现路径](../../../2014/reporting-services/media/rs-render-process-diagram.gif "报表处理/呈现路径")</span><span class="sxs-lookup"><span data-stu-id="e0a84-120">![Report processing/rendering path](../../../2014/reporting-services/media/rs-render-process-diagram.gif "Report processing/rendering path")</span></span>

 <span data-ttu-id="e0a84-121">为了支持上面介绍的函数，当前 SOAP Render 方法已被拆分为多个方法，其中包括执行初始化阶段、处理阶段和呈现阶段。</span><span class="sxs-lookup"><span data-stu-id="e0a84-121">To support the functions described above, the current SOAP Render method has been split into multiple methods encompassing execution initialization, processing, and rendering phases.</span></span>

 <span data-ttu-id="e0a84-122">若要以编程方式呈现报表，您必须：</span><span class="sxs-lookup"><span data-stu-id="e0a84-122">To programmatically render a report, you must:</span></span>

-   <span data-ttu-id="e0a84-123">使用 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 或 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 加载报表或报表定义。</span><span class="sxs-lookup"><span data-stu-id="e0a84-123">Load the report or the report definition using <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.</span></span>

-   <span data-ttu-id="e0a84-124">通过检查由 <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> 或 <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> 返回的 <xref:ReportExecution2005.ExecutionInfo> 对象的 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 和 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 属性，检查报表是否需要凭据或参数。</span><span class="sxs-lookup"><span data-stu-id="e0a84-124">Check to see if the report needs credentials or parameters by checking the values of the <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> and <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> properties of the <xref:ReportExecution2005.ExecutionInfo> object returned by <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A></span></span>

-   <span data-ttu-id="e0a84-125">如果需要，则使用 <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> 和 <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> 方法设置凭据和/或参数。</span><span class="sxs-lookup"><span data-stu-id="e0a84-125">If necessary, set the credentials and/or parameters using the <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> and <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> methods.</span></span>

-   <span data-ttu-id="e0a84-126">调用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法以呈现报表。</span><span class="sxs-lookup"><span data-stu-id="e0a84-126">Call the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to render the report.</span></span>

 <span data-ttu-id="e0a84-127">当报表处于会话中时，存储在报表服务器数据库中的基础报表可能发生变化。</span><span class="sxs-lookup"><span data-stu-id="e0a84-127">While a report is in session, the underlying report stored in the report server database can change.</span></span> <span data-ttu-id="e0a84-128">例如，报表定义可能发生变化，可能删除或移动报表，用户权限可能变化。</span><span class="sxs-lookup"><span data-stu-id="e0a84-128">For example, the report definition can change, the report can be deleted or moved, and user permissions can change.</span></span> <span data-ttu-id="e0a84-129">如果报表处于活动的会话中，则它不受对基础报表（也即，存储在报表服务器数据库中的报表）所做更改的影响。</span><span class="sxs-lookup"><span data-stu-id="e0a84-129">If the report is in an active session, it is not affected by changes made to the underlying report (that is, the report stored in the report server database).</span></span>

 <span data-ttu-id="e0a84-130">您还可以使用 URL 访问命令管理报表会话。</span><span class="sxs-lookup"><span data-stu-id="e0a84-130">You can also manage a report session using URL access commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0a84-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0a84-131">See Also</span></span>
 <span data-ttu-id="e0a84-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A>[使用 REPORTING SERVICES SOAP 标头](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md) [&#40;SSRS&#41;的技术参考](../../../2014/reporting-services/technical-reference-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="e0a84-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A> [Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) [Using Reporting Services SOAP Headers](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)</span></span>


