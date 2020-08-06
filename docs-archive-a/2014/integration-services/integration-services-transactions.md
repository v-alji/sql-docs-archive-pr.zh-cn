---
title: Integration Services 事务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586852"
---
# <a name="integration-services-transactions"></a><span data-ttu-id="f89ab-102">Integration Services 事务</span><span class="sxs-lookup"><span data-stu-id="f89ab-102">Integration Services Transactions</span></span>
  <span data-ttu-id="f89ab-103">包使用事务将任务执行的数据库操作绑定到原子单元中，这样做可以维护数据的完整性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-103">Packages use transactions to bind the database actions that tasks perform into atomic units, and by doing this maintain data integrity.</span></span> <span data-ttu-id="f89ab-104">所有 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 容器类型（包、For 循环、Foreach 循环和序列容器以及封装每个任务的任务宿主）都可以配置为使用事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-104">All [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types-packages, the For Loop, Foreach Loop, and Sequence containers, and the task hosts that encapsulate each task-can be configured to use transactions.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="f89ab-105">提供了三个用于配置事务的选项： **NotSupported**、 **Supported**和 **Required**。</span><span class="sxs-lookup"><span data-stu-id="f89ab-105">provides three options for configuring transactions: **NotSupported**, **Supported**, and **Required**.</span></span>  
  
-   <span data-ttu-id="f89ab-106">**Required** 指示该容器启动一个事务，除非已经存在由其父容器启动的事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-106">**Required** indicates that the container starts a transaction, unless one is already started by its parent container.</span></span> <span data-ttu-id="f89ab-107">如果事务已经存在，容器将联接该事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-107">If a transaction already exists, the container joins the transaction.</span></span> <span data-ttu-id="f89ab-108">例如，如果没有配置为支持事务的包包括一个使用 **Required** 选项的序列容器，则该序列容器会启动其自己的事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-108">For example, if a package that is not configured to support transactions includes a Sequence container that uses the **Required** option, the Sequence container would start its own transaction.</span></span> <span data-ttu-id="f89ab-109">如果包已经配置为使用 **Required** 选项，则序列容器将联接包事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-109">If the package were configured to use the **Required** option, the Sequence container would join the package transaction.</span></span>  
  
-   <span data-ttu-id="f89ab-110">**Supported** 指示容器不启动事务，但将联接由其父容器启动的任何事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-110">**Supported** indicates that the container does not start a transaction, but joins any transaction started by its parent container.</span></span> <span data-ttu-id="f89ab-111">例如，如果具有四个执行 SQL 任务的包启动了一个事务，而且所有这四个任务都使用 **Supported** 选项，则在其中任何一个任务失败时都会回滚执行 SQL 任务所执行的数据库更新。</span><span class="sxs-lookup"><span data-stu-id="f89ab-111">For example, if a package with four Execute SQL tasks starts a transaction and all four tasks use the **Supported** option, the database updates performed by the Execute SQL tasks are rolled back if any task fails.</span></span> <span data-ttu-id="f89ab-112">如果包没有启动事务，则四个执行 SQL 任务将不绑定到该事务，而且除了回滚失败的任务所执行的更新外，不回滚任何其他数据库更新。</span><span class="sxs-lookup"><span data-stu-id="f89ab-112">If the package does not start a transaction, the four Execute SQL tasks are not bound by a transaction, and no database updates except the ones performed by the failed task are rolled back.</span></span>  
  
-   <span data-ttu-id="f89ab-113">**NotSupported** 指示容器不启动事务，也不联接现有事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-113">**NotSupported** indicates that the container does not start a transaction or join an existing transaction.</span></span> <span data-ttu-id="f89ab-114">由父容器启动的事务不影响已经配置为不支持事务的子容器。</span><span class="sxs-lookup"><span data-stu-id="f89ab-114">A transaction started by a parent container does not affect child containers that have been configured to not support transactions.</span></span> <span data-ttu-id="f89ab-115">例如，如果包配置为启动事务，而包中的 For 循环容器使用 **NotSupported** 选项，则在 For 循环中的任务失败时不回滚任何任务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-115">For example, if a package is configured to start a transaction and a For Loop container in the package uses the **NotSupported** option, none of the tasks in the For Loop can roll back if they fail.</span></span>  
  
 <span data-ttu-id="f89ab-116">通过设置容器的 TransactionOption 属性，你可以配置事务。</span><span class="sxs-lookup"><span data-stu-id="f89ab-116">You configure transactions by setting the TransactionOption property on the container.</span></span> <span data-ttu-id="f89ab-117">您可以使用 **中的** “属性” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]窗口设置此属性，也可以通过编程方式设置此属性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-117">You can set this property by using the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], or you can set the property programmatically.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f89ab-118">`TransactionOption` 属性影响是否应用由容器请求的 `IsolationLevel` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="f89ab-118">The `TransactionOption` property influences whether or not the value of the `IsolationLevel` property requested by a container is applied.</span></span> <span data-ttu-id="f89ab-119">有关详细信息，请参阅 `IsolationLevel` 主题中的属性说明，[设置包属性](set-package-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f89ab-119">For more information, see the description of the `IsolationLevel` property in the topic, [Setting Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-configure-a-package-to-use-transactions"></a><span data-ttu-id="f89ab-120">将包配置为使用事务</span><span class="sxs-lookup"><span data-stu-id="f89ab-120">To configure a package to use transactions</span></span>  
  
-   [<span data-ttu-id="f89ab-121">将包配置为使用事务</span><span class="sxs-lookup"><span data-stu-id="f89ab-121">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a><span data-ttu-id="f89ab-122">外部资源</span><span class="sxs-lookup"><span data-stu-id="f89ab-122">External Resources</span></span>  
  
-   <span data-ttu-id="f89ab-123"> www.mssqltips.com 上的博客项 [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783)（如何在 SQL Server Integration Services SSIS 中使用事务）</span><span class="sxs-lookup"><span data-stu-id="f89ab-123">Blog entry, [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783), on www.mssqltips.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89ab-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f89ab-124">See Also</span></span>  
 <span data-ttu-id="f89ab-125">[继承的事务](../../2014/integration-services/inherited-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="f89ab-125">[Inherited Transactions](../../2014/integration-services/inherited-transactions.md) </span></span>  
 [<span data-ttu-id="f89ab-126">多个事务</span><span class="sxs-lookup"><span data-stu-id="f89ab-126">Multiple Transactions</span></span>](../../2014/integration-services/multiple-transactions.md)  
  
  
