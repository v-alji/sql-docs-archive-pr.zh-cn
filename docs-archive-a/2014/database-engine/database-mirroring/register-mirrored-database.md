---
title: 注册镜像数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 24732f82c971959ed202358613ef98c5ccc714d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690116"
---
# <a name="register-mirrored-database"></a><span data-ttu-id="d5f01-102">注册镜像数据库</span><span class="sxs-lookup"><span data-stu-id="d5f01-102">Register Mirrored Database</span></span>
  <span data-ttu-id="d5f01-103">使用此对话框，通过向数据库镜像监视器添加一个或多个数据库，可在给定的服务器实例中注册一个或多个镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="d5f01-103">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="d5f01-104">添加数据库时，数据库镜像监视器会在本地缓存有关数据库及其伙伴的信息，以及如何将数据库连接到伙伴的信息。</span><span class="sxs-lookup"><span data-stu-id="d5f01-104">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d5f01-105">如果是主体服务器实例而不是镜像服务器实例上的 **sysadmin** 固定服务器角色的成员，那么只能查看主体服务器实例上的状态。</span><span class="sxs-lookup"><span data-stu-id="d5f01-105">If you are a member of the **sysadmin** fixed server role on the principal server instance but not on the mirror server instance, you can only see status on the principal server instance.</span></span>  
  
 <span data-ttu-id="d5f01-106">**使用 SQL Server Management Studio 监视数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="d5f01-106">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="d5f01-107">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d5f01-107">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="d5f01-108">选项</span><span class="sxs-lookup"><span data-stu-id="d5f01-108">Options</span></span>  
 <span data-ttu-id="d5f01-109">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="d5f01-109">**Server instance**</span></span>  
 <span data-ttu-id="d5f01-110">从列表中选择一个服务器实例（数据库镜像监视器已为该列表包含的服务器实例存储了一个连接），或单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="d5f01-110">Select a server instance from the list, which contains server instances to which Database Mirroring Monitor already has a connection stored, or click **Connect**.</span></span> <span data-ttu-id="d5f01-111">若要为列出的服务器实例指定新凭据，请单击 **“连接”** 并使用新凭据进行连接。</span><span class="sxs-lookup"><span data-stu-id="d5f01-111">To specify new credentials for a listed server instance, click **Connect** and connect using the new credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5f01-112">若要在多个服务器实例上注册数据库，请在针对某一服务器实例完成所需数据库的检查之后，单击“应用”，然后再选择另一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d5f01-112">To register databases on multiple server instances, after you finish checking the desired databases for one server instance, click **Apply**, and then select another server instance.</span></span>  
  
 <span data-ttu-id="d5f01-113">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="d5f01-113">**Connect**</span></span>  
 <span data-ttu-id="d5f01-114">若要为服务器实例指定新凭据，请单击“连接”并使用新凭据进行连接。</span><span class="sxs-lookup"><span data-stu-id="d5f01-114">To specify new credentials for the server instance, click **Connect** and connect using the new credentials.</span></span> <span data-ttu-id="d5f01-115">当连接到服务器实例时，数据库镜像监视器显示 **“等待数据”** 。</span><span class="sxs-lookup"><span data-stu-id="d5f01-115">While connecting to a server instance, Database Mirroring Monitor displays **Waiting for data**.</span></span>  
  
 <span data-ttu-id="d5f01-116">**镜像数据库**</span><span class="sxs-lookup"><span data-stu-id="d5f01-116">**Mirrored databases**</span></span>  
 <span data-ttu-id="d5f01-117">“镜像数据库”网格可列出服务器实例中的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="d5f01-117">The **Mirrored databases** grid lists the mirrored databases on the server instance.</span></span>  
  
 <span data-ttu-id="d5f01-118">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="d5f01-118">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="d5f01-119">列名称</span><span class="sxs-lookup"><span data-stu-id="d5f01-119">Column name</span></span>|<span data-ttu-id="d5f01-120">说明</span><span class="sxs-lookup"><span data-stu-id="d5f01-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d5f01-121">**注册**</span><span class="sxs-lookup"><span data-stu-id="d5f01-121">**Register**</span></span>|<span data-ttu-id="d5f01-122">检查您要注册的每个数据库。</span><span class="sxs-lookup"><span data-stu-id="d5f01-122">Check each of the databases that you want to register.</span></span> <span data-ttu-id="d5f01-123">如果正在监视数据库，则该数据库的复选框会被选中且禁用。</span><span class="sxs-lookup"><span data-stu-id="d5f01-123">If a database is currently monitored, its check box is checked and is disabled.</span></span><br /><br /> <span data-ttu-id="d5f01-124">注意：若要撤消注册某一数据库，请关闭“已注册镜像数据库”对话框，在导航树中选择该数据库，并从“操作”菜单中选择“撤消注册”  。</span><span class="sxs-lookup"><span data-stu-id="d5f01-124">Note: To unregister a database, close the **Registered Mirrored Database** dialog box, select the database in the navigation tree, and select **Unregister** from the **Action** menu.</span></span>|  
|<span data-ttu-id="d5f01-125">**Database**</span><span class="sxs-lookup"><span data-stu-id="d5f01-125">**Database**</span></span>|<span data-ttu-id="d5f01-126">选定服务器实例上的镜像数据库名称。</span><span class="sxs-lookup"><span data-stu-id="d5f01-126">The name of a mirrored database on the selected server instance.</span></span>|  
|<span data-ttu-id="d5f01-127">**当前角色**</span><span class="sxs-lookup"><span data-stu-id="d5f01-127">**Current Role**</span></span>|<span data-ttu-id="d5f01-128">选定服务器实例上的数据库的当前镜像角色，即主体或镜像。</span><span class="sxs-lookup"><span data-stu-id="d5f01-128">The current mirroring role of the database, either Principal or Mirror, on the selected server instance.</span></span>|  
|<span data-ttu-id="d5f01-129">**伙伴(连接为)**</span><span class="sxs-lookup"><span data-stu-id="d5f01-129">**Partner (Connect as)**</span></span>|<span data-ttu-id="d5f01-130">数据库的故障转移伙伴的名称。</span><span class="sxs-lookup"><span data-stu-id="d5f01-130">The name of the failover partner for the database.</span></span> <span data-ttu-id="d5f01-131">括号中显示“控制台用户的 Windows 身份验证”或“登录名‘\<login name>’的 SQL Server 身份验证”。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d5f01-131">Either **Windows Authentication of console user** or **SQL Server Authentication of login '***\<login name>***'** is displayed within the parentheses.</span></span> <span data-ttu-id="d5f01-132">如果之前已添加实例，则此内容为当前使用的身份验证信息；如果尚未将实例添加到监视器中，则此内容为将要使用的身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="d5f01-132">This is the authentication information currently used, if the instance has been added before, or that will be used, if this instance has not been added to the monitor.</span></span>|  
  
 <span data-ttu-id="d5f01-133">**当单击“确定”后，显示“管理服务器连接”对话框。**</span><span class="sxs-lookup"><span data-stu-id="d5f01-133">**Show the Manage Server Connections dialog box when I click OK.**</span></span>  
 <span data-ttu-id="d5f01-134">在默认情况下，对于以前未给定凭据的伙伴服务器实例，数据库镜像监视器将使用 Windows 身份验证凭据。</span><span class="sxs-lookup"><span data-stu-id="d5f01-134">By default, Database Mirroring Monitor uses Windows Authentication credentials for partner server instances for which credentials have not been previously given.</span></span> <span data-ttu-id="d5f01-135">启用该选项，可在完成数据库注册后为一个或多个服务器实例更改凭据。</span><span class="sxs-lookup"><span data-stu-id="d5f01-135">Enable this option to change the credentials for one or more server instances when you finish registering databases.</span></span>  
  
 <span data-ttu-id="d5f01-136">如果启用该选项，则单击 **“确定”** 时将打开 **“管理服务器连接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="d5f01-136">If this option is enabled, when you click **OK**, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="d5f01-137">在此，您可以选择要指定凭据的服务器实例，以便监视器在连接到给定的故障转移伙伴时使用该凭据。</span><span class="sxs-lookup"><span data-stu-id="d5f01-137">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given failover partner.</span></span>  
  
 <span data-ttu-id="d5f01-138">若要编辑伙伴的凭据，请在 **“服务器实例”** 网格中找到对应条目，并在该行中单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="d5f01-138">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="d5f01-139">此时将为该服务器实例名称打开 **“连接到服务器”** 对话框，同时将凭据控制初始化为当前的缓存值。</span><span class="sxs-lookup"><span data-stu-id="d5f01-139">This opens the **Connect to Server** dialog box for that server instance name, with the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="d5f01-140">根据需要更改凭据，并单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="d5f01-140">Change the credentials as necessary and click **Connect**.</span></span> <span data-ttu-id="d5f01-141">如果凭据有足够的权限，则会以新凭据更新 **“连接方式”** 列。</span><span class="sxs-lookup"><span data-stu-id="d5f01-141">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>  
  
 <span data-ttu-id="d5f01-142">**应用**</span><span class="sxs-lookup"><span data-stu-id="d5f01-142">**Apply**</span></span>  
 <span data-ttu-id="d5f01-143">单击该按钮，在保存对话框打开的状态下注册选定的数据库（并为伙伴服务器实例保存凭据）。</span><span class="sxs-lookup"><span data-stu-id="d5f01-143">Click this button to register the selected databases (and save credentials for the partner server instances) while keeping the dialog box open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f01-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5f01-144">See Also</span></span>  
 <span data-ttu-id="d5f01-145">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="d5f01-145">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="d5f01-146">[监视数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d5f01-146">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="d5f01-147">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d5f01-147">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
