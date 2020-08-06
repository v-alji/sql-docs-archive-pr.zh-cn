---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdca0a3cd9ce47ccb39ebeaf8fd1cd260aafbd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688918"
---
# <a name="mssqlserver_8689"></a><span data-ttu-id="955b3-102">MSSQLSERVER_8689</span><span class="sxs-lookup"><span data-stu-id="955b3-102">MSSQLSERVER_8689</span></span>
    
## <a name="details"></a><span data-ttu-id="955b3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="955b3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="955b3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="955b3-104">Product Name</span></span>|<span data-ttu-id="955b3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="955b3-105">SQL Server</span></span>|  
|<span data-ttu-id="955b3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="955b3-106">Event ID</span></span>|<span data-ttu-id="955b3-107">8689</span><span class="sxs-lookup"><span data-stu-id="955b3-107">8689</span></span>|  
|<span data-ttu-id="955b3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="955b3-108">Event Source</span></span>|<span data-ttu-id="955b3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="955b3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="955b3-110">组件</span><span class="sxs-lookup"><span data-stu-id="955b3-110">Component</span></span>|<span data-ttu-id="955b3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="955b3-111">SQLEngine</span></span>|  
|<span data-ttu-id="955b3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="955b3-112">Symbolic Name</span></span>|<span data-ttu-id="955b3-113">USEPLAN_ERR_NO_DB</span><span class="sxs-lookup"><span data-stu-id="955b3-113">USEPLAN_ERR_NO_DB</span></span>|  
|<span data-ttu-id="955b3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="955b3-114">Message Text</span></span>|<span data-ttu-id="955b3-115">USE PLAN 提示中指定的数据库 '%.\*ls' 不存在。</span><span class="sxs-lookup"><span data-stu-id="955b3-115">Database '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="955b3-116">请指定一个现有数据库。</span><span class="sxs-lookup"><span data-stu-id="955b3-116">Specify an existing database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="955b3-117">说明</span><span class="sxs-lookup"><span data-stu-id="955b3-117">Explanation</span></span>  
 <span data-ttu-id="955b3-118">USE PLAN 提示中指定的数据库不存在。</span><span class="sxs-lookup"><span data-stu-id="955b3-118">A database that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="955b3-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="955b3-119">User Action</span></span>  
 <span data-ttu-id="955b3-120">请确保在 USE PLAN 提示中指定的所有数据库均存在。</span><span class="sxs-lookup"><span data-stu-id="955b3-120">Ensure all databases that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955b3-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="955b3-121">See Also</span></span>  
 <span data-ttu-id="955b3-122">[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="955b3-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="955b3-123">计划指南</span><span class="sxs-lookup"><span data-stu-id="955b3-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
