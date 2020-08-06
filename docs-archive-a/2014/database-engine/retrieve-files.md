---
title: 检索文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebced9ea69f304344893289140687cd6d511e923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589856"
---
# <a name="retrieve-files"></a><span data-ttu-id="34c3c-102">检索文件</span><span class="sxs-lookup"><span data-stu-id="34c3c-102">Retrieve Files</span></span>
  <span data-ttu-id="34c3c-103">打开源代码管理的项目后，可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 将项目文件的本地副本从源代码管理存储区检索到项目所在的本地目录中。</span><span class="sxs-lookup"><span data-stu-id="34c3c-103">After you have opened a source-controlled project, you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to retrieve local copies of project files from the source control store to the local directory in which the project resides.</span></span>  
  
 <span data-ttu-id="34c3c-104">可以通过以下方法使用集成的源代码管理检索文件：</span><span class="sxs-lookup"><span data-stu-id="34c3c-104">You can use integrated source control to retrieve files in the following ways:</span></span>  
  
-   <span data-ttu-id="34c3c-105">\*\* (递归) 命令获取最新版本\*\*</span><span class="sxs-lookup"><span data-stu-id="34c3c-105">**Get Latest Version (Recursive)** command</span></span>  
  
     <span data-ttu-id="34c3c-106">检索选定文件的最新签入版本。</span><span class="sxs-lookup"><span data-stu-id="34c3c-106">Retrieves the latest checked in version of the selected files.</span></span> <span data-ttu-id="34c3c-107">如果选择了解决方案或项目，则此命令将检索所有解决方案和项目文件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="34c3c-107">If a solution or project is selected, this command retrieves the latest version of all solution and project files.</span></span>  
  
-   <span data-ttu-id="34c3c-108">**Get**命令</span><span class="sxs-lookup"><span data-stu-id="34c3c-108">**Get** command</span></span>  
  
     <span data-ttu-id="34c3c-109">显示 "**获取**" 对话框，您可以使用该对话框检索选定文件的最新版本，或检索选定解决方案或项目中的文件子集。</span><span class="sxs-lookup"><span data-stu-id="34c3c-109">Displays the **Get** dialog box, which you can use to retrieve the latest version of a selected file, or to retrieve a subset of the files in the selected solution or project.</span></span>  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a><span data-ttu-id="34c3c-110">检索项目中所有文件的最新版本</span><span class="sxs-lookup"><span data-stu-id="34c3c-110">To retrieve the latest version of all the files in a project</span></span>  
  
1.  <span data-ttu-id="34c3c-111">在“解决方案资源管理器”中，选择项目。</span><span class="sxs-lookup"><span data-stu-id="34c3c-111">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="34c3c-112">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**获取 (递归) 的最新版本**。</span><span class="sxs-lookup"><span data-stu-id="34c3c-112">On the **File** menu, point to **Source Control**, and then click **Get Latest Version (Recursive)**.</span></span>  
  
 <span data-ttu-id="34c3c-113">项目中文件的最新版本将被检索到本地磁盘上的项目位置。</span><span class="sxs-lookup"><span data-stu-id="34c3c-113">The most recent versions of the files in the project are retrieved to the project location on your local disk.</span></span>  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a><span data-ttu-id="34c3c-114">只检索项目中的某些文件</span><span class="sxs-lookup"><span data-stu-id="34c3c-114">To retrieve only certain files in a project</span></span>  
  
1.  <span data-ttu-id="34c3c-115">在解决方案资源管理器中，选择要检索的项。</span><span class="sxs-lookup"><span data-stu-id="34c3c-115">In Solution Explorer, select the item you want to retrieve.</span></span>  
  
2.  <span data-ttu-id="34c3c-116">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**获取**"。</span><span class="sxs-lookup"><span data-stu-id="34c3c-116">On the **File** menu, point to **Source Control**, and then click **Get**.</span></span>  
  
3.  <span data-ttu-id="34c3c-117">在 "**获取**" 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="34c3c-117">In the **Get** dialog box, click **OK**.</span></span> <span data-ttu-id="34c3c-118">或者，如果在解决方案资源管理器中选择了一个解决方案或项目，则对于不希望检索的项，请清除其旁边显示的复选框。</span><span class="sxs-lookup"><span data-stu-id="34c3c-118">Alternatively, if you selected a solution or project in Solution Explorer, clear the check boxes that appear next to the items you do not want to retrieve.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c3c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34c3c-119">See Also</span></span>  
 <span data-ttu-id="34c3c-120">["获取" 对话框 &#40;源代码管理&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="34c3c-120">[Get Dialog Box &#40;Source Control&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span></span>  
 <span data-ttu-id="34c3c-121">[设置和检索版本信息](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="34c3c-121">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="34c3c-122">[查看项目历史记录](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="34c3c-122">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 [<span data-ttu-id="34c3c-123">查看文件状态</span><span class="sxs-lookup"><span data-stu-id="34c3c-123">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
  
