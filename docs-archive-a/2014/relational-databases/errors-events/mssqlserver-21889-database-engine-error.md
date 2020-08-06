---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690622"
---
# <a name="mssqlserver_21889"></a><span data-ttu-id="40cb3-102">MSSQLSERVER_21889</span><span class="sxs-lookup"><span data-stu-id="40cb3-102">MSSQLSERVER_21889</span></span>
    
## <a name="details"></a><span data-ttu-id="40cb3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="40cb3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40cb3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="40cb3-104">Product Name</span></span>|<span data-ttu-id="40cb3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="40cb3-105">SQL Server</span></span>|  
|<span data-ttu-id="40cb3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="40cb3-106">Event ID</span></span>|<span data-ttu-id="40cb3-107">21889</span><span class="sxs-lookup"><span data-stu-id="40cb3-107">21889</span></span>|  
|<span data-ttu-id="40cb3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="40cb3-108">Event Source</span></span>|<span data-ttu-id="40cb3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="40cb3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="40cb3-110">组件</span><span class="sxs-lookup"><span data-stu-id="40cb3-110">Component</span></span>|<span data-ttu-id="40cb3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="40cb3-111">SQLEngine</span></span>|  
|<span data-ttu-id="40cb3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="40cb3-112">Symbolic Name</span></span>|<span data-ttu-id="40cb3-113">SQLErrorNum21889</span><span class="sxs-lookup"><span data-stu-id="40cb3-113">SQLErrorNum21889</span></span>|  
|<span data-ttu-id="40cb3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="40cb3-114">Message Text</span></span>|<span data-ttu-id="40cb3-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例“%s”不是复制发布服务器。</span><span class="sxs-lookup"><span data-stu-id="40cb3-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' is not a replication publisher.</span></span> <span data-ttu-id="40cb3-116">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例“%s”（具有分发服务器“%s”）上运行 `sp_adddistributor`，以便使该实例承载发布数据库“%s”。</span><span class="sxs-lookup"><span data-stu-id="40cb3-116">Run `sp_adddistributor` on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' with distributor '%s' in order to enable the instance to host the publishing database '%s'.</span></span> <span data-ttu-id="40cb3-117">确保指定的登录名和密码与用于原始发布服务器的登录名和密码相同。</span><span class="sxs-lookup"><span data-stu-id="40cb3-117">Make certain to specify the same login and password as that used for the original publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="40cb3-118">说明</span><span class="sxs-lookup"><span data-stu-id="40cb3-118">Explanation</span></span>  
 <span data-ttu-id="40cb3-119">为了承载发布服务器数据库，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例必须为复制发布服务器。</span><span class="sxs-lookup"><span data-stu-id="40cb3-119">In order to host the publisher database, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be a replication publisher.</span></span> <span data-ttu-id="40cb3-120">在远程服务器上，`sp_validate_redirected_publisher` 调用 `sp_helpdistributor`，以确定该服务器是否为复制发布服务器。</span><span class="sxs-lookup"><span data-stu-id="40cb3-120">`sp_validate_redirected_publisher` calls `sp_helpdistributor` at the remote server to determine whether the server is a replication publisher.</span></span> <span data-ttu-id="40cb3-121">如果执行存储过程 `sp_helpdistributor` 时指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的目标实例不是复制发布服务器，则会返回该错误。</span><span class="sxs-lookup"><span data-stu-id="40cb3-121">This error is returned when execution of the stored procedure `sp_helpdistributor` indicates that the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not a replication publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="40cb3-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="40cb3-122">User Action</span></span>  
 <span data-ttu-id="40cb3-123">在承载发布服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上执行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="40cb3-123">Execute `sp_adddistributor` at the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the publisher database.</span></span> <span data-ttu-id="40cb3-124">在运行 `sp_adddistributor` 时，指定正确的分发服务器。</span><span class="sxs-lookup"><span data-stu-id="40cb3-124">When running `sp_adddistributor`, specify the correct distributor.</span></span> <span data-ttu-id="40cb3-125">使用与 *@password* `sp_adddistributor` 最初在分发服务器上运行时使用的参数相同的值。</span><span class="sxs-lookup"><span data-stu-id="40cb3-125">Use the same value for the *@password* parameter as that used when `sp_adddistributor` was initially run at the distributor.</span></span>  
  
  
