---
title: " (SSAS) 预览选定的表 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693526"
---
# <a name="preview-selected-table-ssas"></a><span data-ttu-id="82a82-102">预览选择的表 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="82a82-102">Preview Selected Table (SSAS)</span></span>
  <span data-ttu-id="82a82-103">**“表导入向导”** 的这一页可用于预览所选表中的数据，选择要在数据导入中包括的列，并且筛选所选列中的数据。</span><span class="sxs-lookup"><span data-stu-id="82a82-103">This page of the **Table Import Wizard** enables you to preview the data in the selected table, to select the columns to include in the data import, and to filter data in the selected columns.</span></span> <span data-ttu-id="82a82-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="82a82-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="82a82-105">不是表中的所有行都显示。</span><span class="sxs-lookup"><span data-stu-id="82a82-105">Not all the rows in the table are displayed.</span></span> <span data-ttu-id="82a82-106">但是，在导入过程中，您设置的筛选器将应用于表中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="82a82-106">However, the filters that you set will be applied to all of the data in the table during import.</span></span>  
  
 <span data-ttu-id="82a82-107">对于使用 Windows 身份验证的数据源，当前用户的凭据用于提取在“预览并筛选”对话框中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="82a82-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the data displayed in the Preview and Filter dialog.</span></span> <span data-ttu-id="82a82-108">对于其他数据源，在连接字符串中提供的凭据用于提取数据。</span><span class="sxs-lookup"><span data-stu-id="82a82-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
 <span data-ttu-id="82a82-109">此页上数据的外观将不会确保导入将成功。</span><span class="sxs-lookup"><span data-stu-id="82a82-109">The appearance of data on this page does not guarantee import will succeed.</span></span> <span data-ttu-id="82a82-110">如果在“模拟信息”页中指定的用户名没有足够的权限从所选数据库中读取，则导入将失败。</span><span class="sxs-lookup"><span data-stu-id="82a82-110">If the user name specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="82a82-111">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="82a82-111">UI element list</span></span>  
 <span data-ttu-id="82a82-112">**列标题中的复选框**</span><span class="sxs-lookup"><span data-stu-id="82a82-112">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="82a82-113">选中该复选框可在数据导入中包括列。</span><span class="sxs-lookup"><span data-stu-id="82a82-113">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="82a82-114">取消选中该复选框则从数据导入中删除列。</span><span class="sxs-lookup"><span data-stu-id="82a82-114">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="82a82-115">**列标题中的下箭头按钮**</span><span class="sxs-lookup"><span data-stu-id="82a82-115">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="82a82-116">筛选列中的数据。</span><span class="sxs-lookup"><span data-stu-id="82a82-116">Filter data in the column.</span></span>  
  
 <span data-ttu-id="82a82-117">**清除行筛选器**</span><span class="sxs-lookup"><span data-stu-id="82a82-117">**Clear Row Filters**</span></span>  
 <span data-ttu-id="82a82-118">删除已应用于列中数据的所有筛选器。</span><span class="sxs-lookup"><span data-stu-id="82a82-118">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
