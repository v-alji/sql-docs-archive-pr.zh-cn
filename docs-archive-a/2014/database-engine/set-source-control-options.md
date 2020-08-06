---
title: 设置源代码管理选项 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d4ca19180a7291763780f300172bb2292a98c8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577818"
---
# <a name="set-source-control-options"></a><span data-ttu-id="8f02c-102">设置源代码管理选项</span><span class="sxs-lookup"><span data-stu-id="8f02c-102">Set Source Control Options</span></span>
  <span data-ttu-id="8f02c-103">在利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中内置的源代码管理功能之前，应针对您工作中所处的各种环境对源代码管理选项进行配置。</span><span class="sxs-lookup"><span data-stu-id="8f02c-103">Before you take advantage of the source control features built into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you should configure your source control options for the various environments in which you work.</span></span>  
  
 <span data-ttu-id="8f02c-104">您可以通过使用 "**选项**" 对话框配置一个或多个源代码管理角色来配置源代码管理选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-104">You configure source control options by using the **Options** dialog box to configure one or more source control roles.</span></span> <span data-ttu-id="8f02c-105">组成角色的内容包括：对使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 时所采用设置的常规说明，以及与该设置关联的源代码管理选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-105">A role consists of a general description of the setting in which you use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and the source control options associated with that setting.</span></span>  
  
 <span data-ttu-id="8f02c-106">例如，如果您是独立的数据库开发人员，则在将文件签入后使其继续保持签出状态，通常不会产生与其他用户的冲突。</span><span class="sxs-lookup"><span data-stu-id="8f02c-106">For example, if you are an independent database developer, you generally do not create conflicts with other users by keeping files checked out after you check them in.</span></span> <span data-ttu-id="8f02c-107">因此，[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 定义了“独立开发人员”角色。</span><span class="sxs-lookup"><span data-stu-id="8f02c-107">Consequently, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] defines an Independent Developer role.</span></span> <span data-ttu-id="8f02c-108">对于此角色， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 会自动选择 "**签入时使项保持签出状态**" 选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-108">For this role, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] automatically selects the **Keep items checked out when checking in** option.</span></span>  
  
 <span data-ttu-id="8f02c-109">因为可以定义和自定义角色，因此您不必在每次从一个设置移动到另一个设置时全部重新配置源代码管理选项，即可采用不同的开发设置进行工作。</span><span class="sxs-lookup"><span data-stu-id="8f02c-109">Because you can define and customize roles, you can work in varying development settings without having to completely reconfigure source control every time you move from one setting to another.</span></span>  
  
### <a name="to-set-source-control-options"></a><span data-ttu-id="8f02c-110">设置源代码管理选项</span><span class="sxs-lookup"><span data-stu-id="8f02c-110">To set source control options</span></span>  
  
1.  <span data-ttu-id="8f02c-111">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="8f02c-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="8f02c-112">在 "**选项**" 对话框中，展开 "**源代码管理**"，然后单击 "**插件选择**" 页。</span><span class="sxs-lookup"><span data-stu-id="8f02c-112">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
     <span data-ttu-id="8f02c-113">**当前源代码管理插件**</span><span class="sxs-lookup"><span data-stu-id="8f02c-113">**Current source control plug-in**</span></span>  
     <span data-ttu-id="8f02c-114">从此列表中选择要使用的源代码管理。</span><span class="sxs-lookup"><span data-stu-id="8f02c-114">Select the source control you want to use from this list.</span></span> <span data-ttu-id="8f02c-115">必须在此计算机上安装源代码管理产品客户端，才能在该列表中显示源代码管理产品。</span><span class="sxs-lookup"><span data-stu-id="8f02c-115">The source control product client must be installed on this computer to appear on the list.</span></span> <span data-ttu-id="8f02c-116">如果计算机上没有安装源代码管理客户端，则唯一可用的选项是“无”。</span><span class="sxs-lookup"><span data-stu-id="8f02c-116">If no source control clients are installed on the computer, the only selection available will be None.</span></span> <span data-ttu-id="8f02c-117">如果您安装了 Microsoft Source Safe，则会显示以下插件：</span><span class="sxs-lookup"><span data-stu-id="8f02c-117">If you have installed Microsoft Source Safe, then the following plug ins are displayed:</span></span>  
  
    -   <span data-ttu-id="8f02c-118">Microsoft Visual SourceSafe</span><span class="sxs-lookup"><span data-stu-id="8f02c-118">Microsoft Visual SourceSafe</span></span>  
  
    -   <span data-ttu-id="8f02c-119">Microsoft Visual SourceSafe(Internet)</span><span class="sxs-lookup"><span data-stu-id="8f02c-119">Microsoft Visual SourceSafe(Internet)</span></span>  
  
3.  <span data-ttu-id="8f02c-120">为要使用的每个源代码管理角色设置登录凭据。</span><span class="sxs-lookup"><span data-stu-id="8f02c-120">Set login credentials for each source control role that you want to use.</span></span> <span data-ttu-id="8f02c-121">只有当安装了源代码管理插件时，此页才可用。</span><span class="sxs-lookup"><span data-stu-id="8f02c-121">This page is only available if a source control plug-in is installed.</span></span>  
  
     <span data-ttu-id="8f02c-122">**角色描述**</span><span class="sxs-lookup"><span data-stu-id="8f02c-122">**Role Description**</span></span>  
     <span data-ttu-id="8f02c-123">选择这些角色之一，将自动选择相应的源代码管理选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-123">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
    |<span data-ttu-id="8f02c-124">角色</span><span class="sxs-lookup"><span data-stu-id="8f02c-124">Role</span></span>|<span data-ttu-id="8f02c-125">说明</span><span class="sxs-lookup"><span data-stu-id="8f02c-125">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="8f02c-126">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="8f02c-126">**Visual SourceSafe**</span></span>|<span data-ttu-id="8f02c-127">指定您要使用 Visual SourceSafe 用户最常使用的设置 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8f02c-127">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="8f02c-128">**独立开发人员**</span><span class="sxs-lookup"><span data-stu-id="8f02c-128">**Independent Developer**</span></span>|<span data-ttu-id="8f02c-129">指定您是在独立工作。</span><span class="sxs-lookup"><span data-stu-id="8f02c-129">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="8f02c-130">**自定义**</span><span class="sxs-lookup"><span data-stu-id="8f02c-130">**Custom**</span></span>|<span data-ttu-id="8f02c-131">指定您已为特定角色修改了设置。</span><span class="sxs-lookup"><span data-stu-id="8f02c-131">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="8f02c-132">**执行后台状态更新**</span><span class="sxs-lookup"><span data-stu-id="8f02c-132">**Perform background status updates**</span></span>  
     <span data-ttu-id="8f02c-133">在项的状态改变时，自动更新解决方案资源管理器中源代码管理信号图标。</span><span class="sxs-lookup"><span data-stu-id="8f02c-133">Automatically updates the source control signal icons in Solution Explorer as an item's status changes.</span></span> <span data-ttu-id="8f02c-134">如果在执行占用大量服务器资源的操作时（尤其是在从源代码管理中打开解决方案或项目时）遇到延迟，则清除此复选框可能会改进性能。</span><span class="sxs-lookup"><span data-stu-id="8f02c-134">If you experience delays when performing server-intensive operations, especially when opening a solution or project from source control, clearing this check box could improve performance.</span></span>  
  
     <span data-ttu-id="8f02c-135">**登录 ID**</span><span class="sxs-lookup"><span data-stu-id="8f02c-135">**Login ID**</span></span>  
     <span data-ttu-id="8f02c-136">指定要用来登录源代码管理提供程序的用户名。</span><span class="sxs-lookup"><span data-stu-id="8f02c-136">Specifies the user name to use to log in to the source control provider.</span></span> <span data-ttu-id="8f02c-137">如果源代码管理提供程序支持该名称，则会在**登录**对话框中自动填充此名称，以到达源代码管理服务器。</span><span class="sxs-lookup"><span data-stu-id="8f02c-137">If supported by your source control provider, this name will be filled in automatically in the **Login** dialog box to reach your source control server.</span></span> <span data-ttu-id="8f02c-138">若要激活此选项，请通过使用源代码管理提供程序的管理员程序来禁用用户自动登录，再重新启动 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f02c-138">To make this option active, disable automatic user logins by using your source control provider's administrator program, and then restart [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="8f02c-139">**高级**</span><span class="sxs-lookup"><span data-stu-id="8f02c-139">**Advanced**</span></span>  
     <span data-ttu-id="8f02c-140">显示用于向源代码管理添加项的其他选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-140">Displays additional options for adding items to source control.</span></span> <span data-ttu-id="8f02c-141">这些选项因源代码管理提供程序的不同而有所差异。</span><span class="sxs-lookup"><span data-stu-id="8f02c-141">These options vary depending on your source control provider.</span></span> <span data-ttu-id="8f02c-142">源代码管理程序提供了有关这些选项的帮助。</span><span class="sxs-lookup"><span data-stu-id="8f02c-142">Help for these options is provided by the source control program.</span></span>  
  
4.  <span data-ttu-id="8f02c-143">选择 "**环境**" 页。</span><span class="sxs-lookup"><span data-stu-id="8f02c-143">Select the **Environment** page.</span></span>  
  
5.  <span data-ttu-id="8f02c-144">在 "**源代码管理环境设置**" 框中，选择要设置源代码管理选项的角色。</span><span class="sxs-lookup"><span data-stu-id="8f02c-144">In the **Source Control Environment Settings** box, select the role on which you want to set source control options.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8f02c-145">将自动为您选定的角色选择默认的源代码管理选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-145">automatically selects the default source control options for the role you have selected.</span></span> <span data-ttu-id="8f02c-146">如果清除了任何默认选项，则 "**源代码管理环境设置**" 框将显示 "**自定义**" 选项，以指示你已自定义了最初选择的角色。</span><span class="sxs-lookup"><span data-stu-id="8f02c-146">If you clear any of the default options, the **Source Control Environment Settings** box displays the **Custom** option to indicate that you have customized the originally selected role.</span></span>  
  
     <span data-ttu-id="8f02c-147">**源代码管理环境设置**</span><span class="sxs-lookup"><span data-stu-id="8f02c-147">**Source Control Environment Settings**</span></span>  
     <span data-ttu-id="8f02c-148">指定要使用的角色。</span><span class="sxs-lookup"><span data-stu-id="8f02c-148">Specifies the role that you want to use.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8f02c-149">定义了以下角色。</span><span class="sxs-lookup"><span data-stu-id="8f02c-149">defines the following roles.</span></span>  
  
    |<span data-ttu-id="8f02c-150">角色</span><span class="sxs-lookup"><span data-stu-id="8f02c-150">Role</span></span>|<span data-ttu-id="8f02c-151">说明</span><span class="sxs-lookup"><span data-stu-id="8f02c-151">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="8f02c-152">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="8f02c-152">**Visual SourceSafe**</span></span>|<span data-ttu-id="8f02c-153">指定您要使用 Visual SourceSafe 用户最常使用的设置 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8f02c-153">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="8f02c-154">**独立开发人员**</span><span class="sxs-lookup"><span data-stu-id="8f02c-154">**Independent Developer**</span></span>|<span data-ttu-id="8f02c-155">指定您是在独立工作。</span><span class="sxs-lookup"><span data-stu-id="8f02c-155">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="8f02c-156">**自定义**</span><span class="sxs-lookup"><span data-stu-id="8f02c-156">**Custom**</span></span>|<span data-ttu-id="8f02c-157">指定您已为特定角色修改了设置。</span><span class="sxs-lookup"><span data-stu-id="8f02c-157">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="8f02c-158">选择这些角色之一，将自动选择相应的源代码管理选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-158">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
     <span data-ttu-id="8f02c-159">**签入时使项保持签出状态**</span><span class="sxs-lookup"><span data-stu-id="8f02c-159">**Keep items checked out when checking in**</span></span>  
     <span data-ttu-id="8f02c-160">指定在签入项以更新源代码管理存储区时，这些项将对您保持签出状态。</span><span class="sxs-lookup"><span data-stu-id="8f02c-160">Specifies that when you check in items to update the source control store, the items should remain checked out to you.</span></span> <span data-ttu-id="8f02c-161">如果要为特定签入更改此选项，请单击 "**签入**" 对话框中的 "**选项**" 箭头，然后清除 "**保持签出状态**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-161">If you want to change this option for a specific check-in, click the **Options** arrow in the **Check in** dialog box, and then clear the **Keep checked out** check box.</span></span>  
  
     <span data-ttu-id="8f02c-162">**签入的项**</span><span class="sxs-lookup"><span data-stu-id="8f02c-162">**Checked-in items**</span></span>  
     <span data-ttu-id="8f02c-163">显示一个选项列表，该列表指定在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 您尝试编辑未签出的项时应如何工作。下表描述了可用的选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-163">Displays a list of options that specify how [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] should behave when you attempt to edit an item that is not checked out. The following tables describe the available options.</span></span>  
  
     <span data-ttu-id="8f02c-164">**保存**</span><span class="sxs-lookup"><span data-stu-id="8f02c-164">**Saving**</span></span>  
  
    |<span data-ttu-id="8f02c-165">操作</span><span class="sxs-lookup"><span data-stu-id="8f02c-165">Action</span></span>|<span data-ttu-id="8f02c-166">说明</span><span class="sxs-lookup"><span data-stu-id="8f02c-166">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="8f02c-167">**提示签出**</span><span class="sxs-lookup"><span data-stu-id="8f02c-167">**Prompt for check out**</span></span>|<span data-ttu-id="8f02c-168">显示 "**签出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-168">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="8f02c-169">**自动签出**</span><span class="sxs-lookup"><span data-stu-id="8f02c-169">**Check out automatically**</span></span>|<span data-ttu-id="8f02c-170">签出项而不显示 "**签出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-170">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="8f02c-171">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-171">This is the default option.</span></span>|  
    |<span data-ttu-id="8f02c-172">**另存为**</span><span class="sxs-lookup"><span data-stu-id="8f02c-172">**Save as**</span></span>|<span data-ttu-id="8f02c-173">另存为新文件。</span><span class="sxs-lookup"><span data-stu-id="8f02c-173">Saves as a new file.</span></span>|  
  
     <span data-ttu-id="8f02c-174">**正在编辑**</span><span class="sxs-lookup"><span data-stu-id="8f02c-174">**Editing**</span></span>  
  
    |<span data-ttu-id="8f02c-175">操作</span><span class="sxs-lookup"><span data-stu-id="8f02c-175">Action</span></span>|<span data-ttu-id="8f02c-176">说明</span><span class="sxs-lookup"><span data-stu-id="8f02c-176">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="8f02c-177">**提示签出**</span><span class="sxs-lookup"><span data-stu-id="8f02c-177">**Prompt for check out**</span></span>|<span data-ttu-id="8f02c-178">显示 "**签出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-178">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="8f02c-179">**提示以独占方式签出**</span><span class="sxs-lookup"><span data-stu-id="8f02c-179">**Prompt for exclusive checkouts**</span></span>|<span data-ttu-id="8f02c-180">显示 "**签出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-180">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="8f02c-181">**自动签出**</span><span class="sxs-lookup"><span data-stu-id="8f02c-181">**Check out automatically**</span></span>|<span data-ttu-id="8f02c-182">签出项而不显示 "**签出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f02c-182">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="8f02c-183">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-183">This is the default option.</span></span>|  
    |<span data-ttu-id="8f02c-184">**不执行任何操作**</span><span class="sxs-lookup"><span data-stu-id="8f02c-184">**Do nothing**</span></span>|<span data-ttu-id="8f02c-185">不签出文件。</span><span class="sxs-lookup"><span data-stu-id="8f02c-185">Does not check out the file.</span></span>|  
  
     <span data-ttu-id="8f02c-186">**允许编辑签入的项**</span><span class="sxs-lookup"><span data-stu-id="8f02c-186">**Allow checked-in items to be edited**</span></span>  
     <span data-ttu-id="8f02c-187">指定可以在内存中编辑签入的项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-187">Specifies that items that are checked in can be edited in memory.</span></span> <span data-ttu-id="8f02c-188">如果选中此复选框，则在您尝试编辑签入的项时，"**签出**" 对话框中将显示一个 "**编辑**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="8f02c-188">If you select this check box, an **Edit** button appears in the **Check Out** dialog box when you attempt to edit a checked-in item.</span></span> <span data-ttu-id="8f02c-189">单击此按钮后，即可编辑该项。</span><span class="sxs-lookup"><span data-stu-id="8f02c-189">After clicking this button, you can edit the item.</span></span> <span data-ttu-id="8f02c-190">如果尝试保存该项，则必须签出它或者将其保存到其他位置。</span><span class="sxs-lookup"><span data-stu-id="8f02c-190">If you attempt to save the item, you must check it out or save it to a different location.</span></span>  
  
     <span data-ttu-id="8f02c-191">**重置**</span><span class="sxs-lookup"><span data-stu-id="8f02c-191">**Reset**</span></span>  
     <span data-ttu-id="8f02c-192">将源代码管理确认对话框重置为其默认设置。</span><span class="sxs-lookup"><span data-stu-id="8f02c-192">Resets source control confirmation dialog boxes to their default settings.</span></span> <span data-ttu-id="8f02c-193">例如，如果在 "源代码管理" 对话框中选中了 "**不再显示此对话框**" 复选框，则选择 "**重置**" 选项会反转该操作。</span><span class="sxs-lookup"><span data-stu-id="8f02c-193">For example, if you have selected the **Don't show this dialog again** check box in a source control dialog box, selecting the **Reset** option reverses that action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f02c-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f02c-194">See Also</span></span>  
 <span data-ttu-id="8f02c-195">[源代码管理基础知识](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="8f02c-195">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="8f02c-196">[更改源代码管理连接](../../2014/database-engine/change-source-control-connections.md) </span><span class="sxs-lookup"><span data-stu-id="8f02c-196">[Change Source Control Connections](../../2014/database-engine/change-source-control-connections.md) </span></span>  
 [<span data-ttu-id="8f02c-197">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="8f02c-197">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
