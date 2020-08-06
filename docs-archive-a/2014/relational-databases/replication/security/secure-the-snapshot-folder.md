---
title: 保护快照文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c977936ad2aca6e5a98ee685a15662a00b625494
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588969"
---
# <a name="secure-the-snapshot-folder"></a><span data-ttu-id="2ea51-102">保护快照文件夹的安全</span><span class="sxs-lookup"><span data-stu-id="2ea51-102">Secure the Snapshot Folder</span></span>
  <span data-ttu-id="2ea51-103">快照文件夹是存储快照文件的目录；建议将该目录专门用于存储快照。</span><span class="sxs-lookup"><span data-stu-id="2ea51-103">The snapshot folder is a directory that stores snapshot files; it is recommended that you dedicate the directory for snapshot storage.</span></span> <span data-ttu-id="2ea51-104">请授予快照代理对该文件夹的写入权限，并确保仅为合并代理或分发代理访问文件夹时所用的 Windows 帐户授予读取权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-104">Grant the Snapshot Agent write permission to the folder, and ensure that read permission is granted only to the Windows account that the Merge Agent or Distribution agent uses when accessing the folder.</span></span> <span data-ttu-id="2ea51-105">与该代理相关联的 Windows 帐户必须是访问远程计算机上快照文件夹的域帐户。</span><span class="sxs-lookup"><span data-stu-id="2ea51-105">The Windows account associated with the agent must be a domain account to access a snapshot folder that is located on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ea51-106">用户帐户控制 (UAC) 可帮助管理员管理其提升的用户权限（有时称为“特权”） 。</span><span class="sxs-lookup"><span data-stu-id="2ea51-106">User Account Control (UAC)  helps administrators manage their elevated user rights (sometimes called *privileges*).</span></span> <span data-ttu-id="2ea51-107">在启用 UAC 的操作系统上运行时，管理员并不使用其管理权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-107">When running on operating systems that have UAC enabled, administrators do not use their administrative rights.</span></span> <span data-ttu-id="2ea51-108">相反，他们以标准（非管理）用户的身份执行大多数操作，仅在必要时临时采用其管理权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-108">Instead, they perform most actions as standard (non-administrative) users, temporarily assuming their administrative rights only when it is required.</span></span> <span data-ttu-id="2ea51-109">UAC 可以防止对快照共享的管理访问。</span><span class="sxs-lookup"><span data-stu-id="2ea51-109">UAC can prevent administrative access to the snapshot share.</span></span> <span data-ttu-id="2ea51-110">因此，必须对快照代理、分发代理和合并代理使用的 Windows 帐户显式授予快照共享权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-110">You must therefore explicitly grant snapshot share permissions to the Windows accounts that are used by the Snapshot Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="2ea51-111">即使 Windows 帐户是管理员组的成员，也必须执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2ea51-111">You must do this even if the Windows accounts are members of the Administrators group.</span></span>  
  
 <span data-ttu-id="2ea51-112">当通过“配置分发向导”或“新建发布向导”来配置分发服务器时，快照文件夹默认为本地路径：X:\Program Files\Microsoft SQL Server\\\<instance>\MSSQL\ReplData。</span><span class="sxs-lookup"><span data-stu-id="2ea51-112">When configuring a Distributor through the Configure Distribution Wizard or the New Publication Wizard, the snapshot folder defaults to a local path: X:\Program Files\Microsoft SQL Server\\*\<instance>* \MSSQL\ReplData.</span></span> <span data-ttu-id="2ea51-113">如果使用远程分发服务器或请求订阅，则必须指定 UNC 网络共享路径（如 \\\\<*computername>* \snapshot），而非本地路径。</span><span class="sxs-lookup"><span data-stu-id="2ea51-113">If you are using a remote Distributor or pull subscriptions, you must specify a UNC network share (such as \\\\<*computername>* \snapshot) rather than a local path.</span></span>  
  
 <span data-ttu-id="2ea51-114">授予对快照文件夹的访问权限时，必须根据对文件夹的访问方式来进行授权。</span><span class="sxs-lookup"><span data-stu-id="2ea51-114">When granting permissions to access the snapshot folder, you must grant them according to the way in which the folder is accessed.</span></span> <span data-ttu-id="2ea51-115">下面列出了在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003 中使用的对话框选项卡：</span><span class="sxs-lookup"><span data-stu-id="2ea51-115">The following dialog box tabs are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003:</span></span>  
  
-   <span data-ttu-id="2ea51-116">如果指定本地路径，则可通过该文件夹的 **“属性”** 对话框的 **“安全性”** 选项卡授予权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-116">If you specify a local path, grant permissions through the **Security** tab of the **Properties** dialog box for the folder.</span></span>  
  
-   <span data-ttu-id="2ea51-117">如果指定网络共享，则可通过该文件夹的 **“属性”** 对话框的 **“共享”** 选项卡授予权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-117">If you specify a network share, grant permissions through the **Sharing** tab of the **Properties** dialog box for the folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ea51-118">如果复制代理在分发服务器上运行，则可使用该文件夹的 **“属性”** 对话框的 **“安全性”** 选项卡对用于运行代理的 Windows 帐户授予权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-118">If the replication agent runs on the Distributor, use the **Security** tab of the **Properties** dialog box for the folder to grant permissions to the Windows account used to run the agent.</span></span> <span data-ttu-id="2ea51-119">即使使用网络共享也如此。</span><span class="sxs-lookup"><span data-stu-id="2ea51-119">Do this even when a network share is used.</span></span> <span data-ttu-id="2ea51-120">当发布服务器和分发服务器位于同一台计算机上时，这一点适用于推送订阅的合并代理和分发代理，也适用于快照代理。</span><span class="sxs-lookup"><span data-stu-id="2ea51-120">This applies to the Merge Agent and Distribution Agent for a push subscription and to the Snapshot Agent when the Publisher and Distributor are on the same computer.</span></span>  
  
 <span data-ttu-id="2ea51-121">有关为本地路径和网络共享设置权限的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="2ea51-121">For more information about setting permissions for local paths and network shares, see the Windows documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ea51-122">如果删除发布，复制将尝试在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户的安全上下文中删除快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="2ea51-122">If a publication is dropped, replication attempts to remove the snapshot folder under the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account.</span></span> <span data-ttu-id="2ea51-123">如果此帐户没有足够的权限，请用具有足够权限的帐户登录，然后手动删除文件夹。</span><span class="sxs-lookup"><span data-stu-id="2ea51-123">If this account does not have sufficient privileges, log in with an account that does have sufficient privileges and remove the folder manually.</span></span> <span data-ttu-id="2ea51-124">如果文件夹为本地路径，则删除文件夹需要“修改”  权限；如果文件夹为网络路径，则删除文件夹需要“完全控制”  权限。</span><span class="sxs-lookup"><span data-stu-id="2ea51-124">Removing a folder requires the **Modify** privilege if the folder is a local path or the **Full Control** privilege if the folder is a network path.</span></span>  
  
## <a name="delivering-snapshots-through-ftp"></a><span data-ttu-id="2ea51-125">通过 FTP 传递快照</span><span class="sxs-lookup"><span data-stu-id="2ea51-125">Delivering Snapshots Through FTP</span></span>  
 <span data-ttu-id="2ea51-126">建议您采用最安全的方法：将快照存储在 UNC 共享目录中。但也可以将快照存储在 FTP 共享目录中，然后再通过 FTP 传递给订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="2ea51-126">It is recommended as a security best practice that snapshots be stored in a UNC share, but snapshots can be stored in an FTP share and then delivered to a Subscriber through FTP.</span></span> <span data-ttu-id="2ea51-127">配置 FTP 服务器时，请确保虚拟目录公开一个基本 UNC 共享目录，该共享目录允许用于发布的快照代理进行写访问。</span><span class="sxs-lookup"><span data-stu-id="2ea51-127">When configuring the FTP server, ensure that the virtual directory exposes an underlying UNC share that permits write access by the Snapshot Agent for the publication.</span></span>  
  
 <span data-ttu-id="2ea51-128">若要配置订阅服务器以通过 FTP 检索快照，请先用一个 FTP 登录名和密码设置 FTP 服务器，该 FTP 服务器允许订阅服务器进行读（或“获取”）访问，以便下载快照文件。</span><span class="sxs-lookup"><span data-stu-id="2ea51-128">To configure a Subscriber to retrieve the Snapshot via FTP, first set up an FTP server with an FTP login and password that allows Subscribers read (or "get") access to allow the snapshot files to be downloaded.</span></span>  
  
 <span data-ttu-id="2ea51-129">若要通过 FTP 传递快照，请参阅[通过 FTP 传递快照](../publish/deliver-a-snapshot-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="2ea51-129">To deliver snapshots through FTP, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
 <span data-ttu-id="2ea51-130">有关设置和更改通过 FTP 访问快照的密码的信息，请参阅 [Secure the Publisher](secure-the-publisher.md)主题中的“FTP 快照传递”一节。</span><span class="sxs-lookup"><span data-stu-id="2ea51-130">For information about setting and changing the password for access to snapshots through FTP, see the section "FTP Snapshot Delivery" in the topic [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea51-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ea51-131">See Also</span></span>  
 <span data-ttu-id="2ea51-132">[备用快照文件夹位置](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="2ea51-132">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="2ea51-133">[使用快照初始化订阅](../initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="2ea51-133">[Initialize a Subscription with a Snapshot](../initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="2ea51-134">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="2ea51-134">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="2ea51-135">[SQL Server 复制安全性](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2ea51-135">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="2ea51-136">通过 FTP 传输快照</span><span class="sxs-lookup"><span data-stu-id="2ea51-136">Transfer Snapshots Through FTP</span></span>](../transfer-snapshots-through-ftp.md)  
  
  
