---
title: 多个事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ff909c92a23c965047edc0fcf278e17e4c76d94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586796"
---
# <a name="multiple-transactions"></a><span data-ttu-id="c16b2-102">多个事务</span><span class="sxs-lookup"><span data-stu-id="c16b2-102">Multiple Transactions</span></span>
  <span data-ttu-id="c16b2-103">包可以在一个 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包中包含不相关的事务。</span><span class="sxs-lookup"><span data-stu-id="c16b2-103">It is possible for a package to include unrelated transactions in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="c16b2-104">无论任何时候，位于嵌套容器层次结构中间的容器都不支持事务，位于层次结构中其他位置的容器如果配置为支持事务，则它们将启动单独的事务。</span><span class="sxs-lookup"><span data-stu-id="c16b2-104">Any time a container in the middle of a nested container hierarchy does not support transactions, the containers above or below it in the hierarchy start separate transactions if they are configured to support transactions.</span></span> <span data-ttu-id="c16b2-105">事务按照从嵌套容器层次结构中最里面的任务到包这个顺序来提交或回滚。</span><span class="sxs-lookup"><span data-stu-id="c16b2-105">The transactions commit or roll back in order from the innermost task in the nested container hierarchy to the package.</span></span> <span data-ttu-id="c16b2-106">但是，在内部事务提交后，如果外部事务中止，已提交的事务不会回滚。</span><span class="sxs-lookup"><span data-stu-id="c16b2-106">However, after the inner transaction commits, it does not roll back if an outer transaction is aborted.</span></span>

## <a name="illustration-of-multiple-transactions"></a><span data-ttu-id="c16b2-107">多个事务的说明</span><span class="sxs-lookup"><span data-stu-id="c16b2-107">Illustration of Multiple Transactions</span></span>
 <span data-ttu-id="c16b2-108">例如，某个包包含一个序列容器，该序列容器中又存储有两个 Foreach 循环容器，而后面这两个容器中又分别包含两个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="c16b2-108">For example, a package has a Sequence container that holds two Foreach Loop containers, and each container include two Execute SQL tasks.</span></span> <span data-ttu-id="c16b2-109">序列容器支持事务，而 Foreach 循环容器则不支持事务，但执行 SQL 任务支持。</span><span class="sxs-lookup"><span data-stu-id="c16b2-109">The Sequence container supports transactions, the Foreach Loop containers do not, and the Execute SQL tasks do.</span></span> <span data-ttu-id="c16b2-110">在此示例中，每个执行 SQL 任务都将启动自己的事务，如果序列任务上的事务被中止，则执行 SQL 任务将不会回滚。</span><span class="sxs-lookup"><span data-stu-id="c16b2-110">In this example, each Execute SQL task would start its own transaction and would not roll back if the transaction on the Sequence task was aborted.</span></span>

 <span data-ttu-id="c16b2-111">序列容器、Foreach 循环容器和执行 SQL 任务的 TransactionOption 属性按照如下方式进行设置：</span><span class="sxs-lookup"><span data-stu-id="c16b2-111">The TransactionOption properties of the Sequence container, Foreach Loop container and the Execute SQL tasks are set as follows:</span></span>

-   <span data-ttu-id="c16b2-112">序列容器的 TransactionOption 属性设置为 **Required**。</span><span class="sxs-lookup"><span data-stu-id="c16b2-112">The TransactionOption property of the Sequence container is set to **Required**.</span></span>

-   <span data-ttu-id="c16b2-113">Foreach 循环容器的 TransactionOption 属性设置为 **NotSupported**。</span><span class="sxs-lookup"><span data-stu-id="c16b2-113">The TransactionOption properties of the Foreach Loop containers are set to **NotSupported**.</span></span>

-   <span data-ttu-id="c16b2-114">执行 SQL 任务的 TransactionOption 属性设置为 **Required**。</span><span class="sxs-lookup"><span data-stu-id="c16b2-114">The TransactionOption properties of the Execute SQL tasks are set to **Required**.</span></span>

 <span data-ttu-id="c16b2-115">下面的关系图显示了包中的五个不相关的事务。</span><span class="sxs-lookup"><span data-stu-id="c16b2-115">The following diagram shows the five unrelated transactions in the package.</span></span> <span data-ttu-id="c16b2-116">一个事务是由序列容器启动的，其余四个事务是由执行 SQL 任务启动的。</span><span class="sxs-lookup"><span data-stu-id="c16b2-116">One transaction is started by the Sequence container and four transactions are started by the Execute SQL tasks.</span></span>

 <span data-ttu-id="c16b2-117">![多个事务的实现](media/mw-dts-trans2.gif "多个事务的实现")</span><span class="sxs-lookup"><span data-stu-id="c16b2-117">![Implementation of multiple transactions](media/mw-dts-trans2.gif "Implementation of multiple transactions")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="c16b2-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c16b2-118">Related Tasks</span></span>
 [<span data-ttu-id="c16b2-119">将包配置为使用事务</span><span class="sxs-lookup"><span data-stu-id="c16b2-119">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)


