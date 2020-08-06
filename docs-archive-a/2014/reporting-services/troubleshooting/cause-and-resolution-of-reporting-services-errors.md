---
title: Reporting Services 错误的原因和解决方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- troubleshooting [Reporting Services], errors
ms.assetid: 3db0fef3-37f8-40d0-acc7-1928760dc0e9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa98b9f760485b80f4fa4ac74f3b8008dc3bbec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689728"
---
# <a name="cause-and-resolution-of-reporting-services-errors"></a><span data-ttu-id="d1153-102">Reporting Services 错误的原因和解决方法</span><span class="sxs-lookup"><span data-stu-id="d1153-102">Cause and Resolution of Reporting Services Errors</span></span>
  <span data-ttu-id="d1153-103">本主题包含与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]相关的多个错误的原因和解决方法信息。</span><span class="sxs-lookup"><span data-stu-id="d1153-103">This topic contains cause and resolution information for a number of errors related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="d1153-104">本节中的错误消息主题提供对错误消息、可能的原因以及为更正问题可以采取的所有措施的说明。</span><span class="sxs-lookup"><span data-stu-id="d1153-104">The error message topics in this section provide an explanation of the error message, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1153-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="d1153-105">In This Section</span></span>  
  
|<span data-ttu-id="d1153-106">错误</span><span class="sxs-lookup"><span data-stu-id="d1153-106">Error</span></span>|<span data-ttu-id="d1153-107">消息</span><span class="sxs-lookup"><span data-stu-id="d1153-107">Message</span></span>|  
|-----------|-------------|  
|[<span data-ttu-id="d1153-108">rsAccessedDenied - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-108">rsAccessedDenied - Reporting Services Error</span></span>](rsaccesseddenied-reporting-services-error.md)|<span data-ttu-id="d1153-109">为用户“mydomain\myAccount”授予的权限不足，无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d1153-109">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="d1153-110">(rsAccessDenied) (ReportingServicesLibrary)。</span><span class="sxs-lookup"><span data-stu-id="d1153-110">(rsAccessDenied) (ReportingServicesLibrary).</span></span>|  
|[<span data-ttu-id="d1153-111">rsInternalError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-111">rsInternalError - Reporting Services Error</span></span>](rsinternalerror-reporting-services-error.md)|<span data-ttu-id="d1153-112">报表服务器上出现内部错误。</span><span class="sxs-lookup"><span data-stu-id="d1153-112">An internal error occurred on the report server.</span></span> <span data-ttu-id="d1153-113">有关详细信息，请参阅错误日志。</span><span class="sxs-lookup"><span data-stu-id="d1153-113">See the error log for more details.</span></span>|  
|[<span data-ttu-id="d1153-114">rsModelGenerationError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-114">rsModelGenerationError - Reporting Services Error</span></span>](rsmodelgenerationerror-reporting-services-error.md)|<span data-ttu-id="d1153-115">生成模型时出错。</span><span class="sxs-lookup"><span data-stu-id="d1153-115">An error occurred while generating model.</span></span> <span data-ttu-id="d1153-116">(rsModelGenerationError) (ReportingServicesLibrary) %1。</span><span class="sxs-lookup"><span data-stu-id="d1153-116">(rsModelGenerationError) (ReportingServicesLibrary) %1.</span></span>|  
|[<span data-ttu-id="d1153-117">rsProcessingError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-117">rsProcessingError - Reporting Services Error</span></span>](rsprocessingerror-reporting-services-error.md)|<span data-ttu-id="d1153-118">处理报表时出错。</span><span class="sxs-lookup"><span data-stu-id="d1153-118">Errors have occurred in report processing.</span></span>|  
|[<span data-ttu-id="d1153-119">rsServerConfigurationError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-119">rsServerConfigurationError - Reporting Services Error</span></span>](rsserverconfigurationerror-reporting-services-error.md)|<span data-ttu-id="d1153-120">报表服务器遇到配置错误。</span><span class="sxs-lookup"><span data-stu-id="d1153-120">The report server has encountered a configuration error.</span></span>|  
|[<span data-ttu-id="d1153-121">rrRenderingError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="d1153-121">rrRenderingError - Reporting Services Error</span></span>](rrrenderingerror-reporting-services-error.md)|<span data-ttu-id="d1153-122">呈现报表时出错。</span><span class="sxs-lookup"><span data-stu-id="d1153-122">An error occurred during rendering of the report.</span></span> <span data-ttu-id="d1153-123">(rrRenderingError) %1。</span><span class="sxs-lookup"><span data-stu-id="d1153-123">(rrRenderingError) %1.</span></span>|  
|[<span data-ttu-id="d1153-124">报表服务器 Windows 服务 (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="d1153-124">Report Server Windows Service &#40;MSSQLServer&#41; 107</span></span>](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md)|<span data-ttu-id="d1153-125">报表服务器 Windows 服务 (MSSQLSERVER) 无法与报表服务器数据库建立连接。</span><span class="sxs-lookup"><span data-stu-id="d1153-125">Report Server Windows service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1153-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1153-126">See Also</span></span>  
 <span data-ttu-id="d1153-127">[Reporting Services 日志文件和来源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="d1153-127">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="d1153-128">错误和事件参考 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="d1153-128">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](errors-and-events-reference-reporting-services.md)  
  
  
