---
title: 步骤 3：测试已部署的包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9159da3f-c9ca-4015-9e85-3bf4373a1349
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d11ae071d97d9fdadec6ee144813c91519b54ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581376"
---
# <a name="step-3-testing-the-deployed-packages"></a><span data-ttu-id="338ac-102">步骤 3：测试已部署的包</span><span class="sxs-lookup"><span data-stu-id="338ac-102">Step 3: Testing the Deployed Packages</span></span>
  <span data-ttu-id="338ac-103">在此任务中，将测试已部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例的包。</span><span class="sxs-lookup"><span data-stu-id="338ac-103">In this task, you will test the packages that you deployed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="338ac-104">在其他 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教程中，可以在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的开发环境中使用“调试”菜单上的“开始调试”选项运行 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的包。</span><span class="sxs-lookup"><span data-stu-id="338ac-104">In other [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorials, you ran packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the development environment for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], using the **Start Debugging** option on the **Debug** menu.</span></span> <span data-ttu-id="338ac-105">这一次，将以不同方式运行包。</span><span class="sxs-lookup"><span data-stu-id="338ac-105">This time you will run the packages differently.</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="338ac-106">提供了几个可用于在测试和生产环境中运行包的工具：命令提示实用工具 `dtexec` 和执行包实用工具。</span><span class="sxs-lookup"><span data-stu-id="338ac-106">provides several tools that you can use to run packages in the test and production environment: the command prompt utility `dtexec` and the Execute Package Utility.</span></span> <span data-ttu-id="338ac-107">执行包实用工具是基于 `dtexec` 构建的图形工具。</span><span class="sxs-lookup"><span data-stu-id="338ac-107">The Execute Package Utility is a graphical tool that is built on `dtexec`.</span></span> <span data-ttu-id="338ac-108">这两种工具均可直接执行包。</span><span class="sxs-lookup"><span data-stu-id="338ac-108">Both of these tools execute the package immediately.</span></span> <span data-ttu-id="338ac-109">此外， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 还提供了一个 SQL Server 代理子系统，专门用于将包执行计划为 SQL Server 代理作业中的一个步骤。</span><span class="sxs-lookup"><span data-stu-id="338ac-109">In addition, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides a subsystem of SQL Server Agent that is especially designed for scheduling package execution as a step in a SQL Server Agent job.</span></span>

 <span data-ttu-id="338ac-110">将使用执行包实用工具运行已部署的包。</span><span class="sxs-lookup"><span data-stu-id="338ac-110">You will use the Execute Package Utility to run the deployed packages.</span></span> <span data-ttu-id="338ac-111">将照原样使用包；因此，您不必更新对话框中任何页上的信息。</span><span class="sxs-lookup"><span data-stu-id="338ac-111">The packages will be used as is; therefore, you do not have to update information on any pages in the dialog box.</span></span> <span data-ttu-id="338ac-112">您将从“常规”页运行包，该页是执行包实用工具中的第一页。</span><span class="sxs-lookup"><span data-stu-id="338ac-112">You will run the packages from the General page, which is the first page in the Execute Package Utility.</span></span> <span data-ttu-id="338ac-113">如果愿意，还可以单击其他页以查看其中包含的有关每个包的信息。</span><span class="sxs-lookup"><span data-stu-id="338ac-113">If you like, you can click the other pages too see the information that they contain for each package.</span></span>

> [!NOTE]
>  <span data-ttu-id="338ac-114">为确保在本教程的上下文中成功运行包，您不应修改任何选项。</span><span class="sxs-lookup"><span data-stu-id="338ac-114">To ensure that the packages run successfully in the context of this tutorial, you should not modify any options.</span></span>

 <span data-ttu-id="338ac-115">通过使用执行包实用工具在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中运行包之前，请确保 Integration Services 服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="338ac-115">Before you run packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by using the Execute Package Utility, ensure that the Integration Services service is running.</span></span> <span data-ttu-id="338ac-116">Integration Services 服务提供对包存储和执行的支持。</span><span class="sxs-lookup"><span data-stu-id="338ac-116">The Integration Services service provides support for package storage and execution.</span></span> <span data-ttu-id="338ac-117">如果该服务已停止，则您无法连接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，而且 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 不列出要运行的包。</span><span class="sxs-lookup"><span data-stu-id="338ac-117">If the service is stopped, you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] does not list the packages to run.</span></span> <span data-ttu-id="338ac-118">您还必须具有在其中已部署包的实例上运行包的权限。</span><span class="sxs-lookup"><span data-stu-id="338ac-118">You also must have permissions to run the package on the instance where the package has been deployed.</span></span> <span data-ttu-id="338ac-119">有关详细信息，请参阅 [Integration Services Roles（SSIS 服务）](security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="338ac-119">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="338ac-120">“已存储的包”文件夹内的顶级文件夹是 Integration Services 服务监视的用户定义文件夹。</span><span class="sxs-lookup"><span data-stu-id="338ac-120">The top-level folders within the Stored Packages folder are the user-defined folders that Integration Services service monitors.</span></span> <span data-ttu-id="338ac-121">您可以在 MsDtsSrvr.ini.xml 文件中指定所需数目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="338ac-121">You can specify as many or few folders in the MsDtsSrvr.ini.xml file as you want.</span></span> <span data-ttu-id="338ac-122">本教程假定您使用的是默认 MsDtsSrvr.ini.xml 文件，并假定“已存储的包”文件夹内的顶级文件夹的名称是“文件系统”和“MSDB”。</span><span class="sxs-lookup"><span data-stu-id="338ac-122">This tutorial assumes that you are using the default MsDtsSrvr.ini.xml file, and that the names of the top-level folders within Stored Packages are File System and MSDB.</span></span>

### <a name="to-connect-to-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="338ac-123">在 SQL Server Management Studio 中连接到 Integration Services</span><span class="sxs-lookup"><span data-stu-id="338ac-123">To connect to Integration Services in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="338ac-124">单击 **“开始”** ，依次指向 **“所有程序”** 和 **Microsoft SQL Server**，然后单击 **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="338ac-124">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="338ac-125">在“连接到服务器”对话框中，选择“服务器类型”列表中的“Integration Services”，在“服务器名称”框中提供服务器名称，再单击“连接”。     </span><span class="sxs-lookup"><span data-stu-id="338ac-125">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and click **Connect**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="338ac-126">如果无法连接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]，则 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务可能未运行。</span><span class="sxs-lookup"><span data-stu-id="338ac-126">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="338ac-127">若要了解该服务的状态，请单击 **“开始”** ，依次指向 **“所有程序”** 、 **Microsoft SQL Server**和 **“配置工具”** ，再单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="338ac-127">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="338ac-128">在左窗格中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="338ac-128">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="338ac-129">在右窗格中，查找 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="338ac-129">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="338ac-130">如果该服务尚未运行，请启动该服务。</span><span class="sxs-lookup"><span data-stu-id="338ac-130">Start the service if it is not already running.</span></span>

     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="338ac-131">。</span><span class="sxs-lookup"><span data-stu-id="338ac-131">opens.</span></span> <span data-ttu-id="338ac-132">默认情况下，对象资源管理器窗口是打开的，且位于 Studio 的右上角。</span><span class="sxs-lookup"><span data-stu-id="338ac-132">By default the Object Explorer window is open and placed in the upper right corner of the studio.</span></span> <span data-ttu-id="338ac-133">如果对象资源管理器未打开，请单击 **“视图”** 菜单上的 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="338ac-133">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>

### <a name="to-run-the-packages-using-the-execute-package-utility"></a><span data-ttu-id="338ac-134">使用执行包实用工具运行包</span><span class="sxs-lookup"><span data-stu-id="338ac-134">To run the packages using the Execute Package Utility</span></span>

1.  <span data-ttu-id="338ac-135">在对象资源管理器中，展开“已存储的包”文件夹。</span><span class="sxs-lookup"><span data-stu-id="338ac-135">In Object Explorer, expand the Stored Packages folder.</span></span>

2.  <span data-ttu-id="338ac-136">展开 MSDB 文件夹。</span><span class="sxs-lookup"><span data-stu-id="338ac-136">Expand the MSDB folder.</span></span> <span data-ttu-id="338ac-137">由于您已将包部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，因此所有已部署的包都存储在 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中，并出现在 MSDB 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="338ac-137">Because you deployed the packages to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all the deployed packages are stored in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and all deployed packages appear in the MSDB folder.</span></span> <span data-ttu-id="338ac-138">除非已将包部署到 Deployment Tutorial 外部的文件系统，否则“文件系统”文件夹为空。</span><span class="sxs-lookup"><span data-stu-id="338ac-138">The File System folder is empty, unless you have deployed packages to the file system outside of the Deployment Tutorial.</span></span>

3.  <span data-ttu-id="338ac-139">从包列表的顶部开始，右键单击 DataTransfer，再单击“运行包”。 </span><span class="sxs-lookup"><span data-stu-id="338ac-139">Starting at the top of the package list, right-click DataTransfer, and click **Run Package**.</span></span>

4.  <span data-ttu-id="338ac-140">在“执行包实用工具”对话框中，单击“执行”。  </span><span class="sxs-lookup"><span data-stu-id="338ac-140">In the **Execute Package Utility** dialog box, click **Execute**.</span></span>

5.  <span data-ttu-id="338ac-141">在“执行包实用工具”对话框中，查看包的执行进度和执行结果。 </span><span class="sxs-lookup"><span data-stu-id="338ac-141">In the **Execute Package Utility** dialog box, view the progress and execution results of the package.</span></span> <span data-ttu-id="338ac-142">当“停止”按钮变为不可用时（表示包的执行已完成），单击“关闭”。  </span><span class="sxs-lookup"><span data-stu-id="338ac-142">When the **Stop** button becomes unavailable, which indicates that the package has completed, click **Close**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="338ac-143">如果在包正在执行时单击“停止”，则包的执行将无法完成。 </span><span class="sxs-lookup"><span data-stu-id="338ac-143">If you click **Stop** while the package is running, the package will not finish.</span></span>

6.  <span data-ttu-id="338ac-144">在“执行包实用工具”对话框中，单击“关闭”。  </span><span class="sxs-lookup"><span data-stu-id="338ac-144">In the **Execute Package Utility** dialog box, click **Close**.</span></span>

7.  <span data-ttu-id="338ac-145">对于 LoadXML 包，重复步骤 3-6。</span><span class="sxs-lookup"><span data-stu-id="338ac-145">Repeat steps 3 - 6 for the LoadXML package.</span></span>

8.  <span data-ttu-id="338ac-146">在 **“文件”** 菜单中，单击 **“退出”** 。</span><span class="sxs-lookup"><span data-stu-id="338ac-146">On the **File** menu, click **Exit**.</span></span>

### <a name="to-verify-the-results-of-the-datatransfer-package"></a><span data-ttu-id="338ac-147">验证 DataTransfer 包的结果</span><span class="sxs-lookup"><span data-stu-id="338ac-147">To verify the results of the DataTransfer package</span></span>

1.  <span data-ttu-id="338ac-148">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的工具栏上，单击“新建查询”。 </span><span class="sxs-lookup"><span data-stu-id="338ac-148">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="338ac-149">在“连接到服务器”对话框中，选择“服务器类型”列表中的“数据库引擎”，在“服务器名称”框中提供在其上已安装教程包的服务器的名称或键入 (local)，再选择身份验证模式。    </span><span class="sxs-lookup"><span data-stu-id="338ac-149">In the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server name on which you installed the tutorial packages or type (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="338ac-150">如果使用 SQL Server 身份验证，请提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="338ac-150">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="338ac-151">单击“连接”  。</span><span class="sxs-lookup"><span data-stu-id="338ac-151">Click **Connect**.</span></span>

4.  <span data-ttu-id="338ac-152">在查询窗口中，键入或粘贴以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="338ac-152">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM HighIncomeCustomers`

5.  <span data-ttu-id="338ac-153">按 **F5** 或单击工具栏上的“执行”图标。</span><span class="sxs-lookup"><span data-stu-id="338ac-153">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="338ac-154">查询将返回 31 行数据。</span><span class="sxs-lookup"><span data-stu-id="338ac-154">The query returns 31 rows of data.</span></span> <span data-ttu-id="338ac-155">返回结果包含了文本文件 Customers.txt 的 YearlyIncome 列中值大于 100000 的任何行。</span><span class="sxs-lookup"><span data-stu-id="338ac-155">The return result contains any rows from the text file, Customers.txt, that have values larger than 100000 in the YearlyIncome column.</span></span>

6.  <span data-ttu-id="338ac-156">找到 DeploymentTutorial 文件夹，右键单击日志 XML 文件 Deployment Tutorial Log，再单击“打开”。 </span><span class="sxs-lookup"><span data-stu-id="338ac-156">Locate the DeploymentTutorial folder, right-click the log XML file, Deployment Tutorial Log, and then click **Open**.</span></span> <span data-ttu-id="338ac-157">可以使用记事本或所选的文本/XML 编辑器打开该文件。</span><span class="sxs-lookup"><span data-stu-id="338ac-157">You can open the file by using Notepad or the text/XML editor of choice.</span></span>

### <a name="to-verify-the-results-of-the-loadxmldata-package"></a><span data-ttu-id="338ac-158">验证 LoadXMLData 包的结果</span><span class="sxs-lookup"><span data-stu-id="338ac-158">To verify the results of the LoadXMLData package</span></span>

1.  <span data-ttu-id="338ac-159">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的工具栏上，单击“新建查询”。 </span><span class="sxs-lookup"><span data-stu-id="338ac-159">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="338ac-160">如果再次提示进行连接，请在“连接到服务器”对话框中，选择“服务器类型”列表中的“数据库引擎”，在“服务器名称”框中提供在其上已安装教程包的服务器的名称或输入 (local)，再选择身份验证模式。    </span><span class="sxs-lookup"><span data-stu-id="338ac-160">If prompted to connect again, in the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server on which you installed the tutorial packages or enter (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="338ac-161">如果使用 SQL Server 身份验证，请提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="338ac-161">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="338ac-162">单击“连接”  。</span><span class="sxs-lookup"><span data-stu-id="338ac-162">Click **Connect**.</span></span>

4.  <span data-ttu-id="338ac-163">在查询窗口中，键入或粘贴以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="338ac-163">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM OrderDatesByCountryRegion`

5.  <span data-ttu-id="338ac-164">按 **F5** 或单击工具栏上的“执行”图标。</span><span class="sxs-lookup"><span data-stu-id="338ac-164">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="338ac-165">查询将返回 21 行数据。</span><span class="sxs-lookup"><span data-stu-id="338ac-165">The query returns 21 rows of data.</span></span> <span data-ttu-id="338ac-166">返回结果中包含来自 XML 数据文件 orders.xml 的行。</span><span class="sxs-lookup"><span data-stu-id="338ac-166">The return result consists of the rows from the XML data file, orders.xml.</span></span> <span data-ttu-id="338ac-167">在每行中按国家/地区进行了汇总；行中列出了国家/地区的名称、每个国家/地区的订单数以及最新订单和最早订单的日期。</span><span class="sxs-lookup"><span data-stu-id="338ac-167">Each row is a summary by country/region; the row lists the name of a country/region, the number of orders for each country/region and the dates of the newest and oldest orders.</span></span>

<span data-ttu-id="338ac-168">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="338ac-168">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="338ac-169">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="338ac-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="338ac-170">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="338ac-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="338ac-171">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="338ac-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="338ac-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="338ac-172">See Also</span></span>
 [<span data-ttu-id="338ac-173">dtexec 实用工具</span><span class="sxs-lookup"><span data-stu-id="338ac-173">dtexec Utility</span></span>](packages/dtexec-utility.md)


