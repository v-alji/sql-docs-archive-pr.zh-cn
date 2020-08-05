---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34ebc7c682d2ffe8bc0205565f5dfd44fdd5b66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581229"
---
# <a name="mssqlserver_9532"></a><span data-ttu-id="60644-102">MSSQLSERVER_9532</span><span class="sxs-lookup"><span data-stu-id="60644-102">MSSQLSERVER_9532</span></span>
    
## <a name="details"></a><span data-ttu-id="60644-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="60644-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60644-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="60644-104">Product Name</span></span>|<span data-ttu-id="60644-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="60644-105">SQL Server</span></span>|  
|<span data-ttu-id="60644-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60644-106">Event ID</span></span>|<span data-ttu-id="60644-107">9532</span><span class="sxs-lookup"><span data-stu-id="60644-107">9532</span></span>|  
|<span data-ttu-id="60644-108">事件源</span><span class="sxs-lookup"><span data-stu-id="60644-108">Event Source</span></span>|<span data-ttu-id="60644-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="60644-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="60644-110">组件</span><span class="sxs-lookup"><span data-stu-id="60644-110">Component</span></span>|<span data-ttu-id="60644-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="60644-111">SQLEngine</span></span>|  
|<span data-ttu-id="60644-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="60644-112">Symbolic Name</span></span>|<span data-ttu-id="60644-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span><span class="sxs-lookup"><span data-stu-id="60644-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span></span>|  
|<span data-ttu-id="60644-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="60644-114">Message Text</span></span>|<span data-ttu-id="60644-115">在涉及列集 '%.\*ls' 的查询/DML 操作中，将列 '%.\*ls' 从数据类型 '%ls' 转换为数据类型 '%ls' 时转换失败。</span><span class="sxs-lookup"><span data-stu-id="60644-115">In the query/DML operation involving  column set '%.\*ls', conversion failed when converting from the data type '%ls' to the data type '%ls' for the column '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="60644-116">说明</span><span class="sxs-lookup"><span data-stu-id="60644-116">Explanation</span></span>  
 <span data-ttu-id="60644-117">列集是一种非类型化的 XML 表示形式，它将表的某些列组合成为结构化的输出。</span><span class="sxs-lookup"><span data-stu-id="60644-117">A column set is an untyped XML representation that combines some of the columns of a table into a structured output.</span></span> <span data-ttu-id="60644-118">通过 XML 列集插入或更新稀疏列值时，插入基础稀疏列的值从 `xml` 数据类型隐式转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="60644-118">When you are inserting or updating sparse column values through the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="60644-119">所提供的值无法转换为列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="60644-119">A value was provided that cannot be converted to the data type of the column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60644-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="60644-120">User Action</span></span>  
 <span data-ttu-id="60644-121">由于无法对提供的值进行隐式转换，因此该值可能是一个无效项。</span><span class="sxs-lookup"><span data-stu-id="60644-121">Because the value provided could not be implicitly converted, it might be an invalid entry.</span></span> <span data-ttu-id="60644-122">更正该错误，然后重试。</span><span class="sxs-lookup"><span data-stu-id="60644-122">Correct the error and retry.</span></span> <span data-ttu-id="60644-123">如果该值正确，修改该语句以使用单个列而不使用列集。</span><span class="sxs-lookup"><span data-stu-id="60644-123">If the value is correct, modify the statement to use the individual columns instead of the column set.</span></span> <span data-ttu-id="60644-124">通过此操作可将该值显式转换为正确的数据类型。</span><span class="sxs-lookup"><span data-stu-id="60644-124">This will allow you to explicitly cast the value into the correct data type.</span></span>  
  
  
