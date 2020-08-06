---
title: Integration Services 部署向导 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9afdc529baa4546f126eb67456927e770cb345dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691802"
---
# <a name="integration-services-deployment-wizard"></a><span data-ttu-id="8fb76-102">Integration Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="8fb76-102">Integration Services Deployment Wizard</span></span>
  <span data-ttu-id="8fb76-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 部署向导使用项目部署模型将项目部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例上的 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="8fb76-103">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard deploys projects to the SSISDB catalog on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance using the project deployment model.</span></span>  
  
 <span data-ttu-id="8fb76-104">若要 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 从中打开的项目启动部署向导 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，请从 "**项目**" 菜单中选择 "**部署**"。</span><span class="sxs-lookup"><span data-stu-id="8fb76-104">To start the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard from an open project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], select **Deploy** from the **Project** menu.</span></span> <span data-ttu-id="8fb76-105">若要在中启动该向导 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，请在对象资源管理器中展开**Integration Services 目录**  >  **SSISDB**节点，右键单击 "**项目**" 文件夹，然后单击 "**部署项目**"。</span><span class="sxs-lookup"><span data-stu-id="8fb76-105">To start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** > **SSISDB** node in Object Explorer, right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
 <span data-ttu-id="8fb76-106">该向导继续执行以下四个步骤。</span><span class="sxs-lookup"><span data-stu-id="8fb76-106">The wizard proceeds through the following four steps.</span></span> <span data-ttu-id="8fb76-107">单击 "**下一**步" 转到下一步，或单击 "**上**一步" 返回上一步。</span><span class="sxs-lookup"><span data-stu-id="8fb76-107">Click **Next** to move to the next step, or **Previous** to return to the previous step.</span></span>  
  
1.  <span data-ttu-id="8fb76-108">**选择源**-选择 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 要部署的项目。</span><span class="sxs-lookup"><span data-stu-id="8fb76-108">**Select Source** - Select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that you want to deploy.</span></span>  
  
2.  <span data-ttu-id="8fb76-109">**选择目标**-选择项目目标。</span><span class="sxs-lookup"><span data-stu-id="8fb76-109">**Select Destination** - Select the project destination.</span></span>  
  
3.  <span data-ttu-id="8fb76-110">**查看**-显示你的选择。</span><span class="sxs-lookup"><span data-stu-id="8fb76-110">**Review** - Displays your selections.</span></span>  
  
4.  <span data-ttu-id="8fb76-111">**部署/结果**-部署项目并显示结果。</span><span class="sxs-lookup"><span data-stu-id="8fb76-111">**Deploy/Results** - Deploys the project and displays the results.</span></span>  
  
## <a name="select-source"></a><span data-ttu-id="8fb76-112">选择源</span><span class="sxs-lookup"><span data-stu-id="8fb76-112">Select Source</span></span>  
 <span data-ttu-id="8fb76-113">若要部署你创建的项目部署文件，请选择 "**项目部署文件**" 并输入 .ispac 文件的路径，或者单击 "**浏览**" 在项目文件夹中查找它 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8fb76-113">To deploy a project deployment file that you created, select **Project deployment file** and enter the path to the .ispac file or click **Browse** to find it in the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project folder.</span></span> <span data-ttu-id="8fb76-114">若要部署位于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目录中的项目，请选择 **“Integration Services 目录”**，然后输入目录中指向该项目的服务器名称和路径。</span><span class="sxs-lookup"><span data-stu-id="8fb76-114">To deploy a project that resides in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, select **Integration Services catalog**, and then enter the server name and the path to the project in the catalog.</span></span>  
  
 <span data-ttu-id="8fb76-115">如果在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中启动该向导，则默认情况下该向导选择打开的项目作为源并跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="8fb76-115">If you start the wizard in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], then by default the wizard selects the open project as the source and skips this step.</span></span> <span data-ttu-id="8fb76-116">若要返回此步骤并选择其他源，请单击 "**上一**步" 或单击左窗格中的 "**选择源**"。</span><span class="sxs-lookup"><span data-stu-id="8fb76-116">To return to this step and select a different source, click **Previous** or click **Select Source** in the left pane.</span></span>  
  
## <a name="select-destination"></a><span data-ttu-id="8fb76-117">选择目标</span><span class="sxs-lookup"><span data-stu-id="8fb76-117">Select Destination</span></span>  
 <span data-ttu-id="8fb76-118">若要在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目录中选择项目的目标文件夹，请输入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例或单击 **“浏览”** 从服务器列表中选择。</span><span class="sxs-lookup"><span data-stu-id="8fb76-118">To select the destination folder for the project in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or click **Browse** to select from a list of servers.</span></span> <span data-ttu-id="8fb76-119">然后输入 SSISDB 中的项目路径或单击 **“浏览”** 以选择此路径。</span><span class="sxs-lookup"><span data-stu-id="8fb76-119">Enter the project path in SSISDB or click **Browse** to select it.</span></span>  
  
 <span data-ttu-id="8fb76-120">如果在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中启动该向导，则默认情况下该向导选择连接的服务器实例并输入所选项目的路径。</span><span class="sxs-lookup"><span data-stu-id="8fb76-120">If you start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], then by default the wizard selects the connected server instance and enters the path to the selected project.</span></span> <span data-ttu-id="8fb76-121">您可以更改这些值，以将项目部署到其他位置。</span><span class="sxs-lookup"><span data-stu-id="8fb76-121">You can change these values to deploy the project to a different location.</span></span>  
  
## <a name="review"></a><span data-ttu-id="8fb76-122">审阅</span><span class="sxs-lookup"><span data-stu-id="8fb76-122">Review</span></span>  
 <span data-ttu-id="8fb76-123">该向导允许您在部署项目前检查所选的设置。</span><span class="sxs-lookup"><span data-stu-id="8fb76-123">The wizard allows you to review the settings you have selected before deploying the project.</span></span> <span data-ttu-id="8fb76-124">可以通过单击 **“上一步”** 或单击左窗格中的任意步骤来更改所做的选择。</span><span class="sxs-lookup"><span data-stu-id="8fb76-124">You can change your selections by clicking **Previous**, or by clicking any of the steps in the left pane.</span></span>  
  
## <a name="deployresults"></a><span data-ttu-id="8fb76-125">部署/结果</span><span class="sxs-lookup"><span data-stu-id="8fb76-125">Deploy/Results</span></span>  
 <span data-ttu-id="8fb76-126">当你在 "**检查**" 页中单击 "**部署**" 时 **，将部署**项目，并显示每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="8fb76-126">When you click **Deploy** from the **Review** page, the project is deployed and the **Results** page displays the success or failure of each action.</span></span> <span data-ttu-id="8fb76-127">如果操作失败，单击 **“结果”** 列中的 **“失败”** 可以显示错误说明。</span><span class="sxs-lookup"><span data-stu-id="8fb76-127">If the action fails, click the **Failed** in the **Result** column to display an explanation of the error.</span></span> <span data-ttu-id="8fb76-128">单击 "**保存报告 ...** " 以将结果保存到 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="8fb76-128">Click **Save Report...** to save the results to an XML file.</span></span>  
  
 <span data-ttu-id="8fb76-129">单击“关闭”退出向导。</span><span class="sxs-lookup"><span data-stu-id="8fb76-129">Click **Close** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb76-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fb76-130">See Also</span></span>  
 <span data-ttu-id="8fb76-131">[将项目部署到 Integration Services 服务器](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="8fb76-131">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 [<span data-ttu-id="8fb76-132">项目和包的部署</span><span class="sxs-lookup"><span data-stu-id="8fb76-132">Deployment of Projects and Packages</span></span>](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
