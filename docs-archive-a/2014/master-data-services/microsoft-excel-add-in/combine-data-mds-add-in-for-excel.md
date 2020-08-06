---
title: 合并数据 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc2d5bffb6d7a12164a8643e9a790b32538f8979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688973"
---
# <a name="combine-data-mds-add-in-for-excel"></a><span data-ttu-id="f8500-102">合并数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="f8500-102">Combine Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="f8500-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，当你在发布前想要比较数据时，合并来自两个工作表的数据。</span><span class="sxs-lookup"><span data-stu-id="f8500-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combine data from two worksheets when you want to compare data before publishing.</span></span> <span data-ttu-id="f8500-104">在此过程中，您将来自两个工作表中的数据合并到一个工作表中。</span><span class="sxs-lookup"><span data-stu-id="f8500-104">In this procedure, you combine data from a two worksheets into one.</span></span> <span data-ttu-id="f8500-105">然后可以进行进一步的比较，并确定哪些数据（如果有）将发布到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="f8500-105">Then you can perform further comparisons and determine which data, if any, to publish to the MDS repository.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8500-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="f8500-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="f8500-107">必须具有包含 MDS 管理的数据的工作表。</span><span class="sxs-lookup"><span data-stu-id="f8500-107">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="f8500-108">有关详细信息，请参阅将[数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="f8500-108">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f8500-109">必须具有包含要与 MDS 管理的数据合并的数据的工作表。</span><span class="sxs-lookup"><span data-stu-id="f8500-109">You must have a worksheet that contains data you want to combine with MDS-managed data.</span></span> <span data-ttu-id="f8500-110">此工作表必须具有标题行。</span><span class="sxs-lookup"><span data-stu-id="f8500-110">This sheet must have a header row.</span></span>  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a><span data-ttu-id="f8500-111">将非托管数据合并到 MDS 管理的工作表</span><span class="sxs-lookup"><span data-stu-id="f8500-111">To combine non-managed data into an MDS-managed sheet</span></span>  
  
1.  <span data-ttu-id="f8500-112">在包含 MDS 管理的数据的工作表上，在 **“发布并验证”** 组中，单击 **“合并数据”**。</span><span class="sxs-lookup"><span data-stu-id="f8500-112">On the sheet that contains MDS-managed data, in the **Publish and Validate** group, click **Combine Data**.</span></span>  
  
2.  <span data-ttu-id="f8500-113">在 **“合并数据”** 对话框中的 **“要与 MDS 数据组合的范围”** 文本框旁，单击图标。</span><span class="sxs-lookup"><span data-stu-id="f8500-113">In the **Combine Data** dialog box, next to the **Range to combine with MDS data** text box, click the icon.</span></span> <span data-ttu-id="f8500-114">该对话框将收缩。</span><span class="sxs-lookup"><span data-stu-id="f8500-114">The dialog box contracts.</span></span>  
  
3.  <span data-ttu-id="f8500-115">单击包含要合并的数据的工作表。</span><span class="sxs-lookup"><span data-stu-id="f8500-115">Click the sheet that contains the data you want to combine.</span></span>  
  
4.  <span data-ttu-id="f8500-116">突出显示工作表上要合并的所有单元，包括标题行。</span><span class="sxs-lookup"><span data-stu-id="f8500-116">Highlight all cells on the sheet that you want to combine, including the header row.</span></span>  
  
5.  <span data-ttu-id="f8500-117">在 **“合并数据”** 对话框中，单击图标。</span><span class="sxs-lookup"><span data-stu-id="f8500-117">In the **Combine Data** dialog box, click the icon.</span></span> <span data-ttu-id="f8500-118">该对话框将展开。</span><span class="sxs-lookup"><span data-stu-id="f8500-118">The dialog box expands.</span></span>  
  
6.  <span data-ttu-id="f8500-119">对于为 MDS 实体列出的列，选择 **“相应列”** 下的列。</span><span class="sxs-lookup"><span data-stu-id="f8500-119">For a column listed for the MDS entity, select a column under **Corresponding Column**.</span></span> <span data-ttu-id="f8500-120">所有 MDS 列都不需要相应列。</span><span class="sxs-lookup"><span data-stu-id="f8500-120">All MDS columns do not need corresponding columns.</span></span>  
  
7.  <span data-ttu-id="f8500-121">单击 **“合并”**。</span><span class="sxs-lookup"><span data-stu-id="f8500-121">Click **Combine**.</span></span> <span data-ttu-id="f8500-122">**SOURCE** 列将显示，指示数据是来自 MDS 还是外部源。</span><span class="sxs-lookup"><span data-stu-id="f8500-122">A **SOURCE** column is displayed, indicating whether the data is from MDS or an external source.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f8500-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f8500-123">Next Steps</span></span>  
  
-   <span data-ttu-id="f8500-124">若要查找 MDS 管理和外部数据之间的相似之处，请参阅[匹配相似数据 &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="f8500-124">To find similarities between the MDS-managed and external data, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8500-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8500-125">See Also</span></span>  
 <span data-ttu-id="f8500-126">[MDS Add-in for Excel&#41;中加载数据 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f8500-126">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="f8500-127">用于 Excel 的 MDS 外接程序中的数据质量匹配</span><span class="sxs-lookup"><span data-stu-id="f8500-127">Data Quality Matching in the MDS Add-in for Excel</span></span>](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
