---
title: 安装 SQL Server 2014 服务更新 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace0fd187386d9a9d96e82f61d1efaa254f08c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688156"
---
# <a name="install-sql-server-2014-servicing-updates"></a><span data-ttu-id="94bfd-102">安装 SQL Server 2014 服务更新</span><span class="sxs-lookup"><span data-stu-id="94bfd-102">Install SQL Server 2014 Servicing Updates</span></span>
  <span data-ttu-id="94bfd-103">本主题提供了有关为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]安装更新的信息。</span><span class="sxs-lookup"><span data-stu-id="94bfd-103">This topic provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="94bfd-104">本节提供有关以下方面的信息：</span><span class="sxs-lookup"><span data-stu-id="94bfd-104">This section provides information about the following:</span></span>  
  
-   <span data-ttu-id="94bfd-105">在全新安装期间为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装更新</span><span class="sxs-lookup"><span data-stu-id="94bfd-105">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] during a new installation</span></span>  
  
-   <span data-ttu-id="94bfd-106">在已安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后为其安装更新</span><span class="sxs-lookup"><span data-stu-id="94bfd-106">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed.</span></span>  
  
 <span data-ttu-id="94bfd-107">我们建议客户及时评估和安装最新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新，以便确保系统是最新的并且具有最近的安全更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-107">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span>  
  
## <a name="installing-updates-for-sscurrent-during-a-new-installation"></a><span data-ttu-id="94bfd-108">在全新安装期间为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装更新</span><span class="sxs-lookup"><span data-stu-id="94bfd-108">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] During a New Installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="94bfd-109">安装程序将最新的产品更新集成到主产品安装中，以便可以同时安装主产品及其适用的更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-109">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span> <span data-ttu-id="94bfd-110">产品更新可以从以下位置搜索适用的更新：</span><span class="sxs-lookup"><span data-stu-id="94bfd-110">Product Update can search for the applicable updates from:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="94bfd-111">Update</span><span class="sxs-lookup"><span data-stu-id="94bfd-111">Update</span></span>  
  
-   <span data-ttu-id="94bfd-112">Windows Server Update Services (WSUS)</span><span class="sxs-lookup"><span data-stu-id="94bfd-112">Windows Server Update Services (WSUS)</span></span>  
  
-   <span data-ttu-id="94bfd-113">本地文件夹</span><span class="sxs-lookup"><span data-stu-id="94bfd-113">A local folder</span></span>  
  
-   <span data-ttu-id="94bfd-114">网络共享</span><span class="sxs-lookup"><span data-stu-id="94bfd-114">A network share</span></span>  
  
 <span data-ttu-id="94bfd-115">在找到最新版本的适用更新后，安装程序将下载这些更新并将其与当前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程集成在一起。</span><span class="sxs-lookup"><span data-stu-id="94bfd-115">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="94bfd-116">产品更新可包括累积更新、Service Pack 或者 Service Pack 连同累积更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-116">Product Update can include a cumulative update, service pack, or service pack plus cumulative update.</span></span> <span data-ttu-id="94bfd-117">产品更新功能是 PCU1 中提供的补充[功能](https://go.microsoft.com/fwlink/?LinkId=219945)的扩展 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94bfd-117">Product Update functionality is an extension of the [Slipstream Functionality](https://go.microsoft.com/fwlink/?LinkId=219945) that was available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.</span></span>  
  
## <a name="installing-updates-for-sscurrent-after-it-has-already-been-installed"></a><span data-ttu-id="94bfd-118">在已安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后为其安装更新</span><span class="sxs-lookup"><span data-stu-id="94bfd-118">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed</span></span>  
 <span data-ttu-id="94bfd-119">在的已安装实例上 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，我们建议你应用所有可用的更新：常规分发版本 (GDR-安全/关键更新) 、Service pack (SP) ，以及最新的可用累积更新 (CU) 。</span><span class="sxs-lookup"><span data-stu-id="94bfd-119">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply all available updates: General Distribution Releases (GDR - security/critical updates), Service Packs (SP), as well as the latest available Cumulative Update (CU).</span></span>  
  
 <span data-ttu-id="94bfd-120">根据服务发布的类型，可以通过 Microsoft 更新 (MU) 、Microsoft 下载中心和/或客户支持服务修补程序服务器提供 SQL Server 更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-120">Depending on the type of servicing release, SQL Server updates are available via Microsoft Update (MU), the Microsoft Download Center, and/or the Customer Support Services hotfix Server.</span></span> <span data-ttu-id="94bfd-121">SQL Server 的安全更新和关键更新由 Microsoft 更新 (自动提供，以便通过控制面板) 中的 Windows 更新来查看所需的这些更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-121">Security and Critical updates for SQL Server are automatically provided by Microsoft Update (to be able to see these updates you need to opt-in to MU through Windows Update in Control panel).</span></span> <span data-ttu-id="94bfd-122">在 MU 上，Service Pack 可作为可选/重要下载和下载中心提供。</span><span class="sxs-lookup"><span data-stu-id="94bfd-122">Service Packs are available on MU as Optional/Important downloads as well as the Download Center.</span></span> <span data-ttu-id="94bfd-123">在 CU 知识库文章中提供的 Microsoft 修补程序下载服务器上提供了累积更新。</span><span class="sxs-lookup"><span data-stu-id="94bfd-123">Cumulative updates are available on the Microsoft hotfix download server provided in CU Knowledge Base articles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bfd-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94bfd-124">See Also</span></span>  
 <span data-ttu-id="94bfd-125">[从安装向导安装 SQL Server 2014 &#40;安装程序&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="94bfd-125">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="94bfd-126">[从命令提示符安装更新](installing-updates-from-the-command-prompt.md)会[将功能添加到 SQL Server 2014 &#40;安装程序的实例&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span><span class="sxs-lookup"><span data-stu-id="94bfd-126">[Installing updates from the command prompt](installing-updates-from-the-command-prompt.md) [Add Features to an Instance of SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span></span>  
 [<span data-ttu-id="94bfd-127">删除 SQL Server 2014 安装</span><span class="sxs-lookup"><span data-stu-id="94bfd-127">Drop a SQL Server 2014 Installation</span></span>](repair-a-failed-sql-server-installation.md)  
  
  
