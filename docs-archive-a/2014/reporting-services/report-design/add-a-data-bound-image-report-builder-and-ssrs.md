---
title: 添加数据绑定图像（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577296"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a><span data-ttu-id="7dfe5-102">添加数据绑定图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7dfe5-102">Add a Data-Bound Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7dfe5-103">报表可以包括对存储在数据库中的图像的引用。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-103">A report can include a reference to an image that is stored in a database.</span></span> <span data-ttu-id="7dfe5-104">此类图像称为“数据绑定图像”  。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-104">Such an image is known as a *data-bound image*.</span></span> <span data-ttu-id="7dfe5-105">例如，在产品列表中产品名称旁边显示的图片就是数据绑定图像。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-105">The pictures that appear alongside product names in a product list are examples of data-bound images.</span></span>  
  
 <span data-ttu-id="7dfe5-106">将数据绑定图像添加到页眉或页脚还需要其他步骤。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-106">Adding a data-bound image to a page header or page footer requires additional steps.</span></span> <span data-ttu-id="7dfe5-107">有关详细信息，请参阅[页眉和页脚（报表生成器和 SSRS）](page-headers-and-footers-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-107">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a><span data-ttu-id="7dfe5-108">添加数据绑定图像</span><span class="sxs-lookup"><span data-stu-id="7dfe5-108">To add a data-bound image</span></span>  
  
1.  <span data-ttu-id="7dfe5-109">在报表设计视图中，创建一个表和一个数据集，表中具有数据源连接，数据集中具有包含二进制图像数据的一个字段。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-109">In report design view, create a table with a data source connection and a dataset with a field that contains binary image data.</span></span> <span data-ttu-id="7dfe5-110">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="7dfe5-111">在您的表中插入列。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-111">Insert a column in your table.</span></span> <span data-ttu-id="7dfe5-112">有关详细信息，请参阅[插入或删除列（报表生成器和 SSRS）](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="7dfe5-113">在 **“插入”** 菜单上，单击 **“图像”** ，然后在新列的数据行中单击。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-113">On the **Insert** menu, click **Image**, and then click in the data row of the new column.</span></span>  
  
4.  <span data-ttu-id="7dfe5-114">在 **“图像属性”** 对话框的“常规”页上，在 **“名称”** 文本框中键入名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-114">On the General page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
5.  <span data-ttu-id="7dfe5-115">（可选）在“工具提示”文本框中，键入当用户将鼠标指针悬停在以 HTML 格式呈现的报表中的图像上时所要显示的文本  。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-115">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in the report rendered for HTML.</span></span>  
  
6.  <span data-ttu-id="7dfe5-116">在 **“选择图像源”** 中，选择 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-116">In **Select the image source**, select **Database**.</span></span>  
  
7.  <span data-ttu-id="7dfe5-117">在 **“使用此字段”** 中，选择在您的报表中包含图像的字段。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-117">In **Use this Field**, select the field that contains images in your report.</span></span>  
  
8.  <span data-ttu-id="7dfe5-118">在“使用此 MIME 类型”中，选择图像的 MIME 类型或文件格式，如 bmp  。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-118">In **Use this MIME type**, select the MIME type, or file format, of the image-for example, bmp.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="7dfe5-119">在报表设计图面上将出现图像占位符。</span><span class="sxs-lookup"><span data-stu-id="7dfe5-119">An image placeholder appears on the report design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfe5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dfe5-120">See Also</span></span>  
 <span data-ttu-id="7dfe5-121">[图像（报表生成器和 SSRS）](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7dfe5-121">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7dfe5-122">[在报表中嵌入图像（报表生成器和 SSRS）](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7dfe5-122">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7dfe5-123">[添加外部图像（报表生成器和 SSRS）](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7dfe5-123">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7dfe5-124">“图像属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7dfe5-124">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
