---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34414754ea9d25ad89f6aba767197eb1dfc10d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586727"
---
# <a name="mssqlserver_3151"></a><span data-ttu-id="f06a1-102">MSSQLSERVER_3151</span><span class="sxs-lookup"><span data-stu-id="f06a1-102">MSSQLSERVER_3151</span></span>
    
## <a name="details"></a><span data-ttu-id="f06a1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f06a1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f06a1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f06a1-104">Product Name</span></span>|<span data-ttu-id="f06a1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f06a1-105">SQL Server</span></span>|  
|<span data-ttu-id="f06a1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f06a1-106">Event ID</span></span>|<span data-ttu-id="f06a1-107">3151</span><span class="sxs-lookup"><span data-stu-id="f06a1-107">3151</span></span>|  
|<span data-ttu-id="f06a1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f06a1-108">Event Source</span></span>|<span data-ttu-id="f06a1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f06a1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f06a1-110">组件</span><span class="sxs-lookup"><span data-stu-id="f06a1-110">Component</span></span>|<span data-ttu-id="f06a1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f06a1-111">SQLEngine</span></span>|  
|<span data-ttu-id="f06a1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f06a1-112">Symbolic Name</span></span>|<span data-ttu-id="f06a1-113">LDDB_MASTER_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="f06a1-113">LDDB_MASTER_LOAD_FAILED</span></span>|  
|<span data-ttu-id="f06a1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f06a1-114">Message Text</span></span>|<span data-ttu-id="f06a1-115">无法还原 master 数据库。</span><span class="sxs-lookup"><span data-stu-id="f06a1-115">Failed to restore master database.</span></span> <span data-ttu-id="f06a1-116">正在关闭 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="f06a1-116">Shutting down SQL Server.</span></span> <span data-ttu-id="f06a1-117">请检查错误日志，然后重新生成 master 数据库。</span><span class="sxs-lookup"><span data-stu-id="f06a1-117">Check the error logs, and rebuild the master database.</span></span> <span data-ttu-id="f06a1-118">有关如何重新生成 master 数据库的详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="f06a1-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f06a1-119">说明</span><span class="sxs-lookup"><span data-stu-id="f06a1-119">Explanation</span></span>  
 <span data-ttu-id="f06a1-120">这是一般的错误消息，指示 **master** 数据库存在各种问题。</span><span class="sxs-lookup"><span data-stu-id="f06a1-120">This is a general error message indicating various problems with the **master** database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f06a1-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="f06a1-121">User Action</span></span>  
 <span data-ttu-id="f06a1-122">检查错误日志以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="f06a1-122">Check the error logs for more information.</span></span> <span data-ttu-id="f06a1-123">若要创建可用的 **master** 数据库，请使用 REBUILDDATABASE 选项运行 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="f06a1-123">To create a usable **master** database, run Setup.exe with the REBUILDDATABASE option.</span></span> <span data-ttu-id="f06a1-124">有关详细信息，请参阅“如何：从命令提示符安装 SQL Server”，位于 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="f06a1-124">For more information see "How to: Install SQL Server from the Command Prompt" in SQL Server Books Online.</span></span>  
  
  
