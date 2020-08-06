---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2328ee6366d47130a02c444bce65b7b655af7965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589589"
---
# <a name="mssqlserver_3619"></a><span data-ttu-id="d2146-102">MSSQLSERVER_3619</span><span class="sxs-lookup"><span data-stu-id="d2146-102">MSSQLSERVER_3619</span></span>
    
## <a name="details"></a><span data-ttu-id="d2146-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d2146-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2146-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d2146-104">Product Name</span></span>|<span data-ttu-id="d2146-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2146-105">SQL Server</span></span>|  
|<span data-ttu-id="d2146-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d2146-106">Event ID</span></span>|<span data-ttu-id="d2146-107">3619</span><span class="sxs-lookup"><span data-stu-id="d2146-107">3619</span></span>|  
|<span data-ttu-id="d2146-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d2146-108">Event Source</span></span>|<span data-ttu-id="d2146-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d2146-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d2146-110">组件</span><span class="sxs-lookup"><span data-stu-id="d2146-110">Component</span></span>|<span data-ttu-id="d2146-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d2146-111">SQLEngine</span></span>|  
|<span data-ttu-id="d2146-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d2146-112">Symbolic Name</span></span>|<span data-ttu-id="d2146-113">SYS_NOLOG</span><span class="sxs-lookup"><span data-stu-id="d2146-113">SYS_NOLOG</span></span>|  
|<span data-ttu-id="d2146-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d2146-114">Message Text</span></span>|<span data-ttu-id="d2146-115">由于日志空间用尽，无法在数据库 ID %d 中写入检查点记录。</span><span class="sxs-lookup"><span data-stu-id="d2146-115">Could not write a checkpoint record in database ID %d because the log is out of space.</span></span> <span data-ttu-id="d2146-116">请与数据库管理员联系，截断日志或为数据库日志文件分配更多空间。</span><span class="sxs-lookup"><span data-stu-id="d2146-116">Contact the database administrator to truncate the log or allocate more space to the database log files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d2146-117">说明</span><span class="sxs-lookup"><span data-stu-id="d2146-117">Explanation</span></span>  
 <span data-ttu-id="d2146-118">事务日志的磁盘空间不足。</span><span class="sxs-lookup"><span data-stu-id="d2146-118">The transaction log is out of disk space.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d2146-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="d2146-119">User Action</span></span>  
 <span data-ttu-id="d2146-120">截断日志以释放一些空间，或者为日志分配更多的空间。</span><span class="sxs-lookup"><span data-stu-id="d2146-120">Truncate the log to release some space, or allocate more space to the log.</span></span> <span data-ttu-id="d2146-121">有关详细信息，请参阅 Server SQL 联机丛书中的“解决事务日志已满的问题（错误 9002）”。</span><span class="sxs-lookup"><span data-stu-id="d2146-121">For more information see, "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
  
