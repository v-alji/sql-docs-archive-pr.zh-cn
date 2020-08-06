---
title: 从源代码管理打开解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 808a4851bcc1f51690b2ba924a859bcccf9a6adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590348"
---
# <a name="open-solutions-from-source-control"></a><span data-ttu-id="2d041-102">从源代码管理打开解决方案</span><span class="sxs-lookup"><span data-stu-id="2d041-102">Open Solutions from Source Control</span></span>
  <span data-ttu-id="2d041-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 直接从源代码管理打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="2d041-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open solutions directly from source control.</span></span> <span data-ttu-id="2d041-104">如果执行此操作，Studio 环境将在指定的位置创建最新版本解决方案文件的副本。</span><span class="sxs-lookup"><span data-stu-id="2d041-104">When you do this, the Studio environment creates a copy of the latest version of the solution files at the location you specify.</span></span>  
  
 <span data-ttu-id="2d041-105">如果本地磁盘中没有解决方案的本地副本，则必须先从源代码管理打开项目，然后才能使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 签出解决方案或检索解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="2d041-105">If a local copy of the solution does not exist on your local disk, you must open the project from source control before you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out the solution or retrieve solution files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d041-106">如果已经有了要从源代码管理打开的解决方案的本地副本，系统会提示您覆盖本地副本。</span><span class="sxs-lookup"><span data-stu-id="2d041-106">If you already have a local copy of the solution you are opening from source control, you are prompted to overwrite the local copy.</span></span>  
  
### <a name="to-open-a-solution-from-source-control"></a><span data-ttu-id="2d041-107">从源代码管理打开解决方案</span><span class="sxs-lookup"><span data-stu-id="2d041-107">To open a solution from source control</span></span>  
  
1.  <span data-ttu-id="2d041-108">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**从源代码管理打开**"。</span><span class="sxs-lookup"><span data-stu-id="2d041-108">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="2d041-109">如果出现提示，请登录到 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。</span><span class="sxs-lookup"><span data-stu-id="2d041-109">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="2d041-110">在 "**从 SourceSafe 创建本地项目**" 对话框中，选择包含要打开的解决方案的文件夹，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="2d041-110">In the **Create local project from SourceSafe** dialog box, select the folder that contains the solution you want to open, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="2d041-111">如果本地磁盘驱动器上已存在解决方案的工作文件夹，则 "**在文件夹中创建一个新项目**" 框将发生更改，以标识本地目录。</span><span class="sxs-lookup"><span data-stu-id="2d041-111">If a working folder for the solution already exists on your local disk drive, the **Create a new project in the folder** box changes to identify the local directory.</span></span> <span data-ttu-id="2d041-112">如果不存在解决方案的工作文件夹，则可以键入或通过浏览找到要在其中打开解决方案的本地目录。</span><span class="sxs-lookup"><span data-stu-id="2d041-112">If no working folder for the solution exists, you can type or browse to the local directory in which the solution should be opened.</span></span>  
  
5.  <span data-ttu-id="2d041-113">在 "**打开解决方案**" 对话框中，选择解决方案文件，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="2d041-113">In the **Open Solution** dialog box, select the solution file, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d041-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d041-114">See Also</span></span>  
 [<span data-ttu-id="2d041-115">从源代码管理打开项目</span><span class="sxs-lookup"><span data-stu-id="2d041-115">Open Projects from Source Control</span></span>](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
