---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 36db48ca2a9afd08dadcd12abc13b9978e227b00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588560"
---
# <a name="mssqlserver_8525"></a><span data-ttu-id="b222e-102">MSSQLSERVER_8525</span><span class="sxs-lookup"><span data-stu-id="b222e-102">MSSQLSERVER_8525</span></span>
    
## <a name="details"></a><span data-ttu-id="b222e-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b222e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b222e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b222e-104">Product Name</span></span>|<span data-ttu-id="b222e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b222e-105">SQL Server</span></span>|  
|<span data-ttu-id="b222e-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b222e-106">Event ID</span></span>|<span data-ttu-id="b222e-107">8525</span><span class="sxs-lookup"><span data-stu-id="b222e-107">8525</span></span>|  
|<span data-ttu-id="b222e-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b222e-108">Event Source</span></span>|<span data-ttu-id="b222e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b222e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b222e-110">组件</span><span class="sxs-lookup"><span data-stu-id="b222e-110">Component</span></span>|<span data-ttu-id="b222e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b222e-111">SQLEngine</span></span>|  
|<span data-ttu-id="b222e-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b222e-112">Symbolic Name</span></span>||  
|<span data-ttu-id="b222e-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="b222e-113">Message Text</span></span>|<span data-ttu-id="b222e-114">分布式事务已完成。</span><span class="sxs-lookup"><span data-stu-id="b222e-114">Distributed transaction completed.</span></span> <span data-ttu-id="b222e-115">请将此会话登记到新事务或 NULL 事务中。</span><span class="sxs-lookup"><span data-stu-id="b222e-115">Either enlist this session in a new transaction or the NULL transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b222e-116">说明</span><span class="sxs-lookup"><span data-stu-id="b222e-116">Explanation</span></span>  
 <span data-ttu-id="b222e-117">将分布式事务处理协调器与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配合使用的编程模型需要应用程序显式登记到分布式事务并从中脱离出来。</span><span class="sxs-lookup"><span data-stu-id="b222e-117">The programming model for using the Distributed Transaction Coordinator with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires applications to explicitly enlist to and defect from a distributed transaction.</span></span>  
  
 <span data-ttu-id="b222e-118">满足以下四个条件时会出现此错误：</span><span class="sxs-lookup"><span data-stu-id="b222e-118">This error occurs when the following four conditions are met:</span></span>  
  
-   <span data-ttu-id="b222e-119">应用程序已登记到分布式事务中。</span><span class="sxs-lookup"><span data-stu-id="b222e-119">The application has enlisted into a distributed transaction.</span></span>  
  
-   <span data-ttu-id="b222e-120">无论原因如何，该事务已结束（已提交或回滚）。</span><span class="sxs-lookup"><span data-stu-id="b222e-120">The transaction has ended, either committed or rolled back, for any reason.</span></span>  
  
-   <span data-ttu-id="b222e-121">用户应用程序并未显式地从分布式事务中脱离或显式地登记到新的分布式事务中。</span><span class="sxs-lookup"><span data-stu-id="b222e-121">The user application has not explicitly defected from a distributed transaction or explicitly enlisted into a new distributed transaction.</span></span>  
  
-   <span data-ttu-id="b222e-122">应用程序尝试执行任何脱离现有分布式事务或登记到新的分布式事务以外的事务操作，如发出查询或启动本地事务。</span><span class="sxs-lookup"><span data-stu-id="b222e-122">The application tries to do any transactional operation other than defecting from existing distributed transaction or enlisting to a new distributed transaction, such as issuing a query or starting a local transaction.</span></span>  
  
 <span data-ttu-id="b222e-123">错误状态 1 在应用程序执行创建本地事务的操作时使用，状态 2 在应用程序尝试登记到绑定会话时使用。</span><span class="sxs-lookup"><span data-stu-id="b222e-123">Error state 1 is used when the application performs an operation that creates local transactions, and state 2 is used when application tries to enlist to a bound session.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b222e-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="b222e-124">User Action</span></span>  
 <span data-ttu-id="b222e-125">应用程序登记到分布式事务中之后，应用程序必须显式地从分布式事务中脱离或登记到另一个分布式事务中。</span><span class="sxs-lookup"><span data-stu-id="b222e-125">After an application has enlisted into a distributed transaction, the application must explicitly defect from the distributed transaction or enlist to another distributed transaction.</span></span> <span data-ttu-id="b222e-126">这样将从上一个登记的事务中隐式脱离。</span><span class="sxs-lookup"><span data-stu-id="b222e-126">This will implicitly defect from a previous enlisted transaction.</span></span> <span data-ttu-id="b222e-127">有关从分布式事务脱离或登记到其中的准确语法，请参见该应用程序的编程接口手册。</span><span class="sxs-lookup"><span data-stu-id="b222e-127">For the exact syntax to defect from or enlist to a distributed transaction, see the programming interface manual for the application.</span></span>  
  
  
