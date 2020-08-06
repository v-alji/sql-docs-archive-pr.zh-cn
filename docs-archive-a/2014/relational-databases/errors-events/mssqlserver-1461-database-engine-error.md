---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6667728b2cc134632ddc538b662d73533ee4d6ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589649"
---
# <a name="mssqlserver_1461"></a><span data-ttu-id="ce403-102">MSSQLSERVER_1461</span><span class="sxs-lookup"><span data-stu-id="ce403-102">MSSQLSERVER_1461</span></span>
    
## <a name="details"></a><span data-ttu-id="ce403-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ce403-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce403-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ce403-104">Product Name</span></span>|<span data-ttu-id="ce403-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ce403-105">SQL Server</span></span>|  
|<span data-ttu-id="ce403-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ce403-106">Event ID</span></span>|<span data-ttu-id="ce403-107">1461</span><span class="sxs-lookup"><span data-stu-id="ce403-107">1461</span></span>|  
|<span data-ttu-id="ce403-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ce403-108">Event Source</span></span>|<span data-ttu-id="ce403-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ce403-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ce403-110">组件</span><span class="sxs-lookup"><span data-stu-id="ce403-110">Component</span></span>|<span data-ttu-id="ce403-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ce403-111">SQLEngine</span></span>|  
|<span data-ttu-id="ce403-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ce403-112">Symbolic Name</span></span>|<span data-ttu-id="ce403-113">DBM_SAFETY_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="ce403-113">DBM_SAFETY_MISMATCH</span></span>|  
|<span data-ttu-id="ce403-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ce403-114">Message Text</span></span>|<span data-ttu-id="ce403-115">在服务器中检测到数据库"%.\*ls"的不同数据库镜像安全级别。</span><span class="sxs-lookup"><span data-stu-id="ce403-115">Different database mirroring safety levels among servers were detected for database "%.\*ls".</span></span> <span data-ttu-id="ce403-116">将使用 FULL 安全级别。</span><span class="sxs-lookup"><span data-stu-id="ce403-116">The FULL safety level will be used.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce403-117">说明</span><span class="sxs-lookup"><span data-stu-id="ce403-117">Explanation</span></span>  
 <span data-ttu-id="ce403-118">修改事务安全级别时镜像连接断开，因为事务安全设置在主体数据库和镜像数据库中不一致。</span><span class="sxs-lookup"><span data-stu-id="ce403-118">Mirroring connections were broken when the transaction safety level was modified because the transaction safety settings were inconsistent on the principal and mirror databases.</span></span> <span data-ttu-id="ce403-119">将使用完全事务安全的默认安全设置。</span><span class="sxs-lookup"><span data-stu-id="ce403-119">The default safety setting of full-transaction safety will be used.</span></span> <span data-ttu-id="ce403-120">会话将在高安全模式下运行。</span><span class="sxs-lookup"><span data-stu-id="ce403-120">The session will run in high-safety mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce403-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="ce403-121">User Action</span></span>  
 <span data-ttu-id="ce403-122">若要关闭事务安全，请对主体数据库重新运行 ALTER DATABASE *database_name* SET PARTNER SAFETY OFF 语句。</span><span class="sxs-lookup"><span data-stu-id="ce403-122">To set transaction safety off, rerun the ALTER DATABASE *database_name* SET PARTNER SAFETY OFF statement on the principal database.</span></span>  
  
  
