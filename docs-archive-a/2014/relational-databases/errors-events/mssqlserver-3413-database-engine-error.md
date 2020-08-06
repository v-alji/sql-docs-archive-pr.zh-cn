---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a5d59ea61cff7051c3e1163a463c29443c553923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589601"
---
# <a name="mssqlserver_3413"></a><span data-ttu-id="07425-102">MSSQLSERVER_3413</span><span class="sxs-lookup"><span data-stu-id="07425-102">MSSQLSERVER_3413</span></span>
    
## <a name="details"></a><span data-ttu-id="07425-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="07425-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07425-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="07425-104">Product Name</span></span>|<span data-ttu-id="07425-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="07425-105">SQL Server</span></span>|  
|<span data-ttu-id="07425-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="07425-106">Event ID</span></span>|<span data-ttu-id="07425-107">3413</span><span class="sxs-lookup"><span data-stu-id="07425-107">3413</span></span>|  
|<span data-ttu-id="07425-108">事件源</span><span class="sxs-lookup"><span data-stu-id="07425-108">Event Source</span></span>|<span data-ttu-id="07425-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="07425-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="07425-110">组件</span><span class="sxs-lookup"><span data-stu-id="07425-110">Component</span></span>|<span data-ttu-id="07425-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="07425-111">SQLEngine</span></span>|  
|<span data-ttu-id="07425-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="07425-112">Symbolic Name</span></span>|<span data-ttu-id="07425-113">MARKDB</span><span class="sxs-lookup"><span data-stu-id="07425-113">MARKDB</span></span>|  
|<span data-ttu-id="07425-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="07425-114">Message Text</span></span>|<span data-ttu-id="07425-115">数据库 ID 为 %d。</span><span class="sxs-lookup"><span data-stu-id="07425-115">Database ID %d.</span></span> <span data-ttu-id="07425-116">无法将数据库标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="07425-116">Could not mark database as suspect.</span></span> <span data-ttu-id="07425-117">对 sys.databases.database_id 进行的 Getnext NC 扫描失败。</span><span class="sxs-lookup"><span data-stu-id="07425-117">Getnext NC scan on sys.databases.database_id failed.</span></span> <span data-ttu-id="07425-118">请参阅错误日志中以前的错误，以标识原因并更正任何相关的问题。</span><span class="sxs-lookup"><span data-stu-id="07425-118">Refer to previous errors in the error log to identify the cause and correct any associated problems.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="07425-119">说明</span><span class="sxs-lookup"><span data-stu-id="07425-119">Explanation</span></span>  
 <span data-ttu-id="07425-120">尝试将用户数据库标记为目录中的 SUSPECT 时意外失败。</span><span class="sxs-lookup"><span data-stu-id="07425-120">There was an unexpected failure while trying to mark a user database as SUSPECT in the catalog.</span></span> <span data-ttu-id="07425-121">SUSPECT 状态不会持久化。</span><span class="sxs-lookup"><span data-stu-id="07425-121">The SUSPECT state will not be persisted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="07425-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="07425-122">User Action</span></span>  
 <span data-ttu-id="07425-123">请参阅以前的错误并更正问题。</span><span class="sxs-lookup"><span data-stu-id="07425-123">See previous errors and correct the problem.</span></span>  
  
  
