---
title: 创建和映射服务器环境 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isenvprop.variables.f1
- sql12.ssis.ssms.iscreateenv.f1
- sql12.ssis.ssms.isenvprop.permissions.f1
- sql12.ssis.ssms.isenvprop.general.f1
ms.assetid: b1cbb697-713f-48e4-b234-b23724d87451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9331b5078effb562931f45c48bd8ff975c1d1998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580805"
---
# <a name="create-and-map-a-server-environment"></a><span data-ttu-id="e898a-102">创建和映射服务器环境</span><span class="sxs-lookup"><span data-stu-id="e898a-102">Create and Map a Server Environment</span></span>
  <span data-ttu-id="e898a-103">创建服务器环境来指定已部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器的项目中所含包的运行时值。</span><span class="sxs-lookup"><span data-stu-id="e898a-103">You create a server environment to specify runtime values for packages contained in a project you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e898a-104">您可以随后针对特定包、入口点包或给定项目中的所有包，将环境变量映射到参数。</span><span class="sxs-lookup"><span data-stu-id="e898a-104">You can then map the environment variables to parameters, for a specific package, for entry-point packages, or for all the packages in a given project.</span></span> <span data-ttu-id="e898a-105">入口点包通常是执行子包的父包。</span><span class="sxs-lookup"><span data-stu-id="e898a-105">An entry-point package is typically a parent package that executes a child package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e898a-106">对于给定的执行，只能使用单个服务器环境中包含的值来执行包。</span><span class="sxs-lookup"><span data-stu-id="e898a-106">For a given execution, a package can execute only with the values contained in a single server environment.</span></span>  
  
 <span data-ttu-id="e898a-107">您可以查询视图以获得服务器环境、环境引用和环境变量的列表。</span><span class="sxs-lookup"><span data-stu-id="e898a-107">You can query views for a list of server environments, environment references, and environment variables.</span></span> <span data-ttu-id="e898a-108">您也可以调用存储过程来添加、删除和修改环境、环境引用和环境变量。</span><span class="sxs-lookup"><span data-stu-id="e898a-108">You can also call stored to add, delete, and modify environments, environment references, and environment variables.</span></span> <span data-ttu-id="e898a-109">有关详细信息，请参阅 [SSIS Catalog](catalog/ssis-catalog.md) 中的“服务器环境、服务器变量和服务器环境引用”\*\*\*\* 一节。</span><span class="sxs-lookup"><span data-stu-id="e898a-109">For more information, see the **Server Environments, Server Variables and Server Environment References** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
### <a name="to-create-and-use-a-server-environment"></a><span data-ttu-id="e898a-110">创建和使用服务器环境</span><span class="sxs-lookup"><span data-stu-id="e898a-110">To create and use a server environment</span></span>  
  
1.  <span data-ttu-id="e898a-111">在中 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，展开 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象资源管理器中的 "目录> **SSISDB** " 节点，然后找到要为其创建环境的项目的 "**环境**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e898a-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalogs> **SSISDB** node in Object Explorer, and locate the **Environments** folder of the project for which you want to create an environment.</span></span>  
  
2.  <span data-ttu-id="e898a-112">右键单击“环境”\*\*\*\* 文件夹，然后单击“创建环境”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e898a-112">Right-click the **Environments** folder, and then click **Create Environment**.</span></span>  
  
3.  <span data-ttu-id="e898a-113">为环境键入名称和说明（可选），然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e898a-113">Type a name for the environment and optionally a description, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e898a-114">右键单击该新环境，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e898a-114">Right-click the new environment and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e898a-115">在 **“变量”** 页上，执行以下操作以便添加变量。</span><span class="sxs-lookup"><span data-stu-id="e898a-115">On the **Variables** page, do the following to add a variable.</span></span>  
  
    1.  <span data-ttu-id="e898a-116">选择变量的 **“类型”** 。</span><span class="sxs-lookup"><span data-stu-id="e898a-116">Select the **Type** for the variable.</span></span> <span data-ttu-id="e898a-117">变量的名称 **无需** 匹配您将映射到该变量的项目参数的名称。</span><span class="sxs-lookup"><span data-stu-id="e898a-117">The name of the variable **does not** need to match the name of the project parameter that you map to the variable.</span></span>  
  
    2.  <span data-ttu-id="e898a-118">输入变量的可选 **“说明”** 。</span><span class="sxs-lookup"><span data-stu-id="e898a-118">Enter an optional **Description** for the variable.</span></span>  
  
    3.  <span data-ttu-id="e898a-119">输入环境变量的 **“值”** 。</span><span class="sxs-lookup"><span data-stu-id="e898a-119">Enter the **Value** for the environment variable.</span></span>  
  
         <span data-ttu-id="e898a-120">有关环境变量名称的规则的信息，请参阅 [SSIS Catalog](catalog/ssis-catalog.md) 中的“环境变量”\*\*\*\* 一节。</span><span class="sxs-lookup"><span data-stu-id="e898a-120">For information about the rules for environment variable names, see the **Environment Variable** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
    4.  <span data-ttu-id="e898a-121">通过选中或取消选中 **“敏感”** 复选框，指示该变量是否包含敏感值。</span><span class="sxs-lookup"><span data-stu-id="e898a-121">Indicate whether the variable contains sensitive value, by selecting or clearing the **Sensitive** checkbox.</span></span>  
  
         <span data-ttu-id="e898a-122">如果您选择 **“敏感”**，则变量值不会显示在 **“值”** 字段中。</span><span class="sxs-lookup"><span data-stu-id="e898a-122">If you select **Sensitive**, the variable value does not display in the **Value** field.</span></span>  
  
         <span data-ttu-id="e898a-123">敏感值在 SSISDB 目录中进行加密。</span><span class="sxs-lookup"><span data-stu-id="e898a-123">Sensitive values are encrypted in the SSISDB catalog.</span></span> <span data-ttu-id="e898a-124">有关加密的详细信息，请参阅 [SSIS Catalog](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="e898a-124">For more information about the encryption, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
6.  <span data-ttu-id="e898a-125">在 **“权限”** 页上，通过执行以下操作，授予或拒绝所选用户和角色的权限。</span><span class="sxs-lookup"><span data-stu-id="e898a-125">On the **Permissions** page, grant or deny permissions for selected users and roles by doing the following.</span></span>  
  
    1.  <span data-ttu-id="e898a-126">单击 **“浏览”**，然后在 **“浏览所有主体”** 对话框中选择一个或多个用户和角色。</span><span class="sxs-lookup"><span data-stu-id="e898a-126">Click **Browse**, and then select one or more users and roles in the **Browse All Principals** dialog box.</span></span>  
  
    2.  <span data-ttu-id="e898a-127">在 **“登录名或角色”** 区域中，选择您要为其授予或拒绝权限的用户或角色。</span><span class="sxs-lookup"><span data-stu-id="e898a-127">In the **Logins or roles** area, select the user or role that you want to grant or deny permissions for.</span></span>  
  
    3.  <span data-ttu-id="e898a-128">在 **“显式”** 区域中，单击每个权限旁边的 **“授予”** 或 **“拒绝”** 。</span><span class="sxs-lookup"><span data-stu-id="e898a-128">In the **Explicit** area, click **Grant** or **Deny** next to each permission.</span></span>  
  
7.  <span data-ttu-id="e898a-129">若要编写环境的脚本，请单击 **“脚本”**。</span><span class="sxs-lookup"><span data-stu-id="e898a-129">To script the environment, click **Script**.</span></span> <span data-ttu-id="e898a-130">默认情况下，该脚本显示在一个新的查询编辑器窗口中。</span><span class="sxs-lookup"><span data-stu-id="e898a-130">By default, the script displays in a new Query Editor window.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e898a-131">对环境属性进行了更改（例如添加变量）后，并且在“环境属性”对话框中单击“确定”前，需要单击“脚本”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e898a-131">You need to click **Script** after you've made one or changes to the environment properties, such as adding a variable, and before you click **OK** in the **Environment Properties** dialog box.</span></span> <span data-ttu-id="e898a-132">否则，将不会生成脚本。</span><span class="sxs-lookup"><span data-stu-id="e898a-132">Otherwise, a script is not generated.</span></span>  
  
8.  <span data-ttu-id="e898a-133">单击 **“确定”** 保存对环境属性的更改。</span><span class="sxs-lookup"><span data-stu-id="e898a-133">Click **OK** to save your changes to the environment properties.</span></span>  
  
9. <span data-ttu-id="e898a-134">在对象资源管理器的 **SSISDB** 节点下，展开“项目”\*\*\*\* 文件夹，右键单击项目，然后单击“配置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e898a-134">Under the **SSISDB** node in Object Explorer, expand the **Projects** folder, right-click the project, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="e898a-135">在 **“引用”** 页上，单击 **“添加”** 以便添加一个环境，然后单击 **“确定”** 以便保存对该环境的引用。</span><span class="sxs-lookup"><span data-stu-id="e898a-135">On the **References** page, click **Add** to add an environment, and then click **OK** to save the reference to the environment.</span></span>  
  
11. <span data-ttu-id="e898a-136">再次右键单击该项目，然后单击“配置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e898a-136">Right-click the project again, and then click **Configure**.</span></span>  
  
12. <span data-ttu-id="e898a-137">若要将环境变量映射到在设计时添加到包的参数，或映射到将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目转换为项目部署模型时生成的参数，请执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="e898a-137">To map the environment variable to a parameter that you added to the package at design-time or to a parameter that was generated when you converted the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the project deployment model, do the following.,</span></span>  
  
    1.  <span data-ttu-id="e898a-138">在 **“参数”** 页上的 **“参数”** 选项卡中，单击 **“值”** 字段旁边的浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="e898a-138">In the **Parameters** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="e898a-139">单击 **“使用环境变量”**，然后选择已创建的环境变量。</span><span class="sxs-lookup"><span data-stu-id="e898a-139">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
13. <span data-ttu-id="e898a-140">若要将环境变量映射到连接管理器属性，请执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="e898a-140">To map the environment variable to a connection manager property, do the following.</span></span> <span data-ttu-id="e898a-141">将在 SSIS 服务器上为连接管理器属性自动生成参数。</span><span class="sxs-lookup"><span data-stu-id="e898a-141">Parameters are automatically generated on the SSIS server for the connection manager properties.</span></span>  
  
    1.  <span data-ttu-id="e898a-142">在 **“参数”** 页上的 **“连接管理器”** 选项卡中，单击 **“值”** 字段旁边的浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="e898a-142">In the **Connection Managers** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="e898a-143">单击 **“使用环境变量”**，然后选择已创建的环境变量。</span><span class="sxs-lookup"><span data-stu-id="e898a-143">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
14. <span data-ttu-id="e898a-144">单击“确定”两次以保存更改。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e898a-144">Click **OK** twice to save your changes.</span></span>  
  
  
