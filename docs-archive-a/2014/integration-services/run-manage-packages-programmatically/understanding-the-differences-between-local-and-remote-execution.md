---
title: 了解本地执行与远程执行之间的差异 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 399584c790f4c5a5dd136121c58a5ff7743f4969
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688992"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a><span data-ttu-id="c571a-102">了解本地执行与远程执行之间的差异</span><span class="sxs-lookup"><span data-stu-id="c571a-102">Understanding the Differences between Local and Remote Execution</span></span>
  <span data-ttu-id="c571a-103">包开发人员和管理员应了解与 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包运行位置相关的限制。</span><span class="sxs-lookup"><span data-stu-id="c571a-103">Package developers and administrators should be aware that there are restrictions related to where an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package runs.</span></span>  
  
-   <span data-ttu-id="c571a-104">**包要与启动包的程序运行在同一计算机上。**</span><span class="sxs-lookup"><span data-stu-id="c571a-104">**A package runs on the same computer as the program that launches it**.</span></span> <span data-ttu-id="c571a-105">即使程序加载的是远程存储于另一台计算机上的包，包也要在本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="c571a-105">Even when a program loads a package that is stored remotely on another server, the package runs on the local computer.</span></span>  
  
-   <span data-ttu-id="c571a-106">**在开发环境外，只可以在安装了 Integration Services 的计算机上运行包。**</span><span class="sxs-lookup"><span data-stu-id="c571a-106">**You can only run a package outside the development environment on a computer that has Integration Services installed**.</span></span> <span data-ttu-id="c571a-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 外，您不能在未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的客户端计算机上运行包，您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 许可条款可能不允许您在其他计算机上安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c571a-107">You cannot run packages outside of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing may not permit you to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c571a-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 是服务器组件，不可再分发至客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="c571a-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is a server component and is not redistributable to client computers.</span></span> <span data-ttu-id="c571a-109">若要从客户端计算机运行包，您需要以可确保包运行于服务器上的方式启动包。</span><span class="sxs-lookup"><span data-stu-id="c571a-109">To run packages from a client computer, you need to launch them in a manner that ensures that the packages run on the server.</span></span>  
  
 <span data-ttu-id="c571a-110">有关加载和运行已保存的包的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="c571a-110">For more information about loading and running a saved package, see:</span></span>  
  
-   [<span data-ttu-id="c571a-111">以编程方式加载和运行本地包</span><span class="sxs-lookup"><span data-stu-id="c571a-111">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [<span data-ttu-id="c571a-112">以编程方式加载和运行远程包</span><span class="sxs-lookup"><span data-stu-id="c571a-112">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 <span data-ttu-id="c571a-113">有关运行包并将其输出加载到自定义程序的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="c571a-113">For more information about running a package and loading its output into a custom program, see:</span></span>  
  
-   [<span data-ttu-id="c571a-114">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="c571a-114">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
<span data-ttu-id="c571a-115">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c571a-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c571a-116">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="c571a-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c571a-117">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="c571a-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c571a-118">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="c571a-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c571a-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c571a-119">See Also</span></span>  
 <span data-ttu-id="c571a-120">[以编程方式加载和运行本地包](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="c571a-120">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 <span data-ttu-id="c571a-121">[以编程方式加载和运行远程包](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="c571a-121">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="c571a-122">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="c571a-122">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
