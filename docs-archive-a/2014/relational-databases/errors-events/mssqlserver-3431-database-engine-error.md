---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589595"
---
# <a name="mssqlserver_3431"></a><span data-ttu-id="486fc-102">MSSQLSERVER_3431</span><span class="sxs-lookup"><span data-stu-id="486fc-102">MSSQLSERVER_3431</span></span>
    
## <a name="details"></a><span data-ttu-id="486fc-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="486fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="486fc-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="486fc-104">Product Name</span></span>|<span data-ttu-id="486fc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="486fc-105">SQL Server</span></span>|  
|<span data-ttu-id="486fc-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="486fc-106">Event ID</span></span>|<span data-ttu-id="486fc-107">3431</span><span class="sxs-lookup"><span data-stu-id="486fc-107">3431</span></span>|  
|<span data-ttu-id="486fc-108">事件源</span><span class="sxs-lookup"><span data-stu-id="486fc-108">Event Source</span></span>|<span data-ttu-id="486fc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="486fc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="486fc-110">组件</span><span class="sxs-lookup"><span data-stu-id="486fc-110">Component</span></span>|<span data-ttu-id="486fc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="486fc-111">SQLEngine</span></span>|  
|<span data-ttu-id="486fc-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="486fc-112">Symbolic Name</span></span>|<span data-ttu-id="486fc-113">UNRESOLVED_XACT</span><span class="sxs-lookup"><span data-stu-id="486fc-113">UNRESOLVED_XACT</span></span>|  
|<span data-ttu-id="486fc-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="486fc-114">Message Text</span></span>|<span data-ttu-id="486fc-115">无法恢复数据库 '%.\*ls' (数据库 ID 为 %d)，因为事务结果尚未解析。</span><span class="sxs-lookup"><span data-stu-id="486fc-115">Could not recover database '%.\*ls' (database ID %d) because of unresolved transaction outcomes.</span></span> <span data-ttu-id="486fc-116">Microsoft 分布式事务处理协调器 (MS DTC) 事务已准备好，但 MS DTC 无法确定解析方法。</span><span class="sxs-lookup"><span data-stu-id="486fc-116">Microsoft Distributed Transaction Coordinator (MS DTC) transactions were prepared, but MS DTC was unable to determine the resolution.</span></span> <span data-ttu-id="486fc-117">若要进行解析，请修复 MS DTC，从完整备份进行还原，或者修复数据库。</span><span class="sxs-lookup"><span data-stu-id="486fc-117">To resolve, either fix MS DTC, restore from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="486fc-118">说明</span><span class="sxs-lookup"><span data-stu-id="486fc-118">Explanation</span></span>  
 <span data-ttu-id="486fc-119">在数据库关闭时，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 的一项或多项分布式事务尚未完成。</span><span class="sxs-lookup"><span data-stu-id="486fc-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="486fc-120">此数据库的恢复失败，因为没有来自 MS DTC 的详细信息，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法完成事务或回退事务。</span><span class="sxs-lookup"><span data-stu-id="486fc-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot complete the transactions or roll back the transactions without more information from MS DTC.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="486fc-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="486fc-121">User Action</span></span>  
 <span data-ttu-id="486fc-122">若要恢复该数据库，必须首先解决 MS DTC 存在的问题。</span><span class="sxs-lookup"><span data-stu-id="486fc-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="486fc-123">若要调查 MS DTC 存在的问题，请检查 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="486fc-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="486fc-124">如果无法解决 MS DTC 问题和恢复数据库，请还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="486fc-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
