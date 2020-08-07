---
title: 保护分发服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Distributors
- Distributors [SQL Server replication], security
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d55f5e214f89b678367124da8342ec9801ab686a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576626"
---
# <a name="secure-the-distributor"></a><span data-ttu-id="45519-102">保护分发服务器的安全</span><span class="sxs-lookup"><span data-stu-id="45519-102">Secure the Distributor</span></span>
  <span data-ttu-id="45519-103">下列复制代理连接到分发服务器：日志读取器代理、快照代理、队列读取器代理、分发代理以及合并代理。</span><span class="sxs-lookup"><span data-stu-id="45519-103">The following replication agents connect to the Distributor: the Log Reader Agent, Snapshot Agent, Queue Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="45519-104">在遵守授予必要的最低权限并保护所有密码的存储这一原则的同时，为每个代理提供适当的登录名非常重要。</span><span class="sxs-lookup"><span data-stu-id="45519-104">It is important to provide an appropriate login for each of these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords:</span></span>  
  
-   <span data-ttu-id="45519-105">有关管理登录名和密码的信息，请参阅[管理复制中的登录名和密码](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)。</span><span class="sxs-lookup"><span data-stu-id="45519-105">For information about managing logins and passwords, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="45519-106">有关每个代理所需权限的详细信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="45519-106">For detailed information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="45519-107">除了适当地管理登录名和密码之外，了解 **repl_distributor** 远程服务器链接和 **distributor_admin** 帐户的角色也很重要。</span><span class="sxs-lookup"><span data-stu-id="45519-107">In addition to managing logins and passwords appropriately, it is important to understand the role of the **repl_distributor** remote server link and the **distributor_admin** account.</span></span>  
  
## <a name="securing-the-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="45519-108">保护发布服务器到分发服务器的连接</span><span class="sxs-lookup"><span data-stu-id="45519-108">Securing the Connection from the Publisher to the Distributor</span></span>  
 <span data-ttu-id="45519-109">为了支持管理存储过程在发布服务器上执行并更新分发服务器中的信息时所要的通信，复制将自动配置远程服务器 **repl_distributor**。</span><span class="sxs-lookup"><span data-stu-id="45519-109">To support the communication necessary when administrative stored procedures execute at the Publisher and update information at the Distributor, replication automatically configures the remote server **repl_distributor**.</span></span> <span data-ttu-id="45519-110">**repl_distributor** 远程服务器项用于与分发数据库的通信，而不管此分发数据库是包含在发布服务器实例（本地分发服务器）内，还是驻留在远程 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例（远程分发服务器）内。</span><span class="sxs-lookup"><span data-stu-id="45519-110">The **repl_distributor** remote server entry is used for communication to the distribution database regardless of whether the distribution database is contained within the Publisher instance (a local Distributor) or resides within a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance (a remote Distributor).</span></span>  
  
 <span data-ttu-id="45519-111">当分发数据库包含在本地实例上时，密码将随机产生并自动配置。</span><span class="sxs-lookup"><span data-stu-id="45519-111">When the distribution database is contained on a local instance, a random password is generated and configured automatically.</span></span> <span data-ttu-id="45519-112">当分发数据库位于远程实例中时，管理员需要在设置发布服务器和分发服务器期间配置共享密码；然后，此密码将用于为遍历 **repl_distributor** 链接的通信流量提供身份验证。</span><span class="sxs-lookup"><span data-stu-id="45519-112">When the distribution database is located on a remote instance, the administrator configures a shared password during setup of the Publisher and Distributor; this password is then used to provide authentication of traffic that traverses the **repl_distributor** link.</span></span>  
  
 <span data-ttu-id="45519-113">分发服务器可以使用 **repl_distributor** 远程服务器项来验证调用服务器是否在分发服务器上配置为发布服务器，可以验证该发布服务器提供的密码并验证存储过程在执行期间是否为复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="45519-113">The Distributor uses the **repl_distributor** remote server entry to verify that the calling server is configured as a Publisher at the Distributor, validates the password supplied by the Publisher, and validates that the stored procedure is a replication stored procedure during execution.</span></span>  
  
 <span data-ttu-id="45519-114">设置期间为 **repl_distributor** 远程服务器项配置的密码与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的登录名 **distributor_admin**相关联，此登录名将添加到分发服务器的 **sysadmin** 固定服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="45519-114">The password configured for the **repl_distributor** remote server entry during setup is associated with a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login, **distributor_admin**, which is added to the **sysadmin** fixed server role at the Distributor.</span></span> <span data-ttu-id="45519-115">连接到分发服务器时，复制存储过程将使用 **distributor_admin** 登录名。</span><span class="sxs-lookup"><span data-stu-id="45519-115">The **distributor_admin** login is used by replication stored procedures when connecting to the Distributor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45519-116">不要手动更改 **distributor_admin** 的密码。</span><span class="sxs-lookup"><span data-stu-id="45519-116">Do not change the password for the **distributor_admin** manually.</span></span> <span data-ttu-id="45519-117">始终使用 **中的** sp_changedistributor_password **存储过程、** “分发服务器属性” **或** “更新复制密码” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]对话框，因为密码更改随后将自动应用到本地发布。</span><span class="sxs-lookup"><span data-stu-id="45519-117">Always use the **sp_changedistributor_password** stored procedure, or the **Distributor Properties** or **Update Replication Passwords** dialog boxes in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], because password changes are then applied to local publications automatically.</span></span>  
  
## <a name="snapshot-folder-security"></a><span data-ttu-id="45519-118">快照文件夹的安全性</span><span class="sxs-lookup"><span data-stu-id="45519-118">Snapshot Folder Security</span></span>  
 <span data-ttu-id="45519-119">确保快照共享将读权限授予合并代理（对于合并发布）或分发代理（对于快照复制或事务复制）运行时所用的帐户，并将写权限授予快照代理运行时所用的帐户。</span><span class="sxs-lookup"><span data-stu-id="45519-119">Ensure that the snapshot share has read access granted to the account under which the Merge Agent (for merge replication) or Distribution Agent (for snapshot or transactional replication) runs and write access granted to the account under which the Snapshot Agent runs.</span></span> <span data-ttu-id="45519-120">有关快照文件夹的详细信息，请参阅[保护快照文件夹](secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="45519-120">For more information about the snapshot folder, see [Secure the Snapshot Folder](secure-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45519-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45519-121">See Also</span></span>  
 <span data-ttu-id="45519-122">[查看和修改复制安全设置](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="45519-122">[View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="45519-123">[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="45519-123">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="45519-124">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="45519-124">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="45519-125">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="45519-125">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
