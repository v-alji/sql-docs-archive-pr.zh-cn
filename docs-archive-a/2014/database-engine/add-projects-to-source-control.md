---
title: 向源代码管理添加项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0afef4ef91e4d80db7e956d03a95a2ecffe1dc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579037"
---
# <a name="add-projects-to-source-control"></a><span data-ttu-id="8b760-102">将项目添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="8b760-102">Add Projects to Source Control</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8b760-103">解决方案可以承载多个脚本项目。</span><span class="sxs-lookup"><span data-stu-id="8b760-103">solutions can host multiple script projects.</span></span> <span data-ttu-id="8b760-104">向源代码管理中添加项目的方式取决于项目所属的解决方案是否接受源代码管理。</span><span class="sxs-lookup"><span data-stu-id="8b760-104">How you add a project to source control depends upon whether the solution to which the project belongs is under source control.</span></span> <span data-ttu-id="8b760-105">如果解决方案处于源代码管理下，则签入解决方案时会自动向源代码管理中添加项目。</span><span class="sxs-lookup"><span data-stu-id="8b760-105">If the solution is under source control, checking in the solution automatically adds the project to source control.</span></span> <span data-ttu-id="8b760-106">有关签入解决方案的详细信息，请参阅[签入文件](../../2014/database-engine/check-in-files.md)。</span><span class="sxs-lookup"><span data-stu-id="8b760-106">For more information about checking in solutions, see [Check In Files](../../2014/database-engine/check-in-files.md).</span></span>  
  
 <span data-ttu-id="8b760-107">如果该项目所属的解决方案未处于源代码管理下，则可将该解决方案添加到源代码管理中，这样会自动添加解决方案的项目。</span><span class="sxs-lookup"><span data-stu-id="8b760-107">If the solution that this project belongs to is not under source control, you can add that solution to source control, which then automatically adds the solution's projects.</span></span> <span data-ttu-id="8b760-108">有关将解决方案添加到源代码管理的详细信息，请参阅[将解决方案添加到源代码管理](../../2014/database-engine/add-solutions-to-source-control.md)。</span><span class="sxs-lookup"><span data-stu-id="8b760-108">For more information about adding solutions to source control, see [Add Solutions to Source Control](../../2014/database-engine/add-solutions-to-source-control.md).</span></span>  
  
 <span data-ttu-id="8b760-109">如果不想将解决方案添加到源代码管理，可以使用 "**将所选内容添加到源代码管理**" 命令手动添加项目。</span><span class="sxs-lookup"><span data-stu-id="8b760-109">If you do not want to add the solution to source control, you can use the **Add Selection to Source Control** command to add the project manually.</span></span>  
  
 <span data-ttu-id="8b760-110">数据库对象不直接受源代码管理提供程序的保护，但是可以创建数据库对象脚本并将脚本保存在源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="8b760-110">Database objects are not directly protected by the source control provider, but you can create scripts of database objects and save the scripts under source control.</span></span>  
  
### <a name="to-add-a-project-to-source-control"></a><span data-ttu-id="8b760-111">将项目添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="8b760-111">To add a project to source control</span></span>  
  
1.  <span data-ttu-id="8b760-112">在解决方案资源管理器中，选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="8b760-112">In Solution Explorer, select a project.</span></span>  
  
2.  <span data-ttu-id="8b760-113">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**将所选项目添加到源代码管理**"。</span><span class="sxs-lookup"><span data-stu-id="8b760-113">On the **File** menu, point to **Source Control**, and then click **Add Selected Projects to Source Control**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b760-114">如果使用 "**将选定项目添加到源代码管理**" 命令添加属于源代码管理的解决方案的项目，系统将提示您是要将该项目添加为源代码管理的解决方案的子文件夹，还是将该项目添加为单独的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8b760-114">If you use the **Add Selected Projects to Source Control** command to add a project that belongs to a source-controlled solution, you are prompted whether you want to add the project as a subfolder of the source-controlled solution or to add the project as a separate folder.</span></span>  
  
3.  <span data-ttu-id="8b760-115">如果出现提示，请登录到源代码管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="8b760-115">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="8b760-116">此时将显示 "**添加到 SourceSafe 项目**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8b760-116">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="8b760-117">项目的名称将显示在 "**项目**" 框中。</span><span class="sxs-lookup"><span data-stu-id="8b760-117">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="8b760-118">在 "**文件夹**" 列表中，打开要在其中放置项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8b760-118">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="8b760-119">或者，您可以单击 "**创建**" 以创建一个文件夹，该文件夹的名称显示在 "**项目**" 框中。</span><span class="sxs-lookup"><span data-stu-id="8b760-119">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b760-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b760-120">See Also</span></span>  
 [<span data-ttu-id="8b760-121">将解决方案和项目添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="8b760-121">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
