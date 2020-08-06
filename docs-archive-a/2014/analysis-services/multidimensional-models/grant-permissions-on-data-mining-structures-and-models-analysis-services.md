---
title: 授予对数据挖掘结构和模型的权限 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0db849551bdb38615f280b123c98f0e9d3053d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690828"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a><span data-ttu-id="e13e1-102">授予数据挖掘结构和模型的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e13e1-102">Grant permissions on data mining structures and models (Analysis Services)</span></span>
  <span data-ttu-id="e13e1-103">在默认情况下，仅 Analysis Services 服务器管理员有权限查看数据库中的数据挖掘结构或挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e13e1-103">By default, only an Analysis Services server administrator has permissions to view data mining structures or mining models in the database.</span></span> <span data-ttu-id="e13e1-104">请遵循以下说明，以向非管理员用户授予权限。</span><span class="sxs-lookup"><span data-stu-id="e13e1-104">Follow the instructions below to grant permissions to non-administrator users.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-structure"></a><span data-ttu-id="e13e1-105">设置访问挖掘结构的权限</span><span class="sxs-lookup"><span data-stu-id="e13e1-105">Set permissions to access a mining structure</span></span>  
  
1.  <span data-ttu-id="e13e1-106">在 SSMS 中，连接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="e13e1-106">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="e13e1-107">如果需要此步骤的帮助，请参阅[从客户端应用程序进行连接 (Analysis Services)](../instances/connect-from-client-applications-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e13e1-107">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with the steps.</span></span>  
  
2.  <span data-ttu-id="e13e1-108">打开“数据库” \*\*\*\* 文件夹，并在对象资源管理器中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="e13e1-108">Open the **Databases** folder, and select a database in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="e13e1-109">右键单击“角色”，然后选择“新角色”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e13e1-109">Right-click **Roles** and choose **New Role**.</span></span>  
  
4.  <span data-ttu-id="e13e1-110">在“常规页”中输入名称，并且（可选）输入描述。</span><span class="sxs-lookup"><span data-stu-id="e13e1-110">In the General page, enter a name, and optionally, a description.</span></span> <span data-ttu-id="e13e1-111">此页面也包含多个数据库权限，如完全控制、处理数据库和读取定义。</span><span class="sxs-lookup"><span data-stu-id="e13e1-111">The page also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="e13e1-112">数据挖掘访问不需要这些权限。</span><span class="sxs-lookup"><span data-stu-id="e13e1-112">None of these permissions are needed for data mining access.</span></span> <span data-ttu-id="e13e1-113">有关数据库权限的详细信息，请参阅[授予数据库权限 (Analysis Services)](grant-database-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e13e1-113">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about database permissions.</span></span>  
  
5.  <span data-ttu-id="e13e1-114">在“挖掘结构”\*\*\*\* 窗格中，为每个数据挖掘结构选择“读取”或“读/写”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e13e1-114">In the **Mining Structure** pane, select **Read** or **Read/Write**  for each data mining structure.</span></span>  
  
6.  <span data-ttu-id="e13e1-115">在“成员身份” \*\*\*\* 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="e13e1-115">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
7.  <span data-ttu-id="e13e1-116">单击“确定” \*\*\*\* ，完成角色创建。</span><span class="sxs-lookup"><span data-stu-id="e13e1-116">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-model"></a><span data-ttu-id="e13e1-117">设置访问挖掘模型的权限</span><span class="sxs-lookup"><span data-stu-id="e13e1-117">Set permissions to access a mining model</span></span>  
 <span data-ttu-id="e13e1-118">对于数据挖掘模型，角色可具有“读取”或“读/写”权限，以及允许查看和浏览基础数据的“钻取”和“读取定义”权限\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e13e1-118">For a data mining model, a role can have either **Read** or **Read/Write** permissions, as well as **Drillthrough** and **Read Definition** permissions that allow viewing and browsing the underlying data.</span></span>  
  
 <span data-ttu-id="e13e1-119">**注意** 如果对挖掘结构和挖掘模型都启用了钻取，作为拥有挖掘模型和挖掘结构钻取权限的角色成员的任何用户也可以查看挖掘结构中的列，即使那些列并未包括在挖掘模型中。</span><span class="sxs-lookup"><span data-stu-id="e13e1-119">**Note** If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model and the mining structure can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="e13e1-120">因此，若要保护敏感信息，应设置数据源视图来屏蔽个人信息，并且仅在需要时才允许对挖掘结构进行钻取访问。</span><span class="sxs-lookup"><span data-stu-id="e13e1-120">Therefore, to protect sensitive information, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
 <span data-ttu-id="e13e1-121">若要向数据库角色授予读取或读/写权限，用户必须为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器角色的成员或为拥有完全控制（管理员）权限的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="e13e1-121">To grant read or read/write permissions to a database role, a user must be a member of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server role or a member of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has Full Control (Administrator) permissions.</span></span>  
  
1.  <span data-ttu-id="e13e1-122">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到实例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，在对象资源管理器中展开相应数据库的 "**角色**"，然后单击 "数据库角色" (或 "创建新的数据库角色) "。</span><span class="sxs-lookup"><span data-stu-id="e13e1-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="e13e1-123">在“挖掘结构”窗格中的“挖掘模型”列表中找到“挖掘模型”，然后为此挖掘模型选择“读取”、“读/写”、“钻取”或“浏览”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e13e1-123">In the **Mining Structure** pane, locate the mining model in the **Mining Models** list, and then select **Read**, **Read/Write**, **Drill Through**, or **Browse** for that mining model.</span></span>  
  
3.  <span data-ttu-id="e13e1-124">在“成员身份” \*\*\*\* 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="e13e1-124">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="e13e1-125">单击“确定” \*\*\*\* ，完成角色创建。</span><span class="sxs-lookup"><span data-stu-id="e13e1-125">Click **OK** to finish creating the role.</span></span>  
  
 <span data-ttu-id="e13e1-126">若要在使用数据挖掘扩展插件 (DMX) OPENQUERY 子句的钻取查询中使用数据源，则数据库角色还需要具有读/写相应的数据源对象的权限。</span><span class="sxs-lookup"><span data-stu-id="e13e1-126">To use a data source in a drillthrough query that uses the Data Mining Extensions (DMX) OPENQUERY clause, the database role also needs read/write permission on the appropriate data source object.</span></span> <span data-ttu-id="e13e1-127">有关详细信息，请参阅[授予数据源对象的权限 (Analysis Services)](grant-permissions-on-a-data-source-object-analysis-services.md) 和 [OPENQUERY (DMX)](/sql/dmx/source-data-query-openquery)。</span><span class="sxs-lookup"><span data-stu-id="e13e1-127">For more information, see [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) and [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e13e1-128">默认情况下，将禁用使用 OPENROWSET 提交 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="e13e1-128">By default, the submission of DMX queries by using OPENROWSET is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13e1-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e13e1-129">See Also</span></span>  
 <span data-ttu-id="e13e1-130">[&#40;Analysis Services 授予服务器管理员权限&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e13e1-130">[Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="e13e1-131">[&#40;Analysis Services 授予多维数据集或模型权限&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e13e1-131">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="e13e1-132">[授予对维度数据的自定义访问 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e13e1-132">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 [<span data-ttu-id="e13e1-133">授予单元数据的自定义访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e13e1-133">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
