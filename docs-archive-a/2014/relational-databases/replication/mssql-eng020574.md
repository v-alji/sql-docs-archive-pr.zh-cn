---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e224e9a87d40fa826a05c669216649c45185037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591284"
---
# <a name="mssql_eng020574"></a><span data-ttu-id="52cd9-102">MSSQL_ENG020574</span><span class="sxs-lookup"><span data-stu-id="52cd9-102">MSSQL_ENG020574</span></span>
    
## <a name="message-details"></a><span data-ttu-id="52cd9-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="52cd9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52cd9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="52cd9-104">Product Name</span></span>|<span data-ttu-id="52cd9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="52cd9-105">SQL Server</span></span>|  
|<span data-ttu-id="52cd9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="52cd9-106">Event ID</span></span>|<span data-ttu-id="52cd9-107">20574</span><span class="sxs-lookup"><span data-stu-id="52cd9-107">20574</span></span>|  
|<span data-ttu-id="52cd9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="52cd9-108">Event Source</span></span>|<span data-ttu-id="52cd9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="52cd9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="52cd9-110">组件</span><span class="sxs-lookup"><span data-stu-id="52cd9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="52cd9-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="52cd9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="52cd9-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="52cd9-112">Message Text</span></span>|<span data-ttu-id="52cd9-113">订阅服务器“%s”对发布“%s”中项目“%s”的订阅未通过数据验证。</span><span class="sxs-lookup"><span data-stu-id="52cd9-113">Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="52cd9-114">说明</span><span class="sxs-lookup"><span data-stu-id="52cd9-114">Explanation</span></span>  
 <span data-ttu-id="52cd9-115">根据发布服务器上的数据对订阅服务器上的数据进行验证，数据不匹配；因此验证失败。</span><span class="sxs-lookup"><span data-stu-id="52cd9-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="52cd9-116">有关验证的详细信息，请参阅 [Validate Replicated Data](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="52cd9-116">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52cd9-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="52cd9-117">User Action</span></span>  
 <span data-ttu-id="52cd9-118">建议执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="52cd9-118">We recommend that you do the following:</span></span>  
  
-   <span data-ttu-id="52cd9-119">确定验证失败的原因。</span><span class="sxs-lookup"><span data-stu-id="52cd9-119">Determine why validation failed.</span></span>  
  
-   <span data-ttu-id="52cd9-120">更正导致失败的基本问题。</span><span class="sxs-lookup"><span data-stu-id="52cd9-120">Correct the underlying issue that caused the failure.</span></span>  
  
-   <span data-ttu-id="52cd9-121">通过重新初始化订阅或其他方法收敛数据。</span><span class="sxs-lookup"><span data-stu-id="52cd9-121">Bring the data into convergence by reinitializing the subscription or through another method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cd9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52cd9-122">See Also</span></span>  
 [<span data-ttu-id="52cd9-123">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="52cd9-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
