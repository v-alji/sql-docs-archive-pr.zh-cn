---
title: 快照代理安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 288dc294b7ace9ea5cb098c8deec53c3ae4569a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591241"
---
# <a name="snapshot-agent-security"></a><span data-ttu-id="0ba33-102">快照代理安全性</span><span class="sxs-lookup"><span data-stu-id="0ba33-102">Snapshot Agent Security</span></span>
  <span data-ttu-id="0ba33-103">可以使用 **“快照代理安全性”** 对话框指定以下内容：</span><span class="sxs-lookup"><span data-stu-id="0ba33-103">The **Snapshot Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="0ba33-104">用于在分发服务器上运行快照代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="0ba33-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="0ba33-105">Windows 帐户也称为“进程帐户  ”，因为代理进程是在此帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="0ba33-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="0ba33-106">快照代理与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器建立连接时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="0ba33-106">The context under which the Snapshot Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="0ba33-107">通过模拟 Windows 帐户，或在指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户的上下文中可以进行连接。</span><span class="sxs-lookup"><span data-stu-id="0ba33-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ba33-108">即使发布服务器与分发服务器在同一台计算机上，快照代理也会与发布服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="0ba33-108">The Snapshot Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="0ba33-109">快照代理还可以与分发服务器建立连接；这些连接始终是通过模拟运行代理的 Windows 帐户来建立的。</span><span class="sxs-lookup"><span data-stu-id="0ba33-109">The Snapshot Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="0ba33-110">对于 Oracle 发布服务器，请在 **“发布服务器属性”** 对话框（可以通过 **“分发服务器属性”** 对话框访问）中指定快照代理连接发布服务器时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="0ba33-110">For Oracle Publishers, specify the context under which the Snapshot Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="0ba33-111">有关详细信息，请参阅 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba33-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="0ba33-112">所有帐户必须是有效的，并且为每个帐户指定了正确的密码。</span><span class="sxs-lookup"><span data-stu-id="0ba33-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="0ba33-113">在运行代理之前不会对帐户和密码进行验证。</span><span class="sxs-lookup"><span data-stu-id="0ba33-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ba33-114">选项</span><span class="sxs-lookup"><span data-stu-id="0ba33-114">Options</span></span>  
 <span data-ttu-id="0ba33-115">**进程帐户**</span><span class="sxs-lookup"><span data-stu-id="0ba33-115">**Process account**</span></span>  
 <span data-ttu-id="0ba33-116">输入用于在分发服务器上运行快照代理的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="0ba33-116">Enter a Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="0ba33-117">所指定的 Windows 帐户必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="0ba33-117">The Windows account you specify must:</span></span>  
  
-   <span data-ttu-id="0ba33-118">至少是分发数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="0ba33-118">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
-   <span data-ttu-id="0ba33-119">对快照共享具有写权限。</span><span class="sxs-lookup"><span data-stu-id="0ba33-119">Have write permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="0ba33-120">**“密码”** 和 **“确认密码”**</span><span class="sxs-lookup"><span data-stu-id="0ba33-120">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="0ba33-121">输入 Windows 帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="0ba33-121">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="0ba33-122">**连接到发布服务器**</span><span class="sxs-lookup"><span data-stu-id="0ba33-122">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="0ba33-123">选择快照代理应该通过模拟 **“进程帐户”** 文本框中指定的帐户，还是通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户来建立与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="0ba33-123">Select whether the Snapshot Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="0ba33-124">如果选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="0ba33-124">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ba33-125">建议您选择模拟 Windows 帐户，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="0ba33-125">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="0ba33-126">用于连接的 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户至少必须是发布数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="0ba33-126">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba33-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ba33-127">See Also</span></span>  
 <span data-ttu-id="0ba33-128">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="0ba33-128">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="0ba33-129">[复制代理安全模式](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="0ba33-129">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="0ba33-130">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0ba33-130">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="0ba33-131">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="0ba33-131">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
