---
title: 合并代理安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecbb044ca87ccfc74c5cb39a016667d15cf7a859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690581"
---
# <a name="merge-agent-security"></a><span data-ttu-id="17b57-102">合并代理安全性</span><span class="sxs-lookup"><span data-stu-id="17b57-102">Merge Agent Security</span></span>
  <span data-ttu-id="17b57-103">可以使用 **“合并代理安全性”** 对话框指定用于运行合并代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="17b57-103">The **Merge Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Merge Agent runs.</span></span> <span data-ttu-id="17b57-104">对于推送订阅，合并代理在分发服务器上运行；对于请求订阅，合并代理在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="17b57-104">The Merge Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="17b57-105">Windows 帐户也称为“进程帐户  ”，因为代理进程是在此帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="17b57-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="17b57-106">该对话框中可用的其他选项取决于访问对话框的方式：</span><span class="sxs-lookup"><span data-stu-id="17b57-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="17b57-107">如果从新建订阅向导访问该对话框，您还可以指定合并代理在建立与订阅服务器（对于推送订阅）或发布服务器和分发服务器（对于请求订阅）的连接时所使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="17b57-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Merge Agent makes connections to the Subscriber (for push subscriptions) or the Publisher and Distributor (for pull subscriptions).</span></span> <span data-ttu-id="17b57-108">可以使用 Windows 帐户或在指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户的上下文中建立连接。</span><span class="sxs-lookup"><span data-stu-id="17b57-108">The connection can be made using the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="17b57-109">如果从 **“订阅属性”** 对话框访问该对话框，可通过单击该对话框的 **“订阅服务器连接”** 或 **“发布服务器连接”** 行中的属性按钮 ( **...** ) 来指定合并代理建立连接时所使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="17b57-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Merge Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Publisher Connection** row of that dialog box.</span></span> <span data-ttu-id="17b57-110">有关访问“订阅属性”  对话框的详细信息，请参阅[查看和修改推送订阅属性](view-and-modify-push-subscription-properties.md)和如何[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="17b57-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="17b57-111">所有帐户必须是有效的，并且为每个帐户指定了正确的密码。</span><span class="sxs-lookup"><span data-stu-id="17b57-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="17b57-112">在运行代理之前不会对帐户和密码进行验证。</span><span class="sxs-lookup"><span data-stu-id="17b57-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="17b57-113">选项</span><span class="sxs-lookup"><span data-stu-id="17b57-113">Options</span></span>  
 <span data-ttu-id="17b57-114">**进程帐户**</span><span class="sxs-lookup"><span data-stu-id="17b57-114">**Process Account**</span></span>  
 <span data-ttu-id="17b57-115">输入运行合并代理所使用的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="17b57-115">Enter a Windows account under which the Merge Agent runs.</span></span>  
  
-   <span data-ttu-id="17b57-116">对于推送订阅，该帐户必须：</span><span class="sxs-lookup"><span data-stu-id="17b57-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="17b57-117">至少是分发数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="17b57-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="17b57-118">是 PAL 的成员。</span><span class="sxs-lookup"><span data-stu-id="17b57-118">Be a member of the PAL.</span></span>  
  
    -   <span data-ttu-id="17b57-119">是与发布数据库中的某个用户关联的登录名。</span><span class="sxs-lookup"><span data-stu-id="17b57-119">Be a login associated with a user in the publication database.</span></span>  
  
    -   <span data-ttu-id="17b57-120">对快照共享拥有读取权限。</span><span class="sxs-lookup"><span data-stu-id="17b57-120">Have read permissions on the snapshot share.</span></span>  
  
-   <span data-ttu-id="17b57-121">对于请求订阅，该帐户必须至少为订阅数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="17b57-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="17b57-122">如果在建立连接时模拟进程帐户，则还需要其他权限。</span><span class="sxs-lookup"><span data-stu-id="17b57-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="17b57-123">请参阅下面的 **“连接到发布服务器和分发服务器”** 和 **“连接到订阅服务器”** 部分。</span><span class="sxs-lookup"><span data-stu-id="17b57-123">See the **Connect to the Publisher and Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="17b57-124">由于 **实例上未运行合并代理，因此不能为对** [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的请求订阅指定“进程帐户”[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)][!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="17b57-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Merge Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="17b57-125">**“密码”** 和 **“确认密码”**</span><span class="sxs-lookup"><span data-stu-id="17b57-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="17b57-126">输入 Windows 帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="17b57-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="17b57-127">**“连接到发布服务器和分发服务器”**</span><span class="sxs-lookup"><span data-stu-id="17b57-127">**Connect to the Publisher and Distributor**</span></span>  
 <span data-ttu-id="17b57-128">对于推送订阅，始终通过模拟在 **“进程帐户”** 文本框中指定的帐户来建立与发布服务器和分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="17b57-128">For push subscriptions, connections to the Publisher and Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="17b57-129">对于请求订阅，请选择合并代理是通过模拟在 **“进程帐户”** 文本框中指定的帐户，还是通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户来建立与发布服务器和分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="17b57-129">For pull subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="17b57-130">如果选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="17b57-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="17b57-131">建议您选择模拟 Windows 帐户，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="17b57-131">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="17b57-132">连接所用的 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户必须：</span><span class="sxs-lookup"><span data-stu-id="17b57-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="17b57-133">是 PAL 的成员。</span><span class="sxs-lookup"><span data-stu-id="17b57-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="17b57-134">是与发布数据库中的某个用户关联的登录名。</span><span class="sxs-lookup"><span data-stu-id="17b57-134">Be a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="17b57-135">是与分发数据库中的用户关联的登录名（用户可以是 Guest 用户）。</span><span class="sxs-lookup"><span data-stu-id="17b57-135">Be a login associated with a user in the distribution database (the user can be the Guest user).</span></span>  
  
-   <span data-ttu-id="17b57-136">对快照共享拥有读取权限。</span><span class="sxs-lookup"><span data-stu-id="17b57-136">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="17b57-137">**“连接到订阅服务器”**</span><span class="sxs-lookup"><span data-stu-id="17b57-137">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="17b57-138">对于请求订阅，始终通过模拟 **“进程帐户”** 文本框中指定的帐户来建立与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="17b57-138">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="17b57-139">对于推送订阅，请选择合并代理是通过模拟在 **“进程帐户”** 文本框中指定的帐户，还是通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户来建立与发布服务器和分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="17b57-139">For push subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="17b57-140">如果选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="17b57-140">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17b57-141">建议您选择模拟 Windows 帐户，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="17b57-141">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="17b57-142">连接订阅服务器所用的 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户必须至少为订阅数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="17b57-142">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b57-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17b57-143">See Also</span></span>  
 <span data-ttu-id="17b57-144">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="17b57-144">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="17b57-145">[复制代理安全模式](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="17b57-145">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="17b57-146">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="17b57-146">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="17b57-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="17b57-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="17b57-148">订阅发布</span><span class="sxs-lookup"><span data-stu-id="17b57-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
