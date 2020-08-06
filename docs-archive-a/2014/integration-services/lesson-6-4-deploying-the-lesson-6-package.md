---
title: 步骤 4：部署第 6 课包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c5109dc96af138bbd0c8c0087e8b73cf3bac435
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591483"
---
# <a name="step-4-deploying-the-lesson-6-package"></a><span data-ttu-id="7a9e6-102">步骤 4：部署第 6 课包</span><span class="sxs-lookup"><span data-stu-id="7a9e6-102">Step 4: Deploying the Lesson 6 Package</span></span>
  <span data-ttu-id="7a9e6-103">部署包涉及将包添加到 SQL Server 实例上 Integration Services 中的 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-103">Deploying the package involves adding the package to the SSISDB catalog in Integration Services on an instance of SQL Server.</span></span> <span data-ttu-id="7a9e6-104">在本课程中，你会将第 6 课包添加到 SSISDB 目录，设置参数，然后执行该包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-104">In this lesson you will add the Lesson 6 package to the SSISDB catalog, set the parameter, and execute the package.</span></span> <span data-ttu-id="7a9e6-105">对于本课程，你将使用 SQL Server Management Studio 将第 6 课包添加到 SSISDB 目录，然后部署该包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-105">For this lesson you will use SQL Server Management Studio to add the Lesson 6 package to the SSISDB catalog, and deploy the package.</span></span> <span data-ttu-id="7a9e6-106">部署该包之后，你会修改参数以指向新位置，然后执行该包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-106">After deploying the package you will modify the parameter to point to a new location then execute the package.</span></span>  
  
 <span data-ttu-id="7a9e6-107">在本课程中，你将：</span><span class="sxs-lookup"><span data-stu-id="7a9e6-107">In this lesson you will:</span></span>  
  
-   <span data-ttu-id="7a9e6-108">将包添加到 SQL Server 的 SSIS 节点中的 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-108">Add the package to the SSISDB catalog in the SSIS node in SQL Server.</span></span>  
  
-   <span data-ttu-id="7a9e6-109">部署包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-109">Deploy the package.</span></span>  
  
-   <span data-ttu-id="7a9e6-110">设置包参数值。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-110">Set the package parameter value.</span></span>  
  
-   <span data-ttu-id="7a9e6-111">在 SSMS 中执行包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-111">Execute the package in SSMS.</span></span>  
  
### <a name="to-locate-or-add-the-ssisdb-catalog"></a><span data-ttu-id="7a9e6-112">找到或添加 SSISDB 目录</span><span class="sxs-lookup"><span data-stu-id="7a9e6-112">To Locate or add the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="7a9e6-113">单击“开始”，依次指向“所有程序”和“Microsoft SQL Server 2012”，然后单击“SQL Management Studio”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-113">Click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Management Studio.</span></span>  
  
2.  <span data-ttu-id="7a9e6-114">在“连接到服务器”对话框中，查看默认设置，然后单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-114">On the Connect to Server dialog box, verify the default settings, and then click Connect.</span></span> <span data-ttu-id="7a9e6-115">若要连接，“服务器名称”框必须包含安装 SQL Server 的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-115">To connect, the Server name box must contain the name of the computer where SQL Server is installed.</span></span> <span data-ttu-id="7a9e6-116">如果数据库引擎为命名实例，则“服务器名称”框还应包含格式为 <计算机名>\\<实例名> 的实例名。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-116">If the Database Engine is a named instance, the Server name box should also contain the instance name in the format <computer_name>\\<instance_name>.</span></span>  
  
3.  <span data-ttu-id="7a9e6-117">在对象资源管理器中，展开“Integration Services 目录”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-117">In Object Explorer expand Integration Services Catalogs.</span></span>  
  
4.  <span data-ttu-id="7a9e6-118">如果“Integration Services 目录”下未列出任何目录，请添加 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-118">If there are no catalogs listed under Integration Services Catalogs then add the SSISDB catalog.</span></span>  
  
5.  <span data-ttu-id="7a9e6-119">若要添加 SSISDB 目录，请右键单击“Integration Services 目录”，然后单击“创建目录”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-119">To Add the SSISDB catalog, right-click Integration Services Catalogs and click Create Catalog.</span></span>  
  
6.  <span data-ttu-id="7a9e6-120">在“创建目录”对话框中，选择“启用 CLR 集成”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-120">On the Create Catalog dialog box select Enable CLR Integration.</span></span>  
  
7.  <span data-ttu-id="7a9e6-121">在“密码”框中，输入新密码，然后在“重新键入密码”框中再次输入它。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-121">In the Password box, type a new password then type it again in the Retype Password box.</span></span> <span data-ttu-id="7a9e6-122">请务必记住输入的密码。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-122">Be sure to remember the password you type.</span></span>  
  
8.  <span data-ttu-id="7a9e6-123">单击“确定”以添加 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-123">Click OK to add the SSISDB catalog.</span></span>  
  
### <a name="to-add-the-package-to-the-ssisdb-catalog"></a><span data-ttu-id="7a9e6-124">将包添加到 SSISDB 目录</span><span class="sxs-lookup"><span data-stu-id="7a9e6-124">To add the package to the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="7a9e6-125">在对象资源管理器中，右键单击“SSISDB”，然后单击“创建文件夹”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-125">In Object Explorer, right-click SSISDB and click Create Folder.</span></span>  
  
2.  <span data-ttu-id="7a9e6-126">在“创建文件夹”对话框中，在“文件夹名称”框中输入 SSIS Tutorial，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-126">In the Create Folder dialog box type SSIS Tutorial in the Folder name box and click OK.</span></span>  
  
3.  <span data-ttu-id="7a9e6-127">展开“SSIS Tutorial”文件夹，右键单击“项目”，然后单击“导入包”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-127">Expand the SSIS Tutorial folder, right-click Projects, and click Import Packages.</span></span>  
  
4.  <span data-ttu-id="7a9e6-128">在 Integration Services 项目转换向导简介页面上单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-128">On the Integration Services Project Conversion Wizard Introduction page click Next.</span></span>  
  
5.  <span data-ttu-id="7a9e6-129">在“查找包”页面上，确保在“源”列表中选择“文件系统”，然后单击“浏览”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-129">On the Locate Packages page, ensure that File system is selected in the Source list, then click Browse.</span></span>  
  
6.  <span data-ttu-id="7a9e6-130">在“浏览文件夹”对话框中，浏览到包含 SSIS Tutorial 项目的文件夹，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-130">On the Browse For Folder dialog box, browse to the folder containing the SSIS Tutorial project, then click OK.</span></span>  
  
7.  <span data-ttu-id="7a9e6-131">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-131">Click Next.</span></span>  
  
8.  <span data-ttu-id="7a9e6-132">在“选择包”页面中，应看到 SSIS Tutorial 中的所有六个包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-132">On the Select Packages page you should see all six packages from the SSIS Tutorial.</span></span> <span data-ttu-id="7a9e6-133">在“包”列表中，选择 Lesson 6.dtsx，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-133">In the Packages list, select Lesson 6.dtsx, then click Next.</span></span>  
  
9. <span data-ttu-id="7a9e6-134">在“选择目标”页面上的“项目名称”框中输入 SSIS Tutorial Deployment，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-134">On the Select Destination page, type SSIS Tutorial Deployment in the Project Name box then click Next.</span></span>  
  
10. <span data-ttu-id="7a9e6-135">在其余每个向导页面上单击“下一步”，直到进入“检查”页面。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-135">Click Next on each of the remaining wizard pages until you get to the Review page.</span></span>  
  
11. <span data-ttu-id="7a9e6-136">在“检查”页面上，单击“转换”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-136">On the Review page, click Convert.</span></span>  
  
12. <span data-ttu-id="7a9e6-137">转换完成时，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-137">When the conversion completes, click Close.</span></span>  
  
 <span data-ttu-id="7a9e6-138">关闭 Integration Services 项目转换向导时，SSIS 会显示 Integration Services 部署向导。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-138">When you close the Integration Services Project Conversion Wizard, SSIS displays the Integration Services Deployment Wizard.</span></span> <span data-ttu-id="7a9e6-139">你现在将使用此向导部署第 6 课包。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-139">You will use this wizard now to deploy the Lesson 6 package.</span></span>  
  
1.  <span data-ttu-id="7a9e6-140">在 Integration Services 部署向导简介页面上，检查用于部署项目的步骤，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-140">On the Integration Services Deployment Wizard Introduction page, review the steps for deploying the project, then click Next.</span></span>  
  
2.  <span data-ttu-id="7a9e6-141">在“选择目标”页面上，验证服务器名是否为包含 SSISDB 目录的 SQL Server 实例，以及路径是否显示 SSIS Tutorial Deployment，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-141">On the Select Destination page verify that the server name is the instance of SQL Server containing the SSISDB catalog and that the path shows SSIS Tutorial Deployment, then click Next.</span></span>  
  
3.  <span data-ttu-id="7a9e6-142">在“检查”页面上检查“摘要”，然后单击“部署”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-142">On the Review page, review the Summary then click Deploy.</span></span>  
  
4.  <span data-ttu-id="7a9e6-143">部署完成时，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-143">When the deployment completes, click Close.</span></span>  
  
5.  <span data-ttu-id="7a9e6-144">在对象资源管理器中，右键单击“Integration Services 目录”，然后单击“刷新”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-144">In Object Explorer, right-click Integration Services Catalogs and click Refresh.</span></span>  
  
6.  <span data-ttu-id="7a9e6-145">展开“Integration Services 目录”，然后展开“SSISDB”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-145">Expand Integration Services Catalogs then expand SSISDB.</span></span> <span data-ttu-id="7a9e6-146">继续展开 SSIS Tutorial 下的树，直到完全展开项目。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-146">Continue to Expand the tree under SSIS Tutorial until you have completely expanded the project.</span></span> <span data-ttu-id="7a9e6-147">应在“SSIS Tutorial Deployment”节点的“包”节点下看到 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-147">You should see Lesson 6.dtsx under the Packages node of the SSIS Tutorial Deployment node.</span></span>  
  
 <span data-ttu-id="7a9e6-148">若要验证该包是否完整，请右键单击 Lesson 6.dtsx，然后单击“配置”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-148">To verify that the package is complete, right-click Lesson 6.dtsx and click Configure.</span></span> <span data-ttu-id="7a9e6-149">在“配置”对话框中，选择“参数”，验证是否有一个条目将 Lesson 6.dtsx 作为“容器”、将 VarFolderName 作为“名称”并将 New Sample Data 的路径作为“值”，然后单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-149">On the Configure dialog box, select Parameters and verify that there is an entry with Lesson 6.dtsx as the Container, VarFolderName as the Name and the path to New Sample Data as the value, then click Close.</span></span>  
  
 <span data-ttu-id="7a9e6-150">继续创建新示例数据文件夹之前，将它命名为 Sample Data Two，并将任何三个原始示例文件复制到其中。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-150">Before continuing create a new sample data folder, name it Sample Data Two, and copy any three of the original sample files into it.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="7a9e6-151">创建并填充新的示例数据文件夹</span><span class="sxs-lookup"><span data-stu-id="7a9e6-151">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="7a9e6-152">在 Windows 资源管理器中，在驱动器的根位置（例如，C:\\）创建名为 Sample Data Two 的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-152">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named Sample Data Two.</span></span>  
  
2.  <span data-ttu-id="7a9e6-153">打开 c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data 文件夹，然后复制该文件夹中的任意三个示例文件。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-153">Open the c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data folder and then copy any three of the sample files from the folder.</span></span>  
  
3.  <span data-ttu-id="7a9e6-154">在 New Sample Data 文件夹中，粘贴所复制的文件。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-154">In the New Sample Data folder, paste the copied files.</span></span>  
  
### <a name="to-change-the-package-parameter-to-point-to-the-new-sample-data"></a><span data-ttu-id="7a9e6-155">更改包参数以指向新示例数据</span><span class="sxs-lookup"><span data-stu-id="7a9e6-155">To change the package parameter to point to the new sample data</span></span>  
  
1.  <span data-ttu-id="7a9e6-156">在对象资源管理器中，右键单击 Lesson 6.dtsx，然后单击“配置”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-156">In Object Explorer, right click Lesson 6.dtsx and click Configure.</span></span>  
  
2.  <span data-ttu-id="7a9e6-157">在“配置”对话框中，将参数值更改为 Sample Data Two 的路径。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-157">On the Configure dialog box, change the parameter value to the path to Sample Data Two.</span></span> <span data-ttu-id="7a9e6-158">例如 C:\Sample Data Two（如果将新文件夹置于 C 驱动器上的根文件夹中）。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-158">For example C:\Sample Data Two if you placed the new folder in the root folder on the C drive.</span></span>  
  
3.  <span data-ttu-id="7a9e6-159">单击“确定”关闭“配置”对话框。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-159">Click OK to close the Configure dialog box.</span></span>  
  
### <a name="to-test-the-lesson-6-package-deployment"></a><span data-ttu-id="7a9e6-160">测试第 6 课包部署</span><span class="sxs-lookup"><span data-stu-id="7a9e6-160">To test the Lesson 6 package deployment</span></span>  
  
1.  <span data-ttu-id="7a9e6-161">在对象资源管理器中，右键单击 Lesson 6.dtsx，然后单击“执行”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-161">In Object Explorer, right click Lesson 6.dtsx and click Execute.</span></span>  
  
2.  <span data-ttu-id="7a9e6-162">在“执行包”对话框中，单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-162">On the Execute Package dialog box, click OK.</span></span>  
  
3.  <span data-ttu-id="7a9e6-163">在消息对话框中，单击“是”以打开“概述”报告。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-163">On the message dialog box click Yes to open Overview Report.</span></span>  
  
 <span data-ttu-id="7a9e6-164">包的“概述”报告随即出现，其中显示包的名称以及状态摘要。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-164">The Overview report for the package is displayed showing the name of the package and a status summary.</span></span> <span data-ttu-id="7a9e6-165">“执行概述”部分显示包中每个任务的结果，“使用的参数”部分显示包执行中使用的所有参数的名称和值（包括 VarFolderName）。</span><span class="sxs-lookup"><span data-stu-id="7a9e6-165">The Execution Overview section shows the result from each task in the package and the Parameters Used section shows the names and values of all parameters used in the package execution, including VarFolderName.</span></span>  
  
  
