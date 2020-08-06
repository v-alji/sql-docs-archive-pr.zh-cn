---
title: 第12课：创建角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 962cd19726a5404de81e20a2209b25b9cc277e21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577031"
---
# <a name="lesson-12-create-roles"></a><span data-ttu-id="1fef7-102">第 12 课：创建角色</span><span class="sxs-lookup"><span data-stu-id="1fef7-102">Lesson 12: Create Roles</span></span>
  <span data-ttu-id="1fef7-103">在本课中，您将创建角色。</span><span class="sxs-lookup"><span data-stu-id="1fef7-103">In this lesson, you will create roles.</span></span> <span data-ttu-id="1fef7-104">角色通过只限作为角色成员的那些 Windows 用户进行访问，提供模型数据库对象和数据的安全性。</span><span class="sxs-lookup"><span data-stu-id="1fef7-104">Roles provide model database object and data security by limiting access to only those Windows users which are role members.</span></span> <span data-ttu-id="1fef7-105">每个角色都定义有单一权限：无、读取、读取和处理、处理，或管理员。</span><span class="sxs-lookup"><span data-stu-id="1fef7-105">Each role is defined with a single permission: None, Read, Read and Process, Process, or Administrator.</span></span> <span data-ttu-id="1fef7-106">通过使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中的“角色管理器”对话框，可在模型创作期间定义角色。</span><span class="sxs-lookup"><span data-stu-id="1fef7-106">Roles can be defined during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="1fef7-107">在部署模型后，可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]管理角色。</span><span class="sxs-lookup"><span data-stu-id="1fef7-107">After a model has been deployed, you can manage roles by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1fef7-108">若要了解详细信息，请参阅[角色（SSAS 表格）](tabular-models/roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="1fef7-108">To learn more, see [Roles &#40;SSAS Tabular&#41;](tabular-models/roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1fef7-109">创建角色对于完成本教程不是必需的。</span><span class="sxs-lookup"><span data-stu-id="1fef7-109">Creating roles is not necessary to complete this tutorial.</span></span> <span data-ttu-id="1fef7-110">默认情况下，当前用来登录的帐户将具有对模型的管理员权限。</span><span class="sxs-lookup"><span data-stu-id="1fef7-110">By default, the account you are currently logged in with will have Administrator privileges on the model.</span></span> <span data-ttu-id="1fef7-111">但是，为了让贵组织中的其他用户能够通过报表客户端应用程序浏览模型，您必须至少创建一个具有“读取”权限的角色，并将这些用户添加为成员。</span><span class="sxs-lookup"><span data-stu-id="1fef7-111">However, to allow other users in your organization to browse the model by using a reporting client application, you must create at least one role with Read permissions and add those users as members.</span></span>  
  
 <span data-ttu-id="1fef7-112">将创建三个角色：</span><span class="sxs-lookup"><span data-stu-id="1fef7-112">You will create three roles:</span></span>  
  
-   <span data-ttu-id="1fef7-113">销售经理-此角色可以包含你的组织中希望其对所有模型对象和数据具有 "读取" 权限的用户。</span><span class="sxs-lookup"><span data-stu-id="1fef7-113">Sales Manager - This role can include users in your organization for which you want to have Read permission to all model objects and data.</span></span>  
  
-   <span data-ttu-id="1fef7-114">销售分析人员-此角色可以包含你的组织中的用户，你只希望能够在美国 (美国) 浏览与销售相关的数据。</span><span class="sxs-lookup"><span data-stu-id="1fef7-114">Sales Analyst US - This role can include users in your organization for which you want only to be able to browse data related to sales in the US (United States).</span></span> <span data-ttu-id="1fef7-115">对于此角色，将使用一个 DAX 公式来定义*行筛选器*，该筛选器将成员限制为只能浏览有关美国的数据。</span><span class="sxs-lookup"><span data-stu-id="1fef7-115">For this role, you will use a DAX formula to define a *Row Filter*, which restricts members to browse data only for the United States.</span></span>  
  
-   <span data-ttu-id="1fef7-116">"管理员"-此角色可以包括希望其具有管理员权限的用户，该权限允许无限制的访问和权限，从而对模型数据库执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="1fef7-116">Administrator - This role can include users for which you want to have Administrator permission, which allows unlimited access and permissions to perform administrative tasks on the model database.</span></span>  
  
 <span data-ttu-id="1fef7-117">因为组织中的 Windows 用户和组帐户具有唯一性，所以可以将特定组织中的帐户添加为成员。</span><span class="sxs-lookup"><span data-stu-id="1fef7-117">Because Windows user and group accounts in your organization are unique, you can add accounts from your particular organization to members.</span></span> <span data-ttu-id="1fef7-118">不过，对于本教程，也可以将成员保留为空。</span><span class="sxs-lookup"><span data-stu-id="1fef7-118">However, for this tutorial, you can also leave the members blank.</span></span> <span data-ttu-id="1fef7-119">在稍后的第 12 课“在 Excel 中分析”中，您将仍可以测试每个角色的影响。</span><span class="sxs-lookup"><span data-stu-id="1fef7-119">You will still be able to test the effect of each role later in Lesson 12: Analyze in Excel.</span></span>  
  
 <span data-ttu-id="1fef7-120">学完本课的估计时间： **15 分钟**</span><span class="sxs-lookup"><span data-stu-id="1fef7-120">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1fef7-121">先决条件</span><span class="sxs-lookup"><span data-stu-id="1fef7-121">Prerequisites</span></span>  
 <span data-ttu-id="1fef7-122">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="1fef7-122">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="1fef7-123">在执行本课程中的任务之前，须已完成上一课： [第 11 课：创建分区](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="1fef7-123">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="create-roles"></a><span data-ttu-id="1fef7-124">创建角色</span><span class="sxs-lookup"><span data-stu-id="1fef7-124">Create Roles</span></span>  
  
#### <a name="to-create-a-sales-manager-user-role"></a><span data-ttu-id="1fef7-125">创建 Sales Manager 用户角色</span><span class="sxs-lookup"><span data-stu-id="1fef7-125">To create a Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="1fef7-126">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“模型”菜单，然后单击“角色”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="1fef7-127">在 **“角色管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="1fef7-127">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="1fef7-128">随后会将一个“无”权限的新角色添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="1fef7-128">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="1fef7-129">单击新角色，然后在 "**名称**" 列中，将角色重命名为 `Internet Sales Manager` 。</span><span class="sxs-lookup"><span data-stu-id="1fef7-129">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Manager`.</span></span>  
  
4.  <span data-ttu-id="1fef7-130">在“权限”列中，单击下拉列表，并选择“读取”权限。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-130">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="1fef7-131">可选：单击“成员”选项卡，并单击“添加”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-131">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="1fef7-132">在“选择用户或组”对话框中，输入组织中希望将其包括在该角色中的 Windows 用户或组。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-132">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
7.  <span data-ttu-id="1fef7-133">验证你的选择，然后单击 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="1fef7-133">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a><span data-ttu-id="1fef7-134">创建 Sales Analyst US 用户角色</span><span class="sxs-lookup"><span data-stu-id="1fef7-134">To create a Sales Analyst US user role</span></span>  
  
1.  <span data-ttu-id="1fef7-135">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“模型”菜单，然后单击“角色”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="1fef7-136">在 **“角色管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="1fef7-136">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="1fef7-137">随后会将一个“无”权限的新角色添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="1fef7-137">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="1fef7-138">单击新角色，然后在 "**名称**" 列中，将角色重命名为 `Internet Sales US` 。</span><span class="sxs-lookup"><span data-stu-id="1fef7-138">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales US`.</span></span>  
  
4.  <span data-ttu-id="1fef7-139">在“权限”列中，单击下拉列表，并选择“读取”权限。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-139">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="1fef7-140">单击“行筛选器”选项卡，然后只针对 **Geography** 表，在“DAX 筛选器”列中键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="1fef7-140">Click on the Row Filters tab, and then for the **Geography** table only, in the DAX Filter column, type the following formula:</span></span>  
  
     `=Geography[Country Region Code] = "US"`  
  
     <span data-ttu-id="1fef7-141">行筛选器公式必须解析为布尔 (TRUE/FALSE) 值。</span><span class="sxs-lookup"><span data-stu-id="1fef7-141">A Row Filter formula must resolve to a Boolean (TRUE/FALSE) value.</span></span> <span data-ttu-id="1fef7-142">对于此公式，您指定只有国家/地区区域代码值为 "US" 的行对用户可见。</span><span class="sxs-lookup"><span data-stu-id="1fef7-142">With this formula, you are specifying that only rows with the Country Region Code value of "US" be visible to the user.</span></span>  
  
     <span data-ttu-id="1fef7-143">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="1fef7-143">When you have finished building the formula, press ENTER.</span></span>  
  
6.  <span data-ttu-id="1fef7-144">可选：单击“成员”选项卡，并单击“添加”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-144">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="1fef7-145">在“选择用户或组”对话框中，输入组织中希望将其包括在该角色中的 Windows 用户或组。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-145">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
8.  <span data-ttu-id="1fef7-146">验证你的选择，然后单击 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="1fef7-146">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-an-administrator-role"></a><span data-ttu-id="1fef7-147">创建 Administrator 角色</span><span class="sxs-lookup"><span data-stu-id="1fef7-147">To create an Administrator role</span></span>  
  
1.  <span data-ttu-id="1fef7-148">在 **“角色管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="1fef7-148">In the **Role Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="1fef7-149">单击新角色，然后在 "**名称**" 列中，将角色重命名为 `Internet Sales Administrator` 。</span><span class="sxs-lookup"><span data-stu-id="1fef7-149">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Administrator`.</span></span>  
  
3.  <span data-ttu-id="1fef7-150">在“权限”列中，单击下拉列表，然后选择“管理员”权限。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1fef7-150">In the **Permissions** column, click the dropdown list, and then select the **Administrator** permission.</span></span>  
  
4.  <span data-ttu-id="1fef7-151">单击“成员”\*\*\*\* 选项卡，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1fef7-151">Click on the **Members** tab, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="1fef7-152">可选：在“选择用户或组”\*\*\*\* 对话框中，输入要包括在角色中的来自组织的 Windows 用户或组。</span><span class="sxs-lookup"><span data-stu-id="1fef7-152">Optional: In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
6.  <span data-ttu-id="1fef7-153">验证你的选择，然后单击 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="1fef7-153">Verify your selections, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1fef7-154">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1fef7-154">Next Steps</span></span>  
 <span data-ttu-id="1fef7-155">若要继续学习本教程，请转到下一课：课程： [第 13 课：在 Excel 中进行分析](lesson-12-analyze-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="1fef7-155">To continue this tutorial, go to the next lesson: Lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
  
