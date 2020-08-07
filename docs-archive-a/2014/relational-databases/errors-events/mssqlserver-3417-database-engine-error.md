---
title: MSSQLSERVER_3417 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 680e5a4266c7d0d9aaacb7b3deb9525a002077e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589597"
---
# <a name="mssqlserver_3417"></a><span data-ttu-id="866e0-102">MSSQLSERVER_3417</span><span class="sxs-lookup"><span data-stu-id="866e0-102">MSSQLSERVER_3417</span></span>
    
## <a name="details"></a><span data-ttu-id="866e0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="866e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="866e0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="866e0-104">Product Name</span></span>|<span data-ttu-id="866e0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="866e0-105">SQL Server</span></span>|  
|<span data-ttu-id="866e0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="866e0-106">Event ID</span></span>|<span data-ttu-id="866e0-107">3417</span><span class="sxs-lookup"><span data-stu-id="866e0-107">3417</span></span>|  
|<span data-ttu-id="866e0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="866e0-108">Event Source</span></span>|<span data-ttu-id="866e0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="866e0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="866e0-110">组件</span><span class="sxs-lookup"><span data-stu-id="866e0-110">Component</span></span>|<span data-ttu-id="866e0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="866e0-111">SQLEngine</span></span>|  
|<span data-ttu-id="866e0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="866e0-112">Symbolic Name</span></span>|<span data-ttu-id="866e0-113">REC_BADMASTER</span><span class="sxs-lookup"><span data-stu-id="866e0-113">REC_BADMASTER</span></span>|  
|<span data-ttu-id="866e0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="866e0-114">Message Text</span></span>|<span data-ttu-id="866e0-115">无法恢复 master 数据库。</span><span class="sxs-lookup"><span data-stu-id="866e0-115">Cannot recover the master database.</span></span> <span data-ttu-id="866e0-116">SQL Server 无法运行。</span><span class="sxs-lookup"><span data-stu-id="866e0-116">SQL Server is unable to run.</span></span> <span data-ttu-id="866e0-117">请利用完整备份还原 master 数据库，修复它，或者重新生成它。</span><span class="sxs-lookup"><span data-stu-id="866e0-117">Restore master from a full backup, repair it, or rebuild it.</span></span> <span data-ttu-id="866e0-118">有关如何重新生成 master 数据库的详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="866e0-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="866e0-119">说明</span><span class="sxs-lookup"><span data-stu-id="866e0-119">Explanation</span></span>  
 <span data-ttu-id="866e0-120">SQL Server 无法启动 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="866e0-120">SQL Server cannot start the **master** database.</span></span> <span data-ttu-id="866e0-121">如果无法使 **master** 或 **tempdb** 联机，则 SQL Server 无法运行。</span><span class="sxs-lookup"><span data-stu-id="866e0-121">If the **master** or **tempdb** cannot be brought online, SQL Server cannot run.</span></span> <span data-ttu-id="866e0-122">其他错误通常在此错误之前出现。</span><span class="sxs-lookup"><span data-stu-id="866e0-122">This error is usually preceded by other errors.</span></span> <span data-ttu-id="866e0-123">检查错误日志以查找根本原因。</span><span class="sxs-lookup"><span data-stu-id="866e0-123">Review error logs to find the root cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="866e0-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="866e0-124">User Action</span></span>  
 <span data-ttu-id="866e0-125">还原数据库备份或修复数据库。</span><span class="sxs-lookup"><span data-stu-id="866e0-125">Restore backup of the database or repair the database.</span></span>  
  
  
