---
title: 将 SQL Server 实例设置为自动启动 (SQL Server 配置管理器) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2fc21bd881c1588da47710c6d8437e31d3df2ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692530"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a><span data-ttu-id="c7999-102">将 SQL Server 实例设置为自动启动（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="c7999-102">Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="c7999-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中将 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例设置为自动启动。</span><span class="sxs-lookup"><span data-stu-id="c7999-103">This topic describes how to set an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to start automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="c7999-104">在安装过程中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通常配置为自动启动。</span><span class="sxs-lookup"><span data-stu-id="c7999-104">During setup, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is normally configured to start automatically.</span></span> <span data-ttu-id="c7999-105">如果没有这样做，则可以随时更改该设置。</span><span class="sxs-lookup"><span data-stu-id="c7999-105">If this was not done, you can change that setting at any time.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c7999-106">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="c7999-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a><span data-ttu-id="c7999-107">将 SQL Server 实例设置为自动启动</span><span class="sxs-lookup"><span data-stu-id="c7999-107">To set an instance of SQL Server to start automatically</span></span>  
  
1.  <span data-ttu-id="c7999-108">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="c7999-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7999-109">因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台程序的一个管理单元而不是单独的程序，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器在新版本的 Windows 中不显示为一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="c7999-109">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="c7999-110">**Windows 10**：</span><span class="sxs-lookup"><span data-stu-id="c7999-110">**Windows 10**:</span></span>  
    >          <span data-ttu-id="c7999-111">若要打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，请在 "**开始" 页**上，键入) 的 sqlservermanager12.msc ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c7999-111">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="c7999-112">对于早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请将 12 替换为较小的数字。</span><span class="sxs-lookup"><span data-stu-id="c7999-112">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="c7999-113">单击 SQLServerManager12.msc 可打开“配置管理器”。</span><span class="sxs-lookup"><span data-stu-id="c7999-113">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="c7999-114">若要将 Configuration Manager 固定到 "起始页" 或 "任务栏"，请右键单击 "Sqlservermanager12.msc"，然后单击 "**打开文件位置**"。</span><span class="sxs-lookup"><span data-stu-id="c7999-114">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="c7999-115">在 Windows 文件资源管理器中，右键单击 "Sqlservermanager12.msc"，然后单击 "**固定到\*\*\*\*任务栏**"。</span><span class="sxs-lookup"><span data-stu-id="c7999-115">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="c7999-116">**Windows 8**：</span><span class="sxs-lookup"><span data-stu-id="c7999-116">**Windows 8**:</span></span>  
    >          <span data-ttu-id="c7999-117">若要打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，请在 "**搜索**" 超级按钮中的 "**应用**" 下，键入**sqlservermanager version>.msc （ \<version> **如 `SQLServerManager12.msc` ），然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="c7999-117">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="c7999-118">在 **“SQL Server 配置管理器”** 中，展开 **“服务”** ，再单击 **SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="c7999-118">In **SQL Server Configuration Manager**, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="c7999-119">在详细信息窗格中，右键单击要自动启动的实例的名称，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="c7999-119">In the details pane, right-click the name of the instance you want to start automatically, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="c7999-120">在“SQL Server \<***instancename***> 属性”对话框中，将“启动模式”设置为“自动”  。</span><span class="sxs-lookup"><span data-stu-id="c7999-120">In the **SQL Server \<***instancename***> Properties** dialog box, set **Start Mode** to **Automatic**.</span></span>  
  
5.  <span data-ttu-id="c7999-121">单击 **“确定”** ，然后关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="c7999-121">Click **OK**, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7999-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7999-122">See Also</span></span>  
 <span data-ttu-id="c7999-123">[防止 SQL Server 实例自动启动（SQL Server 配置管理器）](scm-services-prevent-automatic-startup-of-an-instance.md) </span><span class="sxs-lookup"><span data-stu-id="c7999-123">[Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span></span>  
 <span data-ttu-id="c7999-124">[连接到其他计算机（SQL Server 配置管理器）](scm-services-connect-to-another-computer.md) </span><span class="sxs-lookup"><span data-stu-id="c7999-124">[Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](scm-services-connect-to-another-computer.md) </span></span>  
 [<span data-ttu-id="c7999-125">在 SQL Server 工具中将 WMI 配置为显示服务器状态</span><span class="sxs-lookup"><span data-stu-id="c7999-125">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
