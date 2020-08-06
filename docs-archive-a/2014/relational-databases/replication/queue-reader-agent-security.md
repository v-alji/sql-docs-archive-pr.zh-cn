---
title: 队列读取器代理安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22a5e5751184b626ab1af86f01782a42028b5ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590172"
---
# <a name="queue-reader-agent-security"></a><span data-ttu-id="bfb96-102">队列读取器代理安全性</span><span class="sxs-lookup"><span data-stu-id="bfb96-102">Queue Reader Agent Security</span></span>
  <span data-ttu-id="bfb96-103">可以使用 **“队列读取器代理安全性”** 对话框，指定用于运行队列读取器代理以及与分发服务器建立本地连接的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="bfb96-103">The **Queue Reader Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Queue Reader Agent runs and makes local connections to the Distributor.</span></span> <span data-ttu-id="bfb96-104">代理使用 **“发布服务器属性”** 对话框（可通过 **“分发服务器属性”** 对话框访问）中指定的帐户连接发布服务器；代理使用与订阅的分发代理相同的上下文连接订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="bfb96-104">The agent connects to the Publisher using the account specified in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box); the agent connects to the Subscriber using the same context as the Distribution Agent for the subscription.</span></span> <span data-ttu-id="bfb96-105">有关详细信息，请参阅 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb96-105">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="bfb96-106">帐户必须有效，并为帐户指定正确的密码。</span><span class="sxs-lookup"><span data-stu-id="bfb96-106">The account must be valid with the correct password specified.</span></span> <span data-ttu-id="bfb96-107">在运行代理之前不会对帐户和密码进行验证。</span><span class="sxs-lookup"><span data-stu-id="bfb96-107">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfb96-108">选项</span><span class="sxs-lookup"><span data-stu-id="bfb96-108">Options</span></span>  
 <span data-ttu-id="bfb96-109">**进程帐户**</span><span class="sxs-lookup"><span data-stu-id="bfb96-109">**Process account**</span></span>  
 <span data-ttu-id="bfb96-110">输入在分发服务器上运行队列读取器代理所用的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="bfb96-110">Enter a Windows account under which the Queue Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="bfb96-111">指定的 Windows 帐户必须至少为分发数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="bfb96-111">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="bfb96-112">**“密码”** 和 **“确认密码”**</span><span class="sxs-lookup"><span data-stu-id="bfb96-112">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="bfb96-113">输入 Windows 帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="bfb96-113">Enter the password for the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb96-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfb96-114">See Also</span></span>  
 <span data-ttu-id="bfb96-115">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="bfb96-115">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="bfb96-116">[复制代理安全模式](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="bfb96-116">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="bfb96-117">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="bfb96-117">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="bfb96-118">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="bfb96-118">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
