---
title: 将报表保存到报表服务器（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48dfef01-ed8c-4f23-90c3-de67c90a97dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80e35c447593e89d422e72ea31ec6be34c3619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692756"
---
# <a name="save-reports-to-a-report-server-report-builder"></a><span data-ttu-id="b4245-102">将报表保存到报表服务器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="b4245-102">Save Reports to a Report Server (Report Builder)</span></span>
  <span data-ttu-id="b4245-103">在报表生成器中，可以将报表定义保存到报表服务器（也称为发布报表）。</span><span class="sxs-lookup"><span data-stu-id="b4245-103">In Report Builder, you can save a report definition to a report server (also known as publishing a report).</span></span> <span data-ttu-id="b4245-104">将报表保存到报表服务器时，其他用户可以查看报表。</span><span class="sxs-lookup"><span data-stu-id="b4245-104">When the report is saved to a report server, other users can view the report.</span></span> <span data-ttu-id="b4245-105">每次运行已发布的报表时，将检索最新的数据。</span><span class="sxs-lookup"><span data-stu-id="b4245-105">Each time you run the published report, you will retrieve the most current data.</span></span> <span data-ttu-id="b4245-106">若要保存所呈现报表的静态副本，请将该报表导出为另一文件格式并保存它，或使用报表历史记录功能来保存所呈现报表的各个版本。</span><span class="sxs-lookup"><span data-stu-id="b4245-106">To save a static copy of a rendered report, export the report to a different file format and save it or use the report history feature to save versions of rendered reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4245-107">所保存的报表定义的位置不影响在预览报表时报表在服务器上还是在本地进行处理。</span><span class="sxs-lookup"><span data-stu-id="b4245-107">The location of the saved report definition does not affect whether the report is processed on the server or processed locally when you preview the report.</span></span>  
  
### <a name="to-save-a-report-to-a-report-server"></a><span data-ttu-id="b4245-108">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="b4245-108">To save a report to a report server</span></span>  
  
1.  <span data-ttu-id="b4245-109">从“报表生成器”按钮，单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="b4245-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="b4245-110">此时将打开 "**另存为**" _\<Report Item\>_ 对话框。</span><span class="sxs-lookup"><span data-stu-id="b4245-110">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4245-111">如果正在重新保存报表，会自动将其重新保存到以前的位置。</span><span class="sxs-lookup"><span data-stu-id="b4245-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="b4245-112">使用“另存为”选项可以更改位置。</span><span class="sxs-lookup"><span data-stu-id="b4245-112">Use the Save As option to change location.</span></span>  
  
2.  <span data-ttu-id="b4245-113">或者，单击 **“最近使用的站点和服务器”** 以显示最近使用的报表服务器和 SharePoint 站点的列表。</span><span class="sxs-lookup"><span data-stu-id="b4245-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="b4245-114">找到要将此报表保存到的报表服务器中的位置。</span><span class="sxs-lookup"><span data-stu-id="b4245-114">Browse to the report server location where you want to save the report.</span></span>  
  
4.  <span data-ttu-id="b4245-115">在 **“名称”** 中，键入报表的名称。</span><span class="sxs-lookup"><span data-stu-id="b4245-115">In **Name**, type the name of the report.</span></span>  
  
5.  <span data-ttu-id="b4245-116">在 **“项类型”** 中，选择要保存的报表项的类型。</span><span class="sxs-lookup"><span data-stu-id="b4245-116">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="b4245-117">报表的类型为 Reports(\*.rdl)。</span><span class="sxs-lookup"><span data-stu-id="b4245-117">The type for reports is Reports(\*.rdl).</span></span>  
  
### <a name="to-save-a-report-as-a-different-name"></a><span data-ttu-id="b4245-118">将报表另存为不同名称</span><span class="sxs-lookup"><span data-stu-id="b4245-118">To save a report as a different name</span></span>  
  
1.  <span data-ttu-id="b4245-119">从 “报表生成器” 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="b4245-119">From the Report Builder button, click **Save As**.</span></span> <span data-ttu-id="b4245-120">此时将打开 "**另存为**" _\<Report Item\>_ 对话框。</span><span class="sxs-lookup"><span data-stu-id="b4245-120">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
2.  <span data-ttu-id="b4245-121">浏览到报表服务器位置或要保存报表的文件共享。</span><span class="sxs-lookup"><span data-stu-id="b4245-121">Browse to the report server location or to the file share where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="b4245-122">在 **“名称”** 中，键入报表的名称。</span><span class="sxs-lookup"><span data-stu-id="b4245-122">In **Name**, type the name of the report.</span></span>  
  
4.  <span data-ttu-id="b4245-123">在 **“项类型”** 中，选择要保存的报表项的类型。</span><span class="sxs-lookup"><span data-stu-id="b4245-123">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="b4245-124">报表的类型为 Reports(\*.rdl)。</span><span class="sxs-lookup"><span data-stu-id="b4245-124">The type for reports is Reports(\*.rdl).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4245-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4245-125">See Also</span></span>  
 <span data-ttu-id="b4245-126">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4245-126">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b4245-127">[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4245-127">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b4245-128">[&#40;报表生成器保存报表&#41;](saving-reports-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b4245-128">[Saving Reports &#40;Report Builder&#41;](saving-reports-report-builder.md) </span></span>  
 [<span data-ttu-id="b4245-129">将报表导出为其他文件类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4245-129">Export a Report as Another File Type &#40;Report Builder and SSRS&#41;</span></span>](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)  
  
  
