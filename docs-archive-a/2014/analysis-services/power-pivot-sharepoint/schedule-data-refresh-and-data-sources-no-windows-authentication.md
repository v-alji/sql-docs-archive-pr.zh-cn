---
title: 计划数据刷新和不支持 Windows 身份验证的数据源 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587018"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a><span data-ttu-id="0a85b-102">计划数据刷新和不支持 Windows 身份验证的数据源 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="0a85b-102">Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="0a85b-103">本主题介绍当数据源**不**支持 Windows 身份验证时，让 PowerPivot for SharePoint 计划数据刷新能够使用该数据源的工作流。</span><span class="sxs-lookup"><span data-stu-id="0a85b-103">This topic describes a workflow of PowerPivot for SharePoint schedule data fresh that can use data sources that do **NOT** support Windows Authentication.</span></span> <span data-ttu-id="0a85b-104">例如 Oracle 或 IDM DB2 数据源。</span><span class="sxs-lookup"><span data-stu-id="0a85b-104">For example Oracle or IDM DB2 data sources.</span></span> <span data-ttu-id="0a85b-105">本主题中的图示和步骤引用 Oracle 数据源，但此工作流也适用于其他数据源。</span><span class="sxs-lookup"><span data-stu-id="0a85b-105">The illustrations and steps in this topic reference Oracle data sources but the same workflow applies to other data sources.</span></span>  
  
||  
|-|  
|<span data-ttu-id="0a85b-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 &#124; SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="0a85b-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 &#124; SharePoint 2013.</span></span>|  
  
 <span data-ttu-id="0a85b-107">**概述：** 创建两个安全存储区目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a85b-107">**Overview:** Create two Secure Store Target Applications.</span></span> <span data-ttu-id="0a85b-108">将第 1 个目标应用程序 (PowerPivotDataRefresh) 配置为使用 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="0a85b-108">Configure the first target application (PowerPivotDataRefresh) to use Windows credentials.</span></span> <span data-ttu-id="0a85b-109">针对诸如 Oracle 数据库等不支持 Windows 身份验证的数据源，使用这些凭据配置第 2 个目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a85b-109">Configure the second target application with the credentials for a data source that does not support windows authentication, for example, an Oracle database.</span></span> <span data-ttu-id="0a85b-110">对于无人参与的数据刷新帐户，第 2 个目标应用程序也将使用第 1 个目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a85b-110">The second target application also uses the first target application for the unattended data refresh account.</span></span>  
  
 <span data-ttu-id="0a85b-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span><span class="sxs-lookup"><span data-stu-id="0a85b-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span></span>  
  
-   <span data-ttu-id="0a85b-112">**(1) PowerPivotDatarefresh：** 此安全存储区目标应用程序 ID 使用 Windows 身份验证进行设置。</span><span class="sxs-lookup"><span data-stu-id="0a85b-112">**(1) PowerPivotDatarefresh:** A Secure Store Target Application ID that is set with windows authentication.</span></span>  
  
-   <span data-ttu-id="0a85b-113">**(2) OracleAuthentication：** 此安全存储区目标应用程序 ID 使用 Oracle 凭据进行设置。</span><span class="sxs-lookup"><span data-stu-id="0a85b-113">**(2) OracleAuthentication:** A Secure Store Target Application ID that is set with Oracle credentials.</span></span>  
  
-   <span data-ttu-id="0a85b-114">\*\* (3) **对于**无人参与的数据刷新帐户\*\*，PowerPivot 服务应用程序配置为使用目标应用程序 "PowerPivotDataRefresh"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-114">**(3)** The PowerPivot Service application is configure to use the target application "PowerPivotDataRefresh" for the **Unattended Data Refresh Account**.</span></span>  
  
-   <span data-ttu-id="0a85b-115">**(4)** PowerPivot 工作簿使用 Oracle 数据。</span><span class="sxs-lookup"><span data-stu-id="0a85b-115">**(4)** PowerePivot Workbook uses Oracle data.</span></span> <span data-ttu-id="0a85b-116">工作簿刷新设置指定数据源连接以使用凭据的目标应用程序 **(2)** 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-116">The workbook refresh settings specify the data source connection to use the target application **(2)** for credentials.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a85b-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="0a85b-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="0a85b-118">存在 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a85b-118">A PowerPivot Service Application exists.</span></span>  
  
-   <span data-ttu-id="0a85b-119">存在 Secure Store Service 应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a85b-119">A Secure Store Service Application exists.</span></span>  
  
-   <span data-ttu-id="0a85b-120">存在带有 PowerPivot 数据模型的 Excel 工作簿。</span><span class="sxs-lookup"><span data-stu-id="0a85b-120">An Excel workbook with a PowerPivot data model exists.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a><span data-ttu-id="0a85b-121">创建使用 Windows 身份验证的目标应用程序 ID</span><span class="sxs-lookup"><span data-stu-id="0a85b-121">To Create a Target Application ID that uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="0a85b-122">在 SharePoint 管理中心中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-122">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="0a85b-123">单击 Secure Store Service 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="0a85b-123">Click the name of your secure store service application.</span></span>  
  
3.  <span data-ttu-id="0a85b-124">在 "**管理**" 页上，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-124">On the **Manage** page, click **New**.</span></span> <span data-ttu-id="0a85b-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span><span class="sxs-lookup"><span data-stu-id="0a85b-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span></span>  
  
4.  <span data-ttu-id="0a85b-126">在 **“创建新的安全存储区目标应用程序”** 页上，配置下列值：</span><span class="sxs-lookup"><span data-stu-id="0a85b-126">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="0a85b-127">**目标应用程序 ID：** PowerPivotDataRefresh。</span><span class="sxs-lookup"><span data-stu-id="0a85b-127">**Target Application ID:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="0a85b-128">**显示名称：** PowerPivotDataRefresh。</span><span class="sxs-lookup"><span data-stu-id="0a85b-128">**Display Name:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="0a85b-129">**联系人电子邮件：** ？</span><span class="sxs-lookup"><span data-stu-id="0a85b-129">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="0a85b-130">**目标应用程序类型：** 组。</span><span class="sxs-lookup"><span data-stu-id="0a85b-130">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="0a85b-131">**目标应用程序页 URL：** 无。</span><span class="sxs-lookup"><span data-stu-id="0a85b-131">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="0a85b-132">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a85b-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0a85b-133">在“凭据”页上，将 **“Windows 用户名”** 和 **“Windows 密码”** 这两个字段的名称和类型都保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="0a85b-133">On the Credentials page, leave the two default field names and field types for **Windows User Name** and **Windows Password**.</span></span>  
  
7.  <span data-ttu-id="0a85b-134">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a85b-134">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="0a85b-135">在 **“成员资格设置”** 页上，添加至少一个 **“目标应用程序管理员”** ，然后添加需要目标应用程序的访问权限的成员。</span><span class="sxs-lookup"><span data-stu-id="0a85b-135">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="0a85b-136">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0a85b-136">Click **OK**.</span></span>  
  
10. <span data-ttu-id="0a85b-137">一个新的目标应用程序 ID 会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="0a85b-137">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="0a85b-138">选择目标应用程序 ID，然后单击 "**设置凭据**"![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")。</span><span class="sxs-lookup"><span data-stu-id="0a85b-138">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="0a85b-139">键入 Windows 用户名和 Windows 密码，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-139">Type the Windows User Name and Windows Password and then click **OK**.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a><span data-ttu-id="0a85b-140">创建使用 Oracle 凭据的目标应用程序 ID</span><span class="sxs-lookup"><span data-stu-id="0a85b-140">To Create a Target Application ID that uses Oracle credentials</span></span>  
  
1.  <span data-ttu-id="0a85b-141">在 SharePoint 管理中心中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-141">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="0a85b-142">单击 Secure Store Service 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="0a85b-142">Click the name of your Secure Store Service application.</span></span>  
  
3.  <span data-ttu-id="0a85b-143">在 "**管理**" 页上，单击 "**新建**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-143">On the **Manage** page, click **New**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").</span></span>  
  
4.  <span data-ttu-id="0a85b-144">在 **“创建新的安全存储区目标应用程序”** 页上，配置下列值：</span><span class="sxs-lookup"><span data-stu-id="0a85b-144">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="0a85b-145">**目标应用程序 ID：** OracleAuthentication。</span><span class="sxs-lookup"><span data-stu-id="0a85b-145">**Target Application ID:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="0a85b-146">**显示名称：** OracleAuthentication。</span><span class="sxs-lookup"><span data-stu-id="0a85b-146">**Display Name:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="0a85b-147">**联系人电子邮件：** ？</span><span class="sxs-lookup"><span data-stu-id="0a85b-147">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="0a85b-148">**目标应用程序类型：** 组。</span><span class="sxs-lookup"><span data-stu-id="0a85b-148">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="0a85b-149">**目标应用程序页 URL：** 无。</span><span class="sxs-lookup"><span data-stu-id="0a85b-149">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="0a85b-150">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a85b-150">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0a85b-151">在 "**凭据**" 页上，将第一个字段名称更改为 `Oracle User ID` ，并将**字段类型**更改为 `User Name` 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-151">On the **Credentials** page, change the first field name to `Oracle User ID` and change the **Field Type** to `User Name`.</span></span>  
  
     <span data-ttu-id="0a85b-152">将第二个字段名称更改为 `Oracle Password` ，并将**字段类型**更改为 `Password` 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-152">Change the second field name to `Oracle Password` and the **Field Type** to `Password`.</span></span>  
  
7.  <span data-ttu-id="0a85b-153">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a85b-153">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="0a85b-154">在 **“成员资格设置”** 页上，添加至少一个 **“目标应用程序管理员”** ，然后添加需要目标应用程序的访问权限的成员。</span><span class="sxs-lookup"><span data-stu-id="0a85b-154">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="0a85b-155">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0a85b-155">Click **OK**.</span></span>  
  
10. <span data-ttu-id="0a85b-156">一个新的目标应用程序 ID 会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="0a85b-156">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="0a85b-157">选择目标应用程序 ID，然后单击 "**设置凭据**"![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")。</span><span class="sxs-lookup"><span data-stu-id="0a85b-157">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="0a85b-158">键入 Oracle 用户 ID 和 Oracle 密码，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-158">Type the Oracle User ID and Oracle Password and then click **OK**.</span></span>  
  
 <span data-ttu-id="0a85b-159">有关详细信息，请参阅[使用 SQL Server Authentication (SharePoint Server 2013) ](https://technet.microsoft.com/library/gg298949.aspx) (中的 "为 SQL Server 身份验证创建目标应用程序" 部分 https://technet.microsoft.com/library/gg298949.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-159">For more information, see section "To Create a target application for SQL Server Authentication" in [Use Secure Store with SQL Server Authentication (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) (https://technet.microsoft.com/library/gg298949.aspx).</span></span>  
  
## <a name="to-configure-the-powerpivot-service-application"></a><span data-ttu-id="0a85b-160">若要配置 PowerPivot 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="0a85b-160">To Configure the PowerPivot Service Application</span></span>  
  
1.  <span data-ttu-id="0a85b-161">在 SharePoint 管理中心中，单击“管理服务应用程序”。</span><span class="sxs-lookup"><span data-stu-id="0a85b-161">In SharePoint central administration, click Manage Service Applications.</span></span>  
  
2.  <span data-ttu-id="0a85b-162">单击 PowerPivot 服务应用程序的名称，例如 "默认 PowerPivot 服务应用程序"。</span><span class="sxs-lookup"><span data-stu-id="0a85b-162">Click the name of your PowerPivot Service Application, for example "Default PowerPivot Service Application".</span></span>  
  
3.  <span data-ttu-id="0a85b-163">在“操作”节中，单击 **“配置服务应用程序设置”** 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-163">Click **Configure service application settings** in the Actions section.</span></span>  
  
4.  <span data-ttu-id="0a85b-164">在 "**数据刷新**" 部分中，将**PowerPivot 无人参与的数据刷新帐户**设置为， `PowerPivotDataRefresh` 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-164">In the **Data Refresh** section, set the **PowerPivot Unattended Data Refresh Account**to`PowerPivotDataRefresh` and then click **OK**.</span></span>  
  
     <span data-ttu-id="0a85b-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span><span class="sxs-lookup"><span data-stu-id="0a85b-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span></span>  
  
## <a name="to-configure-the-workbook"></a><span data-ttu-id="0a85b-166">配置工作簿</span><span class="sxs-lookup"><span data-stu-id="0a85b-166">To configure the workbook</span></span>  
  
1.  <span data-ttu-id="0a85b-167">在 PowerPivot 库中浏览到工作簿，然后单击 "**管理数据刷新**"![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh")。</span><span class="sxs-lookup"><span data-stu-id="0a85b-167">Browse to your workbook in the PowerPivot Gallery and click **Manage Data Refresh**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").</span></span>  
  
2.  <span data-ttu-id="0a85b-168">如果出现 **“数据刷新历史记录”** 页，单击 **“配置计划”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-168">If you see the **Data Refresh History** page, click **Configure Schedule**.</span></span>  
  
3.  <span data-ttu-id="0a85b-169">单击 **“启用”** 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-169">Click **Enable**.</span></span>  
  
4.  <span data-ttu-id="0a85b-170">单击 **“也尽快刷新”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-170">Click **Also Refresh as soon as possible**.</span></span>  
  
5.  <span data-ttu-id="0a85b-171">在 **“凭据”** 节中，单击 **“使用管理员配置的数据刷新帐户”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-171">In the **Credentials** section, click **Use the Data refresh account configured by the administrator**.</span></span>  
  
6.  <span data-ttu-id="0a85b-172">清除 **“所有数据源”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-172">Clear **All data sources**.</span></span>  
  
7.  <span data-ttu-id="0a85b-173">针对使用 Oracle 数据的数据源，选择 **“刷新”** 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-173">Select **Refresh** for the data source that uses the Oracle data.</span></span> <span data-ttu-id="0a85b-174">在 Microsoft Excel 的 **“数据”**-&gt; **“连接”**-&gt; **“属性”** 菜单中，可以更改此数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="0a85b-174">The name of the data source name can be changed in Microsoft Excel in the **Data**, **Connections**, **Properties** menu.</span></span>  
  
8.  <span data-ttu-id="0a85b-175">在数据源下，选择 **“使用默认计划”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-175">Under your data source, Select **Use Default Schedule**.</span></span>  
  
9. <span data-ttu-id="0a85b-176">选择 **“使用在 Secure Store Service (SSS) 中保存的凭据连接以登录数据源。在 SSS ID 框中输入用于查找凭据的 ID”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-176">Select **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source. Enter the ID used to look up the credentials in the SSS ID box**.</span></span>  
  
10. <span data-ttu-id="0a85b-177">在 " **ID：** " 框中，键入 `OracleAuthentication` 。</span><span class="sxs-lookup"><span data-stu-id="0a85b-177">In the **ID:** box, type `OracleAuthentication`.</span></span>  
  
11. <span data-ttu-id="0a85b-178">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0a85b-178">Click **OK**.</span></span>  
  
     <span data-ttu-id="0a85b-179">如果出现类似以下的错误消息： `The provided Secure Store target application is either incorrectly configured or does not exist`。</span><span class="sxs-lookup"><span data-stu-id="0a85b-179">If you see an error message similar to: `The provided Secure Store target application is either incorrectly configured or does not exist`.</span></span>  
  
     <span data-ttu-id="0a85b-180">通常有两个解决方案：</span><span class="sxs-lookup"><span data-stu-id="0a85b-180">The two common solutions are:</span></span>  
  
    -   <span data-ttu-id="0a85b-181">确认目标应用程序 ID 正确无误。</span><span class="sxs-lookup"><span data-stu-id="0a85b-181">Verify that the Target Application ID is correct.</span></span>  
  
    -   <span data-ttu-id="0a85b-182">确认已为该目标应用程序设置凭据。</span><span class="sxs-lookup"><span data-stu-id="0a85b-182">Verify that you set credentials for the Target Application.</span></span>  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a><span data-ttu-id="0a85b-183">使用新身份验证信息来验证数据刷新</span><span class="sxs-lookup"><span data-stu-id="0a85b-183">To Verify Data Refresh with the new authentication</span></span>  
 <span data-ttu-id="0a85b-184">单击 **“确定”** 时，将出现 **“刷新历史记录”** 页。</span><span class="sxs-lookup"><span data-stu-id="0a85b-184">When you click **ok**, you see the **Refresh History** page.</span></span> <span data-ttu-id="0a85b-185">数分钟内，刷新历史记录中应会出现一个新项，因为在上述步骤中选中了 **“也尽快刷新”**。</span><span class="sxs-lookup"><span data-stu-id="0a85b-185">Within a few minutes, you should see a new item in the refresh history because in the previous steps you selected **Also Refresh as soon as possible**.</span></span> <span data-ttu-id="0a85b-186">**PowerPivot 数据刷新计时器作业**的计时器作业默认值是 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="0a85b-186">The default value for the timer job **PowerPivot Data Refresh Timer Job** is 1 minute.</span></span> <span data-ttu-id="0a85b-187">如果刷新历史记录中未出现新项，请等待数分钟，然后刷新浏览器。</span><span class="sxs-lookup"><span data-stu-id="0a85b-187">If you do not see a new item in the refresh history, wait a few minutes and refresh your browser.</span></span> <span data-ttu-id="0a85b-188">如果仍未出现新项，请确认计时器作业的当前值。</span><span class="sxs-lookup"><span data-stu-id="0a85b-188">If you still do not see the new item, verify the current value of the timer job.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="0a85b-189">更多信息</span><span class="sxs-lookup"><span data-stu-id="0a85b-189">More Information</span></span>  
  
-   <span data-ttu-id="0a85b-190">[配置 SharePoint 2013 中的 Secure Store Service](https://technet.microsoft.com/library/ee806866.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a85b-190">[Configure the Secure Store Service in SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).</span></span>  
  
-   <span data-ttu-id="0a85b-191">请参阅利用 SharePoint 2013 的 PowerPivot 数据刷新的 "计划的数据刷新" 部分[，并 SQL Server 2012 SP1 (Analysis Services) ](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)。</span><span class="sxs-lookup"><span data-stu-id="0a85b-191">See the "Scheduled Data Refresh" section of [PowerPivot Data Refresh with SharePoint 2013 and SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).</span></span>  
  
  
