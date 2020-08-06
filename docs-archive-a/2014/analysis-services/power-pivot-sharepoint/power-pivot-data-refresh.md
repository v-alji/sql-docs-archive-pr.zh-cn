---
title: PowerPivot 数据刷新 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587028"
---
# <a name="powerpivot-data-refresh"></a><span data-ttu-id="8ffd2-102">PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="8ffd2-102">PowerPivot Data Refresh</span></span>
  <span data-ttu-id="8ffd2-103">在您创建包含 PowerPivot 数据的某一工作簿后，最好通过重新运行查询或命令以便从您最初用于创建该工作簿的数据源获取更新的信息，定期刷新数据。</span><span class="sxs-lookup"><span data-stu-id="8ffd2-103">After you create a workbook that contains PowerPivot data, you might want to periodically refresh the data by rerunning a query or command to get updated information from the sources you used originally to create the workbook.</span></span> <span data-ttu-id="8ffd2-104">此过程称作 `data refresh`，并且您可以在 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 中按需刷新数据，或者作为在 SharePoint 场中的应用程序服务器上以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进程形式运行的定期操作来刷新数据。</span><span class="sxs-lookup"><span data-stu-id="8ffd2-104">This process is called `data refresh`, and you can refresh data on demand in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], or as a scheduled operation that runs as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process on an application server in a SharePoint farm.</span></span> <span data-ttu-id="8ffd2-105">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="8ffd2-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="8ffd2-106">使用 SharePoint 2010 进行 PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="8ffd2-106">PowerPivot Data Refresh with SharePoint 2010</span></span>](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [<span data-ttu-id="8ffd2-107">将 PowerPivot 无人参与的数据刷新帐户配置 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="8ffd2-107">Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="8ffd2-108">为 PowerPivot 数据刷新配置存储的凭据 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="8ffd2-108">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="8ffd2-109">计划数据刷新 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="8ffd2-109">Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="8ffd2-110">查看数据刷新历史记录 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="8ffd2-110">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="8ffd2-111">和 SharePoint Server 2013 Excel Services 使用不同的体系结构对 PowerPivot 数据模型进行数据刷新。</span><span class="sxs-lookup"><span data-stu-id="8ffd2-111">and SharePoint Server 2013 Excel Services use a different architecture for data refresh of PowerPivot data models.</span></span> <span data-ttu-id="8ffd2-112">SharePoint 2013 支持的体系结构利用 Excel Services 作为主要组件加载 PowerPivot 数据模型。</span><span class="sxs-lookup"><span data-stu-id="8ffd2-112">The SharePoint 2013 supported architecture utilizes Excel Services as the primary component to load PowerPivot data models.</span></span> <span data-ttu-id="8ffd2-113">以前的数据刷新体系结构依赖在 SharePoint 模式下运行 PowerPivot 系统服务和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的服务器来加载数据模型。</span><span class="sxs-lookup"><span data-stu-id="8ffd2-113">The previous data refresh architecture used relied on a server running PowerPivot System Service and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in SharePoint mode to load data models.</span></span> <span data-ttu-id="8ffd2-114">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="8ffd2-114">For more information, see the following:</span></span>  
> 
>  -   [<span data-ttu-id="8ffd2-115">使用 SharePoint 2013 进行 PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="8ffd2-115">PowerPivot Data Refresh with SharePoint 2013</span></span>](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [<span data-ttu-id="8ffd2-116">&#40;SharePoint 2013&#41;升级工作簿和计划的数据刷新</span><span class="sxs-lookup"><span data-stu-id="8ffd2-116">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
