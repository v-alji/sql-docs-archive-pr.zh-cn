---
title: 更改单元中的项（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 80ef171713e6505867e00e343ce17b70cab9045a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694256"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a><span data-ttu-id="9546d-102">更改单元中的项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9546d-102">Change an Item Within a Cell (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9546d-103">只有非容器项（例如文本框、线条或图像）才可以用新的报表项替换。</span><span class="sxs-lookup"><span data-stu-id="9546d-103">Only a non-container item, such as a text box, line, or image, can be replaced by a new report item.</span></span> <span data-ttu-id="9546d-104">例如，可以将一个表拖到文本框中来用该表替换文本框。</span><span class="sxs-lookup"><span data-stu-id="9546d-104">For example, you can drag a table into a text box to replace the text box with a table.</span></span>  
  
 <span data-ttu-id="9546d-105">如果单元中包含容器项（如矩形、列表、表或矩阵），新项则会添加到该容器项中，而不是替换容器项。</span><span class="sxs-lookup"><span data-stu-id="9546d-105">If the cell contains a container item such as a rectangle, list, table, or matrix, the new item is added to the containing item instead of replacing it.</span></span> <span data-ttu-id="9546d-106">若要用新项替换容器项，则需要先删除该容器。</span><span class="sxs-lookup"><span data-stu-id="9546d-106">To replace a container item with a new item, delete the container.</span></span> <span data-ttu-id="9546d-107">删除容器项将使该容器项替换为文本框，之后即可用其他项来替换该文本框。</span><span class="sxs-lookup"><span data-stu-id="9546d-107">Deleting the container item replaces it with a text box, which you can then replace with another item.</span></span>  
  
 <span data-ttu-id="9546d-108">默认情况下，表、矩阵或列表数据区域中的所有单元都包含文本框。</span><span class="sxs-lookup"><span data-stu-id="9546d-108">By default, all cells in a table, matrix, or list data region contain a text box.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a><span data-ttu-id="9546d-109">更改单元中的项</span><span class="sxs-lookup"><span data-stu-id="9546d-109">To change an item within a cell</span></span>  
  
-   <span data-ttu-id="9546d-110">在 **“插入”** 选项卡的 **“数据区域”** 或 **“报表项”** 组中，单击要添加到报表的项，然后单击报表。</span><span class="sxs-lookup"><span data-stu-id="9546d-110">On the **Insert** tab, in the **Data Regions** or **Report Items** group, click the item that you want to add to the report, and then click the report.</span></span> <span data-ttu-id="9546d-111">该项将添加到报表。</span><span class="sxs-lookup"><span data-stu-id="9546d-111">The item is added to the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9546d-112">在将某一图像报表项拖到单元中时，“图像属性”  对话框将打开，从中可以设置图像添加到单元前的属性，例如图像的源。</span><span class="sxs-lookup"><span data-stu-id="9546d-112">The **Image Properties** dialog box opens when you drag an image report item to a cell, where you can set properties such as the source of the image before the image is added to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9546d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9546d-113">See Also</span></span>  
 <span data-ttu-id="9546d-114">[图像、文本框、矩形和线条（报表生成器和 SSRS）](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9546d-114">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9546d-115">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9546d-115">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
