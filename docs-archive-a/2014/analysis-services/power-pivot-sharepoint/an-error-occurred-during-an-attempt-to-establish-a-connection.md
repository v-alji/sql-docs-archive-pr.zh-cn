---
title: 在尝试建立与外部数据源的连接的过程中出现错误。 以下连接无法刷新： PowerPivot 数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb4329440b69d1bdfdbb96fbcc3926fa000d8877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689618"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="3ea0e-103">在尝试建立与外部数据源的连接的过程中出现错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-103">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="3ea0e-104">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="3ea0e-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="3ea0e-105">如果您在未安装 PowerPivot for SharePoint 的服务器上查询 PowerPivot 数据，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-105">This error occurs if you query PowerPivot data on a server that does not have PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="3ea0e-106">如果停止 SQL Server Analysis Services (PowerPivot) 服务，或是您试图查看以前版本的 PowerPivot 数据，此时也会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-106">It also occurs if the SQL Server Analysis Services (PowerPivot) service is stopped, or if you are attempting to view PowerPivot data from an earlier version.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3ea0e-107">详细信息</span><span class="sxs-lookup"><span data-stu-id="3ea0e-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ea0e-108">适用于</span><span class="sxs-lookup"><span data-stu-id="3ea0e-108">Applies to</span></span>|<span data-ttu-id="3ea0e-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="3ea0e-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="3ea0e-110">产品版本</span><span class="sxs-lookup"><span data-stu-id="3ea0e-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="3ea0e-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea0e-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="3ea0e-112">原因</span><span class="sxs-lookup"><span data-stu-id="3ea0e-112">Cause</span></span>|<span data-ttu-id="3ea0e-113">数据连接失败。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-113">The data connection failed.</span></span>|  
|<span data-ttu-id="3ea0e-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="3ea0e-114">Message Text</span></span>|<span data-ttu-id="3ea0e-115">在尝试建立与外部数据源的连接的过程中出现错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-115">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="3ea0e-116">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="3ea0e-116">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3ea0e-117">说明</span><span class="sxs-lookup"><span data-stu-id="3ea0e-117">Explanation</span></span>  
 <span data-ttu-id="3ea0e-118">当您在发布到 SharePoint 的 Excel 工作簿中查询 PowerPivot 数据时，如果 SharePoint 环境不具有 PowerPivot for SharePoint 服务器，或者 SQL Server Analysis Services (PowerPivot) 服务停止运行，Excel Services 将返回此错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-118">Excel Services returns this error when you query PowerPivot data in an Excel workbook that is published to SharePoint, and the SharePoint environment does not have a PowerPivot for SharePoint server, or the SQL Server Analysis Services (PowerPivot) service is stopped.</span></span>  
  
 <span data-ttu-id="3ea0e-119">在您切分或筛选 PowerPivot 数据时，如果查询引擎不可用，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-119">The error occurs when you slice or filter PowerPivot data when the query engine is not available.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3ea0e-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="3ea0e-120">User Action</span></span>  
 <span data-ttu-id="3ea0e-121">安装 PowerPivot for SharePoint 或者将 PowerPivot 工作簿移到安装了 PowerPivot for SharePoint 的 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-121">Install PowerPivot for SharePoint or move the PowerPivot workbook to a SharePoint environment that has PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="3ea0e-122">有关详细信息，请参阅 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-122">For more information, see [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).</span></span>  
  
 <span data-ttu-id="3ea0e-123">如果安装了该软件，则请确认 SQL Server Analysis Services (PowerPivot) 实例正在运行。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-123">If the software is installed, verify that the SQL Server Analysis Services (PowerPivot) instance is running.</span></span> <span data-ttu-id="3ea0e-124">请在管理中心内检查 **“管理服务器上的服务”** 。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-124">Check **Manage services on server** in Central Administration.</span></span> <span data-ttu-id="3ea0e-125">还要在“管理工具”中检查“服务”控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-125">Also check the Services console application in Administrative Tools.</span></span>  
  
 <span data-ttu-id="3ea0e-126">对于在 SQL Server 2008 R2 版本的 PowerPivot for Excel 中创建的 PowerPivot 工作簿，必须安装 SQL Server 2008 R2 版本的 Analysis Services OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-126">For PowerPivot workbooks that were created in a SQL Server 2008 R2 version of PowerPivot for Excel, you must install the SQL Server 2008 R2 version of the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="3ea0e-127">如果您安装了该访问接口，但未注册 Microsoft.AnalysisServices.ChannelTransport.dll 文件，则将出现此错误。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-127">This error will occur if you installed the provider, but did not register the Microsoft.AnalysisServices.ChannelTransport.dll file.</span></span> <span data-ttu-id="3ea0e-128">有关文件注册的详细信息，请参阅 [在 SharePoint 服务器上安装 Analysis Services OLE DB 提供程序](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea0e-128">For more information about file registration, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea0e-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea0e-129">See Also</span></span>  
 [<span data-ttu-id="3ea0e-130">数据连接使用 Windows 身份验证，因此无法委托用户凭据。以下连接无法刷新： PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="3ea0e-130">The data connection uses Windows Authentication and user credentials could not be delegated. The following connections failed to refresh: PowerPivot Data</span></span>](the-data-connection-user-could-not-be-delegated.md)  
  
  
