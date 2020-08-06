---
title: 将 MSOLAP 5 添加为 Excel Services 中的受信任数据访问接口 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 876ec613f18b2d91b5e06ab5fed4a7b258c30a36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589915"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a><span data-ttu-id="5f552-102">将 MSOLAP.5 添加为 Excel Services 中的受信任数据访问接口</span><span class="sxs-lookup"><span data-stu-id="5f552-102">Add MSOLAP.5 as a Trusted Data Provider in Excel Services</span></span>
  <span data-ttu-id="5f552-103">MSOLAP.5 指代用于 SQL Server 2012 的 Analysis Services OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="5f552-103">MSOLAP.5 refers to the Analysis Services OLE DB provider for SQL Server 2012.</span></span> <span data-ttu-id="5f552-104">Excel Services 必须信任此访问接口，然后才能发出连接请求，请求在服务器上提供 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="5f552-104">Excel Services must trust this provider before it will make the connection request that results in the availability of PowerPivot data on a server.</span></span>  
  
 <span data-ttu-id="5f552-105">如果使用 PowerPivot 配置工具配置了 PowerPivot for SharePoint，MSOLAP.5 可能已是受信任的访问接口，因为该工具包含一项可满足此要求的操作。</span><span class="sxs-lookup"><span data-stu-id="5f552-105">If you configured PowerPivot for SharePoint using the PowerPivot Configuration Tool, MSOLAP.5 might already be a trusted provider because the tool includes an action that satisfies this requirement.</span></span> <span data-ttu-id="5f552-106">但是，如果使用的是 PowerShell、管理中心，或在配置工具中排除了受信任的访问接口操作，该访问接口可能缺失，在这种情况下，您应该在配置用于 PowerPivot 数据访问的场的过程中立即添加该访问接口。</span><span class="sxs-lookup"><span data-stu-id="5f552-106">However, if you are using PowerShell, Central Administration, or if you excluded the trusted provider action in the configuration tool, the provider might be missing, which case you should add it now as part of configuring the farm for PowerPivot data access.</span></span>  
  
 <span data-ttu-id="5f552-107">对于每个 Excel Services 服务应用程序只需执行此步骤一次。</span><span class="sxs-lookup"><span data-stu-id="5f552-107">You only need to perform this step once for each Excel Services service application.</span></span>  
  
 <span data-ttu-id="5f552-108">处理 PowerPivot 数据请求的每个物理服务器（如 PowerPivot for SharePoint 服务器或 Excel Services 服务器）必须在计算机上安装了 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="5f552-108">Each physical server that handles a PowerPivot data request, such as a PowerPivot for SharePoint server or an Excel Services server, must have the OLE DB provider installed on the computer.</span></span> <span data-ttu-id="5f552-109">PowerPivot for SharePoint 安装始终包含 OLE DB 访问接口，但是如果 Excel Services 运行在未安装 PowerPivot for SharePoint 的计算机上，必须手动安装该访问接口。</span><span class="sxs-lookup"><span data-stu-id="5f552-109">A PowerPivot for SharePoint installation always includes the OLE DB provider, but if Excel Services is running on a computer that does not have PowerPivot for SharePoint, you must install the provider manually.</span></span> <span data-ttu-id="5f552-110">有关详细信息，请参阅 [在 SharePoint 服务器上安装 Analysis Services OLE DB 提供程序](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="5f552-110">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="add-a-trusted-provider-to-excel-services"></a><span data-ttu-id="5f552-111">将受信任的访问接口添加到 Excel Services</span><span class="sxs-lookup"><span data-stu-id="5f552-111">Add a trusted provider to Excel Services</span></span>  
  
1.  <span data-ttu-id="5f552-112">在“管理中心”中，单击 **“管理服务应用程序”**，然后单击 Excel Services 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="5f552-112">In Central Administration, click **Manage service applications**, and then click the Excel Services service application.</span></span>  
  
2.  <span data-ttu-id="5f552-113">单击 **“受信任的数据访问接口”** 。</span><span class="sxs-lookup"><span data-stu-id="5f552-113">Click **Trusted Data Providers**.</span></span>  
  
3.  <span data-ttu-id="5f552-114">验证 MSOLAP.5 显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="5f552-114">Verify that MSOLAP.5 appears in the list.</span></span> <span data-ttu-id="5f552-115">根据您配置 PowerPivot for SharePoint 的不同方式，MSOLAP.5 可能已受信任。</span><span class="sxs-lookup"><span data-stu-id="5f552-115">Depending on how you configured PowerPivot for SharePoint, MSOLAP.5 might already be trusted.</span></span>  
  
4.  <span data-ttu-id="5f552-116">如果它未列出，请单击 **“添加受信任的数据访问接口”**。</span><span class="sxs-lookup"><span data-stu-id="5f552-116">If it is not listed, click **Add Trusted Data Provider**.</span></span>  
  
5.  <span data-ttu-id="5f552-117">在“访问接口 ID”中，键入 `MSOLAP.5`。</span><span class="sxs-lookup"><span data-stu-id="5f552-117">In Provider ID, type `MSOLAP.5`.</span></span>  
  
6.  <span data-ttu-id="5f552-118">对于“访问接口类型”，请确保选择 OLE DB。</span><span class="sxs-lookup"><span data-stu-id="5f552-118">For Provider Type, ensure that OLE DB is selected.</span></span>  
  
7.  <span data-ttu-id="5f552-119">在“访问接口说明”中，键入 **Microsoft OLE DB Provider for OLAP Services 11.0**。</span><span class="sxs-lookup"><span data-stu-id="5f552-119">In Provider Description, type **Microsoft OLE DB Provider for OLAP Services 11.0**.</span></span>  
  
  
