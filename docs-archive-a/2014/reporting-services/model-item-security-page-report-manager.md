---
title: 模型项安全性页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 928572437990c7f7fe1117c086c65c939aa9c999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577375"
---
# <a name="model-item-security-page-report-manager"></a><span data-ttu-id="c84b2-102">“模型项安全性”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="c84b2-102">Model Item Security Page (Report Manager)</span></span>
  <span data-ttu-id="c84b2-103">使用此页，可以通过针对特定项授予或撤消只读权限来保护模型的各个部分。</span><span class="sxs-lookup"><span data-stu-id="c84b2-103">Use this page to secure parts of a model by granting or revoking read-only permissions on particular items.</span></span> <span data-ttu-id="c84b2-104">模型项安全性不但会影响运行时的即席数据浏览，而且还会影响在报表生成器中创建报表时对已发布模型各部分的使用。</span><span class="sxs-lookup"><span data-stu-id="c84b2-104">Model item security affects ad hoc data exploration at run time and the ability to use parts of a published model when creating reports in Report Builder.</span></span> <span data-ttu-id="c84b2-105">若要使用此功能，必须具有“内容管理员”权限。</span><span class="sxs-lookup"><span data-stu-id="c84b2-105">To use this feature, you must have Content Manager permissions.</span></span>  
  
 <span data-ttu-id="c84b2-106">模型项安全性应用于报表服务器中处理的模型，不会影响模型设计器中编辑的或报表设计器中使用的 .smdl 文件。</span><span class="sxs-lookup"><span data-stu-id="c84b2-106">Model item security is applied to a model that is processed on the report server and does not affect .smdl files that you edit in Model Designer or use in Report Designer.</span></span> <span data-ttu-id="c84b2-107">此外，它也不会对具有模型定义修改权限的用户产生影响。</span><span class="sxs-lookup"><span data-stu-id="c84b2-107">Furthermore, it has no effect on users who have permission to modify a model definition.</span></span> <span data-ttu-id="c84b2-108">无论是否应用模型项安全性，任何对模型具有“内容管理员”权限或“发布者”权限的用户都可以查看模型项安全性的各部分。</span><span class="sxs-lookup"><span data-stu-id="c84b2-108">Any user who has Content Manager or Publisher permissions on a model can see all parts of it, regardless of whether you apply model item security.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c84b2-109">可以使用安全筛选器进一步加强对模型项的保护。</span><span class="sxs-lookup"><span data-stu-id="c84b2-109">Model items can be further secured through the use of security filters.</span></span>  
  
 <span data-ttu-id="c84b2-110">可以针对模型内的实体、文件夹和单个字段定义模型项安全性。</span><span class="sxs-lookup"><span data-stu-id="c84b2-110">You can define model item security on entities, folders, and individual fields within a model.</span></span> <span data-ttu-id="c84b2-111">由于模型中存在大量可保护的项，因此可以将权限继承内置到模型中，以便可以通过数量相对较少的角色分配来保护大量项。</span><span class="sxs-lookup"><span data-stu-id="c84b2-111">Because a model presents such a large surface of securable items, permission inheritance is built into the model so that you can secure a large number of items through a relatively small number of role assignments.</span></span> <span data-ttu-id="c84b2-112">权限继承基于以下内容：</span><span class="sxs-lookup"><span data-stu-id="c84b2-112">Permission inheritance is based on the following:</span></span>  
  
-   <span data-ttu-id="c84b2-113">模型</span><span class="sxs-lookup"><span data-stu-id="c84b2-113">Model</span></span>  
  
-   <span data-ttu-id="c84b2-114">根节点</span><span class="sxs-lookup"><span data-stu-id="c84b2-114">Root node</span></span>  
  
-   <span data-ttu-id="c84b2-115">文件夹或实体</span><span class="sxs-lookup"><span data-stu-id="c84b2-115">Folders or entities</span></span>  
  
-   <span data-ttu-id="c84b2-116">字段</span><span class="sxs-lookup"><span data-stu-id="c84b2-116">Fields</span></span>  
  
 <span data-ttu-id="c84b2-117">最初，对模型项的访问权限是通过对模型本身设置的角色分配继承的。</span><span class="sxs-lookup"><span data-stu-id="c84b2-117">Initially, permission to access to model items is inherited through role assignments that are set on the model itself.</span></span> <span data-ttu-id="c84b2-118">有权查看报表管理器中文件夹内的模型的用户可以查看该模型中的所有项。</span><span class="sxs-lookup"><span data-stu-id="c84b2-118">A user who has permission to view a model in a folder in Report Manager can view all of the items in the model.</span></span>  
  
 <span data-ttu-id="c84b2-119">如果您应用模型项安全性，则必须针对根节点至少创建一个角色分配。</span><span class="sxs-lookup"><span data-stu-id="c84b2-119">If you apply model item security, you must create at least one role assignment on the root node.</span></span> <span data-ttu-id="c84b2-120">根节点上这个最初的角色分配会成为新的被继承权限来源。</span><span class="sxs-lookup"><span data-stu-id="c84b2-120">This initial role assignment on the root node becomes the new source of inherited permissions.</span></span> <span data-ttu-id="c84b2-121">根节点上的角色分配会自动由模型层次结构中的所有项继承。</span><span class="sxs-lookup"><span data-stu-id="c84b2-121">The role assignment on the root node is automatically inherited by all items in the model hierarchy.</span></span>  
  
 <span data-ttu-id="c84b2-122">若要进一步自定义有关数据浏览的权限，可以改变针对文件夹和实体的权限。</span><span class="sxs-lookup"><span data-stu-id="c84b2-122">To further customize permissions on data exploration, you can vary permissions on folders and entities.</span></span> <span data-ttu-id="c84b2-123">最后，可以针对单个字段设置权限。</span><span class="sxs-lookup"><span data-stu-id="c84b2-123">Finally, you can set permissions on individual fields.</span></span>  
  
 <span data-ttu-id="c84b2-124">为了更方便地维护角色分配，请仅对文件夹或实体设置权限，而不要对单个字段设置权限。</span><span class="sxs-lookup"><span data-stu-id="c84b2-124">To make role assignments easier to maintain, set permissions only on folders or entities rather than individual fields.</span></span> <span data-ttu-id="c84b2-125">您不能搜索您所创建的角色分配。</span><span class="sxs-lookup"><span data-stu-id="c84b2-125">You cannot search for role assignments that you create.</span></span> <span data-ttu-id="c84b2-126">如果对特定字段设置了安全性，而在以后需要更新安全设置，则必须浏览模型命名空间来查找您所保护的字段。</span><span class="sxs-lookup"><span data-stu-id="c84b2-126">If you set security on specific fields and you want to update the security settings later, you must click through the model namespace to find the fields you secured.</span></span>  
  
 <span data-ttu-id="c84b2-127">首先，针对根节点创建一个角色分配，然后针对实体和文件夹创建其他角色分配。</span><span class="sxs-lookup"><span data-stu-id="c84b2-127">To get started, create a role assignment on the root node and then create additional role assignments on entities and folders.</span></span> <span data-ttu-id="c84b2-128">若要清除模型项安全性，请清除与 **“单独保护此模型的各项”** 相对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="c84b2-128">To clear model item security, clear the check box for **Secure individual model items independently for this model**.</span></span> <span data-ttu-id="c84b2-129">清除该复选框会恢复到最初从该模型继承的权限。</span><span class="sxs-lookup"><span data-stu-id="c84b2-129">Clearing the check box reverts back to the initial permissions that are inherited from the model.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c84b2-130">导航</span><span class="sxs-lookup"><span data-stu-id="c84b2-130">Navigation</span></span>  
 <span data-ttu-id="c84b2-131">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="c84b2-131">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a><span data-ttu-id="c84b2-132">打开报表的“常规属性”页</span><span class="sxs-lookup"><span data-stu-id="c84b2-132">To open the General properties page for a report</span></span>  
  
1.  <span data-ttu-id="c84b2-133">打开报表管理器，找到您要为其配置模型项安全性的模型。</span><span class="sxs-lookup"><span data-stu-id="c84b2-133">Open Report Manager, and locate the model for which you want to configure security for model items.</span></span>  
  
2.  <span data-ttu-id="c84b2-134">悬停在该模型之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="c84b2-134">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="c84b2-135">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="c84b2-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="c84b2-136">这会打开该模型的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="c84b2-136">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="c84b2-137">选择 **“模型项安全性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c84b2-137">Select the **Model Item Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c84b2-138">选项</span><span class="sxs-lookup"><span data-stu-id="c84b2-138">Options</span></span>  
 <span data-ttu-id="c84b2-139">**“单独保护此模型的各项”**</span><span class="sxs-lookup"><span data-stu-id="c84b2-139">**Secure individual model items independently for this model**</span></span>  
 <span data-ttu-id="c84b2-140">单击此复选框可以启用模型项安全性。</span><span class="sxs-lookup"><span data-stu-id="c84b2-140">Click this check box to enable model item security.</span></span>  
  
 <span data-ttu-id="c84b2-141">**指定模型中各模型项的安全性**</span><span class="sxs-lookup"><span data-stu-id="c84b2-141">**Specify security for individual model items in the mode**</span></span>  
 <span data-ttu-id="c84b2-142">显示模型中的所有项。</span><span class="sxs-lookup"><span data-stu-id="c84b2-142">Shows all of the items in a model.</span></span> <span data-ttu-id="c84b2-143">您可以浏览模型命名空间来选择要保护的项。</span><span class="sxs-lookup"><span data-stu-id="c84b2-143">You can navigate the model namespace to select the item you want to secure.</span></span> <span data-ttu-id="c84b2-144">一次只能选择一个项。</span><span class="sxs-lookup"><span data-stu-id="c84b2-144">You can only select one item at a time.</span></span> <span data-ttu-id="c84b2-145">请确保先针对根节点创建第一个角色分配，然后再针对其他实体和文件夹创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="c84b2-145">Be sure to create the first role assignment on the root node before proceeding to other entities and folders.</span></span>  
  
 <span data-ttu-id="c84b2-146">**从父项继承权限**</span><span class="sxs-lookup"><span data-stu-id="c84b2-146">**Inherit permissions from the parent item**</span></span>  
 <span data-ttu-id="c84b2-147">单击此项可以继承父项的安全设置。</span><span class="sxs-lookup"><span data-stu-id="c84b2-147">Click this option to inherit the security settings of the parent item.</span></span>  
  
 <span data-ttu-id="c84b2-148">**为以下用户和组(用分号分隔)分配读取权限**</span><span class="sxs-lookup"><span data-stu-id="c84b2-148">**Assign read permission to the following users and groups (semi-colon separated)**</span></span>  
 <span data-ttu-id="c84b2-149">单击此项可以指定要为其定义访问权限的用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="c84b2-149">Click this option to specify the user or group account for which you are defining access.</span></span> <span data-ttu-id="c84b2-150">如果使用默认安全性，则用户帐户和组帐户为 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="c84b2-150">If you are using default security, the user and group accounts are Windows domain accounts.</span></span> <span data-ttu-id="c84b2-151">按以下格式指定帐户： \* \<domain> \\<帐户 \> \*。</span><span class="sxs-lookup"><span data-stu-id="c84b2-151">Specify the accounts in this format: *\<domain>\\<account\>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84b2-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c84b2-152">See Also</span></span>  
 [<span data-ttu-id="c84b2-153">Management Studio 中报表服务器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="c84b2-153">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
