---
title: 配置数据收集器的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05172c2c831ec649269512a625be069cdc67047a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690645"
---
# <a name="configure-properties-of-a-data-collector"></a><span data-ttu-id="10bb2-102">配置数据收集器的属性</span><span class="sxs-lookup"><span data-stu-id="10bb2-102">Configure Properties of a Data Collector</span></span>
  <span data-ttu-id="10bb2-103">本主题将介绍如何配置数据收集器的属性。</span><span class="sxs-lookup"><span data-stu-id="10bb2-103">This topic discusses how you can configure the properties of a data collector.</span></span>  
  
## <a name="data-collection-properties-general-tab"></a><span data-ttu-id="10bb2-104">数据收集属性（“常规”选项卡）</span><span class="sxs-lookup"><span data-stu-id="10bb2-104">Data Collection Properties (General Tab)</span></span>  
 <span data-ttu-id="10bb2-105">使用此页可以配置管理数据仓库的设置，并指定所收集数据在上载到数据仓库之前的存储位置。</span><span class="sxs-lookup"><span data-stu-id="10bb2-105">Use this page to configure settings for the management data warehouse and specify where collected data should be stored before it is uploaded to the data warehouse.</span></span>  
  
 <span data-ttu-id="10bb2-106">**启用数据收集**</span><span class="sxs-lookup"><span data-stu-id="10bb2-106">**Enable Data Collection**</span></span>  
 <span data-ttu-id="10bb2-107">选择此选项可以启用数据收集。</span><span class="sxs-lookup"><span data-stu-id="10bb2-107">Select to enable data collection.</span></span> <span data-ttu-id="10bb2-108">这与运行 sp_syscollector_enable_collector 存储过程的效果相同。</span><span class="sxs-lookup"><span data-stu-id="10bb2-108">This has the same effect as running the sp_syscollector_enable_collector stored procedure.</span></span> <span data-ttu-id="10bb2-109">清除此复选框可禁用数据收集且与运行 sp_syscollector_disable_collector 存储过程的效果相同。</span><span class="sxs-lookup"><span data-stu-id="10bb2-109">Clearing this check box disables data collection and has the same effect as running the sp_syscollector_disable_collector stored procedure.</span></span>  
  
 <span data-ttu-id="10bb2-110">**Server**</span><span class="sxs-lookup"><span data-stu-id="10bb2-110">**Server**</span></span>  
 <span data-ttu-id="10bb2-111">显示将承载管理数据仓库的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="10bb2-111">Displays the name of the server that will host the management data warehouse</span></span>  
  
 <span data-ttu-id="10bb2-112">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="10bb2-112">**Database name**</span></span>  
 <span data-ttu-id="10bb2-113">显示用于管理数据仓库的关系数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="10bb2-113">Displays the name of the relational database that is used for the management data warehouse.</span></span>  
  
 <span data-ttu-id="10bb2-114">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="10bb2-114">**Test Connection**</span></span>  
 <span data-ttu-id="10bb2-115">使用在配置数据收集时提供的信息测试到指定的 **服务器** 的连接。</span><span class="sxs-lookup"><span data-stu-id="10bb2-115">Test the connection to the specified **Server** using information provided when data collection is configured.</span></span>  
  
 <span data-ttu-id="10bb2-116">**缓存目录**</span><span class="sxs-lookup"><span data-stu-id="10bb2-116">**Cache directory**</span></span>  
 <span data-ttu-id="10bb2-117">指定所收集数据在上载到管理数据仓库之前在系统中的存储目录。</span><span class="sxs-lookup"><span data-stu-id="10bb2-117">Specifies the directory where collected data is stored on the system collecting the data before it is uploaded to the management data warehouse.</span></span> <span data-ttu-id="10bb2-118">如果未指定 **“缓存目录”** ，数据收集器会尝试查找 %TEMP% 和 %TMP% 环境变量并将两个位置中的一个位置用作临时存储的默认位置。</span><span class="sxs-lookup"><span data-stu-id="10bb2-118">If **Cache directory** is not specified, the data collector attempts to locate the %TEMP% and %TMP% environment variables and use one these locations as the default location for temporary storage.</span></span> <span data-ttu-id="10bb2-119">如果未配置这两个环境变量，则会出现错误并且系统将会提示创建一个缓存目录。</span><span class="sxs-lookup"><span data-stu-id="10bb2-119">If these environment variables are not configured, an error occurs and you are prompted to create a cache directory.</span></span>  
  
## <a name="data-collection-properties-advanced-tab"></a><span data-ttu-id="10bb2-120">数据收集属性（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="10bb2-120">Data Collection Properties (Advanced Tab)</span></span>  
 <span data-ttu-id="10bb2-121">使用此页可以为指向管理数据仓库的连接配置重试设置。</span><span class="sxs-lookup"><span data-stu-id="10bb2-121">Use this page to configure the retry settings for the connection to the management data warehouse.</span></span>  
  
 <span data-ttu-id="10bb2-122">**上载失败后的重试次数**</span><span class="sxs-lookup"><span data-stu-id="10bb2-122">**Number of times to retry if upload fails**</span></span>  
 <span data-ttu-id="10bb2-123">指定上载失败后重试上载到管理数据仓库的次数。</span><span class="sxs-lookup"><span data-stu-id="10bb2-123">Specifies the number of times to retry an upload to the management data warehouse if an upload fails.</span></span> <span data-ttu-id="10bb2-124">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="10bb2-124">The default is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10bb2-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10bb2-125">See Also</span></span>  
 <span data-ttu-id="10bb2-126">[管理数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="10bb2-126">[Manage Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="10bb2-127">配置管理数据仓库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="10bb2-127">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
