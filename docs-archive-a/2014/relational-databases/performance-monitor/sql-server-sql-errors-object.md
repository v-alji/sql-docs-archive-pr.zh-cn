---
title: SQL Server - SQL Errors 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 11bfb728e79b4fc175fb8a2fe16c9f1662a205ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687799"
---
# <a name="sql-server-sql-errors-object"></a><span data-ttu-id="fa9f4-102">SQL Server SQL Errors 对象</span><span class="sxs-lookup"><span data-stu-id="fa9f4-102">SQL Server, SQL Errors Object</span></span>
  <span data-ttu-id="fa9f4-103">Microsoft **中的** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象提供了一些计数器，以监视 **SQL Errors**。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-103">The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor **SQL Errors**.</span></span>  
  
 <span data-ttu-id="fa9f4-104">下表介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 错误计数器。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-104">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** counters.</span></span>  
  
|<span data-ttu-id="fa9f4-105">SQL Server SQL Errors 计数器</span><span class="sxs-lookup"><span data-stu-id="fa9f4-105">SQL Server SQL Errors counters</span></span>|<span data-ttu-id="fa9f4-106">说明</span><span class="sxs-lookup"><span data-stu-id="fa9f4-106">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="fa9f4-107">**Errors/sec**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-107">**Errors/sec**</span></span>|<span data-ttu-id="fa9f4-108">每秒的错误数。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-108">Number of errors/sec.</span></span>|  
  
 <span data-ttu-id="fa9f4-109">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="fa9f4-109">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="fa9f4-110">Item</span><span class="sxs-lookup"><span data-stu-id="fa9f4-110">Item</span></span>|<span data-ttu-id="fa9f4-111">定义</span><span class="sxs-lookup"><span data-stu-id="fa9f4-111">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="fa9f4-112">**_Total**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-112">**_Total**</span></span>|<span data-ttu-id="fa9f4-113">有关所有错误的信息。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-113">Information for all errors.</span></span>|  
|<span data-ttu-id="fa9f4-114">**DB 离线错误**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-114">**DB Offline Errors**</span></span>|<span data-ttu-id="fa9f4-115">跟踪导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将当前数据库离线的错误。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-115">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to take the current database offline.</span></span>|  
|<span data-ttu-id="fa9f4-116">**信息错误**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-116">**Info Errors**</span></span>|<span data-ttu-id="fa9f4-117">与错误消息相关的信息，错误消息可向用户提供信息但不会导致错误。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-117">Information related to error messages that provide information to users but do not cause errors.</span></span>|  
|<span data-ttu-id="fa9f4-118">**断开连接错误**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-118">**Kill Connection Errors**</span></span>|<span data-ttu-id="fa9f4-119">跟踪导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 断开当前连接的错误。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-119">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to kill the current connection.</span></span>|  
|<span data-ttu-id="fa9f4-120">**用户错误**</span><span class="sxs-lookup"><span data-stu-id="fa9f4-120">**User Errors**</span></span>|<span data-ttu-id="fa9f4-121">有关用户错误的信息。</span><span class="sxs-lookup"><span data-stu-id="fa9f4-121">Information about user errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa9f4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa9f4-122">See Also</span></span>  
 [<span data-ttu-id="fa9f4-123">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="fa9f4-123">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
