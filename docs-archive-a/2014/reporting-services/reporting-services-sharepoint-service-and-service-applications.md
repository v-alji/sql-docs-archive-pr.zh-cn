---
title: SharePoint 服务和服务应用程序 Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5654764f7913002cdae58d3264848250a292c585
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591758"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a><span data-ttu-id="a774c-102">Reporting Services SharePoint 服务和服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-102">Reporting Services SharePoint Service and Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="a774c-103">SharePoint 模式的体系结构以 SharePoint 体系结构为基础，并利用 SharePoint 服务和一对多服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a774c-103">SharePoint mode is architected on the SharePoint service architecture and utilizes a SharePoint service and one to many service applications.</span></span> <span data-ttu-id="a774c-104">创建服务应用程序将使该服务可用并生成服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="a774c-104">Creating a service application makes the service available and generates the service application database.</span></span> <span data-ttu-id="a774c-105">您可以创建多个 Reporting Services 服务应用程序，但一个服务应用程序已足以用于大多数部署方案。</span><span class="sxs-lookup"><span data-stu-id="a774c-105">You can create multiple Reporting Services service applications but one service application is sufficient for most deployment scenarios.</span></span>  
  
 <span data-ttu-id="a774c-106">本主题涵盖以下信息：</span><span class="sxs-lookup"><span data-stu-id="a774c-106">This topic covers the following information:</span></span>  
  
-   [<span data-ttu-id="a774c-107">创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-107">Creating a Reporting Services Service Application</span></span>](#bkmk_createapp)  
  
-   [<span data-ttu-id="a774c-108">修改服务应用程序与代理组的关联</span><span class="sxs-lookup"><span data-stu-id="a774c-108">Modify the Associations of the Service Application with a proxy group</span></span>](#bkmk_associations)  
  
-   [<span data-ttu-id="a774c-109">编辑服务应用程序属性</span><span class="sxs-lookup"><span data-stu-id="a774c-109">Edit Service Application Properties</span></span>](#bkmk_editserviceapplication)  
  
-   [<span data-ttu-id="a774c-110">使用 PowerShell 创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-110">To create a Reporting Services Service Application using PowerShell</span></span>](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [<span data-ttu-id="a774c-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="a774c-111">Related Tasks</span></span>](#bkmk_related)  
  
##  <a name="creating-a-reporting-services-service-application"></a><a name="bkmk_createapp"></a><span data-ttu-id="a774c-112">创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-112">Creating a Reporting Services Service Application</span></span>  
 <span data-ttu-id="a774c-113">您可以使用 SharePoint 管理中心或 PowerShell 脚本创建 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a774c-113">You can use SharePoint Central Administration or PowerShell scripts to create the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services applications.</span></span> <span data-ttu-id="a774c-114">有关如何使用 SharePoint 管理中心的详细信息，请参阅[安装 SharePoint 2010 的 Reporting Services SharePoint 模式](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)中的“创建 Reporting Services 服务应用程序”一节。</span><span class="sxs-lookup"><span data-stu-id="a774c-114">For more information on using SharePoint Central Administration, see the "Create a Reporting Services Service Application" section in [Install Reporting Services SharePoint Mode for SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span> <span data-ttu-id="a774c-115">有关创建服务应用程序的示例 PowerShell 脚本，请参阅本主题中后面的 PowerShell 部分。</span><span class="sxs-lookup"><span data-stu-id="a774c-115">See the PowerShell section later in this topic for a sample PowerShell script for creating service applications.</span></span>  
  
##  <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a><a name="bkmk_associations"></a><span data-ttu-id="a774c-116">修改服务应用程序与代理组的关联</span><span class="sxs-lookup"><span data-stu-id="a774c-116">Modify the Associations of the Service Application with a proxy group</span></span>  
 <span data-ttu-id="a774c-117">创建服务应用程序的“新建”页包含 **“Web 应用程序关联”** 部分。</span><span class="sxs-lookup"><span data-stu-id="a774c-117">The New page for creating a services application contains the section **Web Application Association**.</span></span> <span data-ttu-id="a774c-118">此部分允许您在创建服务应用程序时对其进行关联。</span><span class="sxs-lookup"><span data-stu-id="a774c-118">The section allows you to associate your service application as you create it.</span></span> <span data-ttu-id="a774c-119">使用以下步骤可更改关联和将客户配置分配给服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a774c-119">Use the following steps to change the association and assign a customer configuration to the service application.</span></span> <span data-ttu-id="a774c-120">还可以使用相同的常规过程将代理添加到默认组，而不是更改服务应用程序与自定义组的关联。</span><span class="sxs-lookup"><span data-stu-id="a774c-120">The same general process can also be used to add the proxy to the default group rather than changing the association of the service application to a custom group.</span></span>  
  
1.  <span data-ttu-id="a774c-121">在 SharePoint 管理中心内，在“应用程序管理”中单击 **“配置服务应用程序关联”**。</span><span class="sxs-lookup"><span data-stu-id="a774c-121">In SharePoint Central Administration, in the Application Management, click **Configure Service Application Associations**.</span></span>  
  
2.  <span data-ttu-id="a774c-122">在“服务应用程序关联”页中，将视图更改为 **“服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="a774c-122">On the Service application Associations page, change the view to **Service Applications**.</span></span>  
  
3.  <span data-ttu-id="a774c-123">找到并单击新 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="a774c-123">Find and click the name of your new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service application.</span></span> <span data-ttu-id="a774c-124">也可以单击应用程序代理组名称 **默认值** 以将代理添加到默认组，而不是完成以下步骤。</span><span class="sxs-lookup"><span data-stu-id="a774c-124">You could also click the application proxy group name **default** to add the proxy to default group rather than completing the following steps.</span></span>  
  
4.  <span data-ttu-id="a774c-125">在 **“编辑以下连接组”** 选择框中，选择 **自定义**。</span><span class="sxs-lookup"><span data-stu-id="a774c-125">Select **Custom** in the selection box **Edit the following group of connections**.</span></span>  
  
5.  <span data-ttu-id="a774c-126">选中代理对应的框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a774c-126">Check the box for your proxy and click **Ok**.</span></span>  
  
##  <a name="edit-service-application-properties"></a><a name="bkmk_editserviceapplication"></a><span data-ttu-id="a774c-127">编辑服务应用程序属性</span><span class="sxs-lookup"><span data-stu-id="a774c-127">Edit Service Application Properties</span></span>  
 <span data-ttu-id="a774c-128">您可以重新打开服务应用程序的属性页以修改属性。</span><span class="sxs-lookup"><span data-stu-id="a774c-128">You can reopen the property page of the service application to modify the properties.</span></span>  
  
1.  <span data-ttu-id="a774c-129">在 SharePoint 管理中心的 "应用程序管理" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="a774c-129">In SharePoint Central Administration, in the Application Management group, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="a774c-130">通过单击类型列以选择整行，选择服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a774c-130">Select the service application by clicking the type column to select the entire row.</span></span> <span data-ttu-id="a774c-131">如果您单击应用程序的名称，将打开服务的“管理”选项页，而不是打开服务应用程序的属性。</span><span class="sxs-lookup"><span data-stu-id="a774c-131">If you click the name of the application it, the Management options page for the service opens instead of opening the properties of the service application.</span></span>  
  
3.  <span data-ttu-id="a774c-132">在“服务应用程序”功能区中，单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="a774c-132">In the Service Applications ribbon, click **Properties**.</span></span>  
  
##  <a name="to-create-a-reporting-services-service-application-using-powershell"></a><a name="bkmk_powershell_create_ssrs_serviceapp"></a><span data-ttu-id="a774c-133">使用 PowerShell 创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-133">To create a Reporting Services Service Application using PowerShell</span></span>  
 <span data-ttu-id="a774c-134">您可以使用 PowerShell 创建服务应用程序和代理。</span><span class="sxs-lookup"><span data-stu-id="a774c-134">You can use PowerShell to create the Service application and proxy.</span></span> <span data-ttu-id="a774c-135">下面的示例假定您知道要配置服务应用程序使用的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="a774c-135">The sample below assumes that you know what application pool you want to configure the service application to use.</span></span>  
  
1.  <span data-ttu-id="a774c-136">将应用程序池名称的应用程序池对象添加到要传递到“新建”操作的变量。</span><span class="sxs-lookup"><span data-stu-id="a774c-136">Add the application pool object of your application pool name to a variable that is passed into the New action.</span></span>  
  
    ```powershell
    $appPoolName = Get-SPServiceApplicationPool "<application pool name>"  
    ```  
  
2.  <span data-ttu-id="a774c-137">使用您提供的名称和应用程序池名称创建服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a774c-137">Create the service application with a name and application pool name you provide.</span></span>  
  
    ```powershell
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  <span data-ttu-id="a774c-138">获取新的服务应用程序对象，并将此对象传送到新代理 cmdlet 的管道中。</span><span class="sxs-lookup"><span data-stu-id="a774c-138">Get the new service application object, and pipe the object into the Pipe the new proxy cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="related-tasks"></a><a name="bkmk_related"></a> <span data-ttu-id="a774c-139">相关任务</span><span class="sxs-lookup"><span data-stu-id="a774c-139">Related Tasks</span></span>  
  
|<span data-ttu-id="a774c-140">任务</span><span class="sxs-lookup"><span data-stu-id="a774c-140">Task</span></span>|<span data-ttu-id="a774c-141">链接</span><span class="sxs-lookup"><span data-stu-id="a774c-141">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="a774c-142">管理您的服务应用程序的设置。</span><span class="sxs-lookup"><span data-stu-id="a774c-142">Manage the settings of your Service Application.</span></span>|[<span data-ttu-id="a774c-143">管理 Reporting Services SharePoint 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-143">Manage a Reporting Services SharePoint Service Application</span></span>](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|<span data-ttu-id="a774c-144">备份和还原服务应用程序及相关的组件，如加密密钥和代理。</span><span class="sxs-lookup"><span data-stu-id="a774c-144">Backup and restore the service application and related components such as encryption keys and proxy.</span></span>|[<span data-ttu-id="a774c-145">备份和还原 Reporting Services SharePoint 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a774c-145">Backup and Restore Reporting Services SharePoint Service Applications</span></span>](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
