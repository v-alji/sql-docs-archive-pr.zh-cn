---
title: “浏览所有主体”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c204411a4daace27745e46269cbcfa0ed33f323f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578379"
---
# <a name="browse-all-principals-dialog-box"></a><span data-ttu-id="1ea2c-102">“浏览所有主体”对话框</span><span class="sxs-lookup"><span data-stu-id="1ea2c-102">Browse All Principals Dialog Box</span></span>
  <span data-ttu-id="1ea2c-103">使用“浏览所有主体”对话框选择数据库主体，以更改所选项目或所选文件夹中包含的所有项目的主体权限  。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-103">Use the **Browse All Principals** dialog box to select a database principal to change the principal's permissions on the selected project or on all projects contained in a selected folder.</span></span>  
  
 <span data-ttu-id="1ea2c-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="1ea2c-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="1ea2c-105">打开“浏览所有主体”对话框</span><span class="sxs-lookup"><span data-stu-id="1ea2c-105">Open the Browse All Principals dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="1ea2c-106">配置选项</span><span class="sxs-lookup"><span data-stu-id="1ea2c-106">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-browse-all-principals-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="1ea2c-107">打开“浏览所有主体”对话框</span><span class="sxs-lookup"><span data-stu-id="1ea2c-107">Open the Browse All Principals dialog box</span></span>  
  
1.  <span data-ttu-id="1ea2c-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="1ea2c-109">正在连接到托管 SSISDB 目录的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB catalog.</span></span>  
  
2.  <span data-ttu-id="1ea2c-110">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="1ea2c-111">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="1ea2c-112">要更改所选文件夹中包含的所有项目的主体权限，请右键单击该文件夹，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-112">To change the principal's permissions on all projects contained in a selected folder, right-click the folder and then click **Properties**.</span></span>  
  
     <span data-ttu-id="1ea2c-113">要更改所选文件的主体权限，请扩展包含该项目的文件夹，右键单击该项目，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-113">To change the principal's permissions on a selected project, expand the folder that contains the project, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="1ea2c-114">选择 **“权限”** 页，然后单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-114">Select the **Permissions** page, and then click **Browse**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="1ea2c-115">配置选项</span><span class="sxs-lookup"><span data-stu-id="1ea2c-115">Configure the Options</span></span>  
 <span data-ttu-id="1ea2c-116">此页显示来自 SSISDB 数据库的目录视图 sys.database_principals 的主体。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-116">This page displays the principals from the catalog view, sys.database_principals, of the SSISDB database.</span></span>  
  
 <span data-ttu-id="1ea2c-117">选择主体后，在您单击 **“确定”** 并且关闭 **“浏览所有主体”** 对话框时，会将这些主体添加到父对话框的 **“权限”** 页上的 **“登录名或角色”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-117">Selecting principals adds them to the **Logins or roles** list on the **Permissions** page of the parent dialog box when you click **OK** and close the **Browse All Principals** dialog box.</span></span> <span data-ttu-id="1ea2c-118">在将主体添加到 **“登录名或角色”** 列表后，您可以更改该主体对所选项目的权限。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-118">After adding principals to the **Logins or roles** list, you can change their permissions on the selected project.</span></span>  
  
 <span data-ttu-id="1ea2c-119">**选择列**</span><span class="sxs-lookup"><span data-stu-id="1ea2c-119">**Selection column**</span></span>  
 <span data-ttu-id="1ea2c-120">选择此选项可以将主体添加到父对话框的“权限”页上的“登录名或角色”   列表中。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-120">Select to add the principal to the **Logins or roles** list on the **Permissions** page of the parent dialog box.</span></span>  
  
 <span data-ttu-id="1ea2c-121">**图标列**</span><span class="sxs-lookup"><span data-stu-id="1ea2c-121">**Icon column**</span></span>  
 <span data-ttu-id="1ea2c-122">与主体的  “类型”相对应的图标。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-122">An icon that corresponds to the **Type** of the principal.</span></span>  
  
 <span data-ttu-id="1ea2c-123">**名称**</span><span class="sxs-lookup"><span data-stu-id="1ea2c-123">**Name**</span></span>  
 <span data-ttu-id="1ea2c-124">主体的名称。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-124">The name of the principal.</span></span>  
  
 <span data-ttu-id="1ea2c-125">类型 </span><span class="sxs-lookup"><span data-stu-id="1ea2c-125">**Type**</span></span>  
 <span data-ttu-id="1ea2c-126">主体的类型。</span><span class="sxs-lookup"><span data-stu-id="1ea2c-126">The type of the principal.</span></span> <span data-ttu-id="1ea2c-127">常见类型如下：</span><span class="sxs-lookup"><span data-stu-id="1ea2c-127">The common types are:</span></span>  
  
-   <span data-ttu-id="1ea2c-128">SQL 用户</span><span class="sxs-lookup"><span data-stu-id="1ea2c-128">SQL User</span></span>  
  
-   <span data-ttu-id="1ea2c-129">Windows 用户</span><span class="sxs-lookup"><span data-stu-id="1ea2c-129">Windows User</span></span>  
  
-   <span data-ttu-id="1ea2c-130">数据库角色</span><span class="sxs-lookup"><span data-stu-id="1ea2c-130">Database Role</span></span>  
  
  
