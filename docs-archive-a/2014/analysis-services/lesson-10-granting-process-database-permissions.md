---
title: 授予处理数据库权限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6ada30e3fb509bd1ffd210485ce0e34b7bf86fb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577036"
---
# <a name="granting-process-database-permissions"></a><span data-ttu-id="98d3b-102">授予处理数据库权限</span><span class="sxs-lookup"><span data-stu-id="98d3b-102">Granting Process Database Permissions</span></span>
  <span data-ttu-id="98d3b-103">在安装 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例后，该实例中 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器管理员角色的所有成员都将具有在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例中执行任何任务的服务器范围权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-103">After you install an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], all members of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server administrator role in that instance have server-wide permissions to perform any task within the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="98d3b-104">默认情况下，其他用户都不具有在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例中管理或查看任何对象的任何权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-104">By default, no other users have any permission to administer or view any objects in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

 <span data-ttu-id="98d3b-105">服务器管理员角色的成员可通过使用户成为该角色的成员，在服务器范围的基础上授予用户管理访问权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-105">A member of the server administrator role can grant users administrative access on a server-wide basis by making them members of the role.</span></span> <span data-ttu-id="98d3b-106">通过在数据库级别授予用户有限或完整的管理或访问权限，服务器管理员角色的成员还可以在更为有限的基础上授予用户访问权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-106">A member of the server administrator role can also grant users access on a more limited basis by granting them limited or complete administrative or access permissions at the database level.</span></span> <span data-ttu-id="98d3b-107">有限的管理权限包括在数据库、多维数据集或维度级别处理或读取定义的权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-107">Limited administrative permissions include process or read definition permissions at the database, cube, or dimension level.</span></span>

 <span data-ttu-id="98d3b-108">在此主题的任务中，您将定义“Process Database Objects”安全角色，该角色授予其成员处理所有数据库对象的权限，但没有查看数据库中的数据的权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-108">In the tasks in this topic, you will define a Process Database Objects security role that grants members of the role permission to process all database objects, but no permission to view data within the database.</span></span>

## <a name="defining-a-process-database-objects-security-role"></a><span data-ttu-id="98d3b-109">定义“Process Database Objects”安全角色</span><span class="sxs-lookup"><span data-stu-id="98d3b-109">Defining a Process Database Objects Security Role</span></span>

1.  <span data-ttu-id="98d3b-110">在解决方案资源管理器中，右键单击“角色”\*\*\*\*，然后单击“新建角色”\*\*\*\* 以便打开角色设计器。</span><span class="sxs-lookup"><span data-stu-id="98d3b-110">In Solution Explorer, right-click **Roles** and then click **New Role** to open the Role Designer.</span></span>

2.  <span data-ttu-id="98d3b-111">单击“处理数据库”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="98d3b-111">Click the **Process database** check box.</span></span>

3.  <span data-ttu-id="98d3b-112">在属性窗口中，将此新角色的 "**名称**" 属性更改为 `Process Database Objects Role` 。</span><span class="sxs-lookup"><span data-stu-id="98d3b-112">In the Properties window, change the **Name** property for this new role to `Process Database Objects Role`.</span></span>

     <span data-ttu-id="98d3b-113">![角色设计器](../../2014/tutorials/media/l10-security-1.png "角色设计器")</span><span class="sxs-lookup"><span data-stu-id="98d3b-113">![Role Designer](../../2014/tutorials/media/l10-security-1.png "Role Designer")</span></span>

4.  <span data-ttu-id="98d3b-114">切换到角色设计器的“成员身份”\*\*\*\* 选项卡，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3b-114">Switch to the **Membership** tab of Role Designer and click **Add**.</span></span>

5.  <span data-ttu-id="98d3b-115">输入将是此角色的成员的 Windows 域用户或组的帐户。</span><span class="sxs-lookup"><span data-stu-id="98d3b-115">Enter the accounts of the Windows domain users or groups who will be members of this role.</span></span> <span data-ttu-id="98d3b-116">单击“检查名称”\*\*\*\* 以便验证帐户信息，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3b-116">Click **Check Names** to verify the account information, and then click **OK**.</span></span>

6.  <span data-ttu-id="98d3b-117">切换到角色设计器的“多维数据集”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="98d3b-117">Switch to the **Cubes** tab of Role Designer.</span></span>

     <span data-ttu-id="98d3b-118">注意，此角色的成员有处理此数据库的权限，但不具有访问 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集中的数据的权限，也不具有本地多维数据集/钻取访问权限，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="98d3b-118">Notice that members of this role have permissions to process this database, but have no permission to access the data in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube and have no local cube/drillthrough access, as shown in the following image.</span></span>

     <span data-ttu-id="98d3b-119">![角色设计器的“多维数据集”选项卡](../../2014/tutorials/media/l10-security-2.png "角色设计器的“多维数据集”选项卡")</span><span class="sxs-lookup"><span data-stu-id="98d3b-119">![Cubes tab of Role Designer](../../2014/tutorials/media/l10-security-2.png "Cubes tab of Role Designer")</span></span>

7.  <span data-ttu-id="98d3b-120">切换到角色设计器的“维度”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="98d3b-120">Switch to the **Dimensions** tab of Role Designer.</span></span>

     <span data-ttu-id="98d3b-121">注意，此角色的成员有权处理此数据库中的所有维度对象，并且在默认情况下，对 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 数据库中的每个维度对象有读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="98d3b-121">Notice that members of this role have permissions to process all dimension objects in this database, and, by default, have read permissions to access each dimension object in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial database.</span></span>

8.  <span data-ttu-id="98d3b-122">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3b-122">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

     <span data-ttu-id="98d3b-123">现在，您已经成功定义和部署了“Process Database Objects”安全角色。</span><span class="sxs-lookup"><span data-stu-id="98d3b-123">You have now successfully defined and deployed the Process Database Objects security role.</span></span> <span data-ttu-id="98d3b-124">将多维数据集部署到生产环境之后，所部署的多维数据集的管理员可以根据需要向此角色中添加用户，以便将处理责任委派给具体用户。</span><span class="sxs-lookup"><span data-stu-id="98d3b-124">After a cube is deployed to the production environment, the administrators of the deployed cube can add users to this role as required to delegate processing responsibilities to specific users.</span></span>

> [!NOTE]
>  <span data-ttu-id="98d3b-125">通过下载和安装示例，可以获得第 10 课中使用的完整项目。</span><span class="sxs-lookup"><span data-stu-id="98d3b-125">A completed project for Lesson 10 is available by downloading and installing the samples.</span></span> <span data-ttu-id="98d3b-126">有关详细信息，请参阅[安装 Analysis Services 多维建模教程的示例数据和项目](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="98d3b-126">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98d3b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98d3b-127">See Also</span></span>
 [<span data-ttu-id="98d3b-128">角色和权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="98d3b-128">Roles and Permissions &#40;Analysis Services&#41;</span></span>](multidimensional-models/roles-and-permissions-analysis-services.md)


