---
title: 排查 PowerPivot for SharePoint 安装问题 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3adc27132d976288c14ac702baae0b842e8aef0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586148"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="0034f-102">排除 PowerPivot for SharePoint 安装故障</span><span class="sxs-lookup"><span data-stu-id="0034f-102">Troubleshoot a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="0034f-103">如果看到错误而不是预期的页面和功能，请执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="0034f-103">If you get errors instead of the pages and features you expect, do the following.</span></span>  
  
-   <span data-ttu-id="0034f-104">查阅 SharePoint 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的发行说明以获取已知安装问题的解决办法。</span><span class="sxs-lookup"><span data-stu-id="0034f-104">Review release notes for both SharePoint and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to get workarounds for known installation problems.</span></span> <span data-ttu-id="0034f-105">发行说明随安装介质提供或在您下载软件的 Microsoft 网站上提供。</span><span class="sxs-lookup"><span data-stu-id="0034f-105">Release notes are provided with the installation media or on the Microsoft site from which you downloaded the software.</span></span>  
  
    -   <span data-ttu-id="0034f-106">[SQL Server 2014 发行说明](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0034f-106">[SQL Server 2014 Release Notes](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).</span></span>  
  
-   <span data-ttu-id="0034f-107">请参阅 Technet wiki 主题： [PowerPivot (和其他外接程序的疑难解答) ](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0034f-107">See the Technet wiki topic, [Troubleshooting Installations of PowerPivot (and other add-ins)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).</span></span>  
  
## <a name="issues"></a><span data-ttu-id="0034f-108">问题</span><span class="sxs-lookup"><span data-stu-id="0034f-108">Issues</span></span>  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a><span data-ttu-id="0034f-109">PowerPivot 库缩略图图形显示为红 X</span><span class="sxs-lookup"><span data-stu-id="0034f-109">PowerPivot Gallery Thumbnail images show as a red X</span></span>  
 <span data-ttu-id="0034f-110">一个可能的原因是 "**网站集的 PowerPivot 功能集成**" 未处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="0034f-110">One Possible cause is the **PowerPivot features Integration for Site Collections** is not active.</span></span> <span data-ttu-id="0034f-111">请完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="0034f-111">Complete the following:</span></span>  
  
1.  <span data-ttu-id="0034f-112">在 PowerPivot 库中，从齿轮图标![SharePoint 设置](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 设置")或**Home**列表中单击 "**网站设置**"。</span><span class="sxs-lookup"><span data-stu-id="0034f-112">In the PowerPivot Gallery library, click **Site Settings** from either the gear icon ![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") or the **Home** list.</span></span>  
  
2.  <span data-ttu-id="0034f-113">在 **“网站集管理”** 部分，单击 **“网站集功能”**。</span><span class="sxs-lookup"><span data-stu-id="0034f-113">In the **Site Collection Administration** section, click **Site Collection Features**.</span></span>  
  
3.  <span data-ttu-id="0034f-114">单击 **“网站集功能”**。</span><span class="sxs-lookup"><span data-stu-id="0034f-114">Click **Site Collection Features**.</span></span>  
  
4.  <span data-ttu-id="0034f-115">验证 "**网站集的 PowerPivot 功能集成**" 处于**活动状态**。</span><span class="sxs-lookup"><span data-stu-id="0034f-115">Verify **PowerPivot features Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="0034f-116">有关此问题的其他原因，请参阅[PowerPivot 库为图标 (显示红色 X](https://support.microsoft.com/kb/2361559) https://support.microsoft.com/kb/2361559) 。</span><span class="sxs-lookup"><span data-stu-id="0034f-116">For additional causes of this issue, see [PowerPivot Gallery shows Red X's for Icons](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).</span></span>  
  
  
