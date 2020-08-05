---
title: 移除或删除项或项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 679911f15d6c47f4274180602a5376c4ec03c77b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580507"
---
# <a name="remove-or-delete-an-item-or-project"></a><span data-ttu-id="a553d-102">移除或删除项或项目</span><span class="sxs-lookup"><span data-stu-id="a553d-102">Remove or Delete an Item or Project</span></span>
  <span data-ttu-id="a553d-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 项目中的项目项为查询、连接和杂项文件。</span><span class="sxs-lookup"><span data-stu-id="a553d-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="a553d-104">您可以从解决方案中移除项目查询文件和杂项文件，而并不清除存储区中的文件。</span><span class="sxs-lookup"><span data-stu-id="a553d-104">You can remove project queries and miscellaneous files from your solution without erasing the files from storage.</span></span> <span data-ttu-id="a553d-105">如果项目或项在当前解决方案中不再有用，但是您希望将其包含到其他解决方案中，此时可以将其移除。</span><span class="sxs-lookup"><span data-stu-id="a553d-105">Remove a project or item when it is not useful in the current solution but you want to include it in another solution.</span></span>  
  
### <a name="to-remove-a-project-item"></a><span data-ttu-id="a553d-106">移除项目项</span><span class="sxs-lookup"><span data-stu-id="a553d-106">To remove a project item</span></span>  
  
1.  <span data-ttu-id="a553d-107">在解决方案资源管理器中，选择想要移除的项目项。</span><span class="sxs-lookup"><span data-stu-id="a553d-107">In Solution Explorer, select the project item you want to remove.</span></span>  
  
2.  <span data-ttu-id="a553d-108">在“编辑”  菜单上，单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="a553d-108">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="a553d-109">在确认对话框中，单击“删除”  以从项目中删除项。</span><span class="sxs-lookup"><span data-stu-id="a553d-109">On the confirmation dialog, click **Remove** to remove the item from the project.</span></span>  
  
 <span data-ttu-id="a553d-110">已移除的项仍存在于文件系统中。</span><span class="sxs-lookup"><span data-stu-id="a553d-110">A removed item still exists on the file system.</span></span> <span data-ttu-id="a553d-111">因此，您可以将已移除的项添加到各自的初始解决方案或其他解决方案中。</span><span class="sxs-lookup"><span data-stu-id="a553d-111">Therefore, you can add a removed item to its original solution or to another solution.</span></span>  
  
#### <a name="to-remove-a-project"></a><span data-ttu-id="a553d-112">删除项目</span><span class="sxs-lookup"><span data-stu-id="a553d-112">To remove a project</span></span>  
  
1.  <span data-ttu-id="a553d-113">在解决方案资源管理器中，选择想要移除的项目。</span><span class="sxs-lookup"><span data-stu-id="a553d-113">In Solution Explorer, select the project you want to remove.</span></span>  
  
2.  <span data-ttu-id="a553d-114">在“编辑”  菜单上，单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="a553d-114">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="a553d-115">在确认对话框中，单击“确定”  以从解决方案中删除项目。</span><span class="sxs-lookup"><span data-stu-id="a553d-115">On the confirmation dialog, click **OK**, to remove the project from the solution.</span></span>  
  
 <span data-ttu-id="a553d-116">您可以永久删除项目，但是必须先从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 解决方案中移除对该项目的所有引用，然后再使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 资源管理器从存储区中永久删除关联的文件。</span><span class="sxs-lookup"><span data-stu-id="a553d-116">You can delete a project permanently, but you first need to remove any references to the project from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solutions, and then use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Explorer to permanently delete the associated files from storage.</span></span>  
  
#### <a name="to-delete-a-project"></a><span data-ttu-id="a553d-117">删除项目</span><span class="sxs-lookup"><span data-stu-id="a553d-117">To delete a project</span></span>  
  
1.  <span data-ttu-id="a553d-118">在解决方案资源管理器中，移除要从解决方案中删除的项目。</span><span class="sxs-lookup"><span data-stu-id="a553d-118">In Solution Explorer, remove the project you want to delete from the solution.</span></span>  
  
2.  <span data-ttu-id="a553d-119">在 Windows 资源管理器中，找到并选中与所要删除的项目或项相关联的文件。</span><span class="sxs-lookup"><span data-stu-id="a553d-119">In Windows Explorer, locate and select the files associated with the project or item you want to delete.</span></span>  
  
3.  <span data-ttu-id="a553d-120">在“文件”  菜单上，单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="a553d-120">On the **File** menu, click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a553d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a553d-121">See Also</span></span>  
 <span data-ttu-id="a553d-122">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="a553d-122">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="a553d-123">[向项目添加新项](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="a553d-123">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="a553d-124">向项目中添加现有项</span><span class="sxs-lookup"><span data-stu-id="a553d-124">Add Existing Items to a Project</span></span>](add-existing-items-to-a-project.md)  
  
  
