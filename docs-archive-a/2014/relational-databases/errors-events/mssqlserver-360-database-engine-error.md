---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b30311d7f55231c1e7a6d5969d49c5d1bc07a848
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580770"
---
# <a name="mssqlserver_360"></a><span data-ttu-id="bae61-102">MSSQLSERVER_360</span><span class="sxs-lookup"><span data-stu-id="bae61-102">MSSQLSERVER_360</span></span>
    
## <a name="details"></a><span data-ttu-id="bae61-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="bae61-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bae61-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="bae61-104">Product Name</span></span>|<span data-ttu-id="bae61-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bae61-105">SQL Server</span></span>|  
|<span data-ttu-id="bae61-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="bae61-106">Event ID</span></span>|<span data-ttu-id="bae61-107">360</span><span class="sxs-lookup"><span data-stu-id="bae61-107">360</span></span>|  
|<span data-ttu-id="bae61-108">事件源</span><span class="sxs-lookup"><span data-stu-id="bae61-108">Event Source</span></span>|<span data-ttu-id="bae61-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bae61-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bae61-110">组件</span><span class="sxs-lookup"><span data-stu-id="bae61-110">Component</span></span>|<span data-ttu-id="bae61-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bae61-111">SQLEngine</span></span>|  
|<span data-ttu-id="bae61-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="bae61-112">Symbolic Name</span></span>|<span data-ttu-id="bae61-113">DML_UPDATE_SPARSE_AND_COLSET</span><span class="sxs-lookup"><span data-stu-id="bae61-113">DML_UPDATE_SPARSE_AND_COLSET</span></span>|  
|<span data-ttu-id="bae61-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="bae61-114">Message Text</span></span>|<span data-ttu-id="bae61-115">INSERT、UPDATE 或 MERGE 语句的目标列列表不能同时包含稀疏列和包含稀疏列的列集。</span><span class="sxs-lookup"><span data-stu-id="bae61-115">The target column list of an INSERT, UPDATE, or MERGE statement cannot contain both a sparse column and the column set that contains the sparse column.</span></span> <span data-ttu-id="bae61-116">请重写该语句以包括稀疏列或列集，但不能同时包括这两者。</span><span class="sxs-lookup"><span data-stu-id="bae61-116">Rewrite the statement to include either the sparse column or the column set, but not both.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bae61-117">说明</span><span class="sxs-lookup"><span data-stu-id="bae61-117">Explanation</span></span>  
 <span data-ttu-id="bae61-118">列集是一种非类型化的 XML 表示形式，它将表的某些列组合成为结构化的输出。</span><span class="sxs-lookup"><span data-stu-id="bae61-118">A column set is an untyped XML representation that combines some columns of a table into a structured output.</span></span> <span data-ttu-id="bae61-119">由于尝试修改列集和此列集中包含的某个列，导致这二者引用相同的列。</span><span class="sxs-lookup"><span data-stu-id="bae61-119">An attempt was made to modify both the column set and a column that is included in the column set, causing two references to the same column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bae61-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="bae61-120">User Action</span></span>  
 <span data-ttu-id="bae61-121">重写该语句以使其包含对列或列集的引用，但不同时包含对这二者的引用。</span><span class="sxs-lookup"><span data-stu-id="bae61-121">Rewrite the statement to include references to either the column or the column set, but do not include both in the statement.</span></span>  
  
  
