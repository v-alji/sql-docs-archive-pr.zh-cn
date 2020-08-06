---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1dc7a69023e49b48a10da9f0388cbd72fbe46be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587410"
---
# <a name="mssqlserver_7915"></a><span data-ttu-id="a810a-102">MSSQLSERVER_7915</span><span class="sxs-lookup"><span data-stu-id="a810a-102">MSSQLSERVER_7915</span></span>
    
## <a name="details"></a><span data-ttu-id="a810a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a810a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a810a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a810a-104">Product Name</span></span>|<span data-ttu-id="a810a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a810a-105">SQL Server</span></span>|  
|<span data-ttu-id="a810a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a810a-106">Event ID</span></span>|<span data-ttu-id="a810a-107">7915</span><span class="sxs-lookup"><span data-stu-id="a810a-107">7915</span></span>|  
|<span data-ttu-id="a810a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a810a-108">Event Source</span></span>|<span data-ttu-id="a810a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a810a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a810a-110">组件</span><span class="sxs-lookup"><span data-stu-id="a810a-110">Component</span></span>|<span data-ttu-id="a810a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a810a-111">SQLEngine</span></span>|  
|<span data-ttu-id="a810a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a810a-112">Symbolic Name</span></span>|<span data-ttu-id="a810a-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span><span class="sxs-lookup"><span data-stu-id="a810a-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span></span>|  
|<span data-ttu-id="a810a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a810a-114">Message Text</span></span>|<span data-ttu-id="a810a-115">修复:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的 IAM 链已在页 P_ID 前截断，将重新生成该链。</span><span class="sxs-lookup"><span data-stu-id="a810a-115">Repair: IAM chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), has been truncated before page P_ID and will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a810a-116">说明</span><span class="sxs-lookup"><span data-stu-id="a810a-116">Explanation</span></span>  
 <span data-ttu-id="a810a-117">这是 REPAIR 发送的信息性消息，指示修补了指定的索引分配映射 (IAM) 链，以便可以重新生成它。</span><span class="sxs-lookup"><span data-stu-id="a810a-117">This is an information message sent by REPAIR that indicates that the specified Index Allocation Map (IAM) chain was patched so that it could be rebuilt.</span></span> <span data-ttu-id="a810a-118">此修补可能需要分配新的 IAM 链头或者删除错误页。</span><span class="sxs-lookup"><span data-stu-id="a810a-118">This patching may have required the allocation of a new head of the IAM chain or the removal of bad pages from the chain.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a810a-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="a810a-119">User Action</span></span>  
 <span data-ttu-id="a810a-120">无</span><span class="sxs-lookup"><span data-stu-id="a810a-120">None</span></span>  
  
  
