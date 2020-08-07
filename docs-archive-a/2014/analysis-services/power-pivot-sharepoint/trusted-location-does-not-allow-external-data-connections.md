---
title: 存储工作簿的受信任位置不允许外部数据连接。 以下连接无法刷新： PowerPivot 数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b7f6d335eac0bec0f67012cc413f3917c50348b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577000"
---
# <a name="the-trusted-location-where-the-workbook-is-stored-does-not-allow-external-data-connections-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="e9aa5-103">存储工作簿的受信任位置不允许外部数据连接。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-103">The trusted location where the workbook is stored does not allow external data connections.</span></span> <span data-ttu-id="e9aa5-104">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="e9aa5-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="e9aa5-105">对于包含 PowerPivot 数据的 Excel 工作簿，如果 Excel Services 无法连接到嵌入数据源，则会返回此错误。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to embedded data sources.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9aa5-106">详细信息</span><span class="sxs-lookup"><span data-stu-id="e9aa5-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9aa5-107">适用于</span><span class="sxs-lookup"><span data-stu-id="e9aa5-107">Applies to</span></span>|<span data-ttu-id="e9aa5-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="e9aa5-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="e9aa5-109">产品版本</span><span class="sxs-lookup"><span data-stu-id="e9aa5-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="e9aa5-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9aa5-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="e9aa5-111">原因</span><span class="sxs-lookup"><span data-stu-id="e9aa5-111">Cause</span></span>|<span data-ttu-id="e9aa5-112">Excel Services 配置为拒绝外部数据访问。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-112">Excel Services is configured to deny external data access.</span></span>|  
|<span data-ttu-id="e9aa5-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="e9aa5-113">Message Text</span></span>|<span data-ttu-id="e9aa5-114">存储工作簿的受信任位置不允许外部数据连接。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-114">The trusted location where the workbook is stored does not allow external data connections.</span></span> <span data-ttu-id="e9aa5-115">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="e9aa5-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e9aa5-116">说明</span><span class="sxs-lookup"><span data-stu-id="e9aa5-116">Explanation</span></span>  
 <span data-ttu-id="e9aa5-117">PowerPivot 工作簿包含嵌入数据连接。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-117">PowerPivot workbooks contain embedded data connections.</span></span> <span data-ttu-id="e9aa5-118">若要支持通过切片器和筛选器进行的工作簿交互，Excel Services 必须配置为允许通过嵌入连接信息的外部数据访问。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-118">To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information.</span></span> <span data-ttu-id="e9aa5-119">对于检索在场中 PowerPivot 服务器上加载的 PowerPivot 数据，外部数据访问是必需的。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-119">External data access is required for retrieving PowerPivot data that is loaded on PowerPivot servers in the farm.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e9aa5-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="e9aa5-120">User Action</span></span>  
 <span data-ttu-id="e9aa5-121">更改配置设置以便允许嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-121">Change the configuration settings to allow embedded data sources.</span></span>  
  
1.  <span data-ttu-id="e9aa5-122">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-122">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="e9aa5-123">单击 **“Excel Services 应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-123">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="e9aa5-124">单击 **“受信任文件位置”**。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-124">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="e9aa5-125">单击 **http://** 或者要配置的位置。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-125">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="e9aa5-126">在“外部数据”的“允许外部数据”中，单击 **“受信任的数据连接库和嵌入连接”**。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-126">In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.</span></span>  
  
6.  <span data-ttu-id="e9aa5-127">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-127">Click **OK**.</span></span>  
  
 <span data-ttu-id="e9aa5-128">此外，您还可以为包含 PowerPivot 工作簿的站点创建新的受信任位置，然后仅修改该站点的配置设置。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-128">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="e9aa5-129">有关详细信息，请参阅 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="e9aa5-129">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
