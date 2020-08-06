---
title: 另存为 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.saveas
helpviewer_keywords:
- Save As dialog box
ms.assetid: 61347757-f5a3-481d-8b05-1fed086629b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: e47d9c37371283fc6fba2754896d77b51d26cef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591698"
---
# <a name="save-as"></a><span data-ttu-id="5e32a-102">另存为</span><span class="sxs-lookup"><span data-stu-id="5e32a-102">Save As</span></span>
  <span data-ttu-id="5e32a-103">使用此对话框可以将当前项的实例以指定的文件格式保存到指定位置。</span><span class="sxs-lookup"><span data-stu-id="5e32a-103">Use this dialog box to save an instance of the current item at a specified location in a specified file format.</span></span> <span data-ttu-id="5e32a-104">若要显示此对话框，请**Save**单击 *\<file>* "**文件**" 菜单上的 "另存**为**" (其中 *\<file>* 是当前项) 的名称，或者在代码编辑器中按 ALT + F。</span><span class="sxs-lookup"><span data-stu-id="5e32a-104">To display this dialog box, click **Save** *\<file>* **As** on the **File** menu (where *\<file>* is the name of the current item), or press ALT+F, A in the Code Editor.</span></span>  
  
## <a name="central-panel"></a><span data-ttu-id="5e32a-105">中央面板</span><span class="sxs-lookup"><span data-stu-id="5e32a-105">Central Panel</span></span>  
 <span data-ttu-id="5e32a-106">**保存于**</span><span class="sxs-lookup"><span data-stu-id="5e32a-106">**Save in**</span></span>  
 <span data-ttu-id="5e32a-107">在此下拉菜单中查找现有的项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="5e32a-107">Locate the existing project folder from this drop-down menu.</span></span> <span data-ttu-id="5e32a-108">在此列表中选择某个文件夹会在下面的主窗格中显示该文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="5e32a-108">Selecting a folder from this list displays the contents of the folder in the primary pane below.</span></span>  
  
 <span data-ttu-id="5e32a-109">**文件名**</span><span class="sxs-lookup"><span data-stu-id="5e32a-109">**File name**</span></span>  
 <span data-ttu-id="5e32a-110">使用此选项可以查看当前的文件名，更改文件名，或在显示的文件和文件夹中进行筛选。</span><span class="sxs-lookup"><span data-stu-id="5e32a-110">Use this option to view the current file name, change the file name, or filter the files and folders that are displayed.</span></span> <span data-ttu-id="5e32a-111">若要在显示的文件和文件夹中进行筛选，请输入要筛选的文件的完整文件名或部分文件名。</span><span class="sxs-lookup"><span data-stu-id="5e32a-111">To filter the files and folders that are displayed, enter a full or partial file name on which to filter.</span></span> <span data-ttu-id="5e32a-112">可以使用星号 (`*`) 作为通配符。</span><span class="sxs-lookup"><span data-stu-id="5e32a-112">You can use the asterisk (`*`) as a wildcard.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="5e32a-113">若要显示位于 Web 和网络位置上的文件，请在“文件名”  框中输入 URL 或网络路径。</span><span class="sxs-lookup"><span data-stu-id="5e32a-113">To display files on Web and network locations, enter a URL or network path in the **File name** box.</span></span> <span data-ttu-id="5e32a-114">例如，输入“<http://mywebsite>”可显示“mywebsite”Web 位置中可用的文件，输入“\\\myserver\myshare”可显示“myserver”上的“myshare”位置中可用的文件。</span><span class="sxs-lookup"><span data-stu-id="5e32a-114">For example, "<http://mywebsite>" displays the files available at the "mywebsite" Web location and "\\\myserver\myshare" displays the files available at the "myshare" location on "myserver".</span></span>  
  
 <span data-ttu-id="5e32a-115">**保存类型**</span><span class="sxs-lookup"><span data-stu-id="5e32a-115">**Save as type**</span></span>  
 <span data-ttu-id="5e32a-116">使用此选项可为所选项选择新的文件类型。</span><span class="sxs-lookup"><span data-stu-id="5e32a-116">Use this option to select a new file type for the selected item.</span></span> <span data-ttu-id="5e32a-117">显示的文件类型包括所选项可转换成的所有可用文件类型。</span><span class="sxs-lookup"><span data-stu-id="5e32a-117">The file types displayed include all available file types to which the selected item can be converted.</span></span>  
  
 <span data-ttu-id="5e32a-118">**高级保存选项**</span><span class="sxs-lookup"><span data-stu-id="5e32a-118">**Advanced Save Options**</span></span>  
 <span data-ttu-id="5e32a-119">若要访问“高级保存选项”  对话框，请选择“保存”  按钮右侧的小矩形，再单击“编码保存”  。</span><span class="sxs-lookup"><span data-stu-id="5e32a-119">To access the **Advanced Save Options Dialog Box**, select the small rectangle at the right of the **Save** button and then click **Save with Encoding**.</span></span> <span data-ttu-id="5e32a-120">使用此对话框可以指定文件编码以及要在行尾使用的字符。</span><span class="sxs-lookup"><span data-stu-id="5e32a-120">Use this dialog box to specify an encoding for the file and the characters to use at Line endings.</span></span>  
  
## <a name="left-panel"></a><span data-ttu-id="5e32a-121">左面板</span><span class="sxs-lookup"><span data-stu-id="5e32a-121">Left Panel</span></span>  
 <span data-ttu-id="5e32a-122">**桌面**</span><span class="sxs-lookup"><span data-stu-id="5e32a-122">**Desktop**</span></span>  
 <span data-ttu-id="5e32a-123">显示桌面上的所有文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="5e32a-123">Displays any files and folders located on the desktop.</span></span>  
  
 <span data-ttu-id="5e32a-124">**我的项目**</span><span class="sxs-lookup"><span data-stu-id="5e32a-124">**My Projects**</span></span>  
 <span data-ttu-id="5e32a-125">显示“我的项目”  或最近访问过的位置中的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="5e32a-125">Displays files and folders at the **My Projects** or the most recently visited location.</span></span>  
  
 <span data-ttu-id="5e32a-126">**我的电脑**</span><span class="sxs-lookup"><span data-stu-id="5e32a-126">**My Computer**</span></span>  
 <span data-ttu-id="5e32a-127">显示“我的电脑”  在计算机上的位置。</span><span class="sxs-lookup"><span data-stu-id="5e32a-127">Displays the **My Computer** location on your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e32a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e32a-128">See Also</span></span>  
 <span data-ttu-id="5e32a-129">[高级保存选项](advanced-save-options.md) </span><span class="sxs-lookup"><span data-stu-id="5e32a-129">[Advanced Save Options](advanced-save-options.md) </span></span>  
 [<span data-ttu-id="5e32a-130">管理使用编码的文件</span><span class="sxs-lookup"><span data-stu-id="5e32a-130">Manage Files with Encoding</span></span>](../solution/manage-files-with-encoding.md)  
  
  
