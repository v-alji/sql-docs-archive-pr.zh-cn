---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4249e13a3530f69978c78f2e2ca6e4583eed46a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577731"
---
# <a name="mssqlserver_11409"></a><span data-ttu-id="b6e6f-102">MSSQLSERVER_11409</span><span class="sxs-lookup"><span data-stu-id="b6e6f-102">MSSQLSERVER_11409</span></span>
    
## <a name="details"></a><span data-ttu-id="b6e6f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b6e6f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6e6f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b6e6f-104">Product Name</span></span>|<span data-ttu-id="b6e6f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6e6f-105">SQL Server</span></span>|  
|<span data-ttu-id="b6e6f-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b6e6f-106">Event ID</span></span>|<span data-ttu-id="b6e6f-107">11409</span><span class="sxs-lookup"><span data-stu-id="b6e6f-107">11409</span></span>|  
|<span data-ttu-id="b6e6f-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b6e6f-108">Event Source</span></span>|<span data-ttu-id="b6e6f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b6e6f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b6e6f-110">组件</span><span class="sxs-lookup"><span data-stu-id="b6e6f-110">Component</span></span>|<span data-ttu-id="b6e6f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b6e6f-111">SQLEngine</span></span>|  
|<span data-ttu-id="b6e6f-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b6e6f-112">Symbolic Name</span></span>|<span data-ttu-id="b6e6f-113">ALTERCOL_COLSET_DROP</span><span class="sxs-lookup"><span data-stu-id="b6e6f-113">ALTERCOL_COLSET_DROP</span></span>|  
|<span data-ttu-id="b6e6f-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b6e6f-114">Message Text</span></span>|<span data-ttu-id="b6e6f-115">无法删除列集 '%.\*ls' (位于表 '%.\*ls' 中)，因为该表包含的列超过了 1025 列。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-115">Cannot drop column set '%.\*ls' in table '%.\*ls' because the table contains more than 1025 columns.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6e6f-116">说明</span><span class="sxs-lookup"><span data-stu-id="b6e6f-116">Explanation</span></span>  
 <span data-ttu-id="b6e6f-117">表中最多可以包含 1024 个未指定为稀疏列或计算列的列。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-117">Tables can contain a maximum of 1024 columns that are not designated as sparse, or computed.</span></span> <span data-ttu-id="b6e6f-118">如果稀疏列导致表中超过 1024 列，则必须为该表定义一个列集。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-118">When sparse columns cause the table to exceed 1024 columns, a column set must be defined for the table.</span></span> <span data-ttu-id="b6e6f-119">所引用的表超过了 1024 列，而且您已经尝试删除了列集。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-119">The table referenced has more than 1024 columns and you have attempted to remove the column set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6e6f-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="b6e6f-120">User Action</span></span>  
 <span data-ttu-id="b6e6f-121">在表中具有当前列数的情况下，您必须保留列集。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-121">With the current columns in the table, you must retain the column set.</span></span>  
  
 <span data-ttu-id="b6e6f-122">若要删除列集，请首先从表中删除某些列，直到列数不超过 1024 列。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-122">To remove the column set, first remove columns from the table, until you have no more than 1024 columns.</span></span> <span data-ttu-id="b6e6f-123">随后即可以删除列集。</span><span class="sxs-lookup"><span data-stu-id="b6e6f-123">Then, you can remove the column set.</span></span>  
  
  
