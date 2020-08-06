---
title: 数据库属性（“更改跟踪”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4107f81ef4cdf19df60d4a70d8e79007f2c9270c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690642"
---
# <a name="database-properties-changetracking-page"></a><span data-ttu-id="21ec0-102">数据库属性（“更改跟踪”页）</span><span class="sxs-lookup"><span data-stu-id="21ec0-102">Database Properties (ChangeTracking Page)</span></span>
  <span data-ttu-id="21ec0-103">使用此页可查看或修改所选数据库的更改跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="21ec0-103">Use this page to view or modify change tracking settings for the selected database.</span></span> <span data-ttu-id="21ec0-104">有关在此页上可用选项的详细信息，请参阅[启用和禁用更改跟踪 (SQL Server)](../track-changes/enable-and-disable-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="21ec0-104">For more information about the options available on this page, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="21ec0-105">选项</span><span class="sxs-lookup"><span data-stu-id="21ec0-105">Options</span></span>  
 <span data-ttu-id="21ec0-106">**更改跟踪**</span><span class="sxs-lookup"><span data-stu-id="21ec0-106">**Change Tracking**</span></span>  
 <span data-ttu-id="21ec0-107">用于启用或禁用数据库的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="21ec0-107">Use to enable or disable change tracking for the database.</span></span>  
  
 <span data-ttu-id="21ec0-108">若要启用更改跟踪，您必须拥有修改数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="21ec0-108">To enable change tracking, you must have permission to modify the database.</span></span>  
  
 <span data-ttu-id="21ec0-109">将其值设置为 **True** 即可设置允许对各个表启用更改跟踪的数据库选项。</span><span class="sxs-lookup"><span data-stu-id="21ec0-109">Setting the value to **True** sets a database option that allows change tracking to be enabled on individual tables.</span></span>  
  
 <span data-ttu-id="21ec0-110">还可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)来配置更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="21ec0-110">You can also configure change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="21ec0-111">**保持期**</span><span class="sxs-lookup"><span data-stu-id="21ec0-111">**Retention Period**</span></span>  
 <span data-ttu-id="21ec0-112">指定在数据库中保留更改跟踪信息的最短期限。</span><span class="sxs-lookup"><span data-stu-id="21ec0-112">Specifies the minimum period for keeping change track information in the database.</span></span> <span data-ttu-id="21ec0-113">只有当“自动清除”\*\*\*\* 的值为 **True** 时，才会删除数据。</span><span class="sxs-lookup"><span data-stu-id="21ec0-113">Data is removed only if the **Auto Clean-Up**value is **True**.</span></span>  
  
 <span data-ttu-id="21ec0-114">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="21ec0-114">The default value is 2.</span></span>  
  
 <span data-ttu-id="21ec0-115">**保持期单位**</span><span class="sxs-lookup"><span data-stu-id="21ec0-115">**Retention Period Units**</span></span>  
 <span data-ttu-id="21ec0-116">指定“保持期”值的单位。</span><span class="sxs-lookup"><span data-stu-id="21ec0-116">Specifies the units for the Retention Period value.</span></span> <span data-ttu-id="21ec0-117">可以选择 **“天”** 、 **“小时”** 或 **“分钟”** 。</span><span class="sxs-lookup"><span data-stu-id="21ec0-117">You can select **Days**, **Hours**, or **Minutes**.</span></span> <span data-ttu-id="21ec0-118">默认值为 **“天”** 。</span><span class="sxs-lookup"><span data-stu-id="21ec0-118">The default value is **Days**.</span></span>  
  
 <span data-ttu-id="21ec0-119">最短保持期为 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="21ec0-119">The minimum retention period is 1 minute.</span></span> <span data-ttu-id="21ec0-120">不存在最长保持期。</span><span class="sxs-lookup"><span data-stu-id="21ec0-120">There is no maximum retention period.</span></span>  
  
 <span data-ttu-id="21ec0-121">**自动清除**</span><span class="sxs-lookup"><span data-stu-id="21ec0-121">**Auto Clean-Up**</span></span>  
 <span data-ttu-id="21ec0-122">指示是否在经过指定的保持期后自动删除更改跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="21ec0-122">Indicates whether change tracking information is automatically removed after the specified retention period.</span></span>  
  
 <span data-ttu-id="21ec0-123">启用“自动清除”会将任何先前自定义的保持期重置为默认保持期（即 2 天）。</span><span class="sxs-lookup"><span data-stu-id="21ec0-123">Enabling **Auto Clean-Up** resets any previous custom retention period to the default retention period of 2 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ec0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21ec0-124">See Also</span></span>  
 <span data-ttu-id="21ec0-125">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="21ec0-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="21ec0-126">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="21ec0-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
