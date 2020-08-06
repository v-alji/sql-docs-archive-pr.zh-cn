---
title: “权限”或“安全对象”页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.permissions.f1
- sql12.swb.SecurableAndEffectPermissions.f1
- sql12.swb.availabilitygroupproperties.permission.f1
- sql12.swb.common.columnperm.f1
- sql12.swb.SecurableAndEffectivePermission.f1
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80417c720258833850f07eb67f83f5c47f487ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688749"
---
# <a name="permissions-or-securables-page"></a><span data-ttu-id="239e0-102">“权限”或“安全对象”页</span><span class="sxs-lookup"><span data-stu-id="239e0-102">Permissions or Securables Page</span></span>
  <span data-ttu-id="239e0-103">使用 **“权限”** 或 **“安全对象”** 页可以查看或设置安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-103">Use the **Permissions** page or the **Securables** page to view or set the permissions for securables.</span></span> <span data-ttu-id="239e0-104">此页可以从多个位置打开。</span><span class="sxs-lookup"><span data-stu-id="239e0-104">This page can be opened from many locations.</span></span> <span data-ttu-id="239e0-105">根据此页的打开方式以及其中包含的内容，此页中的内容可能会稍有不同。</span><span class="sxs-lookup"><span data-stu-id="239e0-105">The contents of the page can change slightly, depending on how the page is opened and what it contains.</span></span> <span data-ttu-id="239e0-106">此页在打开时，其顶部网格可能会进行填充，也可能为空。</span><span class="sxs-lookup"><span data-stu-id="239e0-106">The top grid of the page might be populated when the page opens, or it might be empty.</span></span> <span data-ttu-id="239e0-107">若要在上部网格中添加项目，请单击 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="239e0-107">To add items to the upper grid, click **Search**.</span></span> <span data-ttu-id="239e0-108">在上部网格中，选择一个项目，然后在 **“显式”** 选项卡上设置相应的权限。若要查看聚合权限，请使用 **“有效”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="239e0-108">In the upper grid, select an item, and then set the appropriate permissions on the **Explicit** tab. To view aggregated permissions, use the **Effective** tab.</span></span>  
  
 <span data-ttu-id="239e0-109">若要了解安全对象和主体的可能组合，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) 主题中特定于安全对象的语法链接。</span><span class="sxs-lookup"><span data-stu-id="239e0-109">To understand the possible combinations of securables and principals, see the securable-specific syntax links in the topic [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="239e0-110">有关详细信息，请参阅 [Securables](securables.md)。</span><span class="sxs-lookup"><span data-stu-id="239e0-110">For more information, see [Securables](securables.md).</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="239e0-111">页眉</span><span class="sxs-lookup"><span data-stu-id="239e0-111">Page Header</span></span>  
 <span data-ttu-id="239e0-112">**“权限”** 或 **“安全对象”** 页的页眉会根据安全对象或主体的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="239e0-112">The header of the **Permissions** or **Securables** page varies depending on the securable or principal.</span></span> <span data-ttu-id="239e0-113">其中显示了与项有关的信息，如项名称。</span><span class="sxs-lookup"><span data-stu-id="239e0-113">It displays information relevant to the item, such as its name.</span></span>  
  
## <a name="upper-grid"></a><span data-ttu-id="239e0-114">上部网格</span><span class="sxs-lookup"><span data-stu-id="239e0-114">Upper Grid</span></span>  
 <span data-ttu-id="239e0-115">上部网格中包含一个或多个可以设置权限的项。</span><span class="sxs-lookup"><span data-stu-id="239e0-115">The upper grid contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="239e0-116">该对话框提供了一个 **“搜索”** 按钮，使用该按钮可以选择要添加到上部网格中的对象或主体。</span><span class="sxs-lookup"><span data-stu-id="239e0-116">This dialog box provides the **Search** button for selecting objects or principals to add to the upper grid.</span></span> <span data-ttu-id="239e0-117">该网格的名称可能显示为 **“安全对象”** 或者一种或多种类型的安全对象或主体。</span><span class="sxs-lookup"><span data-stu-id="239e0-117">The name of the grid might display **Securables** or one or more types of securables or principals.</span></span> <span data-ttu-id="239e0-118">上部网格中显示的列会根据主体或安全对象的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="239e0-118">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="239e0-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="239e0-119">**Name**</span></span>  
 <span data-ttu-id="239e0-120">添加到网格中的每个主体或安全对象的名称。</span><span class="sxs-lookup"><span data-stu-id="239e0-120">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="239e0-121">类型</span><span class="sxs-lookup"><span data-stu-id="239e0-121">**Type**</span></span>  
 <span data-ttu-id="239e0-122">描述每个项目的类型。</span><span class="sxs-lookup"><span data-stu-id="239e0-122">Describes the type of each item.</span></span>  
  
## <a name="explicit-tab"></a><span data-ttu-id="239e0-123">“显式”选项卡</span><span class="sxs-lookup"><span data-stu-id="239e0-123">Explicit Tab</span></span>  
 <span data-ttu-id="239e0-124">**“显式”** 选项卡列出了上部网格中所选安全对象的可能权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-124">The **Explicit** tab lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="239e0-125">若要配置权限，请选中或清除“授予”（或“允许”）、“具有授予权限”和“拒绝”复选框   。</span><span class="sxs-lookup"><span data-stu-id="239e0-125">To configure the permissions, select or clear the **Grant** (or **Allow**), **With Grant**, and **Deny** check boxes.</span></span> <span data-ttu-id="239e0-126">对于所有显式权限，全部选项均不可用。</span><span class="sxs-lookup"><span data-stu-id="239e0-126">All options are not available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="239e0-127">**权限**</span><span class="sxs-lookup"><span data-stu-id="239e0-127">**Permissions**</span></span>  
 <span data-ttu-id="239e0-128">权限的名称。</span><span class="sxs-lookup"><span data-stu-id="239e0-128">The name of the permission.</span></span>  
  
 <span data-ttu-id="239e0-129">**授权者**</span><span class="sxs-lookup"><span data-stu-id="239e0-129">**Grantor**</span></span>  
 <span data-ttu-id="239e0-130">授予该权限的主体。</span><span class="sxs-lookup"><span data-stu-id="239e0-130">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="239e0-131">**授予**</span><span class="sxs-lookup"><span data-stu-id="239e0-131">**Grant**</span></span>  
 <span data-ttu-id="239e0-132">选中该选项可以将此权限授予该登录名。</span><span class="sxs-lookup"><span data-stu-id="239e0-132">Select to grant this permission to the login.</span></span> <span data-ttu-id="239e0-133">清除该选项将撤消此权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-133">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="239e0-134">**具有授予权限**</span><span class="sxs-lookup"><span data-stu-id="239e0-134">**With Grant**</span></span>  
 <span data-ttu-id="239e0-135">反映所列权限的 WITH GRANT 选项的状态。</span><span class="sxs-lookup"><span data-stu-id="239e0-135">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="239e0-136">此框是只读的。</span><span class="sxs-lookup"><span data-stu-id="239e0-136">This box is read-only.</span></span> <span data-ttu-id="239e0-137">若要应用此权限，请使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="239e0-137">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="239e0-138">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="239e0-138">**Deny**</span></span>  
 <span data-ttu-id="239e0-139">选中该选项可以拒绝该登录名具有该权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-139">Select to deny this permission to the login.</span></span> <span data-ttu-id="239e0-140">清除该选项将撤消此权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-140">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="239e0-141">**列权限**</span><span class="sxs-lookup"><span data-stu-id="239e0-141">**Column Permissions**</span></span>  
 <span data-ttu-id="239e0-142">对于包含列的对象（如表、视图或表值函数），单击“列权限”按钮将打开“列权限”对话框 。</span><span class="sxs-lookup"><span data-stu-id="239e0-142">For objects that contain columns (such as tables, views, or table-valued functions), the **Column Permissions** button opens the **Column Permissions** dialog box.</span></span> <span data-ttu-id="239e0-143">在该对话框中，可以针对表或视图中的各列设置 **“授予”** 、 **“允许”** 或 **“拒绝”** 权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-143">In this dialog box, you can set **Grant**, **Allow**, or **Deny** permissions on individual columns of a table or view.</span></span> <span data-ttu-id="239e0-144">此选项无法用于所有的对象类型或权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-144">This option is not available for all object types or permissions.</span></span>  
  
## <a name="effective-tab"></a><span data-ttu-id="239e0-145">“有效”选项卡</span><span class="sxs-lookup"><span data-stu-id="239e0-145">Effective Tab</span></span>  
 <span data-ttu-id="239e0-146">主体所拥有的与安全对象相关的权限可能来自为多个不同的主体设置的权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-146">The permissions that a principal has related to a securable may come from permissions that are set for several different principals.</span></span> <span data-ttu-id="239e0-147">例如，对于某个登录名，可以为其单独授予权限，也可以将其作为组的成员授予权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-147">For example, a login might be granted permissions individually and also as a member of a group.</span></span> <span data-ttu-id="239e0-148">**“有效”** 选项卡中显示从组或角色成员身份接收的权限与显式权限的组合结果。</span><span class="sxs-lookup"><span data-stu-id="239e0-148">The **Effective** tab shows the result of combining explicit permissions and the permissions that are received from group or role memberships.</span></span> <span data-ttu-id="239e0-149">将对授予权限进行聚合，</span><span class="sxs-lookup"><span data-stu-id="239e0-149">Grant permissions are aggregated.</span></span> <span data-ttu-id="239e0-150">拒绝权限会覆盖所有的授予权限。</span><span class="sxs-lookup"><span data-stu-id="239e0-150">A deny permission overrides all grant permissions.</span></span>  
  
 <span data-ttu-id="239e0-151">**权限**</span><span class="sxs-lookup"><span data-stu-id="239e0-151">**Permissions**</span></span>  
 <span data-ttu-id="239e0-152">权限的名称。</span><span class="sxs-lookup"><span data-stu-id="239e0-152">The name of the permission.</span></span>  
  
 <span data-ttu-id="239e0-153">**列**</span><span class="sxs-lookup"><span data-stu-id="239e0-153">**Column**</span></span>  
 <span data-ttu-id="239e0-154">受到该权限影响的列的名称。</span><span class="sxs-lookup"><span data-stu-id="239e0-154">The names of columns that are affected by the permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239e0-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="239e0-155">See Also</span></span>  
 <span data-ttu-id="239e0-156">[数据库级别的角色](authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="239e0-156">[Database-Level Roles](authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="239e0-157">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="239e0-157">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
