---
title: 如何：运行升级顾问分析向导 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590541"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="7f4ff-102">如何运行升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="7f4ff-102">How to: Run the Upgrade Advisor Analysis Wizard</span></span>
  <span data-ttu-id="7f4ff-103">可以从升级顾问起始页启动升级顾问分析向导。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-103">You start the Upgrade Advisor Analysis Wizard from the Upgrade Advisor start page.</span></span> <span data-ttu-id="7f4ff-104">本主题介绍了如何运行升级顾问分析向导。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-104">This topic describes how to run the Upgrade Advisor Analysis Wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f4ff-105">运行升级顾问分析向导时，升级顾问会将报表保存在默认报表文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-105">When you run the Upgrade Advisor Analysis Wizard, Upgrade Advisor saves the reports in the default report folder.</span></span> <span data-ttu-id="7f4ff-106">但是，报表查看器只显示最近保存的五个报表。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-106">However, the report viewer displays only the five latest saved reports.</span></span> <span data-ttu-id="7f4ff-107">报表的默认位置为 "我的文档" \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级 advisor\110\reports。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-107">The default location for the reports is My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.</span></span>  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="7f4ff-108">运行升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="7f4ff-108">To run the Upgrade Advisor Analysis Wizard</span></span>  
  
1.  <span data-ttu-id="7f4ff-109">在升级顾问起始页上，单击 "**启动升级顾问分析向导**"。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Analysis Wizard**.</span></span>  
  
2.  <span data-ttu-id="7f4ff-110">在 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件**" 页上，在 "**服务器名称**" 框中输入要扫描的服务器的名称，然后单击 "**检测\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-110">On the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components** page, enter the name of the server to scan in the **Server name** box, and then click **Detect**.</span></span> <span data-ttu-id="7f4ff-111">输入服务器名称时应遵守以下原则：</span><span class="sxs-lookup"><span data-stu-id="7f4ff-111">Use the following guidelines for the server name:</span></span>  
  
    -   <span data-ttu-id="7f4ff-112">若要扫描非群集实例，请输入计算机名。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-112">To scan nonclustered instances, enter the computer name.</span></span>  
  
    -   <span data-ttu-id="7f4ff-113">若要扫描群集实例，请输入虚拟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名称。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-113">To scan clustered instances, enter the virtual [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name.</span></span>  
  
    -   <span data-ttu-id="7f4ff-114">若要扫描安装在群集节点上的非群集组件，请输入节点名称。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-114">To scan nonclustered components that are installed on a node of a cluster, enter the node name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="7f4ff-115">升级顾问不支持到未设置为使用标准端口 (1433) 进行客户端连接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-115">Upgrade Advisor does not support connecting to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is not set to use the standard port (1433) for client connections.</span></span> <span data-ttu-id="7f4ff-116">如果要连接到不使用标准端口 (1433) 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请使用 IP 地址和端口创建一个别名。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-116">If you want to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that does not use the standard port (1433), create an alias using the IP address and the port.</span></span> <span data-ttu-id="7f4ff-117">有关为实例配置客户端协议和创建别名的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-117">For more information about configuring client protocols and creating an alias for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
    >   
    >  <span data-ttu-id="7f4ff-118">如果在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行升级顾问的计算机上未安装，请单击 "**开始**"，然后单击 "运行" `cliconfg` 。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-118">If you do not have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer on which you are running Upgrade Advisor, click **Start**, and then run  `cliconfg`.</span></span> <span data-ttu-id="7f4ff-119">这将打开 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络实用工具\*\*" 对话框。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-119">This opens the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility** dialog box.</span></span> <span data-ttu-id="7f4ff-120">使用 "**别名**" 选项卡创建别名。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-120">Use the **Alias** tab to create the alias.</span></span>  
  
3.  <span data-ttu-id="7f4ff-121">查看检测到的组件列表，根据需要修改所选内容，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-121">Review the list of components detected, modify the selections as necessary, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7f4ff-122">在 "**连接参数**" 页上，选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要扫描的实例，选择身份验证方法，并在必要时输入用户名和密码信息，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-122">On the **Connection Parameters** page, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you want to scan, select the authentication method and, if necessary, enter user name and password information, and then click **Next**.</span></span>  
  
     <span data-ttu-id="7f4ff-123">默认实例名为 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-123">The default instance name is MSSQLSERVER.</span></span>  
  
5.  <span data-ttu-id="7f4ff-124">对于选定的组件，请输入所需的信息。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-124">For selected components, enter the requested information.</span></span> <span data-ttu-id="7f4ff-125">有关各个对话框的详细信息，请参阅[升级顾问用户界面参考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-125">For more information about individual dialog boxes, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
6.  <span data-ttu-id="7f4ff-126">在 "**确认升级顾问设置**" 页上，查看您输入的信息。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-126">On the **Confirm Upgrade Advisor Setting** page, review the information that you entered.</span></span> <span data-ttu-id="7f4ff-127">如果要提交升级报表，可以选择 "\*\*将报表发送到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] \*\* "。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-127">You can select **Send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)]** if you want to submit your upgrade report.</span></span> <span data-ttu-id="7f4ff-128">还可以查看隐私策略。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-128">You can also review the privacy policy.</span></span>  
  
7.  <span data-ttu-id="7f4ff-129">单击 "**运行**" 以分析的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-129">Click **Run** to analyze the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
8.  <span data-ttu-id="7f4ff-130">分析完成后，单击 "**启动报告**" 以查看检测到的升级问题。</span><span class="sxs-lookup"><span data-stu-id="7f4ff-130">When the analysis is finished, click **Launch Report** to view the detected upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4ff-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f4ff-131">See Also</span></span>  
 <span data-ttu-id="7f4ff-132">[如何启动升级顾问](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="7f4ff-132">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="7f4ff-133">[&#40;用户界面运行升级顾问&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="7f4ff-133">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 [<span data-ttu-id="7f4ff-134">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="7f4ff-134">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
