---
title: 修改控制器和客户端服务帐户 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a054749f1d53323bde5c9d05a1e7632b1dda85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690984"
---
# <a name="modify-the-controller-and-client-services-accounts"></a><span data-ttu-id="8dc28-102">修改控制器和客户端服务帐户</span><span class="sxs-lookup"><span data-stu-id="8dc28-102">Modify the Controller and Client Services Accounts</span></span>
  <span data-ttu-id="8dc28-103">在本主题中，您将了解如何修改 Distributed Replay 控制器和客户端服务帐户，然后重新应用访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="8dc28-103">In this topic, you will learn how to modify the Distributed Replay controller and client service accounts, and then reapply the access control lists (ACLs).</span></span>  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a><span data-ttu-id="8dc28-104">使用“计算机管理”启动或停止 Distributed Replay 服务</span><span class="sxs-lookup"><span data-stu-id="8dc28-104">To start or stop the Distributed Replay services using Computer Management</span></span>  
  
1.  <span data-ttu-id="8dc28-105">在安装有 Distributed Replay 服务的计算机上，在命令提示符下键入 `dcomcnfg`。</span><span class="sxs-lookup"><span data-stu-id="8dc28-105">On the computer on which the Distributed Replay services are installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
2.  <span data-ttu-id="8dc28-106">双击 "**服务**"，向下滚动并右键单击\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name> **，然后单击 "**启动**" 或 "**停止\*\*"。</span><span class="sxs-lookup"><span data-stu-id="8dc28-106">Double-click **Services**, scroll down and right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name>**, and then click **Start** or **Stop**.</span></span>  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a><span data-ttu-id="8dc28-107">修改 Distributed Replay 控制器服务</span><span class="sxs-lookup"><span data-stu-id="8dc28-107">To modify the Distributed Replay controller service</span></span>  
  
1.  <span data-ttu-id="8dc28-108">在控制器计算机上，停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 控制器服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-108">On the controller computer, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="8dc28-109">在“服务”  下，右键单击  “[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播控制器”，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="8dc28-109">Under **Services**, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**, and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="8dc28-110">在 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 控制器属性”** 窗口中的 **“登录”** 选项卡上，选择 **“本帐户”** ，键入或单击 **“浏览”** 以输入新的登录帐户，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8dc28-110">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8dc28-111">**重要说明**：配置 Distributed Replay 控制器时，可以指定一个或多个用于运行 Distributed Replay 客户端服务的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8dc28-111">**Important**: When you configure Distributed Replay Controller, you can specify one or more user accounts that will be used to run the Distributed Replay Client services.</span></span> <span data-ttu-id="8dc28-112">下面是支持的帐户的列表：</span><span class="sxs-lookup"><span data-stu-id="8dc28-112">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="8dc28-113">域用户帐户</span><span class="sxs-lookup"><span data-stu-id="8dc28-113">Domain user account</span></span>  
  
    -   <span data-ttu-id="8dc28-114">用户创建的本地用户帐户</span><span class="sxs-lookup"><span data-stu-id="8dc28-114">User created local user account</span></span>  
  
    -   <span data-ttu-id="8dc28-115">管理员</span><span class="sxs-lookup"><span data-stu-id="8dc28-115">Administrator</span></span>  
  
    -   <span data-ttu-id="8dc28-116">虚拟帐户和 MSA（托管服务帐户）</span><span class="sxs-lookup"><span data-stu-id="8dc28-116">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="8dc28-117">Network Services、Local Services 和 System</span><span class="sxs-lookup"><span data-stu-id="8dc28-117">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="8dc28-118">不接受组帐户（本地或域）和其他内置帐户（如 Everyone）。</span><span class="sxs-lookup"><span data-stu-id="8dc28-118">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
4.  <span data-ttu-id="8dc28-119">启动 Distributed Replay 控制器服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-119">Start the Distributed Replay controller service.</span></span>  
  
### <a name="to-modify-the-distributed-replay-client-service"></a><span data-ttu-id="8dc28-120">修改 Distributed Replay 客户端服务</span><span class="sxs-lookup"><span data-stu-id="8dc28-120">To modify the Distributed Replay client service</span></span>  
  
1.  <span data-ttu-id="8dc28-121">在修改 Distributed Replay 客户端服务之前，请确保在安装期间指定了您要更改的客户端服务帐户（在控制器计算机上的 CTLRUSERS 参数中）。</span><span class="sxs-lookup"><span data-stu-id="8dc28-121">Before you modify the Distributed Replay client service, make sure the client service account you are changing was specified during setup (in the CTLRUSERS parameter on the controller computer).</span></span> <span data-ttu-id="8dc28-122">如果在安装期间未指定要更改的客户端服务帐户，必须先执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8dc28-122">If the client service account you are changing was not specified during setup, you must perform the following steps first:</span></span>  
  
    1.  <span data-ttu-id="8dc28-123">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 控制器服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
    2.  <span data-ttu-id="8dc28-124">在安装有控制器服务的控制器计算机上，在命令提示符下键入 `dcomcnfg`。</span><span class="sxs-lookup"><span data-stu-id="8dc28-124">On the controller computer on which the controller service is installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
    3.  <span data-ttu-id="8dc28-125">在“组件服务”  窗口中，导航到“控制台根节点 -> 组件服务 -> 计算机 -> 我的电脑 -> DCOM Config ->DReplayController”  。</span><span class="sxs-lookup"><span data-stu-id="8dc28-125">In the **Component Services** window, navigate to **Console Root -> Component Services -> Computers -> My Computer -> DCOM Config ->DReplayController**.</span></span>  
  
    4.  <span data-ttu-id="8dc28-126">右键单击“DReplayController”  ，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="8dc28-126">Right-click **DReplayController**, and then click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="8dc28-127">在 **“DReplayController 属性”** 窗口中的 **“安全性”** 选项卡上，单击 **“启动和激活权限”** 部分的 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="8dc28-127">In the **DReplayController Properties** window, on the **Security** tab, click **Edit** in the **Launch and Activation Permissions** section.</span></span>  
  
    6.  <span data-ttu-id="8dc28-128">为新的客户端服务登录帐户授予 **“本地和远程激活”** 权限，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8dc28-128">Grant the new client service logon account **Local and Remote activation** permissions, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="8dc28-129">单击 **“访问权限”** 部分的 **“编辑”** ，并为新的客户端服务登录帐户授予 **“本地和远程访问”** 权限，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8dc28-129">Click **Edit** in the **Access Permissions** section, and grant the new client service logon account **Local and Remote access** permissions, and then click **OK**.</span></span>  
  
    8.  <span data-ttu-id="8dc28-130">单击 **“确定”** 以关闭 **“DReplayController 属性”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="8dc28-130">Click **OK** to close the **DReplayController Properties** window.</span></span>  
  
    9. <span data-ttu-id="8dc28-131">在控制器计算机上，将更改后的客户端服务登录帐户添加到 **“分布式 COM 用户”** 组中。</span><span class="sxs-lookup"><span data-stu-id="8dc28-131">On the controller computer, add the changed client service logon account to the **Distributed COM Users** group.</span></span>  
  
    10. <span data-ttu-id="8dc28-132">启动 SQL Server 分布式重播控制器服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-132">Start the SQL Server Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="8dc28-133">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 客户端服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-133">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service.</span></span>  
  
3.  <span data-ttu-id="8dc28-134">在 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 客户端属性”** 窗口中的 **“登录”** 选项卡上，选择 **“本帐户”** ，键入或单击 **“浏览”** 以输入新的登录帐户，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8dc28-134">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="8dc28-135">启动 Distributed Replay 客户端服务。</span><span class="sxs-lookup"><span data-stu-id="8dc28-135">Start the Distributed Replay client service.</span></span>  
  
  
