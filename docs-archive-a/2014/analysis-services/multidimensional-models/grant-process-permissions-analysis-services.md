---
title: " (Analysis Services) 授予处理权限 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e41e8710bc167ef53eb2aad2cbf678019b96e0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690826"
---
# <a name="grant-process-permissions-analysis-services"></a><span data-ttu-id="84ecc-102">授予处理权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="84ecc-102">Grant process permissions (Analysis Services)</span></span>
  <span data-ttu-id="84ecc-103">作为管理员，你可以创建专用于 Analysis Services 处理操作的角色，从而可以委派特定任务到其他用户，或者委派到用于无人参与的预定处理的应用程序。</span><span class="sxs-lookup"><span data-stu-id="84ecc-103">As an administrator, you can create a role dedicated to Analysis Services processing operations, allowing you to delegate that particular task to other users, or to applications used for unattended scheduled processing.</span></span> <span data-ttu-id="84ecc-104">可以在数据库、多维数据集、维度和挖掘结构级别授予处理权限。</span><span class="sxs-lookup"><span data-stu-id="84ecc-104">Process permissions can be granted at the database, cube, dimension, and mining structure levels.</span></span> <span data-ttu-id="84ecc-105">除非你正在使用非常大型的多维数据集或表格数据库工作，否则我们建议授予数据库级别的处理权限，包括所有对象，也包括彼此互有相关性的对象。</span><span class="sxs-lookup"><span data-stu-id="84ecc-105">Unless you are working with a very large cube or tabular database, we recommend granting processing rights at the database level, inclusive of all objects, including those having dependencies on each other.</span></span>  
  
 <span data-ttu-id="84ecc-106">权限通过角色授予，将对象与权限以及 Windows 用户或组帐户进行关联。</span><span class="sxs-lookup"><span data-stu-id="84ecc-106">Permissions are granted through roles that associate objects with permissions and Windows user or group accounts.</span></span> <span data-ttu-id="84ecc-107">请记住，权限是可以累加的。</span><span class="sxs-lookup"><span data-stu-id="84ecc-107">Remember that permissions are additive.</span></span> <span data-ttu-id="84ecc-108">如果一个角色授予处理多维数据集的权限，同时另一个角色授予同一用户处理维度的权限，那么两个不同角色的权限会合并以授予用户在该数据库内的处理多维数据集和处理特定维度的权限。</span><span class="sxs-lookup"><span data-stu-id="84ecc-108">If one role grants permission to process a cube, while a second role gives the same user permission to process a dimension, the permissions from the two different roles combine to give the user permission to both process the cube and process the specified dimension within that database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84ecc-109">其角色只有处理权限的用户将不能够使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 来连接 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和处理对象。</span><span class="sxs-lookup"><span data-stu-id="84ecc-109">A user whose role only has Process permissions will be unable to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and process objects.</span></span> <span data-ttu-id="84ecc-110">这些工具要求 `Read Definition` 访问对象元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="84ecc-110">These tools require the `Read Definition` permission to access object metadata.</span></span> <span data-ttu-id="84ecc-111">没有功能使用任一工具时，则必须使用 XMLA 脚本来执行处理操作。</span><span class="sxs-lookup"><span data-stu-id="84ecc-111">Without the ability to use either tool, XMLA script must be used to execute a processing operation.</span></span>  
>   
>  <span data-ttu-id="84ecc-112">我们建议同时授予 `Read Definition` 权限以便进行检测。</span><span class="sxs-lookup"><span data-stu-id="84ecc-112">We suggest you also grant `Read Definition` permissions for testing purposes.</span></span> <span data-ttu-id="84ecc-113">具有 `Read Definition` 和 `Process Database` 权限的用户可交互地处理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的对象。</span><span class="sxs-lookup"><span data-stu-id="84ecc-113">A user having both `Read Definition` and `Process Database` permissions can process objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], interactively.</span></span> <span data-ttu-id="84ecc-114">有关详细信息，请参阅 [授予对象元数据的读取定义权限 (Analysis Services)](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="84ecc-114">See [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) for details.</span></span>  
  
## <a name="set-processing-permissions-at-the-database-level"></a><span data-ttu-id="84ecc-115">设置数据库级别的处理权限</span><span class="sxs-lookup"><span data-stu-id="84ecc-115">Set processing permissions at the database level</span></span>  
 <span data-ttu-id="84ecc-116">此部分解释了如何通过非管理员为数据库中的所有多维数据集、维度、挖掘结构和挖掘模型启用处理。</span><span class="sxs-lookup"><span data-stu-id="84ecc-116">This section explains how to enable processing by non-administrators, for all cubes, dimensions, mining structures, and mining models in the database.</span></span>  
  
1.  <span data-ttu-id="84ecc-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例，打开“数据库”文件夹，并选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="84ecc-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="84ecc-118">右键单击 "**角色**" "  |  **新建角色**"。</span><span class="sxs-lookup"><span data-stu-id="84ecc-118">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="84ecc-119">输入名称和说明。</span><span class="sxs-lookup"><span data-stu-id="84ecc-119">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="84ecc-120">在 "**常规**" 窗格中，选中相应的 `Process Database` 复选框。</span><span class="sxs-lookup"><span data-stu-id="84ecc-120">In the **General** pane, select the `Process Database` check box.</span></span> <span data-ttu-id="84ecc-121">此外， `Read Definition` 还可以选择通过一个 SQL Server 工具（例如）启用交互式处理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="84ecc-121">Additionally, select `Read Definition` to also enable interactive processing through one of the SQL Server tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
4.  <span data-ttu-id="84ecc-122">在“成员身份” \*\*\*\* 窗格，添加有权限处理此数据库中的任何对象的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="84ecc-122">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="84ecc-123">单击“确定” \*\*\*\* ，完成角色定义。</span><span class="sxs-lookup"><span data-stu-id="84ecc-123">Click **OK** to complete the role definition.</span></span>  
  
## <a name="set-processing-permissions-on-individual-objects"></a><span data-ttu-id="84ecc-124">设置单个对象的处理权限</span><span class="sxs-lookup"><span data-stu-id="84ecc-124">Set processing permissions on individual objects</span></span>  
 <span data-ttu-id="84ecc-125">你可设置单个多维数据集、维度、数据挖掘结构或模型的处理权限。</span><span class="sxs-lookup"><span data-stu-id="84ecc-125">You can set processing permissions on individual cubes, dimensions, data mining structures or models.</span></span>  
  
 <span data-ttu-id="84ecc-126">如果你无意中排除了需要一起处理的对象（例如，如果启用了对多维数据集进行处理而未对其相关维度进行处理），处理会失败。</span><span class="sxs-lookup"><span data-stu-id="84ecc-126">Processing can fail if you inadvertently exclude objects that need to be processed together (for example, if you enable processing on a cube, but not on its related dimensions).</span></span> <span data-ttu-id="84ecc-127">因为很容易就会漏掉对象相关性，所以设置单个对象的处理权限时，完全测试是至关重要的。</span><span class="sxs-lookup"><span data-stu-id="84ecc-127">Because it can be easy to miss object dependencies, thorough testing is essential when setting processing permissions on individual objects.</span></span>  
  
1.  <span data-ttu-id="84ecc-128">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例，打开“数据库”文件夹，并选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="84ecc-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="84ecc-129">右键单击 "**角色**" "  |  **新建角色**"。</span><span class="sxs-lookup"><span data-stu-id="84ecc-129">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="84ecc-130">输入名称和说明。</span><span class="sxs-lookup"><span data-stu-id="84ecc-130">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="84ecc-131">在 "**常规**" 窗格中，清除 `Process Database` 复选框。</span><span class="sxs-lookup"><span data-stu-id="84ecc-131">In the **General** pane, clear the `Process Database` check box.</span></span> <span data-ttu-id="84ecc-132">数据库权限通过使角色选项显示为灰色或不可选来覆盖在更低级别对象上设置权限的功能。</span><span class="sxs-lookup"><span data-stu-id="84ecc-132">Database permissions override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
     <span data-ttu-id="84ecc-133">技术上来说，专用处理角色不需要数据库权限。</span><span class="sxs-lookup"><span data-stu-id="84ecc-133">Technically, no database permissions are needed for dedicated processing roles.</span></span> <span data-ttu-id="84ecc-134">但 `Read Definition` 如果没有数据库级别，则无法查看中的数据库 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，从而使测试变得更加困难。</span><span class="sxs-lookup"><span data-stu-id="84ecc-134">But without `Read Definition` at the database level, you cannot view the database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], making testing more difficult.</span></span>  
  
4.  <span data-ttu-id="84ecc-135">选择单个对象来处理：</span><span class="sxs-lookup"><span data-stu-id="84ecc-135">Select individual objects to process:</span></span>  
  
    -   <span data-ttu-id="84ecc-136">在“多维数据集” \*\*\*\* 窗格，为每个多维数据集选中“处理” \*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="84ecc-136">In the **Cubes** pane, select the **Process** check box for each cube.</span></span>  
  
    -   <span data-ttu-id="84ecc-137">在“维度” \*\*\*\* 窗格，选择“所有数据库维度” \*\*\*\*，然后为每个维度选中“处理” \*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="84ecc-137">In the **Dimensions** pane, select **All database dimensions**, and then **Process** check box for each dimension.</span></span> <span data-ttu-id="84ecc-138">或者，选择所有行，然后使用 Shift + 单击来切换复选框选项。</span><span class="sxs-lookup"><span data-stu-id="84ecc-138">Or, select all rows, then use shift-click to toggle the check box selections.</span></span>  
  
5.  <span data-ttu-id="84ecc-139">在“成员身份” \*\*\*\* 窗格，添加有权限处理这些对象的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="84ecc-139">In the **Membership** pane, add the Windows user and group accounts having permission to process these objects.</span></span>  
  
6.  <span data-ttu-id="84ecc-140">单击“确定” \*\*\*\* ，完成角色定义。</span><span class="sxs-lookup"><span data-stu-id="84ecc-140">Click **OK** to complete the role definition.</span></span>  
  
## <a name="test-processing"></a><span data-ttu-id="84ecc-141">测试处理</span><span class="sxs-lookup"><span data-stu-id="84ecc-141">Test processing</span></span>  
  
1.  <span data-ttu-id="84ecc-142">按住 Shift 键并右键单击 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，选择“以不同用户身份运行”\*\*\*\* 并使用分配到正在进行测试的角色的 Windows 帐户连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="84ecc-142">Hold down the shift-key and right-click [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select **Run as a different user** and connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using a Windows account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="84ecc-143">打开“数据库”文件夹，选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="84ecc-143">Open the Databases folder, and select a database.</span></span> <span data-ttu-id="84ecc-144">你将只会看见对角色可见的数据库，你的帐户具有此角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="84ecc-144">You will only see the databases that are visible to the roles for which your account has membership.</span></span>  
  
3.  <span data-ttu-id="84ecc-145">右键单击多维数据集或维度并选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84ecc-145">Right-click a cube or dimension and select **Process**.</span></span> <span data-ttu-id="84ecc-146">选中处理选项。</span><span class="sxs-lookup"><span data-stu-id="84ecc-146">Choose a processing option.</span></span> <span data-ttu-id="84ecc-147">为对象的所有组合测试所有选项。</span><span class="sxs-lookup"><span data-stu-id="84ecc-147">Test all of the options, for all combinations of objects.</span></span> <span data-ttu-id="84ecc-148">如果由于缺失对象而出现错误，请添加对象到角色。</span><span class="sxs-lookup"><span data-stu-id="84ecc-148">If errors occur due to missing objects, add the objects to the role.</span></span>  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a><span data-ttu-id="84ecc-149">设置数据挖掘结构的处理权限</span><span class="sxs-lookup"><span data-stu-id="84ecc-149">Set processing permissions on a data mining structure</span></span>  
 <span data-ttu-id="84ecc-150">你可以创建一个授予处理数据挖掘结构权限的角色。</span><span class="sxs-lookup"><span data-stu-id="84ecc-150">You can create a role granting permission to process data mining structures.</span></span> <span data-ttu-id="84ecc-151">这包括处理所有挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="84ecc-151">This includes the processing of all mining models.</span></span>  
  
 <span data-ttu-id="84ecc-152">用于浏览挖掘模型和结构的 "**钻取**" 和 " `Read Definition` 权限" 是原子的，可以添加到相同的角色，也可以分成不同的角色。</span><span class="sxs-lookup"><span data-stu-id="84ecc-152">**Drill Through** and `Read Definition` permissions used for browsing a mining model and structure are atomic and can be added to the same role, or separated out into a different role.</span></span>  
  
1.  <span data-ttu-id="84ecc-153">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例，打开“数据库”文件夹，并选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="84ecc-153">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="84ecc-154">右键单击 "**角色**" "  |  **新建角色**"。</span><span class="sxs-lookup"><span data-stu-id="84ecc-154">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="84ecc-155">输入名称和说明。</span><span class="sxs-lookup"><span data-stu-id="84ecc-155">Enter a name and description.</span></span> <span data-ttu-id="84ecc-156">在“常规” \*\*\*\* 窗格，确保数据库权限复选框处于清空状态。</span><span class="sxs-lookup"><span data-stu-id="84ecc-156">In the **General** pane, make sure that the database permission check boxes are clear.</span></span> <span data-ttu-id="84ecc-157">数据库权限将通过使角色选项显示为灰色或不可选来覆盖在更低级别对象上设置权限的功能。</span><span class="sxs-lookup"><span data-stu-id="84ecc-157">Database permissions will override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
3.  <span data-ttu-id="84ecc-158">在“挖掘结构” \*\*\*\* 窗格，为每个挖掘结构选中“处理” \*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="84ecc-158">In the **Mining Structures** pane, select the **Process** check box for each mining structure.</span></span>  
  
4.  <span data-ttu-id="84ecc-159">在“成员身份” \*\*\*\* 窗格，添加有权限处理此数据库中的任何对象的 Windows 用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="84ecc-159">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="84ecc-160">单击“确定” \*\*\*\* ，完成角色定义。</span><span class="sxs-lookup"><span data-stu-id="84ecc-160">Click **OK** to complete the role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ecc-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84ecc-161">See Also</span></span>  
 <span data-ttu-id="84ecc-162">[处理数据库、表或分区](../tabular-models/process-database-table-or-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="84ecc-162">[Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) </span></span>  
 <span data-ttu-id="84ecc-163">[多维模型对象处理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="84ecc-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="84ecc-164">[授予数据库权限 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="84ecc-164">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="84ecc-165">授予对象元数据的读取定义权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="84ecc-165">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
