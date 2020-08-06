---
title: 订阅和检查 Finance Name 策略 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2bfe6f463d03fe8b95f000dc6f34dc0718a7729f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577585"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a><span data-ttu-id="fce9d-102">订阅和检查 Finance Name 策略</span><span class="sxs-lookup"><span data-stu-id="fce9d-102">Subscribe to and Check the Finance Name Policy</span></span>
  <span data-ttu-id="fce9d-103">在本任务中，将 Finance 数据库配置为订阅 Finance 策略类别。</span><span class="sxs-lookup"><span data-stu-id="fce9d-103">In this task, you will configure the Finance database to subscribe to the Finance policy category.</span></span> <span data-ttu-id="fce9d-104">然后，测试 Finance Name 策略。</span><span class="sxs-lookup"><span data-stu-id="fce9d-104">Then, you will test the Finance Name policy.</span></span>  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a><span data-ttu-id="fce9d-105">订阅 Finance 策略类别</span><span class="sxs-lookup"><span data-stu-id="fce9d-105">To subscribe to the Finance policy category</span></span>  
  
1.  <span data-ttu-id="fce9d-106">在对象资源管理器中，展开 "**数据库**"，右键单击 `Finance` ，指向 "**策略**"，然后单击 "**类别**"。</span><span class="sxs-lookup"><span data-stu-id="fce9d-106">In Object Explorer, expand **Databases**, right-click `Finance`, point to **Policies**, and then click **Categories**.</span></span>  
  
2.  <span data-ttu-id="fce9d-107">选择该类别的 "已**订阅**" 复选框 `Finance` 。</span><span class="sxs-lookup"><span data-stu-id="fce9d-107">Select the **Subscribed** checkbox for the `Finance` category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a><span data-ttu-id="fce9d-108">测试 Finance Name 策略的实施情况</span><span class="sxs-lookup"><span data-stu-id="fce9d-108">To test the enforcement of the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="fce9d-109">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，打开一个查询窗口。</span><span class="sxs-lookup"><span data-stu-id="fce9d-109">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window.</span></span> <span data-ttu-id="fce9d-110">执行下面的语句，以尝试创建一个违反 **Finance Name** 策略的表。</span><span class="sxs-lookup"><span data-stu-id="fce9d-110">Execute the following statements that try to create a table that violates the **Finance Name** policy.</span></span> <span data-ttu-id="fce9d-111">该表违反了此策略，因为表名没有以字母 **fintbl**开头。</span><span class="sxs-lookup"><span data-stu-id="fce9d-111">The table violates the policy because the table name does not begin with the letters **fintbl**.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="fce9d-112">请注意，此策略禁止创建该表，并返回一条提供策略名称的信息性消息。</span><span class="sxs-lookup"><span data-stu-id="fce9d-112">Notice that the policy prevents the table from being created and returns an informational message that provides the policy name.</span></span>  
  
2.  <span data-ttu-id="fce9d-113">若要提供有效的名称，请按如下方式修改代码并重新运行语句。</span><span class="sxs-lookup"><span data-stu-id="fce9d-113">To provide a valid name, modify the code as follows and run the statement again.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="fce9d-114">此时，将创建该表。</span><span class="sxs-lookup"><span data-stu-id="fce9d-114">This time, the table is created.</span></span>  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a><span data-ttu-id="fce9d-115">将策略应用于整个服务器</span><span class="sxs-lookup"><span data-stu-id="fce9d-115">To apply the policy to the whole server</span></span>  
  
1.  <span data-ttu-id="fce9d-116">当前，仅 Finance 数据库订阅了 Finance 策略类别。</span><span class="sxs-lookup"><span data-stu-id="fce9d-116">Currently, only the Finance database subscribes to the Finance policy category.</span></span> <span data-ttu-id="fce9d-117">在很多情况下，将策略类别应用于整个服务器会更容易一些。</span><span class="sxs-lookup"><span data-stu-id="fce9d-117">In many cases, it is easier to apply the policy category to the whole server.</span></span> <span data-ttu-id="fce9d-118">在对象资源管理器中，展开“管理”\*\*\*\*，右键单击“策略管理”\*\*\*\*，然后单击“管理类别”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fce9d-118">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="fce9d-119">在“管理策略类别”\*\*\*\* 对话框中，找到 Finance 类别，然后选中 Finance 类别的“托管数据库订阅”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="fce9d-119">In the **Manage Policy Categories** dialog box, locate the Finance category, and select the **Mandate Database Subscriptions** checkbox for the Finance category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="fce9d-120">现在，Finance 类别会应用于所有数据库，但创建的条件会将 Finance Name 策略限定为 Finance 数据库。</span><span class="sxs-lookup"><span data-stu-id="fce9d-120">Now the Finance category applies to all databases, but the condition that you have created restricts the Finance Name policy to the Finance database.</span></span> <span data-ttu-id="fce9d-121">这说明了如何使用复杂的条件组合限定策略目标，以便按适当的方式在多个服务器上正确应用策略。</span><span class="sxs-lookup"><span data-stu-id="fce9d-121">This shows how you can use complex combinations of conditions to target policies in ways that will apply correctly on many servers.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="fce9d-122">摘要</span><span class="sxs-lookup"><span data-stu-id="fce9d-122">Summary</span></span>  
 <span data-ttu-id="fce9d-123">本教程说明了如何创建基于策略的管理条件、策略和策略组，以及如何应用筛选器并检查基于策略的管理目标是否符合策略。</span><span class="sxs-lookup"><span data-stu-id="fce9d-123">This tutorial has shown you how to create Policy-Based Management conditions, policies and policy groups, and how to apply filters and check the compliance of Policy-Based Management targets.</span></span>  
  
## <a name="next"></a><span data-ttu-id="fce9d-124">下一步</span><span class="sxs-lookup"><span data-stu-id="fce9d-124">Next</span></span>  
 <span data-ttu-id="fce9d-125">现已学完了本教程。</span><span class="sxs-lookup"><span data-stu-id="fce9d-125">This tutorial is finished.</span></span> <span data-ttu-id="fce9d-126">若要返回到开始位置，请单击 [教程：使用基于策略的管理来管理服务器](tutorial-administering-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="fce9d-126">To return to the start, click [Tutorial: Administering Servers by Using Policy-Based Management](tutorial-administering-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="fce9d-127">有关教程的列表，请参阅[SQL Server 2014 的教程](../../tutorials/tutorials-for-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="fce9d-127">For a list of tutorials, see [Tutorials for SQL Server 2014](../../tutorials/tutorials-for-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce9d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fce9d-128">See Also</span></span>  
 [<span data-ttu-id="fce9d-129">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="fce9d-129">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
