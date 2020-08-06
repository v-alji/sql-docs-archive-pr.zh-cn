---
title: 备份和还原 Reporting Services 加密密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backing up encryption keys [Reporting Services]
- restoring encryption keys [Reporting Services]
- encryption keys [Reporting Services]
- symmetric keys [Reporting Services]
ms.assetid: 6773d5df-03ef-4781-beb7-9f6825bac979
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8e7e61f58632898fc6150210598a671157639a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694309"
---
# <a name="back-up-and-restore-reporting-services-encryption-keys"></a><span data-ttu-id="5d0be-102">备份和还原 Reporting Services 加密密钥</span><span class="sxs-lookup"><span data-stu-id="5d0be-102">Back Up and Restore Reporting Services Encryption Keys</span></span>
  <span data-ttu-id="5d0be-103">报表服务器配置的一个重要部分是为用于加密敏感信息的对称密钥创建备份副本。</span><span class="sxs-lookup"><span data-stu-id="5d0be-103">An important part of report server configuration is creating a backup copy of the symmetric key used for encrypting sensitive information.</span></span> <span data-ttu-id="5d0be-104">该密钥的备份副本对许多例程操作来说是必需的，通过使用备份副本，您可以在新的安装中重用现有报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="5d0be-104">A backup copy of the key is required for many routine operations, and enables you to reuse an existing report server database in a new installation.</span></span>  
  
 <span data-ttu-id="5d0be-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="5d0be-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="5d0be-106">在发生以下任何事件时，必须还原加密密钥的备份副本：</span><span class="sxs-lookup"><span data-stu-id="5d0be-106">It is necessary to restore the backup copy of the encryption key when any of the following events occur:</span></span>  
  
-   <span data-ttu-id="5d0be-107">更改报表服务器 Windows 服务帐户名或重置密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-107">Changing the Report Server Windows service account name or resetting the password.</span></span> <span data-ttu-id="5d0be-108">使用 Reporting Services 配置管理器时，对密钥进行备份是服务帐户名称更改操作的一部分。</span><span class="sxs-lookup"><span data-stu-id="5d0be-108">When you use the Reporting Services Configuration Manager, backing up the key is part of a service account name change operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d0be-109">重置密码不同于更改密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-109">Resetting the password is not the same as changing the password.</span></span> <span data-ttu-id="5d0be-110">密码重置需要相应的权限以覆盖域控制器上的帐户信息。</span><span class="sxs-lookup"><span data-stu-id="5d0be-110">A password reset requires permission to overwrite account information on the domain controller.</span></span> <span data-ttu-id="5d0be-111">密码重置在您忘记或不知道特定密码时由系统管理员执行。</span><span class="sxs-lookup"><span data-stu-id="5d0be-111">Password resets are performed by a system administrator when you forget or do not know a particular password.</span></span> <span data-ttu-id="5d0be-112">只有密码重置才需要还原对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-112">Only password resets require symmetric key restoration.</span></span> <span data-ttu-id="5d0be-113">定期更改帐户密码不需要重置对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-113">Periodically changing an account password does not require you to reset the symmetric key.</span></span>  
  
-   <span data-ttu-id="5d0be-114">重命名承载报表服务器的计算机或实例（报表服务器实例基于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名）。</span><span class="sxs-lookup"><span data-stu-id="5d0be-114">Renaming the computer or instance that hosts the report server (a report server instance is based on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name).</span></span>  
  
-   <span data-ttu-id="5d0be-115">迁移报表服务器安装或配置报表服务器以使用其他报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="5d0be-115">Migrating a report server installation or configuring a report server to use a different report server database.</span></span>  
  
-   <span data-ttu-id="5d0be-116">由于硬件故障而恢复报表服务器安装。</span><span class="sxs-lookup"><span data-stu-id="5d0be-116">Recovering a report server installation due to hardware failure.</span></span>  
  
 <span data-ttu-id="5d0be-117">只需要备份对称密钥的一个副本。</span><span class="sxs-lookup"><span data-stu-id="5d0be-117">You only need to back up one copy of the symmetric key.</span></span> <span data-ttu-id="5d0be-118">报表服务器数据库和对称密钥之间存在一对一的对应关系。</span><span class="sxs-lookup"><span data-stu-id="5d0be-118">There is a one-to-one correspondence between a report server database and a symmetric key.</span></span> <span data-ttu-id="5d0be-119">尽管只需要备份一个副本，但如果在扩展部署模型中运行多个报表服务器，则可能需要多次还原密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-119">Although you only need to back up one copy, you might need to restore the key multiple times if you are running multiple report servers in a scale-out deployment model.</span></span> <span data-ttu-id="5d0be-120">每个报表服务器实例都需要具有自己的对称密钥副本，才能对报表服务器数据库中的数据进行锁定和解锁。</span><span class="sxs-lookup"><span data-stu-id="5d0be-120">Each report server instance will need its copy of the symmetric key to lock and unlock data in the report server database.</span></span>  
  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="5d0be-121">备份加密密钥</span><span class="sxs-lookup"><span data-stu-id="5d0be-121">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="5d0be-122">备份对称密钥是将密钥写入所指定的文件，然后使用所提供的密码对密钥进行加密的过程。</span><span class="sxs-lookup"><span data-stu-id="5d0be-122">Backing up the symmetric key is a process that writes the key to a file that you specify, and then scrambles the key using a password that you provide.</span></span> <span data-ttu-id="5d0be-123">对称密钥绝对不能在未加密状态下存储，所以在将它保存到磁盘时，必须提供密码对密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="5d0be-123">The symmetric key can never be stored in an unencrypted state so you must provide a password to encrypt the key when you save it to disk.</span></span> <span data-ttu-id="5d0be-124">创建文件后，必须将其存储在安全的位置， **并记住文件的解锁密码** 。</span><span class="sxs-lookup"><span data-stu-id="5d0be-124">After the file is created, you must store it in a secure location **and remember the password** that is used to unlock the file.</span></span> <span data-ttu-id="5d0be-125">若要备份对称密钥，可以使用以下工具：</span><span class="sxs-lookup"><span data-stu-id="5d0be-125">To backup the symmetric key, you can use the following tools:</span></span>  
  
 <span data-ttu-id="5d0be-126">**本机模式：** Reporting Services 配置管理器或 **rskeymgmt** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="5d0be-126">**Native mode:** Either the Reporting Services Configuration Manager or the **rskeymgmt** utility.</span></span>  
  
 <span data-ttu-id="5d0be-127">**SharePoint 模式：** SharePoint 管理中心页或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5d0be-127">**SharePoint mode:** SharePoint Central Administration pages or PowerShell.</span></span>  
  
####  <a name="backup-sharepoint-mode-report-servers"></a><a name="bkmk_backup_sharepoint"></a> <span data-ttu-id="5d0be-128">备份 SharePoint 模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="5d0be-128">Backup SharePoint Mode Report Servers</span></span>  
 <span data-ttu-id="5d0be-129">对于 SharePoint 模式报表服务器，您可以使用 PowerShell 命令或使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的管理页。</span><span class="sxs-lookup"><span data-stu-id="5d0be-129">For SharePoint mode report servers you can either use PowerShell commands or use the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="5d0be-130">有关详细信息，请参阅 [管理 Reporting Services SharePoint 服务应用程序](../manage-a-reporting-services-sharepoint-service-application.md)的“密钥管理”部分</span><span class="sxs-lookup"><span data-stu-id="5d0be-130">For more information, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md)</span></span>  
  
####  <a name="back-up-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_backup_configuration_manager"></a> <span data-ttu-id="5d0be-131">备份加密密钥 - Reporting Services 配置管理器（本机模式）</span><span class="sxs-lookup"><span data-stu-id="5d0be-131">Back up encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="5d0be-132">启动 Reporting Services 配置管理器，然后连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="5d0be-132">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="5d0be-133">单击 **“加密密钥”**，再单击 **“备份”**。</span><span class="sxs-lookup"><span data-stu-id="5d0be-133">Click **Encryption Keys**, and then click **Back Up**.</span></span>  
  
3.  <span data-ttu-id="5d0be-134">键入强密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-134">Type a strong password.</span></span>  
  
4.  <span data-ttu-id="5d0be-135">指定用来包含所存储密钥的文件。</span><span class="sxs-lookup"><span data-stu-id="5d0be-135">Specify a file to contain the stored key.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5d0be-136">将向该文件追加 .snk 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="5d0be-136">appends a .snk file extension to the file.</span></span> <span data-ttu-id="5d0be-137">请考虑将文件存储在独立于报表服务器的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="5d0be-137">Consider storing the file on a disk separate from the report server.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="back-up-encryption-keys--rskeymgmt-native-mode"></a><a name="bkmk_backup_rskeymgmt"></a><span data-ttu-id="5d0be-138">备份加密密钥-rskeymgmt (纯模式) </span><span class="sxs-lookup"><span data-stu-id="5d0be-138">Back up encryption keys -rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="5d0be-139">在承载报表服务器的计算机上本地运行 **rskeymgmt.exe** 。</span><span class="sxs-lookup"><span data-stu-id="5d0be-139">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="5d0be-140">必须使用 `-e` 提取参数复制密钥，提供文件名并指定密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-140">You must use the `-e` extract argument to copy the key, provide a file name, and specify a password.</span></span> <span data-ttu-id="5d0be-141">下面的示例演示必须指定的参数：</span><span class="sxs-lookup"><span data-stu-id="5d0be-141">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -e -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="restore-encryption-keys"></a><span data-ttu-id="5d0be-142">还原加密密钥</span><span class="sxs-lookup"><span data-stu-id="5d0be-142">Restore Encryption Keys</span></span>  
 <span data-ttu-id="5d0be-143">还原对称密钥将覆盖存储在报表服务器数据库中的现有对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-143">Restoring the symmetric key overwrites the existing symmetric key that is stored in the report server database.</span></span> <span data-ttu-id="5d0be-144">还原加密密钥将用以前保存到磁盘上的副本来替换无法使用的密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-144">Restoring an encryption key replaces an unusable key with a copy that you previously saved to disk.</span></span> <span data-ttu-id="5d0be-145">还原加密密钥将导致以下操作：</span><span class="sxs-lookup"><span data-stu-id="5d0be-145">Restoring encryption keys results in the following actions:</span></span>  
  
-   <span data-ttu-id="5d0be-146">从密码保护的备份文件中打开对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-146">The symmetric key is opened from the password protected backup file.</span></span>  
  
-   <span data-ttu-id="5d0be-147">使用报表服务器 Windows 服务的公钥加密对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-147">The symmetric key is encrypted using the public key of the Report Server Windows service.</span></span>  
  
-   <span data-ttu-id="5d0be-148">将加密的对称密钥存储到报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="5d0be-148">The encrypted symmetric key is stored in the report server database.</span></span>  
  
-   <span data-ttu-id="5d0be-149">删除以前存储的对称密钥数据（例如，在以前部署的报表服务器数据库中已存在的密钥信息）。</span><span class="sxs-lookup"><span data-stu-id="5d0be-149">The previously stored symmetric key data (for example, key information that was already in the report server database from a previous deployment) is deleted.</span></span>  
  
 <span data-ttu-id="5d0be-150">若要还原加密密钥，必须具有保存在文件中的加密密钥副本。</span><span class="sxs-lookup"><span data-stu-id="5d0be-150">To restore the encryption key, you must have a copy of the encryption key on file.</span></span> <span data-ttu-id="5d0be-151">还必须知道用来对存储的副本进行解锁的密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-151">You must also know the password that unlocks the stored copy.</span></span> <span data-ttu-id="5d0be-152">如果您具有密钥和密码，则可以运行 Reporting Services 配置工具或 **rskeymgmt** 实用工具来还原密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-152">If you have the key and the password, you can run the Reporting Services Configuration tool or **rskeymgmt** utility to restore the key.</span></span> <span data-ttu-id="5d0be-153">该对称密钥必须与用来对报表服务器数据库中当前存储的加密数据进行锁定和解锁的密钥相同。</span><span class="sxs-lookup"><span data-stu-id="5d0be-153">The symmetric key must be the same one that locks and unlocks encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="5d0be-154">如果还原的副本无效，则报表服务器将无法访问报表服务器数据库中当前存储的加密数据。</span><span class="sxs-lookup"><span data-stu-id="5d0be-154">If you restore a copy that is not valid, the report server cannot access the encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="5d0be-155">在这种情况下，如果无法恢复有效的密钥，则最好删除所有加密值。</span><span class="sxs-lookup"><span data-stu-id="5d0be-155">If this occurs, you might need to delete all encrypted values if you cannot restore a valid key.</span></span> <span data-ttu-id="5d0be-156">如果由于某些原因（例如，如果没有备份副本）而无法还原加密密钥，则必须删除现有密钥和加密内容。</span><span class="sxs-lookup"><span data-stu-id="5d0be-156">If for some reason you cannot restore the encryption key (for example, if you do not have a backup copy), you must delete the existing key and encrypted content.</span></span> <span data-ttu-id="5d0be-157">有关详细信息，请参阅[删除和重新创建加密密钥（SSRS 配置管理器）](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="5d0be-157">For more information, see [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md).</span></span> <span data-ttu-id="5d0be-158">有关如何创建对称密钥的详细信息，请参阅[初始化报表服务器（SSRS 配置管理器）](ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5d0be-158">For more information about creating symmetric keys, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
####  <a name="restore-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_restore_configuration_manager"></a> <span data-ttu-id="5d0be-159">还原加密密钥 - Reporting Services 配置管理器（本机模式）</span><span class="sxs-lookup"><span data-stu-id="5d0be-159">Restore encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="5d0be-160">启动 Reporting Services 配置管理器，然后连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="5d0be-160">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="5d0be-161">在 "加密密钥" 页上，单击 "**还原**"。</span><span class="sxs-lookup"><span data-stu-id="5d0be-161">On the Encryption Keys page, click **Restore**.</span></span>  
  
3.  <span data-ttu-id="5d0be-162">选择包含备份副本的 .snk 文件。</span><span class="sxs-lookup"><span data-stu-id="5d0be-162">Select the .snk file that contains the back up copy.</span></span>  
  
4.  <span data-ttu-id="5d0be-163">键入用于解锁该文件的密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-163">Type the password that unlocks the file.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="restore-encryption-keys---rskeymgmt-native-mode"></a><a name="bkmk_restore_rskeymgmt"></a> <span data-ttu-id="5d0be-164">还原加密密钥 - rskeymgmt（本机模式）</span><span class="sxs-lookup"><span data-stu-id="5d0be-164">Restore encryption keys - rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="5d0be-165">在承载报表服务器的计算机上本地运行 **rskeymgmt.exe** 。</span><span class="sxs-lookup"><span data-stu-id="5d0be-165">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="5d0be-166">使用 `-a` 参数还原密钥。</span><span class="sxs-lookup"><span data-stu-id="5d0be-166">Use the `-a` argument to restore the keys.</span></span> <span data-ttu-id="5d0be-167">必须提供完全限定的文件名，并指定密码。</span><span class="sxs-lookup"><span data-stu-id="5d0be-167">You must provide a fully-qualified file name and specify a password.</span></span> <span data-ttu-id="5d0be-168">下面的示例演示必须指定的参数：</span><span class="sxs-lookup"><span data-stu-id="5d0be-168">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -a -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5d0be-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d0be-169">See Also</span></span>  
 [<span data-ttu-id="5d0be-170">配置和管理加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="5d0be-170">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
