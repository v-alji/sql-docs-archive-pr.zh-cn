---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b1c61f3683442e0d474ff36a65c89446dbd7bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591280"
---
# <a name="mssql_eng020596"></a><span data-ttu-id="14cb2-102">MSSQL_ENG020596</span><span class="sxs-lookup"><span data-stu-id="14cb2-102">MSSQL_ENG020596</span></span>
    
## <a name="message-details"></a><span data-ttu-id="14cb2-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="14cb2-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14cb2-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="14cb2-104">Product Name</span></span>|<span data-ttu-id="14cb2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="14cb2-105">SQL Server</span></span>|  
|<span data-ttu-id="14cb2-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="14cb2-106">Event ID</span></span>|<span data-ttu-id="14cb2-107">20596</span><span class="sxs-lookup"><span data-stu-id="14cb2-107">20596</span></span>|  
|<span data-ttu-id="14cb2-108">事件源</span><span class="sxs-lookup"><span data-stu-id="14cb2-108">Event Source</span></span>|<span data-ttu-id="14cb2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="14cb2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="14cb2-110">组件</span><span class="sxs-lookup"><span data-stu-id="14cb2-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="14cb2-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="14cb2-111">Symbolic Name</span></span>||  
|<span data-ttu-id="14cb2-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="14cb2-112">Message Text</span></span>|<span data-ttu-id="14cb2-113">只有 '%s' 或 db_owner 的成员可以删除匿名代理。</span><span class="sxs-lookup"><span data-stu-id="14cb2-113">Only '%s' or members of db_owner can drop the anonymous agent.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14cb2-114">说明</span><span class="sxs-lookup"><span data-stu-id="14cb2-114">Explanation</span></span>  
 <span data-ttu-id="14cb2-115">您没有足够的权限删除匿名订阅代理。</span><span class="sxs-lookup"><span data-stu-id="14cb2-115">You do not have sufficient permissions to drop the agent for the anonymous subscription.</span></span> <span data-ttu-id="14cb2-116">调用 [sp_dropanonymousagent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) 时使用的登录名必须为分发服务器上 **sysadmin** 固定服务器角色的成员或分发数据库中 **db_owner** 固定数据库角色的成员，或者该用户必须是启动该代理首次运行的用户。</span><span class="sxs-lookup"><span data-stu-id="14cb2-116">The login used when calling [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) must be a member of the **sysadmin** fixed server role at the Distributor or **db_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14cb2-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="14cb2-117">User Action</span></span>  
 <span data-ttu-id="14cb2-118">使用适当的凭据登录，并执行 **sp_dropanonymousagent**。</span><span class="sxs-lookup"><span data-stu-id="14cb2-118">Login with the appropriate credentials, and execute **sp_dropanonymousagent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cb2-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14cb2-119">See Also</span></span>  
 [<span data-ttu-id="14cb2-120">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="14cb2-120">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
