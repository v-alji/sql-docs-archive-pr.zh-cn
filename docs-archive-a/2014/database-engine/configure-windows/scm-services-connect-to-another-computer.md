---
title: 连接到其他计算机（SQL Server 配置管理器）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591586"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a><span data-ttu-id="b7984-102">连接到其他计算机（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="b7984-102">Connect to Another Computer (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="b7984-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中连接到其他计算机。</span><span class="sxs-lookup"><span data-stu-id="b7984-103">This topic describes how to connect to another computer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b7984-104">按照第一个过程执行操作，打开 Windows 的“计算机管理” [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台 (mmc)，连接到该计算机，然后展开“服务和应用程序”树。</span><span class="sxs-lookup"><span data-stu-id="b7984-104">Follow the first procedure to open the Windows Computer Management [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc), connect to the computer, and expand the Services and Applications tree.</span></span> <span data-ttu-id="b7984-105">遵循第二个过程，创建一个包含到远程计算机中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的链接的文件。</span><span class="sxs-lookup"><span data-stu-id="b7984-105">Follow the second procedure to create a file with a link to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7984-106">远程连接时，某些程序无法由配置管理器执行。</span><span class="sxs-lookup"><span data-stu-id="b7984-106">Some actions cannot be performed by Configuration Manager when connecting remotely.</span></span>  
  
 <span data-ttu-id="b7984-107">若要在其他计算机上启动、停止、暂停或恢复服务，也可以连接到安装有 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的服务器，右键单击此服务器或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，然后单击需要的操作。</span><span class="sxs-lookup"><span data-stu-id="b7984-107">To start, stop, pause, or resume services on another computer, you can also connect to the server with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the server or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and then click the desired action.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a><span data-ttu-id="b7984-108">使用 Windows 的“计算机管理”连接到另一台计算机</span><span class="sxs-lookup"><span data-stu-id="b7984-108">To connect to another computer with Windows Computer Management</span></span>  
  
1.  <span data-ttu-id="b7984-109">在“开始” \*\*\*\* 菜单上，右键单击“我的电脑” \*\*\*\*，再单击“管理” \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b7984-109">On the **Start** menu, right-click **My Computer**, and then click **Manage.**</span></span>  
  
2.  <span data-ttu-id="b7984-110">在“计算机管理” \*\*\*\* 中，右键单击“计算机管理（本地）” \*\*\*\*，再单击“连接到另一台计算机” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7984-110">In **Computer Management**, right-click **Computer Management (Local)**, and then click **Connect to another computer**.</span></span>  
  
3.  <span data-ttu-id="b7984-111">在 **“选择计算机”** 对话框中的 **“另一台计算机”** 文本框中，键入想要管理的计算机名，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b7984-111">In the **Select Computer** dialog box, in the **Another computer** text box, type the name of the computer you want to manage, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b7984-112">“计算机管理”将显示运行在远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="b7984-112">Computer Management displays the services running on the remote computer.</span></span> <span data-ttu-id="b7984-113">顶级节点更改为“计算机管理 \<*remotecomputer*>”。</span><span class="sxs-lookup"><span data-stu-id="b7984-113">The top-level node changes to **Computer Management** \<*remotecomputer*>.</span></span>  
  
4.  <span data-ttu-id="b7984-114">在控制台树中，依次展开 **“服务和应用程序”** 、 **“SQL Server 配置管理器”** 来管理远程计算机的服务。</span><span class="sxs-lookup"><span data-stu-id="b7984-114">In the console tree, expand **Services and Applications**, and then expand **SQL Server Configuration Manager** to manage the remote computer's services.</span></span>  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a><span data-ttu-id="b7984-115">将链接保存到其他计算机的 SQL Server 配置管理器中</span><span class="sxs-lookup"><span data-stu-id="b7984-115">To save a link to SQL Server Configuration Manager for another computer</span></span>  
  
1.  <span data-ttu-id="b7984-116">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="b7984-116">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="b7984-117">在 "**打开**" 框中，键入 `mmc -a` 以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 在作者模式下打开管理控制台。</span><span class="sxs-lookup"><span data-stu-id="b7984-117">In the **Open** box, type `mmc -a` to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console in author mode.</span></span>  
  
3.  <span data-ttu-id="b7984-118">在“文件”  菜单上，单击“添加/删除管理单元” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-118">On the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
4.  <span data-ttu-id="b7984-119">在“添加/删除管理单元”  窗口中，单击“添加” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-119">In the **Add/Remove Snap-in** window, click **Add**.</span></span>  
  
5.  <span data-ttu-id="b7984-120">在“添加独立管理单元”  窗口中，单击“计算机管理”  ，再单击“添加” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-120">In the **Add Standalone Snap-in** window, click **Computer Management** and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="b7984-121">在 **“计算机管理”** 窗口中，单击 **“其他计算机”** ，键入要管理的远程计算机的名称，再单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="b7984-121">In the **Computer Management** window, click **Another computer**, type the name of the remote computer you wish to manage, and then click **Finish**.</span></span>  
  
7.  <span data-ttu-id="b7984-122">在“添加单独管理单元”  窗口中，单击“关闭” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-122">In the **Add Standalone Snap-in** window, click **Close**.</span></span>  
  
8.  <span data-ttu-id="b7984-123">在“添加/删除管理单元”  窗口中，单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-123">In the **Add/Remove Snap-in** window, click **OK**.</span></span>  
  
9. <span data-ttu-id="b7984-124">展开 "**计算机管理" (***\<computer name>***) **，以及 "**服务和应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="b7984-124">Expand **Computer Management (***\<computer name>***)**, and **Services and Applications**.</span></span>  
  
10. <span data-ttu-id="b7984-125">右键单击“SQL Server 配置管理器” ，再单击“从此处新建窗口” 。</span><span class="sxs-lookup"><span data-stu-id="b7984-125">Right-click **SQL Server Configuration Manager**, and then click **New Window from here**.</span></span>  
  
11. <span data-ttu-id="b7984-126">在“窗口”菜单上，单击“控制台根节点”，切换回第一个窗口，并删除该窗口 。</span><span class="sxs-lookup"><span data-stu-id="b7984-126">On the **Window** menu, click **Console Root**, to switch back to the first window, and delete the window.</span></span>  
  
12. <span data-ttu-id="b7984-127">在 "**文件**" 菜单上，单击 "**另存为**"，并将文件保存在所需的文件夹中，并将文件扩展名保存到相应的文件夹中 `.msc` 。</span><span class="sxs-lookup"><span data-stu-id="b7984-127">On the **File** menu, click **Save As**, and save the file in the desired folder, with an appropriate name with the `.msc` file extension.</span></span> <span data-ttu-id="b7984-128">关闭 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台。</span><span class="sxs-lookup"><span data-stu-id="b7984-128">Close the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span>  
  
13. <span data-ttu-id="b7984-129">若要打开目标计算机中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器，请双击此文件。</span><span class="sxs-lookup"><span data-stu-id="b7984-129">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on the target computer, double-click the file.</span></span> <span data-ttu-id="b7984-130">如果需要，则在桌面上或 **“开始”** 菜单中保存到此文件的链接。</span><span class="sxs-lookup"><span data-stu-id="b7984-130">If desired, save a link to the file on the desktop or in the **Start** menu.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b7984-131">当使用远程计算机中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器时，计算机名称不是显而易见的，因此可能会错误地停止或配置不正确的计算机。</span><span class="sxs-lookup"><span data-stu-id="b7984-131">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer, the computer name is not obvious and it is possible to mistakenly stop or configure the wrong computer.</span></span> <span data-ttu-id="b7984-132">在 **“服务”** 选项卡上，选中 **“主机名”** 复选框以在修改服务前确认计算机名称。</span><span class="sxs-lookup"><span data-stu-id="b7984-132">On the **Service** tab, check the **Host Name** box to confirm the computer name before modifying a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7984-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7984-133">See Also</span></span>  
 [<span data-ttu-id="b7984-134">在 SQL Server 工具中将 WMI 配置为显示服务器状态</span><span class="sxs-lookup"><span data-stu-id="b7984-134">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
