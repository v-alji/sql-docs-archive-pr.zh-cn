---
title: 向源代码管理中添加解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding solutions
- solutions [SQL Server Management Studio], adding
ms.assetid: b9e36569-616d-4e47-9140-0978a9bfe923
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1c72949fd8257332a36af52ab287ed326eed5274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689022"
---
# <a name="add-solutions-to-source-control"></a><span data-ttu-id="6ae70-102">在源代码管理中添加解决方案</span><span class="sxs-lookup"><span data-stu-id="6ae70-102">Add Solutions to Source Control</span></span>
  <span data-ttu-id="6ae70-103">将解决方案添加到源代码管理中时，通常需要添加整个解决方案及其包含的所有项目。</span><span class="sxs-lookup"><span data-stu-id="6ae70-103">When you add a solution to source control, you usually want to add the entire solution and all the projects it contains.</span></span> <span data-ttu-id="6ae70-104">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 将解决方案添加到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="6ae70-104">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to add a solution to source control.</span></span>  
  
 <span data-ttu-id="6ae70-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 项目完全驻留在本地磁盘上。</span><span class="sxs-lookup"><span data-stu-id="6ae70-105">A [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] project resides completely on your local disk.</span></span> <span data-ttu-id="6ae70-106">编辑、保存和生成项目均在本地进行。</span><span class="sxs-lookup"><span data-stu-id="6ae70-106">You edit, save, and build projects locally.</span></span> <span data-ttu-id="6ae70-107">将项目添加到源代码管理后，可以使用 "**签出**" 命令将项目的文件从源代码管理中签出。</span><span class="sxs-lookup"><span data-stu-id="6ae70-107">After adding the project to source control, you can use the **Check Out** command to check the project's files out of source control.</span></span>  
  
### <a name="to-add-a-solution-to-source-control"></a><span data-ttu-id="6ae70-108">将解决方案添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="6ae70-108">To add a solution to source control</span></span>  
  
1.  <span data-ttu-id="6ae70-109">在解决方案资源管理器中，选择要添加的解决方案。</span><span class="sxs-lookup"><span data-stu-id="6ae70-109">In Solution Explorer, select the solution you want to add.</span></span>  
  
2.  <span data-ttu-id="6ae70-110">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**将解决方案添加到源代码管理**"。</span><span class="sxs-lookup"><span data-stu-id="6ae70-110">On the **File** menu, point to **Source Control**, and then click **Add Solution to Source Control**.</span></span>  
  
3.  <span data-ttu-id="6ae70-111">如果出现提示，请登录到源代码管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="6ae70-111">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="6ae70-112">此时将显示 "**添加到 SourceSafe 项目**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="6ae70-112">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="6ae70-113">项目的名称将显示在 "**项目**" 框中。</span><span class="sxs-lookup"><span data-stu-id="6ae70-113">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="6ae70-114">在 "**文件夹**" 列表中，打开要在其中放置项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ae70-114">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="6ae70-115">或者，您可以单击 "**创建**" 以创建一个文件夹，该文件夹的名称显示在 "**项目**" 框中。</span><span class="sxs-lookup"><span data-stu-id="6ae70-115">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae70-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ae70-116">See Also</span></span>  
 <span data-ttu-id="6ae70-117">[将解决方案和项目添加到源代码管理](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="6ae70-117">[Add Solutions and Projects to Source Control](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span></span>  
 [<span data-ttu-id="6ae70-118">将项目添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="6ae70-118">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)  
  
  
