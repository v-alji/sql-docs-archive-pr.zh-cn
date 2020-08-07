---
title: 执行包任务编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587492"
---
# <a name="execute-package-task-editor"></a><span data-ttu-id="26a0c-102">执行包任务编辑器</span><span class="sxs-lookup"><span data-stu-id="26a0c-102">Execute Package Task Editor</span></span>
  <span data-ttu-id="26a0c-103">可以使用执行包任务编辑器来配置执行包任务。</span><span class="sxs-lookup"><span data-stu-id="26a0c-103">Use the Execute Package Task Editor to configure the Execute Package Task.</span></span> <span data-ttu-id="26a0c-104">执行包任务通过允许包将其他包作为工作流的组成部分运行来扩展 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的企业功能。</span><span class="sxs-lookup"><span data-stu-id="26a0c-104">The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by letting packages run other packages as part of a workflow.</span></span>  
  
 <span data-ttu-id="26a0c-105">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="26a0c-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="26a0c-106">打开执行包任务编辑器</span><span class="sxs-lookup"><span data-stu-id="26a0c-106">Open the Execute Package Task Editor</span></span>](#open)  
  
-   [<span data-ttu-id="26a0c-107">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-107">Set the Options on the General Page</span></span>](#general)  
  
-   [<span data-ttu-id="26a0c-108">设置“包”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-108">Set the Options on the Package Page</span></span>](#package)  
  
-   [<span data-ttu-id="26a0c-109">设置“参数绑定”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-109">Set the Options on the Parameter Bindings Page</span></span>](#parameter)  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> <span data-ttu-id="26a0c-110">打开执行包任务编辑器</span><span class="sxs-lookup"><span data-stu-id="26a0c-110">Open the Execute Package Task Editor</span></span>  
  
1.  <span data-ttu-id="26a0c-111">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中，打开包含执行包任务的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="26a0c-111">Open an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] that contains an Execute Package task.</span></span>  
  
2.  <span data-ttu-id="26a0c-112">在 SSIS 设计器中右键单击该任务，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="26a0c-112">Right-click the task in the SSIS Designer, and then click **Edit**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="26a0c-113">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-113">Set the Options on the General Page</span></span>  
 <span data-ttu-id="26a0c-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="26a0c-114">**Name**</span></span>  
 <span data-ttu-id="26a0c-115">为执行包任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="26a0c-115">Provide a unique name for the Execute Package task.</span></span> <span data-ttu-id="26a0c-116">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="26a0c-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26a0c-117">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="26a0c-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="26a0c-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="26a0c-118">**Description**</span></span>  
 <span data-ttu-id="26a0c-119">键入对执行包任务的说明。</span><span class="sxs-lookup"><span data-stu-id="26a0c-119">Type a description of the Execute Package task.</span></span>  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> <span data-ttu-id="26a0c-120">设置“包”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-120">Set the Options on the Package Page</span></span>  
 <span data-ttu-id="26a0c-121">**ReferenceType**</span><span class="sxs-lookup"><span data-stu-id="26a0c-121">**ReferenceType**</span></span>  
 <span data-ttu-id="26a0c-122">为项目中的子包选择“项目引用”  。</span><span class="sxs-lookup"><span data-stu-id="26a0c-122">Select **Project Reference** for child packages that are in the project.</span></span> <span data-ttu-id="26a0c-123">为位于包外部的子包选择 **“外部引用”** 。</span><span class="sxs-lookup"><span data-stu-id="26a0c-123">Select **External Reference** for child packages that are located outside the package</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26a0c-124">“ReferenceType”  选项是只读的，如果包含包的项目尚未转换为项目部署模型，则该选项将设置为“外部引用”  。</span><span class="sxs-lookup"><span data-stu-id="26a0c-124">The **ReferenceType** option is ready-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model.</span></span> <span data-ttu-id="26a0c-125">有关转换的详细信息，请参阅 [将项目部署到 Integration Services 服务器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="26a0c-125">For more information about conversion, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="26a0c-126">**密码**</span><span class="sxs-lookup"><span data-stu-id="26a0c-126">**Password**</span></span>  
 <span data-ttu-id="26a0c-127">如果子包受密码保护，请提供子包的密码，或单击省略号按钮 (…)，为子包创建新的密码。</span><span class="sxs-lookup"><span data-stu-id="26a0c-127">If the child package is password protected, provide the password for the child package, or click the ellipsis button (...) and create a new password for the child package.</span></span>  
  
 `ExecuteOutOfProcess`  
 <span data-ttu-id="26a0c-128">指定子包是在父包的进程中运行还是在单独的进程中运行。</span><span class="sxs-lookup"><span data-stu-id="26a0c-128">Specify whether the child package runs in the process of the parent package or in a separate process.</span></span> <span data-ttu-id="26a0c-129">默认情况下，"执行包" 任务的 ExecuteOutOfProcess 属性设置为 `False` ，子包与父包运行在同一进程中。</span><span class="sxs-lookup"><span data-stu-id="26a0c-129">By default, the ExecuteOutOfProcess property of the Execute Package task is set to `False`, and the child package runs in the same process as the parent package.</span></span> <span data-ttu-id="26a0c-130">如果将此属性设置为 `true`，则在单独的进程中运行子包。 </span><span class="sxs-lookup"><span data-stu-id="26a0c-130">If you set this property to `true`, the child package runs in a separate process.</span></span> <span data-ttu-id="26a0c-131">这可能减慢子包的启动。</span><span class="sxs-lookup"><span data-stu-id="26a0c-131">This may slow down the launching of the child package.</span></span> <span data-ttu-id="26a0c-132">此外，如果将该属性设置为 `true`，则不能在仅工具安装中调试包；必须安装 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 产品。</span><span class="sxs-lookup"><span data-stu-id="26a0c-132">In addition, if set the property to `true`, you cannot debug the package in a tools-only install; you must install the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] product.</span></span> <span data-ttu-id="26a0c-133">有关详细信息，请参阅 [安装 Integration Services](install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="26a0c-133">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
### <a name="referencetype-dynamic-options"></a><span data-ttu-id="26a0c-134">ReferenceType 动态选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-134">ReferenceType Dynamic Options</span></span>  
  
#### <a name="referencetype--external-reference"></a><span data-ttu-id="26a0c-135">ReferenceType = 外部引用</span><span class="sxs-lookup"><span data-stu-id="26a0c-135">ReferenceType = External Reference</span></span>  
 <span data-ttu-id="26a0c-136">**位置**</span><span class="sxs-lookup"><span data-stu-id="26a0c-136">**Location**</span></span>  
 <span data-ttu-id="26a0c-137">选择子包的位置。</span><span class="sxs-lookup"><span data-stu-id="26a0c-137">Select the location of the child package.</span></span> <span data-ttu-id="26a0c-138">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="26a0c-138">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="26a0c-139">值</span><span class="sxs-lookup"><span data-stu-id="26a0c-139">Value</span></span>|<span data-ttu-id="26a0c-140">说明</span><span class="sxs-lookup"><span data-stu-id="26a0c-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26a0c-141">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="26a0c-141">**SQL Server**</span></span>|<span data-ttu-id="26a0c-142">将位置设置为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="26a0c-142">Set the location to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="26a0c-143">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="26a0c-143">**File system**</span></span>|<span data-ttu-id="26a0c-144">将位置设置为文件系统。</span><span class="sxs-lookup"><span data-stu-id="26a0c-144">Set the location to the file system.</span></span>|  
  
 <span data-ttu-id="26a0c-145">**Connection**</span><span class="sxs-lookup"><span data-stu-id="26a0c-145">**Connection**</span></span>  
 <span data-ttu-id="26a0c-146">选择子包的存储位置的类型。</span><span class="sxs-lookup"><span data-stu-id="26a0c-146">Select the type of storage location for the child package.</span></span>  
  
 <span data-ttu-id="26a0c-147">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="26a0c-147">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="26a0c-148">显示包的名称。</span><span class="sxs-lookup"><span data-stu-id="26a0c-148">Displays the package name.</span></span>  
  
#### <a name="referencetype--project-reference"></a><span data-ttu-id="26a0c-149">ReferenceType = 项目引用</span><span class="sxs-lookup"><span data-stu-id="26a0c-149">ReferenceType = Project Reference</span></span>  
 <span data-ttu-id="26a0c-150">**PackageNameFromProjectReference**</span><span class="sxs-lookup"><span data-stu-id="26a0c-150">**PackageNameFromProjectReference**</span></span>  
 <span data-ttu-id="26a0c-151">选择项目中包含的要成为子包的包。</span><span class="sxs-lookup"><span data-stu-id="26a0c-151">Select a package contained in the project, to be the child package.</span></span>  
  
### <a name="location-dynamic-options"></a><span data-ttu-id="26a0c-152">位置动态选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-152">Location Dynamic Options</span></span>  
  
#### <a name="location--sql-server"></a><span data-ttu-id="26a0c-153">位置 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="26a0c-153">Location = SQL Server</span></span>  
 <span data-ttu-id="26a0c-154">**Connection**</span><span class="sxs-lookup"><span data-stu-id="26a0c-154">**Connection**</span></span>  
 <span data-ttu-id="26a0c-155">从列表中选择一个 OLE DB 连接管理器，或单击 \<**New connection...**> 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="26a0c-155">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="26a0c-156">**相关主题：** [OLE DB 连接管理器](connection-manager/ole-db-connection-manager.md)、[配置 OLE DB 连接管理器](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="26a0c-156">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="26a0c-157">**PackageName**</span><span class="sxs-lookup"><span data-stu-id="26a0c-157">**PackageName**</span></span>  
 <span data-ttu-id="26a0c-158">键入子包的名称，或单击省略号 (…) 再定位到包。</span><span class="sxs-lookup"><span data-stu-id="26a0c-158">Type the name of the child package, or click the ellipsis (...) and then locate the package.</span></span>  
  
#### <a name="location--file-system"></a><span data-ttu-id="26a0c-159">位置 = 文件系统</span><span class="sxs-lookup"><span data-stu-id="26a0c-159">Location = File system</span></span>  
 <span data-ttu-id="26a0c-160">**Connection**</span><span class="sxs-lookup"><span data-stu-id="26a0c-160">**Connection**</span></span>  
 <span data-ttu-id="26a0c-161">从列表中选择文件连接管理器，或单击 \<**New connection...**> 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="26a0c-161">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="26a0c-162">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="26a0c-162">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="26a0c-163">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="26a0c-163">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="26a0c-164">显示包的名称。</span><span class="sxs-lookup"><span data-stu-id="26a0c-164">Displays the package name.</span></span>  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> <span data-ttu-id="26a0c-165">设置“参数绑定”页上的选项</span><span class="sxs-lookup"><span data-stu-id="26a0c-165">Set the Options on the Parameter Bindings Page</span></span>  
 <span data-ttu-id="26a0c-166">您可以将父包或项目中的值传递到子包。</span><span class="sxs-lookup"><span data-stu-id="26a0c-166">You can pass values from the parent package or the project, to the child package.</span></span> <span data-ttu-id="26a0c-167">项目必须使用项目部署模型，并且子包必须包含在父包所在的同一项目中。</span><span class="sxs-lookup"><span data-stu-id="26a0c-167">The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.</span></span>  
  
 <span data-ttu-id="26a0c-168">有关将项目转换为项目部署模型的信息，请参阅 [将项目部署到 Integration Services 服务器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="26a0c-168">For information about converting projects to the project deployment model, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="26a0c-169">**子包参数**</span><span class="sxs-lookup"><span data-stu-id="26a0c-169">**Child package parameter**</span></span>  
 <span data-ttu-id="26a0c-170">输入或选择子包参数的名称。</span><span class="sxs-lookup"><span data-stu-id="26a0c-170">Enter or select a name for the child package parameter.</span></span>  
  
 <span data-ttu-id="26a0c-171">**绑定参数或变量**</span><span class="sxs-lookup"><span data-stu-id="26a0c-171">**Binding parameter or variable**</span></span>  
 <span data-ttu-id="26a0c-172">选择包含要传递到子包的值的参数或变量。</span><span class="sxs-lookup"><span data-stu-id="26a0c-172">Select the parameter or variable that contains the value that you want to pass to the child package.</span></span>  
  
 <span data-ttu-id="26a0c-173">**添加**</span><span class="sxs-lookup"><span data-stu-id="26a0c-173">**Add**</span></span>  
 <span data-ttu-id="26a0c-174">单击此选项可将参数或变量映射到子包参数。</span><span class="sxs-lookup"><span data-stu-id="26a0c-174">Click to map a parameter or variable to a child package parameter.</span></span>  
  
 <span data-ttu-id="26a0c-175">**删除**</span><span class="sxs-lookup"><span data-stu-id="26a0c-175">**Remove**</span></span>  
 <span data-ttu-id="26a0c-176">单击此选项可删除参数或变量与子包参数之间的映射。</span><span class="sxs-lookup"><span data-stu-id="26a0c-176">Click to remove a mapping between a parameter or variable and a child package parameter.</span></span>  
  
  
