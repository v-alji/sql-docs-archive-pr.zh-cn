---
title: 报表服务器 Windows 服务 (MSSQLServer) 107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8651f98b47b698fbe3cfb6a152b9220a84ed7256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581127"
---
# <a name="report-server-windows-service-mssqlserver-107"></a><span data-ttu-id="d1a77-102">报表服务器 Windows 服务 (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="d1a77-102">Report Server Windows Service (MSSQLServer) 107</span></span>
    
## <a name="details"></a><span data-ttu-id="d1a77-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d1a77-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1a77-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d1a77-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d1a77-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d1a77-105">Event ID</span></span>|<span data-ttu-id="d1a77-106">107</span><span class="sxs-lookup"><span data-stu-id="d1a77-106">107</span></span>|  
|<span data-ttu-id="d1a77-107">事件源</span><span class="sxs-lookup"><span data-stu-id="d1a77-107">Event Source</span></span>|<span data-ttu-id="d1a77-108">报表服务器 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="d1a77-108">Report Server Windows Service</span></span>|  
|<span data-ttu-id="d1a77-109">组件</span><span class="sxs-lookup"><span data-stu-id="d1a77-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="d1a77-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="d1a77-110">Message Text</span></span>|<span data-ttu-id="d1a77-111">报表服务器 Windows 服务 (MSSQLSERVER) 无法与报表服务器数据库建立连接。</span><span class="sxs-lookup"><span data-stu-id="d1a77-111">Report Server Windows Service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1a77-112">说明</span><span class="sxs-lookup"><span data-stu-id="d1a77-112">Explanation</span></span>  
 <span data-ttu-id="d1a77-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 报表服务器服务无法连接到报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="d1a77-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service cannot connect to the report server database.</span></span> <span data-ttu-id="d1a77-114">如果无法建立与报表服务器数据库的连接，在服务重新启动过程中就会出现该错误。</span><span class="sxs-lookup"><span data-stu-id="d1a77-114">This error occurs during a service restart if a connection to the report server database cannot be established.</span></span> <span data-ttu-id="d1a77-115">在下列情况下会出现此错误：</span><span class="sxs-lookup"><span data-stu-id="d1a77-115">Conditions under which this error occurs include the following:</span></span>  
  
-   <span data-ttu-id="d1a77-116">当报表服务器服务启动时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务没有运行。</span><span class="sxs-lookup"><span data-stu-id="d1a77-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is not running when the Report Server service starts.</span></span>  
  
-   <span data-ttu-id="d1a77-117">由于远程连接或 TCP/IP 协议未启用，无法连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="d1a77-117">The connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service fails because remote connections or the TCP/IP protocol is not enabled.</span></span>  
  
-   <span data-ttu-id="d1a77-118">报表服务器数据库配置不正确。</span><span class="sxs-lookup"><span data-stu-id="d1a77-118">The report server database is not configured correctly.</span></span>  
  
-   <span data-ttu-id="d1a77-119">服务帐户配置不正确，或该帐户不再有权访问报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="d1a77-119">The service account is not configured correctly, or the account no longer has permissions on the report server database.</span></span> <span data-ttu-id="d1a77-120">如果不使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具来设置该帐户或报表服务器数据库，就可能出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="d1a77-120">This can occur if you do not use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set up the account or the report server database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1a77-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="d1a77-121">User Action</span></span>  
 <span data-ttu-id="d1a77-122">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务未运行，请启动此服务，并检查是否针对 TCP/IP 协议启用了远程连接。</span><span class="sxs-lookup"><span data-stu-id="d1a77-122">Start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service if it is not running and check that remote connections are enabled for TCP/IP protocol.</span></span>  
  
 <span data-ttu-id="d1a77-123">使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具配置报表服务器数据库和服务帐户。</span><span class="sxs-lookup"><span data-stu-id="d1a77-123">Use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the report server database and service account.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="d1a77-124">仅内部</span><span class="sxs-lookup"><span data-stu-id="d1a77-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a77-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1a77-125">See Also</span></span>  
 <span data-ttu-id="d1a77-126">[配置报表服务器服务帐户（SSRS 配置管理器）](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d1a77-126">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="d1a77-127">[Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d1a77-127">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 [<span data-ttu-id="d1a77-128">启动和停止报表服务器服务</span><span class="sxs-lookup"><span data-stu-id="d1a77-128">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
