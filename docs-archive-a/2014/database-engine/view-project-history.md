---
title: 查看项目历史记录 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85028141050e19e6ed6394a5bb17709ac8f906ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590932"
---
# <a name="view-project-history"></a><span data-ttu-id="7e416-102">查看项目历史</span><span class="sxs-lookup"><span data-stu-id="7e416-102">View Project History</span></span>
  <span data-ttu-id="7e416-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) 项目的历史记录包括对每个项目文件执行的所有操作（包括文件创建、添加、删除和恢复）的列表。</span><span class="sxs-lookup"><span data-stu-id="7e416-103">The history of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) project includes a list of all the actions taken on each of the project files, including file creation, addition, deletion, and recovery.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e416-104">Visual SourceSafe 项目通常称为源代码管理服务器文件夹，它是服务器上存储源代码管理文件的服务器版本的存储位置。</span><span class="sxs-lookup"><span data-stu-id="7e416-104">A Visual SourceSafe project is more commonly referred to as the source control server folder, the location where the server version of a source-controlled file is stored on the server.</span></span>  
  
 <span data-ttu-id="7e416-105">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 检查当前已加载解决方案所属的 Visual SourceSafe 项目的历史记录。</span><span class="sxs-lookup"><span data-stu-id="7e416-105">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to examine the history of the Visual SourceSafe project to which the currently loaded solution belongs.</span></span> <span data-ttu-id="7e416-106">基于在项目历史记录中显示的信息，可以检索文件版本的本地副本，还原已删除的版本或在项目之间共享文件版本。</span><span class="sxs-lookup"><span data-stu-id="7e416-106">Based on the information displayed as part of the history of a project, you can retrieve local copies of file versions, restore deleted versions, or share a file version between projects.</span></span>  
  
### <a name="to-view-the-history-of-a-vss-project"></a><span data-ttu-id="7e416-107">查看 VSS 项目的历史记录</span><span class="sxs-lookup"><span data-stu-id="7e416-107">To view the history of a VSS project</span></span>  
  
1.  <span data-ttu-id="7e416-108">在“解决方案资源管理器”中，选择项目。</span><span class="sxs-lookup"><span data-stu-id="7e416-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="7e416-109">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**查看历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="7e416-109">On the **File** menu, point to **Source Control** and click **View History**.</span></span>  
  
3.  <span data-ttu-id="7e416-110">在 "**历史记录**" 对话框中 \<Project> ，执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="7e416-110">In the **History of** \<Project> dialog box, perform any of the following actions:</span></span>  
  
    -   <span data-ttu-id="7e416-111">查看所选文件的源代码管理系统副本。</span><span class="sxs-lookup"><span data-stu-id="7e416-111">View the source control system's copy of a selected file.</span></span>  
  
    -   <span data-ttu-id="7e416-112">查看有关所选文件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7e416-112">View detailed information about a selected file.</span></span>  
  
    -   <span data-ttu-id="7e416-113">将所选文件检索到本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="7e416-113">Retrieve a selected file to your local disk.</span></span>  
  
    -   <span data-ttu-id="7e416-114">签出所选文件。</span><span class="sxs-lookup"><span data-stu-id="7e416-114">Check out a selected file.</span></span>  
  
    -   <span data-ttu-id="7e416-115">在两个源代码管理项目之间共享所选文件。</span><span class="sxs-lookup"><span data-stu-id="7e416-115">Share a selected file between two source control projects.</span></span>  
  
    -   <span data-ttu-id="7e416-116">将历史记录报表导出到打印机、文件或剪贴板。</span><span class="sxs-lookup"><span data-stu-id="7e416-116">Export the history report to a printer, a file, or the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e416-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e416-117">See Also</span></span>  
 <span data-ttu-id="7e416-118">[设置和检索版本信息](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="7e416-118">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="7e416-119">[查看文件状态](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="7e416-119">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 <span data-ttu-id="7e416-120">[检索文件](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="7e416-120">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="7e416-121">比较文件</span><span class="sxs-lookup"><span data-stu-id="7e416-121">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
  
