---
title: 更改源代码管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 55831529243608e8c71972a31009e5672fb0234f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588065"
---
# <a name="change-source-control"></a><span data-ttu-id="06434-102">更改源代码管理</span><span class="sxs-lookup"><span data-stu-id="06434-102">Change Source Control</span></span>
  <span data-ttu-id="06434-103">创建和管理特定的连接和绑定（用于将本地保存的解决方案或项目链接到源代码管理数据库文件夹）。</span><span class="sxs-lookup"><span data-stu-id="06434-103">Creates and manages the connections and bindings that link a locally saved solution or project to a source control database folder.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="06434-104">对话框访问</span><span class="sxs-lookup"><span data-stu-id="06434-104">Dialog Box Access</span></span>  
 <span data-ttu-id="06434-105">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，请在解决方案资源管理器中选择一项。</span><span class="sxs-lookup"><span data-stu-id="06434-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="06434-106">在 "**文件**" 菜单上，单击 "**源代码管理**"，然后**更改源代码管理**。</span><span class="sxs-lookup"><span data-stu-id="06434-106">On the **File** menu, click **Source Control**, and then **Change Source Control**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06434-107">也可以右键单击解决方案资源管理器中的项来访问此对话框。</span><span class="sxs-lookup"><span data-stu-id="06434-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="06434-108">选项</span><span class="sxs-lookup"><span data-stu-id="06434-108">Options</span></span>  
 <span data-ttu-id="06434-109">**绑定**</span><span class="sxs-lookup"><span data-stu-id="06434-109">**Bind**</span></span>  
 <span data-ttu-id="06434-110">使所选项与指定的源代码管理服务器位置相关联。</span><span class="sxs-lookup"><span data-stu-id="06434-110">Associate selected items with a specified source control server location.</span></span> <span data-ttu-id="06434-111">例如，您可以使用此按钮绑定到上一次已知的源代码管理服务器文件夹和数据库。</span><span class="sxs-lookup"><span data-stu-id="06434-111">For example, you can use this button to bind to the last known source control server folder and database.</span></span> <span data-ttu-id="06434-112">如果找不到最近使用的服务器文件夹或数据库，则将提示您指定另一个。</span><span class="sxs-lookup"><span data-stu-id="06434-112">If a recent server folder or database cannot be found, you are prompted to specify another.</span></span>  
  
 <span data-ttu-id="06434-113">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="06434-113">**Browse**</span></span>  
 <span data-ttu-id="06434-114">导航到指定项的新源代码管理服务器位置。</span><span class="sxs-lookup"><span data-stu-id="06434-114">Navigate to a new source control server location for the specified item.</span></span>  
  
 <span data-ttu-id="06434-115">**“列”**</span><span class="sxs-lookup"><span data-stu-id="06434-115">**Columns**</span></span>  
 <span data-ttu-id="06434-116">标识要显示的列以及显示它们的顺序。</span><span class="sxs-lookup"><span data-stu-id="06434-116">Identify columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="06434-117">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="06434-117">**Connect**</span></span>  
 <span data-ttu-id="06434-118">在选定项和源代码管理服务器之间创建连接。</span><span class="sxs-lookup"><span data-stu-id="06434-118">Create a connection between selected items and the source control server.</span></span>  
  
 <span data-ttu-id="06434-119">**已连接**</span><span class="sxs-lookup"><span data-stu-id="06434-119">**Connected**</span></span>  
 <span data-ttu-id="06434-120">显示选定解决方案或项目的连接状态。</span><span class="sxs-lookup"><span data-stu-id="06434-120">Displays the connection status of a selected solution or project.</span></span>  
  
 <span data-ttu-id="06434-121">**取消**</span><span class="sxs-lookup"><span data-stu-id="06434-121">**Disconnect**</span></span>  
 <span data-ttu-id="06434-122">断开计算机上解决方案或项目的本地副本与数据库中其主副本的连接。</span><span class="sxs-lookup"><span data-stu-id="06434-122">Disconnect the local copy of a solution or project on your computer from its master copy in the database.</span></span> <span data-ttu-id="06434-123">在断开计算机与源代码管理服务器的连接之前（例如在便携式计算机上脱机工作时），使用此命令。</span><span class="sxs-lookup"><span data-stu-id="06434-123">Use this command before disconnecting your computer from the source control server, for example, when working offline on your laptop.</span></span>  
  
 <span data-ttu-id="06434-124">**确定**</span><span class="sxs-lookup"><span data-stu-id="06434-124">**OK**</span></span>  
 <span data-ttu-id="06434-125">接受在对话框中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="06434-125">Accept changes made in the dialog box.</span></span>  
  
 <span data-ttu-id="06434-126">**提供程序**</span><span class="sxs-lookup"><span data-stu-id="06434-126">**Provider**</span></span>  
 <span data-ttu-id="06434-127">显示您的源代码管理插件的名称。</span><span class="sxs-lookup"><span data-stu-id="06434-127">Displays the name of your source control plug-in.</span></span>  
  
 <span data-ttu-id="06434-128">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="06434-128">**Refresh**</span></span>  
 <span data-ttu-id="06434-129">刷新在此对话框中列出的所有项目的连接信息。</span><span class="sxs-lookup"><span data-stu-id="06434-129">Refreshes the connection information for all projects listed in this dialog box.</span></span>  
  
 <span data-ttu-id="06434-130">**服务器绑定**</span><span class="sxs-lookup"><span data-stu-id="06434-130">**Server Binding**</span></span>  
 <span data-ttu-id="06434-131">指示项绑定到源代码管理服务器。</span><span class="sxs-lookup"><span data-stu-id="06434-131">Indicates the item's binding to a source control server.</span></span>  
  
 <span data-ttu-id="06434-132">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="06434-132">**Server Name**</span></span>  
 <span data-ttu-id="06434-133">显示将相应解决方案或项目绑定到的源代码管理服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="06434-133">Displays the name of the source control server to which the corresponding solution or project is bound.</span></span>  
  
 <span data-ttu-id="06434-134">**解决方案/项目**</span><span class="sxs-lookup"><span data-stu-id="06434-134">**Solution/Project**</span></span>  
 <span data-ttu-id="06434-135">显示当前选择中的每个解决方案和项目的名称。</span><span class="sxs-lookup"><span data-stu-id="06434-135">Displays the name of each solution and project in the current selection.</span></span>  
  
 <span data-ttu-id="06434-136">**Sort**</span><span class="sxs-lookup"><span data-stu-id="06434-136">**Sort**</span></span>  
 <span data-ttu-id="06434-137">对显示的列的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="06434-137">Sort the order of displayed columns.</span></span>  
  
 <span data-ttu-id="06434-138">**Status**</span><span class="sxs-lookup"><span data-stu-id="06434-138">**Status**</span></span>  
 <span data-ttu-id="06434-139">标识项的绑定和连接状态。</span><span class="sxs-lookup"><span data-stu-id="06434-139">Identifies the binding and connection status of an item.</span></span> <span data-ttu-id="06434-140">可能的选项包括：</span><span class="sxs-lookup"><span data-stu-id="06434-140">Possible options are:</span></span>  
  
|<span data-ttu-id="06434-141">**选项**</span><span class="sxs-lookup"><span data-stu-id="06434-141">**Option**</span></span>|<span data-ttu-id="06434-142">**说明**</span><span class="sxs-lookup"><span data-stu-id="06434-142">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="06434-143">有效</span><span class="sxs-lookup"><span data-stu-id="06434-143">Valid</span></span>|<span data-ttu-id="06434-144">项已正确绑定并连接到它所属的服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="06434-144">The item is correctly bound and connected to the server folder to which it belongs.</span></span>|  
|<span data-ttu-id="06434-145">无效</span><span class="sxs-lookup"><span data-stu-id="06434-145">Invalid</span></span>|<span data-ttu-id="06434-146">项没有正确绑定到它所属的文件夹或者与该文件夹断开了连接。</span><span class="sxs-lookup"><span data-stu-id="06434-146">The item is incorrectly bound to or disconnected from the folder to which it belongs.</span></span> <span data-ttu-id="06434-147">对于此项，请使用 "**添加到源代码管理**" 命令而不是 "**绑定**"。</span><span class="sxs-lookup"><span data-stu-id="06434-147">Use the **Add to Source Control** command instead of **Bind** for this item.</span></span>|  
|<span data-ttu-id="06434-148">未知</span><span class="sxs-lookup"><span data-stu-id="06434-148">Unknown</span></span>|<span data-ttu-id="06434-149">尚未确定源代码管理下项的状态。</span><span class="sxs-lookup"><span data-stu-id="06434-149">The status of the item under source control has not yet been determined.</span></span>|  
|<span data-ttu-id="06434-150">不受控制</span><span class="sxs-lookup"><span data-stu-id="06434-150">Not Controlled</span></span>|<span data-ttu-id="06434-151">该项尚未置于源代码管理下。</span><span class="sxs-lookup"><span data-stu-id="06434-151">The item has not been placed under source control.</span></span>|  
  
 <span data-ttu-id="06434-152">**取消绑定**</span><span class="sxs-lookup"><span data-stu-id="06434-152">**Unbind**</span></span>  
 <span data-ttu-id="06434-153">显示 "**源代码管理**" 对话框，允许您从源代码管理中删除所选项，并从其现有文件夹中永久取消项关联。</span><span class="sxs-lookup"><span data-stu-id="06434-153">Display the **Source Control** dialog box to allow you to remove selected items from source control and permanently disassociate the items from their present folders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06434-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06434-154">See Also</span></span>  
 [<span data-ttu-id="06434-155">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="06434-155">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
