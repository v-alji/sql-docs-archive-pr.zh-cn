---
title: 创建 Analysis Services 项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 065fdc60-1791-4e27-9ed5-51d751b3f8c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50640dd7821943dfc3914326f7e8cba32253d307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577048"
---
# <a name="creating-an-analysis-services-project"></a><span data-ttu-id="577f7-102">创建 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="577f7-102">Creating an Analysis Services Project</span></span>
  <span data-ttu-id="577f7-103">在下面的任务中，您将使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Analysis Services Tutorial` 根据项目模板创建名为的新项目 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="577f7-103">In the following task, you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project named `Analysis Services Tutorial`, based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Project template.</span></span> <span data-ttu-id="577f7-104">“ \*\* 项目”是相关对象的集合。</span><span class="sxs-lookup"><span data-stu-id="577f7-104">A *project* is a collection of related objects.</span></span> <span data-ttu-id="577f7-105">项目存在于解决方案中，而解决方案包括一个或多个项目。</span><span class="sxs-lookup"><span data-stu-id="577f7-105">Projects exist within a solution, which includes one or more projects.</span></span> <span data-ttu-id="577f7-106">有关详细信息，请参阅 [创建 Analysis Services 项目 (SSDT)](multidimensional-models/create-an-analysis-services-project-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="577f7-106">For more information, see [Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project"></a><span data-ttu-id="577f7-107">创建新的 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="577f7-107">To create a new Analysis Services project</span></span>  
  
1.  <span data-ttu-id="577f7-108">单击 **“开始”**，依次指向 **“所有程序”** 和 **Microsoft SQL Server 2012**，然后单击 **SQL Server Data Tools**。</span><span class="sxs-lookup"><span data-stu-id="577f7-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
     <span data-ttu-id="577f7-109">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 开发环境将打开。</span><span class="sxs-lookup"><span data-stu-id="577f7-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment opens.</span></span>  
  
2.  <span data-ttu-id="577f7-110">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的起始页上，单击 **“新建项目”**。</span><span class="sxs-lookup"><span data-stu-id="577f7-110">On the Start page of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New Project**.</span></span>  
  
3.  <span data-ttu-id="577f7-111">在 **“新建项目”** 对话框中，在 **“安装的模板”** 窗格中展开 **“商业智能”**，然后选择 **Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="577f7-111">In the **New Project** dialog box, in the **Installed Templates** pane, expand **Business Intelligence**, and then select **Analysis Services**.</span></span> <span data-ttu-id="577f7-112">选择 **“Analysis Services 多维和数据挖掘项目”** 模板。</span><span class="sxs-lookup"><span data-stu-id="577f7-112">Choose the **Analysis Services Multidimensional and Data Mining Project** template.</span></span>  
  
     <span data-ttu-id="577f7-113">您将注意到在对话框底部生成了默认项目名称、位置和默认解决方案名称。</span><span class="sxs-lookup"><span data-stu-id="577f7-113">Notice the default project name, location, and the default solution name are generated in the bottom of the dialog box.</span></span> <span data-ttu-id="577f7-114">默认情况下，将为解决方案创建新的目录。</span><span class="sxs-lookup"><span data-stu-id="577f7-114">By default, a new directory is created for the solution.</span></span>  
  
4.  <span data-ttu-id="577f7-115">将项目名称更改为 `Analysis Services Tutorial` ，这也会更改 "**解决方案名称**" 框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="577f7-115">Change the project Name to `Analysis Services Tutorial`, which also changes the **Solution name** box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="577f7-116">您已成功创建了 `Analysis Services Tutorial` 项目，该项目基于 " **Analysis Services 多维和数据挖掘项目**" 模板，在同样命名的新的解决方案中 `Analysis Services Tutorial` 。</span><span class="sxs-lookup"><span data-stu-id="577f7-116">You have successfully created the `Analysis Services Tutorial` project, based on the **Analysis Services Multidimensional and Data Mining Project** template, within a new solution that is also named `Analysis Services Tutorial`.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="577f7-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="577f7-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="577f7-118">定义数据源</span><span class="sxs-lookup"><span data-stu-id="577f7-118">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="577f7-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="577f7-119">See Also</span></span>  
 <span data-ttu-id="577f7-120">[使用 SQL Server Data Tools &#40;SSDT 创建多维模型&#41;](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="577f7-120">[Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span></span>  
 [<span data-ttu-id="577f7-121">创建 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="577f7-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
