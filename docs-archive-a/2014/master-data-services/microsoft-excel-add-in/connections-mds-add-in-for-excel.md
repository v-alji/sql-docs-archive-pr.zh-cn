---
title: 连接 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4dc41afc6dd59cade9e75475c7cb914d14a8937
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576868"
---
# <a name="connections-mds-add-in-for-excel"></a><span data-ttu-id="62ced-102">连接（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="62ced-102">Connections (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="62ced-103">若要将数据下载到 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，必须首先创建连接。</span><span class="sxs-lookup"><span data-stu-id="62ced-103">To download data in to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must first create a connection.</span></span> <span data-ttu-id="62ced-104">通过建立连接， [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服务才知道要连接到哪个 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="62ced-104">A connection is how the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service knows which MDS database to connect to.</span></span>  
  
 <span data-ttu-id="62ced-105">连接字符串通常是 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的 URL，例如 http://contoso/mds。</span><span class="sxs-lookup"><span data-stu-id="62ced-105">The connection string is usually the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
 <span data-ttu-id="62ced-106">每次启动 Excel 时，您必须连接到一个 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="62ced-106">Each time you start Excel, you must connect to an MDS repository.</span></span> <span data-ttu-id="62ced-107">只有在活动电子表格已包含 MDS 管理的数据的情况下才例外。</span><span class="sxs-lookup"><span data-stu-id="62ced-107">The only exception is when the active spreadsheet already contains MDS-managed data.</span></span> <span data-ttu-id="62ced-108">在这种情况下，每次刷新或发布工作表中的数据时会自动建立连接。</span><span class="sxs-lookup"><span data-stu-id="62ced-108">In this case, a connection is automatically made each time you refresh or publish data in the sheet.</span></span>  
  
 <span data-ttu-id="62ced-109">可以创建多个连接。</span><span class="sxs-lookup"><span data-stu-id="62ced-109">You can create multiple connections.</span></span> <span data-ttu-id="62ced-110">最近访问过的连接被视为默认连接。</span><span class="sxs-lookup"><span data-stu-id="62ced-110">The most recently-accessed connection is considered the default.</span></span>  
  
 <span data-ttu-id="62ced-111">可以同时连接多个用户。</span><span class="sxs-lookup"><span data-stu-id="62ced-111">Multiple users can be connected at the same time.</span></span> <span data-ttu-id="62ced-112">但是，当多个用户试图发布相同的数据时，可能会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="62ced-112">However, conflicts can arise when multiple users attempt to publish the same data.</span></span> <span data-ttu-id="62ced-113">有关详细信息，请参阅[发布数据 &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="62ced-113">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="62ced-114">自动连接和加载常用数据</span><span class="sxs-lookup"><span data-stu-id="62ced-114">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="62ced-115">如果总要连接同一服务器并加载相同的一组数据，您可以创建快捷查询文件，其中包含连接和筛选器信息。</span><span class="sxs-lookup"><span data-stu-id="62ced-115">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="62ced-116">有关查询文件的详细信息，请参阅 [快捷查询文件（用于 Excel 的 MDS 外接程序）](shortcut-query-files-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="62ced-116">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="data-quality-services"></a><span data-ttu-id="62ced-117">数据库引擎服务</span><span class="sxs-lookup"><span data-stu-id="62ced-117">Data Quality Services</span></span>  
 <span data-ttu-id="62ced-118">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 提供数据质量服务功能，可帮助您在将数据发布到 MDS 存储库之前先匹配数据。</span><span class="sxs-lookup"><span data-stu-id="62ced-118">The [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] has Data Quality Services functionality to help you match data before publishing it to the MDS repository.</span></span> <span data-ttu-id="62ced-119">建立连接时，如果 DQS 数据库与 MDS 数据库安装在同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上，您将能够在功能区上看到 DQS 按钮。</span><span class="sxs-lookup"><span data-stu-id="62ced-119">When you make a connection, if a DQS database is installed on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the MDS database, you will be able to view DQS buttons on the ribbon.</span></span> <span data-ttu-id="62ced-120">如果 DQS_Main 数据库没有位于该实例上，则这些按钮不显示，且数据质量功能不可用。</span><span class="sxs-lookup"><span data-stu-id="62ced-120">If the DQS_Main database does not exist on the instance, these buttons are not displayed and data quality functionality is not available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="62ced-121">排除连接故障</span><span class="sxs-lookup"><span data-stu-id="62ced-121">Troubleshooting Connections</span></span>  
 <span data-ttu-id="62ced-122">当你连接到 MDS 时，如果遇到任何问题，请参阅 [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) 故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="62ced-122">When you connect to MDS, if you encounter any issues see [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) for troubleshooting tips.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="62ced-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="62ced-123">Related Tasks</span></span>  
  
|<span data-ttu-id="62ced-124">任务说明</span><span class="sxs-lookup"><span data-stu-id="62ced-124">Task Description</span></span>|<span data-ttu-id="62ced-125">主题</span><span class="sxs-lookup"><span data-stu-id="62ced-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="62ced-126">创建与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="62ced-126">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="62ced-127">连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="62ced-127">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="62ced-128">将 MDS 数据加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="62ced-128">Load MDS data into Excel.</span></span>|[<span data-ttu-id="62ced-129">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="62ced-129">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="62ced-130">将 MDS 数据加载到 Excel 中之前先对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="62ced-130">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="62ced-131">在加载 &#40;MDS Add-in for Excel 前筛选数据&#41;</span><span class="sxs-lookup"><span data-stu-id="62ced-131">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="62ced-132">相关内容</span><span class="sxs-lookup"><span data-stu-id="62ced-132">Related Content</span></span>  
  
-   [<span data-ttu-id="62ced-133">MDS Add-in for Excel&#41;中加载数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="62ced-133">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="62ced-134">快捷查询文件（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="62ced-134">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="62ced-135">用于 Microsoft Excel 的 Master Data Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="62ced-135">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
