---
title: 此工作簿包含一个或多个用于刷新外部数据的查询。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b2095e13d6151c68eb4a3507400dfdb1739564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586009"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a><span data-ttu-id="184dc-103">此工作簿包含一个或多个用于刷新外部数据的查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-103">This workbook contains one or more queries that refresh external data.</span></span>
  <span data-ttu-id="184dc-104">对于包含 PowerPivot 数据的 Excel 工作簿，如果 Excel Services 检测到连接信息，则将显示此警告，并提示您为此工作簿启用或禁用查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-104">For Excel workbooks that contain PowerPivot data, Excel Services shows this warning when it detects connection information and prompts you to enable or disable queries for this workbook.</span></span>  
  
## <a name="details"></a><span data-ttu-id="184dc-105">详细信息</span><span class="sxs-lookup"><span data-stu-id="184dc-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="184dc-106">产品名称</span><span class="sxs-lookup"><span data-stu-id="184dc-106">Product Name</span></span>|<span data-ttu-id="184dc-107">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="184dc-107">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="184dc-108">产品版本</span><span class="sxs-lookup"><span data-stu-id="184dc-108">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="184dc-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184dc-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="184dc-110">原因</span><span class="sxs-lookup"><span data-stu-id="184dc-110">Cause</span></span>|<span data-ttu-id="184dc-111">Excel Services 配置为对数据刷新显示警告。</span><span class="sxs-lookup"><span data-stu-id="184dc-111">Excel Services is configured to warn on data refresh.</span></span>|  
|<span data-ttu-id="184dc-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="184dc-112">Message Text</span></span>|<span data-ttu-id="184dc-113">此工作簿包含一个或多个用于刷新外部数据的查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-113">This workbook contains one or more queries that refresh external data.</span></span> <span data-ttu-id="184dc-114">恶意用户可能设计一个查询来访问机密信息，并将其分发给其他用户或执行其他有害操作。</span><span class="sxs-lookup"><span data-stu-id="184dc-114">A malicious user can design a query to access confidential information and distribute it to other users or perform other harmful actions.</span></span><br /><br /> <span data-ttu-id="184dc-115">如果您信任此工作簿的源，则单击“是”以启用对此工作簿中外部数据的查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-115">If you trust the source of this workbook, click Yes to enable queries to external data in this workbook.</span></span> <span data-ttu-id="184dc-116">如果您不确定，则单击“否”，以便不将更改应用到您的工作簿。</span><span class="sxs-lookup"><span data-stu-id="184dc-116">If you are not sure, click No so that changes are not applied to your workbook.</span></span><br /><br /> <span data-ttu-id="184dc-117">是否要启用对此工作簿中外部数据的查询？</span><span class="sxs-lookup"><span data-stu-id="184dc-117">Do you want to enable queries to external data in this workbook?</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="184dc-118">说明</span><span class="sxs-lookup"><span data-stu-id="184dc-118">Explanation</span></span>  
 <span data-ttu-id="184dc-119">PowerPivot 工作簿包含由 Excel 使用的嵌入数据连接字符串，以便与加载和计算数据的外部 PowerPivot 服务器进行通信。</span><span class="sxs-lookup"><span data-stu-id="184dc-119">PowerPivot workbooks contain embedded data connection strings that are used by Excel to communicate with an external PowerPivot server that loads and calculates the data.</span></span> <span data-ttu-id="184dc-120">当启用数据刷新警告时，Excel Services 检测此连接字符串，并相应向用户发出警告。</span><span class="sxs-lookup"><span data-stu-id="184dc-120">When warn on data refresh is enabled, Excel Services detects this connection string and warns the user accordingly.</span></span>  
  
 <span data-ttu-id="184dc-121">若要筛选工作簿中的 PowerPivot 数据并对其执行切片，必须启用查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-121">To filter and slice PowerPivot data in the workbook, queries must be enabled.</span></span> <span data-ttu-id="184dc-122">确保您只对您信任的这些 PowerPivot 工作簿启用查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-122">Be sure that you enable queries for only those PowerPivot workbooks that you trust.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="184dc-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="184dc-123">User Action</span></span>  
 <span data-ttu-id="184dc-124">单击 **“是”** 以启用查询。</span><span class="sxs-lookup"><span data-stu-id="184dc-124">Click **Yes** to enable queries.</span></span>  
  
 <span data-ttu-id="184dc-125">还可以更改配置设置，以便不再发生刷新时警告：</span><span class="sxs-lookup"><span data-stu-id="184dc-125">You can also change the configuration settings so that warn on refresh no longer occurs:</span></span>  
  
1.  <span data-ttu-id="184dc-126">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="184dc-126">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="184dc-127">单击 **“Excel Services 应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="184dc-127">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="184dc-128">单击 **“受信任文件位置”**。</span><span class="sxs-lookup"><span data-stu-id="184dc-128">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="184dc-129">单击 **http://** 或者要配置的位置。</span><span class="sxs-lookup"><span data-stu-id="184dc-129">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="184dc-130">在“外部数据”中，取消选中 **“数据刷新时警告”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="184dc-130">In External Data, clear the checkbox for **Warn on data refresh**.</span></span>  
  
6.  <span data-ttu-id="184dc-131">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="184dc-131">Click **OK**.</span></span>  
  
 <span data-ttu-id="184dc-132">此外，您还可以为包含 PowerPivot 工作簿的站点创建新的受信任位置，然后仅修改该站点的配置设置。</span><span class="sxs-lookup"><span data-stu-id="184dc-132">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="184dc-133">有关详细信息，请参阅 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="184dc-133">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
