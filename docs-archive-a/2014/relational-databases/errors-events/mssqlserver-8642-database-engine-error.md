---
title: MSSQLSERVER_8642 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30296fa569599b91ca74edc7535d330119e1680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588555"
---
# <a name="mssqlserver_8642"></a><span data-ttu-id="59c99-102">MSSQLSERVER_8642</span><span class="sxs-lookup"><span data-stu-id="59c99-102">MSSQLSERVER_8642</span></span>
    
## <a name="details"></a><span data-ttu-id="59c99-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="59c99-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59c99-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="59c99-104">Product Name</span></span>|<span data-ttu-id="59c99-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="59c99-105">SQL Server</span></span>|  
|<span data-ttu-id="59c99-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="59c99-106">Event ID</span></span>|<span data-ttu-id="59c99-107">8642</span><span class="sxs-lookup"><span data-stu-id="59c99-107">8642</span></span>|  
|<span data-ttu-id="59c99-108">事件源</span><span class="sxs-lookup"><span data-stu-id="59c99-108">Event Source</span></span>|<span data-ttu-id="59c99-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="59c99-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="59c99-110">组件</span><span class="sxs-lookup"><span data-stu-id="59c99-110">Component</span></span>|<span data-ttu-id="59c99-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="59c99-111">SQLEngine</span></span>|  
|<span data-ttu-id="59c99-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="59c99-112">Symbolic Name</span></span>|<span data-ttu-id="59c99-113">EXCHNGSTART_ERR</span><span class="sxs-lookup"><span data-stu-id="59c99-113">EXCHNGSTART_ERR</span></span>|  
|<span data-ttu-id="59c99-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="59c99-114">Message Text</span></span>|<span data-ttu-id="59c99-115">查询处理器未能为执行并行查询启动必要的线程资源。</span><span class="sxs-lookup"><span data-stu-id="59c99-115">The query processor could not start the necessary thread resources for parallel query execution.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59c99-116">说明</span><span class="sxs-lookup"><span data-stu-id="59c99-116">Explanation</span></span>  
 <span data-ttu-id="59c99-117">服务器中的线程资源不足。</span><span class="sxs-lookup"><span data-stu-id="59c99-117">Thread resources are low in the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59c99-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="59c99-118">User Action</span></span>  
 <span data-ttu-id="59c99-119">减少服务器上的负载，然后重新运行查询。</span><span class="sxs-lookup"><span data-stu-id="59c99-119">Reduce load on the server, and run the query again.</span></span>  
  
  
