---
title: 指定外部项的路径（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 097a3566f914e7810039ee07bc3d3bf3185d7f06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577258"
---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a><span data-ttu-id="1a5fa-102">指定外部项的路径（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a5fa-102">Specifying Paths to External Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a5fa-103">在报表项属性中指定钻取报表、子报表和图像文件等引用项的路径，这些引用项在报表定义文件外部并存储在报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-103">You specify paths in report item properties to reference items such as drillthrough reports, subreports, and image files that are external to the report definition file and are stored on a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="1a5fa-104">在报表生成器中，项的路径必须指定报表服务器上的项。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-104">In Report Builder, paths to items must specify items on a report server.</span></span> <span data-ttu-id="1a5fa-105">不支持项在文件系统上的路径。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-105">Paths to items on a file system are not supported.</span></span> <span data-ttu-id="1a5fa-106">仅当连接到项所在的报表服务器时，才能预览使用这些项的报表。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-106">You can preview a report that uses these items only if you are connected to the report server where the items are located.</span></span>  
  
 <span data-ttu-id="1a5fa-107">在操作、子报表或图像的对话框中指定外部项的路径时，可以直接浏览到报表服务器并选择项。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-107">When you specify a path for an external item in a dialog box for actions, subreports, or images, you can browse directly to the report server and select the item.</span></span> <span data-ttu-id="1a5fa-108">指定钻取报表或子报表的推荐方式是直接浏览到该项并选择它。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-108">Browsing to an item and selecting it directly is the recommended way to specify a drillthrough report or subreport.</span></span> <span data-ttu-id="1a5fa-109">使用这种方式，当您指定报表或子报表参数时，将在下拉列表中出现正确的参数名称。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-109">That way the correct parameter names will be available in a drop-down list when you specify report or subreport parameters.</span></span> <span data-ttu-id="1a5fa-110">更改项路径以指向不同项时，必须根据需要手动更新正确的参数名称和值。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-110">When you change an item path to point to a different item, you must manually update the correct parameter names and values as needed.</span></span>  
  
 <span data-ttu-id="1a5fa-111">在以本机模式配置的报表服务器上，指定钻取报表名称时不需要包括文件扩展名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-111">On a report server configured in native mode, specify a drillthrough report name without the file extension .rdl.</span></span>  
  
 <span data-ttu-id="1a5fa-112">而在以 SharePoint 集成模式配置的报表服务器上，则必须包含文件扩展名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-112">On a report server configured in SharePoint integrated mode, you must include the file extension .rdl.</span></span> <span data-ttu-id="1a5fa-113">路径可以是以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="1a5fa-113">The path can be one of the following:</span></span>  
  
-   <span data-ttu-id="1a5fa-114">**主报表中的项的相对路径。**</span><span class="sxs-lookup"><span data-stu-id="1a5fa-114">**A relative path to the item from the main report.**</span></span> <span data-ttu-id="1a5fa-115">例如，../AllSubreports/Subreport1。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-115">For example, ../AllSubreports/Subreport1.</span></span> <span data-ttu-id="1a5fa-116">在本例中， **..**</span><span class="sxs-lookup"><span data-stu-id="1a5fa-116">In this example, the **..**</span></span> <span data-ttu-id="1a5fa-117">表示主报表所在文件夹的上一级文件夹。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-117">indicates the folder above the folder where the main report is located.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a5fa-118">在报表生成器内运行报表时，不支持相对路径。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-118">Relative paths are not supported when the report is run inside Report Builder.</span></span> <span data-ttu-id="1a5fa-119">若要查看使用外部项的相对路径的报表，请将报表保存到报表服务器，并从那里运行报表。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-119">To view a report that uses relative paths to external items, save the report to the report server, and run the report from there</span></span>  
  
-   <span data-ttu-id="1a5fa-120">**项的完整路径。**</span><span class="sxs-lookup"><span data-stu-id="1a5fa-120">**A full path to the item.**</span></span>  
  
    -   <span data-ttu-id="1a5fa-121">**在报表服务器上：** 路径将从 **/** 主文件夹开始。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-121">**On a report server:** The path starts from **/**, the Home folder.</span></span> <span data-ttu-id="1a5fa-122">例如，/Reports/AllSubreports/Subreport1。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-122">For example, /Reports/AllSubreports/Subreport1.</span></span>  
  
    -   <span data-ttu-id="1a5fa-123">**在 SharePoint 站点上：** 必须在表达式中指定报表名称，并包含报表项的完整 URL 以及文件扩展名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-123">**On a SharePoint site:** You must specify the report name in an expression, with the full URL of the item and the file extension .rdl.</span></span> <span data-ttu-id="1a5fa-124">例如，`="http://server/site/library/folder/Report1.rdl"` 。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-124">For example, `="http://server/site/library/folder/Report1.rdl"`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5fa-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a5fa-125">See Also</span></span>  
 <span data-ttu-id="1a5fa-126">[添加外部图像（报表生成器和 SSRS）](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a5fa-126">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1a5fa-127">[添加子报表和参数（报表生成器和 SSRS）](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a5fa-127">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a5fa-128">在报表中添加钻取操作（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a5fa-128">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
