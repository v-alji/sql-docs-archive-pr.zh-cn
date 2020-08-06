---
title: 备份和还原 Reporting Services SharePoint 服务应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488659d269542381be9bcf1b1b6115acf89f8a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586513"
---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a><span data-ttu-id="02be0-102">备份和还原 Reporting Services SharePoint 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-102">Backup and Restore Reporting Services SharePoint Service Applications</span></span>
  <span data-ttu-id="02be0-103">本主题说明如何使用 SharePoint 管理中心或 PowerShell 备份和还原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-103">This topic describes how to backup and restore a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services application using SharePoint Central Administration or PowerShell.</span></span> <span data-ttu-id="02be0-104">本主题包含：</span><span class="sxs-lookup"><span data-stu-id="02be0-104">The topic contains:</span></span>  
  
-   [<span data-ttu-id="02be0-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="02be0-105">Limitations and Restrictions</span></span>](#bkmk_Restrictions)  
  
-   [<span data-ttu-id="02be0-106">备份服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-106">Backup The Service application</span></span>](#bkmk_backup)  
  
-   [<span data-ttu-id="02be0-107">还原服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-107">Restore the Service Application</span></span>](#bkmk_restore)  
  
##  <a name="before-you-begin"></a><a name="bkmk_BeforeYouBegin"></a> <span data-ttu-id="02be0-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="02be0-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="bkmk_Restrictions"></a> <span data-ttu-id="02be0-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="02be0-109">Limitations and Restrictions</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02be0-110">通过使用 SharePoint 备份和还原功能，可以部分地备份和还原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications can partially be backed up and restored using the SharePoint backup and restore functionality.</span></span> <span data-ttu-id="02be0-111">**需要执行其他步骤** ，本主题中介绍了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="02be0-111">**Additional steps are required** and the steps are documented in this topic.</span></span> <span data-ttu-id="02be0-112">备份过程当前 **不** 备份无人参与的执行帐户 (UEA) 或对 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 数据库的 Windows 身份验证的加密密钥和凭据。</span><span class="sxs-lookup"><span data-stu-id="02be0-112">Currently the backup process **does not** backup encryption keys and credentials for unattended execution accounts (UEA) or windows authentication to the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] database.</span></span>  
  
###  <a name="recommendations"></a><a name="bkmk_recommendations"></a> <span data-ttu-id="02be0-113">建议</span><span class="sxs-lookup"><span data-stu-id="02be0-113">Recommendations</span></span>  
  
-   <span data-ttu-id="02be0-114">启动 SharePoint 备份之前备份加密密钥。</span><span class="sxs-lookup"><span data-stu-id="02be0-114">Backup the encryption keys before starting the SharePoint backup.</span></span> <span data-ttu-id="02be0-115">如果您没有备份加密密钥，则在还原服务应用程序之后将无法访问加密的数据。</span><span class="sxs-lookup"><span data-stu-id="02be0-115">If you do not backup the encryption keys, then you will not be able to access your encrypted data, following the restore of the service application.</span></span> <span data-ttu-id="02be0-116">您将需要删除加密数据。</span><span class="sxs-lookup"><span data-stu-id="02be0-116">You will need to delete your encrypted data.</span></span>  
  
-   <span data-ttu-id="02be0-117">验证您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序是正在使用 UEA 还是 Windows 身份验证来访问数据库。</span><span class="sxs-lookup"><span data-stu-id="02be0-117">Verify if your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application is using UEA or Windows authentication for database access.</span></span> <span data-ttu-id="02be0-118">如果正在使用其中一个，请验证正确的凭据，以便在还原过程之后可以正确地配置该服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-118">If it is using either, verify what the proper credentials are so you can correctly configure the service application after the restore process.</span></span>  
  
-   <span data-ttu-id="02be0-119">查看在与备份文件相同的文件夹中创建的 SharePoint 备份日志。</span><span class="sxs-lookup"><span data-stu-id="02be0-119">Review the SharePoint backup log is created in the same folder as the backup file.</span></span> <span data-ttu-id="02be0-120">该文件通常名为 **spbackup.log**</span><span class="sxs-lookup"><span data-stu-id="02be0-120">The file is typically named **spbackup.log**</span></span>  
  
##  <a name="backup-the-service-application"></a><a name="bkmk_backup"></a><span data-ttu-id="02be0-121">备份服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-121">Backup The Service application</span></span>  
 <span data-ttu-id="02be0-122">请按顺序完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="02be0-122">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="02be0-123">备份加密密钥</span><span class="sxs-lookup"><span data-stu-id="02be0-123">Backup the encryption keys</span></span>  
  
2.  <span data-ttu-id="02be0-124">备份服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-124">Backup the Service application</span></span>  
  
3.  <span data-ttu-id="02be0-125">验证您的服务应用程序是使用 UEA 还是 Windows 身份验证来访问数据库。</span><span class="sxs-lookup"><span data-stu-id="02be0-125">Verify if you service application uses an UEA or Windows authentication for database access.</span></span> <span data-ttu-id="02be0-126">如果确实使用这两种方法，请记下凭据，以便在还原服务应用程序之后，可以使用这些凭据配置服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-126">If it does, make a note of the credentials so you can use them to configure the service application after it is restored.</span></span>  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a><span data-ttu-id="02be0-127">使用管理中心备份加密密钥</span><span class="sxs-lookup"><span data-stu-id="02be0-127">Backup the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="02be0-128">有关备份 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 加密密钥的信息，请参阅[管理 Reporting Services SharePoint 服务应用程序](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)的“加密密钥”部分。</span><span class="sxs-lookup"><span data-stu-id="02be0-128">For information on backing up the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
###  <a name="backup-the-service-application-using-sharepoint-central-administration"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="02be0-129">使用 SharePoint 管理中心备份服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-129">Backup the Service application Using SharePoint Central Administration</span></span>  
 <span data-ttu-id="02be0-130">若要备份服务应用程序，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="02be0-130">To back up the Service Application, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="02be0-131">在 SharePoint 管理中心中，单击 **“备份和还原”** 组中的 **“执行备份”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-131">In SharePoint Central Administration Click **Perform a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="02be0-132">在 **“共享服务”** 节点下，展开 **“共享服务应用程序”** ，然后选择您的服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-132">Under the **Shared Services** node, expand **Shared Service Applications** and select your service application.</span></span> <span data-ttu-id="02be0-133">该应用程序将具有 **“SQL Server Reporting Services 服务应用程序”** 类型。</span><span class="sxs-lookup"><span data-stu-id="02be0-133">It will have a type of **SQL Server Reporting Services Service Application**.</span></span>  
  
3.  <span data-ttu-id="02be0-134">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="02be0-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="02be0-135">\*\*\*\* 键入 **“备份位置:”** 的路径，然后单击“开始备份”</span><span class="sxs-lookup"><span data-stu-id="02be0-135">Type the path for the **Backup location:** and click **Start Backup**</span></span>  
  
5.  <span data-ttu-id="02be0-136">重复上述过程，而不是选择服务应用程序，展开 **“共享服务代理”** 节点，然后选择服务应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="02be0-136">Repeat the process above but instead of selecting the service application, expand the **Shared Services Proxies** node, and select service application proxy.</span></span> <span data-ttu-id="02be0-137">该应用程序将具有 **“SQL Server Reporting Services 服务应用程序代理”** 类型。</span><span class="sxs-lookup"><span data-stu-id="02be0-137">It will have a type of **SQL Server Reporting Services Service Application Proxy**.</span></span>  
  
 <span data-ttu-id="02be0-138">有关详细信息，请参阅 SharePoint 文档中的以下主题：</span><span class="sxs-lookup"><span data-stu-id="02be0-138">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="02be0-139">[SharePoint 文档中的备份服务应用程序 (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748601.aspx)。</span><span class="sxs-lookup"><span data-stu-id="02be0-139">[Back up a service application (SharePoint Foundation 2010) in the SharePoint documenttation](https://msdn.microsoft.com/library/ee748601.aspx).</span></span>  
  
 [<span data-ttu-id="02be0-140">备份服务应用程序 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="02be0-140">Back up a service application (SharePoint Server 2010)</span></span>](https://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a><span data-ttu-id="02be0-141">验证执行帐户和数据库身份验证</span><span class="sxs-lookup"><span data-stu-id="02be0-141">Verify Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="02be0-142">**执行帐户** ：验证您的服务应用程序是否正在使用执行帐户：</span><span class="sxs-lookup"><span data-stu-id="02be0-142">**Execution Account:** To verify if your service application is using an execution account:</span></span>  
  
1.  <span data-ttu-id="02be0-143">在 SharePoint 管理中心的 "**应用程序管理**" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="02be0-143">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="02be0-144">单击您的服务应用程序的名称，然后单击 SharePoint 功能区中的 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-144">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="02be0-145">单击 **“执行帐户”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-145">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="02be0-146">如果配置了执行帐户，则当需要还原服务应用程序备份时，您需要知道凭据。</span><span class="sxs-lookup"><span data-stu-id="02be0-146">If an execution account is configured, you need to know the credentials when it is time to restore the service application backup.</span></span> <span data-ttu-id="02be0-147">在知道正确的凭据之前，请不要继续执行备份和还原过程。</span><span class="sxs-lookup"><span data-stu-id="02be0-147">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
 <span data-ttu-id="02be0-148">**数据库身份验证** ：验证您的服务应用程序是否正在使用 Windows 身份验证来进行数据库身份验证：</span><span class="sxs-lookup"><span data-stu-id="02be0-148">**Database Authentication:** To verify if your service application is using Windows Authentication for the database authentication:</span></span>  
  
1.  <span data-ttu-id="02be0-149">在 SharePoint 管理中心的 "**应用程序管理**" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="02be0-149">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="02be0-150">单击您的服务应用程序的名称，然后单击 SharePoint 功能区中的 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-150">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="02be0-151">查看“Reporting Services (SSRS) 服务数据库”\*\*\*\* 部分。</span><span class="sxs-lookup"><span data-stu-id="02be0-151">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="02be0-152">如果配置了 Windows 身份验证，则您需要知道凭据，以便您可以在还原服务应用程序后对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="02be0-152">If Windows Authentication is configured, you need to know the credentials so you can configure the service application after you restore it.</span></span> <span data-ttu-id="02be0-153">在知道正确的凭据之前，请不要继续执行备份和还原过程。</span><span class="sxs-lookup"><span data-stu-id="02be0-153">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
##  <a name="restore-the-service-application"></a><a name="bkmk_restore"></a><span data-ttu-id="02be0-154">还原服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-154">Restore the Service Application</span></span>  
 <span data-ttu-id="02be0-155">请按顺序完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="02be0-155">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="02be0-156">还原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="02be0-156">Restore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="02be0-157">还原加密密钥</span><span class="sxs-lookup"><span data-stu-id="02be0-157">Restore the encryption keys</span></span>  
  
3.  <span data-ttu-id="02be0-158">如果您的服务应用程序正在使用执行帐户或 Windows 身份验证来访问数据库，请配置凭据。</span><span class="sxs-lookup"><span data-stu-id="02be0-158">If your service application was using an execution account or Windows authentication for database access, configure the credentials.</span></span>  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a><span data-ttu-id="02be0-159">使用 SharePoint 管理中心还原服务应用程序</span><span class="sxs-lookup"><span data-stu-id="02be0-159">Restore the Service application Using SharePoint Central Administration</span></span>  
  
1.  <span data-ttu-id="02be0-160">在 SharePoint 管理中心中，单击 **“备份和还原”** 组中的 **“从备份中还原”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-160">In SharePoint Central Administration Click **Restore from a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="02be0-161">在 **“备份目录位置”** 框中键入指向备份文件的路径，然后单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-161">Type the path to your backup file in **Backup Directory Location** box and click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="02be0-162">从 **“顶部组件”** 列表中选择服务应用程序备份，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-162">Select your service application backup from the **Top Component** list and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="02be0-163">选择您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 应用程序，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-163">Select your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="02be0-164">在 **“登录名和密码”** 部分中，键入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="02be0-164">In the **Login Names and Passwords** section type the password for the login name.</span></span> <span data-ttu-id="02be0-165">登录名框中应填充服务应用程序在备份之前使用的登录名。</span><span class="sxs-lookup"><span data-stu-id="02be0-165">The login name box should be populated with the login the service application was using prior to the backup.</span></span>  
  
6.  <span data-ttu-id="02be0-166">单击 **“开始还原”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-166">Click **Start Restore**.</span></span>  
  
7.  <span data-ttu-id="02be0-167">重复上述过程，而不是还原服务应用程序，展开 **“共享服务”** 节点，然后展开 **“共享服务应用程序”** 节点。</span><span class="sxs-lookup"><span data-stu-id="02be0-167">Repeat the process above but instead of restoring the service application, expand the **Shared Services** node and then expand the **Shared Service Applications** node.</span></span>  
  
 <span data-ttu-id="02be0-168">有关详细信息，请参阅 SharePoint 文档中的以下主题：</span><span class="sxs-lookup"><span data-stu-id="02be0-168">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="02be0-169">[还原服务应用程序 (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="02be0-169">[Restore a service application (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx).</span></span>  
  
 <span data-ttu-id="02be0-170">[还原服务应用程序 (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)。</span><span class="sxs-lookup"><span data-stu-id="02be0-170">[Restore a service application (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx).</span></span>  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a><span data-ttu-id="02be0-171">使用管理中心还原加密密钥</span><span class="sxs-lookup"><span data-stu-id="02be0-171">Restore the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="02be0-172">有关还原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 加密密钥的信息，请参阅[管理 Reporting Services SharePoint 服务应用程序](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)的“加密密钥”部分。</span><span class="sxs-lookup"><span data-stu-id="02be0-172">For information on restoring the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
### <a name="configure-the-execution-account-and-database-authentication"></a><span data-ttu-id="02be0-173">配置执行帐户和数据库身份验证</span><span class="sxs-lookup"><span data-stu-id="02be0-173">Configure the Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="02be0-174">**执行帐户** ：如果您的服务应用程序正在使用执行帐户，请完成一些步骤对它进行配置：</span><span class="sxs-lookup"><span data-stu-id="02be0-174">**Execution Account:** If your service application was using an execution account complete the following steps to configure it:</span></span>  
  
1.  <span data-ttu-id="02be0-175">在 SharePoint 管理中心的 "**应用程序管理**" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="02be0-175">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="02be0-176">单击您的服务应用程序的名称，然后单击 SharePoint 功能区中的 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-176">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="02be0-177">单击 **“执行帐户”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-177">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="02be0-178">键入帐户和密码，然后选中 **“指定执行帐户”** 框。</span><span class="sxs-lookup"><span data-stu-id="02be0-178">Type the account, password, and select the **Specify and Execution Account** box.</span></span>  
  
5.  <span data-ttu-id="02be0-179">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="02be0-179">Click **OK**.</span></span>  
  
 <span data-ttu-id="02be0-180">**数据库身份验证** ：如果您的服务应用程序正在使用 Windows 身份验证来进行数据库身份验证，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="02be0-180">**Database Authentication:** If your service application was using Windows Authentication for the database authentication complete the following steps:</span></span>  
  
1.  <span data-ttu-id="02be0-181">在 SharePoint 管理中心中，单击 "管理**应用程序管理**" 组中的 "**服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="02be0-181">In SharePoint Central Administration click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="02be0-182">单击您的服务应用程序的名称，然后单击 SharePoint 功能区中的 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-182">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="02be0-183">查看“Reporting Services (SSRS) 服务数据库”\*\*\*\* 部分。</span><span class="sxs-lookup"><span data-stu-id="02be0-183">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="02be0-184">选择 **“Windows 身份验证”**。</span><span class="sxs-lookup"><span data-stu-id="02be0-184">Select **Windows Authentication**.</span></span>  
  
5.  <span data-ttu-id="02be0-185">键入帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="02be0-185">Type the account and password.</span></span> <span data-ttu-id="02be0-186">如果适当，请选择 **“用作 Windows 凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="02be0-186">Select **Use as Windows Credentials** if appropriate.</span></span>  
  
6.  <span data-ttu-id="02be0-187">单击“确定”</span><span class="sxs-lookup"><span data-stu-id="02be0-187">Click **Ok**</span></span>  
  
  
