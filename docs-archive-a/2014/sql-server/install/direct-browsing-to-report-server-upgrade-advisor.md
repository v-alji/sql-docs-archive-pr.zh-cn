---
title: 直接浏览到报表服务器 (升级顾问) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ab4d146bba4bd87de56b30ad100b57f79eb68de3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591105"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a><span data-ttu-id="6ed37-102">直接浏览到报表服务器（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="6ed37-102">Direct Browsing to Report Server (Upgrade Advisor)</span></span>
  <span data-ttu-id="6ed37-103">升级顾问检测到您的当前安装 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 正在直接浏览到 Report Server 虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="6ed37-103">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory.</span></span>  
  
||  
|-|  
|<span data-ttu-id="6ed37-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="6ed37-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="6ed37-105">组件</span><span class="sxs-lookup"><span data-stu-id="6ed37-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6ed37-106">说明</span><span class="sxs-lookup"><span data-stu-id="6ed37-106">Description</span></span>  
 <span data-ttu-id="6ed37-107">升级顾问检测到您的当前安装 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 正在直接浏览到 Report Server 虚拟目录，例如**http:// \<server name> /ReportServer**。</span><span class="sxs-lookup"><span data-stu-id="6ed37-107">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory, for example **http://\<server name>/ReportServer**.</span></span> <span data-ttu-id="6ed37-108">在当前版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中不支持它。</span><span class="sxs-lookup"><span data-stu-id="6ed37-108">This is not supported in current versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ed37-109">此规则是一则警告，将不阻止升级。</span><span class="sxs-lookup"><span data-stu-id="6ed37-109">This rule is a warning and upgrade is not blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6ed37-110">纠正措施</span><span class="sxs-lookup"><span data-stu-id="6ed37-110">Corrective Action</span></span>  
 <span data-ttu-id="6ed37-111">浏览使用用于文档库的 SharePoint 用户界面，或使用**http:// \<server name> /sharepoint site>/_vti_bin/reportserver**。</span><span class="sxs-lookup"><span data-stu-id="6ed37-111">Browse using the SharePoint user interface for document libraries or use **http://\<server name>/sharepoint site>/_vti_bin/reportserver**.</span></span>  
  
  
