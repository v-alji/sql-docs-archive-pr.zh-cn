---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27b2ceed40274df4ba57c4d61a83fbc60b6a7f80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586742"
---
# <a name="mssqlserver_2596"></a><span data-ttu-id="b4548-102">MSSQLSERVER_2596</span><span class="sxs-lookup"><span data-stu-id="b4548-102">MSSQLSERVER_2596</span></span>
    
## <a name="details"></a><span data-ttu-id="b4548-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b4548-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4548-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b4548-104">Product Name</span></span>|<span data-ttu-id="b4548-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4548-105">SQL Server</span></span>|  
|<span data-ttu-id="b4548-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b4548-106">Event ID</span></span>|<span data-ttu-id="b4548-107">2596</span><span class="sxs-lookup"><span data-stu-id="b4548-107">2596</span></span>|  
|<span data-ttu-id="b4548-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b4548-108">Event Source</span></span>|<span data-ttu-id="b4548-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b4548-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b4548-110">组件</span><span class="sxs-lookup"><span data-stu-id="b4548-110">Component</span></span>|<span data-ttu-id="b4548-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b4548-111">SQLEngine</span></span>|  
|<span data-ttu-id="b4548-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b4548-112">Symbolic Name</span></span>|<span data-ttu-id="b4548-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span><span class="sxs-lookup"><span data-stu-id="b4548-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span></span>|  
|<span data-ttu-id="b4548-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b4548-114">Message Text</span></span>|<span data-ttu-id="b4548-115">未处理修复语句。</span><span class="sxs-lookup"><span data-stu-id="b4548-115">The repair statement was not processed.</span></span> <span data-ttu-id="b4548-116">该数据库不能处于只读模式。</span><span class="sxs-lookup"><span data-stu-id="b4548-116">The database cannot be in read-only mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4548-117">说明</span><span class="sxs-lookup"><span data-stu-id="b4548-117">Explanation</span></span>  
 <span data-ttu-id="b4548-118">此消息指示数据库处于只读模式。</span><span class="sxs-lookup"><span data-stu-id="b4548-118">This message indicates that the database is in read-only mode.</span></span> <span data-ttu-id="b4548-119">当数据库处于只读模式时不能进行修复。</span><span class="sxs-lookup"><span data-stu-id="b4548-119">Repairs are not possible when a database is in read-only mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4548-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="b4548-120">User Action</span></span>  
 <span data-ttu-id="b4548-121">使用 ALTER DATABASE 设置要读写的数据库，然后重新运行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="b4548-121">Set the database to read-write by using ALTER DATABASE, and then re-run the DBCC command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4548-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4548-122">See Also</span></span>  
 [<span data-ttu-id="b4548-123">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b4548-123">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
