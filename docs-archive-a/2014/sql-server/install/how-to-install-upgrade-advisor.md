---
title: 如何：安装升级顾问 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3ed5b66522126bfabc94bfa8036ec6c31ac04500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590544"
---
# <a name="how-to-install-upgrade-advisor"></a><span data-ttu-id="ea7b6-102">如何安装升级顾问</span><span class="sxs-lookup"><span data-stu-id="ea7b6-102">How to: Install Upgrade Advisor</span></span>
  <span data-ttu-id="ea7b6-103">升级顾问支持对除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之外的所有受支持组件进行远程分析。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-103">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ea7b6-104">如果不打算扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例，则可在能够连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的任何计算机上安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-104">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ea7b6-105">计算机还必须满足升级顾问的前提条件。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-105">The computer must also meet Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="ea7b6-106">如果要扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]实例，则必须在报表服务器上安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="ea7b6-107">有关详细信息，请参阅[安装升级顾问](../../../2014/sql-server/install/installing-upgrade-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-107">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
### <a name="to-install-upgrade-advisor"></a><span data-ttu-id="ea7b6-108">安装升级顾问</span><span class="sxs-lookup"><span data-stu-id="ea7b6-108">To install Upgrade Advisor</span></span>  
  
1.  <span data-ttu-id="ea7b6-109">使用以下方法之一开始安装：</span><span class="sxs-lookup"><span data-stu-id="ea7b6-109">Start the installation using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="ea7b6-110">如果要从网站安装 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ，请单击 "**下载**" 链接，然后单击 "**运行**" 按钮开始安装。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-110">If you are installing from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site, click the **Download** link and then click the **Run** button to start the installation.</span></span>  
  
    -   <span data-ttu-id="ea7b6-111">如果要从产品媒体进行安装，请打开 "已再**发行**" 文件夹，打开 "**升级顾问**" 文件夹，然后双击 " **SQLUA.msi**"。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-111">If you are installing from the product media, open the **redist** folder, open the **Upgrade Advisor** folder, and then double-click **SQLUA.msi**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea7b6-112">升级顾问要求 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-112">Upgrade Advisor requires the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4.</span></span> <span data-ttu-id="ea7b6-113">如果该软件未安装，或者如果安装的是预发行版本，则将出现一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-113">If it is not installed, or if you have a pre-release version, an error message will appear.</span></span> <span data-ttu-id="ea7b6-114">请卸载 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的所有早期版本，然后安装最新版本的 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-114">Uninstall any earlier version of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and then install the latest version of .NET Framework 4.</span></span>  
    >   
    >  <span data-ttu-id="ea7b6-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom 是安装升级顾问的必备组件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，并且不是由升级顾问安装程序安装的。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-115">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="ea7b6-116">安装程序需要 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能包下载和安装 ScriptDom。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-116">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
2.  <span data-ttu-id="ea7b6-117">在 "**欢迎使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升级顾问安装程序**" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-117">On the **Welcome to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor Setup** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="ea7b6-118">在 "**许可协议**" 页上，阅读许可协议。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-118">On the **License Agreement** page, read the license agreement.</span></span> <span data-ttu-id="ea7b6-119">如果同意，请选择 **"我接受许可协议"** ，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-119">If you agree, select **I accept the license agreement** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ea7b6-120">在 "**注册信息**" 页上，输入您的姓名和公司。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-120">On the **Registration Information** page, enter your name and company.</span></span>  
  
5.  <span data-ttu-id="ea7b6-121">在 "**功能选择**" 页上，查看 "**安装路径**" 值。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-121">On the **Feature Selection** page, review the **Installation path** value.</span></span> <span data-ttu-id="ea7b6-122">如有必要，请使用 "**浏览**" 按钮更改位置。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-122">If necessary, use the **Browse** button to change the location.</span></span> <span data-ttu-id="ea7b6-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-123">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="ea7b6-124">在 "**准备安装程序"** 页上，单击 "**安装**" 以安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-124">On the **Ready to Install the Program** page, click **Install** to install Upgrade Advisor.</span></span>  
  
7.  <span data-ttu-id="ea7b6-125">单击“完成”\*\*\*\* 以退出向导。</span><span class="sxs-lookup"><span data-stu-id="ea7b6-125">Click **Finish** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7b6-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea7b6-126">See Also</span></span>  
 [<span data-ttu-id="ea7b6-127">升级顾问必备组件</span><span class="sxs-lookup"><span data-stu-id="ea7b6-127">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
