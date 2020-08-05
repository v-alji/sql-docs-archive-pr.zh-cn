---
title: 选择表和视图 (数据馈送)  (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 46c317ecf2a87adcde264e8d6d7e822eb833b8b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580914"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a><span data-ttu-id="99f19-102">选择表和视图（数据馈送）(SSAS)</span><span class="sxs-lookup"><span data-stu-id="99f19-102">Select Tables and Views (Data Feeds) (SSAS)</span></span>
  <span data-ttu-id="99f19-103">**“表导入向导”** 的这一页可用于选择要从其导入数据的表和视图。</span><span class="sxs-lookup"><span data-stu-id="99f19-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="99f19-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="99f19-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="99f19-105">此页上表和视图的外观将不会确保该导入将成功。</span><span class="sxs-lookup"><span data-stu-id="99f19-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="99f19-106">如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将失败。</span><span class="sxs-lookup"><span data-stu-id="99f19-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="99f19-107">对于使用 Windows 身份验证的数据源，当前用户的凭据用于在“选择表和视图”对话框中提取表和视图。</span><span class="sxs-lookup"><span data-stu-id="99f19-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="99f19-108">对于其他数据源，在连接字符串中提供的凭据用于提取数据。</span><span class="sxs-lookup"><span data-stu-id="99f19-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="99f19-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="99f19-109">UI element list</span></span>  
 <span data-ttu-id="99f19-110">**数据馈送 URL**</span><span class="sxs-lookup"><span data-stu-id="99f19-110">**Data feed URL**</span></span>  
 <span data-ttu-id="99f19-111">显示所选数据馈送的 URL。</span><span class="sxs-lookup"><span data-stu-id="99f19-111">Displays the URL for the data feed that you selected.</span></span>  
  
 <span data-ttu-id="99f19-112">**表和视图**</span><span class="sxs-lookup"><span data-stu-id="99f19-112">**Tables and views**</span></span>  
 <span data-ttu-id="99f19-113">列出数据馈送中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="99f19-113">Lists the tables and views in the data feed.</span></span> <span data-ttu-id="99f19-114">选中要导入的每个表和视图旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="99f19-114">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="99f19-115">**源表**</span><span class="sxs-lookup"><span data-stu-id="99f19-115">**Source Table**</span></span>  
 <span data-ttu-id="99f19-116">基于数据源的类型指定源表的名称。</span><span class="sxs-lookup"><span data-stu-id="99f19-116">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="99f19-117">**友好名称**</span><span class="sxs-lookup"><span data-stu-id="99f19-117">**Friendly Name**</span></span>  
 <span data-ttu-id="99f19-118">指定源表的友好名称。</span><span class="sxs-lookup"><span data-stu-id="99f19-118">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="99f19-119">默认情况下，该列显示在 **“源表”** 列中出现的源表的名称。</span><span class="sxs-lookup"><span data-stu-id="99f19-119">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span>  
  
 <span data-ttu-id="99f19-120">**筛选器详细信息**</span><span class="sxs-lookup"><span data-stu-id="99f19-120">**Filter Details**</span></span>  
 <span data-ttu-id="99f19-121">在某一筛选器已应用于要导入的数据时，在“筛选器详细信息”\*\*\*\* 对话框中显示数据导入筛选器。</span><span class="sxs-lookup"><span data-stu-id="99f19-121">Displays the data import filter in the **Filter Details** dialog box, when a filter has been applied to the data that is being imported.</span></span> <span data-ttu-id="99f19-122">有关详细信息，请参阅[筛选器详细信息 (SSAS)](filter-details-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="99f19-122">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="99f19-123">**预览并筛选**</span><span class="sxs-lookup"><span data-stu-id="99f19-123">**Preview and Filter**</span></span>  
 <span data-ttu-id="99f19-124">显示“预览选择的表”\*\*\*\* 对话框，该对话框用于将筛选器应用于要导入的数据。</span><span class="sxs-lookup"><span data-stu-id="99f19-124">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="99f19-125">有关详细信息，请参阅[预览选择的表 (SSAS)](preview-selected-table-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="99f19-125">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="99f19-126">**选择相关表**</span><span class="sxs-lookup"><span data-stu-id="99f19-126">**Select Related Tables**</span></span>  
 <span data-ttu-id="99f19-127">选择与您选择的表和视图相关的表。</span><span class="sxs-lookup"><span data-stu-id="99f19-127">Select tables that are related to the tables and views that you have selected.</span></span>  
  
  
