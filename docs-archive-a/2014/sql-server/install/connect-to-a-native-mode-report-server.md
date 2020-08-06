---
title: 连接到本机模式报表服务器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579978"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="3bf5a-102">连接到本机模式的报表服务器</span><span class="sxs-lookup"><span data-stu-id="3bf5a-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="3bf5a-103">使用此对话框连接到本地或远程 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="3bf5a-104">不能使用此工具连接到早期版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="3bf5a-105">一次仅能连接到一个实例。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="3bf5a-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bf5a-107">不使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器来配置和管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="3bf5a-108">使用 SharePoint 管理中心和 PowerShell 脚本在 SharePoint 模式中配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="3bf5a-109">有关详细信息，请参阅[Install Reporting Services Sharepoint Mode For sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="3bf5a-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="3bf5a-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]安装 Configuration Manager ( # A0) 的权限级别为 "highestAvailable"。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="3bf5a-111">此行为是设计使然。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-111">This behavior is by design.</span></span> <span data-ttu-id="3bf5a-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器要求与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API 进行通信。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="3bf5a-113">一些 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通信要求更高级别的权限或管理权限。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="3bf5a-114">若要连接到本地报表服务器实例，请使用默认值并单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="3bf5a-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器提供了本地服务器名称并可检测到默认实例。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="3bf5a-116">在大多数情况下，您可以单击 **“连接”** 而不必更改值。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="3bf5a-117">如果安装了多个实例，则必须选择要使用的实例。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="3bf5a-118">若要连接到远程报表服务器实例，请键入服务器名称，单击 **“查找”**，再选择该实例，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="3bf5a-119">若要打开此对话框，请启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="3bf5a-120">启动此工具后，该对话框会立即显示出来。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="3bf5a-121">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3bf5a-122">选项</span><span class="sxs-lookup"><span data-stu-id="3bf5a-122">Options</span></span>  
 <span data-ttu-id="3bf5a-123">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="3bf5a-123">**Server Name**</span></span>  
 <span data-ttu-id="3bf5a-124">输入安装了 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的计算机的网络名称。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="3bf5a-125">只键入计算机名称；不包括前缀或斜杠。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="3bf5a-126">**查找**</span><span class="sxs-lookup"><span data-stu-id="3bf5a-126">**Find**</span></span>  
 <span data-ttu-id="3bf5a-127">查找 **“服务器名称”** 中指定的计算机。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="3bf5a-128">**报表服务器实例**</span><span class="sxs-lookup"><span data-stu-id="3bf5a-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="3bf5a-129">如果安装了多个报表服务器实例，则选择哪个实例进行连接。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="3bf5a-130">只有有效的实例可供选择。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="3bf5a-131">如果将旧版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并行运行，则那些实例将不会显示在此列表中。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="3bf5a-132">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="3bf5a-132">**Connect**</span></span>  
 <span data-ttu-id="3bf5a-133">连接到指定的服务器和实例。</span><span class="sxs-lookup"><span data-stu-id="3bf5a-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf5a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bf5a-134">See Also</span></span>  
 [<span data-ttu-id="3bf5a-135">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="3bf5a-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
