---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0caa1c218e8b80059c0c97aac652da7db870af3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590850"
---
# <a name="mssqlserver_611"></a><span data-ttu-id="63f2c-102">MSSQLSERVER_611</span><span class="sxs-lookup"><span data-stu-id="63f2c-102">MSSQLSERVER_611</span></span>
    
## <a name="details"></a><span data-ttu-id="63f2c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="63f2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63f2c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="63f2c-104">Product Name</span></span>|<span data-ttu-id="63f2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="63f2c-105">SQL Server</span></span>|  
|<span data-ttu-id="63f2c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="63f2c-106">Event ID</span></span>|<span data-ttu-id="63f2c-107">611</span><span class="sxs-lookup"><span data-stu-id="63f2c-107">611</span></span>|  
|<span data-ttu-id="63f2c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="63f2c-108">Event Source</span></span>|<span data-ttu-id="63f2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="63f2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="63f2c-110">组件</span><span class="sxs-lookup"><span data-stu-id="63f2c-110">Component</span></span>|<span data-ttu-id="63f2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="63f2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="63f2c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="63f2c-112">Symbolic Name</span></span>|<span data-ttu-id="63f2c-113">VAR_SIZE_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="63f2c-113">VAR_SIZE_TOO_BIG</span></span>|  
|<span data-ttu-id="63f2c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="63f2c-114">Message Text</span></span>|<span data-ttu-id="63f2c-115">无法插入或更新行，因为总可变列大小(包括系统开销)比限值多出 %d 个字节。</span><span class="sxs-lookup"><span data-stu-id="63f2c-115">Cannot insert or update a row because total variable column size, including overhead, is %d bytes more than the limit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63f2c-116">说明</span><span class="sxs-lookup"><span data-stu-id="63f2c-116">Explanation</span></span>  
 <span data-ttu-id="63f2c-117">最大可变列大小超过架构所允许的大小。</span><span class="sxs-lookup"><span data-stu-id="63f2c-117">The maximum variable column size is more than that allowed by the schema.</span></span> <span data-ttu-id="63f2c-118">当可变列超过启用 vardecimal 存储格式时的固定列大小限制，或可变列大小超过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 对压缩数据记录所允许的限制时，将返回错误 611。</span><span class="sxs-lookup"><span data-stu-id="63f2c-118">Error 611 is returned when the variable column is over the limit in the fixed case when vardecimal storage format is enabled, or when the variable column size is over the limit allowed in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for a compressed data record.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63f2c-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="63f2c-119">User Action</span></span>  
 <span data-ttu-id="63f2c-120">减小记录的大小。</span><span class="sxs-lookup"><span data-stu-id="63f2c-120">Reduce the size of the record.</span></span>  
  
  
