---
title: 复制管理对象概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- replication [SQL Server], RMO
- programming interfaces [SQL Server replication]
- replication [SQL Server], how-to topics
- RMO [SQL Server]
- Replication Management Objects
- programming [SQL Server replication], RMO
ms.assetid: 37476d50-fb47-49e3-9504-3b163ac381d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0dc41416e0fb585db376c6b72f28f7c30cfff052
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586618"
---
# <a name="replication-management-objects-concepts"></a><span data-ttu-id="05860-102">Replication Management Objects Concepts</span><span class="sxs-lookup"><span data-stu-id="05860-102">Replication Management Objects Concepts</span></span>
  <span data-ttu-id="05860-103">复制管理对象 (RMO) 是一个封装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制功能的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="05860-103">Replication Management Objects (RMO) is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05860-104">RMO 是由 <xref:Microsoft.SqlServer.Replication> 命名空间实现的。</span><span class="sxs-lookup"><span data-stu-id="05860-104">RMO is implemented by the <xref:Microsoft.SqlServer.Replication> namespace.</span></span>  
  
 <span data-ttu-id="05860-105">以下几节中的主题介绍如何使用 RMO 以编程方式控制复制任务：</span><span class="sxs-lookup"><span data-stu-id="05860-105">The topics in the following sections describe how you can use RMO to programmatically control replication tasks:</span></span>  
  
 [<span data-ttu-id="05860-106">配置分发</span><span class="sxs-lookup"><span data-stu-id="05860-106">Configure Distribution</span></span>](../configure-distribution.md)  
 <span data-ttu-id="05860-107">本节中的主题介绍如何使用 RMO 配置发布和分发。</span><span class="sxs-lookup"><span data-stu-id="05860-107">Topics in this section show how to use RMO to configure publishing and distribution.</span></span>  
  
 [<span data-ttu-id="05860-108">创建发布</span><span class="sxs-lookup"><span data-stu-id="05860-108">Create a Publication</span></span>](../publish/create-a-publication.md)  
 <span data-ttu-id="05860-109">本节中的主题介绍如何使用 RMO 创建、删除和修改发布和项目。</span><span class="sxs-lookup"><span data-stu-id="05860-109">Topics in this section show how to use RMO to create, delete, and modify publications and articles.</span></span>  
  
 [<span data-ttu-id="05860-110">订阅发布</span><span class="sxs-lookup"><span data-stu-id="05860-110">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
 <span data-ttu-id="05860-111">本节中的主题介绍如何使用 RMO 创建、删除和修改订阅。</span><span class="sxs-lookup"><span data-stu-id="05860-111">Topics in this section show how to use RMO to create, delete, and modify subscriptions.</span></span>  
  
 [<span data-ttu-id="05860-112">保护复制拓扑</span><span class="sxs-lookup"><span data-stu-id="05860-112">Secure a Replication Topology</span></span>](../security/view-and-modify-replication-security-settings.md)  
 <span data-ttu-id="05860-113">本节中的主题介绍如何使用 RMO 查看和修改安全设置。</span><span class="sxs-lookup"><span data-stu-id="05860-113">Topics in this section show how to use RMO to view and modify security settings.</span></span>  
  
 [<span data-ttu-id="05860-114">同步订阅（复制）</span><span class="sxs-lookup"><span data-stu-id="05860-114">Synchronize Subscriptions &#40;Replication&#41;</span></span>](../synchronize-data.md)  
 <span data-ttu-id="05860-115">本节中的主题介绍如何同步订阅。</span><span class="sxs-lookup"><span data-stu-id="05860-115">Topics in this section show how to synchronize subscriptions.</span></span>  
  
 [<span data-ttu-id="05860-116">监视复制</span><span class="sxs-lookup"><span data-stu-id="05860-116">Monitoring Replication</span></span>](../monitoring-replication.md)  
 <span data-ttu-id="05860-117">本节中的主题介绍如何以编程方式监视复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="05860-117">Topics in this section show how to programmatically monitor a replication topology.</span></span>  
  
## <a name="introduction-to-rmo-programming"></a><span data-ttu-id="05860-118">RMO 编程简介</span><span class="sxs-lookup"><span data-stu-id="05860-118">Introduction to RMO Programming</span></span>  
 <span data-ttu-id="05860-119">RMO 专用于对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制的各个方面进行编程。</span><span class="sxs-lookup"><span data-stu-id="05860-119">RMO is designed for programming all aspects of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="05860-120">RMO 的命名空间为 <xref:Microsoft.SqlServer.Replication>，它是由 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 程序集 Microsoft.SqlServer.Rmo.dll 实现的。</span><span class="sxs-lookup"><span data-stu-id="05860-120">The RMO namespace is <xref:Microsoft.SqlServer.Replication>, and it is implemented by the Microsoft.SqlServer.Rmo.dll, which is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="05860-121">Microsoft.SqlServer.Replication.dll 程序集也属于 <xref:Microsoft.SqlServer.Replication> 命名空间，该程序集实现了用于编程多种复制代理（快照代理、分发代理和合并代理）的托管代码接口。</span><span class="sxs-lookup"><span data-stu-id="05860-121">The Microsoft.SqlServer.Replication.dll assembly, which also belongs to the <xref:Microsoft.SqlServer.Replication> namespace, implements a managed code interface for programming the various replication agents (Snapshot Agent, Distribution Agent, and Merge Agent).</span></span> <span data-ttu-id="05860-122">该程序集的类可以从 RMO 访问以同步订阅。</span><span class="sxs-lookup"><span data-stu-id="05860-122">Its classes can be accessed from RMO to synchronize subscriptions.</span></span> <span data-ttu-id="05860-123"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空间中的类由 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll 程序集实现，这些类用于创建合并复制的自定义业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="05860-123">Classes in the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace, implemented by the Microsoft.SqlServer.Replication.BusinessLogicSupport.dll assembly, are used to create custom business logic for merge replication.</span></span> <span data-ttu-id="05860-124">此程序集独立于 RMO。</span><span class="sxs-lookup"><span data-stu-id="05860-124">This assembly is independent from RMO.</span></span>  
  
## <a name="deploying-applications-based-on-rmo"></a><span data-ttu-id="05860-125">部署基于 RMO 的应用程序</span><span class="sxs-lookup"><span data-stu-id="05860-125">Deploying Applications Based on RMO</span></span>  
 <span data-ttu-id="05860-126">RMO 依赖于复制组件和客户端连接组件，这些组件包含在除 SQL Server Compact 之外的所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中。</span><span class="sxs-lookup"><span data-stu-id="05860-126">RMO depends on the replication components and client connectivity components that are included with all versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] except SQL Server Compact.</span></span> <span data-ttu-id="05860-127">若要部署基于 RMO 的应用程序，必须在要运行该应用程序的计算机上安装包含复制组件和客户端连接组件的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="05860-127">To deploy an application based on RMO, you must install a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that includes replication components and client connectivity components on the computer on which the application will run.</span></span>  
  
## <a name="getting-started-with-rmo"></a><span data-ttu-id="05860-128">RMO 入门</span><span class="sxs-lookup"><span data-stu-id="05860-128">Getting Started with RMO</span></span>  
 <span data-ttu-id="05860-129">本节介绍如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 开始一个简单的 RMO 项目。</span><span class="sxs-lookup"><span data-stu-id="05860-129">This section describes how to start a simple RMO project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio.</span></span>  
  
#### <a name="to-create-a-new-microsoft-visual-c-project"></a><span data-ttu-id="05860-130">创建新的 Microsoft Visual C# 项目</span><span class="sxs-lookup"><span data-stu-id="05860-130">To create a new Microsoft Visual C# project</span></span>  
  
1.  <span data-ttu-id="05860-131">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="05860-131">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="05860-132">在“文件”菜单中，单击“新建项目”。  </span><span class="sxs-lookup"><span data-stu-id="05860-132">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="05860-133">将显示“新建项目”对话框  。</span><span class="sxs-lookup"><span data-stu-id="05860-133">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="05860-134">在“项目类型”对话框中，选择“Visual C# 项目”。  </span><span class="sxs-lookup"><span data-stu-id="05860-134">In the **Project Types** dialog box, select **Visual C# Projects**.</span></span> <span data-ttu-id="05860-135">在“模板”窗格中，选择“Windows 应用程序”。  </span><span class="sxs-lookup"><span data-stu-id="05860-135">In the **Templates** pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="05860-136">（可选）在“名称”中，键入新应用程序的名称。 </span><span class="sxs-lookup"><span data-stu-id="05860-136">(Optional) In **Name**, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="05860-137">单击“确定”加载 Visual C# Windows 模板。 </span><span class="sxs-lookup"><span data-stu-id="05860-137">Click **OK** to load the Visual C# Windows template.</span></span>  
  
6.  <span data-ttu-id="05860-138">在“项目”菜单中，选择“添加引用”项。  </span><span class="sxs-lookup"><span data-stu-id="05860-138">On the **Project** menu, select **Add Reference** item.</span></span> <span data-ttu-id="05860-139">此时将显示“添加引用”对话框。 </span><span class="sxs-lookup"><span data-stu-id="05860-139">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="05860-140">从“.NET”选项卡上的列表中选择以下程序集，然后单击“确定”。  </span><span class="sxs-lookup"><span data-stu-id="05860-140">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="05860-141">Microsoft.SqlServer.Replication .NET Programming Interface</span><span class="sxs-lookup"><span data-stu-id="05860-141">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="05860-142">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="05860-142">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="05860-143">Replication Agent Library</span><span class="sxs-lookup"><span data-stu-id="05860-143">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05860-144">使用 CTRL 键可选择多个文件。</span><span class="sxs-lookup"><span data-stu-id="05860-144">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="05860-145">（可选）重复步骤 6。</span><span class="sxs-lookup"><span data-stu-id="05860-145">(Optional) Repeat step 6.</span></span> <span data-ttu-id="05860-146">单击“浏览”选项卡，导航到 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM，选择“Microsoft.SqlServer.Replication.BusinessLogicSupport.dll”，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="05860-146">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="05860-147">在 **“视图”** 菜单上，单击 **“代码”** 。</span><span class="sxs-lookup"><span data-stu-id="05860-147">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="05860-148">在代码的命名空间语句前，键入以下 `using` 语句，以限定 RMO 命名空间中的类型：</span><span class="sxs-lookup"><span data-stu-id="05860-148">In the code, before the namespace statement, type the following `using` statements to qualify the types in the RMO namespaces:</span></span>  
  
    ```  
    // These namespaces are required.  
    using Microsoft.SqlServer.Replication;  
    using Microsoft.SqlServer.Management.Common;  
    // This namespace is only used when creating custom business  
    // logic for merge replication.  
    using Microsoft.SqlServer.Replication.BusinessLogicSupport;   
    ```  
  
#### <a name="to-create-a-new-microsoft-visual-basic-net-project"></a><span data-ttu-id="05860-149">创建新的 Microsoft Visual Basic .NET 项目</span><span class="sxs-lookup"><span data-stu-id="05860-149">To create a new Microsoft Visual Basic .NET project</span></span>  
  
1.  <span data-ttu-id="05860-150">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="05860-150">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="05860-151">在“文件”菜单中，选择“新建项目”。  </span><span class="sxs-lookup"><span data-stu-id="05860-151">On the **File** menu, select **New Project**.</span></span> <span data-ttu-id="05860-152">将显示“新建项目”对话框  。</span><span class="sxs-lookup"><span data-stu-id="05860-152">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="05860-153">在“项目类型”窗格中，选择“Visual Basic”。 </span><span class="sxs-lookup"><span data-stu-id="05860-153">In the Project Types pane, select **Visual Basic**.</span></span> <span data-ttu-id="05860-154">在“模板”窗格中，选择“Windows 应用程序”。 </span><span class="sxs-lookup"><span data-stu-id="05860-154">In the Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="05860-155">（可选）在“名称”框中，键入新应用程序的名称。 </span><span class="sxs-lookup"><span data-stu-id="05860-155">(Optional) In the **Name** box, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="05860-156">单击“确定”加载 Visual Basic Windows 模板。 </span><span class="sxs-lookup"><span data-stu-id="05860-156">Click **OK** to load the Visual Basic Windows template.</span></span>  
  
6.  <span data-ttu-id="05860-157">在“项目”菜单中，选择“添加引用”。  </span><span class="sxs-lookup"><span data-stu-id="05860-157">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="05860-158">此时将显示“添加引用”对话框。 </span><span class="sxs-lookup"><span data-stu-id="05860-158">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="05860-159">从“.NET”选项卡上的列表中选择以下程序集，然后单击“确定”。  </span><span class="sxs-lookup"><span data-stu-id="05860-159">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="05860-160">Microsoft.SqlServer.Replication .NET Programming Interface</span><span class="sxs-lookup"><span data-stu-id="05860-160">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="05860-161">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="05860-161">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="05860-162">Replication Agent Library</span><span class="sxs-lookup"><span data-stu-id="05860-162">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05860-163">使用 CTRL 键可选择多个文件。</span><span class="sxs-lookup"><span data-stu-id="05860-163">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="05860-164">（可选）重复步骤 6。</span><span class="sxs-lookup"><span data-stu-id="05860-164">(Optional) Repeat step 6.</span></span> <span data-ttu-id="05860-165">单击“浏览”选项卡，导航到 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM，选择“Microsoft.SqlServer.Replication.BusinessLogicSupport.dll”，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="05860-165">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="05860-166">在 **“视图”** 菜单上，单击 **“代码”** 。</span><span class="sxs-lookup"><span data-stu-id="05860-166">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="05860-167">在代码的任何声明前，键入以下 `Imports` 语句，以限定 RMO 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="05860-167">In the code, before any declarations, type the following `Imports` statements to qualify the types in the RMO namespaces.</span></span>  
  
    ```  
    ' These namespaces are required.  
    Imports Microsoft.SqlServer.Replication  
    Imports Microsoft.SqlServer.Management.Common  
    ' This namespace is only used when creating custom business  
    ' logic for merge replication.  
    Imports Microsoft.SqlServer.Replication.BusinessLogicSupport   
    ```  
  
## <a name="connecting-to-a-replication-server"></a><span data-ttu-id="05860-168">连接复制服务器</span><span class="sxs-lookup"><span data-stu-id="05860-168">Connecting to a Replication Server</span></span>  
 <span data-ttu-id="05860-169">RMO 编程对象要求使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类的实例连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="05860-169">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span> <span data-ttu-id="05860-170">与该服务器的连接是独立于任何 RMO 编程对象的。</span><span class="sxs-lookup"><span data-stu-id="05860-170">This connection to the server is made independently of any RMO programming objects.</span></span> <span data-ttu-id="05860-171">然后，在创建实例的过程中或在给 RMO 对象的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性赋值的过程中，该编程对象会传递给 RMO 对象。</span><span class="sxs-lookup"><span data-stu-id="05860-171">It is then passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="05860-172">采用这种方式，RMO 编程对象实例和连接对象实例可以分别创建和管理，而多个 RMO 编程对象可以重用一个连接对象。</span><span class="sxs-lookup"><span data-stu-id="05860-172">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="05860-173">连接复制服务器时适用下列规则：</span><span class="sxs-lookup"><span data-stu-id="05860-173">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="05860-174">该连接的所有属性都对给定的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象定义。</span><span class="sxs-lookup"><span data-stu-id="05860-174">All properties for the connection are defined for a given <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="05860-175">与每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的连接必须有自己的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="05860-175">A connection to each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="05860-176">将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象赋给正在创建的或正在服务器上访问的 RMO 编程对象的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="05860-176">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is assigned to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the RMO programming object being created or accessed on the server.</span></span>  
  
-   <span data-ttu-id="05860-177"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法打开与服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="05860-177">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method opens the connection to the server.</span></span> <span data-ttu-id="05860-178">必须在调用此方法后，才能对任何使用该连接的 RMO 编程对象调用任一访问服务器的方法。</span><span class="sxs-lookup"><span data-stu-id="05860-178">This method must be called before calling any methods that access the server on any RMO programming objects using the connection.</span></span>  
  
-   <span data-ttu-id="05860-179">由于 RMO 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 都使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类来连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，因此 RMO 和 SMO 对象可使用相同的连接。</span><span class="sxs-lookup"><span data-stu-id="05860-179">Because RMO and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) both use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the same connection can be used by both RMO and SMO objects.</span></span> <span data-ttu-id="05860-180">有关详细信息，请参阅[连接到 SQL Server 的实例](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="05860-180">For more information, see [Connecting to an Instance of SQL Server](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md).</span></span>  
  
-   <span data-ttu-id="05860-181">执行连接并成功登录服务器所需的所有验证信息由 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象提供。</span><span class="sxs-lookup"><span data-stu-id="05860-181">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="05860-182">默认情况下使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="05860-182">Windows Authentication is the default.</span></span> <span data-ttu-id="05860-183">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证，<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> 必须设置为 `false` 且 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> 和 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> 必须设置为有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="05860-183">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to `false` and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="05860-184">安全凭据必须始终以安全的方式存储和处理，并且尽可能在运行时才提供。</span><span class="sxs-lookup"><span data-stu-id="05860-184">Security credentials must always be stored and handled securely, and supplied at run-time whenever possible.</span></span>  
  
-   <span data-ttu-id="05860-185">对于多线程应用程序，每个线程应使用单独的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="05860-185">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
 <span data-ttu-id="05860-186">对 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 对象调用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 方法将关闭 RMO 对象所使用的活动的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="05860-186">Call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method on the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object to close active server connections used by RMO objects.</span></span>  
  
## <a name="setting-rmo-properties"></a><span data-ttu-id="05860-187">设置 RMO 属性</span><span class="sxs-lookup"><span data-stu-id="05860-187">Setting RMO Properties</span></span>  
 <span data-ttu-id="05860-188">RMO 编程对象的属性表示服务器上这些复制对象的属性。</span><span class="sxs-lookup"><span data-stu-id="05860-188">The properties of RMO programming objects represent the properties of these replication objects at the server.</span></span> <span data-ttu-id="05860-189">在服务器上创建新的复制对象时，RMO 属性用于定义这些对象。</span><span class="sxs-lookup"><span data-stu-id="05860-189">When creating new replication objects at the server, RMO properties are used to define these objects.</span></span> <span data-ttu-id="05860-190">对于现有对象，RMO 属性表示现有对象的属性，其中可修改的只有可写和可设置的属性。</span><span class="sxs-lookup"><span data-stu-id="05860-190">For existing objects, the RMO properties represent the existing object's properties, which can be modified only for properties that are writable or settable.</span></span> <span data-ttu-id="05860-191">对新对象或现有对象都可以设置属性。</span><span class="sxs-lookup"><span data-stu-id="05860-191">Properties can be set on new objects or existing objects.</span></span>  
  
### <a name="setting-properties-for-new-replication-objects"></a><span data-ttu-id="05860-192">为新复制对象设置属性</span><span class="sxs-lookup"><span data-stu-id="05860-192">Setting Properties for New Replication Objects</span></span>  
 <span data-ttu-id="05860-193">在服务器上创建新的复制对象时，必须指定所有必需的属性，然后才能调用该对象的 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="05860-193">When creating a new replication object at the server, you must specify all required properties before calling the `Create` method of the object.</span></span> <span data-ttu-id="05860-194">有关为新的复制对象设置属性的详细信息，请参阅[配置发布和分发](../configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="05860-194">For more information about setting properties for a new replication object, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
### <a name="setting-properties-for-existing-replication-objects"></a><span data-ttu-id="05860-195">为现有复制对象设置属性</span><span class="sxs-lookup"><span data-stu-id="05860-195">Setting Properties for Existing Replication Objects</span></span>  
 <span data-ttu-id="05860-196">对于服务器上存在的复制对象，RMO 可能只支持更改其属性的部分或全部，具体取决于对象。</span><span class="sxs-lookup"><span data-stu-id="05860-196">For replication objects that exist at the server, depending on the object, RMO might support the ability to change some or all of its properties.</span></span> <span data-ttu-id="05860-197">只有可写或可设置的属性才能更改。</span><span class="sxs-lookup"><span data-stu-id="05860-197">Only writable or settable properties can be changed.</span></span> <span data-ttu-id="05860-198">更改属性前，必须调用 `Load` 或 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法从服务器获取当前属性。</span><span class="sxs-lookup"><span data-stu-id="05860-198">Before properties can be changed, either the `Load` or the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method must be called to get the current properties from the server.</span></span> <span data-ttu-id="05860-199">调用这些方法表示要修改现有对象。</span><span class="sxs-lookup"><span data-stu-id="05860-199">Calling these methods indicates that an existing object is being modified.</span></span>  
  
 <span data-ttu-id="05860-200">默认情况下，更改对象属性时，RMO 会根据所使用的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 的执行模式向服务器提交这些更改。</span><span class="sxs-lookup"><span data-stu-id="05860-200">By default, when changing object properties, RMO commits these changes to the server based on the execution mode of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> being used.</span></span> <span data-ttu-id="05860-201">尝试检索或更改对象的属性之前，可以使用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 方法来验证服务器上是否存在该对象。</span><span class="sxs-lookup"><span data-stu-id="05860-201">The <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> method can be used to verify that an object exists at the server before attempting to retrieve or change its properties.</span></span> <span data-ttu-id="05860-202">有关更改复制对象属性的详细信息，请参阅[查看和修改分发服务器和发布服务器属性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="05860-202">For more information about changing the properties of a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05860-203">多个 RMO 客户端或一个 RMO 编程对象的多个实例同时访问服务器上的同一个复制对象时，可根据服务器上该对象的当前状态，调用 RMO 对象的 `Refresh` 方法来更新属性。</span><span class="sxs-lookup"><span data-stu-id="05860-203">When multiple RMO clients or multiple instances of an RMO programming object are accessing the same replication object at the server, the `Refresh` method of the RMO object can be called to update the properties based on the current state of the object at the server.</span></span>  
  
### <a name="caching-property-changes"></a><span data-ttu-id="05860-204">缓存属性更改</span><span class="sxs-lookup"><span data-stu-id="05860-204">Caching Property Changes</span></span>  
 <span data-ttu-id="05860-205"><xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 属性设置为 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> 时，RMO 生成的所有 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句都会被捕获，因此可使用执行方法之一在一个批次内手动执行这些语句。</span><span class="sxs-lookup"><span data-stu-id="05860-205">When the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> property is set to <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> all [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements generated by RMO are captured so that they can be executed manually in a single batch by using one of the execution methods.</span></span> <span data-ttu-id="05860-206">RMO 可以缓存属性更改并使用对象的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法在一个批次内将这些更改一起提交。</span><span class="sxs-lookup"><span data-stu-id="05860-206">RMO lets you cache property changes and commit them together in a single batch by using the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method of the object.</span></span> <span data-ttu-id="05860-207">若要缓存属性更改，对象的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 属性必须设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="05860-207">To cache property changes, the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property of the object must be set to `true`.</span></span> <span data-ttu-id="05860-208">缓存 RMO 中的属性更改时，<xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象仍控制何时向服务器发送更改。</span><span class="sxs-lookup"><span data-stu-id="05860-208">When caching property changes in RMO, the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object still controls when changes are sent to the server.</span></span> <span data-ttu-id="05860-209">有关缓存复制对象的属性更改的详细信息，请参阅[查看和修改分发服务器和发布服务器属性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="05860-209">For more information about caching property changes for a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05860-210">虽然 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类支持在设置属性时声明显式事务，但这样的事务会影响内部复制事务，可能产生难以预料的结果，因此不应在 RMO 中使用。</span><span class="sxs-lookup"><span data-stu-id="05860-210">Although the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class supports declaring explicit transactions when setting properties, such transactions may interfere with internal replication transactions, can produce unanticipated results, and should not be used with RMO.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05860-211">示例</span><span class="sxs-lookup"><span data-stu-id="05860-211">Example</span></span>  
 <span data-ttu-id="05860-212">本示例演示如何缓存属性更改。</span><span class="sxs-lookup"><span data-stu-id="05860-212">This example demonstrates the caching of property changes.</span></span> <span data-ttu-id="05860-213">对事务发布属性的更改被缓存，直到将其显式发送给服务器。</span><span class="sxs-lookup"><span data-stu-id="05860-213">Changes made to the attributes of a transactional publication are cached until they are explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_ChangeTranPub_cached)]  
  
## <a name="see-also"></a><span data-ttu-id="05860-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05860-214">See Also</span></span>  
 <span data-ttu-id="05860-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="05860-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="05860-216">复制编程概念</span><span class="sxs-lookup"><span data-stu-id="05860-216">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
  
  
