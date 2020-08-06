---
title: 步骤 3：添加包和其他文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d5ddcb6315576558161119a8774bccbd63fa5844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586840"
---
# <a name="step-3-adding-packages-and-other-files"></a><span data-ttu-id="91201-102">步骤 3：添加包和其他文件</span><span class="sxs-lookup"><span data-stu-id="91201-102">Step 3: Adding Packages and Other Files</span></span>
  <span data-ttu-id="91201-103">在此任务中，将现有的包、支持单个包的辅助文件以及自述文件添加到您在上一任务中创建的 Deployment Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="91201-103">In this task, you will add existing packages, ancillary files that support individual packages, and a Readme to the Deployment Tutorial project that you created in the previous task.</span></span> <span data-ttu-id="91201-104">例如，您将添加一个包含包数据的 XML 数据文件和一个提供有关项目中所有包的自述文件信息的文本文件。</span><span class="sxs-lookup"><span data-stu-id="91201-104">For example, you will add an XML data file that contains the data for a package and a text file that provides Readme information about all the packages in the project.</span></span>  
  
 <span data-ttu-id="91201-105">在将包部署到测试环境或生产环境时，通常在部署中不包括数据文件，而是改用配置来更新数据源的路径，以访问数据文件或数据库的测试版本或生产版本。</span><span class="sxs-lookup"><span data-stu-id="91201-105">When you deploy packages to a test or production environment, you typically do not include the data files in the deployment, but instead use configurations to update the paths of the data sources to access test or production versions of the data files or databases.</span></span> <span data-ttu-id="91201-106">为了便于学习，本教程将数据文件包括在包部署中。</span><span class="sxs-lookup"><span data-stu-id="91201-106">For instructional purposes, this tutorial includes data files in the package deployment.</span></span>  
  
 <span data-ttu-id="91201-107">在您安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 示例时，将安装包和包所用的示例数据。</span><span class="sxs-lookup"><span data-stu-id="91201-107">The packages and the sample data that the packages use are installed when you install the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="91201-108">将下列包添加到 Deployment Tutorial 项目：</span><span class="sxs-lookup"><span data-stu-id="91201-108">You will add the following packages to the Deployment Tutorial project:</span></span>  
  
-   <span data-ttu-id="91201-109">**DataTransfer。**</span><span class="sxs-lookup"><span data-stu-id="91201-109">**DataTransfer.**</span></span> <span data-ttu-id="91201-110">它是从平面文件提取数据、计算列值以便按条件保留数据集中的行、再将数据加载到 AdventureWorks 数据库中的表的基本包。</span><span class="sxs-lookup"><span data-stu-id="91201-110">Basic package that extracts data from a flat file, evaluates column values to conditionally keep rows in the dataset, and loads data into a table in the AdventureWorks database.</span></span>  
  
-   <span data-ttu-id="91201-111">**LoadXMLData。**</span><span class="sxs-lookup"><span data-stu-id="91201-111">**LoadXMLData.**</span></span> <span data-ttu-id="91201-112">它是从 XML 数据文件提取数据、计算并聚合列值、再将数据加载到 AdventureWorks 数据库中的表的数据传输包。</span><span class="sxs-lookup"><span data-stu-id="91201-112">Data-transfer package that extracts data from an XML data file, evaluates and aggregates column values, and loads data into a table in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="91201-113">若要支持这些包的部署，请将下列辅助文件添加到 Deployment Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="91201-113">To support the deployment of these packages, you will add the following ancillary files to the Deployment Tutorial project.</span></span>  
  
|<span data-ttu-id="91201-114">程序包</span><span class="sxs-lookup"><span data-stu-id="91201-114">Package</span></span>|<span data-ttu-id="91201-115">文件</span><span class="sxs-lookup"><span data-stu-id="91201-115">File</span></span>|  
|-------------|----------|  
|<span data-ttu-id="91201-116">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="91201-116">DataTransfer</span></span>|<span data-ttu-id="91201-117">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="91201-117">NewCustomers.txt</span></span>|  
|<span data-ttu-id="91201-118">LoadXMLData</span><span class="sxs-lookup"><span data-stu-id="91201-118">LoadXMLData</span></span>|<span data-ttu-id="91201-119">orders.xml 和 orders.xsd</span><span class="sxs-lookup"><span data-stu-id="91201-119">orders.xml and orders.xsd</span></span>|  
  
 <span data-ttu-id="91201-120">还将添加一个自述文件，该文件是提供有关 Deployment Tutorial 项目的信息的文本文件。</span><span class="sxs-lookup"><span data-stu-id="91201-120">You will also add a Readme, which is a text file that provides information about the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="91201-121">在下列过程中使用的路径假定， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 示例安装在默认位置 [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="91201-121">The paths used in the following procedures assume that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples were installed in the default location, [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)].</span></span> <span data-ttu-id="91201-122">如果将这些示例安装到其他位置，则应该使用该位置，而不是上述过程中的位置。</span><span class="sxs-lookup"><span data-stu-id="91201-122">If you installed the samples to a different location, you should use that location instead in the procedures.</span></span>  
  
 <span data-ttu-id="91201-123">在下一任务中，将配置添加到 DataTransfer 和 LoadXMLData 包。</span><span class="sxs-lookup"><span data-stu-id="91201-123">In the next task, you will add configurations to the DataTransfer and LoadXMLData packages.</span></span> <span data-ttu-id="91201-124">所有配置都存储在 XML 文件中，而且您将使用系统环境变量指定这些文件的位置。</span><span class="sxs-lookup"><span data-stu-id="91201-124">All configurations are stored in XML files, and you will use a system environment variable to specify the location of the files.</span></span> <span data-ttu-id="91201-125">创建配置文件后，将它们添加到项目。</span><span class="sxs-lookup"><span data-stu-id="91201-125">After you create the configuration files, you will add them to the project.</span></span>  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a><span data-ttu-id="91201-126">将包添加到 Deployment Tutorial 项目</span><span class="sxs-lookup"><span data-stu-id="91201-126">To add packages to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="91201-127">如果 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 尚未打开，请单击“开始”  ，依次指向“所有程序”  和“Microsoft SQL Server”  ，再单击“SQL Server Data Tools”  。</span><span class="sxs-lookup"><span data-stu-id="91201-127">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="91201-128">在“文件”  菜单上，依次单击“打开”  、“项目/解决方案”  、“Deployment Tutorial”  文件夹，然后再次单击“打开”  ，最后双击“Deployment Tutorial.sln”  。</span><span class="sxs-lookup"><span data-stu-id="91201-128">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="91201-129">在解决方案资源管理器中，右键单击“Deployment Tutorial”，再单击“添加”  ，然后单击“现有包”  。</span><span class="sxs-lookup"><span data-stu-id="91201-129">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Package**.</span></span>  
  
4.  <span data-ttu-id="91201-130">在“添加现有包的副本”  对话框的“包位置”  中，选择“文件系统”  。</span><span class="sxs-lookup"><span data-stu-id="91201-130">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
5.  <span data-ttu-id="91201-131">单击“浏览(…)”按钮，导航到 C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages，选择“DataTransfer.dtsx”，再单击“打开”    。</span><span class="sxs-lookup"><span data-stu-id="91201-131">Click the browse **(...)** button, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages, select **DataTransfer.dtsx**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="91201-132">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="91201-132">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="91201-133">重复步骤 3-6，但这一次添加的是 LoadXMLData.dtsx（它位于 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages 中）。</span><span class="sxs-lookup"><span data-stu-id="91201-133">Repeat steps 3 - 6, and this time add LoadXMLData.dtsx, which is found in C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages.</span></span>  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a><span data-ttu-id="91201-134">将辅助文件添加到 Deployment Tutorial 项目</span><span class="sxs-lookup"><span data-stu-id="91201-134">To add ancillary files to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="91201-135">在解决方案资源管理器中，右键单击“Deployment Tutorial”，再单击“添加”  ，然后单击“现有项”  。</span><span class="sxs-lookup"><span data-stu-id="91201-135">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="91201-136">在“添加现有项 - Deployment Tutorial”  对话框中，导航到 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data，选择 orders.xml、orders.xsd 和 NewCustomers.txt，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="91201-136">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data, select orders.xml, orders.xsd, and NewCustomers.txt, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="91201-137">在“添加现有项 - Deployment Tutorial”  对话框中，导航到 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\，选择 Readme.txt，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="91201-137">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\, select Readme.txt and click **Add**.</span></span>  
  
4.  <span data-ttu-id="91201-138">在“文件”菜单上，单击“全部保存”  。</span><span class="sxs-lookup"><span data-stu-id="91201-138">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="91201-139">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="91201-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="91201-140">步骤 4：添加包配置</span><span class="sxs-lookup"><span data-stu-id="91201-140">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
<span data-ttu-id="91201-141">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="91201-141">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="91201-142">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="91201-142">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="91201-143">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="91201-143">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="91201-144">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="91201-144">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
