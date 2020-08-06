---
title: rsServerConfigurationError - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02f8a18c42715d1f118920614eb425820130dacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692232"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a><span data-ttu-id="44faf-102">rsServerConfigurationError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="44faf-102">rsServerConfigurationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="44faf-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="44faf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44faf-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="44faf-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="44faf-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="44faf-105">Event ID</span></span>|<span data-ttu-id="44faf-106">rsServerConfiguration</span><span class="sxs-lookup"><span data-stu-id="44faf-106">rsServerConfiguration</span></span>|  
|<span data-ttu-id="44faf-107">事件源</span><span class="sxs-lookup"><span data-stu-id="44faf-107">Event Source</span></span>|<span data-ttu-id="44faf-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="44faf-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="44faf-109">组件</span><span class="sxs-lookup"><span data-stu-id="44faf-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="44faf-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="44faf-110">Message Text</span></span>|<span data-ttu-id="44faf-111">报表服务器遇到配置错误。</span><span class="sxs-lookup"><span data-stu-id="44faf-111">The report server has encountered a configuration error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="44faf-112">说明</span><span class="sxs-lookup"><span data-stu-id="44faf-112">Explanation</span></span>  
 <span data-ttu-id="44faf-113">这是一个在报表服务器或报表创作工具具有无效配置设置时出现的常规错误。</span><span class="sxs-lookup"><span data-stu-id="44faf-113">This is a general purpose error that occurs when either the report server or a report authoring tool has invalid configuration settings.</span></span> <span data-ttu-id="44faf-114">通常该错误还附带另一条消息，该消息声明此错误的实际原因。</span><span class="sxs-lookup"><span data-stu-id="44faf-114">The error is usually accompanied by a second message that states the actual cause of the error.</span></span>  
  
 <span data-ttu-id="44faf-115">下面的列表汇总了可能的原因：</span><span class="sxs-lookup"><span data-stu-id="44faf-115">The following list summarizes possible causes:</span></span>  
  
-   <span data-ttu-id="44faf-116">找不到或无法读取 RSReportServer.config 或 RSReportDesigner.config 文件。</span><span class="sxs-lookup"><span data-stu-id="44faf-116">The RSReportServer.config or RSReportDesigner.config file cannot be found or read.</span></span>  
  
-   <span data-ttu-id="44faf-117">这两个配置文件中有一个文件的 XML 元素丢失或无效。</span><span class="sxs-lookup"><span data-stu-id="44faf-117">XML elements in either configuration file are missing or invalid.</span></span>  
  
-   <span data-ttu-id="44faf-118">一个或多个 XML 元素的值丢失或无效。</span><span class="sxs-lookup"><span data-stu-id="44faf-118">Values for one or more XML elements are missing or invalid.</span></span>  
  
-   <span data-ttu-id="44faf-119">注册表设置无效。</span><span class="sxs-lookup"><span data-stu-id="44faf-119">Registry settings are invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="44faf-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="44faf-120">User Action</span></span>  
 <span data-ttu-id="44faf-121">如果该错误在您手动编辑配置文件后开始出现，请删除所做的更改并输入以前的值，或者如果您有备份，请还原先前的版本。</span><span class="sxs-lookup"><span data-stu-id="44faf-121">If this error began to occur after you manually edited a configuration file, remove your changes and enter the previous value, or restore a previous version if you have a backup.</span></span>  
  
 <span data-ttu-id="44faf-122">若要查看错误附带的其他错误消息信息 `rsServerConfiguration` ，请查看 Report Server 跟踪日志文件，这些文件位于 \MICROSOFT SQL Server\MSRS12. \<instancename >\Reporting Services\logfiles。</span><span class="sxs-lookup"><span data-stu-id="44faf-122">To review additional error message information that accompanies the `rsServerConfiguration` error, review the report server trace log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="44faf-123">有关详细信息，请参阅 [Reporting Services 日志文件和源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="44faf-123">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="44faf-124">仅内部</span><span class="sxs-lookup"><span data-stu-id="44faf-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44faf-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44faf-125">See Also</span></span>  
 <span data-ttu-id="44faf-126">[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="44faf-126">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="44faf-127">修改 Reporting Services 配置文件 (RSreportserver.config)</span><span class="sxs-lookup"><span data-stu-id="44faf-127">Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;</span></span>](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
