---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b05ca549781215e0c4f247110fee87f6def56f04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690551"
---
# <a name="mssql_eng018456"></a><span data-ttu-id="9addd-102">MSSQL_ENG018456</span><span class="sxs-lookup"><span data-stu-id="9addd-102">MSSQL_ENG018456</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9addd-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="9addd-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9addd-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9addd-104">Product Name</span></span>|<span data-ttu-id="9addd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9addd-105">SQL Server</span></span>|  
|<span data-ttu-id="9addd-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9addd-106">Event ID</span></span>|<span data-ttu-id="9addd-107">18456</span><span class="sxs-lookup"><span data-stu-id="9addd-107">18456</span></span>|  
|<span data-ttu-id="9addd-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9addd-108">Event Source</span></span>|<span data-ttu-id="9addd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9addd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9addd-110">组件</span><span class="sxs-lookup"><span data-stu-id="9addd-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9addd-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="9addd-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9addd-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="9addd-112">Message Text</span></span>|<span data-ttu-id="9addd-113">用户 '%.\*ls'.%.\*ls 登录失败</span><span class="sxs-lookup"><span data-stu-id="9addd-113">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9addd-114">说明</span><span class="sxs-lookup"><span data-stu-id="9addd-114">Explanation</span></span>  
 <span data-ttu-id="9addd-115">每当尝试登录失败时都会引发 MSSQL_ENG018456 错误。</span><span class="sxs-lookup"><span data-stu-id="9addd-115">Error MSSQL_ENG018456 is raised whenever a login attempt fails.</span></span> <span data-ttu-id="9addd-116">如果错误消息包括帐户 **distributor_admin** （用户“distributor_admin”登录失败。)，则问题出在复制所用的帐户上。</span><span class="sxs-lookup"><span data-stu-id="9addd-116">If the error message includes the account **distributor_admin** (Login failed for user 'distributor_admin'.), the issue is with an account used by replication.</span></span> <span data-ttu-id="9addd-117">复制过程将创建远程服务器 **repl_distributor**，该服务器允许在分发服务器和发布服务器之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="9addd-117">Replication creates a remote server, **repl_distributor**, which allows communication between the Distributor and Publisher.</span></span> <span data-ttu-id="9addd-118">登录名 **distributor_admin** 与此远程服务器关联，并且必须具有有效的密码。</span><span class="sxs-lookup"><span data-stu-id="9addd-118">The login **distributor_admin** is associated with this remote server and must have a valid password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9addd-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="9addd-119">User Action</span></span>  
 <span data-ttu-id="9addd-120">确保为此帐户指定了密码。</span><span class="sxs-lookup"><span data-stu-id="9addd-120">Ensure that you have specified a password for this account.</span></span> <span data-ttu-id="9addd-121">有关详细信息，请参阅[保护分发服务器的安全](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="9addd-121">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9addd-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9addd-122">See Also</span></span>  
 [<span data-ttu-id="9addd-123">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="9addd-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
