---
title: 升级顾问先决条件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586112"
---
# <a name="upgrade-advisor-prerequisites"></a><span data-ttu-id="a8d9f-102">升级顾问必备组件</span><span class="sxs-lookup"><span data-stu-id="a8d9f-102">Upgrade Advisor Prerequisites</span></span>
  <span data-ttu-id="a8d9f-103">本主题介绍升级顾问的必备组件。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-103">This topic describes the software requirements for Upgrade Advisor.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8d9f-104">必备条件</span><span class="sxs-lookup"><span data-stu-id="a8d9f-104">Prerequisites</span></span>  
 <span data-ttu-id="a8d9f-105">安装和运行升级顾问的必备组件如下：</span><span class="sxs-lookup"><span data-stu-id="a8d9f-105">The prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] <span data-ttu-id="a8d9f-106">SP1、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]（最低为 SP2 版）、Windows 7 或 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-106">SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginning with SP2, Windows 7, or [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.</span></span>  
  
-   <span data-ttu-id="a8d9f-107">Windows Installer 4.5。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-107">Windows Installer 4.5.</span></span> <span data-ttu-id="a8d9f-108">你可以从[Windows Installer](https://www.microsoft.com/download/details.aspx?id=8483)网站安装 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-108">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="a8d9f-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]（最低为 .NET Framework 4）。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-109">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginning with .NET Framework 4.</span></span> <span data-ttu-id="a8d9f-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]可在产品媒体上找到， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 也可从[SDK、可再发行组件和 Service Pack 下载](https://go.microsoft.com/fwlink/?LinkId=48882)网站中获得。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-110">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [SDK, redistributable, and service pack download Web site](https://go.microsoft.com/fwlink/?LinkId=48882).</span></span>  
  
    -   <span data-ttu-id="a8d9f-111">若要从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 介质安装 .NET Framework 4，请找到磁盘驱动器的根目录。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-111">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="a8d9f-112">然后双击 \redist 文件夹，再双击 DotNetFrameworks 文件夹，然后运行 dotNetFx40_Full_x86_x64.exe（对于 32 位和 64 位操作系统）。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-112">Then double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for both 32-bit and 64-bit operating systems).</span></span>  
  
-   <span data-ttu-id="a8d9f-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom 是安装升级顾问的必备组件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，并且不是由升级顾问安装程序安装的。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="a8d9f-114">安装程序需要 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能包下载和安装 ScriptDom。</span><span class="sxs-lookup"><span data-stu-id="a8d9f-114">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d9f-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8d9f-115">See Also</span></span>  
 [<span data-ttu-id="a8d9f-116">如何安装升级顾问</span><span class="sxs-lookup"><span data-stu-id="a8d9f-116">How to: Install Upgrade Advisor</span></span>](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
