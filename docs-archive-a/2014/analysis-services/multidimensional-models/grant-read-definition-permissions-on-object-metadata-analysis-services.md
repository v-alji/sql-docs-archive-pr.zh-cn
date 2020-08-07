---
title: 授予对对象元数据的读取定义权限 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e3b18b913ed4b678baf0969b006f1386ba748e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587635"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a><span data-ttu-id="387cc-102">授予对象元数据的读取定义权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="387cc-102">Grant read definition permissions on object metadata (Analysis Services)</span></span>
  <span data-ttu-id="387cc-103">读取所选对象的对象定义或元数据的权限使得管理员能够授予查看对象信息的权限，而不用同时授予修改对象定义、修改对象结构或查看对象的实际数据的权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-103">Permission to read an object definition, or metadata, on selected objects lets an administrator grant permission to view object information, without also granting permission to modify the object's definition, modify the object's structure, or view the actual data for the object.</span></span> <span data-ttu-id="387cc-104">`Read Definition`可以在数据库、数据源、维度、挖掘结构和挖掘模型级别授予权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-104">`Read Definition` permissions can be granted at the database, data source, dimension, mining structure, and mining model levels.</span></span> <span data-ttu-id="387cc-105">如果需要 `Read Definition` 多维数据集的权限，则必须 `Read Definition` 为数据库启用。请记住，权限是累加的。</span><span class="sxs-lookup"><span data-stu-id="387cc-105">If you require `Read Definition` permissions for a cube, you must enable `Read Definition` for the database.Remember that permissions are additive.</span></span> <span data-ttu-id="387cc-106">例如，一个角色授予读取多维数据集的元数据的权限，同时，另一个角色向同一个用户授予读取维度元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-106">For example, one role grants permission to read the metadata for a cube, while a second role grants the same user permission to read the metadata for a dimension.</span></span> <span data-ttu-id="387cc-107">两个不同角色的权限合并授予用户在该数据库内的读取多维数据集元数据和维度元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-107">The permissions from the two different roles combine to give the user permission to both read metadata for the cube and the metadata for the dimension within that database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="387cc-108">读取数据库元数据的权限是使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 连接到 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]数据库时所需的最低权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-108">Permission to read a database's metadata is the minimum permission required to connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database using either [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="387cc-109">可读取元数据的用户还可以使用 DISCOVER_XML_METADATA 架构行集来查询对象并查看其元数据。</span><span class="sxs-lookup"><span data-stu-id="387cc-109">A user who has permission to read metadata can also use the DISCOVER_XML_METADATA schema rowset to query the object and view its metadata.</span></span> <span data-ttu-id="387cc-110">有关详细信息，请参阅 [DISCOVER_XML_METADATA 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)。</span><span class="sxs-lookup"><span data-stu-id="387cc-110">For more information, see [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).</span></span>  
  
## <a name="set-read-definition-permissions-on-a-database"></a><span data-ttu-id="387cc-111">设置数据库的读取定义权限</span><span class="sxs-lookup"><span data-stu-id="387cc-111">Set read definition permissions on a database</span></span>  
 <span data-ttu-id="387cc-112">授予读取数据库元数据的权限便同时授予了读取数据库中所有对象的元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-112">Granting permission to read database metadata also grants permission to read the metadata of all objects in the database.</span></span>  
  
 <span data-ttu-id="387cc-113">建议你在为 `Read Definition` 专用处理设置角色时，包括数据库级别的权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-113">We suggest that you include the `Read Definition` permission at the database level whenever you are setting up roles for dedicated processing.</span></span> <span data-ttu-id="387cc-114">`Read Definition`使非管理员能够在中查看模型的对象层次结构 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，并导航到各个对象进行后续处理。</span><span class="sxs-lookup"><span data-stu-id="387cc-114">Having `Read Definition` allows non-administrators to view a model's object hierarchy in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and navigate to individual objects for subsequent processing.</span></span>  
  
1.  <span data-ttu-id="387cc-115">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到实例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，在对象资源管理器中展开相应数据库的 "**角色**"，然后单击 "数据库角色" (或 "创建新的数据库角色) "。</span><span class="sxs-lookup"><span data-stu-id="387cc-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="387cc-116">在 "**常规**" 选项卡上，选择 `Read Definition` 选项。</span><span class="sxs-lookup"><span data-stu-id="387cc-116">On the **General** tab, select the `Read Definition` option.</span></span>  
  
3.  <span data-ttu-id="387cc-117">在“成员身份” \*\*\*\* 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="387cc-117">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="387cc-118">单击“确定” \*\*\*\* ，完成角色创建。</span><span class="sxs-lookup"><span data-stu-id="387cc-118">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a><span data-ttu-id="387cc-119">设置单个对象的读取定义权限</span><span class="sxs-lookup"><span data-stu-id="387cc-119">Set read definition permissions on individual objects</span></span>  
  
1.  <span data-ttu-id="387cc-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，打开“数据库”\*\*\*\* 文件夹，选择一个数据库，在对象资源管理器中展开相应数据库的“角色”\*\*\*\*，然后单击某个数据库角色（或创建新的数据库角色）。</span><span class="sxs-lookup"><span data-stu-id="387cc-120">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the **Databases** folder, select a database, expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="387cc-121">在 "**常规**" 窗格中，清除的数据库权限 `Read Definition` 。</span><span class="sxs-lookup"><span data-stu-id="387cc-121">In the **General** pane, clear the database permission for `Read Definition`.</span></span> <span data-ttu-id="387cc-122">此步骤清除了权限继承，这样便可对单个对象设置权限。</span><span class="sxs-lookup"><span data-stu-id="387cc-122">This step removes permission inheritance so that you can set permissions on individual objects.</span></span>  
  
3.  <span data-ttu-id="387cc-123">选择要为其指定属性的对象 `Read Definition` ：</span><span class="sxs-lookup"><span data-stu-id="387cc-123">Select the object for which you are specifying `Read Definition` properties:</span></span>  
  
    -   <span data-ttu-id="387cc-124">在 "**数据源**" 窗格中，单击 `Read Definition` 该数据源的复选框。</span><span class="sxs-lookup"><span data-stu-id="387cc-124">In the **Data Sources** pane, click the `Read Definition` check box for that data source.</span></span> <span data-ttu-id="387cc-125">角色成员可查看数据源的连接字符串，包括服务器名称，还可能包括用户名称。</span><span class="sxs-lookup"><span data-stu-id="387cc-125">Role members can view the connection string to the data source, including the server name and possibly the user name.</span></span> <span data-ttu-id="387cc-126">假如你想提供连接字符串信息，而不同时授予修改连接字符串或查看任何其它对象定义的权限，这时该权限可用。</span><span class="sxs-lookup"><span data-stu-id="387cc-126">This permission is available in case you want to provide connection string information, without also granting permission to modify the connection string or view the definitions of any other objects.</span></span>  
  
    -   <span data-ttu-id="387cc-127">在 "**维度**" 窗格中，单击 `Read Definition` 该维度对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="387cc-127">In the **Dimensions** pane, click the `Read Definition` check box for that dimension.</span></span> <span data-ttu-id="387cc-128">有经验的分析人员和开发人员在没有能修改定义或查看其他对象（例如，其他维度、多维数据集对象或挖掘结构和模型）定义的权限的情况下，可能需要查看定义。</span><span class="sxs-lookup"><span data-stu-id="387cc-128">Experienced analysts and developers may need to view the definition without permission to modify it or view the definitions of other objects (such as other dimensions, cube objects, or mining structures and models).</span></span>  
  
    -   <span data-ttu-id="387cc-129">在 "挖掘结构" 窗格中，单击 `Read Definition` 数据挖掘结构或模型的复选框。</span><span class="sxs-lookup"><span data-stu-id="387cc-129">In the Mining Structures pane, click the `Read Definition` check box for data mining structures or models.</span></span> <span data-ttu-id="387cc-130">`Read Definition`浏览数据模型是必需的。</span><span class="sxs-lookup"><span data-stu-id="387cc-130">`Read Definition` is required for browsing the data model.</span></span> <span data-ttu-id="387cc-131">有关详细信息，请参阅[授予数据挖掘结构和模型的权限 (Analysis Services)](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="387cc-131">See [Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) for details.</span></span>  
  
4.  <span data-ttu-id="387cc-132">在“成员身份” \*\*\*\* 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="387cc-132">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
5.  <span data-ttu-id="387cc-133">单击“确定” \*\*\*\* ，完成角色创建。</span><span class="sxs-lookup"><span data-stu-id="387cc-133">Click **OK** to finish creating the role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="387cc-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="387cc-134">See Also</span></span>  
 <span data-ttu-id="387cc-135">[授予数据库权限 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="387cc-135">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="387cc-136">授予处理权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="387cc-136">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
  
