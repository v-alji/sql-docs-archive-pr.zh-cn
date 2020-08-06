---
title: 创建与 PowerPivot 工作簿的 BI 语义模型连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589277"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a><span data-ttu-id="7e13e-102">创建与 PowerPivot 工作簿的 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="7e13e-102">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>
  <span data-ttu-id="7e13e-103">使用本主题中的信息可设置一个 BI 语义模型连接，该连接重定向到同一个场中的 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="7e13e-103">Use the information in this topic to set up a BI semantic model connection that redirects to a PowerPivot workbook in the same farm.</span></span>  
  
 <span data-ttu-id="7e13e-104">在您创建了 BI 语义模型连接并且配置了 SharePoint 权限后，可以将其用作 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表的数据源。</span><span class="sxs-lookup"><span data-stu-id="7e13e-104">After you create a BI semantic model connection and configure SharePoint permissions, you can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="7e13e-105">本主题包含以下各节。</span><span class="sxs-lookup"><span data-stu-id="7e13e-105">This topic includes the following sections.</span></span> <span data-ttu-id="7e13e-106">按给出的顺序执行每个任务。</span><span class="sxs-lookup"><span data-stu-id="7e13e-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="7e13e-107">检查必备条件</span><span class="sxs-lookup"><span data-stu-id="7e13e-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="7e13e-108">创建连接</span><span class="sxs-lookup"><span data-stu-id="7e13e-108">Create a Connection</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="7e13e-109">配置针对 BI 语义模型连接的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="7e13e-109">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="7e13e-110">配置针对工作簿的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="7e13e-110">Configure SharePoint Permissions on the Workbook</span></span>](#bkmk_userdb)  
  
 [<span data-ttu-id="7e13e-111">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7e13e-111">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="7e13e-112">查看先决条件</span><span class="sxs-lookup"><span data-stu-id="7e13e-112">Review Prerequisites</span></span>  
 <span data-ttu-id="7e13e-113">您必须具有“参与讨论”权限或更高权限以创建 BI 语义模型连接文件。</span><span class="sxs-lookup"><span data-stu-id="7e13e-113">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="7e13e-114">您必须具有支持 BI 语义模型连接内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="7e13e-114">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="7e13e-115">有关详细信息，请参阅[将 BI 语义模型连接内容类型添加到库 &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)。</span><span class="sxs-lookup"><span data-stu-id="7e13e-115">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="7e13e-116">您必须知道您为其设置 BI 语义模型连接 (例如 http://adventure-works/shared 文档/myworkbook.xlsx) 的 PowerPivot 工作簿的 URL。</span><span class="sxs-lookup"><span data-stu-id="7e13e-116">You must know the URL of the PowerPivot workbook for which you are setting up a BI semantic model connection (for example, http://adventure-works/shared documents/myworkbook.xlsx).</span></span> <span data-ttu-id="7e13e-117">工作簿必须位于同一场中。</span><span class="sxs-lookup"><span data-stu-id="7e13e-117">The workbook must be in the same farm.</span></span>  
  
 <span data-ttu-id="7e13e-118">参与连接序列的所有计算机和用户都必须处于同一个域或可信域（双向信任）中。</span><span class="sxs-lookup"><span data-stu-id="7e13e-118">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a><span data-ttu-id="7e13e-119">创建连接</span><span class="sxs-lookup"><span data-stu-id="7e13e-119">Create a Connection</span></span>  
  
1.  <span data-ttu-id="7e13e-120">在将包含 BI 语义模型连接的库中，单击 SharePoint 功能区上的 **“文档”** 。</span><span class="sxs-lookup"><span data-stu-id="7e13e-120">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span> <span data-ttu-id="7e13e-121">单击“新建文档”上的向下箭头，然后选择 **“BISM 连接文件”** 以便打开“新建 BI 语义模型连接”页。</span><span class="sxs-lookup"><span data-stu-id="7e13e-121">Click the down arrow on New Document, and select **BISM Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
     <span data-ttu-id="7e13e-122">![SharePoint 库中的“新建文档”子菜单](../media/ssas-bismconnection-new.gif "SharePoint 库中的“新建文档”子菜单")</span><span class="sxs-lookup"><span data-stu-id="7e13e-122">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
2.  <span data-ttu-id="7e13e-123">将**服务器**属性设置为 PowerPivot 工作簿的 SharePoint URL (例如， \*\* http://mysharepoint/shared documents/myWorkbook.xlsx\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e13e-123">Set the **Server** property to the SharePoint URL of the PowerPivot workbook (for example, **http://mysharepoint/shared documents/myWorkbook.xlsx**.</span></span> <span data-ttu-id="7e13e-124">在 PowerPivot for SharePoint 部署中，数据可从场中的任何服务器上加载。</span><span class="sxs-lookup"><span data-stu-id="7e13e-124">In a PowerPivot for SharePoint deployment, data can be loaded on any server in the farm.</span></span> <span data-ttu-id="7e13e-125">因此，与 PowerPivot 数据的数据源连接仅指定指向工作簿的路径。</span><span class="sxs-lookup"><span data-stu-id="7e13e-125">For this reason, data source connections to PowerPivot data specify just the path to the workbook.</span></span> <span data-ttu-id="7e13e-126">PowerPivot 系统服务将确定哪一服务器将加载数据。</span><span class="sxs-lookup"><span data-stu-id="7e13e-126">The PowerPivot System Service determines which server loads the data.</span></span>  
  
     <span data-ttu-id="7e13e-127">不要使用**数据库**属性;它在指定 PowerPivot 工作簿的位置时不使用。</span><span class="sxs-lookup"><span data-stu-id="7e13e-127">Do not use the **Database** property; it is not used when specifying the location of a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="7e13e-128">页面的外观应该如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7e13e-128">Your page should look similar to the following illustration.</span></span>  
  
     <span data-ttu-id="7e13e-129">![显示工作簿 URL 的 BISM 连接页](../media/ssas-bismconnection-ppvtds.gif "显示工作簿 URL 的 BISM 连接页")</span><span class="sxs-lookup"><span data-stu-id="7e13e-129">![BISM connection page showing URL to workbook](../media/ssas-bismconnection-ppvtds.gif "BISM connection page showing URL to workbook")</span></span>  
  
     <span data-ttu-id="7e13e-130">或者，如果您具有针对工作簿的 SharePoint 权限，则要执行一个附加的验证步骤，以便确保该位置有效。</span><span class="sxs-lookup"><span data-stu-id="7e13e-130">Optionally, if you have SharePoint permissions to the workbook, an extra validation step is performed, ensuring that the location is valid.</span></span> <span data-ttu-id="7e13e-131">如果您没有对数据的访问权限，则会向您提供一个无需验证响应即保存 BI 语义模型连接的选项。</span><span class="sxs-lookup"><span data-stu-id="7e13e-131">If you do not have permission to access the data, you are given the option of saving the BI semantic model connection without the validation response.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="7e13e-132">配置针对 BI 语义模型连接的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="7e13e-132">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="7e13e-133">为了能够使用 BI 语义模型连接作为 Excel 工作簿或 Reporting Services 报表的数据源，需要针对 SharePoint 库中 BI 语义模型连接项的 **“读取”** 权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-133">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="7e13e-134">该“读取”权限级别包括 **“打开项”** 权限，该权限支持将 BI 语义模型连接信息下载到 Excel 桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="7e13e-134">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="7e13e-135">有几种方法可在 SharePoint 中授予权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-135">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="7e13e-136">下面的说明解释如何新建一个名为 **BISM Users** 的具有“读取” \*\*\*\* 权限级别的组。</span><span class="sxs-lookup"><span data-stu-id="7e13e-136">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="7e13e-137">您必须是网站所有者才能更改权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-137">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="7e13e-138">在“网站操作”中，单击 **“网站权限”**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-138">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="7e13e-139">单击“创建组” \*\*\*\* 并将新组命名为 **BISM Users**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-139">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="7e13e-140">选择 **“读取”** 权限级别，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-140">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="7e13e-141">在“人员和组”中选择 **BISM Users** 。</span><span class="sxs-lookup"><span data-stu-id="7e13e-141">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="7e13e-142">指向“新建”，单击 **“添加用户”**，然后添加用户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="7e13e-142">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="7e13e-143">此时，这些用户和组将拥有对整个网站的“读取”权限，包括从网站级别继承权限的所有库和列表。</span><span class="sxs-lookup"><span data-stu-id="7e13e-143">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="7e13e-144">如果这些权限太高，则可以选择从特定的库、列表或项中删除此组。</span><span class="sxs-lookup"><span data-stu-id="7e13e-144">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="7e13e-145">若要选择性地删除项目级别的权限，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7e13e-145">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="7e13e-146">在库中选择一个文档。</span><span class="sxs-lookup"><span data-stu-id="7e13e-146">In a library, select a document.</span></span> <span data-ttu-id="7e13e-147">单击右下箭头，然后单击 **“管理权限”**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-147">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="7e13e-148">默认情况下，项会继承权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-148">By default, an item inherits permissions.</span></span> <span data-ttu-id="7e13e-149">若要更改此库中的单个文档的权限，请单击 **“停止继承权限”**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-149">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="7e13e-150">选中 \*\*\*\*“BISM 用户”旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="7e13e-150">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="7e13e-151">单击 **“删除用户权限”**。</span><span class="sxs-lookup"><span data-stu-id="7e13e-151">Click **Remove User Permissions**.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a><span data-ttu-id="7e13e-152">配置针对工作簿的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="7e13e-152">Configure SharePoint Permissions on the Workbook</span></span>  
 <span data-ttu-id="7e13e-153">如果您在一个 Excel 工作簿内使用某一 PowerPivot 数据库，则针对该 Excel 工作簿的 SharePoint 权限将确定通过 BI 语义模型连接进行的数据访问。</span><span class="sxs-lookup"><span data-stu-id="7e13e-153">If you are using a PowerPivot database inside an Excel workbook, the SharePoint permissions on the Excel workbook determine data access via the BI semantic model connection.</span></span> <span data-ttu-id="7e13e-154">为了将工作簿用作外部数据源，访问该工作簿的所有用户都必须对工作簿具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-154">All users who access the workbook must have Read permissions on the workbook in order to use it as an external data source.</span></span>  
  
 <span data-ttu-id="7e13e-155">如果你使用了前一部分中的说明创建了 **BISM Users** 组，则 **BISM Users** 组成员的用户和组帐户将拥有该工作簿以及 BI 语义模型连接文件的足够权限，并且假定该工作簿使用继承的权限。</span><span class="sxs-lookup"><span data-stu-id="7e13e-155">If you created a **BISM Users** group using the instructions in the previous section, user and group accounts that are members of **BISM Users** will have sufficient permission on the workbook as well as the BI semantic model connection file, assuming the workbook uses inherited permissions.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a><span data-ttu-id="7e13e-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7e13e-156">Next Steps</span></span>  
 <span data-ttu-id="7e13e-157">创建了 BI 语义模型连接并且确保其安全后，可以将该连接指定为数据源。</span><span class="sxs-lookup"><span data-stu-id="7e13e-157">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="7e13e-158">有关详细信息，请参阅 [在 Excel 或 Reporting Services 中使用 BI 语义模型连接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7e13e-158">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e13e-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e13e-159">See Also</span></span>  
 <span data-ttu-id="7e13e-160">[PowerPivot BI 语义模型连接 &#40; bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="7e13e-160">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 <span data-ttu-id="7e13e-161">[在 Excel 或 Reporting Services 中使用 BI 语义模型连接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="7e13e-161">[Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span></span>  
 [<span data-ttu-id="7e13e-162">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="7e13e-162">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
