---
title: " (SSAS) 选择 \"表和视图\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 891da51478670122f5dbce8fdd7be55c98c898c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692575"
---
# <a name="select-tables-and-views-ssas"></a><span data-ttu-id="d8cf1-102">选择表和视图 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="d8cf1-102">Select Tables and Views (SSAS)</span></span>
  <span data-ttu-id="d8cf1-103">**“表导入向导”** 的这一页可用于选择要从其导入数据的表和视图。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="d8cf1-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="d8cf1-105">此页上表和视图的外观将不会确保该导入将成功。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="d8cf1-106">如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将失败。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="d8cf1-107">对于使用 Windows 身份验证的数据源，当前用户的凭据用于在“选择表和视图”对话框中提取表和视图。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="d8cf1-108">对于其他数据源，在连接字符串中提供的凭据用于提取数据。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d8cf1-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="d8cf1-109">UI element list</span></span>  
 <span data-ttu-id="d8cf1-110">**Server**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-110">**Server**</span></span>  
 <span data-ttu-id="d8cf1-111">显示连接到的服务器。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-111">Displays the server that you are connected to.</span></span>  
  
 <span data-ttu-id="d8cf1-112">**Database**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-112">**Database**</span></span>  
 <span data-ttu-id="d8cf1-113">显示您选择的数据库。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-113">Displays the database that you selected.</span></span>  
  
 <span data-ttu-id="d8cf1-114">**表和视图**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-114">**Tables and Views**</span></span>  
 <span data-ttu-id="d8cf1-115">列出数据库中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-115">Lists the tables and views in the database.</span></span> <span data-ttu-id="d8cf1-116">选中要导入的每个表和视图旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-116">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="d8cf1-117">**源表**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-117">**Source Table**</span></span>  
 <span data-ttu-id="d8cf1-118">基于数据源的类型指定源表的名称。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-118">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="d8cf1-119">**架构**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-119">**Schema**</span></span>  
 <span data-ttu-id="d8cf1-120">指定包含源表的架构。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-120">Specifies the schema in which the source table is contained.</span></span> <span data-ttu-id="d8cf1-121">根据数据库的类型，架构可作为其他对象（例如表）的容器，并且还可指示这些对象的所有权。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-121">Depending on the type of database, a schema functions as a container for other objects, such as tables, and can also indicate ownership of those objects.</span></span>  
  
 <span data-ttu-id="d8cf1-122">**友好名称**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-122">**Friendly Name**</span></span>  
 <span data-ttu-id="d8cf1-123">指定源表的友好名称。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-123">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="d8cf1-124">默认情况下，该列显示在 **“源表”** 列中出现的源表的名称。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-124">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span> <span data-ttu-id="d8cf1-125">如果您要使用与源数据库中所用名称不同的名称，请更改该名称。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-125">Change the name if you want to use a different name than the name used in the source database.</span></span>  
  
 <span data-ttu-id="d8cf1-126">**筛选器详细信息**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-126">**Filter Details**</span></span>  
 <span data-ttu-id="d8cf1-127">在某一筛选器已应用于要导入的数据时，在“筛选器详细信息”对话框中显示数据导入筛选器。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d8cf1-127">When a filter has been applied to the data that is being imported, displays the data import filter in the **Filter Details** dialog box.</span></span> <span data-ttu-id="d8cf1-128">有关详细信息，请参阅[筛选器详细信息 (SSAS)](filter-details-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-128">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="d8cf1-129">**预览并筛选**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-129">**Preview and Filter**</span></span>  
 <span data-ttu-id="d8cf1-130">显示“预览选择的表”\*\*\*\* 对话框，该对话框用于将筛选器应用于要导入的数据。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-130">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="d8cf1-131">有关详细信息，请参阅[预览选择的表 (SSAS)](preview-selected-table-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-131">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="d8cf1-132">**选择相关表**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-132">**Select Related Tables**</span></span>  
 <span data-ttu-id="d8cf1-133">选择与您已经选择的表和视图相关的表和视图以进行导入。</span><span class="sxs-lookup"><span data-stu-id="d8cf1-133">Selects for import those tables and views that are related to the tables and views that you have already selected.</span></span>  
  
  
