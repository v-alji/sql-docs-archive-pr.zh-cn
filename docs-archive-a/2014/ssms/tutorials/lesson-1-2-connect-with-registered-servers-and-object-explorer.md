---
title: 连接已注册的服务器和对象资源管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682621"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a><span data-ttu-id="da025-102">与已注册的服务器和对象资源管理器连接</span><span class="sxs-lookup"><span data-stu-id="da025-102">Connect with Registered Servers and Object Explorer</span></span>
  <span data-ttu-id="da025-103">本教程演示如何使用已注册的服务器和对象资源管理器。</span><span class="sxs-lookup"><span data-stu-id="da025-103">This tutorial demonstrates the use of Registered Servers and Object Explorer.</span></span>  
  
 <span data-ttu-id="da025-104">本教程使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="da025-104">This tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="da025-105">为了帮助增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="da025-105">To help enhance security, by default, the sample databases are not installed.</span></span> <span data-ttu-id="da025-106">有关详细信息，请参阅 [安装 SQL Server 示例和示例数据库](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="da025-106">For more information, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="connecting-to-servers"></a><span data-ttu-id="da025-107">连接到服务器</span><span class="sxs-lookup"><span data-stu-id="da025-107">Connecting to Servers</span></span>  
 <span data-ttu-id="da025-108">已注册的服务器组件的工具栏包含用于 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的按钮。</span><span class="sxs-lookup"><span data-stu-id="da025-108">The toolbar of the Registered Servers component has buttons for the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="da025-109">可以注册上述的一个或多个服务器类型以便于管理。</span><span class="sxs-lookup"><span data-stu-id="da025-109">You can register one or more of these server types for convenient management.</span></span> <span data-ttu-id="da025-110">请尝试以下练习来注册 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="da025-110">Try the following exercise to register the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
#### <a name="to-register-the-database"></a><span data-ttu-id="da025-111">注册数据库</span><span class="sxs-lookup"><span data-stu-id="da025-111">To register the database</span></span>  
  
1.  <span data-ttu-id="da025-112">在“已注册的服务器”工具栏中，如有必要，请单击“数据库引擎”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-112">On the Registered Servers toolbar, click **Database Engine** if you have to.</span></span> <span data-ttu-id="da025-113">（该选项可能已选中。）</span><span class="sxs-lookup"><span data-stu-id="da025-113">(It may already be selected.)</span></span>  
  
2.  <span data-ttu-id="da025-114">展开“数据库引擎”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-114">Expand **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="da025-115">右键单击“本地服务器组”\*\*\*\*，然后单击“新建服务器注册”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-115">Right-click **Local Server Groups**, and then click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="da025-116">在“新建服务器注册”\*\*\*\* 对话框中的“服务器名称”\*\*\*\* 文本框中，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="da025-116">In the **New Server Registration** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="da025-117">在“已注册的服务器名称”\*\*\*\* 框中，键入 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da025-117">In the **Registered server name** box, type [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
6.  <span data-ttu-id="da025-118">在 "**连接属性**" 选项卡上的 "**连接到数据库**" 列表中，选择 **\<Browse server...>** 。</span><span class="sxs-lookup"><span data-stu-id="da025-118">On the **Connection Properties** tab, in the **Connect to database** list, select **\<Browse server...>**.</span></span>  
  
7.  <span data-ttu-id="da025-119">在“查找数据库”\*\*\*\* 对话框中，单击“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-119">In the **Browse for Databases** dialog box, click **Yes**.</span></span>  
  
8.  <span data-ttu-id="da025-120">在“查找服务器上的数据库”\*\*\*\* 对话框中，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-120">In the **Browse Server for Database** dialog box, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
9. <span data-ttu-id="da025-121">要验证服务器已正确注册，请单击“测试”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-121">To verify that the server has been registered correctly, click **Test**.</span></span>  
  
10. <span data-ttu-id="da025-122">在“新建服务器注册”\*\*\*\* 对话框中，单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-122">In the **New Server Registration** dialog box, click **Save**.</span></span>  
  
## <a name="connecting-with-object-explorer"></a><span data-ttu-id="da025-123">与对象资源管理器连接</span><span class="sxs-lookup"><span data-stu-id="da025-123">Connecting with Object Explorer</span></span>  
 <span data-ttu-id="da025-124">与已注册的服务器类似，对象资源管理器也可以连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da025-124">Like Registered Servers, Object Explorer can connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
#### <a name="to-connect-with-object-explorer"></a><span data-ttu-id="da025-125">与对象资源管理器连接</span><span class="sxs-lookup"><span data-stu-id="da025-125">To connect with Object Explorer</span></span>  
  
1.  <span data-ttu-id="da025-126">在对象资源管理器的工具栏中，单击“连接”\*\*\*\* 显示可用连接类型列表，再选择“数据库引擎”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-126">On the toolbar of Object Explorer, click **Connect** for a list of possible connection types, and then select **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="da025-127">在“连接到服务器”\*\*\*\* 对话框中的“服务器名称”\*\*\*\* 文本框中，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="da025-127">In the **Connect to Server** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="da025-128">单击“选项”\*\*\*\*，然后浏览各选项。</span><span class="sxs-lookup"><span data-stu-id="da025-128">Click **Options** and explore the choices.</span></span>  
  
4.  <span data-ttu-id="da025-129">若要连接到服务器，请单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da025-129">To connect to the server, click **Connect**.</span></span> <span data-ttu-id="da025-130">如果已经连接，则此操作会使您直接返回到对象资源管理器，并将该服务器设置为焦点。</span><span class="sxs-lookup"><span data-stu-id="da025-130">If you are already connected, this action just returns you to Object Explorer and sets the focus on that server.</span></span>  
  
     <span data-ttu-id="da025-131">利用对象资源管理器，可以管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、复制和数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="da025-131">With Object Explorer you can administer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Security, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Replication, and Database Mail.</span></span> <span data-ttu-id="da025-132">对象资源管理器只能管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssIS](../../includes/ssis-md.md)]的部分功能。</span><span class="sxs-lookup"><span data-stu-id="da025-132">Object Explorer can only manage some of the features of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssIS](../../includes/ssis-md.md)].</span></span> <span data-ttu-id="da025-133">上述每个组件都有其他专用工具。</span><span class="sxs-lookup"><span data-stu-id="da025-133">Each of those components has additional specialized tools.</span></span>  
  
5.  <span data-ttu-id="da025-134">在对象资源管理器中，展开“数据库”\*\*\*\* 文件夹并且选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da025-134">In Object Explorer, expand the **Databases** folder and select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
     <span data-ttu-id="da025-135">请注意，[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将系统数据库放在一个单独的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="da025-135">Notice that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] presents the system databases in a separate folder.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="da025-136">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="da025-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="da025-137">更改环境布局</span><span class="sxs-lookup"><span data-stu-id="da025-137">Change the Environment Layout</span></span>](lesson-1-3-change-the-environment-layout.md)  
  
  
