---
title: 添加外部图像（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d0030c8f29b14b2c62048be306daa15948cd8d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687455"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a><span data-ttu-id="bc38d-102">添加外部图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bc38d-102">Add an External Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bc38d-103">外部图像可在本机模式或 SharePoint 集成模式下处于报表服务器上，或者可处于任何其他网站上。</span><span class="sxs-lookup"><span data-stu-id="bc38d-103">External images can be on a report server in native mode or SharePoint integrated mode, or on any other Web site.</span></span> <span data-ttu-id="bc38d-104">当您在报表中包括外部图像时，必须验证图像是否存在以及报表读取器是否拥有访问图像的权限。</span><span class="sxs-lookup"><span data-stu-id="bc38d-104">When you include external images in your report, you must verify that the image exists and that the report reader has permissions to access the image.</span></span> <span data-ttu-id="bc38d-105">有关详细信息，请参阅[图像（报表生成器和 SSRS）](images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bc38d-105">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a><span data-ttu-id="bc38d-106">添加外部图像</span><span class="sxs-lookup"><span data-stu-id="bc38d-106">To add an external image</span></span>  
  
1.  <span data-ttu-id="bc38d-107">在报表设计视图的 **“插入”** 选项卡上，单击 **“图像”** 。</span><span class="sxs-lookup"><span data-stu-id="bc38d-107">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="bc38d-108">在设计图面上，单击某个位置，然后拖动一个框调整到所需图像大小。</span><span class="sxs-lookup"><span data-stu-id="bc38d-108">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="bc38d-109">在 **“图像属性”** 对话框的 **“常规”** 选项卡中，在 **“名称”** 文本框中键入名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="bc38d-109">On the **General** tab of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="bc38d-110">（可选）在“工具提示”文本框中，键入当用户将鼠标指针悬停在以 HTML 格式呈现的报表中的图像上时所要显示的文本  。</span><span class="sxs-lookup"><span data-stu-id="bc38d-110">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in a report rendered for HTML.</span></span>  
  
5.  <span data-ttu-id="bc38d-111">在 **“选择图像源”** 中，选择 **“外部”** 。</span><span class="sxs-lookup"><span data-stu-id="bc38d-111">In **Select the image source**, select **External**.</span></span>  
  
     <span data-ttu-id="bc38d-112">对于在本机模式下的报表服务器上的图像，在“使用此图像”框中键入图像的相对路径，例如 ../images/image1.jpg  。</span><span class="sxs-lookup"><span data-stu-id="bc38d-112">For an image on a report server in native mode, type a relative path to the image in the **Use this image** box-for example, ../images/image1.jpg.</span></span>  
  
     <span data-ttu-id="bc38d-113">对于 SharePoint 集成模式下的 Report Server 上的图像，或者任何其他网站，请在 "**使用此图像**" 框中键入图像的完整 URL，例如，http:// \<SharePointservername> / \<site> /Documents/images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="bc38d-113">For an image on a report server in SharePoint integrated mode, or any other Web site, type a full URL to the image in the **Use this image** box-for example, http://\<SharePointservername>/\<site>/Documents/images/image1.jpg.</span></span>  
  
     <span data-ttu-id="bc38d-114">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bc38d-114">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="bc38d-115">（可选）单击“大小”、“可见性”、“操作”或“边框”以设置图像报表项的其他属性     。</span><span class="sxs-lookup"><span data-stu-id="bc38d-115">(Optional) Click **Size**, **Visibility**, **Action**, or **Border** to set additional properties for the image report item.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bc38d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc38d-116">See Also</span></span>  
 <span data-ttu-id="bc38d-117">[在报表中嵌入图像（报表生成器和 SSRS）](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bc38d-117">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bc38d-118">[添加背景图像（报表生成器和 SSRS）](add-a-background-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bc38d-118">[Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bc38d-119">“图像属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bc38d-119">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
