---
title: 启动 SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8fc9de4884da9a4c372eecdeb6fde12cf3c507e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682628"
---
# <a name="start-sql-server-management-studio"></a><span data-ttu-id="3c832-102">启动 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c832-102">Start SQL Server Management Studio</span></span>
  <span data-ttu-id="3c832-103">开始本教程之前，让我们先来了解一下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c832-103">To begin this tutorial, let's take a look at [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="opening-sql-server-management-studio"></a><span data-ttu-id="3c832-104">打开 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c832-104">Opening SQL Server Management Studio</span></span>  
  
#### <a name="to-open-sql-server-management-studio"></a><span data-ttu-id="3c832-105">打开 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c832-105">To open SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="3c832-106">在 "**开始**" 菜单上，指向 "**所有程序**"，指向 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] ""，然后单击 " **SQL Server Management Studio**"。</span><span class="sxs-lookup"><span data-stu-id="3c832-106">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c832-107">默认情况下不会安装 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c832-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is not installed by default.</span></span> <span data-ttu-id="3c832-108">如果 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 不可用，则运行安装程序安装此程序。</span><span class="sxs-lookup"><span data-stu-id="3c832-108">If [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is unavailable, install it by running Setup.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="3c832-109">不可用于 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c832-109">is not available with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="3c832-110">可以从[Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=14630)免费下载 Express，但其用户界面不同于本教程中所述的用户界面。</span><span class="sxs-lookup"><span data-stu-id="3c832-110">Express is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630), but has a different user interface than is described in this tutorial.</span></span>  
  
2.  <span data-ttu-id="3c832-111">在“连接到服务器”对话框中，确认默认设置，再单击“连接”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="3c832-111">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span> <span data-ttu-id="3c832-112">若要进行连接，"**服务器名称**" 框必须包含安装的计算机的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3c832-112">To connect, the **Server name** box must contain the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="3c832-113">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是命名实例，则 "**服务器名称**" 框还应包含格式为 \<*computer_name*> \\ < *instance_name*> 的实例名称。</span><span class="sxs-lookup"><span data-stu-id="3c832-113">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is a named instance, the **Server name** box should also contain the instance name in the format \<*computer_name*>\\<*instance_name*>.</span></span>  
  
## <a name="management-studio-components"></a><span data-ttu-id="3c832-114">Management Studio 组件</span><span class="sxs-lookup"><span data-stu-id="3c832-114">Management Studio Components</span></span>  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="3c832-115">在专用于特定信息类型的窗口中显示信息。</span><span class="sxs-lookup"><span data-stu-id="3c832-115">presents information in windows dedicated to specific types of information.</span></span> <span data-ttu-id="3c832-116">数据库信息显示在对象资源管理器和文档窗口中。</span><span class="sxs-lookup"><span data-stu-id="3c832-116">Database information is shown in Object Explorer and document windows.</span></span>  
  
-   <span data-ttu-id="3c832-117">对象资源管理器是服务器中所有数据库对象的树视图。</span><span class="sxs-lookup"><span data-stu-id="3c832-117">Object Explorer is a tree view of all the database objects in a server.</span></span> <span data-ttu-id="3c832-118">此树视图可以包括 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的数据库。</span><span class="sxs-lookup"><span data-stu-id="3c832-118">This can include the databases of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3c832-119">对象资源管理器包括与其连接的所有服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="3c832-119">Object Explorer includes information for all servers to which it is connected.</span></span> <span data-ttu-id="3c832-120">打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]时，系统会提示您将对象资源管理器连接到上次使用的设置。</span><span class="sxs-lookup"><span data-stu-id="3c832-120">When you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you are prompted to connect Object Explorer to the settings that were last used.</span></span> <span data-ttu-id="3c832-121">您可以在“已注册的服务器”组件中双击任意服务器进行连接，但无需注册要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="3c832-121">You can double-click any server in the Registered Servers component to connect to it, but you do not have to register a server to connect.</span></span>  
  
-   <span data-ttu-id="3c832-122">文档窗口是 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的最大部分。</span><span class="sxs-lookup"><span data-stu-id="3c832-122">The document window is the largest portion of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="3c832-123">文档窗口可能包含查询编辑器和浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="3c832-123">The document windows can contain query editors and browser windows.</span></span> <span data-ttu-id="3c832-124">默认情况下，将显示已与当前计算机上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例连接的“摘要”页。</span><span class="sxs-lookup"><span data-stu-id="3c832-124">By default, the Summary page is displayed, connected to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the current computer.</span></span>  
  
## <a name="showing-additional-windows"></a><span data-ttu-id="3c832-125">显示其他窗口</span><span class="sxs-lookup"><span data-stu-id="3c832-125">Showing Additional Windows</span></span>  
  
#### <a name="to-show-the-registered-servers-window"></a><span data-ttu-id="3c832-126">显示“已注册的服务器”窗口</span><span class="sxs-lookup"><span data-stu-id="3c832-126">To show the Registered Servers window</span></span>  
  
1.  <span data-ttu-id="3c832-127">在“视图”菜单上，单击“已注册的服务器”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="3c832-127">On the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="3c832-128">“已注册的服务器”窗口将显示在对象资源管理器的上面。</span><span class="sxs-lookup"><span data-stu-id="3c832-128">The Registered Servers window appears above Object Explorer.</span></span> <span data-ttu-id="3c832-129">“已注册的服务器”窗口列出的是经常管理的服务器。</span><span class="sxs-lookup"><span data-stu-id="3c832-129">Registered Servers lists servers which you manage frequently.</span></span> <span data-ttu-id="3c832-130">可以在此列表中添加和删除服务器。</span><span class="sxs-lookup"><span data-stu-id="3c832-130">You can add and remove servers from this list.</span></span> <span data-ttu-id="3c832-131">列出的服务器中仅包含运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3c832-131">The only servers listed are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the computer where you are running [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="3c832-132">如果服务器未显示，请在 "已注册的服务器" 中右键单击**数据库引擎**，然后单击 "**更新本地服务器注册**"。</span><span class="sxs-lookup"><span data-stu-id="3c832-132">If your server does not appear, in Registered Servers, right-click **Database Engine**, and then click **Update Local Server Registration**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3c832-133">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="3c832-133">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3c832-134">与已注册的服务器和对象资源管理器连接</span><span class="sxs-lookup"><span data-stu-id="3c832-134">Connect with Registered Servers and Object Explorer</span></span>](../object/object-explorer.md)  
  
  
