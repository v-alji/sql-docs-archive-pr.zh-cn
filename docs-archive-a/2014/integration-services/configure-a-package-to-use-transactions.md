---
title: 将包配置为使用事务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f469c2439deb2d16ac9046a1628e82c34e39b31d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688123"
---
# <a name="configure-a-package-to-use-transactions"></a><span data-ttu-id="e66f5-102">将包配置为使用事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-102">Configure a Package to Use Transactions</span></span>
  <span data-ttu-id="e66f5-103">将包配置为使用事务时，您有两种选择：</span><span class="sxs-lookup"><span data-stu-id="e66f5-103">When you configure a package to use transactions, you have two options:</span></span>  
  
-   <span data-ttu-id="e66f5-104">包仅包含单个事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-104">Have a single transaction for the package.</span></span> <span data-ttu-id="e66f5-105">在这种情况下，将由包自身“启动” \*\* 此事务，而此包中的各个任务和容器参与此单个事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-105">In this case, it is the package itself that *initiates* this transaction, whereas individual tasks and containers in the package participate in this single transaction.</span></span>  
  
-   <span data-ttu-id="e66f5-106">包包含多个事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-106">Have multiple transactions in the package.</span></span> <span data-ttu-id="e66f5-107">在这种情况下，包支持多个事务，但这些事务实际上是由包中的各个任务或容器启动的。</span><span class="sxs-lookup"><span data-stu-id="e66f5-107">In this case, the package supports transactions, but individual tasks and containers in the package actually initiate the transactions.</span></span>  
  
 <span data-ttu-id="e66f5-108">下面的过程介绍如何配置上述两种选择。</span><span class="sxs-lookup"><span data-stu-id="e66f5-108">The following procedures describe how to configure both options.</span></span>  
  
## <a name="configuring-a-single-transaction"></a><span data-ttu-id="e66f5-109">配置单个事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-109">Configuring a Single Transaction</span></span>  
 <span data-ttu-id="e66f5-110">在此选择中，程序包自身启动单个事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-110">In this option, the package itself initiates a single transaction.</span></span> <span data-ttu-id="e66f5-111">通过将包的 TransactionOption 属性设置为，可以将包配置为启动此事务 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-111">You configure the package to initiate this transaction by setting the TransactionOption property of the package to `Required`.</span></span>  
  
 <span data-ttu-id="e66f5-112">接着，在此单个事务中登记特定任务和容器。</span><span class="sxs-lookup"><span data-stu-id="e66f5-112">Next, you enlist specific tasks and containers in this single transaction.</span></span> <span data-ttu-id="e66f5-113">若要在事务中登记任务或容器，请将该任务或容器的 TransactionOption 属性设置为 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-113">To enlist a task or container in a transaction, you set the TransactionOption property of that task or container to `Supported`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a><span data-ttu-id="e66f5-114">将包配置为使用单个事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-114">To configure a package to use a single transaction</span></span>  
  
1.  <span data-ttu-id="e66f5-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要配置为使用事务的包所在的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e66f5-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use a transaction.</span></span>  
  
2.  <span data-ttu-id="e66f5-116">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e66f5-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e66f5-117">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e66f5-117">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="e66f5-118">右键单击控制流设计图面背景中的任意位置，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e66f5-118">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e66f5-119">在 "**属性**" 窗口中，将 "TransactionOption" 属性设置为 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-119">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
6.  <span data-ttu-id="e66f5-120">在“控制流”\*\*\*\* 选项卡的设计图面上，右键单击要在事务中注册的任务或容器，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e66f5-120">On the design surface of the **ControlFlow** tab, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="e66f5-121">在 "**属性**" 窗口中，将 "TransactionOption" 属性设置为 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-121">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e66f5-122">若要在事务中登记连接，请注册在该事务中使用连接的任务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-122">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="e66f5-123">有关详细信息，请参阅 [Integration Services (SSIS) 连接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="e66f5-123">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
8.  <span data-ttu-id="e66f5-124">对要在事务中注册的每个任务和容器，请重复步骤 6 和 7。</span><span class="sxs-lookup"><span data-stu-id="e66f5-124">Repeat steps 6 and 7 for each task and container that you want to enroll in the transaction.</span></span>  
  
## <a name="configuring-multiple-transactions"></a><span data-ttu-id="e66f5-125">配置多个事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-125">Configuring Multiple Transactions</span></span>  
 <span data-ttu-id="e66f5-126">在此选择中，包自身支持但不启动事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-126">In this option, the package itself supports transactions but does not start a transaction.</span></span> <span data-ttu-id="e66f5-127">通过将包的 TransactionOption 属性设置为，可以将包配置为支持事务 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-127">You configure the package to support transactions by setting the TransactionOption property of the package to `Supported`.</span></span>  
  
 <span data-ttu-id="e66f5-128">接着，在包中将所需任务和容器配置为启动或参与事务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-128">Next, you configure the desired tasks and containers inside the package to initiate or participate in transactions.</span></span> <span data-ttu-id="e66f5-129">若要将任务或容器配置为启动事务，请将该任务或容器的 TransactionOption 属性设置为 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-129">To configure a task or container to initiate a transaction, you set the TransactionOption property of that task or container to `Required`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a><span data-ttu-id="e66f5-130">将包配置为使用多个事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-130">To configure a package to use multiple transactions</span></span>  
  
1.  <span data-ttu-id="e66f5-131">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要配置为使用事务的包所在的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e66f5-131">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use transaction.s</span></span>  
  
2.  <span data-ttu-id="e66f5-132">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e66f5-132">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e66f5-133">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e66f5-133">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="e66f5-134">右键单击控制流设计图面背景中的任意位置，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e66f5-134">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e66f5-135">在 "**属性**" 窗口中，将 "TransactionOption" 属性设置为 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-135">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e66f5-136">该包支持事务，但事务是由包中的任务或容器启动的。</span><span class="sxs-lookup"><span data-stu-id="e66f5-136">The package supports transactions, but the transactions are started by task or containers in the package.</span></span>  
  
6.  <span data-ttu-id="e66f5-137">在“控制流”\*\*\*\* 选项卡的设计图面上，右键单击要为其启动事务的包中的任务或容器，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e66f5-137">On the design surface of the **ControlFlow** tab, right-click the task or the container in the package for which you want to start a transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="e66f5-138">在 "**属性**" 窗口中，将 "TransactionOption" 属性设置为 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-138">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
8.  <span data-ttu-id="e66f5-139">如果事务由容器启动，则右键单击要在事务中注册的任务或容器，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e66f5-139">If a transaction is started by a container, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
9. <span data-ttu-id="e66f5-140">在 "**属性**" 窗口中，将 "TransactionOption" 属性设置为 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="e66f5-140">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e66f5-141">若要在事务中登记连接，请注册在该事务中使用连接的任务。</span><span class="sxs-lookup"><span data-stu-id="e66f5-141">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="e66f5-142">有关详细信息，请参阅 [Integration Services (SSIS) 连接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="e66f5-142">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
10. <span data-ttu-id="e66f5-143">对启动事务的每个任务和容器，请重复步骤 6 到 9。</span><span class="sxs-lookup"><span data-stu-id="e66f5-143">Repeat steps 6 through 9 for each task and container that starts a transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66f5-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e66f5-144">See Also</span></span>  
 [<span data-ttu-id="e66f5-145">Integration Services 事务</span><span class="sxs-lookup"><span data-stu-id="e66f5-145">Integration Services Transactions</span></span>](integration-services-transactions.md)  
  
  
