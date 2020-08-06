---
title: 对列重新排序 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f0c47a631ffe699936a8d45bcc4e47e0b6f0a985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688969"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a><span data-ttu-id="5ddb4-102">对列重新排序（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="5ddb4-102">Reorder Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="5ddb4-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，你可以在加载前先通过筛选列表对列重新排序。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you can reorder columns by filtering the list before loading.</span></span>  
  
 <span data-ttu-id="5ddb4-104">当您在 **“筛选器”** 对话框中对属性重新排序后，数据将以新顺序加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-104">When you reorder attributes in the **Filter** dialog box, the data is loaded into Excel with the new order.</span></span> <span data-ttu-id="5ddb4-105">但是，下次筛选属性数据时，顺序将恢复为原始设计中的顺序。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-105">However, the next time that you filter the attribute data, the order will revert to the order in the original design.</span></span> <span data-ttu-id="5ddb4-106">若要永久更改该顺序，管理员应该在主数据管理器的 **“系统管理”** 区域中更改该顺序。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-106">To change the order permanently, an administrator should change the order in the **System Administration** area of Master Data Manager.</span></span> <span data-ttu-id="5ddb4-107">有关详细信息，请参阅 [Change the Order of Attributes](../change-the-order-of-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-107">For more information, see [Change the Order of Attributes](../change-the-order-of-attributes.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5ddb4-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="5ddb4-108">Prerequisites</span></span>  
 <span data-ttu-id="5ddb4-109">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="5ddb4-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5ddb4-110">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-110">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-reorder-mds-managed-columns"></a><span data-ttu-id="5ddb4-111">对 MDS 管理的列重新排序</span><span class="sxs-lookup"><span data-stu-id="5ddb4-111">To reorder MDS-managed columns</span></span>  
  
1.  <span data-ttu-id="5ddb4-112">打开 Excel，在 **“主数据”** 选项卡上连接到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-112">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="5ddb4-113">有关详细信息，请参阅[连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-113">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="5ddb4-114">在 **“主数据资源管理器”** 窗格中，选择所需模型和版本。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-114">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="5ddb4-115">随之填充实体列表。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-115">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="5ddb4-116">如果 **“主数据资源管理器”** 窗格不可见，请在 **“连接并加载”** 组中，单击 **“显示资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-116">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="5ddb4-117">如果 **“主数据资源管理器”** 窗格被禁用，则是因为现有工作表中已包含 MDS 管理的数据。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-117">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="5ddb4-118">若要启用该窗格，请打开一个新工作表。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-118">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="5ddb4-119">在 **“主数据资源管理器”** 窗格中，单击一个实体。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-119">In the **Master Data Explorer** pane, click an entity.</span></span>  
  
4.  <span data-ttu-id="5ddb4-120">在 **“连接并加载”** 组中，单击 **“筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-120">In the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="5ddb4-121">在 **“筛选器”** 对话框 **“列”** 部分的属性列表中，单击要移动的属性。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-121">In the **Filter** dialog box, in the **Columns** section, in the list of attributes, click the attribute you want to move.</span></span>  
  
6.  <span data-ttu-id="5ddb4-122">在列表右侧，单击 **上** 箭头或 **下** 箭头，在工作表中左右移动该属性。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-122">To the right of the list, click the **Up** or **Down** arrow to move the attribute left and right in the worksheet.</span></span>  
  
7.  <span data-ttu-id="5ddb4-123">对于每个属性重复步骤 7，直到从上到下的顺序表示您想在工作表中呈现的从左到右的顺序。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-123">Repeat step 7 for each attribute until the top-to-bottom order represents the left-to-right order you want in the worksheet.</span></span>  
  
8.  <span data-ttu-id="5ddb4-124">单击 **“加载数据”**。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-124">Click **Load Data**.</span></span> <span data-ttu-id="5ddb4-125">工作表将使用 MDS 管理的数据填充，且列按您指定的顺序显示。</span><span class="sxs-lookup"><span data-stu-id="5ddb4-125">The sheet is populated with MDS-managed data and the columns are displayed in the order you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ddb4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ddb4-126">See Also</span></span>  
 [<span data-ttu-id="5ddb4-127">MDS Add-in for Excel&#41;中加载数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="5ddb4-127">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
