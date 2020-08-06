---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e91b0d64140329639cf57f3a336cd2eab8e4e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689390"
---
# <a name="mssqlserver_2511"></a><span data-ttu-id="02b86-102">MSSQLSERVER_2511</span><span class="sxs-lookup"><span data-stu-id="02b86-102">MSSQLSERVER_2511</span></span>
    
## <a name="details"></a><span data-ttu-id="02b86-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="02b86-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02b86-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="02b86-104">Product Name</span></span>|<span data-ttu-id="02b86-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="02b86-105">SQL Server</span></span>|  
|<span data-ttu-id="02b86-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="02b86-106">Event ID</span></span>|<span data-ttu-id="02b86-107">2511</span><span class="sxs-lookup"><span data-stu-id="02b86-107">2511</span></span>|  
|<span data-ttu-id="02b86-108">事件源</span><span class="sxs-lookup"><span data-stu-id="02b86-108">Event Source</span></span>|<span data-ttu-id="02b86-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="02b86-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="02b86-110">组件</span><span class="sxs-lookup"><span data-stu-id="02b86-110">Component</span></span>|<span data-ttu-id="02b86-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="02b86-111">SQLEngine</span></span>|  
|<span data-ttu-id="02b86-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="02b86-112">Symbolic Name</span></span>|<span data-ttu-id="02b86-113">DBCC_KEYS_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="02b86-113">DBCC_KEYS_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="02b86-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="02b86-114">Message Text</span></span>|<span data-ttu-id="02b86-115">表错误:对象 ID %d，索引 ID %d，分区 ID %I64d，分配单元 ID %I64d (类型为 %.\*ls)。</span><span class="sxs-lookup"><span data-stu-id="02b86-115">Table error: Object ID %d, index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls).</span></span> <span data-ttu-id="02b86-116">页 %S_PGID，槽 %d 和 %d 中的键顺序不对。</span><span class="sxs-lookup"><span data-stu-id="02b86-116">Keys out of order on page %S_PGID, slots %d and %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02b86-117">说明</span><span class="sxs-lookup"><span data-stu-id="02b86-117">Explanation</span></span>  
 <span data-ttu-id="02b86-118">在指定的索引中检测到顺序不对的键。</span><span class="sxs-lookup"><span data-stu-id="02b86-118">Out-of-order keys were detected in the specified index.</span></span> <span data-ttu-id="02b86-119">包含这些键的页可能已损坏。</span><span class="sxs-lookup"><span data-stu-id="02b86-119">The page in which the keys are contained may be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02b86-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="02b86-120">User Action</span></span>  
 <span data-ttu-id="02b86-121">使用 ALTER INDEX REBUILD 语句重新生成指定的索引。</span><span class="sxs-lookup"><span data-stu-id="02b86-121">Rebuild the specified index by using the ALTER INDEX REBUILD statement.</span></span>  
  
  
