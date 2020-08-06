---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d37ce2dc11f231e8a6f8ae6cc8b95d8b2f87c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586697"
---
# <a name="mssqlserver_7911"></a><span data-ttu-id="5c4a4-102">MSSQLSERVER_7911</span><span class="sxs-lookup"><span data-stu-id="5c4a4-102">MSSQLSERVER_7911</span></span>
    
## <a name="details"></a><span data-ttu-id="5c4a4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5c4a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c4a4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5c4a4-104">Product Name</span></span>|<span data-ttu-id="5c4a4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5c4a4-105">SQL Server</span></span>|  
|<span data-ttu-id="5c4a4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5c4a4-106">Event ID</span></span>|<span data-ttu-id="5c4a4-107">7911</span><span class="sxs-lookup"><span data-stu-id="5c4a4-107">7911</span></span>|  
|<span data-ttu-id="5c4a4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5c4a4-108">Event Source</span></span>|<span data-ttu-id="5c4a4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5c4a4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5c4a4-110">组件</span><span class="sxs-lookup"><span data-stu-id="5c4a4-110">Component</span></span>|<span data-ttu-id="5c4a4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5c4a4-111">SQLEngine</span></span>|  
|<span data-ttu-id="5c4a4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5c4a4-112">Symbolic Name</span></span>|<span data-ttu-id="5c4a4-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="5c4a4-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span></span>|  
|<span data-ttu-id="5c4a4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5c4a4-114">Message Text</span></span>|<span data-ttu-id="5c4a4-115">修复:页 P_ID 已从对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）中释放。</span><span class="sxs-lookup"><span data-stu-id="5c4a4-115">Repair: The page P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5c4a4-116">说明</span><span class="sxs-lookup"><span data-stu-id="5c4a4-116">Explanation</span></span>  
 <span data-ttu-id="5c4a4-117">这是来自 REPAIR 的信息性消息，指出页已从索引分配映射 (IAM) 页的单页槽数组释放。</span><span class="sxs-lookup"><span data-stu-id="5c4a4-117">This is an informational message from REPAIR that states that a page has been deallocated from the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c4a4-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="5c4a4-118">User Action</span></span>  
 <span data-ttu-id="5c4a4-119">无</span><span class="sxs-lookup"><span data-stu-id="5c4a4-119">None</span></span>  
  
  
