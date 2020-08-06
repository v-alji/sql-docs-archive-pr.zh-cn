---
title: 将 PowerPivot 无人参与的数据刷新帐户配置 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6f53d7272dc48ed55ffb175e0ace3e97263946c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579225"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a><span data-ttu-id="45474-102">配置 PowerPivot 无人参与的数据刷新帐户 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="45474-102">Configure the PowerPivot Unattended Data Refresh Account (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="45474-103">PowerPivot 无人参与的数据刷新帐户是为在 SharePoint 场中运行 PowerPivot 数据刷新作业而指定的帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-103">The PowerPivot unattended data refresh account is a designated account for running PowerPivot data refresh jobs in a SharePoint farm.</span></span> <span data-ttu-id="45474-104">配置后，可以在数据刷新计划页中启用 "**使用管理员配置的数据刷新帐户**" 选项 (参见下面的) 。</span><span class="sxs-lookup"><span data-stu-id="45474-104">By configuring it, you enable the **Use the data refresh account configured by the administrator** option in a data refresh schedule page (see below).</span></span> <span data-ttu-id="45474-105">如果计划数据刷新的工作簿作者希望使用 PowerPivot 无人参与的数据刷新帐户来运行数据刷新作业，则可以选择此选项。</span><span class="sxs-lookup"><span data-stu-id="45474-105">Workbook authors who schedule data refresh can choose this option if they want to use the PowerPivot unattended data refresh account to run a data refresh job.</span></span> <span data-ttu-id="45474-106">有关如何在数据刷新计划中查看凭据选项的详细信息，请参阅[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="45474-106">For more information about how to view the Credentials options in a data refresh schedule, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="45474-107">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span><span class="sxs-lookup"><span data-stu-id="45474-107">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span></span>  
  
 <span data-ttu-id="45474-108">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="45474-108">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="45474-109">根据配置服务器时选择的选项，可能已创建无人参与的数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-109">Depending on which options you selected when configuring the server, the unattended data refresh account might already be created.</span></span> <span data-ttu-id="45474-110">在默认配置中，无人参与的数据刷新帐户的标识最初将设置为场帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-110">In a default configuration, the identity of the unattended data refresh account is initially set to the farm account.</span></span> <span data-ttu-id="45474-111">您可以通过更改帐户以便以其他用户身份运行，从而改进部署的安全性。</span><span class="sxs-lookup"><span data-stu-id="45474-111">You can improve the security of your deployment by changing the account to run as a different user.</span></span> <span data-ttu-id="45474-112">按照以下说明更改帐户：[更新现有的 PowerPivot 无人参与的数据刷新帐户所使用的凭据](#bkmk_editUA)。</span><span class="sxs-lookup"><span data-stu-id="45474-112">Follow these instructions to change the account: [Update the credentials used by an existing PowerPivot unattended data refresh account](#bkmk_editUA).</span></span>  
  
 <span data-ttu-id="45474-113">对于所有其他安装情况，您必须使用下面的说明手动配置此帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-113">For all other installation scenarios, you must configure this account manually using the instructions below.</span></span>  
  
 <span data-ttu-id="45474-114">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="45474-114">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="45474-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="45474-115">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="45474-116">步骤 1：创建目标应用程序并设置凭据</span><span class="sxs-lookup"><span data-stu-id="45474-116">Step 1: Create a target application and set the credentials</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="45474-117">步骤 2：在 PowerPivot 服务器配置页中指定无人参与的帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-117">Step 2: Specify the unattended account in PowerPivot server configuration pages</span></span>](#bkmk_specifyUA)  
  
 [<span data-ttu-id="45474-118">步骤3：向帐户授予 "参与讨论" 权限</span><span class="sxs-lookup"><span data-stu-id="45474-118">Step 3: Grant contribute permissions to the account</span></span>](#bkmk_grant)  
  
 [<span data-ttu-id="45474-119">步骤 4：授予读取权限以便访问在数据刷新中使用的外部数据源</span><span class="sxs-lookup"><span data-stu-id="45474-119">Step 4: Grant read permissions to access external data sources used in data refresh</span></span>](#bkmk_dbread)  
  
 [<span data-ttu-id="45474-120">步骤 5：在数据刷新配置页中验证帐户可用性</span><span class="sxs-lookup"><span data-stu-id="45474-120">Step 5: Verify account availability in data refresh configuration pages</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="45474-121">使用 PowerPivot 无人参与的数据刷新帐户</span><span class="sxs-lookup"><span data-stu-id="45474-121">Using the PowerPivot Unattended Data Refresh Account</span></span>](#bkmk_use)  
  
 [<span data-ttu-id="45474-122">更新现有的 PowerPivot 无人参与数据刷新帐户使用的凭据</span><span class="sxs-lookup"><span data-stu-id="45474-122">Update the credentials used by an existing PowerPivot unattended data refresh account</span></span>](#bkmk_editUA)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="45474-123">先决条件</span><span class="sxs-lookup"><span data-stu-id="45474-123">Prerequisites</span></span>  
 <span data-ttu-id="45474-124">必须启用和配置 Secure Store Service，并且必须生成主密钥。</span><span class="sxs-lookup"><span data-stu-id="45474-124">Secure Store Service must be enabled and configured, and a master key must be generated.</span></span> <span data-ttu-id="45474-125">有关如何执行此操作的说明，请参阅[通过 SharePoint 2010 进行 PowerPivot 数据刷新](powerpivot-data-refresh-with-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="45474-125">For instructions on how to do this, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="45474-126">您必须提前确定哪一 Windows 域用户帐户用作 PowerPivot 无人参与的数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-126">You must decide in advance which Windows domain user account to use as the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="45474-127">该帐户应该是为此目的而专门创建的帐户，以便您可以监视其使用方式。</span><span class="sxs-lookup"><span data-stu-id="45474-127">This should be an account that is created specifically for this purpose so that you can monitor how it is used.</span></span>  
  
 <span data-ttu-id="45474-128">您必须知道 PowerPivot 系统服务的应用程序标识。</span><span class="sxs-lookup"><span data-stu-id="45474-128">You must know the application identity of the PowerPivot System Service.</span></span> <span data-ttu-id="45474-129">在步骤1中为此服务帐户创建目标应用程序时，会向此服务帐户授予 "**完全控制**" 权限。</span><span class="sxs-lookup"><span data-stu-id="45474-129">You will give this service account **Full Control** permissions over the unattended data refresh account when you create the target application for it in step 1.</span></span> <span data-ttu-id="45474-130">这些权限允许 PowerPivot 系统服务在数据刷新过程中检索无人参与的数据刷新帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-130">These permissions allow the PowerPivot System Service to retrieve the credentials of the unattended data refresh account during data refresh.</span></span> <span data-ttu-id="45474-131">若要获取所需的服务帐户信息，请在 "管理中心" 中打开 "**配置服务帐户**" 页，然后选择 PowerPivot 服务应用程序使用的服务应用程序池。</span><span class="sxs-lookup"><span data-stu-id="45474-131">To get the required service account information, open the **Configure service accounts** page in Central Administration and select the service application pool used by the PowerPivot service application.</span></span> <span data-ttu-id="45474-132">默认情况下，这是 "**服务应用程序池-SharePoint Web 服务系统**"。</span><span class="sxs-lookup"><span data-stu-id="45474-132">By default, this is the **Service Application Pool - SharePoint Web Services System**.</span></span>  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a><span data-ttu-id="45474-133">配置无人参与的 PowerPivot 数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-133">Configure the unattended PowerPivot data refresh account</span></span>  
 <span data-ttu-id="45474-134">对于每个 PowerPivot 服务应用程序，您只能配置一个 PowerPivot 无人参与的数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-134">You can configure only one PowerPivot unattended data refresh account for each PowerPivot service application.</span></span> <span data-ttu-id="45474-135">帐户信息存储于目标应用程序中设置为预定义的 Windows 域用户帐户的 Secure Store Service 中。</span><span class="sxs-lookup"><span data-stu-id="45474-135">Account information is stored in Secure Store Service in a target application that is set to a predefined Windows domain user account.</span></span> <span data-ttu-id="45474-136">一旦创建目标应用程序后，您可以在 PowerPivot 服务应用程序的配置页中将其指定为 PowerPivot 数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-136">Once the target application is created, you can specify it as the PowerPivot data refresh account in the configuration pages of a PowerPivot service application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45474-137">在基于无人参与的数据刷新帐户执行数据刷新时，对于用于无人参与的数据刷新的 Windows 用户帐户记录，将记录其使用情况报告和数据刷新历史记录。</span><span class="sxs-lookup"><span data-stu-id="45474-137">When data refresh is performed under the unattended data refresh account, usage reporting and data refresh history is recorded against the Windows user account used for unattended data refresh.</span></span> <span data-ttu-id="45474-138">如果您要求对请求数据刷新或拥有计划的个体的更精确记录，则考虑用于运行数据刷新的其他选项之一。</span><span class="sxs-lookup"><span data-stu-id="45474-138">If you require a more accurate record of the individuals who are requesting data refresh or who own schedules, consider one of the other options for running data refresh.</span></span> <span data-ttu-id="45474-139">也就是说，让用户指定自己的凭据（这是默认设置）或者创建其他目标应用程序以便存储要用于数据刷新的任何 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-139">Namely, having users specify their own credentials (this is the default), or creating additional target applications for storing any Windows credentials that you want to use for data refresh purposes.</span></span> <span data-ttu-id="45474-140">有关详细信息，请参阅为[PowerPivot 数据刷新配置存储的凭据 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="45474-140">For more information, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
 <span data-ttu-id="45474-141">创建无人参与的数据刷新帐户包括五个部分。</span><span class="sxs-lookup"><span data-stu-id="45474-141">There are five parts to creating the unattended data refresh account.</span></span>  
  
-   <span data-ttu-id="45474-142">在 Secure Store Service 中创建目标应用程序并指定凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-142">Create a target application in Secure Store Service for the account and specify the credentials.</span></span>  
  
-   <span data-ttu-id="45474-143">在 PowerPivot 服务器配置页中为无人参与的数据刷新帐户指定目标应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="45474-143">Specify the target application ID for the unattended data refresh account in the PowerPivot server configuration page.</span></span>  
  
-   <span data-ttu-id="45474-144">对该帐户授予“参与讨论”权限。</span><span class="sxs-lookup"><span data-stu-id="45474-144">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="45474-145">授予该帐户读取权限以便在数据刷新过程中访问外部数据源。</span><span class="sxs-lookup"><span data-stu-id="45474-145">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="45474-146">验证该帐户在已发布的 PowerPivot 工作簿的“管理数据刷新计划”页中可用。</span><span class="sxs-lookup"><span data-stu-id="45474-146">Verify the account is available in the Manage Data Refresh schedule page for a published PowerPivot workbook.</span></span>  
  
###  <a name="step-1-create-a-target-application-and-set-the-credentials"></a><a name="bkmk_create"></a><span data-ttu-id="45474-147">步骤1：创建目标应用程序并设置凭据</span><span class="sxs-lookup"><span data-stu-id="45474-147">Step 1: Create a target application and set the credentials</span></span>  
  
1.  <span data-ttu-id="45474-148">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="45474-148">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="45474-149">单击 " **Secure Store Service**"。</span><span class="sxs-lookup"><span data-stu-id="45474-149">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="45474-150">在 "管理目标应用程序" 中，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="45474-150">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="45474-151">在 "目标应用程序 ID" 中，键入**PowerPivotDataRefresh**。</span><span class="sxs-lookup"><span data-stu-id="45474-151">In Target application ID, type **PowerPivotDataRefresh**.</span></span>  
  
5.  <span data-ttu-id="45474-152">在 "显示名称" 中，键入 " **PowerPivot 数据刷新**"。</span><span class="sxs-lookup"><span data-stu-id="45474-152">In Display Name, type **PowerPivot Data Refresh**.</span></span>  
  
6.  <span data-ttu-id="45474-153">在“联系人电子邮件”中，键入您的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="45474-153">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="45474-154">在 "目标应用程序类型" 中，选择 "**个人**"。</span><span class="sxs-lookup"><span data-stu-id="45474-154">In Target Application Type, select **Individual**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45474-155">指定“单独”帐户类型适合于此情况，因为只有 PowerPivot 服务应用程序将请求 PowerPivot 无人参与的数据刷新帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-155">Specifying an Individual account type is correct for this scenario because only the PowerPivot service application will request the credentials of the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="45474-156">实际上，该服务应用程序是无人参与的数据刷新帐户的唯一用户，这使得“单独”帐户类型成为此目标应用程序的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="45474-156">In practice, the service application is the sole user of the unattended data refresh account, making the Individual account type the best choice for this target application.</span></span>  
  
8.  <span data-ttu-id="45474-157">跳过“目标应用程序页 URL”。</span><span class="sxs-lookup"><span data-stu-id="45474-157">Skip Target Application Page URL.</span></span> <span data-ttu-id="45474-158">PowerPivot 数据刷新不会使用它。</span><span class="sxs-lookup"><span data-stu-id="45474-158">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="45474-159">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="45474-159">Click **Next**.</span></span>  
  
10. <span data-ttu-id="45474-160">在 "**为安全存储目标应用程序指定凭据字段**" 页上，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="45474-160">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="45474-161">字段名称和类型应该是 Windows 用户名和 Windows 密码</span><span class="sxs-lookup"><span data-stu-id="45474-161">Field names and types should be Windows User Name and Windows Password</span></span>  
  
11. <span data-ttu-id="45474-162">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="45474-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="45474-163">在“目标应用程序管理员”中，指定 PowerPivot 服务应用程序的应用程序池标识。</span><span class="sxs-lookup"><span data-stu-id="45474-163">In Target Application Administrators, specify the application pool identity of the PowerPivot service application.</span></span> <span data-ttu-id="45474-164">服务需要**完全控制**权限，以便它可以在运行时检索无人参与的数据刷新帐户信息。</span><span class="sxs-lookup"><span data-stu-id="45474-164">The service requires **Full Control** permissions so that it can retrieve unattended data refresh account information at run time.</span></span> <span data-ttu-id="45474-165">此外，指定应该对应用程序设置具有管理权限的任何其他 SharePoint 用户的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-165">In addition, specify the Windows domain user accounts of any other SharePoint user who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="45474-166">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="45474-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="45474-167">选择刚创建的目标应用程序，单击向下箭头并选择 "**设置凭据"。**</span><span class="sxs-lookup"><span data-stu-id="45474-167">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
15. <span data-ttu-id="45474-168">在 "**凭据所有者**" 中，键入你想要拥有更新凭据的权限的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-168">In **Credential Owners**, type a Windows domain user account that you want to have permissions to update the credentials.</span></span> <span data-ttu-id="45474-169">凭据用于数据全新操作，**凭据所有者**有权修改凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-169">The credentials are used for data fresh actions and the **Credential Owners** have permissions to modify the credentials.</span></span>  
  
16. <span data-ttu-id="45474-170">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="45474-170">Click **OK**.</span></span>  
  
###  <a name="step-2-specify-the-unattended-account-in-powerpivot-server-configuration-pages"></a><a name="bkmk_specifyUA"></a><span data-ttu-id="45474-171">步骤2：在 PowerPivot 服务器配置页中指定无人参与帐户</span><span class="sxs-lookup"><span data-stu-id="45474-171">Step 2: Specify the unattended account in PowerPivot server configuration pages</span></span>  
  
1.  <span data-ttu-id="45474-172">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="45474-172">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="45474-173">找到 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="45474-173">Find the PowerPivot Service application.</span></span> <span data-ttu-id="45474-174">您可以通过类型来确定服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="45474-174">You can identify a service application by its type.</span></span> <span data-ttu-id="45474-175">PowerPivot 服务应用程序的类型为 **“PowerPivot 服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="45474-175">A PowerPivot service application type is **PowerPivot Service Application**.</span></span>  
  
3.  <span data-ttu-id="45474-176">单击 PowerPivot 服务应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="45474-176">Click the PowerPivot service application name.</span></span> <span data-ttu-id="45474-177">等待 PowerPivot 管理面板出现。</span><span class="sxs-lookup"><span data-stu-id="45474-177">Wait for the PowerPivot Management Dashboard to appear.</span></span>  
  
4.  <span data-ttu-id="45474-178">在 "操作" 的右上角，单击 "**配置服务应用程序设置**"。</span><span class="sxs-lookup"><span data-stu-id="45474-178">In Actions, in the top right corner, click **Configure service application settings**.</span></span>  
  
5.  <span data-ttu-id="45474-179">在 "数据刷新" 的 "PowerPivot 无人参与的数据刷新帐户" 中，键入在上一步中创建的目标应用程序 ID： **PowerPivotDataRefresh**。</span><span class="sxs-lookup"><span data-stu-id="45474-179">In Data Refresh, in PowerPivot Unattended Data Refresh Account, type the target application ID you created in a previous step: **PowerPivotDataRefresh**.</span></span>  
  
6.  <span data-ttu-id="45474-180">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="45474-180">Click **OK**.</span></span>  
  
###  <a name="step-3-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="45474-181">步骤3：向帐户授予 "参与讨论" 权限</span><span class="sxs-lookup"><span data-stu-id="45474-181">Step 3: Grant contribute permissions to the account</span></span>  
 <span data-ttu-id="45474-182">在您可以使用 PowerPivot 无人参与的数据刷新帐户之前，对于使用该帐户的任何 PowerPivot 工作簿，必须授予“参与讨论”权限。</span><span class="sxs-lookup"><span data-stu-id="45474-182">Before you can use the PowerPivot unattended data refresh account, it must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="45474-183">此权限级别是从库中打开工作簿、然后在刷新数据后将其保存回库中所必需的。</span><span class="sxs-lookup"><span data-stu-id="45474-183">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="45474-184">分配权限这个步骤将由网站集管理员来执行。</span><span class="sxs-lookup"><span data-stu-id="45474-184">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="45474-185">SharePoint 权限可以在根网站集或其下的任何级别分配，包括单独的文档和项。</span><span class="sxs-lookup"><span data-stu-id="45474-185">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="45474-186">设置权限的方式将因您所需的粒度而异。</span><span class="sxs-lookup"><span data-stu-id="45474-186">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="45474-187">下面的步骤说明可用于授予权限的一个方法。</span><span class="sxs-lookup"><span data-stu-id="45474-187">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="45474-188">在 SharePoint 站点上的 "站点操作" 中，单击 "**网站权限**"。</span><span class="sxs-lookup"><span data-stu-id="45474-188">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="45474-189">单击“授予权限”  。</span><span class="sxs-lookup"><span data-stu-id="45474-189">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="45474-190">在“选择用户”中，键入您指派为 PowerPivot 无人参与的帐户的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-190">In Select users, type the name of the Windows domain user account that you designated as the PowerPivot unattended account.</span></span> <span data-ttu-id="45474-191">这是在 Secure Store Service 的目标应用程序中指定的 Windows 域用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="45474-191">This is the name of the Windows domain user account that you specified in target application in Secure Store Service.</span></span>  
  
4.  <span data-ttu-id="45474-192">在 "授予权限" 中，选择 "**直接授予用户权限**"。</span><span class="sxs-lookup"><span data-stu-id="45474-192">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="45474-193">选择 "**参与**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="45474-193">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-4-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="45474-194">步骤4：授予读取权限以便访问在数据刷新中使用的外部数据源</span><span class="sxs-lookup"><span data-stu-id="45474-194">Step 4: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="45474-195">在将数据导入到某一 PowerPivot 工作簿时，与外部数据的连接常常基于可信连接或者使用当前用户标识来连接到数据源的模拟连接。</span><span class="sxs-lookup"><span data-stu-id="45474-195">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="45474-196">只有在当前用户有权读取其导入的数据时，这些连接类型才有效。</span><span class="sxs-lookup"><span data-stu-id="45474-196">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="45474-197">在数据刷新方案中，现在将重复使用过去用于导入数据的相同连接字符串来刷新数据。</span><span class="sxs-lookup"><span data-stu-id="45474-197">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="45474-198">如果该连接字符串假定当前用户（例如，包含 Integrated_Security=SSPI 的字符串），则 PowerPivot 系统服务会将 PowerPivot 无人参与的数据刷新帐户的用户标识作为当前用户传递。</span><span class="sxs-lookup"><span data-stu-id="45474-198">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity of the PowerPivot unattended data refresh account as the current user.</span></span> <span data-ttu-id="45474-199">只有在 PowerPivot 无人参与的数据刷新帐户对外部数据源具有读取权限时，此连接才会成功。</span><span class="sxs-lookup"><span data-stu-id="45474-199">This connection will only succeed if the PowerPivot unattended data refresh account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="45474-200">因此，您必须向 PowerPivot 无人参与的数据刷新帐户授予相应的只读权限，使此帐户能够以只读方式访问在该无人参与的帐户下运行的任何数据刷新操作中使用的所有外部数据源。</span><span class="sxs-lookup"><span data-stu-id="45474-200">For this reason, you must grant the PowerPivot unattended data refresh account read-only permissions on all of the external data sources that are used in any data refresh operation that runs under the unattended account.</span></span>  
  
 <span data-ttu-id="45474-201">如果您是组织中使用的数据源的管理员，则可以创建一个登录名，然后分配必需的权限。</span><span class="sxs-lookup"><span data-stu-id="45474-201">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="45474-202">否则，您必须与数据所有者联系并且提供帐户信息。</span><span class="sxs-lookup"><span data-stu-id="45474-202">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="45474-203">请确保指定映射到 PowerPivot 无人参与的数据刷新帐户的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-203">Be sure to specify the Windows domain user account that maps to the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="45474-204">这是你在本主题的 " (步骤 1) ：创建目标应用程序并设置凭据" 中指定的帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-204">This is the account you specified in "(Step 1): Create a target application and set the credentials" in this topic.</span></span>  
  
###  <a name="step-5-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="45474-205">步骤5：在数据刷新配置页中验证帐户可用性</span><span class="sxs-lookup"><span data-stu-id="45474-205">Step 5: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="45474-206">打开包含 PowerPivot 数据的已发布工作簿的数据刷新配置页。</span><span class="sxs-lookup"><span data-stu-id="45474-206">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="45474-207">有关如何打开该页的说明，请参阅[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="45474-207">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="45474-208">验证是否在数据刷新配置页中启用了 "**使用管理员配置的数据刷新帐户**" 选项。</span><span class="sxs-lookup"><span data-stu-id="45474-208">Verify that the **Use the data refresh account configured by the administrator** option is enabled in the data refresh configuration page.</span></span>  
  
3.  <span data-ttu-id="45474-209">选中 "**也尽快刷新**" 复选框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="45474-209">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="45474-210">在包含该工作簿的库中，选择该工作簿，单击右侧显示的向下箭头，然后选择 "**管理 PowerPivot 数据刷新**"。</span><span class="sxs-lookup"><span data-stu-id="45474-210">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="45474-211">如果数据刷新作业正在返回大量数据，您可能需要等待几分钟。</span><span class="sxs-lookup"><span data-stu-id="45474-211">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="45474-212">如果发生错误，你可以在数据刷新历史记录页中单击 "**配置计划**"，尝试使用不同的凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-212">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="45474-213">您还可能需要检查原始工作簿中的数据源连接信息，以便查看在数据刷新过程中使用的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="45474-213">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="45474-214">该连接字符串将提供与您可用于解决问题的服务器位置和数据库有关的信息。</span><span class="sxs-lookup"><span data-stu-id="45474-214">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="45474-215">有关故障排除的详细信息，请参阅 TechNet Wiki 上的[PowerPivot 数据刷新故障排除](https://go.microsoft.com/fwlink/p/?LinkID=223279)。</span><span class="sxs-lookup"><span data-stu-id="45474-215">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="using-the-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_use"></a><span data-ttu-id="45474-216">使用 PowerPivot 无人参与的数据刷新帐户</span><span class="sxs-lookup"><span data-stu-id="45474-216">Using the PowerPivot Unattended Data Refresh Account</span></span>  
 <span data-ttu-id="45474-217">在 PowerPivot 数据刷新计划页上的三个凭据选项中，只有第一个选项与无人参与的数据刷新帐户相关。</span><span class="sxs-lookup"><span data-stu-id="45474-217">Of the three credential options in PowerPivot data refresh scheduling page, only the first one corresponds to the unattended data refresh account.</span></span> <span data-ttu-id="45474-218">在设置数据刷新计划时，请务必选择此选项。</span><span class="sxs-lookup"><span data-stu-id="45474-218">Be sure to select this option when setting up the data refresh schedule.</span></span>  
  
 <span data-ttu-id="45474-219">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span><span class="sxs-lookup"><span data-stu-id="45474-219">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span></span>  
  
 <span data-ttu-id="45474-220">不要使用第三个凭据选项（要求您输入目标应用程序 ID 的选项）来访问 PowerPivot 无人参与的数据刷新帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-220">Do not use the third credential option (the one that requires you to enter the target application ID) to access the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="45474-221">因为使用该选项会执行一个附加的模拟检查，如果您尝试将其与 PowerPivot 无人参与的数据刷新帐户（或者基于“单独”帐户类型的任何目标应用程序）一起使用，将会导致验证错误。</span><span class="sxs-lookup"><span data-stu-id="45474-221">There is an additional impersonation check that is performed with that option that will result in a validation error if you try to use it with the PowerPivot unattended data refresh account (or any target application that is based on the Individual account type).</span></span> <span data-ttu-id="45474-222">有关如何使用第三个选项的详细信息，请参阅为[PowerPivot 数据刷新配置存储的凭据 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="45474-222">For more information about how to use the third option, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
##  <a name="update-the-credentials-used-by-an-existing-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_editUA"></a><span data-ttu-id="45474-223">更新现有的 PowerPivot 无人参与的数据刷新帐户使用的凭据</span><span class="sxs-lookup"><span data-stu-id="45474-223">Update the credentials used by an existing PowerPivot unattended data refresh account</span></span>  
 <span data-ttu-id="45474-224">如果无人参与的数据刷新帐户已通过安装程序配置或者已由管理员配置，则您可以通过编辑存储凭据的目标应用程序，更新用户名或密码。</span><span class="sxs-lookup"><span data-stu-id="45474-224">If the unattended data refresh account is already configured through setup or by an administrator, you can update the user name or password by editing the target application that stores the credentials.</span></span> <span data-ttu-id="45474-225">请注意，当您在 Secure Store Service 中编辑凭据时，以前与 PowerPivot 无人参与的数据刷新帐户相关联的原始 Windows 标识将不可见。</span><span class="sxs-lookup"><span data-stu-id="45474-225">Note that the original Windows identity that was previously associated with PowerPivot unattended data refresh account will not be visible when you edit the credentials in Secure Store Service.</span></span> <span data-ttu-id="45474-226">无论您是更新到期的密码还是指定不同帐户，都必须始终在 Secure Store Service 中为该目标应用程序重新键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="45474-226">Whether you are updating an expired password or specifying different account, you must always re-type both the user name and password for that target application in Secure Store Service.</span></span>  
  
1.  <span data-ttu-id="45474-227">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="45474-227">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="45474-228">单击 " **Secure Store Service**"。</span><span class="sxs-lookup"><span data-stu-id="45474-228">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="45474-229">选中 " **PowerPivotDataRefresh**" 旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="45474-229">Select the checkbox next to **PowerPivotDataRefresh**.</span></span>  
  
4.  <span data-ttu-id="45474-230">在 "凭据" 中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="45474-230">In Credentials, click **Set**.</span></span>  
  
5.  <span data-ttu-id="45474-231">在 "**凭据所有者**" 中，键入你想要拥有更新凭据的权限的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-231">In **Credential Owners**, type a Windows domain user account that you want to have permissions to update the credentials.</span></span> <span data-ttu-id="45474-232">凭据用于数据全新操作，**凭据所有者**有权修改凭据。</span><span class="sxs-lookup"><span data-stu-id="45474-232">The credentials are used for data fresh actions and the **Credential Owners** have permissions to modify the credentials.</span></span>  
  
6.  <span data-ttu-id="45474-233">在“用户名”中，键入将成为无人参与的数据刷新凭据的一部分的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="45474-233">In User Name, type the Windows domain user account that will be part of the unattended data refresh credentials.</span></span>  
  
7.  <span data-ttu-id="45474-234">在“密码”中，键入该帐户的密码，然后重新键入以确认该密码。</span><span class="sxs-lookup"><span data-stu-id="45474-234">In Password, type the password for the account, and then re-type it to confirm the password.</span></span>  
  
8.  <span data-ttu-id="45474-235">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="45474-235">Click **OK**.</span></span>  
  
 <span data-ttu-id="45474-236">如果您不仅要更改密码，也要更改帐户用户名，则很可能需要执行附加的配置步骤，例如向外部数据源授予读取权限和 SharePoint 权限以便更新 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="45474-236">If you are changing not just the password, but the account user name as well, you will most likely need to perform additional configuration steps, such as granting read permissions to external data sources and SharePoint permissions to update the PowerPivot workbook.</span></span> <span data-ttu-id="45474-237">有关说明，请转到 PowerPivot 无人参与的数据刷新帐户配置中的此步骤：[步骤3：向帐户授予 "参与讨论" 权限](#bkmk_grant)，然后继续执行剩余的所有步骤，最后检查帐户是否已正确配置。</span><span class="sxs-lookup"><span data-stu-id="45474-237">For instructions, go to this step in PowerPivot unattended data refresh account configuration: [Step 3: Grant contribute permissions to the account](#bkmk_grant), and then continue with all remaining steps, concluding with verification that the account is configured correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45474-238">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45474-238">See Also</span></span>  
 <span data-ttu-id="45474-239">[通过 SharePoint 2010 进行 PowerPivot 数据刷新](powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="45474-239">[PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 <span data-ttu-id="45474-240">[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="45474-240">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="45474-241">PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="45474-241">PowerPivot Data Refresh</span></span>](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
