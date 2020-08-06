---
title: 步骤 2：创建部署项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebfce8796f98628c2832c5ab7f4be665c7915d10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586839"
---
# <a name="step-2-creating-the-deployment-project"></a><span data-ttu-id="d0cb6-102">步骤 2：创建部署项目</span><span class="sxs-lookup"><span data-stu-id="d0cb6-102">Step 2: Creating the Deployment Project</span></span>
  <span data-ttu-id="d0cb6-103">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中，可部署的单元是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-103">In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the deployable unit is an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="d0cb6-104">必须先创建一个新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，再将所有包和要与包一起部署的任何辅助文件添加到该项目，才能部署包。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-104">Before you can deploy packages, you must create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and add all the packages and any ancillary files that you want to deploy with the packages to that project.</span></span>  
  
### <a name="to-create-the-integration-services-project"></a><span data-ttu-id="d0cb6-105">创建 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="d0cb6-105">To create the Integration Services project</span></span>  
  
1.  <span data-ttu-id="d0cb6-106">单击“开始”  ，依次指向“所有程序”  和“Microsoft SQL Server”  ，然后依次单击“SQL Server”和“SQL Server Data Tools”  。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL ServerSQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="d0cb6-107">在“文件”  菜单上，指向“新建”  ，然后单击“项目”  创建新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-107">On the **File** menu, point to **New**, and then click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="d0cb6-108">在“新建项目”对话框的“模板”窗格中，选择“Integration Services 项目”。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-108">In the **New Project** dialog box, select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="d0cb6-109">在“名称”  框中，将默认名称更改为“Deployment Tutorial”  。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-109">In the **Name** box, change the default name to **Deployment Tutorial**.</span></span> <span data-ttu-id="d0cb6-110">或者，清除“创建解决方案的目录”  复选框。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-110">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="d0cb6-111">接受默认位置，或单击“浏览”  找到要使用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-111">Accept the default location, or click **Browse** to locate the folder you want to use.</span></span>  
  
6.  <span data-ttu-id="d0cb6-112">在“项目位置”  对话框中，单击文件夹，再单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-112">In the **Project Location** dialog box, click the folder, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="d0cb6-113">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="d0cb6-113">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="d0cb6-114">默认情况下，将创建一个名为 Package.dtsx 的空包，并将该包添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-114">By default, an empty package, named Package.dtsx, is created and added to your project.</span></span> <span data-ttu-id="d0cb6-115">但是您将不使用此包；相反您将现有的包添加到项目。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-115">However, you will not use this package; instead, you will add existing packages to the project.</span></span> <span data-ttu-id="d0cb6-116">由于项目中的所有包都包括在部署中，因此您应该删除 Package.dtsx。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-116">Because all the packages in a project will be included in the deployment, you should delete Package.dtsx.</span></span> <span data-ttu-id="d0cb6-117">若要删除它，右键单击它，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-117">To delete it, right-click it, and then click **Delete**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d0cb6-118">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d0cb6-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d0cb6-119">步骤 3：添加包和其他文件</span><span class="sxs-lookup"><span data-stu-id="d0cb6-119">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
<span data-ttu-id="d0cb6-120">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d0cb6-120">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d0cb6-121">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="d0cb6-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d0cb6-122">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="d0cb6-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d0cb6-123">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="d0cb6-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cb6-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0cb6-124">See Also</span></span>  
 [<span data-ttu-id="d0cb6-125">Integration Services (SSIS) 项目</span><span class="sxs-lookup"><span data-stu-id="d0cb6-125">Integration Services &#40;SSIS&#41; Projects</span></span>](integration-services-ssis-projects-and-solutions.md)  
  
  
