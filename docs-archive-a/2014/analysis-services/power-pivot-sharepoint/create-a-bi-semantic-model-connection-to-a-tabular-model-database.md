---
title: 创建与表格模型数据库的 BI 语义模型连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69b306f6-ee8a-44d2-8f51-0cad2c0bc135
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b4281050b8672891fc01e8bbeb4b3bc1920c94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589274"
---
# <a name="create-a-bi-semantic-model-connection-to-a-tabular-model-database"></a><span data-ttu-id="43a1f-102">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="43a1f-102">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>
  <span data-ttu-id="43a1f-103">使用本主题中的信息设置一个 BI 语义模型连接，该连接将重定向到在 SharePoint 场外的 Analysis Services 实例上运行的表格模型数据库。</span><span class="sxs-lookup"><span data-stu-id="43a1f-103">Use the information in this topic to set up a BI semantic model connection that redirects to a tabular model database running on an Analysis Services instance outside the SharePoint farm.</span></span>  
  
 <span data-ttu-id="43a1f-104">在创建 BI 语义模型连接并配置 SharePoint Services 和 Analysis Services 权限后，可将其用作 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报告的数据源。</span><span class="sxs-lookup"><span data-stu-id="43a1f-104">After you create a BI semantic model connection and configure SharePoint and Analysis Services permissions, people can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="43a1f-105">本主题包含以下各节。</span><span class="sxs-lookup"><span data-stu-id="43a1f-105">This topic includes the following sections.</span></span> <span data-ttu-id="43a1f-106">按给出的顺序执行每个任务。</span><span class="sxs-lookup"><span data-stu-id="43a1f-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="43a1f-107">检查必备条件</span><span class="sxs-lookup"><span data-stu-id="43a1f-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="43a1f-108">授予对共享服务应用程序的 Analysis Services 管理权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-108">Grant Analysis Services Administrative Permissions to Shared Service Applications</span></span>](#bkmk_ssas)  
  
 [<span data-ttu-id="43a1f-109">授予对表格模型数据库的读取权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-109">Grant Read Permissions on the Tabular Model Database</span></span>](#bkmk_BISM)  
  
 [<span data-ttu-id="43a1f-110">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="43a1f-110">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](#bkmk_connect)  
  
 [<span data-ttu-id="43a1f-111">配置 BI 语义模型连接的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-111">Configure SharePoint permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="43a1f-112">后续步骤</span><span class="sxs-lookup"><span data-stu-id="43a1f-112">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="43a1f-113">查看先决条件</span><span class="sxs-lookup"><span data-stu-id="43a1f-113">Review Prerequisites</span></span>  
 <span data-ttu-id="43a1f-114">您必须具有“参与讨论”权限或更高权限以创建 BI 语义模型连接文件。</span><span class="sxs-lookup"><span data-stu-id="43a1f-114">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="43a1f-115">您必须具有支持 BI 语义模型连接内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="43a1f-115">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="43a1f-116">有关详细信息，请参阅[将 BI 语义模型连接内容类型添加到库 &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)。</span><span class="sxs-lookup"><span data-stu-id="43a1f-116">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="43a1f-117">您必须知道将为其设置 BI 语义模型连接的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="43a1f-117">You must know the server and database name for which you are setting up a BI semantic model connection.</span></span> <span data-ttu-id="43a1f-118">必须为表格模式配置 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="43a1f-118">Analysis Services must be configured for tabular mode.</span></span> <span data-ttu-id="43a1f-119">服务器上运行的数据库必须是表格模型数据库。</span><span class="sxs-lookup"><span data-stu-id="43a1f-119">Databases running on the server must be tabular model databases.</span></span> <span data-ttu-id="43a1f-120">有关如何检查服务器模式的说明，请参阅 [确定 Analysis Services 实例的服务器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="43a1f-120">For instructions on how to check for server mode, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="43a1f-121">在某些情况下，SharePoint 环境下的共享服务必须对 Analysis Services 实例具有管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-121">In certain scenarios, the shared services in a SharePoint environment must have administrative permissions on the Analysis Services instance.</span></span> <span data-ttu-id="43a1f-122">这些服务包括 PowerPivot 服务应用程序、Reporting Services 服务应用程序和 PerformancePoint 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="43a1f-122">These services include PowerPivot service applications, Reporting Services service applications, and PerformancePoint service applications.</span></span> <span data-ttu-id="43a1f-123">您必须首先知道这些服务应用程序的标识，然后才能授予管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-123">Before you can grant administrative permissions, you must know the identity of these service applications.</span></span> <span data-ttu-id="43a1f-124">您可以使用管理中心来确定标识。</span><span class="sxs-lookup"><span data-stu-id="43a1f-124">You can use Central Administration to determine the identity.</span></span>  
  
 <span data-ttu-id="43a1f-125">您必须是 SharePoint 服务管理员才能查看管理中心内的安全信息。</span><span class="sxs-lookup"><span data-stu-id="43a1f-125">You must be a SharePoint service administrator to view security information in Central Administration.</span></span>  
  
 <span data-ttu-id="43a1f-126">您必须是 Analysis Services 系统管理员才能授予 Management Studio 中的管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-126">You must be an Analysis Services system administrator to grant administrative rights in Management Studio.</span></span>  
  
 <span data-ttu-id="43a1f-127">必须通过使用经典身份验证模式的 Web 应用程序访问 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="43a1f-127">PowerPivot for SharePoint must be accessed via web applications that use classic authentication mode.</span></span> <span data-ttu-id="43a1f-128">外部数据源的 BI 语义模型连接依赖于经典模式登录。</span><span class="sxs-lookup"><span data-stu-id="43a1f-128">BI semantic model connections to external data sources have a dependency on classic mode sign-in.</span></span> <span data-ttu-id="43a1f-129">有关详细信息，请参阅[PowerPivot 身份验证和授权](power-pivot-authentication-and-authorization.md)。</span><span class="sxs-lookup"><span data-stu-id="43a1f-129">For more information, see [PowerPivot Authentication and Authorization](power-pivot-authentication-and-authorization.md).</span></span>  
  
 <span data-ttu-id="43a1f-130">参与连接序列的所有计算机和用户都必须处于同一个域或可信域（双向信任）中。</span><span class="sxs-lookup"><span data-stu-id="43a1f-130">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="grant-analysis-services-administrative-permissions-to-shared-service-applications"></a><a name="bkmk_ssas"></a><span data-ttu-id="43a1f-131">授予对共享服务应用程序的 Analysis Services 管理权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-131">Grant Analysis Services Administrative Permissions to Shared Service Applications</span></span>  
 <span data-ttu-id="43a1f-132">SharePoint 与 Analysis Services 服务器上的表格模型数据库之间的连接有时候是由共享服务代表请求数据的用户建立的。</span><span class="sxs-lookup"><span data-stu-id="43a1f-132">Connections that originate from SharePoint to a tabular model database on an Analysis Services server are sometimes made by a shared service on behalf of the user requesting the data.</span></span> <span data-ttu-id="43a1f-133">发出请求的服务可以是 PowerPivot 服务应用程序、Reporting Services 服务应用程序或 PerformancePoint 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="43a1f-133">The service making the request might be a PowerPivot service application, a Reporting Services service application, or a PerformancePoint service application.</span></span> <span data-ttu-id="43a1f-134">为了能成功连接，该服务必须拥有 Analysis Services 服务器的管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-134">In order for the connection to succeed, the service must have administrative permissions on the Analysis Services server.</span></span> <span data-ttu-id="43a1f-135">在 Analysis Services 中，仅管理员能够代表其他用户建立模拟连接。</span><span class="sxs-lookup"><span data-stu-id="43a1f-135">In Analysis Services, only an administrator is allowed to make an impersonated connection on behalf of another user.</span></span>  
  
 <span data-ttu-id="43a1f-136">在以下条件下使用连接时需要管理权限：</span><span class="sxs-lookup"><span data-stu-id="43a1f-136">Administrative permissions are necessary when the connection is used under these conditions:</span></span>  
  
-   <span data-ttu-id="43a1f-137">在配置 BI 语义模型连接文件的过程中验证连接信息时。</span><span class="sxs-lookup"><span data-stu-id="43a1f-137">When verifying the connection information during the configuration of a BI semantic model connection file.</span></span>  
  
-   <span data-ttu-id="43a1f-138">在使用 BI 语义模型连接启动 Power View 报表时。</span><span class="sxs-lookup"><span data-stu-id="43a1f-138">When starting a Power View report using a BI semantic model connection.</span></span>  
  
-   <span data-ttu-id="43a1f-139">在使用 BI 语义模型连接填充 PerformancePoint Web 部件时。</span><span class="sxs-lookup"><span data-stu-id="43a1f-139">When populating a PerformancePoint web part using a BI semantic model connection.</span></span>  
  
 <span data-ttu-id="43a1f-140">为了确保这些行为按预期执行，请在 Analysis Services 实例上向各服务标识授予管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-140">To ensure these behaviors perform as expected, grant to each service identity administrative permissions on the Analysis Services instance.</span></span> <span data-ttu-id="43a1f-141">使用以下说明授予所需权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-141">Use the following instructions to grant the necessary permission.</span></span>  
  
 <span data-ttu-id="43a1f-142">**将服务标识添加到服务器管理员角色**</span><span class="sxs-lookup"><span data-stu-id="43a1f-142">**Add service identities to the Server Administrator role**</span></span>  
  
1.  <span data-ttu-id="43a1f-143">在 SQL Server Management Studio 中，连接到 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="43a1f-143">In SQL Server Management Studio, connect to the Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="43a1f-144">右键单击服务器名称并选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43a1f-144">Right-click the server name and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="43a1f-145">单击 **“安全性”**，然后单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-145">Click **Security**, and then click **Add**.</span></span> <span data-ttu-id="43a1f-146">输入用于运行服务应用程序的 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="43a1f-146">Enter the Windows user account that is used to run the service application.</span></span>  
  
     <span data-ttu-id="43a1f-147">您可以使用管理中心来确定标识。</span><span class="sxs-lookup"><span data-stu-id="43a1f-147">You can use Central Administration to determine the identity.</span></span> <span data-ttu-id="43a1f-148">在“安全性”部分中，打开 **“配置服务帐户”** 可查看与用于各应用程序的服务应用程序池关联的 Windows 帐户，然后，按照本主题中提供的说明执行，以便向帐户授予管理权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-148">In the Security section, open the **Configure service accounts** to view which Windows account is associated with the service application pool used for each application, then follow the instructions provided in this topic to grant the account administrative permissions.</span></span>  
  
##  <a name="grant-read-permissions-on-the-tabular-model-database"></a><a name="bkmk_BISM"></a> <span data-ttu-id="43a1f-149">授予对表格模型数据库的读取权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-149">Grant Read Permissions on the Tabular Model Database</span></span>  
 <span data-ttu-id="43a1f-150">由于数据库在服务器场外部的服务器上运行，因此设置您的连接的部分工作是授予后端 Analysis Services 服务器的数据库用户权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-150">Because the database is running on a server that is external to the farm, part of setting up your connections will include granting database user permissions on the backend Analysis Services server.</span></span> <span data-ttu-id="43a1f-151">Analysis Services 使用基于角色的权限模型。</span><span class="sxs-lookup"><span data-stu-id="43a1f-151">Analysis Services uses a role-based permission model.</span></span> <span data-ttu-id="43a1f-152">连接到模型数据库的用户必须具有读取权限或更高权限并且通过对其成员授予读取读取访问权限的角色才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="43a1f-152">Users who connect to model databases must do so with Read permissions or higher, through a role that grants read access to its members.</span></span>  
  
 <span data-ttu-id="43a1f-153">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中创建模型时会定义角色（有时会定义角色成员身份）。</span><span class="sxs-lookup"><span data-stu-id="43a1f-153">Roles, and sometimes role membership, are defined when the model is created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="43a1f-154">虽然无法使用 SQL Server Management Studio 创建角色，但可以使用它向已定义的角色中添加成员。</span><span class="sxs-lookup"><span data-stu-id="43a1f-154">You cannot use SQL Server Management Studio to create roles, but you can use it to add members to a role that is already defined.</span></span> <span data-ttu-id="43a1f-155">有关创建角色的详细信息，请参阅[创建和管理角色（SSAS 表格）](../tabular-models/roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="43a1f-155">For more information about creating roles, see [Create and Manage Roles &#40;SSAS Tabular&#41;](../tabular-models/roles-ssas-tabular.md).</span></span>  
  
#### <a name="assign-role-membership"></a><span data-ttu-id="43a1f-156">分配角色成员身份</span><span class="sxs-lookup"><span data-stu-id="43a1f-156">Assign role membership</span></span>  
  
1.  <span data-ttu-id="43a1f-157">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例，再在对象资源管理器中展开数据库，然后展开 **“角色”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-157">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand the database in Object Explorer, and then expand **Roles**.</span></span> <span data-ttu-id="43a1f-158">您应看到已定义的角色。</span><span class="sxs-lookup"><span data-stu-id="43a1f-158">You should see a role that is already defined.</span></span> <span data-ttu-id="43a1f-159">如果角色不存在，请与模型作者联系并请求添加或角色。</span><span class="sxs-lookup"><span data-stu-id="43a1f-159">If a role does not exist, contact the author of the model and request the addition or a role.</span></span> <span data-ttu-id="43a1f-160">必须先重新部署模型，然后角色才会显示在 Management Studio 中。</span><span class="sxs-lookup"><span data-stu-id="43a1f-160">The model must be redeployed before the role is visible in Management Studio.</span></span>  
  
2.  <span data-ttu-id="43a1f-161">右键单击该角色，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="43a1f-161">Right-click the role, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="43a1f-162">在“成员身份”页中，添加要求访问权限的 Windows 组和用户帐户。</span><span class="sxs-lookup"><span data-stu-id="43a1f-162">In the Membership page, add the Windows group and user accounts that require access.</span></span>  
  
##  <a name="create-a-bi-semantic-model-connection-to-a-tabular-model-database"></a><a name="bkmk_connect"></a><span data-ttu-id="43a1f-163">创建与表格模型数据库的 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="43a1f-163">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>  
 <span data-ttu-id="43a1f-164">在 Analysis Services 中设置权限后，您可以返回到 SharePoint 并创建 BI 语义模型连接。</span><span class="sxs-lookup"><span data-stu-id="43a1f-164">After you set permissions in Analysis Services, you can return to SharePoint and create a BI semantic model connection.</span></span>  
  
1.  <span data-ttu-id="43a1f-165">在将包含 BI 语义模型连接的库中，单击 SharePoint 功能区上的 **“文档”** 。</span><span class="sxs-lookup"><span data-stu-id="43a1f-165">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="43a1f-166">单击“新建文档”上的向下箭头，然后选择 **“BI 语义模型连接文件”** 以打开“新建 BI 语义模型连接”页。</span><span class="sxs-lookup"><span data-stu-id="43a1f-166">Click the down arrow on New Document, and select **BI Semantic Model Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
3.  <span data-ttu-id="43a1f-167">设置 **“服务器”** 和 **“数据库”** 属性。</span><span class="sxs-lookup"><span data-stu-id="43a1f-167">Set both **Server** and **Database** properties.</span></span> <span data-ttu-id="43a1f-168">如果您不确定数据库名称，则使用 SQL Server Management Studio 可以查看在服务器上部署的数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="43a1f-168">If you are unsure of the database name, use SQL Server Management Studio to view a list of the databases that are deployed on the server.</span></span>  
  
     <span data-ttu-id="43a1f-169">“服务器名称”\*\*\*\* 为服务器的网络名称、IP 地址或完全限定域名（例如，myserver.mydomain.corp.adventure-works.com）。</span><span class="sxs-lookup"><span data-stu-id="43a1f-169">**Server name** is either the network name of the server, the IP address, or the fully qualified domain name (for example, myserver.mydomain.corp.adventure-works.com).</span></span> <span data-ttu-id="43a1f-170">如果服务器作为命名实例安装，则以 computername\instancename 格式输入服务器名称。</span><span class="sxs-lookup"><span data-stu-id="43a1f-170">If the server is installed as a named instance, enter the server name in this format: computername\instancename.</span></span>  
  
     <span data-ttu-id="43a1f-171">**数据库** 必须为服务器上当前可用的表格数据库。</span><span class="sxs-lookup"><span data-stu-id="43a1f-171">**Database** must be a tabular database that is currently available on the server.</span></span> <span data-ttu-id="43a1f-172">不要指定其他 BI 语义模型连接文件、Office 数据连接 (.odc) 文件、Analysis Services OLAP 数据库或 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="43a1f-172">Do not specify another BI semantic model connection file, an Office Data Connection (.odc) file, an Analysis Services OLAP database, or a PowerPivot workbook.</span></span> <span data-ttu-id="43a1f-173">若要获取数据库名称，您可以使用 Management Studio 连接到服务器并查看可用数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="43a1f-173">To get the database name, you can use Management Studio to connect to the server and view the list of available databases.</span></span> <span data-ttu-id="43a1f-174">使用数据库的属性页以确保您拥有正确的名称。</span><span class="sxs-lookup"><span data-stu-id="43a1f-174">Use the property page of the database to ensure you have the correct name.</span></span>  
  
4.  <span data-ttu-id="43a1f-175">单击 **“确定”** 保存该页。</span><span class="sxs-lookup"><span data-stu-id="43a1f-175">Click **OK** to save the page.</span></span> <span data-ttu-id="43a1f-176">此时，PowerPivot 服务应用程序将验证连接。</span><span class="sxs-lookup"><span data-stu-id="43a1f-176">At this point, the PowerPivot service application will verify the connection.</span></span>  
  
     <span data-ttu-id="43a1f-177">如果连接信息正确，并且您向 PowerPivot 服务应用程序授予了管理权限，以便它可以作为当前用户连接到 Analysis Services，验证将成功。</span><span class="sxs-lookup"><span data-stu-id="43a1f-177">Verification succeeds if the connection information is correct, and you have granted administrative permissions to the PowerPivot service application so that it can connect to Analysis Services as the current user.</span></span>  
  
     <span data-ttu-id="43a1f-178">如果连接信息错误或服务应用程序缺少权限，验证将失败。</span><span class="sxs-lookup"><span data-stu-id="43a1f-178">Verification fails if the connection information is wrong, or the service application lacks permissions.</span></span> <span data-ttu-id="43a1f-179">验证消息将在页面上出现，询问您是否要保存该文件。</span><span class="sxs-lookup"><span data-stu-id="43a1f-179">A validation message will appear on the page asking whether you want to save the file.</span></span> <span data-ttu-id="43a1f-180">如果您知道连接有效，则应保存该文件，因为错误是由于缺少权限导致的，而非连接信息无效。</span><span class="sxs-lookup"><span data-stu-id="43a1f-180">If you know that the connection is valid, you should save the file anyway, because the error is the result of missing permissions rather than invalid connection information.</span></span>  
  
     <span data-ttu-id="43a1f-181">您可以通过在 Excel 或 Power View 中使用该连接来连接到表格模型数据库，对连接进行验证。</span><span class="sxs-lookup"><span data-stu-id="43a1f-181">You can verify the connection by using it in Excel or Power View to connect to tabular model database.</span></span> <span data-ttu-id="43a1f-182">如果数据源连接成功，则连接是有效的，尽管出现验证警告。</span><span class="sxs-lookup"><span data-stu-id="43a1f-182">If the data source connection succeeds, the connection is valid despite the verification warning.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="43a1f-183">配置针对 BI 语义模型连接的 SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="43a1f-183">Configure SharePoint permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="43a1f-184">为了能够使用 BI 语义模型连接作为 Excel 工作簿或 Reporting Services 报表的数据源，需要针对 SharePoint 库中 BI 语义模型连接项的 **“读取”** 权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-184">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="43a1f-185">该“读取”权限级别包括 **“打开项”** 权限，该权限支持将 BI 语义模型连接信息下载到 Excel 桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="43a1f-185">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="43a1f-186">有几种方法可在 SharePoint 中授予权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-186">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="43a1f-187">下面的说明解释如何新建一个名为 **BISM Users** 的具有“读取” \*\*\*\* 权限级别的组。</span><span class="sxs-lookup"><span data-stu-id="43a1f-187">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="43a1f-188">您必须是网站所有者才能更改权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-188">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="43a1f-189">在“网站操作”中，单击 **“网站权限”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-189">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="43a1f-190">单击“创建组” \*\*\*\* 并将新组命名为 **BISM Users**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-190">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="43a1f-191">选择 **“读取”** 权限级别，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-191">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="43a1f-192">在“人员和组”中选择 **BISM Users** 。</span><span class="sxs-lookup"><span data-stu-id="43a1f-192">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="43a1f-193">指向“新建”，单击 **“添加用户”**，然后添加用户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="43a1f-193">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="43a1f-194">此时，这些用户和组将拥有对整个网站的“读取”权限，包括从网站级别继承权限的所有库和列表。</span><span class="sxs-lookup"><span data-stu-id="43a1f-194">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="43a1f-195">如果这些权限太高，则可以选择从特定的库、列表或项中删除此组。</span><span class="sxs-lookup"><span data-stu-id="43a1f-195">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="43a1f-196">若要选择性地删除项目级别的权限，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="43a1f-196">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="43a1f-197">在库中选择一个文档。</span><span class="sxs-lookup"><span data-stu-id="43a1f-197">In a library, select a document.</span></span> <span data-ttu-id="43a1f-198">单击右下箭头，然后单击 **“管理权限”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-198">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="43a1f-199">默认情况下，项会继承权限。</span><span class="sxs-lookup"><span data-stu-id="43a1f-199">By default, an item inherits permissions.</span></span> <span data-ttu-id="43a1f-200">若要更改此库中的单个文档的权限，请单击 **“停止继承权限”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-200">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="43a1f-201">选中 \*\*\*\*“BISM 用户”旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="43a1f-201">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="43a1f-202">单击 **“删除用户权限”**。</span><span class="sxs-lookup"><span data-stu-id="43a1f-202">Click **Remove User Permissions**.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a><span data-ttu-id="43a1f-203">后续步骤</span><span class="sxs-lookup"><span data-stu-id="43a1f-203">Next Steps</span></span>  
 <span data-ttu-id="43a1f-204">创建了 BI 语义模型连接并且确保其安全后，可以将该连接指定为数据源。</span><span class="sxs-lookup"><span data-stu-id="43a1f-204">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="43a1f-205">有关详细信息，请参阅 [在 Excel 或 Reporting Services 中使用 BI 语义模型连接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43a1f-205">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a1f-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43a1f-206">See Also</span></span>  
 <span data-ttu-id="43a1f-207">[PowerPivot BI 语义模型连接 &#40; bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="43a1f-207">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="43a1f-208">创建与 PowerPivot 工作簿的 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="43a1f-208">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
  
