---
title: 创建、删除或修改文件夹（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bd7d5ceebdb7b3a48ded66ed108bddda25d8a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588284"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a><span data-ttu-id="f1b10-102">创建、删除或修改文件夹（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="f1b10-102">Create, Delete, or Modify a Folder (Report Manager)</span></span>
  <span data-ttu-id="f1b10-103">可以创建文件夹来组织和管理发布到报表服务器的项。</span><span class="sxs-lookup"><span data-stu-id="f1b10-103">You can create folders to organize and manage the items you publish to a report server.</span></span> <span data-ttu-id="f1b10-104">创建文件夹有助于用户查找他们关注的报表。</span><span class="sxs-lookup"><span data-stu-id="f1b10-104">Creating folders can help users find reports of interest to them.</span></span> <span data-ttu-id="f1b10-105">对于内容管理员来说，文件夹提供了应用权限的框架。</span><span class="sxs-lookup"><span data-stu-id="f1b10-105">For content managers, folders provide a framework for applying permissions.</span></span> <span data-ttu-id="f1b10-106">可以对特定的文件夹创建角色分配，来限制对处于开发阶段或者不应大范围分布的报表的访问。</span><span class="sxs-lookup"><span data-stu-id="f1b10-106">You can create role assignments on specific folders to restrict access to reports that are in development or that should not be widely distributed.</span></span>  
  
### <a name="to-create-a-folder"></a><span data-ttu-id="f1b10-107">创建文件夹</span><span class="sxs-lookup"><span data-stu-id="f1b10-107">To create a folder</span></span>  
  
1.  <span data-ttu-id="f1b10-108">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b10-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="f1b10-109">在报表管理器中，选择主文件夹，再单击 **“新建文件夹”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-109">In Report Manager, select the Home folder and click **New Folder**.</span></span> <span data-ttu-id="f1b10-110">或者，若要在现有文件夹中创建文件夹，请在 **“内容”** 页中导航到该文件夹，再单击该文件夹将其打开。</span><span class="sxs-lookup"><span data-stu-id="f1b10-110">Or, to create a folder under an existing folder, navigate to that folder in the **Contents** page and click the folder to open it.</span></span> <span data-ttu-id="f1b10-111">然后单击 **“新建文件夹”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-111">Then click **New Folder**.</span></span>  
  
     <span data-ttu-id="f1b10-112">此时，将打开 **“新建文件夹”** 页。</span><span class="sxs-lookup"><span data-stu-id="f1b10-112">The **New Folder** page opens.</span></span>  
  
3.  <span data-ttu-id="f1b10-113">键入文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="f1b10-113">Type a folder name.</span></span> <span data-ttu-id="f1b10-114">文件夹名称可以包含空格，但不能包含以下用于 URL 编码的保留字符：; ?</span><span class="sxs-lookup"><span data-stu-id="f1b10-114">A folder name can include spaces, but cannot include reserved characters that are used for URL encoding: ; ?</span></span> <span data-ttu-id="f1b10-115">： \@ & = +，$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="f1b10-115">: \@ & = + , $ / \* \< > |.</span></span> <span data-ttu-id="f1b10-116">不能通过键入一系列文件夹名称来同时创建多个文件夹。</span><span class="sxs-lookup"><span data-stu-id="f1b10-116">You cannot type a series of folder names to create several folders at once.</span></span>  
  
4.  <span data-ttu-id="f1b10-117">根据需要，可以键入说明。</span><span class="sxs-lookup"><span data-stu-id="f1b10-117">Optionally type a description.</span></span>  
  
5.  <span data-ttu-id="f1b10-118">如果不希望在 **“内容”** 页的默认视图中显示该文件夹，请选择 **“在列表视图中隐藏”** 。</span><span class="sxs-lookup"><span data-stu-id="f1b10-118">Select **Hide in list view** if you do not want to display the folder in the default view of the **Contents** page.</span></span> <span data-ttu-id="f1b10-119">只有在用户单击了 **“内容”** 页上的 **“显示详细信息”** 时，才可以看到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="f1b10-119">The folder will be visible to users only when they click **Show Details** on the **Contents** page.</span></span>  
  
6.  <span data-ttu-id="f1b10-120">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f1b10-120">Click **OK**.</span></span>  
  
### <a name="to-delete-a-folder"></a><span data-ttu-id="f1b10-121">删除文件夹</span><span class="sxs-lookup"><span data-stu-id="f1b10-121">To delete a folder</span></span>  
  
1.  <span data-ttu-id="f1b10-122">在报表管理器中，导航到 **“内容”** 页，然后找到要修改的项。</span><span class="sxs-lookup"><span data-stu-id="f1b10-122">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="f1b10-123">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="f1b10-123">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="f1b10-124">在下拉菜单中，单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1b10-124">In the drop-down menu, click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a><span data-ttu-id="f1b10-125">修改或删除文件夹</span><span class="sxs-lookup"><span data-stu-id="f1b10-125">To modify or delete a folder</span></span>  
  
1.  <span data-ttu-id="f1b10-126">在报表管理器中，导航到 **“内容”** 页，然后找到要修改的项。</span><span class="sxs-lookup"><span data-stu-id="f1b10-126">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="f1b10-127">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="f1b10-127">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="f1b10-128">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-128">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="f1b10-129">此时将打开“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="f1b10-129">The General Properties page opens.</span></span>  
  
4.  <span data-ttu-id="f1b10-130">若要更改该文件夹位置，请单击 **“移动”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-130">To change the folder location, click **Move**.</span></span> <span data-ttu-id="f1b10-131">键入目标文件夹的位置，或从树中选择目标文件夹，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-131">Type the location of the destination folder, or choose the destination folder from the tree, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f1b10-132">或者，通过以下方式修改该文件夹属性：</span><span class="sxs-lookup"><span data-stu-id="f1b10-132">Or, modify folder properties in the following ways:</span></span>  
  
    -   <span data-ttu-id="f1b10-133">若要修改关于该文件夹的显示文本，请键入名称或说明。</span><span class="sxs-lookup"><span data-stu-id="f1b10-133">To modify display text about the folder, type a name or description.</span></span>  
  
    -   <span data-ttu-id="f1b10-134">若要在 **“内容”** 页上的默认视图中显示该文件夹，请清除 **“在列表视图中隐藏”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-134">To display the folder in the default view on the **Contents** page, clear **Hide in list view**.</span></span>  
  
6.  <span data-ttu-id="f1b10-135">或者，若要删除该文件夹及其内容，请单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="f1b10-135">Or, to remove the folder and its contents, click **Delete**.</span></span>  
  
7.  <span data-ttu-id="f1b10-136">单击“应用”\*\*\*\* 保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f1b10-136">Click **Apply** to save changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b10-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1b10-137">See Also</span></span>  
 <span data-ttu-id="f1b10-138">[新文件夹页 &#40;报表管理器&#41;](../new-folder-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f1b10-138">[New Folder Page &#40;Report Manager&#41;](../new-folder-page-report-manager.md) </span></span>  
 <span data-ttu-id="f1b10-139">["内容" 页 &#40;报表管理器&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f1b10-139">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="f1b10-140">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f1b10-140">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
