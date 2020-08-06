---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689412"
---
# <a name="mssqlserver_17130"></a><span data-ttu-id="de1b8-102">MSSQLSERVER_17130</span><span class="sxs-lookup"><span data-stu-id="de1b8-102">MSSQLSERVER_17130</span></span>
    
## <a name="details"></a><span data-ttu-id="de1b8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="de1b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de1b8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="de1b8-104">Product Name</span></span>|<span data-ttu-id="de1b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="de1b8-105">SQL Server</span></span>|  
|<span data-ttu-id="de1b8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="de1b8-106">Event ID</span></span>|<span data-ttu-id="de1b8-107">17130</span><span class="sxs-lookup"><span data-stu-id="de1b8-107">17130</span></span>|  
|<span data-ttu-id="de1b8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="de1b8-108">Event Source</span></span>|<span data-ttu-id="de1b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="de1b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="de1b8-110">组件</span><span class="sxs-lookup"><span data-stu-id="de1b8-110">Component</span></span>|<span data-ttu-id="de1b8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="de1b8-111">SQLEngine</span></span>|  
|<span data-ttu-id="de1b8-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="de1b8-112">Symbolic Name</span></span>|<span data-ttu-id="de1b8-113">INIT_NOLOCKSPACE</span><span class="sxs-lookup"><span data-stu-id="de1b8-113">INIT_NOLOCKSPACE</span></span>|  
|<span data-ttu-id="de1b8-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="de1b8-114">Message Text</span></span>|<span data-ttu-id="de1b8-115">没有足够的内存分配给所配置的锁数。</span><span class="sxs-lookup"><span data-stu-id="de1b8-115">Not enough memory for the configured number of locks.</span></span> <span data-ttu-id="de1b8-116">正尝试以较小的锁哈希表启动，但这可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="de1b8-116">Attempting to start with a smaller lock hash table, which may impact performance.</span></span> <span data-ttu-id="de1b8-117">请与数据库管理员联系，为数据库引擎的这一实例配置更多内存。</span><span class="sxs-lookup"><span data-stu-id="de1b8-117">Contact the database administrator to configure more memory for this instance of the Database Engine.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="de1b8-118">说明</span><span class="sxs-lookup"><span data-stu-id="de1b8-118">Explanation</span></span>  
 <span data-ttu-id="de1b8-119">没有足够的内存来分配所需大小的锁管理器哈希表。</span><span class="sxs-lookup"><span data-stu-id="de1b8-119">Not enough memory for the desired lock manager hash table size.</span></span>  <span data-ttu-id="de1b8-120">将尝试分配一个较小的哈希表。</span><span class="sxs-lookup"><span data-stu-id="de1b8-120">An attempt will be made to allocate a smaller hash table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="de1b8-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="de1b8-121">User Action</span></span>  
 <span data-ttu-id="de1b8-122">检查服务器内存配置参数（最小/最大服务器内存），然后检查内存不足情况。</span><span class="sxs-lookup"><span data-stu-id="de1b8-122">Check server memory configuration parameters (min/max server memory), check for memory pressures.</span></span> <span data-ttu-id="de1b8-123">为 SQL Server 提供更多的内存。</span><span class="sxs-lookup"><span data-stu-id="de1b8-123">Provide SQL Server more memory.</span></span>  
  
  
