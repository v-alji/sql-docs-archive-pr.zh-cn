---
title: 使用 Windows 同步管理器 (Windows 同步管理器同步订阅) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bb31c344f91c68b04e03dd218f22b09bec44830b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689852"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a><span data-ttu-id="07e7e-102">使用 Windows 同步管理器同步订阅（Windows 同步管理器）</span><span class="sxs-lookup"><span data-stu-id="07e7e-102">Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)</span></span>
  <span data-ttu-id="07e7e-103">如果[!INCLUDE[msCoName](../../includes/msconame-md.md)] 与同步管理器在同一台计算机上运行，那么只能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 同步管理器同步对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布的订阅（也可用来同步脱机文件和网页）。</span><span class="sxs-lookup"><span data-stu-id="07e7e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager can only be used to synchronize subscriptions to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the same computer as Synchronization Manager (it can also be used to synchronize offline files and Web pages).</span></span> <span data-ttu-id="07e7e-104">若要使用同步管理器：</span><span class="sxs-lookup"><span data-stu-id="07e7e-104">To use Synchronization Manager:</span></span>  
  
1.  <span data-ttu-id="07e7e-105">在“订阅属性 - \<Subscriber>: \<SubscriptionDatabase>”对话框中，启用使用 Windows 同步管理器对请求订阅进行同步的选项。</span><span class="sxs-lookup"><span data-stu-id="07e7e-105">Enable the synchronization of pull subscriptions with Windows Synchronization Manager in the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box.</span></span> <span data-ttu-id="07e7e-106">有关访问此对话框的详细信息，请参阅[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="07e7e-106">For more information about accessing this dialog box, see [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
2.  <span data-ttu-id="07e7e-107">通过 Windows 的 **“开始”** 菜单访问同步管理器。</span><span class="sxs-lookup"><span data-stu-id="07e7e-107">Access Synchronization Manager through the **Start** menu in Windows.</span></span>  
  
 <span data-ttu-id="07e7e-108">同步管理器允许对合并订阅使用交互式冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="07e7e-108">Synchronization Manager allows you to use the Interactive Resolver for merge subscriptions.</span></span> <span data-ttu-id="07e7e-109">通常，同步过程中检测到的冲突都能够自动解决，但如果启用了交互式解决，则可由用户在同步过程中解决。</span><span class="sxs-lookup"><span data-stu-id="07e7e-109">Typically, conflicts detected during synchronization are resolved automatically, but if interactive resolution is enabled, conflicts can be resolved by a user during synchronization.</span></span> <span data-ttu-id="07e7e-110">如果在 Windows 同步管理器的外部执行同步（作为 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或复制监视器中的计划同步或按需同步），系统会根据为项目指定的冲突解决程序自动解决冲突，无需用户干预。</span><span class="sxs-lookup"><span data-stu-id="07e7e-110">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07e7e-111">从 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]开始，64 位版本的 Windows 同步管理器无法检测 32 位的订阅。</span><span class="sxs-lookup"><span data-stu-id="07e7e-111">Beginning with [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] and [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], 64-bit versions of the Windows Synchronization Manager cannot detect 32-bit subscriptions.</span></span>  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a><span data-ttu-id="07e7e-112">启用使用 Windows 同步管理器对请求订阅进行同步的选项</span><span class="sxs-lookup"><span data-stu-id="07e7e-112">To enable the synchronization of pull subscriptions with Windows Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="07e7e-113">在“订阅属性 - \<Subscriber>: \<SubscriptionDatabase>”对话框的“常规”页上，为“使用 Windows 同步管理器”选择值“启用”。   </span><span class="sxs-lookup"><span data-stu-id="07e7e-113">On the **General** page of the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select a value of **Enable** for the **Use Windows Synchronization Manager** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="07e7e-114">使用同步管理器同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="07e7e-114">To synchronize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="07e7e-115">使用下列方法之一启动同步管理器：</span><span class="sxs-lookup"><span data-stu-id="07e7e-115">Launch Synchronization Manager using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="07e7e-116">在 Internet Explorer 中，单击 **“工具”** ，再单击 **“同步”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-116">In Internet Explorer, click **Tools**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="07e7e-117">单击 **“开始”** ，指向 **“程序”** 或 **“所有程序”** ，然后指向 **“附件”** ，再单击 **“同步”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-117">Click **Start**, point to **Programs** or **All Programs**, point to **Accessories**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="07e7e-118">单击 **“开始”** ，再单击 **“运行”**</span><span class="sxs-lookup"><span data-stu-id="07e7e-118">Click **Start**, and then click **Run.**</span></span> <span data-ttu-id="07e7e-119">在 "**运行**" 对话框中，在 `mobsync.exe` "**打开**" 字段中键入，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="07e7e-119">In the **Run** dialog box, type `mobsync.exe` in the **Open** field, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="07e7e-120">在 **“要同步的项”** 对话框中，选择要同步的订阅。</span><span class="sxs-lookup"><span data-stu-id="07e7e-120">In the **Items to Synchronize** dialog box, select the subscriptions to synchronize.</span></span> <span data-ttu-id="07e7e-121">将在计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例下列出订阅。</span><span class="sxs-lookup"><span data-stu-id="07e7e-121">Subscriptions are listed under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
3.  <span data-ttu-id="07e7e-122">单击 **“同步”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-122">Click **Synchronize**.</span></span>  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="07e7e-123">使用同步管理器重新初始化请求订阅</span><span class="sxs-lookup"><span data-stu-id="07e7e-123">To reinitialize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="07e7e-124">在 **“要同步的项”** 对话框中，选择订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-124">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="07e7e-125">在 **“SQL Server 订阅属性”** 对话框中，单击 **“重新初始化订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-125">In the **SQL Server Subscription Properties** dialog box, click **Reinitialize Subscription**.</span></span>  
  
3.  <span data-ttu-id="07e7e-126">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-126">Click **Yes**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="07e7e-127">下次同步订阅时，默认情况下会将一个新快照应用于订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="07e7e-127">The next time the subscription is synchronized, by default a new snapshot is applied to the subscription database.</span></span> <span data-ttu-id="07e7e-128">有关详细信息，请参阅 [重新初始化订阅](reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="07e7e-128">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07e7e-129">合并复制允许在应用快照之前将所有未完成的更改上载到发布服务器，但同步管理器没有提供此选项。</span><span class="sxs-lookup"><span data-stu-id="07e7e-129">Merge replication allows any outstanding changes to be uploaded to the Publisher before the snapshot is applied, but this option is not available from Synchronization Manager.</span></span> <span data-ttu-id="07e7e-130">若要上载更改，请先同步，然后再重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="07e7e-130">To upload changes, synchronize the subscription before reinitializing it.</span></span>  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a><span data-ttu-id="07e7e-131">在同步管理器中设置请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="07e7e-131">To set properties for a pull subscription in Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="07e7e-132">在 **“要同步的项”** 对话框中，选择订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-132">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="07e7e-133">在下列选项卡上查看和修改属性：</span><span class="sxs-lookup"><span data-stu-id="07e7e-133">View and modify properties on the following tabs:</span></span>  
  
    -   <span data-ttu-id="07e7e-134">**标识**</span><span class="sxs-lookup"><span data-stu-id="07e7e-134">**Identification**</span></span>  
  
    -   <span data-ttu-id="07e7e-135">**“订阅服务器登录”** 、 **“分发服务器登录”** 和 **“发布服务器登录”** （仅适用于合并复制）</span><span class="sxs-lookup"><span data-stu-id="07e7e-135">**Subscriber Login**, **Distributor Login**, and **Publisher Login** (for merge replication only)</span></span>  
  
    -   <span data-ttu-id="07e7e-136">**“Web 服务器信息”** （适用于运行 SQL Server 2005 或更高版本的订阅服务器中的合并订阅）</span><span class="sxs-lookup"><span data-stu-id="07e7e-136">**Web Server Information** (for merge subscriptions on Subscribers running SQL Server 2005 or later)</span></span>  
  
    -   <span data-ttu-id="07e7e-137">**其他**</span><span class="sxs-lookup"><span data-stu-id="07e7e-137">**Other**</span></span>  
  
     <span data-ttu-id="07e7e-138">建议对所有连接都使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="07e7e-138">It is recommended to use Windows Authentication for all connections.</span></span> <span data-ttu-id="07e7e-139">有关分发代理和合并代理所需权限的信息，请参阅 [Replication Agent Security Model](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="07e7e-139">For information about the permissions required by the Distribution Agent and the Merge Agent, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a><span data-ttu-id="07e7e-140">从同步管理器中删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="07e7e-140">To remove a pull subscription from Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="07e7e-141">在 **“要同步的项”** 对话框中，选择订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-141">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="07e7e-142">在 **“SQL Server 订阅属性”** 对话框中，单击 **“删除订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="07e7e-142">In the **SQL Server Subscription Properties** dialog box, click **Remove Subscription**.</span></span>  
  
3.  <span data-ttu-id="07e7e-143">从 **“删除订阅”** 对话框中选择一个选项。</span><span class="sxs-lookup"><span data-stu-id="07e7e-143">Select an option in the **Remove Subscription** dialog box.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a><span data-ttu-id="07e7e-144">使用交互式冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="07e7e-144">To use the Interactive Resolver</span></span>  
  
1.  <span data-ttu-id="07e7e-145">启用要使用交互式解决方法的项目和订阅。</span><span class="sxs-lookup"><span data-stu-id="07e7e-145">Enable the article and subscription to use interactive resolution.</span></span> <span data-ttu-id="07e7e-146">有关详细信息，请参阅[指定合并项目的交互式冲突解决方法](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution)。</span><span class="sxs-lookup"><span data-stu-id="07e7e-146">For more information, see [Specify Interactive Conflict Resolution for Merge Articles](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>
  
2.  <span data-ttu-id="07e7e-147">如果启用了交互式冲突解决，并且一个和多个项目存在冲突，那么在同步管理器开始同步订阅后，交互式冲突解决程序就会自动启动。</span><span class="sxs-lookup"><span data-stu-id="07e7e-147">After the subscription begins synchronizing in Synchronization Manager, the Interactive Resolver launches automatically if interactive conflict resolution is enabled and there are conflicts for one or more articles.</span></span> <span data-ttu-id="07e7e-148">交互式冲突解决程序每次显示一个冲突，并为每个冲突提出建议的解决方法（基于创建发布和订阅时指定的冲突解决程序）。</span><span class="sxs-lookup"><span data-stu-id="07e7e-148">The Interactive Resolver displays conflicts one at a time, with a suggested resolution for each conflict (based on the resolver specified when the publication and subscription were created).</span></span>  
  
3.  <span data-ttu-id="07e7e-149">根据需要编辑交互式冲突解决程序中显示的任何列，然后单击下列按钮之一以解决冲突：</span><span class="sxs-lookup"><span data-stu-id="07e7e-149">Optionally edit any of the columns displayed in the Interactive Resolver, and then click one of the following buttons to resolve the conflict:</span></span>  
  
    -   <span data-ttu-id="07e7e-150">**接受建议**</span><span class="sxs-lookup"><span data-stu-id="07e7e-150">**Accept Suggested**</span></span>  
  
    -   <span data-ttu-id="07e7e-151">**接受发布服务器**</span><span class="sxs-lookup"><span data-stu-id="07e7e-151">**Accept Publisher**</span></span>  
  
    -   <span data-ttu-id="07e7e-152">**接受订阅服务器**</span><span class="sxs-lookup"><span data-stu-id="07e7e-152">**Accept Subscriber**</span></span>  
  
    -   <span data-ttu-id="07e7e-153">**“自动解决所有冲突”** （无须进一步输入即可解决当前的所有冲突）</span><span class="sxs-lookup"><span data-stu-id="07e7e-153">**Resolve All Automatically** (all current conflicts are resolved without further input)</span></span>  
  
     <span data-ttu-id="07e7e-154">选定的行然后应用于发布服务器和/或订阅服务器，并在后续同步过程中传播到拓扑中的其他节点。</span><span class="sxs-lookup"><span data-stu-id="07e7e-154">The selected row is then applied to the Publisher and/or Subscriber; it is propagated to other nodes in the topology during subsequent synchronizations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07e7e-155">所做的编辑只有在属于为解决冲突而选择的行时才生效。</span><span class="sxs-lookup"><span data-stu-id="07e7e-155">Edits are only applied if they are part of the row that is chosen for resolution.</span></span> <span data-ttu-id="07e7e-156">例如，如果在 **“发布服务器”** 下进行编辑，然后单击 **“接受订阅服务器”** ，那么所做的编辑将被忽略。</span><span class="sxs-lookup"><span data-stu-id="07e7e-156">For example, if you make edits under **Publisher**, and then click **Accept Subscriber**, the edits are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e7e-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07e7e-157">See Also</span></span>  
 [<span data-ttu-id="07e7e-158">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="07e7e-158">Interactive Conflict Resolution</span></span>](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
