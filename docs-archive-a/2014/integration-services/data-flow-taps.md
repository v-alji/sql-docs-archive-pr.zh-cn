---
title: 数据流点击 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053b34add45354d0df71fa73a72f8786cc706d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688079"
---
# <a name="data-flow-taps"></a><span data-ttu-id="1ba54-102">数据分流</span><span class="sxs-lookup"><span data-stu-id="1ba54-102">Data Flow Taps</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="1ba54-103">引入了一个新功能，可用来在运行时在包数据流路径上添加数据分流点，并将数据分流点的输出定向到外部文件。</span><span class="sxs-lookup"><span data-stu-id="1ba54-103">introduces a new feature that allows you to add a data tap on a data flow path of a package at runtime and direct the output from the data tap to an external file.</span></span> <span data-ttu-id="1ba54-104">若要使用此功能，您必须使用项目部署工具将 SSIS 项目部署到 SSIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="1ba54-104">To use this feature, you must deploy your SSIS project using the project deployment model to an SSIS Server.</span></span> <span data-ttu-id="1ba54-105">将包部署到服务器之后，需要对 SSISDB 数据库执行 T-SQL 脚本，以便在执行该包之前添加数据分流点。</span><span class="sxs-lookup"><span data-stu-id="1ba54-105">After you deploy the package to the server, you need to execute T-SQL scripts against the SSISDB database to add data taps before executing the package.</span></span> <span data-ttu-id="1ba54-106">下面是一个示例方案：</span><span class="sxs-lookup"><span data-stu-id="1ba54-106">Here is a sample scenario:</span></span>  
  
1.  <span data-ttu-id="1ba54-107">通过使用 [catalog.create_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)存储过程，创建包的执行实例。</span><span class="sxs-lookup"><span data-stu-id="1ba54-107">Create an execution instance of a package by using the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) stored procedure.</span></span>  
  
2.  <span data-ttu-id="1ba54-108">通过使用 [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) 或 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) 存储过程，添加数据分流点。</span><span class="sxs-lookup"><span data-stu-id="1ba54-108">Add a data tap by using either [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) or [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) stored procedure.</span></span>  
  
3.  <span data-ttu-id="1ba54-109">使用 [catalog.start_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)，启动包的执行实例。</span><span class="sxs-lookup"><span data-stu-id="1ba54-109">Start the execution instance of the package by using the [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
 <span data-ttu-id="1ba54-110">下面是执行上述方案中所述步骤的示例 SQL 脚本：</span><span class="sxs-lookup"><span data-stu-id="1ba54-110">Here is a sample SQL script that performs the steps described in the above scenario:</span></span>  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 <span data-ttu-id="1ba54-111">该 create_execution 存储过程的文件夹名称、项目名称和包名称参数对应于 Integration Services 目录中的文件夹、项目和包名称。</span><span class="sxs-lookup"><span data-stu-id="1ba54-111">The folder name, project name, and package name parameters of the create_execution stored procedure correspond to the folder, project, and package names in the Integration Services catalog.</span></span> <span data-ttu-id="1ba54-112">如下图所示，您可以从 SQL Server Management Studio 获取在 create_execution 调用中使用的文件夹、项目和包名称。</span><span class="sxs-lookup"><span data-stu-id="1ba54-112">You can get the folder, project, and package names to use in the create_execution call from the SQL Server Management Studio as shown in the following image.</span></span> <span data-ttu-id="1ba54-113">如果您在这里没有看到该 SSIS 项目，则可能还未将该项目部署到 SSIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="1ba54-113">If you do not see your SSIS project here, you may not have deployed the project to SSIS server yet.</span></span> <span data-ttu-id="1ba54-114">在 Visual Studio 中右键单击 SSIS 项目，然后单击“部署”以将该项目部署到目标 SSIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="1ba54-114">Right-click on SSIS project in Visual Studio and click Deploy to deploy the project to the expected SSIS server.</span></span>  
  
 <span data-ttu-id="1ba54-115">您可以不键入 SQL 语句，而是通过执行以下步骤来生成执行包脚本：</span><span class="sxs-lookup"><span data-stu-id="1ba54-115">Instead of typing the SQL statements, you can generate the execute package script by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="1ba54-116">右键单击“Package.dtsx”  ，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="1ba54-116">Right-click **Package.dtsx** and click **Execute**.</span></span>  
  
2.  <span data-ttu-id="1ba54-117">单击 **“脚本”** 工具栏按钮以生成脚本。</span><span class="sxs-lookup"><span data-stu-id="1ba54-117">Click **Script** toolbar button to generate the script.</span></span>  
  
3.  <span data-ttu-id="1ba54-118">现在，在 start_execution 调用的前面添加 add_data_tap 语句。</span><span class="sxs-lookup"><span data-stu-id="1ba54-118">Now, add the add_data_tap statement before the start_execution call.</span></span>  
  
 <span data-ttu-id="1ba54-119">add_data_tap 存储过程的 task_package_path 参数对应于 Visual Studio 中数据流任务的 PackagePath 属性。</span><span class="sxs-lookup"><span data-stu-id="1ba54-119">The task_package_path parameter of add_data_tap stored procedure corresponds to the PackagePath property of the data flow task in Visual Studio.</span></span> <span data-ttu-id="1ba54-120">在 Visual Studio 中，右键单击“数据流任务”  ，然后单击“属性”  启动“属性”窗口。</span><span class="sxs-lookup"><span data-stu-id="1ba54-120">In Visual Studio, right-click the **Data Flow Task**, and click **Properties** to launch the Properties window.</span></span>  <span data-ttu-id="1ba54-121">请记下 **PackagePath** 属性的值，以将其用作 add_data_tap 存储过程调用的 task_package_path 参数值。</span><span class="sxs-lookup"><span data-stu-id="1ba54-121">Note the value of the **PackagePath** property to use it as a value for the task_package_path parameter for add_data_tap stored procedure call.</span></span>  
  
 <span data-ttu-id="1ba54-122">add_data_tap 存储过程的 dataflow_path_id_string 参数对应于您要添加数据分流点的数据流路径的 IdentificationString 属性。</span><span class="sxs-lookup"><span data-stu-id="1ba54-122">The dataflow_path_id_string  parameter of add_data_tap stored procedure corresponds to the IdentificationString property of the data flow path to which you want to add a data tap.</span></span> <span data-ttu-id="1ba54-123">若要获取 dataflow_path_id_string，请单击数据流路径（数据流中任务间的箭头），并记下“属性”窗口中 **IdentificationString** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1ba54-123">To get the dataflow_path_id_string, click the data flow path (arrow between tasks in the data flow), and note the value of the **IdentificationString** property in the Properties window.</span></span>  
  
 <span data-ttu-id="1ba54-124">执行脚本时，输出文件存储在 \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps 中。</span><span class="sxs-lookup"><span data-stu-id="1ba54-124">When you execute the script, the output file is stored in \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps.</span></span> <span data-ttu-id="1ba54-125">如果已存在同名文件，则将创建带有后缀的新文件（例如：output[1].txt）。</span><span class="sxs-lookup"><span data-stu-id="1ba54-125">If a file with the name already exists, a new file with a suffix (for example: output[1].txt)  is created.</span></span>  
  
 <span data-ttu-id="1ba54-126">如前所述，也可使用 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)存储过程代替使用 add_data_tap 存储过程。</span><span class="sxs-lookup"><span data-stu-id="1ba54-126">As mentioned earlier, you can also use [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)stored procedure instead of using add_data_tap stored procedure.</span></span> <span data-ttu-id="1ba54-127">此存储过程将数据流任务的 ID 用作参数，而不使用 task_package_path。</span><span class="sxs-lookup"><span data-stu-id="1ba54-127">This stored procedure takes the ID of data flow task as a parameter instead of task_package_path.</span></span> <span data-ttu-id="1ba54-128">您可以从 Visual Studio 中的属性窗口获取数据流任务的 ID。</span><span class="sxs-lookup"><span data-stu-id="1ba54-128">You can get the ID of data flow task from the properties window in Visual Studio.</span></span>  
  
## <a name="removing-a-data-tap"></a><span data-ttu-id="1ba54-129">删除数据分流点</span><span class="sxs-lookup"><span data-stu-id="1ba54-129">Removing a data tap</span></span>  
 <span data-ttu-id="1ba54-130">可使用 [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) 存储过程删除数据分流点，然后再启动执行。</span><span class="sxs-lookup"><span data-stu-id="1ba54-130">You can remove a data tap before starting the execution by using the [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) stored procedure.</span></span> <span data-ttu-id="1ba54-131">此存储过程将数据分流点 ID 用作参数，此 ID 可作为 add_data_tap 存储过程的输出来获取。</span><span class="sxs-lookup"><span data-stu-id="1ba54-131">This stored procedure takes the ID of data tap as a parameter, which you can get as an output of the add_data_tap stored procedure.</span></span>  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a><span data-ttu-id="1ba54-132">列出所有数据分流点</span><span class="sxs-lookup"><span data-stu-id="1ba54-132">Listing all data taps</span></span>  
 <span data-ttu-id="1ba54-133">您也可以使用 catalog.execution_data_taps 视图列出所有数据分流点。</span><span class="sxs-lookup"><span data-stu-id="1ba54-133">You can also list all the data taps by using the catalog.execution_data_taps view.</span></span> <span data-ttu-id="1ba54-134">下面的示例提取一个规范执行实例（ID：54）的数据分流点。</span><span class="sxs-lookup"><span data-stu-id="1ba54-134">The following example extracts data taps for a specification execution instance (ID: 54).</span></span>  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a><span data-ttu-id="1ba54-135">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="1ba54-135">Performance consideration</span></span>  
 <span data-ttu-id="1ba54-136">启用详细日志记录级别并添加数据分流点会增加数据集成解决方案所执行的 I/O 操作数。</span><span class="sxs-lookup"><span data-stu-id="1ba54-136">Enabling verbose logging level and adding data taps increase the I/O operations performed by your data integration solution.</span></span> <span data-ttu-id="1ba54-137">因此，建议仅出于故障排除目的添加数据分流点。</span><span class="sxs-lookup"><span data-stu-id="1ba54-137">Hence, we recommend that you add data taps only for troubleshooting purposes</span></span>  
  
## <a name="video"></a><span data-ttu-id="1ba54-138">视频</span><span class="sxs-lookup"><span data-stu-id="1ba54-138">Video</span></span>  
 <span data-ttu-id="1ba54-139">此 [video on TechNet](https://technet.microsoft.com/sqlserver/dn600163) 演示了如何在 SQL Server 2012 SSISDB 目录中添加/使用数据分流点，从而有助于以编程方式对包进行调试并在运行时捕获部分结果。</span><span class="sxs-lookup"><span data-stu-id="1ba54-139">This [video on TechNet](https://technet.microsoft.com/sqlserver/dn600163) demonstrates how to add/use data taps in SQL Server 2012 SSISDB catalog that help with debugging packages programmatically and capturing the partial results at the runtime.</span></span> <span data-ttu-id="1ba54-140">它还讨论了如何列出/删除这些数据分流点，并讨论了在 SSIS 包中使用数据分流点的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="1ba54-140">It also discusses how to list/ remove these data taps and best practices for using data taps in SSIS packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ba54-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1ba54-141">Related Tasks</span></span>  
 [<span data-ttu-id="1ba54-142">调试数据流</span><span class="sxs-lookup"><span data-stu-id="1ba54-142">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="1ba54-143">包执行的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="1ba54-143">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
