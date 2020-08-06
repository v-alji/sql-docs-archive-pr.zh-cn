---
title: “项目属性”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.general.f1
- sql12.ssis.ssms.isprojectprop.permissions.f1
ms.assetid: d5cf52f5-1fe2-438a-98a3-fe117360acf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 259ad48f2b1f33356243635bbaa5426a5199eccf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689558"
---
# <a name="project-properties-dialog-box"></a><span data-ttu-id="e4912-102">“项目属性”对话框</span><span class="sxs-lookup"><span data-stu-id="e4912-102">Project Properties Dialog Box</span></span>
  <span data-ttu-id="e4912-103">一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目就是一个部署单元。</span><span class="sxs-lookup"><span data-stu-id="e4912-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is a unit of deployment.</span></span> <span data-ttu-id="e4912-104">每个项目都可以包含包、参数和环境引用。</span><span class="sxs-lookup"><span data-stu-id="e4912-104">Each project can contain packages, parameters, and environment references.</span></span> <span data-ttu-id="e4912-105">项目是安全对象并且可为数据库主体定义权限。</span><span class="sxs-lookup"><span data-stu-id="e4912-105">A project is a securable object and can define permissions for database principals.</span></span> <span data-ttu-id="e4912-106">在重新部署某一项目时，该项目的之前版本可以存储在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录中。</span><span class="sxs-lookup"><span data-stu-id="e4912-106">When a project is re-deployed, the previous version of the project can be stored in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
 <span data-ttu-id="e4912-107">项目参数和包参数可用于在执行时向包内的属性赋值。</span><span class="sxs-lookup"><span data-stu-id="e4912-107">Project parameters and package parameters can be used to assign values to properties within packages at the time of execution.</span></span> <span data-ttu-id="e4912-108">某些参数要求首先具有值，之后才能运行包。</span><span class="sxs-lookup"><span data-stu-id="e4912-108">Some parameters require values before the package can be executed.</span></span> <span data-ttu-id="e4912-109">引用环境变量的参数值要求项目在执行前具有相应的环境引用。</span><span class="sxs-lookup"><span data-stu-id="e4912-109">Parameter values that reference environment variables require that the project has the corresponding environment reference prior to execution.</span></span>  
  
 <span data-ttu-id="e4912-110">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="e4912-110">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="e4912-111">打开“项目属性”对话框</span><span class="sxs-lookup"><span data-stu-id="e4912-111">Open the Project Properties dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="e4912-112">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="e4912-112">Set the options on the General page</span></span>](#general)  
  
-   [<span data-ttu-id="e4912-113">设置“权限”页上的选项</span><span class="sxs-lookup"><span data-stu-id="e4912-113">Set the options on the Permissions page</span></span>](#permissions)  
  
##  <a name="open-the-project-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="e4912-114">打开“项目属性”对话框</span><span class="sxs-lookup"><span data-stu-id="e4912-114">Open the Project Properties dialog box</span></span>  
  
1.  <span data-ttu-id="e4912-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="e4912-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="e4912-116">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="e4912-116">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="e4912-117">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="e4912-117">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="e4912-118">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="e4912-118">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="e4912-119">展开包含您要设置其属性的项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e4912-119">Expand the folder that contains the project that you want to set properties for.</span></span>  
  
5.  <span data-ttu-id="e4912-120">右键单击该项目，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e4912-120">Right-click the project, and then click **Properties**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="e4912-121">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="e4912-121">Set the options on the General page</span></span>  
 <span data-ttu-id="e4912-122">使用“常规”页查看项目属性。</span><span class="sxs-lookup"><span data-stu-id="e4912-122">Use the General page to view project properties.</span></span>  
  
 <span data-ttu-id="e4912-123">**名称**</span><span class="sxs-lookup"><span data-stu-id="e4912-123">**Name**</span></span>  
 <span data-ttu-id="e4912-124">列出项目名称。</span><span class="sxs-lookup"><span data-stu-id="e4912-124">Lists the project name.</span></span>  
  
 <span data-ttu-id="e4912-125">**标识符**</span><span class="sxs-lookup"><span data-stu-id="e4912-125">**Identifier**</span></span>  
 <span data-ttu-id="e4912-126">列出项目 ID。</span><span class="sxs-lookup"><span data-stu-id="e4912-126">Lists the project ID.</span></span>  
  
 <span data-ttu-id="e4912-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="e4912-127">**Description**</span></span>  
 <span data-ttu-id="e4912-128">显示项目的可选说明。</span><span class="sxs-lookup"><span data-stu-id="e4912-128">Displays the optional description of the project.</span></span>  
  
 <span data-ttu-id="e4912-129">**项目版本**</span><span class="sxs-lookup"><span data-stu-id="e4912-129">**Project Version**</span></span>  
 <span data-ttu-id="e4912-130">列出项目版本。</span><span class="sxs-lookup"><span data-stu-id="e4912-130">Lists the project version.</span></span>  
  
 <span data-ttu-id="e4912-131">**部署日期**</span><span class="sxs-lookup"><span data-stu-id="e4912-131">**Deployment Date**</span></span>  
 <span data-ttu-id="e4912-132">列出部署或重新部署项目的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="e4912-132">Lists the date and time the project was deployed or redeployed.</span></span>  
  
##  <a name="set-the-options-on-the-permissions-page"></a><a name="permissions"></a> <span data-ttu-id="e4912-133">设置“权限”页上的选项</span><span class="sxs-lookup"><span data-stu-id="e4912-133">Set the options on the Permissions page</span></span>  
 <span data-ttu-id="e4912-134">使用 **“权限”** 页可以查看和设置项目的显式权限。</span><span class="sxs-lookup"><span data-stu-id="e4912-134">Use the **Permissions** page to view and set explicit permissions for the project.</span></span>  
  
 <span data-ttu-id="e4912-135">浏览</span><span class="sxs-lookup"><span data-stu-id="e4912-135">Browse</span></span>  
 <span data-ttu-id="e4912-136">使用“浏览所有主体”对话框，单击“浏览”选择要为其设置权限的用户和角色。</span><span class="sxs-lookup"><span data-stu-id="e4912-136">Click **Browse** to select users and roles that you want to set permissions for, by using the **Browse All Principals** dialog box.</span></span>  
  
 <span data-ttu-id="e4912-137">**名称**</span><span class="sxs-lookup"><span data-stu-id="e4912-137">**Name**</span></span>  
 <span data-ttu-id="e4912-138">列出用户或角色的名称。</span><span class="sxs-lookup"><span data-stu-id="e4912-138">Lists the name of the user or role.</span></span>  
  
 <span data-ttu-id="e4912-139">类型 </span><span class="sxs-lookup"><span data-stu-id="e4912-139">**Type**</span></span>  
 <span data-ttu-id="e4912-140">列出用户或角色的类型。</span><span class="sxs-lookup"><span data-stu-id="e4912-140">Lists the type of user or role.</span></span>  
  
 <span data-ttu-id="e4912-141">**权限**</span><span class="sxs-lookup"><span data-stu-id="e4912-141">**Permission**</span></span>  
 <span data-ttu-id="e4912-142">列出权限。</span><span class="sxs-lookup"><span data-stu-id="e4912-142">Lists the permissions.</span></span>  
  
 <span data-ttu-id="e4912-143">**授权者**</span><span class="sxs-lookup"><span data-stu-id="e4912-143">**Grantor**</span></span>  
 <span data-ttu-id="e4912-144">列出授予权限的用户或角色。</span><span class="sxs-lookup"><span data-stu-id="e4912-144">Lists the user or role that grants the permission.</span></span>  
  
 <span data-ttu-id="e4912-145">**授予**</span><span class="sxs-lookup"><span data-stu-id="e4912-145">**Grant**</span></span>  
 <span data-ttu-id="e4912-146">选择“授予”  时，为所选用户或角色授予权限。</span><span class="sxs-lookup"><span data-stu-id="e4912-146">When **Grant** is selected, the permission is granted for the selected user or role.</span></span>  
  
 <span data-ttu-id="e4912-147">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="e4912-147">**Deny**</span></span>  
 <span data-ttu-id="e4912-148">选择“拒绝”  时，为所选用户或角色拒绝权限。</span><span class="sxs-lookup"><span data-stu-id="e4912-148">When **Deny** is selected, the permission is denied for the selected user or role.</span></span>  
  
  
