---
title: 比较文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- versions [SQL Server], file comparisons
- comparing files
- file comparisons [SQL Server]
ms.assetid: 728811c4-5d7a-4420-abce-f56c5a0994d2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f29bf7098f0c73d0b672e20b973b1347349b31f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588056"
---
# <a name="compare-files"></a><span data-ttu-id="9693e-102">比较文件</span><span class="sxs-lookup"><span data-stu-id="9693e-102">Compare Files</span></span>
  <span data-ttu-id="9693e-103">可以对文件进行比较，确定文件是如何进展到其现有状态的。</span><span class="sxs-lookup"><span data-stu-id="9693e-103">You can compare files to determine how a file has progressed to its present state.</span></span> <span data-ttu-id="9693e-104">例如，如果在签入特定的源文件版本后，在代码项目的内部版本中检测到一个缺陷，则可以将当前文件版本与以前的版本进行比较。</span><span class="sxs-lookup"><span data-stu-id="9693e-104">For example, if you detect a defect in a build of your code project after a particular source file version is checked in, you can compare the current file version to a previous one.</span></span> <span data-ttu-id="9693e-105">这有助于精确定位导致缺陷的代码。</span><span class="sxs-lookup"><span data-stu-id="9693e-105">This helps you to pinpoint the code that introduced the defect.</span></span>  
  
 <span data-ttu-id="9693e-106">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，将项目或文件的本地副本与存储在源代码管理中的版本进行比较，也可以比较两个本地文件。</span><span class="sxs-lookup"><span data-stu-id="9693e-106">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to compare a local copy of a project or file to the version stored in source control, or to compare two local files.</span></span> <span data-ttu-id="9693e-107">此外，使用**History**命令，可以比较任意两个受源代码管理的版本。</span><span class="sxs-lookup"><span data-stu-id="9693e-107">Also, using the **History** command, you can compare any two source-controlled versions.</span></span>  
  
### <a name="to-compare-files"></a><span data-ttu-id="9693e-108">比较文件</span><span class="sxs-lookup"><span data-stu-id="9693e-108">To compare files</span></span>  
  
1.  <span data-ttu-id="9693e-109">在解决方案资源管理器中，选择一个项目或其中一个项目文件。</span><span class="sxs-lookup"><span data-stu-id="9693e-109">In Solution Explorer, select either a project or one of the project files.</span></span>  
  
2.  <span data-ttu-id="9693e-110">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**比较**"。</span><span class="sxs-lookup"><span data-stu-id="9693e-110">On the **File** menu, point to **Source Control**, and click **Compare**.</span></span>  
  
3.  <span data-ttu-id="9693e-111">在 "**差异选项**" 对话框中，选择相应的选项，然后单击 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="9693e-111">In the **Difference Options** dialog box, select the appropriate options, and then click **Report**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9693e-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9693e-112">See Also</span></span>  
 <span data-ttu-id="9693e-113">[设置和检索版本信息](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="9693e-113">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="9693e-114">[查看文件历史记录](../../2014/database-engine/view-file-history.md) </span><span class="sxs-lookup"><span data-stu-id="9693e-114">[View File History](../../2014/database-engine/view-file-history.md) </span></span>  
 <span data-ttu-id="9693e-115">[查看项目历史记录](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="9693e-115">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 <span data-ttu-id="9693e-116">[查看文件状态](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="9693e-116">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 [<span data-ttu-id="9693e-117">检索文件</span><span class="sxs-lookup"><span data-stu-id="9693e-117">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
  
