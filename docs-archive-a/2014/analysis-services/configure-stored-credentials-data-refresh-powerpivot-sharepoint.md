---
title: 为 PowerPivot 数据刷新配置存储的凭据 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a1350c5d776891397401e9d3127b7849281b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579231"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="88f19-102">为 PowerPivot 数据刷新配置存储的凭据 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="88f19-102">Configure Stored Credentials for PowerPivot Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="88f19-103">只要您在 Secure Store Service 中创建一个目标应用程序来存储要使用的凭据，PowerPivot 数据刷新作业就可以在任何 Windows 用户帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="88f19-103">PowerPivot data refresh jobs can run under any Windows user account as long as you create a target application in Secure Store Service to store the credentials you want to use.</span></span> <span data-ttu-id="88f19-104">同样，如果您想要提供的数据库登录名不同于最初用于导入 PowerPivot for Excel 中的数据的数据库登录名，则可以将这些凭据映射到 Secure Store Service 目标应用程序，然后在数据刷新计划中指定该目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="88f19-104">Similarly, if you want to provide a database login that varies from the one used to originally import the data in PowerPivot for Excel, you can map those credentials to a Secure Store Service target application, and then specify that target application in a data refresh schedule.</span></span>  
  
 <span data-ttu-id="88f19-105">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="88f19-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="88f19-106">在您按照本主题中的说明执行后，将能够使用 PowerPivot 数据刷新计划页中的以下凭据选项：</span><span class="sxs-lookup"><span data-stu-id="88f19-106">After you follow the instructions in this topic, you will be able to use the following credentials option in the PowerPivot data refresh schedule page:</span></span>  
  
 <span data-ttu-id="88f19-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span><span class="sxs-lookup"><span data-stu-id="88f19-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span></span>  
  
 <span data-ttu-id="88f19-108">本主题介绍如何设置用于在 SharePoint 2010 场中进行 PowerPivot 数据刷新的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="88f19-108">This topic explains how to set up the user names and passwords that are used for PowerPivot data refresh in a SharePoint 2010 farm.</span></span> <span data-ttu-id="88f19-109">您必须首先已启用 Secure Store Service 并生成了主密钥，之后才能采用这些步骤。</span><span class="sxs-lookup"><span data-stu-id="88f19-109">Before you can use these steps, you must have enabled Secure Store Service and generated a master key.</span></span> <span data-ttu-id="88f19-110">有关详细信息，请参阅[通过 SharePoint 2010 进行 PowerPivot 数据刷新](powerpivot-data-refresh-with-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="88f19-110">For more information, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="88f19-111">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="88f19-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="88f19-112">配置用于数据刷新的任何 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="88f19-112">Configure any Windows account for data refresh</span></span>](#configAny)  
  
 [<span data-ttu-id="88f19-113">配置用于访问外部或第三方数据源的预定义帐户</span><span class="sxs-lookup"><span data-stu-id="88f19-113">Configure a predefined account for accessing external or third-party data sources</span></span>](#config3rd)  
  
 <span data-ttu-id="88f19-114">如果在配置或使用数据刷新时遇到问题，请参考 TechNet wiki 上的[PowerPivot 数据刷新故障排除](https://go.microsoft.com/fwlink/?LinkID=223279)页，了解可能的解决方法。</span><span class="sxs-lookup"><span data-stu-id="88f19-114">If you have problems configuring or using data refresh, refer to the [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkID=223279) page on the TechNet wiki for possible solutions.</span></span>  
  
##  <a name="configure-any-windows-account-for-data-refresh"></a><a name="configAny"></a><span data-ttu-id="88f19-115">配置用于数据刷新的任何 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="88f19-115">Configure any Windows account for data refresh</span></span>  
 <span data-ttu-id="88f19-116">在某一 SharePoint 用户定义数据刷新计划时，该用户必须指定执行数据刷新所基于的用户标识。</span><span class="sxs-lookup"><span data-stu-id="88f19-116">When a SharePoint user defines a data refresh schedule, he or she must specify the user identity under which data refresh is performed.</span></span> <span data-ttu-id="88f19-117">有关的选项包括选择 PowerPivot 无人参与的数据刷新帐户，输入其 Windows 域用户帐户，以及输入对数据刷新目的有效的某个其他 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-117">Options include selecting the PowerPivot unattended data refresh account, entering his or her Windows domain user account, or entering some other Windows user account that is valid for data refresh purposes.</span></span> <span data-ttu-id="88f19-118">本节中的步骤针对最后一个选项：指定某个其他 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-118">The steps in this section are for the last option: specifying some other Windows account.</span></span>  
  
 <span data-ttu-id="88f19-119">如果您想要采用其他方法，来代替使用 PowerPivot 无人参与的数据刷新帐户（可用于 SharePoint 上的所有 PowerPivot 用户）或者工作簿所有者的凭据，则可以选择此方法。</span><span class="sxs-lookup"><span data-stu-id="88f19-119">You might choose this approach if you want an alternative to using the PowerPivot unattended data refresh account (available to all PowerPivot users on SharePoint) or the credentials of the workbook owner.</span></span> <span data-ttu-id="88f19-120">例如，您可能要建立可用于不同工作组的一系列数据刷新帐户，以便帮助您在组织级别跟踪和管理数据刷新活动。</span><span class="sxs-lookup"><span data-stu-id="88f19-120">For example, you might want to make a series of data refresh accounts available to different workgroups to help you track and manage data refresh activity at the organizational level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="88f19-121">使用此目标应用程序（及其存储的凭据）的人员和应用程序必须列为此应用程序的成员。</span><span class="sxs-lookup"><span data-stu-id="88f19-121">People and applications that use this target application (and the credentials that it stores) must be listed as members of the application.</span></span> <span data-ttu-id="88f19-122">您必须添加将使用此目标应用程序的每个 PowerPivot 服务应用程序的标识、您的 Windows 帐户，以及将在其数据刷新计划中指定此目标应用程序的人员的组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-122">You must add the identity of each PowerPivot service application that will use the target application, your Windows account, and the group or user accounts of people who will be specifying this target application in their data refresh schedules.</span></span> <span data-ttu-id="88f19-123">您可以在创建目标应用程序时指定所有这些帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-123">You can specify all of these accounts when you create the target application.</span></span> <span data-ttu-id="88f19-124">如果您不知道将需要访问此应用程序的所有用户和组帐户，可以在创建目标应用程序以后再添加它们。</span><span class="sxs-lookup"><span data-stu-id="88f19-124">If you do not know all of the user and group accounts that will require access to this application, you can add them later after the target application is created.</span></span>  
  
 <span data-ttu-id="88f19-125">为数据刷新配置存储的凭据这一过程分为 4 个部分：</span><span class="sxs-lookup"><span data-stu-id="88f19-125">There are 4 parts to configuring stored credentials for data refresh:</span></span>  
  
-   <span data-ttu-id="88f19-126">创建存储凭据的目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="88f19-126">Create the target application that stores the credentials.</span></span>  
  
-   <span data-ttu-id="88f19-127">对该帐户授予“参与讨论”权限。</span><span class="sxs-lookup"><span data-stu-id="88f19-127">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="88f19-128">授予该帐户读取权限以便在数据刷新过程中访问外部数据源。</span><span class="sxs-lookup"><span data-stu-id="88f19-128">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="88f19-129">确认当您在数据刷新计划中指定此目标应用程序时数据刷新将生效。</span><span class="sxs-lookup"><span data-stu-id="88f19-129">Verify that data refresh works when you specify this target application in a data refresh schedule.</span></span>  
  
### <a name="step-1-create-a-target-application"></a><span data-ttu-id="88f19-130">步骤 1：创建目标应用程序</span><span class="sxs-lookup"><span data-stu-id="88f19-130">Step 1: Create a target application</span></span>  
  
1.  <span data-ttu-id="88f19-131">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="88f19-131">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="88f19-132">单击 " **Secure Store Service**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-132">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="88f19-133">在 "管理目标应用程序" 中，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-133">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="88f19-134">在“目标应用程序 ID”中，键入文本字符串。</span><span class="sxs-lookup"><span data-stu-id="88f19-134">In Target application ID, type a text string.</span></span> <span data-ttu-id="88f19-135">此字符串必须唯一，但是还应该容易记住。</span><span class="sxs-lookup"><span data-stu-id="88f19-135">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="88f19-136">每当用户希望使用存储在此应用程序中的凭据时，将在数据刷新计划页中键入此字符串。</span><span class="sxs-lookup"><span data-stu-id="88f19-136">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="88f19-137">在“显示名称”中，输入一个说明性名称。</span><span class="sxs-lookup"><span data-stu-id="88f19-137">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="88f19-138">此名称仅用于显示目的。</span><span class="sxs-lookup"><span data-stu-id="88f19-138">This name is used for display purposes only.</span></span> <span data-ttu-id="88f19-139">不会在数据刷新计划中将其用于指定目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="88f19-139">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="88f19-140">在“联系人电子邮件”中，键入您的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="88f19-140">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="88f19-141">在 "目标应用程序类型" 中选择 "**组**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-141">In Target Application Type, select **Group**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88f19-142">选择“组”帐户类型是必需的，因为这将允许您指定请求对凭据进行访问的所有用户和服务帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-142">Choosing a Group account type is necessary because it allows you to specify all of the user and service accounts requesting access to the credentials.</span></span> <span data-ttu-id="88f19-143">对于每个请求，PowerPivot 系统服务都会确认请求者是否为目标应用程序的成员。</span><span class="sxs-lookup"><span data-stu-id="88f19-143">For each request, PowerPivot System Service verifies whether the requestor is a member of the target application.</span></span>  
  
8.  <span data-ttu-id="88f19-144">跳过“目标应用程序页 URL”。</span><span class="sxs-lookup"><span data-stu-id="88f19-144">Skip Target Application Page URL.</span></span> <span data-ttu-id="88f19-145">PowerPivot 数据刷新不会使用它。</span><span class="sxs-lookup"><span data-stu-id="88f19-145">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="88f19-146">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="88f19-146">Click **Next**.</span></span>  
  
10. <span data-ttu-id="88f19-147">在 "**为安全存储目标应用程序指定凭据字段**" 页上，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="88f19-147">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="88f19-148">字段名称和类型应该是 Windows 用户名和 Windows 密码。</span><span class="sxs-lookup"><span data-stu-id="88f19-148">Field names and types should be Windows User Name and Windows Password.</span></span>  
  
11. <span data-ttu-id="88f19-149">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="88f19-149">Click Next.</span></span>  
  
12. <span data-ttu-id="88f19-150">在“目标应用程序管理员”中，指定应该对目标应用程序设置具有管理权限（例如，能够从成员列表添加或删除帐户）的 SharePoint 用户的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-150">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to target application settings (for example, the ability to add or remove accounts from the Members list).</span></span>  
  
13. <span data-ttu-id="88f19-151">在“成员”中，添加以下用户和组帐户：</span><span class="sxs-lookup"><span data-stu-id="88f19-151">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="88f19-152">作为创建该应用程序的人员，将您的 Windows 用户帐户添加到“成员”列表中。</span><span class="sxs-lookup"><span data-stu-id="88f19-152">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="88f19-153">添加 PowerPivot 服务应用程序的应用程序池标识，以便它可以在数据刷新计划运行时检索凭据。</span><span class="sxs-lookup"><span data-stu-id="88f19-153">Add the application pool identity of the PowerPivot service application so that it can retrieve the credentials when data refresh is scheduled to run.</span></span> <span data-ttu-id="88f19-154">若要查看应用程序池标识，请在 "**管理服务应用**程序" 中，通过单击名称旁边的空白区域选择 PowerPivot 服务应用程序 (这将选择行) ，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-154">To view the application pool identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="88f19-155">此页上显示的安全帐户是要作为目标应用程序的成员来添加的帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-155">The security account that appears on this page is the account to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="88f19-156">在数据刷新计划中添加将输入此目标应用程序的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-156">Add Windows user and group accounts that will be entering this target application in data refresh schedules.</span></span>  
  
14. <span data-ttu-id="88f19-157">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="88f19-157">Click **OK**.</span></span>  
  
15. <span data-ttu-id="88f19-158">选择刚创建的目标应用程序，单击向下箭头并选择 "**设置凭据"。**</span><span class="sxs-lookup"><span data-stu-id="88f19-158">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="88f19-159">在“凭据所有者”中，请注意凭据所有者的列表是只读的。</span><span class="sxs-lookup"><span data-stu-id="88f19-159">In Credential Owner, notice that the list of credential owners is read-only.</span></span> <span data-ttu-id="88f19-160">对凭据具有所有权的帐户是目标应用程序的成员。</span><span class="sxs-lookup"><span data-stu-id="88f19-160">The accounts who have ownership over the credentials are the members of the target application.</span></span> <span data-ttu-id="88f19-161">若要添加或删除凭据所有者，则必须在目标应用程序成员列表中添加或删除帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-161">To add or remove a credential owner, you must add or remove accounts from the target application members list.</span></span>  
  
     <span data-ttu-id="88f19-162">在“Windows 用户名”和“Windows 密码”中，键入将用于运行数据刷新的 Windows 用户帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="88f19-162">In Windows User Name and Windows Password, type credentials of Windows user account that will be used to run data refresh.</span></span>  
  
17. <span data-ttu-id="88f19-163">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="88f19-163">Click **OK**.</span></span>  
  
###  <a name="step-2-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="88f19-164">步骤2：向帐户授予 "参与讨论" 权限</span><span class="sxs-lookup"><span data-stu-id="88f19-164">Step 2: Grant Contribute permissions to the account</span></span>  
 <span data-ttu-id="88f19-165">在您可以使用存储的凭据之前，对于使用该帐户的任何 PowerPivot 工作簿，必须授予“参与讨论”权限。</span><span class="sxs-lookup"><span data-stu-id="88f19-165">Before you can use the stored credentials, the account must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="88f19-166">此权限级别是从库中打开工作簿、然后在刷新数据后将其保存回库中所必需的。</span><span class="sxs-lookup"><span data-stu-id="88f19-166">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="88f19-167">分配权限这个步骤将由网站集管理员来执行。</span><span class="sxs-lookup"><span data-stu-id="88f19-167">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="88f19-168">SharePoint 权限可以在根网站集或其下的任何级别分配，包括单独的文档和项。</span><span class="sxs-lookup"><span data-stu-id="88f19-168">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="88f19-169">设置权限的方式将因您所需的粒度而异。</span><span class="sxs-lookup"><span data-stu-id="88f19-169">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="88f19-170">下面的步骤说明可用于授予权限的一个方法。</span><span class="sxs-lookup"><span data-stu-id="88f19-170">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="88f19-171">在 SharePoint 站点上的 "站点操作" 中，单击 "**网站权限**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-171">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="88f19-172">单击“授予权限”  。</span><span class="sxs-lookup"><span data-stu-id="88f19-172">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="88f19-173">在“选择用户”中，键入您在目标应用程序中指定的 Windows 域用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="88f19-173">In Select users, type the name of the Windows domain user account that you specified in the target application.</span></span>  
  
4.  <span data-ttu-id="88f19-174">在 "授予权限" 中，选择 "**直接授予用户权限**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-174">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="88f19-175">选择 "**参与**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="88f19-175">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-3-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="88f19-176">步骤3：授予读取权限以便访问在数据刷新中使用的外部数据源</span><span class="sxs-lookup"><span data-stu-id="88f19-176">Step 3: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="88f19-177">在将数据导入到某一 PowerPivot 工作簿时，与外部数据的连接常常基于可信连接或者使用当前用户标识来连接到数据源的模拟连接。</span><span class="sxs-lookup"><span data-stu-id="88f19-177">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="88f19-178">只有在当前用户有权读取其导入的数据时，这些连接类型才有效。</span><span class="sxs-lookup"><span data-stu-id="88f19-178">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="88f19-179">在数据刷新方案中，现在将重复使用过去用于导入数据的相同连接字符串来刷新数据。</span><span class="sxs-lookup"><span data-stu-id="88f19-179">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="88f19-180">如果该连接字符串假定当前用户（例如，包含 Integrated_Security=SSPI 的字符串），则 PowerPivot 系统服务会将在目标应用程序中指定的用户标识作为当前用户传递。</span><span class="sxs-lookup"><span data-stu-id="88f19-180">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity specified in the target application as the current user.</span></span> <span data-ttu-id="88f19-181">只有在帐户对外部数据源具有读取权限时，此连接才会成功。</span><span class="sxs-lookup"><span data-stu-id="88f19-181">This connection will only succeed if the account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="88f19-182">因此，您必须向该帐户授予对数据刷新过程中使用的所有外部数据源的只读权限。</span><span class="sxs-lookup"><span data-stu-id="88f19-182">For this reason, you must grant the account read-only permissions on all of the external data sources that are used during data refresh.</span></span>  
  
 <span data-ttu-id="88f19-183">如果您是组织中使用的数据源的管理员，则可以创建一个登录名，然后分配必需的权限。</span><span class="sxs-lookup"><span data-stu-id="88f19-183">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="88f19-184">否则，您必须与数据所有者联系并且提供帐户信息。</span><span class="sxs-lookup"><span data-stu-id="88f19-184">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="88f19-185">请确保指定映射到目标应用程序的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-185">Be sure to specify the Windows domain user account that maps to the target application.</span></span> <span data-ttu-id="88f19-186">这是你在本主题的 "步骤1：创建目标应用程序" 中指定的帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-186">This is the account you specified in "Step 1: Create a target application" in this topic.</span></span>  
  
###  <a name="step-4-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="88f19-187">步骤4：在数据刷新配置页中验证帐户可用性</span><span class="sxs-lookup"><span data-stu-id="88f19-187">Step 4: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="88f19-188">打开包含 PowerPivot 数据的已发布工作簿的数据刷新配置页。</span><span class="sxs-lookup"><span data-stu-id="88f19-188">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="88f19-189">有关如何打开该页的说明，请参阅[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="88f19-189">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="88f19-190">验证是否在 "数据刷新配置" 页中启用了 "**使用保存在 Secure Store Service (SSS) 登录数据源**" 选项，然后输入目标应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="88f19-190">Verify that the **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source** option is enabled in the data refresh configuration page, and then enter the name of the target application.</span></span>  
  
3.  <span data-ttu-id="88f19-191">选中 "**也尽快刷新**" 复选框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="88f19-191">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="88f19-192">在包含该工作簿的库中，选择该工作簿，单击右侧显示的向下箭头，然后选择 "**管理 PowerPivot 数据刷新**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-192">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="88f19-193">如果数据刷新作业正在返回大量数据，您可能需要等待几分钟。</span><span class="sxs-lookup"><span data-stu-id="88f19-193">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="88f19-194">如果发生错误，你可以在数据刷新历史记录页中单击 "**配置计划**"，尝试使用不同的凭据。</span><span class="sxs-lookup"><span data-stu-id="88f19-194">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="88f19-195">您还可能需要检查原始工作簿中的数据源连接信息，以便查看在数据刷新过程中使用的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="88f19-195">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="88f19-196">该连接字符串将提供与您可用于解决问题的服务器位置和数据库有关的信息。</span><span class="sxs-lookup"><span data-stu-id="88f19-196">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="88f19-197">有关故障排除的详细信息，请参阅 TechNet Wiki 上的[PowerPivot 数据刷新故障排除](https://go.microsoft.com/fwlink/p/?LinkID=223279)。</span><span class="sxs-lookup"><span data-stu-id="88f19-197">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="configure-a-predefined-account-for-accessing-external-or-third-party-data-sources"></a><a name="config3rd"></a><span data-ttu-id="88f19-198">配置用于访问外部或第三方数据源的预定义帐户</span><span class="sxs-lookup"><span data-stu-id="88f19-198">Configure a predefined account for accessing external or third-party data sources</span></span>  
 <span data-ttu-id="88f19-199">数据库服务器通常附带有自己的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="88f19-199">Database servers often come with their own authentication methods.</span></span> <span data-ttu-id="88f19-200">如果 PowerPivot 工作簿要求提供数据库凭据以便在数据刷新期间访问外部数据源，则可以为这些凭据创建一个目标应用程序 ID，然后在“计划数据刷新”页的“数据源”部分指定该目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="88f19-200">If you have a PowerPivot workbook that requires database credentials to access an external data source during data refresh, you can create a target application ID for the credentials, and then specify the target application in the Data Sources section of the schedule data refresh page.</span></span>  
  
 <span data-ttu-id="88f19-201">仅当您希望为用户提供选项，允许其覆盖 PowerPivot 工作簿中已嵌入的数据库凭据时，才需要此步骤。</span><span class="sxs-lookup"><span data-stu-id="88f19-201">This step is only necessary if you want to provide users with an option of overriding the database credentials that are already embedded in the PowerPivot workbook.</span></span>  
  
 <span data-ttu-id="88f19-202">此步骤仅适用于连接字符串已包含用户名和密码的情况。</span><span class="sxs-lookup"><span data-stu-id="88f19-202">This step only works if the connection string already includes a user name and password.</span></span> <span data-ttu-id="88f19-203">请注意，在连接字符串中具有凭据不大常见，因此，您能否使用此选项有时候会受到限制。</span><span class="sxs-lookup"><span data-stu-id="88f19-203">Note that having credentials in the connection string is relatively uncommon, so your ability to make use of this option is somewhat limited.</span></span> <span data-ttu-id="88f19-204">在大多数情况下，如果您在使用数据库身份验证来连接到数据源，则在连接字符串中将仅具有用户 ID 和密码。</span><span class="sxs-lookup"><span data-stu-id="88f19-204">In most cases, you will only have a user ID and password in the connection string if you are using database authentication to connect to the data source.</span></span> <span data-ttu-id="88f19-205">有关如何检查连接字符串以查看它是否包括用户 ID 和密码的详细信息，请参阅[PowerPivot 数据刷新与 SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)中的 "授予创建计划和访问外部数据的权限" 一节。</span><span class="sxs-lookup"><span data-stu-id="88f19-205">For more information about how to check the connection string to see if it includes a User ID and password, see the "Grant permissions to create schedules and access external data" section in [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).</span></span>  
  
1.  <span data-ttu-id="88f19-206">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="88f19-206">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="88f19-207">单击 " **Secure Store Service**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-207">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="88f19-208">在 "管理目标应用程序" 中，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-208">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="88f19-209">在“目标应用程序 ID”中，键入文本字符串。</span><span class="sxs-lookup"><span data-stu-id="88f19-209">In Target application ID, type a text string.</span></span> <span data-ttu-id="88f19-210">此字符串必须唯一，但是还应该容易记住。</span><span class="sxs-lookup"><span data-stu-id="88f19-210">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="88f19-211">每当用户希望使用存储在此应用程序中的凭据时，将在数据刷新计划页中键入此字符串。</span><span class="sxs-lookup"><span data-stu-id="88f19-211">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="88f19-212">在“显示名称”中，输入一个说明性名称。</span><span class="sxs-lookup"><span data-stu-id="88f19-212">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="88f19-213">此名称仅用于显示目的。</span><span class="sxs-lookup"><span data-stu-id="88f19-213">This name is used for display purposes only.</span></span> <span data-ttu-id="88f19-214">不会在数据刷新计划中将其用于指定目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="88f19-214">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="88f19-215">在“联系人电子邮件”中，键入您的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="88f19-215">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="88f19-216">在 "目标应用程序类型" 中选择 "**组**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-216">In Target Application Type, select **Group**.</span></span>  
  
8.  <span data-ttu-id="88f19-217">跳过“目标应用程序页 URL”。</span><span class="sxs-lookup"><span data-stu-id="88f19-217">Skip Target Application Page URL.</span></span> <span data-ttu-id="88f19-218">PowerPivot 数据刷新不会使用它。</span><span class="sxs-lookup"><span data-stu-id="88f19-218">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="88f19-219">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="88f19-219">Click **Next**.</span></span>  
  
10. <span data-ttu-id="88f19-220">在 "**为安全存储目标应用程序指定凭据字段**" 页中，仅在数据源使用 Windows 身份验证时才接受默认值。</span><span class="sxs-lookup"><span data-stu-id="88f19-220">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values only if the data source uses Windows authentication.</span></span> <span data-ttu-id="88f19-221">否则，选择对您的数据源有效的字段类型，然后编辑字段名称以便匹配您选择的类型。</span><span class="sxs-lookup"><span data-stu-id="88f19-221">Otherwise, choose the field types that are valid for your data source, and then edit the field names to match the type.</span></span>  
  
     <span data-ttu-id="88f19-222">例如，您可以为字段名称指定 SQL Server 用户名和 SQL Server 用户密码，然后为字段类型选择用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="88f19-222">For example, you might specify SQL Server User Name and SQL Server User Password for field names, and then choose User Name and Password for field types.</span></span>  
  
11. <span data-ttu-id="88f19-223">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="88f19-223">Click Next.</span></span>  
  
12. <span data-ttu-id="88f19-224">在“目标应用程序管理员”中，指定应该对应用程序设置具有管理权限的 SharePoint 用户的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-224">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="88f19-225">在“成员”中，添加以下用户和组帐户：</span><span class="sxs-lookup"><span data-stu-id="88f19-225">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="88f19-226">作为创建该应用程序的人员，将您的 Windows 用户帐户添加到“成员”列表中。</span><span class="sxs-lookup"><span data-stu-id="88f19-226">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="88f19-227">添加将使用该目标应用程序以访问其存储的凭据的每个 PowerPivot 服务应用程序的应用程序池标识。</span><span class="sxs-lookup"><span data-stu-id="88f19-227">Add the application pool identity of each PowerPivot service application that will be using the target application to access its stored credentials.</span></span> <span data-ttu-id="88f19-228">若要查看标识，请在 "**管理服务应用程序**" 中，通过单击名称旁边的空白区域选择 PowerPivot 服务应用程序 (这将选择行) ，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="88f19-228">To view the identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="88f19-229">此页上显示的安全帐户是您想要作为目标应用程序的成员来添加的帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-229">The security account that appears on this page is the account that you want to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="88f19-230">在数据刷新计划页的数据源部分中添加将输入此目标应用程序的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="88f19-230">Add Windows user and group accounts that will be entering this target application in the data sources section of a data refresh schedule page.</span></span>  
  
14. <span data-ttu-id="88f19-231">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="88f19-231">Click **OK**.</span></span>  
  
15. <span data-ttu-id="88f19-232">选择刚创建的目标应用程序，单击向下箭头并选择 "**设置凭据"。**</span><span class="sxs-lookup"><span data-stu-id="88f19-232">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="88f19-233">输入将用于连接到数据源的凭据（例如，SQL Server 登录名的用户名和密码）。</span><span class="sxs-lookup"><span data-stu-id="88f19-233">Enter the credentials that will be used to connect to the data source (for example, the user name and password of a SQL Server login).</span></span>  
  
17. <span data-ttu-id="88f19-234">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="88f19-234">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f19-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88f19-235">See Also</span></span>  
 <span data-ttu-id="88f19-236">[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="88f19-236">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="88f19-237">使用 SharePoint 2010 进行 PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="88f19-237">PowerPivot Data Refresh with SharePoint 2010</span></span>](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
