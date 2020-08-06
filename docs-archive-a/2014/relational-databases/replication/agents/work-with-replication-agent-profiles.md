---
title: 使用复制代理配置文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc20451edfb1096fca7e468effb14df78b51f758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578137"
---
# <a name="work-with-replication-agent-profiles"></a><span data-ttu-id="f0a2d-102">使用复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-102">Work with Replication Agent Profiles</span></span>
  <span data-ttu-id="f0a2d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中处理复制代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-103">This topic describes how to work with Replication Agent Profiles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="f0a2d-104">每个复制代理的行为都受一组参数控制，这些参数是通过代理配置文件设置的。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-104">The behavior of each replication agent is controlled by a set of parameters that can be set through agent profiles.</span></span> <span data-ttu-id="f0a2d-105">每个代理都有一个默认配置文件，有些代理还有一些其他的预定义配置文件；每个代理每次只能使用一个配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-105">Each agent has a default profile, and some have additional predefined profiles; at a given time, only one profile is active for an agent.</span></span>  
  
 <span data-ttu-id="f0a2d-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f0a2d-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f0a2d-107">**处理复制代理配置文件，使用：**</span><span class="sxs-lookup"><span data-stu-id="f0a2d-107">**To work with Replication Agent Profiles, using:**</span></span>  
  
     [<span data-ttu-id="f0a2d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0a2d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   <span data-ttu-id="f0a2d-109">访问“代理配置文件”对话框</span><span class="sxs-lookup"><span data-stu-id="f0a2d-109">Access the Agent Profiles dialog box</span></span>  
  
    -   <span data-ttu-id="f0a2d-110">指定代理的配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-110">Specify a profile for an agent</span></span>  
  
    -   <span data-ttu-id="f0a2d-111">创建配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-111">Create a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-112">修改配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-112">Modify a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-113">删除配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-113">Delete a profile</span></span>  
  
     [<span data-ttu-id="f0a2d-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0a2d-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   <span data-ttu-id="f0a2d-115">创建配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-115">Create a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-116">修改配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-116">Modify a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-117">删除配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-117">Delete a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-118">在同步期间使用代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-118">Use agent profiles during synchronization</span></span>  
  
    -   <span data-ttu-id="f0a2d-119">Transact-SQL 示例</span><span class="sxs-lookup"><span data-stu-id="f0a2d-119">Transact-SQL example</span></span>  
  
     [<span data-ttu-id="f0a2d-120">复制管理对象</span><span class="sxs-lookup"><span data-stu-id="f0a2d-120">Replication Management Objects</span></span>](#RMOProcedure)  
  
    -   <span data-ttu-id="f0a2d-121">创建配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-121">Create a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-122">修改配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-122">Modify a profile</span></span>  
  
    -   <span data-ttu-id="f0a2d-123">删除配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-123">Delete a profile</span></span>  
  
-   <span data-ttu-id="f0a2d-124">**跟进：** [在更改代理参数后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-124">**Follow Up:**  [After Changing Agent Parameters](#FollowUp)</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f0a2d-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0a2d-125">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> <span data-ttu-id="f0a2d-126">从 SQL Server Management Studio 访问“代理配置文件”对话框</span><span class="sxs-lookup"><span data-stu-id="f0a2d-126">To access the Agent Profiles dialog box from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="f0a2d-127">在“分发服务器属性 - \<Distributor>”对话框的“常规”页面上，单击“配置文件默认值”  。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-127">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click **Profile Defaults**.</span></span>  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a><span data-ttu-id="f0a2d-128">从复制监视器访问“代理配置文件”对话框</span><span class="sxs-lookup"><span data-stu-id="f0a2d-128">To access the Agent Profiles dialog box from Replication Monitor</span></span>  
  
-   <span data-ttu-id="f0a2d-129">若要为所有代理打开此对话框，请右键单击发布服务器，再单击 **“代理配置文件”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-129">To open the dialog box for all agents, right-click a Publisher, and then click **Agent Profiles**.</span></span>  
  
-   <span data-ttu-id="f0a2d-130">为单个代理打开此对话框：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-130">To open the dialog box for a single agent:</span></span>  
  
    1.  <span data-ttu-id="f0a2d-131">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-131">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="f0a2d-132">对于分发代理配置文件和合并代理配置文件，请右键单击 **“所有订阅”** 选项卡上的订阅，再单击 **“代理配置文件”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-132">For Distribution Agent and Merge Agent profiles, right-click a subscription on the **All Subscriptions** tab, and then click **Agent Profile**.</span></span> <span data-ttu-id="f0a2d-133">对于其他代理，右键单击 **“代理”** 选项卡上的代理，然后单击 **“代理配置文件”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-133">For other agents, right-click the agent on the **Agents** tab, and then click **Agent Profile**.</span></span>  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> <span data-ttu-id="f0a2d-134">指定代理的配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-134">To specify a profile for an agent</span></span>  
  
1.  <span data-ttu-id="f0a2d-135">如果 **“代理配置文件”** 对话框中显示了多个代理的配置文件，请选择一个代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-135">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="f0a2d-136">在 **“代理配置文件”** 网格的 **“作为新项的默认值”** 列中选择一个配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-136">Select a profile in the **Default for new** column of the **Agent profiles** grid.</span></span> <span data-ttu-id="f0a2d-137">默认情况下，该配置文件只应用于新发布和订阅的代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-137">By default, the profile is only applied to agents for new publications and subscriptions.</span></span>  
  
3.  <span data-ttu-id="f0a2d-138">若要指定用于现有发布或订阅且属于选定类型的所有代理都使用该配置文件，请单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-138">To specify that all agents of the selected type for existing publications or subscriptions should use this profile, click **Change existing agents**.</span></span>  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> <span data-ttu-id="f0a2d-139">查看和编辑与配置文件关联的参数</span><span class="sxs-lookup"><span data-stu-id="f0a2d-139">To view and edit the parameters associated with a profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-140">如果 **“代理配置文件”** 对话框中显示了多个代理的配置文件，请选择一个代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-140">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="f0a2d-141">单击配置文件旁边的属性按钮 (...)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-141">Click the properties button (**...**) next to a profile.</span></span>  
  
3.  <span data-ttu-id="f0a2d-142">查看“\<ProfileName> 配置文件属性”对话框中的参数和值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-142">View the parameters and values in the **\<ProfileName> Profile Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="f0a2d-143">用户定义配置文件中的参数可以编辑，但预定义系统配置文件中的参数不可编辑。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-143">Parameters in user-defined profiles can be edited; parameters in predefined system profiles cannot.</span></span>  
  
    -   <span data-ttu-id="f0a2d-144">若要查看代理的所有参数，请清除 **“仅显示此配置文件中使用的参数”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-144">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="f0a2d-145">有关代理参数的信息，请参阅本主题末尾处的链接。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-145">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
4.  <span data-ttu-id="f0a2d-146">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-146">Click **Close**.</span></span>  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> <span data-ttu-id="f0a2d-147">创建用户定义的配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-147">To create a user-defined profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-148">如果 **“代理配置文件”** 对话框中显示了多个代理的配置文件，请选择一个代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-148">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="f0a2d-149">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-149">Click **New**.</span></span>  
  
3.  <span data-ttu-id="f0a2d-150">在 **“新建代理配置文件”** 初始化对话框中，选择一个作为新配置文件基础的现有配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-150">In the **New Agent Profile** initialization dialog box, select an existing profile on which to base the new profile.</span></span>  
  
4.  <span data-ttu-id="f0a2d-151">在 **“新建代理配置文件”** 对话框的 **“名称”** 和 **“说明”** 文本框中输入相应值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-151">In the **New Agent Profile** dialog box, enter values in the **Name** and **Description** text boxes.</span></span>  
  
5.  <span data-ttu-id="f0a2d-152">修改参数以调整配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-152">Modify parameters to tailor the profile.</span></span> <span data-ttu-id="f0a2d-153">若要查看代理的所有参数，请清除 **“仅显示此配置文件中使用的参数”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-153">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="f0a2d-154">有关代理参数的信息，请参阅本主题末尾处的链接。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-154">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> <span data-ttu-id="f0a2d-155">删除用户定义的配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-155">To delete a user-defined profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-156">如果 **“代理配置文件”** 对话框中显示了多个代理的配置文件，请选择一个代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-156">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="f0a2d-157">如果一个配置文件与一个或多个代理相关联，请更改这些代理的配置文件：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-157">If a profile is associated with one or more agents, change the profile for those agents:</span></span>  
  
    1.  <span data-ttu-id="f0a2d-158">在 **“代理配置文件”** 网格中选择其他配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-158">Select a different profile in the **Agent profiles** grid.</span></span>  
  
    2.  <span data-ttu-id="f0a2d-159">单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-159">Click **Change existing agents**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f0a2d-160">此操作将更改用于现有发布或订阅且属于选定类型的所有代理的配置文件，而不只更改那些使用要删除的配置文件的代理的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-160">This will change the profile for all agents of the selected type for existing publications or subscriptions, not only the ones using the profile you want to delete.</span></span>  
  
3.  <span data-ttu-id="f0a2d-161">选择要删除的配置文件，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-161">Select the profile you want to delete, and then click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f0a2d-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0a2d-162">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> <span data-ttu-id="f0a2d-163">创建一个新的代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-163">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-164">在分发服务器上，执行 [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-164">At the Distributor, execute [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-165">为指定 **@name** ，值为**1** ，为指定 **@profile_type** 以下值之一 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-165">Specify **@name**, a value of **1** for **@profile_type**, and one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="f0a2d-166">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-166">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="f0a2d-171">如果此配置文件将成为此复制代理类型的新默认配置文件，请将 **@profile_type** 的值指定为 **@default**。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-171">If this profile will become the new default profile for its type of replication agent, specify a value of **1** for **@default**.</span></span> <span data-ttu-id="f0a2d-172">使用 output 参数返回新配置文件的标识符 **@profile_id** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-172">The identifier for the new profile is returned using the **@profile_id** output parameter.</span></span> <span data-ttu-id="f0a2d-173">这将会使用基于给定代理类型的默认配置文件的配置文件参数集创建新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-173">This creates a new profile with a set of profile parameters based on the default profile for the given agent type.</span></span>  
  
2.  <span data-ttu-id="f0a2d-174">在已创建新配置文件后，可添加、删除或修改默认参数以自定义该配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-174">After the new profile has been created, add, remove, or modify the default parameters to customize the profile.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> <span data-ttu-id="f0a2d-175">修改现有代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-175">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-176">在分发服务器上，执行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-176">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-177">为指定下列值之一 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-177">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="f0a2d-178">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-178">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="f0a2d-183">这将返回指定类型的代理的所有配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-183">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="f0a2d-184">请记下要更改的配置文件在结果集中的 **profile_id** 值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-184">Note the value of **profile_id** in the result set for the profile to change.</span></span>  
  
2.  <span data-ttu-id="f0a2d-185">在分发服务器上，执行 [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-185">At the Distributor, execute [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql).</span></span> <span data-ttu-id="f0a2d-186">为指定步骤1中的配置文件标识符 **@profile_id** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-186">Specify the profile identifier from step 1 for **@profile_id**.</span></span> <span data-ttu-id="f0a2d-187">这将返回该配置文件的所有参数。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-187">This returns all parameters for the profile.</span></span> <span data-ttu-id="f0a2d-188">请记下要从配置文件中修改或删除的任何参数的名称。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-188">Note the name of any parameters to modify or remove from the profile.</span></span>  
  
3.  <span data-ttu-id="f0a2d-189">若要更改配置文件中的参数值，请执行 [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-189">To change the value of a parameter in a profile, execute [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-190">为指定步骤1中的配置文件标识符，为指定 **@profile_id** 要更改的参数的名称，并为的 **@property** 参数指定新值 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-190">Specify the profile identifier from step 1 for **@profile_id**, the name of the parameter to change for **@property**, and a new value for the parameter for **@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0a2d-191">您不能将现有的代理配置文件更改为代理的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-191">You cannot change an existing agent profile to become the default profile for an agent.</span></span> <span data-ttu-id="f0a2d-192">相反，您必须创建一个新的配置文件以作为默认配置文件，如前面的过程所示。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-192">You must instead create a new profile as the default profile, as shown in the previous procedure.</span></span>  
  
4.  <span data-ttu-id="f0a2d-193">若要从配置文件中删除参数，请执行 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-193">To remove a parameter from a profile, execute [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql).</span></span> <span data-ttu-id="f0a2d-194">为指定步骤1中的配置文件标识符 **@profile_id** ，并指定要为其删除的参数的名称 **@parameter_name** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-194">Specify the profile identifier from step 1 for **@profile_id** and the name of the parameter to remove for **@parameter_name**.</span></span>  
  
5.  <span data-ttu-id="f0a2d-195">若要向配置文件添加新的参数，必须执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-195">To add a new parameter to a profile, you must do the following:</span></span>  
  
    -   <span data-ttu-id="f0a2d-196">查询分发服务器上的 [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) 表以确定可为每个代理类型设置哪些配置文件参数。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-196">Query the [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) table at the Distributor to determine which profile parameters can be set for each agent type.</span></span>  
  
    -   <span data-ttu-id="f0a2d-197">在分发服务器上，执行 [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-197">At the Distributor, execute [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql).</span></span> <span data-ttu-id="f0a2d-198">为指定步骤1中的配置文件标识符，为指定 **@profile_id** 要添加的有效参数的名称，并为指定 **@parameter_name** 参数的值 **@parameter_value** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-198">Specify the profile identifier from step 1 for **@profile_id**, the name of a valid parameter to add for **@parameter_name**, and the value of the parameter for **@parameter_value**.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> <span data-ttu-id="f0a2d-199">删除代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-199">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-200">在分发服务器上，执行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-200">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-201">为指定下列值之一 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-201">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="f0a2d-202">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-202">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="f0a2d-207">这将返回指定类型的代理的所有配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-207">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="f0a2d-208">请记下要删除的配置文件在结果集中的 **profile_id** 值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-208">Note the value of **profile_id** in the result set for the profile to remove.</span></span>  
  
2.  <span data-ttu-id="f0a2d-209">在分发服务器上，执行 [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-209">At the Distributor, execute [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-210">为指定步骤1中的配置文件标识符 **@profile_id** 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-210">Specify the profile identifier from step 1 for **@profile_id**.</span></span>  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> <span data-ttu-id="f0a2d-211">在同步期间使用代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-211">To use agent profiles during synchronization</span></span>  
  
1.  <span data-ttu-id="f0a2d-212">在分发服务器上，执行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-212">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="f0a2d-213">为指定下列值之一 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-213">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="f0a2d-214">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-214">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="f0a2d-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="f0a2d-219">这将返回指定类型的代理的所有配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-219">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="f0a2d-220">请注意 `profile_name` 要使用的配置文件在结果集中的值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-220">Note the value of `profile_name` in the result set for the profile to use.</span></span>  
  
2.  <span data-ttu-id="f0a2d-221">如果代理是从代理作业启动的，则编辑用于启动该代理的作业步骤，以指定 `profile_name` 在步骤1中的**ProfileName**命令行参数之后获取的值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-221">If the agent is started from an agent job, edit the job step that starts the agent to specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span> <span data-ttu-id="f0a2d-222">有关详细信息，请参阅[查看和修改复制代理命令提示符参数 &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-222">For more information, see [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).</span></span>  
  
3.  <span data-ttu-id="f0a2d-223">从命令提示符处启动代理时，请在 `profile_name` **-ProfileName**命令行参数后指定在步骤1中获得的值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-223">When starting the agent from the command prompt, specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f0a2d-224">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f0a2d-224">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f0a2d-225">此示例将为名为 **custom_merge**的合并代理创建自定义配置文件，更改 **-UploadReadChangesPerBatch** 参数的值，添加新的 **-ExchangeType** 参数，并返回有关创建的配置文件的信息。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-225">This example creates a custom profile for the Merge Agent named **custom_merge**, changes the value of the **-UploadReadChangesPerBatch** parameter, adds a new **-ExchangeType** parameter, and returns information on the profile that is created.</span></span>  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="f0a2d-226">使用 RMO</span><span class="sxs-lookup"><span data-stu-id="f0a2d-226">Using RMO</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> <span data-ttu-id="f0a2d-227">创建一个新的代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-227">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-228">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类的实例创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-228">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f0a2d-229">创建的 <xref:Microsoft.SqlServer.Replication.AgentProfile> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-229">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span>  
  
3.  <span data-ttu-id="f0a2d-230">设置对象的下列属性：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-230">Set the following properties on the object:</span></span>  
  
    -   <span data-ttu-id="f0a2d-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - 配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - the name for the profile.</span></span>  
  
    -   <span data-ttu-id="f0a2d-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - 一个 <xref:Microsoft.SqlServer.Replication.AgentType> 值，该值指定要为其创建该配置文件的复制代理的类型。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - an <xref:Microsoft.SqlServer.Replication.AgentType> value that specifies the type of replication agent for which the profile is being created.</span></span>  
  
    -   <span data-ttu-id="f0a2d-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 步骤 1 中创建的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
    -   <span data-ttu-id="f0a2d-234">（可选） <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - 配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-234">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - a description of the profile.</span></span>  
  
    -   <span data-ttu-id="f0a2d-235">（可选）<xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - 如果默认情况下此 <xref:Microsoft.SqlServer.Replication.AgentType> 的所有新代理作业都将使用此配置文件，则将此属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-235">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - set this property to `true` if all new agent jobs for this <xref:Microsoft.SqlServer.Replication.AgentType> will use this profile by default.</span></span>  
  
4.  <span data-ttu-id="f0a2d-236">调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> 方法以在服务器上创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-236">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> method to create the profile on the server.</span></span>  
  
5.  <span data-ttu-id="f0a2d-237">在服务器上存在此配置文件后，可以通过添加、删除或更改复制代理参数的值来对该配置文件进行自定义。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-237">Once the profile exists on the server, you can customize it by adding, removing, or changing the values of replication agent parameters.</span></span>  
  
6.  <span data-ttu-id="f0a2d-238">若要将此配置文件分配给现有的复制代理作业，请调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-238">To assign the profile to an existing replication agent job, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> method.</span></span> <span data-ttu-id="f0a2d-239">为 *distributionDBName* 传递分发数据库的名称并为 *agentID*传递作业 ID。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-239">Pass the name of the distribution database for *distributionDBName* and the ID of the job for *agentID*.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> <span data-ttu-id="f0a2d-240">修改现有代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-240">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-241">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类的实例创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-241">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f0a2d-242">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-242">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="f0a2d-243">传递步骤 1 中创建的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-243">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object created in step 1.</span></span>  
  
3.  <span data-ttu-id="f0a2d-244">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-244">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="f0a2d-245">如果此方法返回 `false`，请验证分发服务器是否存在。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-245">If this method returns `false`, verify that the Distributor exists.</span></span>  
  
4.  <span data-ttu-id="f0a2d-246">调用 <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-246">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> method.</span></span> <span data-ttu-id="f0a2d-247">传递一个 <xref:Microsoft.SqlServer.Replication.AgentType> 值以将返回的配置文件缩小至指定类型的复制代理。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-247">Pass an <xref:Microsoft.SqlServer.Replication.AgentType> value to narrow down the returned profiles to a specific type of replication agent.</span></span>  
  
5.  <span data-ttu-id="f0a2d-248">从返回的 <xref:Microsoft.SqlServer.Replication.AgentProfile> 中获取所需的 <xref:System.Collections.ArrayList>对象，其中此对象的 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> 属性与配置文件名相匹配。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-248">Get the desired <xref:Microsoft.SqlServer.Replication.AgentProfile> object from the returned <xref:System.Collections.ArrayList>, where the <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> property of the object matches the profile name.</span></span>  
  
6.  <span data-ttu-id="f0a2d-249">调用 <xref:Microsoft.SqlServer.Replication.AgentProfile> 的以下方法之一更改配置文件：</span><span class="sxs-lookup"><span data-stu-id="f0a2d-249">Call one of the following methods of <xref:Microsoft.SqlServer.Replication.AgentProfile> to change the profile:</span></span>  
  
    -   <span data-ttu-id="f0a2d-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - 向此配置文件添加支持的参数，其中 *name* 为复制代理参数的名称， *value* 为指定的值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - adds a supported parameter to the profile, where *name* is the name of the replication agent parameter and *value* is the specified value.</span></span> <span data-ttu-id="f0a2d-251">若要枚举给定代理类型的所有支持的代理参数，请调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-251">To enumerate all supported agent parameters for a given agent type, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="f0a2d-252">此方法返回表示所有支持参数的一个 <xref:System.Collections.ArrayList> 对象的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> 。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-252">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent all supported parameters.</span></span>  
  
    -   <span data-ttu-id="f0a2d-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - 删除配置文件中的某个现有参数，其中 *name* 为复制代理参数的名称。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - removes an existing parameter from the profile, where *name* is the name of the replication agent parameter.</span></span> <span data-ttu-id="f0a2d-254">若要枚举为配置文件定义的所有当前代理参数，请调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-254">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="f0a2d-255">此方法返回一个 <xref:System.Collections.ArrayList> 对象的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> ，表示此配置文件的现有参数。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-255">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span>  
  
    -   <span data-ttu-id="f0a2d-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - 更改配置文件中现有参数的设置，其中 *name* 为代理参数的名称， *newValue* 为更改参数时的目标值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - changes the setting of an existing parameter in the profile, where *name* is the name of the agent parameter and *newValue* is the value to which the parameter is being changed.</span></span> <span data-ttu-id="f0a2d-257">若要枚举为配置文件定义的所有当前代理参数，请调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-257">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="f0a2d-258">此方法返回一个 <xref:System.Collections.ArrayList> 对象的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> ，表示此配置文件的现有参数。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-258">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span> <span data-ttu-id="f0a2d-259">若要枚举所有支持的代理参数设置，请调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-259">To enumerate all supported agent parameter settings, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="f0a2d-260">此方法返回 <xref:System.Collections.ArrayList> 对象的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> ，表示所有参数的支持值。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-260">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent the supported values for all parameters.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> <span data-ttu-id="f0a2d-261">删除代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f0a2d-261">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="f0a2d-262">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类的实例创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-262">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f0a2d-263">创建的 <xref:Microsoft.SqlServer.Replication.AgentProfile> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-263">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span> <span data-ttu-id="f0a2d-264">将 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> 设置为配置文件的名称，将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 设置为从步骤 1 中获得的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-264">Set the name of the profile for <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="f0a2d-265">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-265">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="f0a2d-266">如果此方法返回 `false`，则指定的名称不正确或服务器上不存在该配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-266">If this method returns `false`, either the specified name was incorrect or the profile does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="f0a2d-267">验证 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> 属性是否设置为指示某个客户配置文件的 <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-267">Verify that the <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> property is set to <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, which indicates a customer profile.</span></span> <span data-ttu-id="f0a2d-268">您不应该删除 <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> 的值为 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-268">You should not remove a profile that has a value of <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> for <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.</span></span>  
  
5.  <span data-ttu-id="f0a2d-269">调用 <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> 方法从服务器中删除此对象表示的用户定义的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-269">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> method to remove the user-defined profile represented by this object from the server.</span></span>  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a> <span data-ttu-id="f0a2d-270">跟进：在更改代理参数后</span><span class="sxs-lookup"><span data-stu-id="f0a2d-270">Follow Up: After Changing Agent Parameters</span></span>  
 <span data-ttu-id="f0a2d-271">对代理参数所做的更改在下次启动代理时生效。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-271">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="f0a2d-272">如果代理连续运行，则必须停止该代理，然后重新启动。</span><span class="sxs-lookup"><span data-stu-id="f0a2d-272">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a2d-273">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0a2d-273">See Also</span></span>  
 <span data-ttu-id="f0a2d-274">[复制代理配置文件](replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="f0a2d-274">[Replication Agent Profiles](replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="f0a2d-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span><span class="sxs-lookup"><span data-stu-id="f0a2d-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span></span>  
 <span data-ttu-id="f0a2d-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="f0a2d-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="f0a2d-277">[Replication Distribution Agent](replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="f0a2d-277">[Replication Distribution Agent](replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="f0a2d-278">[Replication Merge Agent](replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="f0a2d-278">[Replication Merge Agent](replication-merge-agent.md) </span></span>  
 [<span data-ttu-id="f0a2d-279">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="f0a2d-279">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)  
  
  
