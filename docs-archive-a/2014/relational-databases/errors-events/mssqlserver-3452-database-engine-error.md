---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 662d342064e8094400a6b672e21704877b4d0448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576794"
---
# <a name="mssqlserver_3452"></a><span data-ttu-id="5d4eb-102">MSSQLSERVER_3452</span><span class="sxs-lookup"><span data-stu-id="5d4eb-102">MSSQLSERVER_3452</span></span>
    
## <a name="details"></a><span data-ttu-id="5d4eb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5d4eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d4eb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5d4eb-104">Product Name</span></span>|<span data-ttu-id="5d4eb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d4eb-105">SQL Server</span></span>|  
|<span data-ttu-id="5d4eb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5d4eb-106">Event ID</span></span>|<span data-ttu-id="5d4eb-107">3452</span><span class="sxs-lookup"><span data-stu-id="5d4eb-107">3452</span></span>|  
|<span data-ttu-id="5d4eb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5d4eb-108">Event Source</span></span>|<span data-ttu-id="5d4eb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5d4eb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5d4eb-110">组件</span><span class="sxs-lookup"><span data-stu-id="5d4eb-110">Component</span></span>|<span data-ttu-id="5d4eb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5d4eb-111">SQLEngine</span></span>|  
|<span data-ttu-id="5d4eb-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5d4eb-112">Symbolic Name</span></span>|<span data-ttu-id="5d4eb-113">REC_CHECKIDENTITY</span><span class="sxs-lookup"><span data-stu-id="5d4eb-113">REC_CHECKIDENTITY</span></span>|  
|<span data-ttu-id="5d4eb-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5d4eb-114">Message Text</span></span>|<span data-ttu-id="5d4eb-115">数据库 '%.\*ls' (%d)的恢复操作检测到表 ID %d 中的标识值可能不一致。</span><span class="sxs-lookup"><span data-stu-id="5d4eb-115">Recovery of database '%.\*ls' (%d) detected possible identity value inconsistency in table ID %d.</span></span> <span data-ttu-id="5d4eb-116">请运行 DBCC CHECKIDENT ('%.\*ls')。</span><span class="sxs-lookup"><span data-stu-id="5d4eb-116">Run DBCC CHECKIDENT ('%.\*ls').</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5d4eb-117">说明</span><span class="sxs-lookup"><span data-stu-id="5d4eb-117">Explanation</span></span>  
 <span data-ttu-id="5d4eb-118">在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 期间，用于恢复数据库中标识值的进程发现元数据中存在不一致的地方。</span><span class="sxs-lookup"><span data-stu-id="5d4eb-118">During the upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the process to recover the identity values in the database found an inconsistency in the metadata.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5d4eb-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="5d4eb-119">User Action</span></span>  
 <span data-ttu-id="5d4eb-120">运行 DBCC CHECKIDENT。</span><span class="sxs-lookup"><span data-stu-id="5d4eb-120">Run DBCC CHECKIDENT.</span></span>  
  
  
