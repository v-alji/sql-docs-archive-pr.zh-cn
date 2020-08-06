---
title: 为多维数据 (报表生成器和 SSRS) 的参数值显示隐藏的数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9c005b6e7c8927316c19a3302e32f4407f9885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694265"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a><span data-ttu-id="66c4d-102">为多维数据的参数值显示隐藏的数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="66c4d-102">Show Hidden Datasets for Parameter Values for Multidimensional Data (Report Builder and SSRS)</span></span>
  <span data-ttu-id="66c4d-103">报表可能包括默认在“报表数据”窗格中不显示的自动生成的数据集（也称为隐藏数据集）。</span><span class="sxs-lookup"><span data-stu-id="66c4d-103">Your report might include automatically-generated datasets (also known as hidden datasets) that do not appear by default in the Report Data pane.</span></span> <span data-ttu-id="66c4d-104">这些数据集是用下列方法创建的：</span><span class="sxs-lookup"><span data-stu-id="66c4d-104">These datasets are created in the following ways:</span></span>  
  
-   <span data-ttu-id="66c4d-105">在用于多维数据库的某些查询设计器中，可以在查询窗格的筛选区域中指定要筛选的字段，并选择是否为筛选器创建查询参数。</span><span class="sxs-lookup"><span data-stu-id="66c4d-105">In some query designers for multidimensional databases, you can specify fields to filter on in the filter area of the query pane, and select whether to create a query parameter for the filter.</span></span> <span data-ttu-id="66c4d-106">如果选择参数选项，会自动创建报表数据集以便为报表参数提供有效的值。</span><span class="sxs-lookup"><span data-stu-id="66c4d-106">If you select the parameter option, report datasets are automatically created to provide valid values for the report parameter.</span></span>  
  
-   <span data-ttu-id="66c4d-107">如果导入基于多维数据库的查询，则还可能将隐藏数据集包括在报表中。</span><span class="sxs-lookup"><span data-stu-id="66c4d-107">If you import a query based on multidimensional databases, you might also include hidden datasets in your report.</span></span>  
  
 <span data-ttu-id="66c4d-108">无法通过向导使用隐藏数据集。</span><span class="sxs-lookup"><span data-stu-id="66c4d-108">Hidden datasets are not available to use from a wizard.</span></span>  
  
 <span data-ttu-id="66c4d-109">可以更改“报表数据”窗格中的视图以显示报表中的所有数据集。</span><span class="sxs-lookup"><span data-stu-id="66c4d-109">You can change the view in the Report Data pane to display all datasets in the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a><span data-ttu-id="66c4d-110">显示隐藏数据集</span><span class="sxs-lookup"><span data-stu-id="66c4d-110">To display hidden datasets</span></span>  
  
-   <span data-ttu-id="66c4d-111">在“报表数据”窗格中，右键单击“数据集”文件夹，然后单击“显示隐藏数据集”  。</span><span class="sxs-lookup"><span data-stu-id="66c4d-111">In the Report Data pane, right-click the Datasets folder, and then click **Show Hidden Datasets**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c4d-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66c4d-112">See Also</span></span>  
 <span data-ttu-id="66c4d-113">[查询设计器 &#40;报表生成器&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="66c4d-113">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="66c4d-114">[Reporting Services 查询设计器](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="66c4d-114">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 <span data-ttu-id="66c4d-115">[报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66c4d-115">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="66c4d-116">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66c4d-116">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
  
  
