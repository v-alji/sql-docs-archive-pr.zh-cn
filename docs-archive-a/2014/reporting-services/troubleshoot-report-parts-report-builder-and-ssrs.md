---
title: " (报表生成器和 SSRS) 的报表部件疑难解答 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 798bb59fc2470dedd3bdc5c996b4da395e57bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689730"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="cb2f4-102">报表部件故障排除（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="cb2f4-102">Troubleshoot Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cb2f4-103">下面的这些技巧可在您使用报表部件时对您有所帮助。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-103">These tips can help when working with report parts.</span></span>  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a><span data-ttu-id="cb2f4-104">为何我的同事和我在搜索报表部件时对于同一个报表部件看到不同的实例？</span><span class="sxs-lookup"><span data-stu-id="cb2f4-104">Why do my co-worker and I see different instances of the same report part when we search for it?</span></span>  
 <span data-ttu-id="cb2f4-105">在报表服务器上或者与报表服务器相集成的 SharePoint 站点上，对于单个报表部件可能存在多个实例，并且所有实例将具有相同的全局唯一标识符 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-105">There can be multiple instances of a single report part on a report server or SharePoint site integrated with a report server, and all instances will have the same globally unique identifier (GUID).</span></span> <span data-ttu-id="cb2f4-106">在搜索结果列表中仅显示最新实例。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-106">Only the most recent instance is displayed in the list of search results.</span></span> <span data-ttu-id="cb2f4-107">在某些情况下，单个报表部件的不同实例可能拥有不同的权限。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-107">In some situations, different instances of a single report part can have different permissions.</span></span> <span data-ttu-id="cb2f4-108">如果您的同事与您对服务器拥有的权限不同，你们将不会看到同一个实例。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-108">If your co-worker and you have different permissions on the server, you will not see the same instance.</span></span> <span data-ttu-id="cb2f4-109">例如，假定全都具有相同 GUID 的报表部件的多个副本保存在 SharePoint 集成模式下报表服务器上的不同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-109">For example, say that multiple copies of a report part, all with the same GUID, are saved in different folders on a report server in SharePoint integrated mode.</span></span> <span data-ttu-id="cb2f4-110">如果这些文件夹具有不同的权限，则它们中的报表部件也将具有不同的权限。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-110">If the folders have different permissions, then the report parts in those folders will also have different permissions.</span></span>  
  
 <span data-ttu-id="cb2f4-111">若要查看您和您的同事拥有哪些权限，请咨询报表服务器管理员。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-111">To see what permissions you and your co-worker have, ask your report server administrator.</span></span>  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a><span data-ttu-id="cb2f4-112">在我搜索已上载到 SharePoint 服务器的报表部件时，我看不到它们。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-112">When I search for report parts that I uploaded to a SharePoint server, I do not see them.</span></span> <span data-ttu-id="cb2f4-113">为什么看不到？</span><span class="sxs-lookup"><span data-stu-id="cb2f4-113">Why not?</span></span>  
 <span data-ttu-id="cb2f4-114">如果报表部件是您手动上载到 SharePoint 文档库中的，而非通过使用报表生成器发布的，则这些报表部件在报表部件库中可能不出现。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-114">Report Parts that you have manually uploaded to a SharePoint document library, instead of published by using Report Builder, might not appear in the Report Part Gallery.</span></span> <span data-ttu-id="cb2f4-115">用于库搜索的报表服务器可能需要与 SharePoint 文档库的内容保持同步。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-115">The report server used for the gallery search might need to be synchronized with the contents of the SharePoint document library.</span></span> <span data-ttu-id="cb2f4-116">有关详细信息，请参阅 msdn.microsoft.com 上联机丛书中[的在 SharePoint 管理中心中激活报表服务器文件同步功能](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-116">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a><span data-ttu-id="cb2f4-117">为何其他人在其报表中看不到图像？</span><span class="sxs-lookup"><span data-stu-id="cb2f4-117">Why can't others see the image in their reports?</span></span>  
 <span data-ttu-id="cb2f4-118">如果您发布的报表部件是指向某一图像文件的链接，则该报表部件实际上只是链接。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-118">If you publish a report part that is a link to an image file, the report part is really just a link.</span></span> <span data-ttu-id="cb2f4-119">如果其他人在将图像报表部件添加到其报表后看不到图像，则他们可能对您链接到的图像不具备权限。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-119">If others cannot see the image when they add the image report part to their reports, they might not have permissions for the image that you are linking to.</span></span>  
  
 <span data-ttu-id="cb2f4-120">此种情况有几个可能的解决方案：</span><span class="sxs-lookup"><span data-stu-id="cb2f4-120">There are a few possible solutions to this:</span></span>  
  
-   <span data-ttu-id="cb2f4-121">使该图像文件成为报表部件，而不是使指向图像文件的链接成为报表部件。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-121">Make the image file a report part, instead of making the link to the image file the report part.</span></span>  
  
-   <span data-ttu-id="cb2f4-122">将图像文件移到其他人具有权限的位置。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-122">Move the image file to a location for which others have permissions.</span></span>  
  
-   <span data-ttu-id="cb2f4-123">咨询报表服务器管理员以更改权限。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-123">Ask the report server administrator to change permissions.</span></span>  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a><span data-ttu-id="cb2f4-124">在我尝试发布我的报表部件时，为什么系统显示“循环引用”错误消息？</span><span class="sxs-lookup"><span data-stu-id="cb2f4-124">Why do I get a "circular reference" error message when I try to publish my report part?</span></span>  
 <span data-ttu-id="cb2f4-125">如果报表项具有循环引用，则您无法将其作为报表部件发布。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-125">If report items have a circular reference, you won't be able to publish them as report parts.</span></span> <span data-ttu-id="cb2f4-126">例如，某一报表项指向一个数据集，而该数据集又指向一个参数。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-126">For example, a report item points to a dataset, which in turn points to a parameter.</span></span> <span data-ttu-id="cb2f4-127">而该参数又指向该数据集。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-127">The parameter, in turn, points to the dataset¸ too.</span></span> <span data-ttu-id="cb2f4-128">您将需要首先删除其中一个引用，然后才能发布该报表部件。</span><span class="sxs-lookup"><span data-stu-id="cb2f4-128">You'll need to delete one of the references first before you can publish the report part.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb2f4-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb2f4-129">See Also</span></span>  
 [<span data-ttu-id="cb2f4-130">报表部件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="cb2f4-130">Report Parts &#40;Report Builder and SSRS&#41;</span></span>](report-parts-report-builder-and-ssrs.md)  
  
  
