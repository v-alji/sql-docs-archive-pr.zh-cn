---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f98c831642580587552bf60c604d84c38fffca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589582"
---
# <a name="mssqlserver_5245"></a><span data-ttu-id="0d14f-102">MSSQLSERVER_5245</span><span class="sxs-lookup"><span data-stu-id="0d14f-102">MSSQLSERVER_5245</span></span>
    
## <a name="details"></a><span data-ttu-id="0d14f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0d14f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d14f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0d14f-104">Product Name</span></span>|<span data-ttu-id="0d14f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0d14f-105">SQL Server</span></span>|  
|<span data-ttu-id="0d14f-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0d14f-106">Event ID</span></span>|<span data-ttu-id="0d14f-107">5245</span><span class="sxs-lookup"><span data-stu-id="0d14f-107">5245</span></span>|  
|<span data-ttu-id="0d14f-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0d14f-108">Event Source</span></span>|<span data-ttu-id="0d14f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0d14f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0d14f-110">组件</span><span class="sxs-lookup"><span data-stu-id="0d14f-110">Component</span></span>|<span data-ttu-id="0d14f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0d14f-111">SQLEngine</span></span>|  
|<span data-ttu-id="0d14f-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="0d14f-112">Symbolic Name</span></span>|<span data-ttu-id="0d14f-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="0d14f-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span></span>|  
|<span data-ttu-id="0d14f-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="0d14f-114">Message Text</span></span>|<span data-ttu-id="0d14f-115">对象 ID O_ID （对象“NAME”）：由于超过了锁请求超时期限，DBCC 无法获取该对象的锁。</span><span class="sxs-lookup"><span data-stu-id="0d14f-115">Object ID O_ID (object 'NAME'): DBCC could not obtain a lock on this object because the lock request time-out period was exceeded.</span></span> <span data-ttu-id="0d14f-116">已跳过此对象，不会处理它。</span><span class="sxs-lookup"><span data-stu-id="0d14f-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d14f-117">说明</span><span class="sxs-lookup"><span data-stu-id="0d14f-117">Explanation</span></span>  
 <span data-ttu-id="0d14f-118">在 DBCC 等待指定对象的表锁时，出现锁超时。</span><span class="sxs-lookup"><span data-stu-id="0d14f-118">A lock time-out occurred while DBCC was waiting on a table lock for the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d14f-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="0d14f-119">User Action</span></span>  
 <span data-ttu-id="0d14f-120">重新运行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="0d14f-120">Rerun the DBCC command.</span></span>  
  
  
