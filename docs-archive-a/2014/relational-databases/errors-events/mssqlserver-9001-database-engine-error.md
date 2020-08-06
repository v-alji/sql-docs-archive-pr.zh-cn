---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691212"
---
# <a name="mssqlserver_9001"></a><span data-ttu-id="e0f42-102">MSSQLSERVER_9001</span><span class="sxs-lookup"><span data-stu-id="e0f42-102">MSSQLSERVER_9001</span></span>
    
## <a name="details"></a><span data-ttu-id="e0f42-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e0f42-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0f42-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e0f42-104">Product Name</span></span>|<span data-ttu-id="e0f42-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e0f42-105">SQL Server</span></span>|  
|<span data-ttu-id="e0f42-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e0f42-106">Event ID</span></span>|<span data-ttu-id="e0f42-107">9001</span><span class="sxs-lookup"><span data-stu-id="e0f42-107">9001</span></span>|  
|<span data-ttu-id="e0f42-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e0f42-108">Event Source</span></span>|<span data-ttu-id="e0f42-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e0f42-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e0f42-110">组件</span><span class="sxs-lookup"><span data-stu-id="e0f42-110">Component</span></span>|<span data-ttu-id="e0f42-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e0f42-111">SQLEngine</span></span>|  
|<span data-ttu-id="e0f42-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e0f42-112">Symbolic Name</span></span>|<span data-ttu-id="e0f42-113">LOG_NOT_AVAIL</span><span class="sxs-lookup"><span data-stu-id="e0f42-113">LOG_NOT_AVAIL</span></span>|  
|<span data-ttu-id="e0f42-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e0f42-114">Message Text</span></span>|<span data-ttu-id="e0f42-115">数据库 '%.\*ls' 的日志不可用。</span><span class="sxs-lookup"><span data-stu-id="e0f42-115">The log for database '%.\*ls' is not available.</span></span> <span data-ttu-id="e0f42-116">有关相应错误消息，请查看事件日志。</span><span class="sxs-lookup"><span data-stu-id="e0f42-116">Check the event log for related error messages.</span></span> <span data-ttu-id="e0f42-117">修复所有错误后重新启动数据库。</span><span class="sxs-lookup"><span data-stu-id="e0f42-117">Resolve any errors and restart the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e0f42-118">说明</span><span class="sxs-lookup"><span data-stu-id="e0f42-118">Explanation</span></span>  
 <span data-ttu-id="e0f42-119">数据库日志处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="e0f42-119">The database log was taken offline.</span></span> <span data-ttu-id="e0f42-120">通常，这表示需要重新启动数据库的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="e0f42-120">Usually this signifies a catastrophic failure that requires the database to restart.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e0f42-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="e0f42-121">User Action</span></span>  
 <span data-ttu-id="e0f42-122">诊断其他错误并重新启动 SQL Server 实例（如果尚未自行重新启动）。</span><span class="sxs-lookup"><span data-stu-id="e0f42-122">Diagnose other errors and restart the instance of SQL Server if it has not already restarted itself.</span></span>  
  
  
