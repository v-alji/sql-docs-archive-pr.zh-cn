---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589645"
---
# <a name="mssqlserver_15517"></a><span data-ttu-id="4b74e-102">MSSQLSERVER_15517</span><span class="sxs-lookup"><span data-stu-id="4b74e-102">MSSQLSERVER_15517</span></span>
    
## <a name="details"></a><span data-ttu-id="4b74e-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="4b74e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b74e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="4b74e-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="4b74e-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4b74e-105">Event ID</span></span>|<span data-ttu-id="4b74e-106">15517</span><span class="sxs-lookup"><span data-stu-id="4b74e-106">15517</span></span>|  
|<span data-ttu-id="4b74e-107">事件源</span><span class="sxs-lookup"><span data-stu-id="4b74e-107">Event Source</span></span>|<span data-ttu-id="4b74e-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4b74e-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4b74e-109">组件</span><span class="sxs-lookup"><span data-stu-id="4b74e-109">Component</span></span>|<span data-ttu-id="4b74e-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4b74e-110">SQLEngine</span></span>|  
|<span data-ttu-id="4b74e-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="4b74e-111">Symbolic Name</span></span>|<span data-ttu-id="4b74e-112">SEC_CANNOTEXECUTEASUSER</span><span class="sxs-lookup"><span data-stu-id="4b74e-112">SEC_CANNOTEXECUTEASUSER</span></span>|  
|<span data-ttu-id="4b74e-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="4b74e-113">Message Text</span></span>|<span data-ttu-id="4b74e-114">无法作为数据库主体执行，因为主体“*principal*”不存在、无法模拟这种类型的主体，或你没有所需的权限。</span><span class="sxs-lookup"><span data-stu-id="4b74e-114">Cannot execute as the database principal because the principal "*principal*" does not exist, this type of principal cannot be impersonated, or you do not have permission.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="4b74e-115">用户操作</span><span class="sxs-lookup"><span data-stu-id="4b74e-115">User Action</span></span>  
 <span data-ttu-id="4b74e-116">使用现有主体的名称或者获取针对该主体的 IMPERSONATE 权限。</span><span class="sxs-lookup"><span data-stu-id="4b74e-116">Use the name of an existing principal or get the IMPERSONATE permission on that principal.</span></span>  
  
 <span data-ttu-id="4b74e-117">在并非原始数据库所有者的某个其他人执行数据库的附加和还原后，也可能会发生错误 15517。</span><span class="sxs-lookup"><span data-stu-id="4b74e-117">15517 can also occur after performing an attach and restore of a database by someone other than the original database owner.</span></span> <span data-ttu-id="4b74e-118">若要纠正此错误，请通过运行以下命令，将 db_owner 更改为您的服务器上的某个登录名：</span><span class="sxs-lookup"><span data-stu-id="4b74e-118">To resolve this error, change the db_owner to a login on your server, by running the following command:</span></span>  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b74e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b74e-119">See Also</span></span>  
 [<span data-ttu-id="4b74e-120">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="4b74e-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
