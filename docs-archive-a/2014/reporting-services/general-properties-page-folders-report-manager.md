---
title: "\"常规属性\" 页，文件夹 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1c3fbf2e9020ac5d1fe5ebbd1e9ed48b45adb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590591"
---
# <a name="general-properties-page-folders-report-manager"></a><span data-ttu-id="5edd9-102">文件夹的“常规”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="5edd9-102">General Properties Page, Folders (Report Manager)</span></span>
  <span data-ttu-id="5edd9-103">使用文件夹的“常规”属性页可以查看和设置所创建文件夹的属性。</span><span class="sxs-lookup"><span data-stu-id="5edd9-103">Use the General properties page for folders to view and set properties for the folders that you create.</span></span> <span data-ttu-id="5edd9-104">有关创建或修改文件夹的用户以及修改文件夹的时间的信息显示在“常规属性”页面顶部。</span><span class="sxs-lookup"><span data-stu-id="5edd9-104">Information about who created or modified the folder and when the folder was modified appear at the top of the General properties page.</span></span>  
  
 <span data-ttu-id="5edd9-105">文件夹属性也包括安全性设置。</span><span class="sxs-lookup"><span data-stu-id="5edd9-105">Folder properties also include security settings.</span></span> <span data-ttu-id="5edd9-106">有关文件夹安全性的详细信息，请参阅[保护文件夹](security/secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="5edd9-106">For more information about folder security, see [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="5edd9-107">不能在报表服务器命名空间中重命名或移动专用文件夹，例如主文件夹、我的报表和用户文件夹。</span><span class="sxs-lookup"><span data-stu-id="5edd9-107">Special-purpose folders such as Home, My Reports, and Users folders cannot be renamed or moved within the report server namespace.</span></span> <span data-ttu-id="5edd9-108">这些文件夹的“常规”属性页不可用。</span><span class="sxs-lookup"><span data-stu-id="5edd9-108">The General properties page is not available for these folders.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="5edd9-109">导航</span><span class="sxs-lookup"><span data-stu-id="5edd9-109">Navigation</span></span>  
 <span data-ttu-id="5edd9-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="5edd9-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a><span data-ttu-id="5edd9-111">打开文件夹的“常规属性”页</span><span class="sxs-lookup"><span data-stu-id="5edd9-111">To open the General properties page for a folder</span></span>  
  
1.  <span data-ttu-id="5edd9-112">打开报表管理器，并打开您要查看或配置属性的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5edd9-112">Open Report Manager, and open the folder for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="5edd9-113">在文件夹标志下，在工具栏中单击 **“文件夹设置”**。</span><span class="sxs-lookup"><span data-stu-id="5edd9-113">Under the folder banner, in the toolbar, click **Folder Settings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5edd9-114">选项</span><span class="sxs-lookup"><span data-stu-id="5edd9-114">Options</span></span>  
 <span data-ttu-id="5edd9-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="5edd9-115">**Name**</span></span>  
 <span data-ttu-id="5edd9-116">指定文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="5edd9-116">Specify a name for the folder.</span></span> <span data-ttu-id="5edd9-117">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="5edd9-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="5edd9-118">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="5edd9-118">It can also include spaces and some symbols.</span></span> <span data-ttu-id="5edd9-119">在指定名称时，不得使用字符 ; ?</span><span class="sxs-lookup"><span data-stu-id="5edd9-119">Do not use the characters ; ?</span></span> <span data-ttu-id="5edd9-120">： \@ & = +，$ \* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="5edd9-120">: \@ & = + , $ \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="5edd9-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="5edd9-121">**Description**</span></span>  
 <span data-ttu-id="5edd9-122">键入对文件夹内容的说明。</span><span class="sxs-lookup"><span data-stu-id="5edd9-122">Type a description of the folder contents.</span></span> <span data-ttu-id="5edd9-123">有权访问该文件夹的用户可以在“内容”页中查看此说明。</span><span class="sxs-lookup"><span data-stu-id="5edd9-123">This description appears on the Contents page for users who have permission to access the folder.</span></span>  
  
 <span data-ttu-id="5edd9-124">**在列表视图中隐藏**</span><span class="sxs-lookup"><span data-stu-id="5edd9-124">**Hide in list view**</span></span>  
 <span data-ttu-id="5edd9-125">选择此选项可对正在报表管理器中使用列表视图模式的用户隐藏文件夹。</span><span class="sxs-lookup"><span data-stu-id="5edd9-125">Select this option to hide the folder from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="5edd9-126">列表视图模式是浏览报表服务器文件夹层次结构时的默认视图格式。</span><span class="sxs-lookup"><span data-stu-id="5edd9-126">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="5edd9-127">在列表视图中，项的名称和说明可跨越页面。</span><span class="sxs-lookup"><span data-stu-id="5edd9-127">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="5edd9-128">备用格式为详细信息视图。</span><span class="sxs-lookup"><span data-stu-id="5edd9-128">The alternate format is details view.</span></span> <span data-ttu-id="5edd9-129">详细信息视图省略了说明，但包含项的其他信息。</span><span class="sxs-lookup"><span data-stu-id="5edd9-129">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="5edd9-130">虽然可以在列表视图中隐藏项，但不能在详细信息视图中隐藏项。</span><span class="sxs-lookup"><span data-stu-id="5edd9-130">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="5edd9-131">如果希望限制访问项，必须创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="5edd9-131">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="5edd9-132">**应用**</span><span class="sxs-lookup"><span data-stu-id="5edd9-132">**Apply**</span></span>  
 <span data-ttu-id="5edd9-133">单击此选项可保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="5edd9-133">Click to save your changes.</span></span>  
  
 <span data-ttu-id="5edd9-134">**删除**</span><span class="sxs-lookup"><span data-stu-id="5edd9-134">**Delete**</span></span>  
 <span data-ttu-id="5edd9-135">单击此选项可删除文件夹及其内容。</span><span class="sxs-lookup"><span data-stu-id="5edd9-135">Click to remove the folder and its contents.</span></span>  
  
 <span data-ttu-id="5edd9-136">**移动**</span><span class="sxs-lookup"><span data-stu-id="5edd9-136">**Move**</span></span>  
 <span data-ttu-id="5edd9-137">单击此选项可在报表服务器命名空间内重新定位报表或文件夹。</span><span class="sxs-lookup"><span data-stu-id="5edd9-137">Click to relocate a report or folder within the report server namespace.</span></span> <span data-ttu-id="5edd9-138">单击此按钮将打开“移动项”页，使用此页可以浏览文件夹以选择新的文件夹位置。</span><span class="sxs-lookup"><span data-stu-id="5edd9-138">Clicking this button opens the Move Items page that allows you to browse folders for a new folder location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5edd9-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5edd9-139">See Also</span></span>  
 <span data-ttu-id="5edd9-140">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5edd9-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="5edd9-141">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="5edd9-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
