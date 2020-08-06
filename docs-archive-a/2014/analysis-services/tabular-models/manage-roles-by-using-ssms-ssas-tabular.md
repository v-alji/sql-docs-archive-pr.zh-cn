---
title: 使用 SSMS (SSAS 表格) 管理角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee34d5e75d5d4ce3679d46d29af3215852d2bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683112"
---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a><span data-ttu-id="c6412-102">使用 SSMS 管理角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c6412-102">Manage Roles by using SSMS (SSAS Tabular)</span></span>
  <span data-ttu-id="c6412-103">对于部署的表格模型，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建、编辑和管理角色。</span><span class="sxs-lookup"><span data-stu-id="c6412-103">You can create, edit, and manage roles for a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c6412-104">本主题中的任务：</span><span class="sxs-lookup"><span data-stu-id="c6412-104">Tasks in this topic:</span></span>  
  
-   [<span data-ttu-id="c6412-105">创建新角色</span><span class="sxs-lookup"><span data-stu-id="c6412-105">To create a new role</span></span>](#bkmk_new_role)  
  
-   [<span data-ttu-id="c6412-106">复制角色</span><span class="sxs-lookup"><span data-stu-id="c6412-106">To copy a role</span></span>](#bkmk_copy_role)  
  
-   [<span data-ttu-id="c6412-107">编辑角色</span><span class="sxs-lookup"><span data-stu-id="c6412-107">To edit a role</span></span>](#bkmk_edit_role)  
  
-   [<span data-ttu-id="c6412-108">删除角色</span><span class="sxs-lookup"><span data-stu-id="c6412-108">To delete a role</span></span>](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  <span data-ttu-id="c6412-109">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中通过角色管理器使用已定义的角色重新部署表格模型项目，将覆盖已部署的表格模型中定义的角色。</span><span class="sxs-lookup"><span data-stu-id="c6412-109">Re-deploying a tabular model project with roles defined by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite roles defined in a deployed tabular model.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c6412-110">如果在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中打开模型项目时使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 来管理表格模型工作区数据库，可能会导致 Model.bim 文件损坏。</span><span class="sxs-lookup"><span data-stu-id="c6412-110">Using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage a tabular model workspace database while the model project is open in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] may cause the Model.bim file to become corrupted.</span></span> <span data-ttu-id="c6412-111">在创建和管理表格模型工作区数据库的角色时，请使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中的角色管理器。</span><span class="sxs-lookup"><span data-stu-id="c6412-111">When creating and managing roles for a tabular model workspace database, use Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="c6412-112">创建新角色</span><span class="sxs-lookup"><span data-stu-id="c6412-112">To create a new role</span></span>  
  
1.  <span data-ttu-id="c6412-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开要为其创建新角色的表格模型数据库，右键单击 **“角色”**，然后单击 **“新建角色”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database for which you want to create a new role, then right click on **Roles**, and then click **New Role**.</span></span>  
  
2.  <span data-ttu-id="c6412-114">在 **“创建角色”** 对话框的“选择页”窗口中，单击 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-114">In the **Create Role** dialog box, in the Select a page window, click **General**.</span></span>  
  
3.  <span data-ttu-id="c6412-115">在常规设置窗口的 **“名称”** 字段中，键入角色的名称。</span><span class="sxs-lookup"><span data-stu-id="c6412-115">In the general settings window, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="c6412-116">默认情况下，对于每个新建角色，默认角色的名称将为递增式编号。</span><span class="sxs-lookup"><span data-stu-id="c6412-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="c6412-117">建议您键入明确标识成员类型的名称，例如财务经理或人力资源专员。</span><span class="sxs-lookup"><span data-stu-id="c6412-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="c6412-118">在 **“为此角色设置数据库权限”** 中，选择以下权限选项之一：</span><span class="sxs-lookup"><span data-stu-id="c6412-118">In **Set the database permissions for this role**, select one of the following permissions options:</span></span>  
  
    |<span data-ttu-id="c6412-119">权限</span><span class="sxs-lookup"><span data-stu-id="c6412-119">Permission</span></span>|<span data-ttu-id="c6412-120">说明</span><span class="sxs-lookup"><span data-stu-id="c6412-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="c6412-121">**完全控制（管理员）**</span><span class="sxs-lookup"><span data-stu-id="c6412-121">**Full control (Administrator)**</span></span>|<span data-ttu-id="c6412-122">成员可以对模型架构进行修改并可以查看所有数据。</span><span class="sxs-lookup"><span data-stu-id="c6412-122">Members can make modifications to the model schema and can view all data.</span></span>|  
    |<span data-ttu-id="c6412-123">**处理数据库**</span><span class="sxs-lookup"><span data-stu-id="c6412-123">**Process database**</span></span>|<span data-ttu-id="c6412-124">成员可以运行“处理”和“全部处理”操作。</span><span class="sxs-lookup"><span data-stu-id="c6412-124">Members can run Process and Process All operations.</span></span> <span data-ttu-id="c6412-125">不能修改模型架构且不能查看数据。</span><span class="sxs-lookup"><span data-stu-id="c6412-125">Cannot modify the model schema and cannot view data.</span></span>|  
    |<span data-ttu-id="c6412-126">**读取**</span><span class="sxs-lookup"><span data-stu-id="c6412-126">**Read**</span></span>|<span data-ttu-id="c6412-127">允许成员查看数据（基于行筛选器），但不能对模型架构进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="c6412-127">Members are allowed to view data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
  
5.  <span data-ttu-id="c6412-128">在 **“创建角色”** 对话框的“选择页”窗口中，单击 **“成员身份”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-128">In the **Create Role** dialog box, in the Select a page window, click **Membership**.</span></span>  
  
6.  <span data-ttu-id="c6412-129">在“成员身份设置”窗口中单击 **“添加”**，然后在 **“选择用户或组”** 对话框中，添加要作为成员添加的 Windows 用户或组。</span><span class="sxs-lookup"><span data-stu-id="c6412-129">In the membership settings window, click **Add**, and then in the **Select Users or Groups** dialog box, add the Windows users or groups you want to add as members.</span></span>  
  
7.  <span data-ttu-id="c6412-130">如果您创建的角色已具有“读取”权限，则可以使用 DAX 公式为任意表添加行筛选器。</span><span class="sxs-lookup"><span data-stu-id="c6412-130">If the role you are creating has Read permissions, you can add row filters for any table using a DAX formula.</span></span> <span data-ttu-id="c6412-131">若要添加行筛选器，请在 "**角色属性- \<rolename> \*\* " 对话框的 "**选择页**" 中，单击 "**行筛选器\*\*"。</span><span class="sxs-lookup"><span data-stu-id="c6412-131">To add row filters, in the **Role Properties - \<rolename>** dialog box, in **Select a page**, click on **Row Filters**.</span></span>  
  
8.  <span data-ttu-id="c6412-132">在 "行筛选器" 窗口中，选择一个表，然后单击 " **Dax 筛选器**" 字段，然后在 " \*\* \<tablename> dax 筛选器\*\*" 字段中键入 dax 公式。</span><span class="sxs-lookup"><span data-stu-id="c6412-132">In the row filters window, select a table, then click on the **DAX Filter** field, and then in the **DAX Filter - \<tablename>** field, type a DAX formula.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6412-133">DAX 筛选器 \<tablename> 字段不包含自动完成查询编辑器或插入函数功能。</span><span class="sxs-lookup"><span data-stu-id="c6412-133">The DAX Filter - \<tablename> field does not contain an AutoComplete query editor or insert function feature.</span></span> <span data-ttu-id="c6412-134">若要在写入 DAX 公式时使用自动完成功能，必须在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中使用 DAX 公式编辑器。</span><span class="sxs-lookup"><span data-stu-id="c6412-134">To use AutoComplete when writing a DAX formula, you must use a DAX formula editor in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
9. <span data-ttu-id="c6412-135">单击 **“确定”** 保存角色。</span><span class="sxs-lookup"><span data-stu-id="c6412-135">Click **Ok** to save the role.</span></span>  
  
###  <a name="to-copy-a-role"></a><a name="bkmk_copy_role"></a><span data-ttu-id="c6412-136">复制角色</span><span class="sxs-lookup"><span data-stu-id="c6412-136">To copy a role</span></span>  
  
1.  <span data-ttu-id="c6412-137">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开包含要复制的角色的表格模型数据库，展开 **“角色”**，右键单击该角色，然后单击 **“复制”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-137">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to copy, then expand **Roles**, then right click on the role, and then click **Duplicate**.</span></span>  
  
###  <a name="to-edit-a-role"></a><a name="bkmk_edit_role"></a><span data-ttu-id="c6412-138">编辑角色</span><span class="sxs-lookup"><span data-stu-id="c6412-138">To edit a role</span></span>  
  
-   <span data-ttu-id="c6412-139">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开包含要编辑的角色的表格模型数据库，展开 **“角色”**，右键单击该角色，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-139">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to edit, then expand **Roles**, then right click on the role, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="c6412-140">在 "**角色属性**" \<rolename> 对话框中，您可以更改权限、添加或删除成员，以及添加/编辑行筛选器。</span><span class="sxs-lookup"><span data-stu-id="c6412-140">In the **Role Properties** \<rolename> dialog box, you can change permissions, add or remove members, and add/edit row filters.</span></span>  
  
###  <a name="to-delete-a-role"></a><a name="bkmk_deletet_role"></a><span data-ttu-id="c6412-141">删除角色</span><span class="sxs-lookup"><span data-stu-id="c6412-141">To delete a role</span></span>  
  
-   <span data-ttu-id="c6412-142">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开包含要删除的角色的表格模型数据库，展开 **“角色”**，右键单击该角色，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="c6412-142">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to delete, then expand **Roles**, then right click on the role, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6412-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6412-143">See Also</span></span>  
 [<span data-ttu-id="c6412-144">角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c6412-144">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
