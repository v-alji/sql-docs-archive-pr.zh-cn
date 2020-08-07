---
title: 第1课：创建 Web 服务客户端项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0070daa6-56b0-4663-83b2-44c96acafad8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: eda9413867c4ca6d44a5cf98b82be9bddc04d0f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690929"
---
# <a name="lesson-1-creating-the-web-service-client-project"></a><span data-ttu-id="c5fa7-102">第 1 课：创建 Web 服务客户端项目</span><span class="sxs-lookup"><span data-stu-id="c5fa7-102">Lesson 1: Creating the Web Service Client Project</span></span>
  <span data-ttu-id="c5fa7-103">针对本演练，您将创建访问报表服务器 Web 服务的简单控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-103">For this walkthrough, you will create a simple console application that accesses the Report Server Web service.</span></span> <span data-ttu-id="c5fa7-104">本演练假定您是在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 环境中进行开发的。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-104">This walkthrough assumes you are developing in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="c5fa7-105">创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="c5fa7-105">To create a console application</span></span>  
  
1.  <span data-ttu-id="c5fa7-106">在“文件”\*\*\*\* 菜单上指向“新建”\*\*\*\*，然后单击“项目”\*\*\*\* 打开“新建项目”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-106">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="c5fa7-107">在左窗格中的 "**已安装的模板**" 下，单击 " **Visual Basic** " 或 " **Visual c #** " 节点，然后从展开的列表中选择一类项目类型。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-107">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="c5fa7-108">选择 "**控制台应用程序**" 项目类型。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-108">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="c5fa7-109">在 "**名称**" 框中，输入项目的名称。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-109">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="c5fa7-110">键入名称 `GetPropertiesSample` 。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-110">Type the name `GetPropertiesSample`.</span></span>  
  
5.  <span data-ttu-id="c5fa7-111">在 "**位置**" 框中，输入要保存项目的路径，或单击 "**浏览**" 导航到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-111">In the **Location** box, enter the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="c5fa7-112">项目的折叠视图以解决方案资源管理器显示。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-112">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
     <span data-ttu-id="c5fa7-113">在解决方案资源管理器中，展开该项目节点。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-113">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="c5fa7-114">已将默认名称) 为 Program.cs (Module1 的文件 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="c5fa7-114">A file with the default name of Program.cs (Module1.vb for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fa7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5fa7-115">See Also</span></span>  
 <span data-ttu-id="c5fa7-116">[第2课：添加 Web 引用](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c5fa7-116">[Lesson 2: Adding a Web Reference](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span></span>  
 [<span data-ttu-id="c5fa7-117">使用 Visual Basic 或 Visual C&#35; &#40;SSRS 教程访问报表服务器 Web 服务&#41;</span><span class="sxs-lookup"><span data-stu-id="c5fa7-117">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
