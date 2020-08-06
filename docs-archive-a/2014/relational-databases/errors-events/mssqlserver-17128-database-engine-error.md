---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e08c668acd0a8b2decb14da338b8d1f1e650de5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688934"
---
# <a name="mssqlserver_17128"></a><span data-ttu-id="4346c-102">MSSQLSERVER_17128</span><span class="sxs-lookup"><span data-stu-id="4346c-102">MSSQLSERVER_17128</span></span>
    
## <a name="details"></a><span data-ttu-id="4346c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="4346c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4346c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="4346c-104">Product Name</span></span>|<span data-ttu-id="4346c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4346c-105">SQL Server</span></span>|  
|<span data-ttu-id="4346c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4346c-106">Event ID</span></span>|<span data-ttu-id="4346c-107">17128</span><span class="sxs-lookup"><span data-stu-id="4346c-107">17128</span></span>|  
|<span data-ttu-id="4346c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="4346c-108">Event Source</span></span>|<span data-ttu-id="4346c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4346c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4346c-110">组件</span><span class="sxs-lookup"><span data-stu-id="4346c-110">Component</span></span>|<span data-ttu-id="4346c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4346c-111">SQLEngine</span></span>|  
|<span data-ttu-id="4346c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="4346c-112">Symbolic Name</span></span>|<span data-ttu-id="4346c-113">INIT_NOBUFSPACE</span><span class="sxs-lookup"><span data-stu-id="4346c-113">INIT_NOBUFSPACE</span></span>|  
|<span data-ttu-id="4346c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="4346c-114">Message Text</span></span>|<span data-ttu-id="4346c-115">initdata:没有可用于核心缓冲区的内存。</span><span class="sxs-lookup"><span data-stu-id="4346c-115">initdata: No memory for kernel buffers.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4346c-116">说明</span><span class="sxs-lookup"><span data-stu-id="4346c-116">Explanation</span></span>  
 <span data-ttu-id="4346c-117">缓冲池的初始内存分配或预留失败，并且 SQL Server 退出。</span><span class="sxs-lookup"><span data-stu-id="4346c-117">The buffer pool's initial memory allocations or reservations have failed, and SQL Server exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4346c-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="4346c-118">User Action</span></span>  
 <span data-ttu-id="4346c-119">通常是由在非常小的计算机（远小于最低系统要求）上启动 SQL Server 引起的。</span><span class="sxs-lookup"><span data-stu-id="4346c-119">Usually caused by starting SQL Server on an extremely small machine - far smaller than the minimum system requirements.</span></span>  
  
  
