---
title: rsInternalError - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85b88519df810f60c580ad2d6eb355dde236d081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587158"
---
# <a name="rsinternalerror---reporting-services-error"></a><span data-ttu-id="30247-102">rsInternalError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="30247-102">rsInternalError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="30247-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="30247-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30247-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="30247-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="30247-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="30247-105">Event ID</span></span>|<span data-ttu-id="30247-106">rsInternalError</span><span class="sxs-lookup"><span data-stu-id="30247-106">rsInternalError</span></span>|  
|<span data-ttu-id="30247-107">事件源</span><span class="sxs-lookup"><span data-stu-id="30247-107">Event Source</span></span>|<span data-ttu-id="30247-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="30247-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="30247-109">组件</span><span class="sxs-lookup"><span data-stu-id="30247-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="30247-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="30247-110">Message Text</span></span>|<span data-ttu-id="30247-111">报表服务器上出现内部错误。</span><span class="sxs-lookup"><span data-stu-id="30247-111">An internal error occurred on the report server.</span></span> <span data-ttu-id="30247-112">有关详细信息，请参阅错误日志。</span><span class="sxs-lookup"><span data-stu-id="30247-112">See the error log for more details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="30247-113">说明</span><span class="sxs-lookup"><span data-stu-id="30247-113">Explanation</span></span>  
 <span data-ttu-id="30247-114">这是一种一般性错误消息，后面通常跟着可提供详细信息的更具说明性的错误。</span><span class="sxs-lookup"><span data-stu-id="30247-114">This is a generic error message that is often followed by a more descriptive error that provides more detail.</span></span>  
  
 <span data-ttu-id="30247-115">内部错误不常见。</span><span class="sxs-lookup"><span data-stu-id="30247-115">Internal errors are uncommon.</span></span> <span data-ttu-id="30247-116">如果出现此错误，可以查看报表服务器跟踪日志以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="30247-116">If you get this error, more information is available in report server trace logs.</span></span> <span data-ttu-id="30247-117">此外，如果是以本地管理员的身份在出现错误的计算机上运行，则可以查看调用堆栈以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="30247-117">In addition, if you are running as local administrator on the same computer on which the error occurs, you can view the call stack for more information.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="30247-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="30247-118">User Action</span></span>  
 <span data-ttu-id="30247-119">若要确定出现此消息的具体原因，请查看 Report Server 日志文件，这些文件位于 \Microsoft SQL Server\MSRS12. \<instancename >\Reporting Services\logfiles。</span><span class="sxs-lookup"><span data-stu-id="30247-119">To determine the specific cause for this message, review the report server log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="30247-120">有关详细信息，请参阅 [Reporting Services 日志文件和源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="30247-120">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
 <span data-ttu-id="30247-121">若要查看调用堆栈，请右键单击出现错误的页，然后指向“查看源”  。</span><span class="sxs-lookup"><span data-stu-id="30247-121">To view the call stack, right-click the page on which the error occurs and point to **View Source**.</span></span> <span data-ttu-id="30247-122">必须在出现该错误的同一计算机上具有管理员权限，才可查看调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="30247-122">Viewing the call stack requires administrator permissions on the same computer on which the error occurs.</span></span>  
  
 <span data-ttu-id="30247-123">如果没有其他可用信息，请再次尝试请求。</span><span class="sxs-lookup"><span data-stu-id="30247-123">If there is no additional information available, you can try your request again.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="30247-124">仅内部</span><span class="sxs-lookup"><span data-stu-id="30247-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30247-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30247-125">See Also</span></span>  
 [<span data-ttu-id="30247-126">启动和停止报表服务器服务</span><span class="sxs-lookup"><span data-stu-id="30247-126">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
