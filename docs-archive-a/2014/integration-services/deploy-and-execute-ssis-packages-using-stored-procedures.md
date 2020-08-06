---
title: 使用存储过程部署和执行 SSIS 包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1570207dca6e944b54c553a1d83256d8f4fa3244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693001"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a><span data-ttu-id="09e93-102">使用存储过程部署和执行 SSIS 包</span><span class="sxs-lookup"><span data-stu-id="09e93-102">Deploy and Execute SSIS Packages using Stored Procedures</span></span>
  <span data-ttu-id="09e93-103">在您配置一个 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目以便使用项目部署模型时，可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 目录中的存储过程部署该项目并且执行包。</span><span class="sxs-lookup"><span data-stu-id="09e93-103">When you configure an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to use the project deployment model, you can use stored procedures in the [!INCLUDE[ssIS](../includes/ssis-md.md)] catalog to deploy the project and execute the packages.</span></span> <span data-ttu-id="09e93-104">有关项目部署模型的信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="09e93-104">For information about the project deployment model, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="09e93-105">您还可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 部署项目和执行包。</span><span class="sxs-lookup"><span data-stu-id="09e93-105">You can also use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to deploy the project and execute the packages.</span></span> <span data-ttu-id="09e93-106">有关详细信息，请参阅“另请参见” \*\*\*\* 部分中的主题。</span><span class="sxs-lookup"><span data-stu-id="09e93-106">For more information, see the topics in the **See Also** section.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="09e93-107">您可以通过执行以下操作为下面的过程中列出的存储过程轻松地生成 Transact-SQL 语句，但 catalog.deploy_project 除外：</span><span class="sxs-lookup"><span data-stu-id="09e93-107">You can easily generate the Transact-SQL statements for the stored procedures listed in the procedure below, with the exception of catalog.deploy_project, by doing the following:</span></span>  
> 
>  1.  <span data-ttu-id="09e93-108">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，在对象资源管理器中展开“Integration Services 目录” \*\*\*\* 节点，然后导航到您要执行的包。</span><span class="sxs-lookup"><span data-stu-id="09e93-108">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** node in Object Explorer and navigate to the package you want to execute.</span></span>  
> 2.  <span data-ttu-id="09e93-109">右键单击该包，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="09e93-109">Right-click the package, and then click **Execute**.</span></span>  
> 3.  <span data-ttu-id="09e93-110">根据需要，设置参数值、连接管理器属性和 **“高级”** 选项卡中的选项（例如，日志记录级别）。</span><span class="sxs-lookup"><span data-stu-id="09e93-110">As needed, set parameters values, connection manager properties, and options in the **Advanced** tab such as the logging level.</span></span>  
> 
>      <span data-ttu-id="09e93-111">有关日志记录级别的详细信息，请参阅 [启用日志记录在 SSIS 服务器上的包执行的](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md)。</span><span class="sxs-lookup"><span data-stu-id="09e93-111">For more information about logging levels, see [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).</span></span>  
> 4.  <span data-ttu-id="09e93-112">在单击 **“确定”** 以便执行该包之前，单击 **“脚本”**。</span><span class="sxs-lookup"><span data-stu-id="09e93-112">Before clicking **OK** to execute the package, click **Script**.</span></span> <span data-ttu-id="09e93-113">Transact-SQL 将出现在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的“查询编辑器”窗口中。</span><span class="sxs-lookup"><span data-stu-id="09e93-113">The Transact-SQL appears in a Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a><span data-ttu-id="09e93-114">使用存储过程部署和执行包</span><span class="sxs-lookup"><span data-stu-id="09e93-114">To deploy and execute a package using stored procedures</span></span>  
  
1.  <span data-ttu-id="09e93-115">调用 [catalog.deploy_project（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) 将包含包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="09e93-115">Call [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) to deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="09e93-116">若要检索 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署文件的二进制内容，请对\* \@ project_stream\*参数使用带有 OPENROWSET 函数和 BULK 行集提供程序的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="09e93-116">To retrieve the binary contents of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project deployment file, for the *\@project_stream* parameter, use a SELECT statement with the OPENROWSET function and the BULK rowset provider.</span></span> <span data-ttu-id="09e93-117">通过 BULK 行集提供程序，您可以从文件读取数据。</span><span class="sxs-lookup"><span data-stu-id="09e93-117">The BULK rowset provider enables you to read data from a file.</span></span> <span data-ttu-id="09e93-118">BULK 行集提供程序的 SINGLE_BLOB 参数将该数据文件的内容以 varbinary(max) 类型的单行、单列行集的形式返回。</span><span class="sxs-lookup"><span data-stu-id="09e93-118">The SINGLE_BLOB argument for the BULK rowset provider returns the contents of the data file as a single-row, single-column rowset of type varbinary(max).</span></span> <span data-ttu-id="09e93-119">有关详细信息，请参阅 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09e93-119">For more information, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
     <span data-ttu-id="09e93-120">在下面的示例中，SSISPackages_ProjectDeployment 项目将部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器上的“SSIS 包”文件夹。</span><span class="sxs-lookup"><span data-stu-id="09e93-120">In the following example, the SSISPackages_ProjectDeployment project is deployed to the SSIS Packages folder on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="09e93-121">将从项目文件中读取二进制数据 (SSISPackage_ProjectDeployment .ispac) ，并将其存储在类型为 varbinary (max) 的\* \@ ProjectBinary\*参数中。</span><span class="sxs-lookup"><span data-stu-id="09e93-121">The binary data is read from the project file (SSISPackage_ProjectDeployment.ispac) and is stored in the *\@ProjectBinary* parameter of type varbinary(max).</span></span> <span data-ttu-id="09e93-122">\* \@ ProjectBinary*参数值将分配给* \@ project_stream\*参数。</span><span class="sxs-lookup"><span data-stu-id="09e93-122">The *\@ProjectBinary* parameter value is assigned to the *\@project_stream* parameter.</span></span>  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  <span data-ttu-id="09e93-123">调用 [catalog.create_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) 来创建包执行的实例，并根据需要调用 [catalog.set_execution_parameter_value（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) 来设置运行时参数值。</span><span class="sxs-lookup"><span data-stu-id="09e93-123">Call [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) to create an instance of the package execution, and optionally call [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) to set runtime parameter values.</span></span>  
  
     <span data-ttu-id="09e93-124">在下面的示例中，catalog.create_execution 为在 SSISPackage_ProjectDeployment 项目中包含的 package.dtsx 创建一个执行实例。</span><span class="sxs-lookup"><span data-stu-id="09e93-124">In the following example, catalog.create_execution creates an instance of execution for package.dtsx that is contained in the SSISPackage_ProjectDeployment project.</span></span> <span data-ttu-id="09e93-125">该项目位于“SSIS 包”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="09e93-125">The project is located in the SSIS Packages folder.</span></span> <span data-ttu-id="09e93-126">存储过程返回的 execution_id 用于对 catalog.set_execution_parameter_value 的调用中。</span><span class="sxs-lookup"><span data-stu-id="09e93-126">The execution_id returned by the stored procedure is used in the call to catalog.set_execution_parameter_value.</span></span> <span data-ttu-id="09e93-127">此第二个存储过程将 LOGGING_LEVEL 参数设置为 3（详细日志记录），并且将名为 Parameter1 的包参数设置为值 1。</span><span class="sxs-lookup"><span data-stu-id="09e93-127">This second stored procedure sets the LOGGING_LEVEL parameter to 3 (verbose logging) and sets a package parameter named Parameter1 to a value of 1.</span></span>  
  
     <span data-ttu-id="09e93-128">对于 LOGGING_LEVEL 之类的参数，object_type 值为 50。</span><span class="sxs-lookup"><span data-stu-id="09e93-128">For parameters such as LOGGING_LEVEL the object_type value is 50.</span></span> <span data-ttu-id="09e93-129">对于包参数，object_type 值为 30。</span><span class="sxs-lookup"><span data-stu-id="09e93-129">For package parameters the object_type value is 30.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  <span data-ttu-id="09e93-130">调用 [catalog.start_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)执行包。</span><span class="sxs-lookup"><span data-stu-id="09e93-130">Call [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) to execute the package.</span></span>  
  
     <span data-ttu-id="09e93-131">在下面的示例中，将对 catalog.start_execution 的调用添加到 Transact-SQL 以便开始包执行。</span><span class="sxs-lookup"><span data-stu-id="09e93-131">In the following example, a call to catalog.start_execution is added to the Transact-SQL to start the package execution.</span></span> <span data-ttu-id="09e93-132">将使用 catalog.create_execution 存储过程返回的 execution_id。</span><span class="sxs-lookup"><span data-stu-id="09e93-132">The execution_id returned by the catalog.create_execution stored procedure is used.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a><span data-ttu-id="09e93-133">使用存储过程将项目从一个服务器部署到另一个服务器</span><span class="sxs-lookup"><span data-stu-id="09e93-133">To deploy a project from server to server using stored procedures</span></span>  
 <span data-ttu-id="09e93-134">可以通过使用 [catalog.get_project（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database)和 [catalog.deploy_project（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database)存储过程在服务器之间部署项目。</span><span class="sxs-lookup"><span data-stu-id="09e93-134">You can deploy a project from server to server by using the [catalog.get_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) and [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) stored procedures.</span></span>  
  
 <span data-ttu-id="09e93-135">在运行存储过程之前，您需要执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="09e93-135">You need to do the following before running the stored procedures.</span></span>  
  
-   <span data-ttu-id="09e93-136">创建一个链接服务器对象。</span><span class="sxs-lookup"><span data-stu-id="09e93-136">Create a linked server object.</span></span> <span data-ttu-id="09e93-137">有关详细信息，请参阅[创建链接服务器（SQL Server 数据库引擎）](../database-engine/sql-server-database-engine-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="09e93-137">For more information, see [Create Linked Servers &#40;SQL Server Database Engine&#41;](../database-engine/sql-server-database-engine-overview.md).</span></span>  
  
     <span data-ttu-id="09e93-138">在 **“链接服务器属性”** 的 **“服务器选项”** 页上，将 **RPC** 和 **RPC Out** 设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="09e93-138">On the **Server Options** page of the **Linked Server Properties** dialog box, set **RPC** and **RPC Out** to **True**.</span></span> <span data-ttu-id="09e93-139">此外，将 **“为 RPC 启用针对分布式事务的升级”** 设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="09e93-139">Also, set **Enable Promotion of Distributed Transactions for RPC** to **False**.</span></span>  
  
-   <span data-ttu-id="09e93-140">通过在对象资源管理器中展开“链接服务器”下的“提供程序”节点，右键单击该提供程序，然后单击“属性”，对为链接服务器选择的提供程序启用动态参数。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="09e93-140">Enable dynamic parameters for the provider you selected for the linked server, by expanding the **Providers** node under **Linked Servers** in Object Explorer, right-clicking the provider, and then clicking **Properties**.</span></span> <span data-ttu-id="09e93-141">选择 **“动态参数”** 旁边的 **“启用”**。</span><span class="sxs-lookup"><span data-stu-id="09e93-141">Select **Enable** next to **Dynamic parameter.**</span></span>  
  
-   <span data-ttu-id="09e93-142">确认分布式事务处理协调器 (DTC) 在两个服务器上均启动。</span><span class="sxs-lookup"><span data-stu-id="09e93-142">Confirm that the Distributed Transaction Coordinator (DTC) is started on both servers.</span></span>  
  
 <span data-ttu-id="09e93-143">调用 catalog.get_project 以便返回该项目的二进制文件，然后调用 catalog.deploy_project。</span><span class="sxs-lookup"><span data-stu-id="09e93-143">Call catalog.get_project to return the binary for the project, and then call catalog.deploy_project.</span></span> <span data-ttu-id="09e93-144">将 catalog.get_project 返回的值插入 varbinary(max) 类型的表变量中。</span><span class="sxs-lookup"><span data-stu-id="09e93-144">The value returned by catalog.get_project is inserted into a table variable of type varbinary(max).</span></span> <span data-ttu-id="09e93-145">链接服务器无法返回类型为 varbinary(max) 的结果。</span><span class="sxs-lookup"><span data-stu-id="09e93-145">The linked server can't return results that are varbinary(max).</span></span>  
  
 <span data-ttu-id="09e93-146">在下面的示例中，catalog.get_project 为链接服务器上的 SSISPackages 项目返回二进制文件。</span><span class="sxs-lookup"><span data-stu-id="09e93-146">In the following example, catalog.get_project returns a binary for the SSISPackages project on the linked server.</span></span> <span data-ttu-id="09e93-147">catalog.deploy_project 将该项目部署到本地服务器上名为 DestFolder 的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="09e93-147">The catalog.deploy_project deploys the project to the local server, to the folder named DestFolder.</span></span>  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="09e93-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09e93-148">See Also</span></span>  
 <span data-ttu-id="09e93-149">[将项目部署到 Integration Services 服务器](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="09e93-149">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 <span data-ttu-id="09e93-150">[在 SQL Server Data Tools 中运行包](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="09e93-150">[Run a Package in SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="09e93-151">使用 SQL Server Management Studio 在 SSIS 服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="09e93-151">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
