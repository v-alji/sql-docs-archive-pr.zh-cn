---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 261d352084e490fb7f9216e1a7e352542e85a6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581273"
---
# <a name="mssqlserver_1807"></a><span data-ttu-id="51d89-102">MSSQLSERVER_1807</span><span class="sxs-lookup"><span data-stu-id="51d89-102">MSSQLSERVER_1807</span></span>
    
## <a name="details"></a><span data-ttu-id="51d89-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="51d89-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51d89-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="51d89-104">Product Name</span></span>|<span data-ttu-id="51d89-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="51d89-105">SQL Server</span></span>|  
|<span data-ttu-id="51d89-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="51d89-106">Event ID</span></span>|<span data-ttu-id="51d89-107">1807</span><span class="sxs-lookup"><span data-stu-id="51d89-107">1807</span></span>|  
|<span data-ttu-id="51d89-108">事件源</span><span class="sxs-lookup"><span data-stu-id="51d89-108">Event Source</span></span>|<span data-ttu-id="51d89-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="51d89-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="51d89-110">组件</span><span class="sxs-lookup"><span data-stu-id="51d89-110">Component</span></span>|<span data-ttu-id="51d89-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="51d89-111">SQLEngine</span></span>|  
|<span data-ttu-id="51d89-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="51d89-112">Symbolic Name</span></span>|<span data-ttu-id="51d89-113">CANNOT_EX_LOCK</span><span class="sxs-lookup"><span data-stu-id="51d89-113">CANNOT_EX_LOCK</span></span>|  
|<span data-ttu-id="51d89-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="51d89-114">Message Text</span></span>|<span data-ttu-id="51d89-115">无法获得数据库 '%.\*ls' 上的排他锁。</span><span class="sxs-lookup"><span data-stu-id="51d89-115">Could not obtain exclusive lock on database '%.\*ls'.</span></span> <span data-ttu-id="51d89-116">请稍后重试该操作。</span><span class="sxs-lookup"><span data-stu-id="51d89-116">Retry the operation later.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="51d89-117">说明</span><span class="sxs-lookup"><span data-stu-id="51d89-117">Explanation</span></span>  
 <span data-ttu-id="51d89-118">需要对数据库进行排他访问的操作无法获取它。</span><span class="sxs-lookup"><span data-stu-id="51d89-118">An operation that required exclusive access to the database was unable to obtain it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="51d89-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="51d89-119">User Action</span></span>  
 <span data-ttu-id="51d89-120">断开与该数据库的所有连接，或者稍后重试查询。</span><span class="sxs-lookup"><span data-stu-id="51d89-120">Disconnect all the connections to that database or try the query again later.</span></span>  
  
  
