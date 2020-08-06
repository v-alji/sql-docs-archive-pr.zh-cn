---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d3a12d5d0732ba8694db3d4c7dcae1eac59d28b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591901"
---
# <a name="mssqlserver_8966"></a><span data-ttu-id="c2203-102">MSSQLSERVER_8966</span><span class="sxs-lookup"><span data-stu-id="c2203-102">MSSQLSERVER_8966</span></span>
    
## <a name="details"></a><span data-ttu-id="c2203-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c2203-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2203-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c2203-104">Product Name</span></span>|<span data-ttu-id="c2203-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c2203-105">SQL Server</span></span>|  
|<span data-ttu-id="c2203-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c2203-106">Event ID</span></span>|<span data-ttu-id="c2203-107">8966</span><span class="sxs-lookup"><span data-stu-id="c2203-107">8966</span></span>|  
|<span data-ttu-id="c2203-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c2203-108">Event Source</span></span>|<span data-ttu-id="c2203-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c2203-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c2203-110">组件</span><span class="sxs-lookup"><span data-stu-id="c2203-110">Component</span></span>|<span data-ttu-id="c2203-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c2203-111">SQLEngine</span></span>|  
|<span data-ttu-id="c2203-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="c2203-112">Symbolic Name</span></span>|<span data-ttu-id="c2203-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span><span class="sxs-lookup"><span data-stu-id="c2203-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span></span>|  
|<span data-ttu-id="c2203-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="c2203-114">Message Text</span></span>|<span data-ttu-id="c2203-115">无法使用闩锁类型 TYPE 读取并闩锁页 P_ID。</span><span class="sxs-lookup"><span data-stu-id="c2203-115">Unable to read and latch page P_ID with latch type TYPE.</span></span> <span data-ttu-id="c2203-116">操作失败。</span><span class="sxs-lookup"><span data-stu-id="c2203-116">OPERATION failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2203-117">说明</span><span class="sxs-lookup"><span data-stu-id="c2203-117">Explanation</span></span>  
 <span data-ttu-id="c2203-118">页读取失败或无法针对 PFS 或 GAM 页进行闩锁。</span><span class="sxs-lookup"><span data-stu-id="c2203-118">The page read failed or a latch could not be taken on a PFS or GAM page.</span></span> <span data-ttu-id="c2203-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中可能会有闩锁超时或其他附带的消息。</span><span class="sxs-lookup"><span data-stu-id="c2203-119">There may be latch time-out or other accompanying messages in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2203-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="c2203-120">User Action</span></span>  
 <span data-ttu-id="c2203-121">查阅 SQL 错误日志，检查附带的消息并解决其中的错误。</span><span class="sxs-lookup"><span data-stu-id="c2203-121">Review the SQL error log for accompanying messages and resolve these errors.</span></span>  
  
  
