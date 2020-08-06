---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88e9feb7c3ac5d8cf646d2243319b2b160b7757e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690613"
---
# <a name="mssqlserver_617"></a><span data-ttu-id="a4fbe-102">MSSQLSERVER_617</span><span class="sxs-lookup"><span data-stu-id="a4fbe-102">MSSQLSERVER_617</span></span>
    
## <a name="details"></a><span data-ttu-id="a4fbe-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a4fbe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4fbe-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a4fbe-104">Product Name</span></span>|<span data-ttu-id="a4fbe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4fbe-105">SQL Server</span></span>|  
|<span data-ttu-id="a4fbe-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a4fbe-106">Event ID</span></span>|<span data-ttu-id="a4fbe-107">617</span><span class="sxs-lookup"><span data-stu-id="a4fbe-107">617</span></span>|  
|<span data-ttu-id="a4fbe-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a4fbe-108">Event Source</span></span>|<span data-ttu-id="a4fbe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a4fbe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a4fbe-110">组件</span><span class="sxs-lookup"><span data-stu-id="a4fbe-110">Component</span></span>|<span data-ttu-id="a4fbe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a4fbe-111">SQLEngine</span></span>|  
|<span data-ttu-id="a4fbe-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a4fbe-112">Symbolic Name</span></span>|<span data-ttu-id="a4fbe-113">NODESHASH</span><span class="sxs-lookup"><span data-stu-id="a4fbe-113">NODESHASH</span></span>|  
|<span data-ttu-id="a4fbe-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a4fbe-114">Message Text</span></span>|<span data-ttu-id="a4fbe-115">尝试对数据库 ID %d 中的对象 ID %ld 的描述符进行解哈希运算时，在哈希表中没有找到该描述符。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-115">Descriptor for object ID %ld in database ID %d not found in the hash table during attempt to unhash it.</span></span> <span data-ttu-id="a4fbe-116">工作表缺少条目。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-116">A work table is missing an entry.</span></span> <span data-ttu-id="a4fbe-117">请重新运行查询。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-117">Rerun the query.</span></span> <span data-ttu-id="a4fbe-118">如果涉及到游标，请关闭游标，然后重新打开。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-118">If a cursor is involved, close and reopen the cursor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4fbe-119">说明</span><span class="sxs-lookup"><span data-stu-id="a4fbe-119">Explanation</span></span>  
 <span data-ttu-id="a4fbe-120">SQL Server 在工作表中找不到特定项。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-120">SQL Server cannot locate the work table for a specific entry.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4fbe-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="a4fbe-121">User Action</span></span>  
  
1.  <span data-ttu-id="a4fbe-122">如果涉及到游标，请关闭游标，然后重新打开。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-122">If a cursor is involved, close the cursor and re-open the cursor.</span></span>  
  
2.  <span data-ttu-id="a4fbe-123">再次运行查询。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-123">Run the query again.</span></span>  
  
  
