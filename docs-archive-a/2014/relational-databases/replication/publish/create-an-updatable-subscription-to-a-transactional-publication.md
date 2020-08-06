---
title: " (Management Studio) 创建对事务发布的可更新订阅 |Microsoft Docs"
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693732"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a><span data-ttu-id="b5eee-102">创建事务发布的可更新订阅 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b5eee-102">Create an Updatable Subscription to a Transactional Publication (Management Studio)</span></span>

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
<span data-ttu-id="b5eee-103">通过事务复制，可以将在订阅服务器上进行的更改回传到使用立即或排队更新订阅的发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-103">Transactional replication enables changes made at a Subscriber to be propagated back to the Publisher using either immediate or queued updating subscriptions.</span></span> <span data-ttu-id="b5eee-104">可以使用复制存储过程以编程方式创建更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-104">You can create an updating subscription programmatically using replication stored procedures.</span></span>

<span data-ttu-id="b5eee-105">可以在“新建订阅向导”的“可更新订阅”页上配置可更新订阅。 </span><span class="sxs-lookup"><span data-stu-id="b5eee-105">Configure updatable subscriptions on the **Updatable Subscriptions** page of the **New Subscription Wizard**.</span></span> <span data-ttu-id="b5eee-106">只有为可更新订阅启用了事务发布，此页才可用。</span><span class="sxs-lookup"><span data-stu-id="b5eee-106">This page is only available if you have enabled a transactional publication for updatable subscriptions.</span></span> <span data-ttu-id="b5eee-107">有关启用可更新订阅的详细信息，请参阅[为事务发布启用更新订阅](enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-107">For more information about enabling updatable subscriptions, see [Enable Updating Subscriptions for Transactional Publications](enable-updating-subscriptions-for-transactional-publications.md).</span></span>   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a><span data-ttu-id="b5eee-108">从发布服务器配置可更新订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-108">Configure an updatable subscription from the Publisher</span></span>  

1. <span data-ttu-id="b5eee-109">在 Microsoft SQL Server Management Studio 中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="b5eee-109">Connect to the Publisher in Microsoft SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="b5eee-110">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5eee-110">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>
3. <span data-ttu-id="b5eee-111">右键单击为更新订阅启用的事务发布，然后单击“新建订阅”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-111">Right-click a transactional publication enabled for updating subscriptions, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="b5eee-112">按照向导中的页，为订阅指定选项，如分发代理应在何处运行。</span><span class="sxs-lookup"><span data-stu-id="b5eee-112">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
5. <span data-ttu-id="b5eee-113">在“新建订阅向导”的“可更新订阅”页上，确保已选中“复制”。  </span><span class="sxs-lookup"><span data-stu-id="b5eee-113">On the **Updatable Subscriptions** page of the **New Subscription Wizard**, ensure **Replicate** is selected.</span></span>
6. <span data-ttu-id="b5eee-114">从“在发布服务器提交”下拉列表中选择一个选项：</span><span class="sxs-lookup"><span data-stu-id="b5eee-114">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    *  <span data-ttu-id="b5eee-115">若要使用立即更新订阅，请选择“同时提交更改”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-115">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="b5eee-116">如果选择此选项，并且发布允许排队更新订阅（使用新建发布向导所创建发布的默认设置），则订阅属性 **update_mode** 将设置为“故障转移”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-116">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="b5eee-117">此模式使您以后在必要时能够切换到排队更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-117">This mode allows you to switch to queued updating later if necessary.</span></span>
    *  <span data-ttu-id="b5eee-118">若要使用排队更新订阅，请选择“对更改进行排队并在可能时提交”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-118">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="b5eee-119">如果选择此选项且发布允许立即更新订阅（使用新建发布向导所创建发布的默认设置），而且订阅服务器运行的是 SQL Server 2005 或更高版本，则订阅属性 **update_mode** 将设置为排队故障转移。</span><span class="sxs-lookup"><span data-stu-id="b5eee-119">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued failover.</span></span> <span data-ttu-id="b5eee-120">此模式使您以后在必要时能够切换到立即更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-120">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="b5eee-121">有关切换更新模式的详细信息，请参阅[切换可更新事务性订阅的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-121">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

7. <span data-ttu-id="b5eee-122">对于使用立即更新或将 **update_mode** 设置为**排队故障转移**的订阅，显示“用于可更新订阅的登录名”页。</span><span class="sxs-lookup"><span data-stu-id="b5eee-122">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to **queued failover**.</span></span> <span data-ttu-id="b5eee-123">在“用于可更新订阅的登录名”页上，指定链接服务器，通过此服务器可与发布服务器建立连接，以便立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-123">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="b5eee-124">连接用于在订阅服务器上激发的触发器，这些触发器用于将更改传播到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-124">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="b5eee-125">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-125">Select one of the following options:</span></span>

    * <span data-ttu-id="b5eee-126">**创建使用 SQL Server 身份验证进行连接的链接服务器。**</span><span class="sxs-lookup"><span data-stu-id="b5eee-126">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="b5eee-127">如果尚未在订阅服务器和发布服务器之间定义远程服务器或链接服务器，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-127">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="b5eee-128">复制会为您创建链接服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-128">Replication creates a linked server for you.</span></span> <span data-ttu-id="b5eee-129">所指定的帐户在发布服务器上必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="b5eee-129">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="b5eee-130">**使用您指定的链接服务器或远程服务器。**</span><span class="sxs-lookup"><span data-stu-id="b5eee-130">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="b5eee-131">如果已使用 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio 或其他方法在订阅服务器和发布服务器之间定义了远程服务器或链接服务器，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-131">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="b5eee-132">有关链接服务器帐户所需权限的信息，请参阅[在此处输入链接说明](../security/secure-the-subscriber.md)的**排队更新订阅**部分。</span><span class="sxs-lookup"><span data-stu-id="b5eee-132">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

8. <span data-ttu-id="b5eee-133">完成向导。</span><span class="sxs-lookup"><span data-stu-id="b5eee-133">Complete the wizard.</span></span>

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a><span data-ttu-id="b5eee-134">从订阅服务器配置可更新订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-134">Configure an updatable subscription from the Subscriber</span></span>


1. <span data-ttu-id="b5eee-135">在 SQL Server Management Studio 中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="b5eee-135">Connect to the Subscriber in SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="b5eee-136">展开 **“复制”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5eee-136">Expand the **Replication** folder.</span></span>
3. <span data-ttu-id="b5eee-137">右键单击 **“本地订阅”** 文件夹，再单击 **“新建订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="b5eee-137">Right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="b5eee-138">在“新建订阅向导”的“发布”页上，从“发布服务器”下拉列表中选择“查找 SQL Server 发布服务器”。   </span><span class="sxs-lookup"><span data-stu-id="b5eee-138">On the **Publication** page of the **New Subscription Wizard**, select **Find SQL Server Publisher** from the **Publisher** drop-down list.</span></span>
5. <span data-ttu-id="b5eee-139">在 **“连接到服务器”** 对话框中连接到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-139">Connect to the Publisher in the **Connect to Server** dialog box.</span></span>
6. <span data-ttu-id="b5eee-140">在“发布”页上，选择为更新订阅启用的事务发布。</span><span class="sxs-lookup"><span data-stu-id="b5eee-140">Select a transactional publication enabled for updating subscriptions on the **Publication** page.</span></span>
7. <span data-ttu-id="b5eee-141">按照向导中的页，为订阅指定选项，如分发代理应在何处运行。</span><span class="sxs-lookup"><span data-stu-id="b5eee-141">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
8. <span data-ttu-id="b5eee-142">在“新建订阅向导”的“可更新订阅”页上，确保已选中“复制”。 </span><span class="sxs-lookup"><span data-stu-id="b5eee-142">On the **Updatable Subscriptions** page of the New Subscription Wizard, ensure **Replicate** is selected.</span></span>
9. <span data-ttu-id="b5eee-143">从“在发布服务器提交”下拉列表中选择一个选项：</span><span class="sxs-lookup"><span data-stu-id="b5eee-143">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    * <span data-ttu-id="b5eee-144">若要使用立即更新订阅，请选择“同时提交更改”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-144">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="b5eee-145">如果选择此选项，并且发布允许排队更新订阅（使用新建发布向导所创建发布的默认设置），则订阅属性 **update_mode** 将设置为“故障转移”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-145">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="b5eee-146">此模式使您以后在必要时能够切换到排队更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-146">This mode allows you to switch to queued updating later if necessary.</span></span>
    * <span data-ttu-id="b5eee-147">若要使用排队更新订阅，请选择“对更改进行排队并在可能时提交”。</span><span class="sxs-lookup"><span data-stu-id="b5eee-147">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="b5eee-148">如果选择此选项且发布允许立即更新订阅（使用新建发布向导所创建发布的默认设置），而且订阅服务器运行的是 SQL Server 2005 或更高版本，则订阅属性 **update_mode** 将设置为排队**故障转移**。</span><span class="sxs-lookup"><span data-stu-id="b5eee-148">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued **failover**.</span></span> <span data-ttu-id="b5eee-149">此模式使您以后在必要时能够切换到立即更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-149">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="b5eee-150">有关切换更新模式的详细信息，请参阅[切换可更新事务性订阅的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-150">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

10. <span data-ttu-id="b5eee-151">对于使用立即更新或将 **update_mode** 设置为排队**故障转移**的订阅，显示“用于可更新订阅的登录名”页。</span><span class="sxs-lookup"><span data-stu-id="b5eee-151">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to queued **failover**.</span></span> <span data-ttu-id="b5eee-152">在“用于可更新订阅的登录名”页上，指定链接服务器，通过此服务器可与发布服务器建立连接，以便立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-152">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="b5eee-153">连接用于在订阅服务器上激发的触发器，这些触发器用于将更改传播到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-153">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="b5eee-154">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-154">Select one of the following options:</span></span>

    * <span data-ttu-id="b5eee-155">**创建使用 SQL Server 身份验证进行连接的链接服务器。**</span><span class="sxs-lookup"><span data-stu-id="b5eee-155">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="b5eee-156">如果尚未在订阅服务器和发布服务器之间定义远程服务器或链接服务器，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-156">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="b5eee-157">复制会为您创建链接服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-157">Replication creates a linked server for you.</span></span> <span data-ttu-id="b5eee-158">所指定的帐户在发布服务器上必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="b5eee-158">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="b5eee-159">**使用您指定的链接服务器或远程服务器。**</span><span class="sxs-lookup"><span data-stu-id="b5eee-159">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="b5eee-160">如果已使用 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio 或其他方法在订阅服务器和发布服务器之间定义了远程服务器或链接服务器，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-160">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="b5eee-161">有关链接服务器帐户所需权限的信息，请参阅[在此处输入链接说明](../security/secure-the-subscriber.md)的**排队更新订阅**部分。</span><span class="sxs-lookup"><span data-stu-id="b5eee-161">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

11. <span data-ttu-id="b5eee-162">完成向导。</span><span class="sxs-lookup"><span data-stu-id="b5eee-162">Complete the wizard.</span></span>

## <a name="create-an-immediate-updating-pull-subscription"></a><span data-ttu-id="b5eee-163">创建立即更新请求订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-163">Create an immediate updating pull subscription</span></span>

1. <span data-ttu-id="b5eee-164">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-164">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-165">如果结果集中 `allow_sync_tran` 的值为 `1`，说明该发布支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-165">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="b5eee-166">如果结果集中 `allow_sync_tran` 的值为 `0`，说明必须重新创建该发布以使其支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-166">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="b5eee-167">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-167">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-168">如果结果集中 `allow_pull` 的值为 `1`，说明该发布支持请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-168">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="b5eee-169">如果 `allow_pull` 的值是 `0`，则执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)（为 `allow_pull` 指定 `@property` ，并为 `true` 指定 `@value`）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-169">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="b5eee-170">在订阅服务器上，执行 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-170">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="b5eee-171">指定 `@publisher` 和 `@publication`，并为 `@update_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-171">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="b5eee-172">`sync tran` - 使订阅支持立即更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-172">`sync tran` - enables the subscription for immediate updating.</span></span>
    * <span data-ttu-id="b5eee-173">`failover` - 支持对订阅进行立即更新，并将排队更新作为故障转移选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-173">`failover` - enables the subscription for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="b5eee-174">`failover` 要求发布也支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-174">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="b5eee-175">在订阅服务器上，执行 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-175">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b5eee-176">指定下列各项：</span><span class="sxs-lookup"><span data-stu-id="b5eee-176">Specify the following:</span></span>

    * <span data-ttu-id="b5eee-177">`@publisher`、 `@publisher_db`和 `@publication` 参数。</span><span class="sxs-lookup"><span data-stu-id="b5eee-177">The `@publisher`, `@publisher_db`, and `@publication` parameters.</span></span> 
    * <span data-ttu-id="b5eee-178">订阅服务器中的分发代理运行时所使用的 Microsoft Windows 凭据： `@job_login` 和 `@job_password`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-178">The Microsoft Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="b5eee-179">在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password`指定的 Windows 凭据来建立连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-179">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="b5eee-180">分发代理始终使用 Windows 集成身份验证与订阅服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-180">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="b5eee-181">默认情况下，代理使用 Windows 集成身份验证连接到分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-181">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="b5eee-182">（可选） `0` 的值 `@distributor_security_mode` ，以及 Microsoft SQL Server 登录信息 `@distributor_login` 和 `@distributor_password`（如果在连接到分发服务器时需要使用 SQL Server 身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-182">(Optional) A value of `0` for `@distributor_security_mode` and the Microsoft SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="b5eee-183">该订阅的分发代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="b5eee-183">A schedule for the Distribution Agent job for this subscription.</span></span> 

5. <span data-ttu-id="b5eee-184">在订阅服务器上的订阅数据库中，执行 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-184">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="b5eee-185">指定 `@publisher`、 `@publication`、发布数据库的名称 `@publisher_db`，以及为 `@security_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-185">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

    * <span data-ttu-id="b5eee-186">`0` - 表示在发布服务器上执行更新时使用 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b5eee-186">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="b5eee-187">此选项需要为 `@login` 和 `@password`指定发布服务器上的一个有效登录名。</span><span class="sxs-lookup"><span data-stu-id="b5eee-187">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
    * <span data-ttu-id="b5eee-188">`1` - 在连接到发布服务器时，使用在订阅服务器上执行更改的用户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="b5eee-188">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="b5eee-189">请参阅 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) ，了解与此安全模式相关的限制。</span><span class="sxs-lookup"><span data-stu-id="b5eee-189">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
    * <span data-ttu-id="b5eee-190">`2` - 使用现有的、用户定义的链接服务器登录名，该登录名是使用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)创建的。</span><span class="sxs-lookup"><span data-stu-id="b5eee-190">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>

6. <span data-ttu-id="b5eee-191">在发布服务器上，执行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) （指定 `@publication`、 `@subscriber`、 `@destination_db`，为 `@subscription_type`指定值 pull，并为 `@update_mode`指定步骤 3 中指定的相同值）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-191">At the publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="b5eee-192">这会在发布服务器上注册请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-192">This registers the pull subscription at the Publisher.</span></span> 


## <a name="create-an-immediate-updating-push-subscription"></a><span data-ttu-id="b5eee-193">创建立即更新推送订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-193">Create an immediate updating push subscription</span></span> 

1. <span data-ttu-id="b5eee-194">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-194">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-195">如果结果集中 `allow_sync_tran` 的值为 `1`，说明该发布支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-195">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="b5eee-196">如果结果集中 `allow_sync_tran` 的值为 `0`，说明必须重新创建该发布以使其支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-196">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="b5eee-197">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)以验证发布是否支持推送订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-197">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-198">如果结果集中 `allow_push` 的值为 `1`，说明该发布支持推送订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-198">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="b5eee-199">如果 `allow_push` 的值是 `0`，则执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)（为 `allow_push` 指定 `@property` ，并为 `true` 指定 `@value`）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-199">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_push` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="b5eee-200">在发布服务器上，执行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-200">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="b5eee-201">指定 `@publication`、 `@subscriber`和 `@destination_db`，并为 `@update_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-201">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="b5eee-202">`sync tran` - 支持立即更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-202">`sync tran` - enables support for immediate updating.</span></span>
    * <span data-ttu-id="b5eee-203">`failover` - 支持立即更新，并且将排队更新作为故障转移选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-203">`failover` - enables support for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="b5eee-204">`failover` 要求发布也支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-204">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="b5eee-205">在发布服务器上，执行 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-205">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b5eee-206">指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="b5eee-206">Specify the following parameters:</span></span>

    * <span data-ttu-id="b5eee-207">`@subscriber`、 `@subscriber_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-207">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="b5eee-208">分发服务器中的分发代理运行时所使用的 Windows 凭据： `@job_login` 和 `@job_password`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-208">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="b5eee-209">在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password`指定的 Windows 凭据来建立连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-209">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="b5eee-210">分发代理始终使用 Windows 集成身份验证与分发服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-210">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="b5eee-211">默认情况下，该代理将使用 Windows 集成身份验证连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-211">By default, the agent will connect to the Subscriber using Windows Integrated Authentication.</span></span> 

    * <span data-ttu-id="b5eee-212">（可选） `0` 的值 `@subscriber_security_mode` ，以及 SQL Server 登录信息 `@subscriber_login` 和 `@subscriber_password`（如果在连接到订阅服务器时需要使用 SQL Server 身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-212">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="b5eee-213">该订阅的分发代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="b5eee-213">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="b5eee-214">在订阅服务器上的订阅数据库中，执行 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-214">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="b5eee-215">指定 `@publisher`、 `@publication`、发布数据库的名称 `@publisher_db`，以及为 `@security_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-215">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

     * <span data-ttu-id="b5eee-216">`0` - 表示在发布服务器上执行更新时使用 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b5eee-216">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="b5eee-217">此选项需要为 `@login` 和 `@password`指定发布服务器上的一个有效登录名。</span><span class="sxs-lookup"><span data-stu-id="b5eee-217">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
     * <span data-ttu-id="b5eee-218">`1` - 在连接到发布服务器时，使用在订阅服务器上执行更改的用户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="b5eee-218">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="b5eee-219">请参阅 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) ，了解与此安全模式相关的限制。</span><span class="sxs-lookup"><span data-stu-id="b5eee-219">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
     * <span data-ttu-id="b5eee-220">`2` - 使用现有的、用户定义的链接服务器登录名，该登录名是使用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)创建的。</span><span class="sxs-lookup"><span data-stu-id="b5eee-220">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>


## <a name="create-a-queued-updating-pull-subscription"></a><span data-ttu-id="b5eee-221">创建排队更新请求订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-221">Create a queued updating pull subscription</span></span> ##

1. <span data-ttu-id="b5eee-222">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-222">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-223">如果结果集中 `allow_queued_tran` 的值为 `1`，说明该发布支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-223">If the value of `allow_queued_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="b5eee-224">如果结果集中 `allow_queued_tran` 的值为 `0`，说明必须重新创建该发布以使其支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-224">If the value of `allow_queued_tran` in the result set is `0`, the publication must be recreated with queued updating subscriptions enabled.</span></span>

2. <span data-ttu-id="b5eee-225">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-225">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-226">如果结果集中 `allow_pull` 的值为 `1`，说明该发布支持请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-226">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="b5eee-227">如果 `allow_pull` 的值是 `0`，则执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)（为 `allow_pull` 指定 `@property` ，并为 `true` 指定 `@value`）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-227">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="b5eee-228">在订阅服务器上，执行 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-228">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="b5eee-229">指定 `@publisher` 和 `@publication`，并为 `@update_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-229">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="b5eee-230">`queued tran` - 支持订阅进行排队更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-230">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="b5eee-231">`queued failover` - 支持排队更新，并将立即更新作为故障转移选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-231">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="b5eee-232">`queued failover` 要求发布也支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-232">`queued failover` requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="b5eee-233">若要故障转移到立即更新，必须使用 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 定义将订阅服务器上的更改复制到发布服务器所用的凭据。</span><span class="sxs-lookup"><span data-stu-id="b5eee-233">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>
 
4. <span data-ttu-id="b5eee-234">在订阅服务器上，执行 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-234">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b5eee-235">指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="b5eee-235">Specify the following parameters:</span></span>

    * <span data-ttu-id="b5eee-236">@publisher、 `@publisher_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-236">@publisher, `@publisher_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="b5eee-237">订阅服务器中的分发代理运行时所使用的 Windows 凭据： `@job_login` 和 `@job_password`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-237">The Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="b5eee-238">在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password`指定的 Windows 凭据来建立连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-238">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="b5eee-239">分发代理始终使用 Windows 集成身份验证与订阅服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-239">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="b5eee-240">默认情况下，代理使用 Windows 集成身份验证连接到分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-240">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="b5eee-241">（可选） `0` 的值 `@distributor_security_mode` ，以及 SQL Server 登录信息 `@distributor_login` 和 `@distributor_password`（如果在连接到分发服务器时需要使用 SQL Server 身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-241">(Optional) A value of `0` for `@distributor_security_mode` and the SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="b5eee-242">该订阅的分发代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="b5eee-242">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="b5eee-243">在发布服务器上，执行 [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) 以在发布服务器上注册订阅服务器（指定 `@publication`、 `@subscriber`、 `@destination_db`，为 `@subscription_type`指定值 pull，并为 `@update_mode`指定步骤 3 中指定的相同值）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-243">At the publisher, execute [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) to register the Subscriber at the Publisher, specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="b5eee-244">这会在发布服务器上注册请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-244">This registers the pull subscription at the Publisher.</span></span> 


## <a name="to-create-a-queued-updating-push-subscription"></a><span data-ttu-id="b5eee-245">创建排队更新推送订阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-245">To create a queued updating push subscription</span></span> ##

1. <span data-ttu-id="b5eee-246">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)验证发布是否支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-246">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-247">如果结果集中 allow_queued_tran 的值为 1，说明发布支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-247">If the value of allow_queued_tran in the result set is 1, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="b5eee-248">如果结果集中 allow_queued_tran 的值为 0，说明必须重新创建该发布以使其支持排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-248">If the value of allow_queued_tran in the result set is 0, the publication must be recreated with queued updating subscriptions enabled.</span></span> <span data-ttu-id="b5eee-249">有关详细信息，请参阅如何：为事务发布启用更新订阅（复制 Transact-SQL 编程）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-249">For more information, see How to: Enable Updating Subscriptions for Transactional Publications (Replication Transact-SQL Programming).</span></span>

2. <span data-ttu-id="b5eee-250">在发布服务器上，通过执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)以验证发布是否支持推送订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-250">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="b5eee-251">如果结果集中 `allow_push` 的值为 `1`，说明该发布支持推送订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-251">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="b5eee-252">如果 `allow_push` 的值是 `0`，则执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)（为 `@property` 指定 allow_push，并为 `true` 指定 `@value`）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-252">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying allow_push for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="b5eee-253">在发布服务器上，执行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-253">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="b5eee-254">指定 `@publication`、 `@subscriber`和 `@destination_db`，并为 `@update_mode`指定以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-254">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="b5eee-255">`queued tran` - 支持订阅进行排队更新。</span><span class="sxs-lookup"><span data-stu-id="b5eee-255">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="b5eee-256">`queued failover` - 支持排队更新，并将立即更新作为故障转移选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-256">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="b5eee-257">queued failover 选项要求发布也支持立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-257">The queued failover option requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="b5eee-258">若要故障转移到立即更新，必须使用 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 定义将订阅服务器上的更改复制到发布服务器所用的凭据。</span><span class="sxs-lookup"><span data-stu-id="b5eee-258">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>

4. <span data-ttu-id="b5eee-259">在发布服务器上，执行 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-259">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b5eee-260">指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="b5eee-260">Specify the following parameters:</span></span>

    * <span data-ttu-id="b5eee-261">`@subscriber`、 `@subscriber_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-261">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="b5eee-262">分发服务器中的分发代理运行时所使用的 Windows 凭据： `@job_login` 和 `@job_password`。</span><span class="sxs-lookup"><span data-stu-id="b5eee-262">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="b5eee-263">在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password`指定的 Windows 凭据来建立连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-263">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="b5eee-264">分发代理始终使用 Windows 集成身份验证与分发服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="b5eee-264">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="b5eee-265">默认情况下，代理使用 Windows 集成身份验证连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="b5eee-265">By default, the agent connects to the Subscriber using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="b5eee-266">（可选） `0` 的值 `@subscriber_security_mode` ，以及 SQL Server 登录信息 `@subscriber_login` 和 `@subscriber_password`（如果在连接到订阅服务器时需要使用 SQL Server 身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b5eee-266">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="b5eee-267">该订阅的分发代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="b5eee-267">A schedule for the Distribution Agent job for this subscription.</span></span>


## <a name="example"></a><span data-ttu-id="b5eee-268">示例</span><span class="sxs-lookup"><span data-stu-id="b5eee-268">Example</span></span> ##

<span data-ttu-id="b5eee-269">本示例针对某个支持立即更新订阅的发布创建了一个立即更新请求订阅。</span><span class="sxs-lookup"><span data-stu-id="b5eee-269">This example creates an immediate updating pull subscription to a publication that supports immediate updating subscriptions.</span></span> <span data-ttu-id="b5eee-270">登录名和密码在运行时使用 sqlcmd 脚本变量进行提供。</span><span class="sxs-lookup"><span data-stu-id="b5eee-270">Login and password values are supplied at runtime using sqlcmd scripting variables.</span></span>

> [!NOTE]  
>  <span data-ttu-id="b5eee-271">此脚本使用 sqlcmd 脚本变量。</span><span class="sxs-lookup"><span data-stu-id="b5eee-271">This script uses sqlcmd scripting variables.</span></span> <span data-ttu-id="b5eee-272">它们采用 `$(MyVariable)`的形式。</span><span class="sxs-lookup"><span data-stu-id="b5eee-272">They are in the form `$(MyVariable)`.</span></span> <span data-ttu-id="b5eee-273">有关如何在命令行上和 SQL Server Management Studio 中使用脚本变量的信息，请参阅 **复制系统存储过程概念** 主题中的 [执行复制脚本](../concepts/replication-system-stored-procedures-concepts.md)部分。</span><span class="sxs-lookup"><span data-stu-id="b5eee-273">For information about how to use scripting variables on the command line and in SQL Server Management Studio, see the **Executing Replication Scripts** section in the topic [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md).</span></span>

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a><span data-ttu-id="b5eee-274">设置排队更新冲突解决选项 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b5eee-274">Set Queued Updating Conflict Resolution Options (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b5eee-275"> 在“发布属性 - \<Publication>”对话框的“订阅选项”页上，为支持排队更新订阅的发布设置冲突解决选项。</span><span class="sxs-lookup"><span data-stu-id="b5eee-275">Set conflict resolution options for publications that support queued updating subscriptions on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="b5eee-276">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b5eee-276">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a><span data-ttu-id="b5eee-277">设置排队更新冲突解决选项</span><span class="sxs-lookup"><span data-stu-id="b5eee-277">To set queued updating conflict resolution options</span></span>  
  
1.  <span data-ttu-id="b5eee-278">在“发布属性 - \<Publication>”对话框的“订阅选项”页上，为“冲突解决策略”选项选择以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b5eee-278">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select one of the following values for the **Conflict resolution policy** option:</span></span>    
    -   <span data-ttu-id="b5eee-279">**保留发布服务器更改**</span><span class="sxs-lookup"><span data-stu-id="b5eee-279">**Keep the Publisher change**</span></span>    
    -   <span data-ttu-id="b5eee-280">**保留订阅服务器更改**</span><span class="sxs-lookup"><span data-stu-id="b5eee-280">**Keep the Subscriber change**</span></span>    
    -   <span data-ttu-id="b5eee-281">**重新初始化订阅**</span><span class="sxs-lookup"><span data-stu-id="b5eee-281">**Reinitialize the subscription**</span></span>    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a><span data-ttu-id="b5eee-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5eee-282">See Also</span></span> ##
 <span data-ttu-id="b5eee-283">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="b5eee-283">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="b5eee-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="b5eee-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="b5eee-285">将 sqlcmd 与脚本变量结合使用</span><span class="sxs-lookup"><span data-stu-id="b5eee-285">Use sqlcmd with Scripting Variables</span></span>](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
