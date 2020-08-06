---
title: " (SSAS 表格) 创建和管理角色 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 335e0e311d97ea452449cd0c5d6550f6dbcca4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578489"
---
# <a name="create-and-manage-roles-ssas-tabular"></a><span data-ttu-id="3e853-102">创建和管理角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="3e853-102">Create and Manage Roles (SSAS Tabular)</span></span>
  <span data-ttu-id="3e853-103">在表格模型中，角色定义模型的成员权限。</span><span class="sxs-lookup"><span data-stu-id="3e853-103">Roles, in tabular models, define member permissions for a model.</span></span> <span data-ttu-id="3e853-104">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的“角色管理器”对话框为模型项目定义角色。</span><span class="sxs-lookup"><span data-stu-id="3e853-104">Roles are defined for a model project by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3e853-105">在部署模型时，数据库管理员可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]管理角色。</span><span class="sxs-lookup"><span data-stu-id="3e853-105">When a model is deployed, database administrators can manage roles by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3e853-106">本主题中的任务说明如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的“角色管理器”对话框在模型创作期间创建和管理角色。</span><span class="sxs-lookup"><span data-stu-id="3e853-106">The tasks in this topic describe how to create and manage roles during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3e853-107">有关在部署的模型数据库中管理角色的信息，请参阅[表格模型角色（SSAS 表格）](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="3e853-107">For information about managing roles in a deployed model database, see [Tabular Model Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3e853-108">任务</span><span class="sxs-lookup"><span data-stu-id="3e853-108">Tasks</span></span>  
 <span data-ttu-id="3e853-109">若要创建、编辑、复制和删除角色，可使用 **“角色管理器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3e853-109">To create, edit, copy, and delete roles, you will use the **Role Manager** dialog box.</span></span> <span data-ttu-id="3e853-110">若要查看 **“角色管理器”** 对话框，请在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“角色管理器”**。</span><span class="sxs-lookup"><span data-stu-id="3e853-110">To view the **Role Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="3e853-111">创建新角色</span><span class="sxs-lookup"><span data-stu-id="3e853-111">To create a new role</span></span>  
  
1.  <span data-ttu-id="3e853-112">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“角色管理器”**。</span><span class="sxs-lookup"><span data-stu-id="3e853-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
2.  <span data-ttu-id="3e853-113">在 **“角色管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="3e853-113">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="3e853-114">一个新的突出显示的角色会添加到“角色”列表中。</span><span class="sxs-lookup"><span data-stu-id="3e853-114">A new highlighted role is added to the Roles list.</span></span>  
  
3.  <span data-ttu-id="3e853-115">在 **“角色”** 列表的 **“名称”** 字段中，键入角色的名称。</span><span class="sxs-lookup"><span data-stu-id="3e853-115">In the **Roles** list, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="3e853-116">默认情况下，对于每个新建角色，默认角色的名称将为递增式编号。</span><span class="sxs-lookup"><span data-stu-id="3e853-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="3e853-117">建议您键入明确标识成员类型的名称，例如财务经理或人力资源专员。</span><span class="sxs-lookup"><span data-stu-id="3e853-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="3e853-118">在 **“权限”** 字段中，单击向下箭头，然后选择以下权限类型之一：</span><span class="sxs-lookup"><span data-stu-id="3e853-118">In the **Permissions** field, click the down arrow and then select one of the following permission types:</span></span>  
  
    |<span data-ttu-id="3e853-119">权限</span><span class="sxs-lookup"><span data-stu-id="3e853-119">Permission</span></span>|<span data-ttu-id="3e853-120">说明</span><span class="sxs-lookup"><span data-stu-id="3e853-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="3e853-121">**无**</span><span class="sxs-lookup"><span data-stu-id="3e853-121">**None**</span></span>|<span data-ttu-id="3e853-122">成员无法对模型架构进行任何修改，也无法查询数据。</span><span class="sxs-lookup"><span data-stu-id="3e853-122">Members cannot make any modifications to the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="3e853-123">**读取**</span><span class="sxs-lookup"><span data-stu-id="3e853-123">**Read**</span></span>|<span data-ttu-id="3e853-124">允许成员查询数据（基于行筛选器），但不能对模型架构进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="3e853-124">Members are allowed to query data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="3e853-125">**读取和处理**</span><span class="sxs-lookup"><span data-stu-id="3e853-125">**Read and Process**</span></span>|<span data-ttu-id="3e853-126">允许成员查询数据（基于行级别筛选器）并运行“处理”和“全部处理”操作，但无法对模型架构进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="3e853-126">Members are allowed to query data (based on row-level filters) and run Process and Process All operations, but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="3e853-127">**处理**</span><span class="sxs-lookup"><span data-stu-id="3e853-127">**Process**</span></span>|<span data-ttu-id="3e853-128">成员可以运行“处理”和“全部处理”操作。</span><span class="sxs-lookup"><span data-stu-id="3e853-128">Members can run Process and Process All operations.</span></span> <span data-ttu-id="3e853-129">无法修改模型架构，也无法查询数据。</span><span class="sxs-lookup"><span data-stu-id="3e853-129">Cannot modify the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="3e853-130">**管理员**</span><span class="sxs-lookup"><span data-stu-id="3e853-130">**Administrator**</span></span>|<span data-ttu-id="3e853-131">成员可以对模型架构进行修改并可以查询所有数据。</span><span class="sxs-lookup"><span data-stu-id="3e853-131">Members can make modifications to the model schema and can query all data.</span></span>|  
  
5.  <span data-ttu-id="3e853-132">若要输入角色的说明，请单击 **“说明”** 字段，然后键入说明。</span><span class="sxs-lookup"><span data-stu-id="3e853-132">To enter a description for the role, click the **Description** field, and then type a description.</span></span>  
  
6.  <span data-ttu-id="3e853-133">如果您创建的角色已具有“读取”或者“读取和处理”权限，则您可以使用 DAX 公式添加行筛选器。</span><span class="sxs-lookup"><span data-stu-id="3e853-133">If the role you are creating has Read or Read and Process permission, you can add row filters using a DAX formula.</span></span> <span data-ttu-id="3e853-134">若要添加行筛选器，请单击 **“行筛选器”** 选项卡，选择某个表，然后单击 **“DAX 筛选器”** 字段，再键入 DAX 公式。</span><span class="sxs-lookup"><span data-stu-id="3e853-134">To add row filters, click the **Row Filters** tab, then select a table, then click the **DAX Filter** field, and then type a DAX formula.</span></span>  
  
7.  <span data-ttu-id="3e853-135">若要向角色添加成员，请单击 **“成员”** 选项卡，然后单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="3e853-135">To add members to the role, click the **Members** tab, and then click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3e853-136">也可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]将角色成员添加到已部署的模型中。</span><span class="sxs-lookup"><span data-stu-id="3e853-136">Role members can also be added to a deployed model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3e853-137">有关详细信息，请参阅[使用 SSMS 管理角色（SSAS 表格）](manage-roles-by-using-ssms-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="3e853-137">For more information, see [Manage Roles by using SSMS &#40;SSAS Tabular&#41;](manage-roles-by-using-ssms-ssas-tabular.md).</span></span>  
  
8.  <span data-ttu-id="3e853-138">在 **“选择用户或组”** 对话框中，将 Windows 用户或 Windows 组对象作为成员输入。</span><span class="sxs-lookup"><span data-stu-id="3e853-138">In the **Select Users or Groups** dialog box, enter Windows user or Windows group objects as members.</span></span>  
  
9. <span data-ttu-id="3e853-139">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="3e853-139">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e853-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e853-140">See Also</span></span>  
 <span data-ttu-id="3e853-141">[&#40;SSAS 表格&#41;的角色](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3e853-141">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 <span data-ttu-id="3e853-142">[SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3e853-142">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 <span data-ttu-id="3e853-143">[在 Excel 中分析 &#40;SSAS 表格&#41;](analyze-in-excel-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3e853-143">[Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md) </span></span>  
 <span data-ttu-id="3e853-144">[USERNAME 函数 &#40;DAX&#41;](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="3e853-144">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 [<span data-ttu-id="3e853-145">&#40;DAX&#41;的 CUSTOMDATA 函数</span><span class="sxs-lookup"><span data-stu-id="3e853-145">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
