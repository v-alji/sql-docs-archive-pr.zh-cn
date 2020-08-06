---
title: 分发代理安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4342d44a221d9b816a95a283917f005eb018827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578117"
---
# <a name="distribution-agent-security"></a><span data-ttu-id="60700-102">分发代理安全性</span><span class="sxs-lookup"><span data-stu-id="60700-102">Distribution Agent Security</span></span>
  <span data-ttu-id="60700-103">使用 **“分发代理安全性”** 对话框可以指定用于运行分发代理的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="60700-103">The **Distribution Agent Security** dialog box allows you to specify the Windows account under which the Distribution Agent runs.</span></span> <span data-ttu-id="60700-104">对于推送订阅，分发代理在分发服务器上运行；对于请求订阅，分发代理在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="60700-104">The Distribution Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="60700-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户也称为“进程帐户  ”，因为代理进程是在此帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="60700-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="60700-106">该对话框中可用的其他选项取决于访问对话框的方式：</span><span class="sxs-lookup"><span data-stu-id="60700-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="60700-107">如果从新建订阅向导访问该对话框，您还可以指定分发代理在建立与订阅服务器（对于推送订阅）或分发服务器（对于请求订阅）的连接时所使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="60700-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Distribution Agent makes connections to the Subscriber (for push subscriptions) or the Distributor (for pull subscriptions).</span></span> <span data-ttu-id="60700-108">可以通过模拟 Windows 帐户，或在指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户的上下文中建立连接。</span><span class="sxs-lookup"><span data-stu-id="60700-108">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="60700-109">如果从 **“订阅属性”** 对话框访问该对话框，可通过单击该对话框的 **“订阅服务器连接”** 或 **“分发服务器连接”** 行中的属性按钮 ( **...** ) 来指定分发代理建立连接时所使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="60700-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Distribution Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Distributor Connection** row of that dialog box.</span></span> <span data-ttu-id="60700-110">有关访问“订阅属性”  对话框的详细信息，请参阅[查看和修改推送订阅属性](view-and-modify-push-subscription-properties.md)和如何[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="60700-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="60700-111">所有帐户必须是有效的，并且为每个帐户指定了正确的密码。</span><span class="sxs-lookup"><span data-stu-id="60700-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="60700-112">在运行代理之前不会对帐户和密码进行验证。</span><span class="sxs-lookup"><span data-stu-id="60700-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="60700-113">选项</span><span class="sxs-lookup"><span data-stu-id="60700-113">Options</span></span>  
 <span data-ttu-id="60700-114">**进程帐户**</span><span class="sxs-lookup"><span data-stu-id="60700-114">**Process Account**</span></span>  
 <span data-ttu-id="60700-115">输入运行分发代理所使用的 Windows 帐户：</span><span class="sxs-lookup"><span data-stu-id="60700-115">Enter a Windows account under which the Distribution Agent runs:</span></span>  
  
-   <span data-ttu-id="60700-116">对于推送订阅，该帐户必须：</span><span class="sxs-lookup"><span data-stu-id="60700-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="60700-117">至少是分发数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="60700-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="60700-118">是发布访问列表 (PAL) 的成员。</span><span class="sxs-lookup"><span data-stu-id="60700-118">Be a member of the publication access list (PAL).</span></span>  
  
    -   <span data-ttu-id="60700-119">对快照共享拥有读取权限。</span><span class="sxs-lookup"><span data-stu-id="60700-119">Have read permissions on the snapshot share.</span></span>  
  
    -   <span data-ttu-id="60700-120">如果是对非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的订阅，必须对订阅服务器的 OLE DB 访问接口的安装路径具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="60700-120">Have read permissions on the install directory of the OLE DB provider for the Subscriber if the subscription is for a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber.</span></span>  
  
-   <span data-ttu-id="60700-121">对于请求订阅，该帐户必须至少为订阅数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="60700-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="60700-122">如果在建立连接时模拟进程帐户，则还需要其他权限。</span><span class="sxs-lookup"><span data-stu-id="60700-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="60700-123">请参阅下面的 **“连接到分发服务器”** 和 **“连接到订阅服务器”** 部分。</span><span class="sxs-lookup"><span data-stu-id="60700-123">See the **Connect to the Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="60700-124">由于 **的实例上未运行分发代理，因此不能为对** [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的请求订阅指定“进程帐户”[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)][!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="60700-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="60700-125">**“密码”** 和 **“确认密码”**</span><span class="sxs-lookup"><span data-stu-id="60700-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="60700-126">输入 Windows 帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="60700-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="60700-127">**“连接到分发服务器”**</span><span class="sxs-lookup"><span data-stu-id="60700-127">**Connect to the Distributor**</span></span>  
 <span data-ttu-id="60700-128">对于推送订阅，始终通过模拟 **“进程帐户”** 文本框中指定的帐户来建立与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="60700-128">For push subscriptions, connections to the Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="60700-129">对于请求订阅，请选择分发代理是通过模拟在 **“进程帐户”** 文本框中指定的帐户，还是通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户来建立与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="60700-129">For pull subscriptions, select whether the Distribution Agent should make connections to the Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="60700-130">如果选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="60700-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60700-131">建议您选择模拟 Windows 帐户，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="60700-131">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="60700-132">连接所用的 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户必须：</span><span class="sxs-lookup"><span data-stu-id="60700-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="60700-133">是 PAL 的成员。</span><span class="sxs-lookup"><span data-stu-id="60700-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="60700-134">对快照共享拥有读取权限。</span><span class="sxs-lookup"><span data-stu-id="60700-134">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="60700-135">**“连接到订阅服务器”**</span><span class="sxs-lookup"><span data-stu-id="60700-135">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="60700-136">对于请求订阅，始终通过模拟 **“进程帐户”** 文本框中指定的帐户来建立与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="60700-136">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="60700-137">对于推送订阅， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器和非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的选项是不同的：</span><span class="sxs-lookup"><span data-stu-id="60700-137">For push subscriptions, the options are different for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="60700-138">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器：请选择分发代理是通过模拟在 **“进程帐户”** 文本框中指定的帐户，还是通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户来建立与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="60700-138">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers: select whether the Distribution Agent should make connections to the Subscriber by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="60700-139">如果选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="60700-139">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60700-140">建议您选择模拟 Windows 帐户，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="60700-140">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
     <span data-ttu-id="60700-141">连接订阅服务器所用的 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户必须至少为订阅数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="60700-141">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
-   <span data-ttu-id="60700-142">对于非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器，请在订阅服务器上指定当分发代理连接到订阅服务器时所使用的数据库登录名。</span><span class="sxs-lookup"><span data-stu-id="60700-142">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, specify the database login at the Subscriber that should be used when the Distribution Agent connects to the Subscriber.</span></span> <span data-ttu-id="60700-143">该登录名应具有足够的权限以在订阅数据库中创建对象。</span><span class="sxs-lookup"><span data-stu-id="60700-143">The login should have sufficient permissions to create objects in the subscription database.</span></span> <span data-ttu-id="60700-144">有关配置非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的详细信息，请参阅[为非 SQL Server 订阅服务器创建订阅](create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="60700-144">For more information about configuring non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, see [Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
 <span data-ttu-id="60700-145">**其他连接选项**</span><span class="sxs-lookup"><span data-stu-id="60700-145">**Additional connection options**</span></span>  
 <span data-ttu-id="60700-146">仅限非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="60700-146">Non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers only.</span></span> <span data-ttu-id="60700-147">以连接字符串的形式为订阅服务器指定所有连接选项（Oracle 不需要指定附加选项）。</span><span class="sxs-lookup"><span data-stu-id="60700-147">Specify any connection options for the Subscriber in the form of a connection string (Oracle does not require additional options).</span></span> <span data-ttu-id="60700-148">应使用分号分隔每个选项。</span><span class="sxs-lookup"><span data-stu-id="60700-148">Each option should be separated by a semi-colon.</span></span> <span data-ttu-id="60700-149">下面是 IBM DB2 连接字符串的示例（使用分行符是为了提高可读性）：</span><span class="sxs-lookup"><span data-stu-id="60700-149">The following is an example of an IBM DB2 connection string (line breaks are for readability):</span></span>  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 <span data-ttu-id="60700-150">字符串中的大多数选项都特定于正在配置的 DB2 服务器，但是应始终将“将二进制数作为字符处理”  选项设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="60700-150">Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**.</span></span> <span data-ttu-id="60700-151">需要为“初始目录”  选项指定一个值以标识订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="60700-151">A value is required for the **Initial Catalog** option to identify the subscription database.</span></span> <span data-ttu-id="60700-152">有关详细信息，请参阅 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="60700-152">For more information, see [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60700-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60700-153">See Also</span></span>  
 <span data-ttu-id="60700-154">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="60700-154">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="60700-155">[复制代理安全模式](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="60700-155">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="60700-156">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="60700-156">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="60700-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="60700-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="60700-158">订阅发布</span><span class="sxs-lookup"><span data-stu-id="60700-158">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
