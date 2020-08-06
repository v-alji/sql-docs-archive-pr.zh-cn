---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689387"
---
# <a name="mssqlserver_3937"></a><span data-ttu-id="29ebc-102">MSSQLSERVER_3937</span><span class="sxs-lookup"><span data-stu-id="29ebc-102">MSSQLSERVER_3937</span></span>
    
## <a name="details"></a><span data-ttu-id="29ebc-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="29ebc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29ebc-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="29ebc-104">Product Name</span></span>|<span data-ttu-id="29ebc-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29ebc-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29ebc-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="29ebc-106">Event ID</span></span>|<span data-ttu-id="29ebc-107">3937</span><span class="sxs-lookup"><span data-stu-id="29ebc-107">3937</span></span>|  
|<span data-ttu-id="29ebc-108">事件源</span><span class="sxs-lookup"><span data-stu-id="29ebc-108">Event Source</span></span>|<span data-ttu-id="29ebc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29ebc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29ebc-110">组件</span><span class="sxs-lookup"><span data-stu-id="29ebc-110">Component</span></span>|<span data-ttu-id="29ebc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29ebc-111">SQLEngine</span></span>|  
|<span data-ttu-id="29ebc-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="29ebc-112">Symbolic Name</span></span>|<span data-ttu-id="29ebc-113">XACT_FILESTREAM_ROLLBACK_ERROR</span><span class="sxs-lookup"><span data-stu-id="29ebc-113">XACT_FILESTREAM_ROLLBACK_ERROR</span></span>|  
|<span data-ttu-id="29ebc-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="29ebc-114">Message Text</span></span>|<span data-ttu-id="29ebc-115">在试图通知 FILESTREAM 筛选器驱动程序某事务已回滚时出错。</span><span class="sxs-lookup"><span data-stu-id="29ebc-115">An error occurred while trying to notify the FILESTREAM filter driver that a transaction was rolled back.</span></span> <span data-ttu-id="29ebc-116">错误代码:0x%0x。</span><span class="sxs-lookup"><span data-stu-id="29ebc-116">Error code: 0x%0x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29ebc-117">说明</span><span class="sxs-lookup"><span data-stu-id="29ebc-117">Explanation</span></span>  
 <span data-ttu-id="29ebc-118">发出有关某事务的回滚通知时，RsFx 驱动程序返回错误。</span><span class="sxs-lookup"><span data-stu-id="29ebc-118">An error was returned by the RsFx driver when issuing a rollback notification for a transaction.</span></span> <span data-ttu-id="29ebc-119">这可能是因资源不足而造成的。</span><span class="sxs-lookup"><span data-stu-id="29ebc-119">This is probably caused by a resource shortage.</span></span> <span data-ttu-id="29ebc-120">这可能会导致 RsFx 筛选器驱动程序发生少量内存泄漏，但是，如果存在创建事务的 sqlservr.exe 进程，则可能不会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="29ebc-120">This can cause a small memory leak in the RsFx filter driver, but this will be freed when the sqlservr.exe process that created the transaction exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29ebc-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="29ebc-121">User Action</span></span>  
  
