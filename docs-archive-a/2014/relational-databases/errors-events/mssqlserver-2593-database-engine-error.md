---
title: MSSQLSERVER_2593 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecd231f38fbb36e2f98a1e9ce254165002bb56e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687908"
---
# <a name="mssqlserver_2593"></a><span data-ttu-id="73554-102">MSSQLSERVER_2593</span><span class="sxs-lookup"><span data-stu-id="73554-102">MSSQLSERVER_2593</span></span>
    
## <a name="details"></a><span data-ttu-id="73554-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="73554-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73554-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="73554-104">Product Name</span></span>|<span data-ttu-id="73554-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="73554-105">SQL Server</span></span>|  
|<span data-ttu-id="73554-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="73554-106">Event ID</span></span>|<span data-ttu-id="73554-107">2593</span><span class="sxs-lookup"><span data-stu-id="73554-107">2593</span></span>|  
|<span data-ttu-id="73554-108">事件源</span><span class="sxs-lookup"><span data-stu-id="73554-108">Event Source</span></span>|<span data-ttu-id="73554-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="73554-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="73554-110">组件</span><span class="sxs-lookup"><span data-stu-id="73554-110">Component</span></span>|<span data-ttu-id="73554-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="73554-111">SQLEngine</span></span>|  
|<span data-ttu-id="73554-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="73554-112">Symbolic Name</span></span>|<span data-ttu-id="73554-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span><span class="sxs-lookup"><span data-stu-id="73554-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span></span>|  
|<span data-ttu-id="73554-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="73554-114">Message Text</span></span>|<span data-ttu-id="73554-115">对象 'object' 的 PAGECOUNT 页中有 ROWCOUNT 行。</span><span class="sxs-lookup"><span data-stu-id="73554-115">There are ROWCOUNT rows in PAGECOUNT pages for object 'OBJECT'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="73554-116">说明</span><span class="sxs-lookup"><span data-stu-id="73554-116">Explanation</span></span>  
 <span data-ttu-id="73554-117">此消息是所有 DBCC 检查（DBCC CHECKALLOC 除外）返回的信息性输出的一部分，指示指定对象的行和页计数。</span><span class="sxs-lookup"><span data-stu-id="73554-117">This message is part of the informational output that is returned by all DBCC checks, except DBCC CHECKALLOC, and indicates the row and page counts for a specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73554-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="73554-118">User Action</span></span>  
 <span data-ttu-id="73554-119">无</span><span class="sxs-lookup"><span data-stu-id="73554-119">None</span></span>  
  
  
