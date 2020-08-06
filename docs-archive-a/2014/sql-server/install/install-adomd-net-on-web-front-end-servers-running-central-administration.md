---
title: 在运行管理中心的 Web 前端服务器上安装 ADOMD.NET |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f52bf612c4878a8dacd4f5acfdcc135ae115e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578026"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a><span data-ttu-id="b801e-102">在运行管理中心的 Web 前端服务器上安装 ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="b801e-102">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>
  <span data-ttu-id="b801e-103">如果您将 PowerPivot for SharePoint 安装到具有管理中心拓扑，但没有 Excel Services 或 PowerPivot for SharePoint 的场中，并且希望对 PowerPivot 管理面板中的内置报表具有完全访问权限，则需下载和安装 Microsoft ADOMD.NET 客户端库。</span><span class="sxs-lookup"><span data-stu-id="b801e-103">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="b801e-104">该面板中的某些报表将使用 ADOMD.NET 来访问内部数据，内部数据可提供有关 PowerPivot 查询处理和场中服务器运行状况的报告数据。</span><span class="sxs-lookup"><span data-stu-id="b801e-104">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span>  
  
 <span data-ttu-id="b801e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="b801e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="b801e-106">对于 SharePoint 2013，访问接口包含在 SQL Server 功能包中。</span><span class="sxs-lookup"><span data-stu-id="b801e-106">For SharePoint 2013, the provider is included in the SQL Server feature pack.</span></span> <span data-ttu-id="b801e-107">有关如何下载 spPowerPivot.msi 的信息，请参阅 [Microsoft SQL Server 2014 功能包](https://www.microsoft.com/download/details.aspx?id=35577)</span><span class="sxs-lookup"><span data-stu-id="b801e-107">For information on how to download spPowerPivot.msi, see [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)</span></span>  
  
### <a name="download-and-install-the-client-library"></a><span data-ttu-id="b801e-108">下载并安装客户端库</span><span class="sxs-lookup"><span data-stu-id="b801e-108">Download and install the client library</span></span>  
  
1.  <span data-ttu-id="b801e-109">在 [“SQL Server 2014 功能包”页](https://go.microsoft.com/fwlink/?LinkID=296473)上查找 Microsoft ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="b801e-109">On the [SQL Server 2014 Feature Pack page](https://go.microsoft.com/fwlink/?LinkID=296473), find Microsoft ADOMD.NET.</span></span>  
  
2.  <span data-ttu-id="b801e-110">下载 `SQL_AS_ADOMD.msi` 安装程序的 x64 包。</span><span class="sxs-lookup"><span data-stu-id="b801e-110">Download the x64 Package of the `SQL_AS_ADOMD.msi` installation program.</span></span>  
  
3.  <span data-ttu-id="b801e-111">运行 .msi 安装库。</span><span class="sxs-lookup"><span data-stu-id="b801e-111">Run the .msi to install the library.</span></span>  
  
4.  <span data-ttu-id="b801e-112">安装完成后，重置 IIS。</span><span class="sxs-lookup"><span data-stu-id="b801e-112">Reset IIS after installation is finished.</span></span> <span data-ttu-id="b801e-113">打开管理命令提示符，然后键入 **IISRESET**。</span><span class="sxs-lookup"><span data-stu-id="b801e-113">Open an administrative command prompt and type **IISRESET**.</span></span>  
  
### <a name="verify-installation"></a><span data-ttu-id="b801e-114">验证安装</span><span class="sxs-lookup"><span data-stu-id="b801e-114">Verify installation</span></span>  
  
1.  <span data-ttu-id="b801e-115">转到 Windows\Assembly。</span><span class="sxs-lookup"><span data-stu-id="b801e-115">Go to Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="b801e-116">右键单击 Microsoft.AnalysisServices.AdomdClient 并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="b801e-116">Right-click Microsoft.AnalysisServices.AdomdClient and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="b801e-117">单击 **“版本”**。</span><span class="sxs-lookup"><span data-stu-id="b801e-117">Click **Version**.</span></span>  
  
4.  <span data-ttu-id="b801e-118">验证版本是否包含12.00。\<build number></span><span class="sxs-lookup"><span data-stu-id="b801e-118">Verify that the version includes 12.00.\<build number></span></span> <span data-ttu-id="b801e-119">并且说明为是否为 microsoft.analysisservice.adomdclient. AdomdClient。</span><span class="sxs-lookup"><span data-stu-id="b801e-119">and that the description is Microsoft.AnalysisService.AdomdClient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b801e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b801e-120">See Also</span></span>  
 [<span data-ttu-id="b801e-121">PowerPivot 管理面板和使用情况数据</span><span class="sxs-lookup"><span data-stu-id="b801e-121">PowerPivot Management Dashboard and Usage Data</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
