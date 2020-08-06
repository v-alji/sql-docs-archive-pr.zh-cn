---
title: 步骤 1：创建工作文件夹和环境变量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63308d406e230538e5ca8b90dbb55bb802759bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586846"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a><span data-ttu-id="b2b05-102">步骤 1：创建工作文件夹和环境变量</span><span class="sxs-lookup"><span data-stu-id="b2b05-102">Step 1: Creating Working Folders and Environment Variables</span></span>
  <span data-ttu-id="b2b05-103">在此任务中，您将创建工作文件夹 (C:\DeploymentTutorial) 和新的系统环境变量（`DataTransfer` 和 `LoadXMLData`），在后面的教程任务中您将使用它们。</span><span class="sxs-lookup"><span data-stu-id="b2b05-103">In this task, you will create the working folder (C:\DeploymentTutorial) and the new system environment variables (`DataTransfer` and `LoadXMLData`) that you will use in later tutorial tasks.</span></span>  
  
 <span data-ttu-id="b2b05-104">工作文件夹位于 C 驱动器的根目录。</span><span class="sxs-lookup"><span data-stu-id="b2b05-104">The working folder is at the root of the C drive.</span></span> <span data-ttu-id="b2b05-105">如果必须使用其他驱动器或位置，也可以使用其他驱动器或位置。</span><span class="sxs-lookup"><span data-stu-id="b2b05-105">If you must use a different drive or location, you can do that.</span></span> <span data-ttu-id="b2b05-106">但是，您需要记下此位置；然后，只要教程引用 DeploymentTutorial 工作文件夹的位置，就使用它。</span><span class="sxs-lookup"><span data-stu-id="b2b05-106">However, you need to note this location and then use it wherever the tutorial refers to the location of the DeploymentTutorial working folder.</span></span>  
  
 <span data-ttu-id="b2b05-107">在后面的课程中，需将保存到文件系统的包部署到 msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中的 sysssispackages 表中。</span><span class="sxs-lookup"><span data-stu-id="b2b05-107">In a later lesson, you will deploy packages that are saved to the file system to the sysssispackages table in the msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="b2b05-108">理想的情况是，将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包部署到其他计算机。</span><span class="sxs-lookup"><span data-stu-id="b2b05-108">Ideally you will deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to a different computer.</span></span> <span data-ttu-id="b2b05-109">如果这是不可能的，则仍可以通过将包部署到本地计算机上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例而从本教程中学到许多知识。</span><span class="sxs-lookup"><span data-stu-id="b2b05-109">If that is not possible, you can still learn a lot from doing this tutorial by deploying the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is on the local computer.</span></span> <span data-ttu-id="b2b05-110">在本地计算机和目标计算机上使用的环境变量具有相同的变量名称，但是在变量中存储的值不同。</span><span class="sxs-lookup"><span data-stu-id="b2b05-110">The environment variables that are used on the local and destination computers have the same variable names, but different values are stored in the variables.</span></span> <span data-ttu-id="b2b05-111">例如，在本地计算机上，环境变量 `DataTransfer` 的值引用 C:\DeploymentTutorial 文件夹，而在目标计算机上，环境变量 `DataTransfer` 引用 C:\DeploymentTutorialInstall 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2b05-111">For example, on the local computer, the value of the environment variable `DataTransfer` references the C:\DeploymentTutorial folder, whereas on the target computer the environment variable `DataTransfer` references the C:\DeploymentTutorialInstall folder.</span></span>  
  
 <span data-ttu-id="b2b05-112">如果计划部署到本地计算机，则只需要创建一组环境变量；但是，在执行本地部署之前，您需要将环境变量的值更新为相应值。</span><span class="sxs-lookup"><span data-stu-id="b2b05-112">If you plan to deploy to the local computer, you need to create only one set of environment variables; however, you will need to update the value of the environment variables to an appropriate value before you do the local deployment.</span></span>  
  
 <span data-ttu-id="b2b05-113">如果计划将包部署到其他计算机，则必须创建两组环境变量：一组用于本地计算机，另一组用于目标计算机。</span><span class="sxs-lookup"><span data-stu-id="b2b05-113">If you plan to deploy the packages to a different computer, you must create two sets of environment variables: one set for the local computer, and one set for the destination computer.</span></span> <span data-ttu-id="b2b05-114">您能够眼下只为源计算机创建变量，稍后再为目标计算机创建变量；但是要在目标计算机上安装包，您必须先使文件夹和环境变量在该计算机上都可用。</span><span class="sxs-lookup"><span data-stu-id="b2b05-114">You can create only the variables for the source computer now, and create the variables for the destination computer later, but you must have both the folder and environment variables available on the destination computer before you can install the packages on that computer.</span></span>  
  
### <a name="to-create-the-local-working-folder"></a><span data-ttu-id="b2b05-115">创建本地工作文件夹</span><span class="sxs-lookup"><span data-stu-id="b2b05-115">To create the local working folder</span></span>  
  
1.  <span data-ttu-id="b2b05-116">右键单击“开始”菜单，再单击“资源管理器”。</span><span class="sxs-lookup"><span data-stu-id="b2b05-116">Right-click the Start menu, and click Explore.</span></span>  
  
2.  <span data-ttu-id="b2b05-117">单击“本地磁盘 (C:)”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-117">Click **Local Disk (C:)**.</span></span>  
  
3.  <span data-ttu-id="b2b05-118">在“文件”  菜单上，指向“新建”  ，再单击“文件夹”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-118">On the **File** menu, point to **New**, and then click **Folder**.</span></span>  
  
4.  <span data-ttu-id="b2b05-119">将新文件夹重命名为 `DeploymentTutorial` 。</span><span class="sxs-lookup"><span data-stu-id="b2b05-119">Rename New Folder to `DeploymentTutorial`.</span></span>  
  
### <a name="to-create-local-environment-variables"></a><span data-ttu-id="b2b05-120">创建本地环境变量</span><span class="sxs-lookup"><span data-stu-id="b2b05-120">To create local environment variables</span></span>  
  
1.  <span data-ttu-id="b2b05-121">在 **“开始”** 菜单上，单击 **“控制面板”** 。</span><span class="sxs-lookup"><span data-stu-id="b2b05-121">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="b2b05-122">在控制面板中，双击“系统”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-122">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="b2b05-123">在 **“系统属性”** 对话框中，单击 **“高级”** 选项卡，再单击 **“环境变量”** 。</span><span class="sxs-lookup"><span data-stu-id="b2b05-123">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="b2b05-124">在“环境变量”  对话框的“系统变量”  框架中，单击“新建”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-124">In the **Environment Variables** dialog box, in the **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="b2b05-125">在 "**新建系统变量**" 对话框中，在 "变量 `DataTransfer` **名**" 框中键入，然后 `C:\DeploymentTutorial\datatransferconfig.dtsconfig` 在 "**变量值**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="b2b05-125">In the **New System Variable** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorial\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="b2b05-126">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b2b05-126">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="b2b05-127">再次单击 "**新建**"，然后在 "变量 `LoadXMLData` **名称**" 框和 `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` "**变量值**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="b2b05-127">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="b2b05-128">单击“确定”  退出“环境变量”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b2b05-128">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="b2b05-129">单击“确定”  退出“系统属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b2b05-129">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="b2b05-130">（可选）重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="b2b05-130">Optionally, restart your computer.</span></span> <span data-ttu-id="b2b05-131">如果不重新启动计算机，则在包配置向导中将不显示新变量的名称，但是您仍可以使用它。</span><span class="sxs-lookup"><span data-stu-id="b2b05-131">If you do not restart the computer, the name of the new variable will not be displayed in the Package Configuration Wizard, but you can still use it.</span></span>  
  
### <a name="to-create-destination-environment-variables"></a><span data-ttu-id="b2b05-132">创建目标环境变量</span><span class="sxs-lookup"><span data-stu-id="b2b05-132">To create destination environment variables</span></span>  
  
1.  <span data-ttu-id="b2b05-133">在 **“开始”** 菜单上，单击 **“控制面板”** 。</span><span class="sxs-lookup"><span data-stu-id="b2b05-133">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="b2b05-134">在控制面板中，双击“系统”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-134">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="b2b05-135">在 **“系统属性”** 对话框中，单击 **“高级”** 选项卡，再单击 **“环境变量”** 。</span><span class="sxs-lookup"><span data-stu-id="b2b05-135">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="b2b05-136">在“环境变量”  对话框的“系统变量”  框架中，单击“新建”  。</span><span class="sxs-lookup"><span data-stu-id="b2b05-136">In the **Environment Variables** dialog box, in **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="b2b05-137">在 "**新建系统变量**" 对话框中，在 "变量 `DataTransfer` **名称**" 框中键入，然后 `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` 在 "**变量值**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="b2b05-137">In the **New System Variables** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="b2b05-138">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b2b05-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="b2b05-139">再次单击 "**新建**"，然后在 "变量 `LoadXMLData` **名称**" 框和 `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` "**变量值**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="b2b05-139">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="b2b05-140">单击“确定”  退出“环境变量”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b2b05-140">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="b2b05-141">单击“确定”  退出“系统属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b2b05-141">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="b2b05-142">（可选）重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="b2b05-142">Optionally, restart your computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b2b05-143">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="b2b05-143">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b2b05-144">步骤 2：创建部署项目</span><span class="sxs-lookup"><span data-stu-id="b2b05-144">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
<span data-ttu-id="b2b05-145">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b2b05-145">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b2b05-146">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b2b05-146">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b2b05-147">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b2b05-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b2b05-148">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b2b05-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
