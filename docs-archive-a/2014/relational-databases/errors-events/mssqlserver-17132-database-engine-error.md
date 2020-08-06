---
title: MSSQLSERVER_17132 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 609b9cea138db15cefd002f494620b5a1da7b208
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689410"
---
# <a name="mssqlserver_17132"></a><span data-ttu-id="2da7f-102">MSSQLSERVER_17132</span><span class="sxs-lookup"><span data-stu-id="2da7f-102">MSSQLSERVER_17132</span></span>
    
## <a name="details"></a><span data-ttu-id="2da7f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2da7f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2da7f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2da7f-104">Product Name</span></span>|<span data-ttu-id="2da7f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2da7f-105">SQL Server</span></span>|  
|<span data-ttu-id="2da7f-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2da7f-106">Event ID</span></span>|<span data-ttu-id="2da7f-107">17132</span><span class="sxs-lookup"><span data-stu-id="2da7f-107">17132</span></span>|  
|<span data-ttu-id="2da7f-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2da7f-108">Event Source</span></span>|<span data-ttu-id="2da7f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2da7f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2da7f-110">组件</span><span class="sxs-lookup"><span data-stu-id="2da7f-110">Component</span></span>|<span data-ttu-id="2da7f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2da7f-111">SQLEngine</span></span>|  
|<span data-ttu-id="2da7f-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2da7f-112">Symbolic Name</span></span>|<span data-ttu-id="2da7f-113">INIT_NODESSPACE</span><span class="sxs-lookup"><span data-stu-id="2da7f-113">INIT_NODESSPACE</span></span>|  
|<span data-ttu-id="2da7f-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2da7f-114">Message Text</span></span>|<span data-ttu-id="2da7f-115">由于没有足够的内存可用于描述符，导致服务器启动失败。</span><span class="sxs-lookup"><span data-stu-id="2da7f-115">Server startup failed due to insufficient memory for descriptor.</span></span> <span data-ttu-id="2da7f-116">请减少不重要的内存负载或增加系统内存。</span><span class="sxs-lookup"><span data-stu-id="2da7f-116">Reduce non-essential memory load or increase system memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2da7f-117">说明</span><span class="sxs-lookup"><span data-stu-id="2da7f-117">Explanation</span></span>  
 <span data-ttu-id="2da7f-118">无法分配足够的内存来存储服务器内部描述符。</span><span class="sxs-lookup"><span data-stu-id="2da7f-118">Failed to allocate enough memory to store server internal descriptor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2da7f-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="2da7f-119">User Action</span></span>  
 <span data-ttu-id="2da7f-120">在计算机中添加更多内存。</span><span class="sxs-lookup"><span data-stu-id="2da7f-120">Add more memory to the machine.</span></span> <span data-ttu-id="2da7f-121">一般内存故障排除步骤可能会非常有用。</span><span class="sxs-lookup"><span data-stu-id="2da7f-121">Generic memory troubleshooting steps may be useful.</span></span>  
  
  
