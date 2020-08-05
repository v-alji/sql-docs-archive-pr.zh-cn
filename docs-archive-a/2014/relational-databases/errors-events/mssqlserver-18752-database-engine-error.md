---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a463e4019875f4a233ae2920f32bc2252376a41c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581271"
---
# <a name="mssqlserver_18752"></a><span data-ttu-id="cf771-102">MSSQLSERVER_18752</span><span class="sxs-lookup"><span data-stu-id="cf771-102">MSSQLSERVER_18752</span></span>
    
## <a name="details"></a><span data-ttu-id="cf771-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cf771-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf771-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cf771-104">Product Name</span></span>|<span data-ttu-id="cf771-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf771-105">SQL Server</span></span>|  
|<span data-ttu-id="cf771-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cf771-106">Event ID</span></span>|<span data-ttu-id="cf771-107">18752</span><span class="sxs-lookup"><span data-stu-id="cf771-107">18752</span></span>|  
|<span data-ttu-id="cf771-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cf771-108">Event Source</span></span>|<span data-ttu-id="cf771-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf771-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf771-110">组件</span><span class="sxs-lookup"><span data-stu-id="cf771-110">Component</span></span>|<span data-ttu-id="cf771-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cf771-111">SQLEngine</span></span>|  
|<span data-ttu-id="cf771-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cf771-112">Symbolic Name</span></span>|<span data-ttu-id="cf771-113">REPL_INUSE</span><span class="sxs-lookup"><span data-stu-id="cf771-113">REPL_INUSE</span></span>|  
|<span data-ttu-id="cf771-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cf771-114">Message Text</span></span>|<span data-ttu-id="cf771-115">一次只能有一个日志读取器代理或日志相关过程(sp_repldone、sp_replcmds 和 sp_replshowcmds)连接到某个数据库。</span><span class="sxs-lookup"><span data-stu-id="cf771-115">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="cf771-116">如果执行了一个日志相关过程，那么在启动日志读取器代理或者执行另一个日志相关过程之前，请删除执行第一个过程时所用的连接，或者在该连接上执行 sp_replflush。</span><span class="sxs-lookup"><span data-stu-id="cf771-116">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf771-117">说明</span><span class="sxs-lookup"><span data-stu-id="cf771-117">Explanation</span></span>  
 <span data-ttu-id="cf771-118">一次只能有一个日志读取器代理或日志相关过程连接到某个数据库。</span><span class="sxs-lookup"><span data-stu-id="cf771-118">Only one Log Reader agent or log-related procedure can connect to a database at a time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf771-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="cf771-119">User Action</span></span>  
 <span data-ttu-id="cf771-120">确保没有为相同发布数据库运行其他日志读取器，并且以前其他活动连接在运行 sp_replcmds/sp_repltrans/sp_repldone 后均运行了 sp_replflush 或断开了连接。</span><span class="sxs-lookup"><span data-stu-id="cf771-120">Make sure no other logreader is running for the same publishing database, and no other active connection had previously run sp_replcmds/sp_repltrans/sp_repldone without running sp_replflush afterwards or disconnecting.</span></span>  
  
  
