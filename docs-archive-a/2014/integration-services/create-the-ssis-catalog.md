---
title: 创建 SSIS 目录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2572cc131f34a21171054a159e3b7968c453a780
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578977"
---
# <a name="create-the-ssis-catalog"></a><span data-ttu-id="723f1-102">创建 SSIS 目录</span><span class="sxs-lookup"><span data-stu-id="723f1-102">Create the SSIS Catalog</span></span>
  <span data-ttu-id="723f1-103">当您在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中设计和测试包后，可将包含包的项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="723f1-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="723f1-104">在您可以将项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器之前，该服务器必须包含 `SSISDB` 目录。</span><span class="sxs-lookup"><span data-stu-id="723f1-104">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the server must contain the `SSISDB` catalog.</span></span> <span data-ttu-id="723f1-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 的安装程序并不会自动创建目录；您需要使用以下说明手动创建目录。</span><span class="sxs-lookup"><span data-stu-id="723f1-105">The installation program for [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] does not automatically create the catalog; you need to manually create the catalog by using the following instructions.</span></span>  
  
 <span data-ttu-id="723f1-106">您可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中创建 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="723f1-106">You can create the SSISDB catalog in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="723f1-107">还可以使用 Windows PowerShell 以编程方式创建目录。</span><span class="sxs-lookup"><span data-stu-id="723f1-107">You also create the catalog programmatically by using Windows PowerShell.</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a><span data-ttu-id="723f1-108">在 SQL Server Management Studio 中创建 SSISDB</span><span class="sxs-lookup"><span data-stu-id="723f1-108">To create the SSISDB catalog in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="723f1-109">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="723f1-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="723f1-110">连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="723f1-110">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Database Engine.</span></span>  
  
3.  <span data-ttu-id="723f1-111">在“对象资源管理器”中，展开服务器节点，右键单击“Integration Services 目录”  节点，然后单击“创建目录” 。</span><span class="sxs-lookup"><span data-stu-id="723f1-111">In Object Explorer, expand the server node, right-click the **Integration Services Catalogs** node, and then click **Create Catalog**.</span></span>  
  
4.  <span data-ttu-id="723f1-112">单击 **“启用 CLR 集成”** 。</span><span class="sxs-lookup"><span data-stu-id="723f1-112">Click **Enable CLR Integration**.</span></span>  
  
     <span data-ttu-id="723f1-113">该目录使用 CLR 存储过程。</span><span class="sxs-lookup"><span data-stu-id="723f1-113">The catalog uses CLR stored procedures.</span></span>  
  
5.  <span data-ttu-id="723f1-114">单击“在 SQL Server 启动时启用自动执行 Integration Services 存储过程”，使 [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) 存储过程在每次重启 [!INCLUDE[ssIS](../includes/ssis-md.md)] 服务器后运行。</span><span class="sxs-lookup"><span data-stu-id="723f1-114">Click **Enable automatic execution of Integration Services stored procedure at SQL Server startup** to enable the [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) stored procedure to run each time the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance is restarted.</span></span>  
  
     <span data-ttu-id="723f1-115">该存储过程对 SSISDB 目录的操作状态进行维护。</span><span class="sxs-lookup"><span data-stu-id="723f1-115">The stored procedure performs maintenance of the state of operations for the SSISDB catalog.</span></span> <span data-ttu-id="723f1-116">它可以纠正当 [!INCLUDE[ssIS](../includes/ssis-md.md)] 服务器实例出现故障时正在运行的任何包的状态。</span><span class="sxs-lookup"><span data-stu-id="723f1-116">It fixes the status of any packages there were running if and when the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance goes down.</span></span>  
  
6.  <span data-ttu-id="723f1-117">输入密码，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="723f1-117">Enter a password, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="723f1-118">该密码保护用于对目录数据进行加密的数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="723f1-118">The password protects the database master key that is used for encrypting the catalog data.</span></span> <span data-ttu-id="723f1-119">将该密码保存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="723f1-119">Save the password in a secure location.</span></span> <span data-ttu-id="723f1-120">同时建议您也备份数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="723f1-120">It is recommended that you also back up the database master key.</span></span> <span data-ttu-id="723f1-121">有关详细信息，请参阅 [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="723f1-121">For more information, see [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md).</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a><span data-ttu-id="723f1-122">以编程方式创建 SSISDB 目录</span><span class="sxs-lookup"><span data-stu-id="723f1-122">To create the SSISDB catalog programmatically</span></span>  
  
1.  <span data-ttu-id="723f1-123">执行以下 PowerShell 脚本：</span><span class="sxs-lookup"><span data-stu-id="723f1-123">Execute the following PowerShell script:</span></span>  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     <span data-ttu-id="723f1-124">有关如何使用 Windows PowerShell 和 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空间的更多示例，请参阅 blogs.msdn.com 上的博客文章 [SQL Server 2012 中的 SSIS 和 PowerShell](https://go.microsoft.com/fwlink/?LinkId=242539)。</span><span class="sxs-lookup"><span data-stu-id="723f1-124">For more examples of how to use Windows PowerShell and the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace, see the blog entry, [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), on blogs.msdn.com.</span></span> <span data-ttu-id="723f1-125">有关命名空间和代码示例的概述，请参阅 blogs.msdn.com 上的博客文章 [SSIS 目录托管对象模型一瞥](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)。</span><span class="sxs-lookup"><span data-stu-id="723f1-125">For an overview of the namespace and code examples, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723f1-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="723f1-126">See Also</span></span>  
 <span data-ttu-id="723f1-127">[SSIS 目录](catalog/ssis-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="723f1-127">[SSIS Catalog](catalog/ssis-catalog.md) </span></span>  
 [<span data-ttu-id="723f1-128">备份、还原和移动 SSIS 目录</span><span class="sxs-lookup"><span data-stu-id="723f1-128">Backup, Restore, and Move the SSIS Catalog</span></span>](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
