---
title: 新文件夹页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9212fc68-f0a6-4f79-83c1-84baf4d1957e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27c6a82c4911ba42215d4ab7dcafd666ddce5d54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588939"
---
# <a name="new-folder-page-report-manager"></a><span data-ttu-id="5b70d-102">“新建文件夹”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="5b70d-102">New Folder Page (Report Manager)</span></span>
  <span data-ttu-id="5b70d-103">使用“新建文件夹”页可以在报表服务器文件夹层次结构中创建新文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b70d-103">Use the New Folder page to create a new folder in the report server folder hierarchy.</span></span> <span data-ttu-id="5b70d-104">您创建的文件夹是存储在报表服务器数据库中的虚拟文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b70d-104">The folder that you create is a virtual folder that is stored in a report server database.</span></span> <span data-ttu-id="5b70d-105">未在计算机的文件系统中创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b70d-105">The folder is not created in the file system of your computer.</span></span>  
  
 <span data-ttu-id="5b70d-106">创建的文件夹将作为当前选定文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b70d-106">A folder is created in-place, as a subfolder of the folder that is currently selected.</span></span> <span data-ttu-id="5b70d-107">在创建文件夹以前，您应导航到要创建该文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="5b70d-107">Before creating a folder, you should navigate to the location where you want to create the folder.</span></span>  
  
 <span data-ttu-id="5b70d-108">创建文件夹后，您可以通过文件夹的“常规”属性页修改其名称和说明。</span><span class="sxs-lookup"><span data-stu-id="5b70d-108">After you create a folder, you can modify its name and description through the General properties page of the folder.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="5b70d-109">导航</span><span class="sxs-lookup"><span data-stu-id="5b70d-109">Navigation</span></span>  
 <span data-ttu-id="5b70d-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="5b70d-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-folder-page"></a><span data-ttu-id="5b70d-111">打开“新建文件夹”页</span><span class="sxs-lookup"><span data-stu-id="5b70d-111">To open the New Folder page</span></span>  
  
1.  <span data-ttu-id="5b70d-112">打开报表管理器，导航到要在其中创建新文件夹的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b70d-112">Open Report Manager, and navigate to the folder in which you want to create a new folder.</span></span>  
  
2.  <span data-ttu-id="5b70d-113">在工具栏中，单击 **“新建文件夹”**。</span><span class="sxs-lookup"><span data-stu-id="5b70d-113">In the toolbar, click **New Folder**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b70d-114">选项</span><span class="sxs-lookup"><span data-stu-id="5b70d-114">Options</span></span>  
 <span data-ttu-id="5b70d-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="5b70d-115">**Name**</span></span>  
 <span data-ttu-id="5b70d-116">指定文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="5b70d-116">Specify the name of the folder.</span></span> <span data-ttu-id="5b70d-117">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="5b70d-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="5b70d-118">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="5b70d-118">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="5b70d-119">在指定名称时，不得使用字符 ; ?</span><span class="sxs-lookup"><span data-stu-id="5b70d-119">Do not use the characters ; ?</span></span> <span data-ttu-id="5b70d-120">： \@ & = +，$/\* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="5b70d-120">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="5b70d-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="5b70d-121">**Description**</span></span>  
 <span data-ttu-id="5b70d-122">键入文件夹内容的说明。</span><span class="sxs-lookup"><span data-stu-id="5b70d-122">Type a description of folder contents.</span></span> <span data-ttu-id="5b70d-123">有权访问该文件夹的用户可以在“内容”页中看到此说明。</span><span class="sxs-lookup"><span data-stu-id="5b70d-123">This description appears in the Contents page to users who have permission to access the folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b70d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b70d-124">See Also</span></span>  
 <span data-ttu-id="5b70d-125">[创建、删除或修改文件夹 &#40;报表管理器&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5b70d-125">[Create, Delete, or Modify a Folder &#40;Report Manager&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span></span>  
 <span data-ttu-id="5b70d-126">["常规属性" 页，文件夹 &#40;报表管理器&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5b70d-126">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="5b70d-127">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5b70d-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="5b70d-128">["内容" 页 &#40;报表管理器&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5b70d-128">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="5b70d-129">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5b70d-129">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="5b70d-130">"常规属性" 页，文件夹 &#40;报表管理器&#41;</span><span class="sxs-lookup"><span data-stu-id="5b70d-130">General Properties Page, Folders &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/general-properties-page-folders-report-manager.md)  
  
  
