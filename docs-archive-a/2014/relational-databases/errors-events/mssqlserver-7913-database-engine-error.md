---
title: MSSQLSERVER_7913 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7913 (Database Engine error)
ms.assetid: 9d8ad456-b1a2-4f79-a252-657fbec9ad9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb4110ef3aed8697db426ebd80f6764d873944db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587413"
---
# <a name="mssqlserver_7913"></a><span data-ttu-id="2e9d4-102">MSSQLSERVER_7913</span><span class="sxs-lookup"><span data-stu-id="2e9d4-102">MSSQLSERVER_7913</span></span>
    
## <a name="details"></a><span data-ttu-id="2e9d4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e9d4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e9d4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2e9d4-104">Product Name</span></span>|<span data-ttu-id="2e9d4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2e9d4-105">SQL Server</span></span>|  
|<span data-ttu-id="2e9d4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2e9d4-106">Event ID</span></span>|<span data-ttu-id="2e9d4-107">7913</span><span class="sxs-lookup"><span data-stu-id="2e9d4-107">7913</span></span>|  
|<span data-ttu-id="2e9d4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2e9d4-108">Event Source</span></span>|<span data-ttu-id="2e9d4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2e9d4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2e9d4-110">组件</span><span class="sxs-lookup"><span data-stu-id="2e9d4-110">Component</span></span>|<span data-ttu-id="2e9d4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2e9d4-111">SQLEngine</span></span>|  
|<span data-ttu-id="2e9d4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2e9d4-112">Symbolic Name</span></span>|<span data-ttu-id="2e9d4-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="2e9d4-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span></span>|  
|<span data-ttu-id="2e9d4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2e9d4-114">Message Text</span></span>|<span data-ttu-id="2e9d4-115">修复:区 P_ID 已从对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID （类型为 TYPE）释放。</span><span class="sxs-lookup"><span data-stu-id="2e9d4-115">Repair: Extent P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e9d4-116">说明</span><span class="sxs-lookup"><span data-stu-id="2e9d4-116">Explanation</span></span>  
 <span data-ttu-id="2e9d4-117">这是来自 REPAIR 的信息性消息，该消息声明已将一个区从指定的对象释放。</span><span class="sxs-lookup"><span data-stu-id="2e9d4-117">This is an informational message from REPAIR that states that an extent has been deallocated from the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e9d4-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="2e9d4-118">User Action</span></span>  
 <span data-ttu-id="2e9d4-119">无</span><span class="sxs-lookup"><span data-stu-id="2e9d4-119">None</span></span>  
  
  
