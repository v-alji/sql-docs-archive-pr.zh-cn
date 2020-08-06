---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687919"
---
# <a name="mssqlserver_2516"></a><span data-ttu-id="c6540-102">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="c6540-102">MSSQLSERVER_2516</span></span>
    
## <a name="details"></a><span data-ttu-id="c6540-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c6540-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6540-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c6540-104">Product Name</span></span>|<span data-ttu-id="c6540-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6540-105">SQL Server</span></span>|  
|<span data-ttu-id="c6540-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c6540-106">Event ID</span></span>|<span data-ttu-id="c6540-107">2516</span><span class="sxs-lookup"><span data-stu-id="c6540-107">2516</span></span>|  
|<span data-ttu-id="c6540-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c6540-108">Event Source</span></span>|<span data-ttu-id="c6540-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c6540-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c6540-110">组件</span><span class="sxs-lookup"><span data-stu-id="c6540-110">Component</span></span>|<span data-ttu-id="c6540-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c6540-111">SQLEngine</span></span>|  
|<span data-ttu-id="c6540-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="c6540-112">Symbolic Name</span></span>|<span data-ttu-id="c6540-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span><span class="sxs-lookup"><span data-stu-id="c6540-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span></span>|  
|<span data-ttu-id="c6540-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="c6540-114">Message Text</span></span>|<span data-ttu-id="c6540-115">修复操作已经使数据库 NAME 的差异位图无效。</span><span class="sxs-lookup"><span data-stu-id="c6540-115">Repair has invalidated the differential bitmap for database NAME.</span></span> <span data-ttu-id="c6540-116">差异备份链断开。</span><span class="sxs-lookup"><span data-stu-id="c6540-116">The differential backup chain is broken.</span></span> <span data-ttu-id="c6540-117">必须首先执行完全数据库备份，才能执行差异备份。</span><span class="sxs-lookup"><span data-stu-id="c6540-117">You must perform a full database backup before you can perform a differential backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6540-118">说明</span><span class="sxs-lookup"><span data-stu-id="c6540-118">Explanation</span></span>  
 <span data-ttu-id="c6540-119">在修复错误 MSSQLEngine_2515 时返回了此信息性消息。</span><span class="sxs-lookup"><span data-stu-id="c6540-119">This informational message is returned when error MSSQLEngine_2515 is repaired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6540-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="c6540-120">User Action</span></span>  
 <span data-ttu-id="c6540-121">执行一次完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="c6540-121">Perform a full database backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6540-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6540-122">See Also</span></span>  
 [<span data-ttu-id="c6540-123">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c6540-123">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
