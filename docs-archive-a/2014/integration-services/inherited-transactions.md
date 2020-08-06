---
title: 继承的事务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ecb480420fe9f2492c29fad37ee3cc6e6501e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586891"
---
# <a name="inherited-transactions"></a><span data-ttu-id="df7de-102">继承的事务</span><span class="sxs-lookup"><span data-stu-id="df7de-102">Inherited Transactions</span></span>
  <span data-ttu-id="df7de-103">一个包可以使用执行包任务运行另一个包。</span><span class="sxs-lookup"><span data-stu-id="df7de-103">A package can run another package by using the Execute Package task.</span></span> <span data-ttu-id="df7de-104">子包也就是执行包任务所运行的包，它可以创建自己的包事务，也可以继承父包事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-104">The child package, which is the package run by the Execute Package task, may create its own package transaction, or it may inherit the parent package transaction.</span></span>  
  
 <span data-ttu-id="df7de-105">如果同时满足下面这两个条件，则子包会继承父包事务：</span><span class="sxs-lookup"><span data-stu-id="df7de-105">A child package inherits the parent package transaction if both of the following are true:</span></span>  
  
-   <span data-ttu-id="df7de-106">该包由执行包任务调用。</span><span class="sxs-lookup"><span data-stu-id="df7de-106">The package is invoked by an Execute Package task.</span></span>  
  
-   <span data-ttu-id="df7de-107">调用该包的执行包任务同时还联接父包事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-107">The Execute Package task that invoked the package also joined the parent package transaction.</span></span>  
  
 <span data-ttu-id="df7de-108">子包中的容器和任务无法联接父包事务，除非子包本身联接该事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-108">Containers and tasks in the child package cannot join the parent package transaction unless the child package itself joins the transaction.</span></span>  
  
## <a name="illustration-of-package-transactions"></a><span data-ttu-id="df7de-109">包事务的说明</span><span class="sxs-lookup"><span data-stu-id="df7de-109">Illustration of Package Transactions</span></span>  
 <span data-ttu-id="df7de-110">在下面的关系图中，三个包都使用事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-110">In the following diagram, there are three packages that all use transactions.</span></span> <span data-ttu-id="df7de-111">每个包包含多项任务。</span><span class="sxs-lookup"><span data-stu-id="df7de-111">Each package contains multiple tasks.</span></span> <span data-ttu-id="df7de-112">为了强调事务的行为，只显示了执行包任务。</span><span class="sxs-lookup"><span data-stu-id="df7de-112">To emphasize the behavior of the transactions, only the Execute Package tasks are shown.</span></span> <span data-ttu-id="df7de-113">包 A 运行包 B 和包 C。而包 B 运行包 D 和包 E，包 C 运行包 F。</span><span class="sxs-lookup"><span data-stu-id="df7de-113">Package A runs packages B and C. In turn, package B runs packages D and E, and package C runs package F.</span></span>  
  
 <span data-ttu-id="df7de-114">包和任务具有下列事务属性：</span><span class="sxs-lookup"><span data-stu-id="df7de-114">Packages and tasks have the following transaction attributes:</span></span>  
  
-   <span data-ttu-id="df7de-115">对于包 A 和包 C，**TransactionOption** 设置为 **Required** 。</span><span class="sxs-lookup"><span data-stu-id="df7de-115">**TransactionOption** is set to **Required** on packages A and C</span></span>  
  
-   <span data-ttu-id="df7de-116">对于包 B 和包 D 以及任务执行包 B、执行包 D 和执行包 F，**TransactionOption** 设置为 **Supported** 。</span><span class="sxs-lookup"><span data-stu-id="df7de-116">**TransactionOption** is set to **Supported** on packages B and D, and on the tasks Execute Package B, Execute Package D, and Execute Package F.</span></span>  
  
-   <span data-ttu-id="df7de-117">对于包 E 以及任务执行包 C 和执行包 E，**TransactionOption** 设置为 **NotSupported** 。</span><span class="sxs-lookup"><span data-stu-id="df7de-117">**TransactionOption** is set to **NotSupported** on package E, and on the tasks Execute Package C and Execute Package E.</span></span>  
  
 <span data-ttu-id="df7de-118">![继承事务的流](media/mw-dts-executepack.gif "继承事务的流")</span><span class="sxs-lookup"><span data-stu-id="df7de-118">![Flow of inherited transactions](media/mw-dts-executepack.gif "Flow of inherited transactions")</span></span>  
  
 <span data-ttu-id="df7de-119">只有包 B、包 D 和包 F 可以从它们的父包继承事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-119">Only packages B, D, and F can inherit transactions from their parent packages.</span></span>  
  
 <span data-ttu-id="df7de-120">包 B 和包 D 继承包 A 启动的事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-120">Packages B and D inherit the transaction that was started by package A.</span></span>  
  
 <span data-ttu-id="df7de-121">包 F 继承包 C 启动的事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-121">Package F inherits the transaction that was started by package C.</span></span>  
  
 <span data-ttu-id="df7de-122">包 A 和包 C 控制它们自己的事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-122">Packages A and C control their own transactions.</span></span>  
  
 <span data-ttu-id="df7de-123">包 E 不使用事务。</span><span class="sxs-lookup"><span data-stu-id="df7de-123">Package E does not use transactions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="df7de-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="df7de-124">Related Tasks</span></span>  
 [<span data-ttu-id="df7de-125">将包配置为使用事务</span><span class="sxs-lookup"><span data-stu-id="df7de-125">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
