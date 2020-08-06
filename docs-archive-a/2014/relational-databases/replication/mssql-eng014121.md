---
title: MSSQL_ENG014121 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04d4cbdd2197745d2d795814d88c4f7bc28eb90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576667"
---
# <a name="mssql_eng014121"></a><span data-ttu-id="930a9-102">MSSQL_ENG014121</span><span class="sxs-lookup"><span data-stu-id="930a9-102">MSSQL_ENG014121</span></span>
    
## <a name="message-details"></a><span data-ttu-id="930a9-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="930a9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="930a9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="930a9-104">Product Name</span></span>|<span data-ttu-id="930a9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="930a9-105">SQL Server</span></span>|  
|<span data-ttu-id="930a9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="930a9-106">Event ID</span></span>|<span data-ttu-id="930a9-107">14121</span><span class="sxs-lookup"><span data-stu-id="930a9-107">14121</span></span>|  
|<span data-ttu-id="930a9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="930a9-108">Event Source</span></span>|<span data-ttu-id="930a9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="930a9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="930a9-110">组件</span><span class="sxs-lookup"><span data-stu-id="930a9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="930a9-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="930a9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="930a9-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="930a9-112">Message Text</span></span>|<span data-ttu-id="930a9-113">无法删除分发服务器 '%s'。</span><span class="sxs-lookup"><span data-stu-id="930a9-113">Could not drop the Distributor '%s'.</span></span> <span data-ttu-id="930a9-114">此分发服务器与分发数据库相关联。</span><span class="sxs-lookup"><span data-stu-id="930a9-114">This Distributor has associated distribution databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="930a9-115">说明</span><span class="sxs-lookup"><span data-stu-id="930a9-115">Explanation</span></span>  
 <span data-ttu-id="930a9-116">配置为分发服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例无法从分发服务器的角色中删除，因为存在与此实例相关联的分发数据库。</span><span class="sxs-lookup"><span data-stu-id="930a9-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance.</span></span> <span data-ttu-id="930a9-117">如果试图删除与一个或多个发布服务器相关联的分发数据库，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="930a9-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="930a9-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="930a9-118">User Action</span></span>  
 <span data-ttu-id="930a9-119">若要查找与此分发服务器关联的任何发布服务器和分发数据库的名称，请从分发服务器上的任何数据库中执行 [sp_helpdistpublisher (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="930a9-119">To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) from any database on the Distributor.</span></span>  
  
 <span data-ttu-id="930a9-120">对与此分发服务器关联的任何分发数据库，执行 [sp_dropdistributiondb (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="930a9-120">Execute [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) for any distribution databases associated with this Distributor.</span></span> <span data-ttu-id="930a9-121">删除所有分发数据库关联后，才可以禁用分发。</span><span class="sxs-lookup"><span data-stu-id="930a9-121">After all distribution database associations are removed, you can disable distribution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930a9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="930a9-122">See Also</span></span>  
 <span data-ttu-id="930a9-123">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="930a9-123">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="930a9-124">配置分发</span><span class="sxs-lookup"><span data-stu-id="930a9-124">Configure Distribution</span></span>](configure-distribution.md)  
  
  
