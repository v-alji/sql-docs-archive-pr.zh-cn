---
title: 重命名多维数据库 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3974e7671aff5d1cba22b10563bbc85a129a1dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588103"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a><span data-ttu-id="fbc1e-102">重命名多维数据库 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="fbc1e-102">Rename a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="fbc1e-103">更改数据库名称的方式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 取决于连接到数据库的方式 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-103">The manner in which you change the name of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database depends upon how you connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fbc1e-104">若要更改现有数据库的名称，则必须在联机模式下进行连接。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-104">To change the name of an existing database, you must connect in online mode.</span></span> <span data-ttu-id="fbc1e-105">若要更改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中要进行实例化的对象所在数据库的名称，必须以项目模式进行连接。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-105">To change the name of the database into which objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project will be instantiated, you must connect in project mode.</span></span>  
  
### <a name="to-change-the-database-name-in-online-mode"></a><span data-ttu-id="fbc1e-106">在联机模式下更改数据库名称</span><span class="sxs-lookup"><span data-stu-id="fbc1e-106">To change the database name in online mode</span></span>  
  
1.  <span data-ttu-id="fbc1e-107">使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]，直接连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-107">Using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], connect directly to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="fbc1e-108">在解决方案资源管理器中，右键单击该数据库，再单击“编辑数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-108">In Solution Explorer, right-click the database and then click **Edit Database**.</span></span>  
  
3.  <span data-ttu-id="fbc1e-109">在 **“数据库名称”** 文本框中，更改数据库名称。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-109">In the **Database name** text box, change the database name.</span></span>  
  
4.  <span data-ttu-id="fbc1e-110">在工具栏上单击 **“保存”** 或 **“全部保存”** ，在 **“文件”** 菜单上单击 **“保存选定项”** 或 **“全部保存”** ，或者关闭 **数据库设计器** 并在出现提示时单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-110">Click **Save** or **Save All** on the toolbar, click **Save Selected Items** or **Save All** on the **File** menu, or close the **Database Designer** and then click **Save** when prompted.</span></span>  
  
     <span data-ttu-id="fbc1e-111">这样便会在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中更新数据库名称，并且会刷新解决方案资源管理器中的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-111">The database name is updated in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the database object in Solution Explorer is refreshed.</span></span>  
  
### <a name="to-change-the-database-name-in-project-mode"></a><span data-ttu-id="fbc1e-112">在项目模式下更改数据库名称</span><span class="sxs-lookup"><span data-stu-id="fbc1e-112">To change the database name in project mode</span></span>  
  
1.  <span data-ttu-id="fbc1e-113">打开 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-113">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="fbc1e-114">在解决方案资源管理器中，右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-114">In Solution Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fbc1e-115">在 **“属性页”** 对话框中，单击 **“配置属性”** 部分中的 **“部署”** 。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-115">In the **Property Pages** dialog box, click **Deployment** in the **Configuration Properties** section.</span></span>  
  
4.  <span data-ttu-id="fbc1e-116">将 **“数据库”** 属性更改为新的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-116">Change the **Database** property to the new database name.</span></span>  
  
     <span data-ttu-id="fbc1e-117">下次部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目时，会将其部署为这一新的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-117">The next time the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed, it will be deployed to this new database name.</span></span> <span data-ttu-id="fbc1e-118">如果此数据库已存在，则会将其覆盖。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-118">If this database already exists, it will be overwritten.</span></span>  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a><span data-ttu-id="fbc1e-119">使用 SQL Server Management Studio 更改数据库名称</span><span class="sxs-lookup"><span data-stu-id="fbc1e-119">To change the database name using SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="fbc1e-120">右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库并且编辑 Name 属性。</span><span class="sxs-lookup"><span data-stu-id="fbc1e-120">Right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and edit the Name property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc1e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbc1e-121">See Also</span></span>  
 <span data-ttu-id="fbc1e-122">[在 Analysis Services 中配置服务器属性](../server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="fbc1e-122">[Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="fbc1e-123">[设置多维数据库属性 &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="fbc1e-123">[Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="fbc1e-124">[配置 Analysis Services 项目属性 &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="fbc1e-124">[Configure Analysis Services Project Properties &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span></span>  
 [<span data-ttu-id="fbc1e-125">部署 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="fbc1e-125">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](deploy-analysis-services-projects-ssdt.md)  
  
  
