---
title: MSSQLSERVER_12304 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2347fc46fe5ab83ef2ff46b81500cd737ed02d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587858"
---
# <a name="mssqlserver_12304"></a><span data-ttu-id="e44aa-102">MSSQLSERVER_12304</span><span class="sxs-lookup"><span data-stu-id="e44aa-102">MSSQLSERVER_12304</span></span>
    
## <a name="details"></a><span data-ttu-id="e44aa-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e44aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e44aa-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e44aa-104">Product Name</span></span>|<span data-ttu-id="e44aa-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e44aa-105">SQL Server</span></span>|  
|<span data-ttu-id="e44aa-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e44aa-106">Event ID</span></span>|<span data-ttu-id="e44aa-107">12304</span><span class="sxs-lookup"><span data-stu-id="e44aa-107">12304</span></span>|  
|<span data-ttu-id="e44aa-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e44aa-108">Event Source</span></span>|<span data-ttu-id="e44aa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e44aa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e44aa-110">组件</span><span class="sxs-lookup"><span data-stu-id="e44aa-110">Component</span></span>|<span data-ttu-id="e44aa-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e44aa-111">SQLEngine</span></span>|  
|<span data-ttu-id="e44aa-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e44aa-112">Symbolic Name</span></span>|<span data-ttu-id="e44aa-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span><span class="sxs-lookup"><span data-stu-id="e44aa-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span></span>|  
|<span data-ttu-id="e44aa-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e44aa-114">Message Text</span></span>|<span data-ttu-id="e44aa-115">在本机编译的存储过程外部使用内存优化表类型时，如果该类型对表的任意列使用 IDENTITY 属性，则该类型不受支持。</span><span class="sxs-lookup"><span data-stu-id="e44aa-115">Using a memory optimized table type that uses the IDENTITY property with any of its columns is not supported when using the type outside the context of a natively compiled stored procedure.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="e44aa-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="e44aa-116">User Action</span></span>  
 <span data-ttu-id="e44aa-117">切勿使用对任意表列使用 identity 属性的内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="e44aa-117">Do not use a memory-optimized table type that uses the identity property with any of its columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44aa-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e44aa-118">See Also</span></span>  
 [<span data-ttu-id="e44aa-119">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="e44aa-119">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
