---
title: 导入 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importing.f1
ms.assetid: f1681be4-c543-4e77-875d-b13eeb75cf77
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95ea60385014e5ca8b998b986a66c384f7151081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590418"
---
# <a name="importing-ssas"></a><span data-ttu-id="4c67e-102">导入 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="4c67e-102">Importing (SSAS)</span></span>
  <span data-ttu-id="4c67e-103">**“表导入向导”** 的这一页可用于查看导入操作的进度。</span><span class="sxs-lookup"><span data-stu-id="4c67e-103">This page of the **Table Import Wizard** enables you to view the progress of the import operation.</span></span> <span data-ttu-id="4c67e-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="4c67e-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4c67e-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="4c67e-105">UI element list</span></span>  
 <span data-ttu-id="4c67e-106">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="4c67e-106">**Details**</span></span>  
 <span data-ttu-id="4c67e-107">为每个数据导入操作显示以下信息。</span><span class="sxs-lookup"><span data-stu-id="4c67e-107">Displays the following information for each data import operation.</span></span>  
  
|<span data-ttu-id="4c67e-108">列</span><span class="sxs-lookup"><span data-stu-id="4c67e-108">Column</span></span>|<span data-ttu-id="4c67e-109">说明</span><span class="sxs-lookup"><span data-stu-id="4c67e-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4c67e-110">**工作项**</span><span class="sxs-lookup"><span data-stu-id="4c67e-110">**Work Item**</span></span>|<span data-ttu-id="4c67e-111">显示要导入的表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="4c67e-111">Displays the name of the table or view that is being imported.</span></span>|  
|<span data-ttu-id="4c67e-112">**Status**</span><span class="sxs-lookup"><span data-stu-id="4c67e-112">**Status**</span></span>|<span data-ttu-id="4c67e-113">指示表或视图是否已成功导入以及已导入的行数。</span><span class="sxs-lookup"><span data-stu-id="4c67e-113">Indicates whether the table or view was successfully imported and the number of rows that were imported.</span></span>|  
|<span data-ttu-id="4c67e-114">**Message**</span><span class="sxs-lookup"><span data-stu-id="4c67e-114">**Message**</span></span>|<span data-ttu-id="4c67e-115">如果表或视图的导入失败，则显示指向详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="4c67e-115">If the table or view import failed, displays a link to more information.</span></span> <span data-ttu-id="4c67e-116">在“详细信息”窗口中显示此信息。</span><span class="sxs-lookup"><span data-stu-id="4c67e-116">This information is displayed in the Details window.</span></span><br /><br /> <span data-ttu-id="4c67e-117">若要再次尝试导入表或视图，请退出该向导，然后再次运行它。</span><span class="sxs-lookup"><span data-stu-id="4c67e-117">To try again to import the table or view, exit the wizard and run it again.</span></span>|  
  
 <span data-ttu-id="4c67e-118">**停止导入**</span><span class="sxs-lookup"><span data-stu-id="4c67e-118">**Stop Import**</span></span>  
 <span data-ttu-id="4c67e-119">单击此项可使导入操作中途停止。</span><span class="sxs-lookup"><span data-stu-id="4c67e-119">Click to stop the import operation before it is finished.</span></span> <span data-ttu-id="4c67e-120">已导入的表和视图将显示在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 设计器中。</span><span class="sxs-lookup"><span data-stu-id="4c67e-120">Tables and views that have already been imported will be displayed in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] designer.</span></span> <span data-ttu-id="4c67e-121">但不会导入尚未导入的表和视图。</span><span class="sxs-lookup"><span data-stu-id="4c67e-121">Tables and views that have not been imported yet will not be imported.</span></span>  
  
  
