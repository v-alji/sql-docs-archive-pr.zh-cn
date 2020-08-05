---
title: "\"表属性\" 对话框 (SSAS-表格) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.TableProperties.f1
ms.assetid: 77571ccd-bdba-4e07-af55-465509dc6a33
author: minewiskan
ms.author: owend
ms.openlocfilehash: e3ca6d787616821532b30af0fe3591f79d6dbea6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580911"
---
# <a name="table-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="fb882-102">“表属性”对话框（SSAS - 表格）</span><span class="sxs-lookup"><span data-stu-id="fb882-102">Table Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="fb882-103">可以使用 **中的** “表属性” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框来查看表格模型数据库中的表的属性。</span><span class="sxs-lookup"><span data-stu-id="fb882-103">Use the **Table Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view the properties of a table in a tabular model database.</span></span> <span data-ttu-id="fb882-104">所有属性为只读属性。</span><span class="sxs-lookup"><span data-stu-id="fb882-104">All properties are read-only.</span></span>  
  
 <span data-ttu-id="fb882-105">在对象资源管理器中右键单击某个表，并选择“属性”，可以显示“表属性”对话框。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fb882-105">You can display the **Table Properties** dialog box by right-clicking a table in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fb882-106">选项</span><span class="sxs-lookup"><span data-stu-id="fb882-106">Options</span></span>  
  
|<span data-ttu-id="fb882-107">术语</span><span class="sxs-lookup"><span data-stu-id="fb882-107">Term</span></span>|<span data-ttu-id="fb882-108">定义</span><span class="sxs-lookup"><span data-stu-id="fb882-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="fb882-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="fb882-109">**Name**</span></span>|<span data-ttu-id="fb882-110">显示表的名称。</span><span class="sxs-lookup"><span data-stu-id="fb882-110">Displays the name of the table.</span></span>|  
|<span data-ttu-id="fb882-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="fb882-111">**ID**</span></span>|<span data-ttu-id="fb882-112">显示表的标识符。</span><span class="sxs-lookup"><span data-stu-id="fb882-112">Displays the identifier of the table.</span></span>|  
|<span data-ttu-id="fb882-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="fb882-113">**Description**</span></span>|<span data-ttu-id="fb882-114">显示表的说明。</span><span class="sxs-lookup"><span data-stu-id="fb882-114">Displays the description of the table.</span></span>|  
|<span data-ttu-id="fb882-115">**创建时间戳**</span><span class="sxs-lookup"><span data-stu-id="fb882-115">**Create Timestamp**</span></span>|<span data-ttu-id="fb882-116">显示表的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fb882-116">Displays the date and time the table was created.</span></span>|  
|<span data-ttu-id="fb882-117">**上次架构更新时间**</span><span class="sxs-lookup"><span data-stu-id="fb882-117">**Last Schema Update**</span></span>|<span data-ttu-id="fb882-118">显示表的元数据的上次更新日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fb882-118">Displays the date and time the metadata for the table was last updated.</span></span>|  
|<span data-ttu-id="fb882-119">**State**</span><span class="sxs-lookup"><span data-stu-id="fb882-119">**State**</span></span>|<span data-ttu-id="fb882-120">显示表的处理状态。</span><span class="sxs-lookup"><span data-stu-id="fb882-120">Displays the processing state of the table.</span></span> <span data-ttu-id="fb882-121">有关此属性的值的详细信息，请参阅 <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>。</span><span class="sxs-lookup"><span data-stu-id="fb882-121">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="fb882-122">**上次处理时间**</span><span class="sxs-lookup"><span data-stu-id="fb882-122">**Last Processed**</span></span>|<span data-ttu-id="fb882-123">显示表的上次处理日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fb882-123">Displays the date and time the table was last processed.</span></span>|  
|<span data-ttu-id="fb882-124">**当前存储模式**</span><span class="sxs-lookup"><span data-stu-id="fb882-124">**Current Storage Mode**</span></span>|<span data-ttu-id="fb882-125">显示表的当前存储模式。</span><span class="sxs-lookup"><span data-stu-id="fb882-125">Displays the current storage mode for the table.</span></span> <span data-ttu-id="fb882-126">存储模式在数据库级别设置并由所有表继承。</span><span class="sxs-lookup"><span data-stu-id="fb882-126">Storage mode is set at the database level and inherited by all tables.</span></span> <span data-ttu-id="fb882-127">无法使用表级别的其他存储模式。</span><span class="sxs-lookup"><span data-stu-id="fb882-127">You cannot use different storage modes at the table level.</span></span> <span data-ttu-id="fb882-128">有效值为 InMemory（默认值）、InMemoryWithDirectQuery、DirectQuery 和 DirectQueryWithinMemory。</span><span class="sxs-lookup"><span data-stu-id="fb882-128">Valid values are InMemory (default), InMemoryWithDirectQuery, DirectQuery, DirectQueryWithinMemory.</span></span>|  
  
  
