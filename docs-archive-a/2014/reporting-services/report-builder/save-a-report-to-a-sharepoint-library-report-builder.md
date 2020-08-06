---
title: 将报表保存到 SharePoint 库（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49878a0d7115a11e804382cb5139aa0ec7b3d254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586474"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a><span data-ttu-id="84e25-102">将报表保存到 SharePoint 库（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="84e25-102">Save a Report to a SharePoint Library (Report Builder)</span></span>
  <span data-ttu-id="84e25-103">若要将报表保存到配置为 SharePoint 集成模式的报表服务器，必须找到 SharePoint 服务器并建立与报表服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="84e25-103">To save a report to a report server configured for SharePoint integration, you must browse to the SharePoint server and establish a connection to the report server.</span></span> <span data-ttu-id="84e25-104">在报表定义中，对与报表相关的项的所有引用都必须使用特定于 SharePoint 报表服务器的值。</span><span class="sxs-lookup"><span data-stu-id="84e25-104">In the report definition, all references to items related to the report must use values that are specific to a SharePoint report server.</span></span> <span data-ttu-id="84e25-105">相关项包括子报表、钻取报表和基于 Web 的图像等资源。</span><span class="sxs-lookup"><span data-stu-id="84e25-105">Related items include subreports, drillthrough reports, and resources such as Web-based images.</span></span> <span data-ttu-id="84e25-106">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="84e25-106">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="84e25-107">必须对 SharePoint 站点拥有 **“成员”** 或 **“所有者”** 权限，才能设置项目的属性。</span><span class="sxs-lookup"><span data-stu-id="84e25-107">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span>  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a><span data-ttu-id="84e25-108">将报表保存到 SharePoint 站点</span><span class="sxs-lookup"><span data-stu-id="84e25-108">To save a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="84e25-109">从“报表生成器”按钮，单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="84e25-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="84e25-110">此时将打开 "**另存为**" _\<Report Item>_ 对话框。</span><span class="sxs-lookup"><span data-stu-id="84e25-110">The **Save As**_\<Report Item>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84e25-111">如果正在重新保存报表，会自动将其重新保存到以前的位置。</span><span class="sxs-lookup"><span data-stu-id="84e25-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="84e25-112">使用 **“另存为”** 选项可以更改位置。</span><span class="sxs-lookup"><span data-stu-id="84e25-112">Use the **Save As** option to change location.</span></span>  
  
2.  <span data-ttu-id="84e25-113">或者，单击 **“最近使用的站点和服务器”** 以显示最近使用的报表服务器和 SharePoint 站点的列表。</span><span class="sxs-lookup"><span data-stu-id="84e25-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="84e25-114">找到 SharePoint 站点，然后单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="84e25-114">Browse to the SharePoint site, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84e25-115">如果超过 10 小时未对已更改的报表进行保存，则该报表将断开与服务器的连接，而且未保存。</span><span class="sxs-lookup"><span data-stu-id="84e25-115">If you leave a changed report for more than 10 hours without saving it, it is disconnected from the server without being saved.</span></span> <span data-ttu-id="84e25-116">如果发生这种情况，请在右下角的状态栏中单击“断开连接”，然后单击“连接”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84e25-116">If that happens, in the lower-right status bar, click **Disconnect**, and then click **Connect**.</span></span> <span data-ttu-id="84e25-117">最近的服务器将位于可用服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="84e25-117">The most recent server will be in the list of available servers.</span></span> <span data-ttu-id="84e25-118">选择该服务器，并且报表将重新连接。</span><span class="sxs-lookup"><span data-stu-id="84e25-118">Select it and the report will reconnect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e25-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84e25-119">See Also</span></span>  
 [<span data-ttu-id="84e25-120">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="84e25-120">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
