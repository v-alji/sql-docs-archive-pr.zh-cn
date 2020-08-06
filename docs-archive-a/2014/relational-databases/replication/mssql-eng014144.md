---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d93f06a585bcc01c52438ff7b99bbd635532402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576662"
---
# <a name="mssql_eng014144"></a><span data-ttu-id="8c575-102">MSSQL_ENG014144</span><span class="sxs-lookup"><span data-stu-id="8c575-102">MSSQL_ENG014144</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8c575-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8c575-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c575-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8c575-104">Product Name</span></span>|<span data-ttu-id="8c575-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8c575-105">SQL Server</span></span>|  
|<span data-ttu-id="8c575-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8c575-106">Event ID</span></span>|<span data-ttu-id="8c575-107">14144</span><span class="sxs-lookup"><span data-stu-id="8c575-107">14144</span></span>|  
|<span data-ttu-id="8c575-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8c575-108">Event Source</span></span>|<span data-ttu-id="8c575-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8c575-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8c575-110">组件</span><span class="sxs-lookup"><span data-stu-id="8c575-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8c575-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8c575-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8c575-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8c575-112">Message Text</span></span>|<span data-ttu-id="8c575-113">无法删除订阅服务器 '%s'。</span><span class="sxs-lookup"><span data-stu-id="8c575-113">Cannot drop Subscriber '%s'.</span></span> <span data-ttu-id="8c575-114">在发布数据库 '%s' 中已有此服务器的订阅。</span><span class="sxs-lookup"><span data-stu-id="8c575-114">There are subscriptions for it in the publication database '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8c575-115">说明</span><span class="sxs-lookup"><span data-stu-id="8c575-115">Explanation</span></span>  
 <span data-ttu-id="8c575-116">配置为订阅服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例在存在有为其配置的活动订阅时无法从订阅服务器的角色中删除。</span><span class="sxs-lookup"><span data-stu-id="8c575-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Subscriber cannot be removed from the role of Subscriber while there are active subscriptions configured for the instance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c575-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="8c575-117">User Action</span></span>  
 <span data-ttu-id="8c575-118">在尝试更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的订阅服务器状态之前，删除所有相关联的订阅。</span><span class="sxs-lookup"><span data-stu-id="8c575-118">Drop all associated subscriptions before attempting to change the Subscriber status of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="8c575-119">在发布服务器的发布数据库中执行 [sp_helpsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)，以查找订阅。</span><span class="sxs-lookup"><span data-stu-id="8c575-119">Execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) in the publication database at the Publisher to find subscriptions.</span></span>  
  
2.  <span data-ttu-id="8c575-120">在发布数据库中执行 [sp_dropsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)，以删除订阅。</span><span class="sxs-lookup"><span data-stu-id="8c575-120">Execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) in the publication database to drop subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c575-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c575-121">See Also</span></span>  
 <span data-ttu-id="8c575-122">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8c575-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="8c575-123">订阅发布</span><span class="sxs-lookup"><span data-stu-id="8c575-123">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
