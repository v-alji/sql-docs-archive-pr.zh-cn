---
title: " (SSAS 表格) 的表属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9613609c42de8fd3a4aab7aec3208dfe3d31be4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692551"
---
# <a name="table-properties-ssas-tabular"></a><span data-ttu-id="56fda-102">表属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="56fda-102">Table Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="56fda-103">本主题介绍表格模型表属性。</span><span class="sxs-lookup"><span data-stu-id="56fda-103">This topic describes tabular model table properties.</span></span> <span data-ttu-id="56fda-104">此处所述的属性不同于“编辑表属性”对话框中的那些属性，后者可以定义从源导入哪些列。</span><span class="sxs-lookup"><span data-stu-id="56fda-104">The properties described here are different from those in the Edit Table Properties dialog box, which define which columns from the source are imported.</span></span>  
  
 <span data-ttu-id="56fda-105">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="56fda-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="56fda-106">表属性</span><span class="sxs-lookup"><span data-stu-id="56fda-106">Table Properties</span></span>](#bkmk_properties)  
  
-   [<span data-ttu-id="56fda-107">配置表属性设置</span><span class="sxs-lookup"><span data-stu-id="56fda-107">To configure table property settings</span></span>](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a><span data-ttu-id="56fda-108">表属性</span><span class="sxs-lookup"><span data-stu-id="56fda-108">Table Properties</span></span>  
 <span data-ttu-id="56fda-109">**基本**</span><span class="sxs-lookup"><span data-stu-id="56fda-109">**Basic**</span></span>  
  
|<span data-ttu-id="56fda-110">属性</span><span class="sxs-lookup"><span data-stu-id="56fda-110">Property</span></span>|<span data-ttu-id="56fda-111">默认设置</span><span class="sxs-lookup"><span data-stu-id="56fda-111">Default Setting</span></span>|<span data-ttu-id="56fda-112">说明</span><span class="sxs-lookup"><span data-stu-id="56fda-112">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="56fda-113">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="56fda-113">**Connection Name**</span></span>|\<connection name>|<span data-ttu-id="56fda-114">与表的数据源的连接的名称。</span><span class="sxs-lookup"><span data-stu-id="56fda-114">The name of the connection to the table's data source.</span></span><br /><br /> <span data-ttu-id="56fda-115">若要编辑连接，请单击该按钮。</span><span class="sxs-lookup"><span data-stu-id="56fda-115">To edit the connection, click the button.</span></span>|  
|<span data-ttu-id="56fda-116">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="56fda-116">**Hidden**</span></span>|<span data-ttu-id="56fda-117">错误</span><span class="sxs-lookup"><span data-stu-id="56fda-117">False</span></span>|<span data-ttu-id="56fda-118">指定是否在报表客户端字段列表中隐藏表。</span><span class="sxs-lookup"><span data-stu-id="56fda-118">Specifies whether the table is hidden from reporting client field lists.</span></span>|  
|<span data-ttu-id="56fda-119">**分区**</span><span class="sxs-lookup"><span data-stu-id="56fda-119">**Partitions**</span></span>||<span data-ttu-id="56fda-120">表的分区不能显示在 **“属性”** 窗口中。</span><span class="sxs-lookup"><span data-stu-id="56fda-120">Partitions for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="56fda-121">若要查看、创建或编辑分区，请单击该按钮以打开分区管理器。</span><span class="sxs-lookup"><span data-stu-id="56fda-121">To view, create, or edit partitions, click the button to open the Partition Manager.</span></span>|  
|<span data-ttu-id="56fda-122">**源数据**</span><span class="sxs-lookup"><span data-stu-id="56fda-122">**Source Data**</span></span>||<span data-ttu-id="56fda-123">表的源数据不能显示在 **“属性”** 窗口中。</span><span class="sxs-lookup"><span data-stu-id="56fda-123">Source data for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="56fda-124">若要查看或编辑源数据，请单击该按钮以打开“编辑表属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="56fda-124">To view or edit the source data, click the button to open the Edit Table Properties dialog box.</span></span>|  
|<span data-ttu-id="56fda-125">**表说明**</span><span class="sxs-lookup"><span data-stu-id="56fda-125">**Table Description**</span></span>||<span data-ttu-id="56fda-126">表的文本说明。</span><span class="sxs-lookup"><span data-stu-id="56fda-126">A text description for the table.</span></span><br /><br /> <span data-ttu-id="56fda-127">在 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]中，如果最终用户将光标置于字段列表的此表上方，则说明将以工具提示的形式出现。</span><span class="sxs-lookup"><span data-stu-id="56fda-127">In [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], if an end-user places the cursor over this table in the field list, the description appears as a tooltip.</span></span>|  
|<span data-ttu-id="56fda-128">**表名**</span><span class="sxs-lookup"><span data-stu-id="56fda-128">**Table Name**</span></span>|\<friendly name>|<span data-ttu-id="56fda-129">指定表的友好名称。</span><span class="sxs-lookup"><span data-stu-id="56fda-129">Specifies the table's friendly name.</span></span> <span data-ttu-id="56fda-130">当您使用“表导入向导”导入表时或在导入后的任意时间，可以指定表名。</span><span class="sxs-lookup"><span data-stu-id="56fda-130">The table name can be specified when a table is imported using the Table Import Wizard or at any time after import.</span></span> <span data-ttu-id="56fda-131">模型中的表名可以不同于源的相关表名。</span><span class="sxs-lookup"><span data-stu-id="56fda-131">The table name in the model can be different from the associated table at the source.</span></span> <span data-ttu-id="56fda-132">表的友好名称显示在报表客户端应用程序的字段列表以及 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的模型数据库中。</span><span class="sxs-lookup"><span data-stu-id="56fda-132">The table friendly name appears in the reporting client application field list as well as in the model database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
  
 <span data-ttu-id="56fda-133">**报表属性**</span><span class="sxs-lookup"><span data-stu-id="56fda-133">**Reporting Properties**</span></span>  
  
 <span data-ttu-id="56fda-134">有关报表属性的详细说明和配置信息，请参阅 [Power View 报表属性（SSAS 表格）](properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="56fda-134">For detailed descriptions and configuration information for reporting properties, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
|<span data-ttu-id="56fda-135">属性</span><span class="sxs-lookup"><span data-stu-id="56fda-135">Property</span></span>|<span data-ttu-id="56fda-136">默认设置</span><span class="sxs-lookup"><span data-stu-id="56fda-136">Default Setting</span></span>|<span data-ttu-id="56fda-137">说明</span><span class="sxs-lookup"><span data-stu-id="56fda-137">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="56fda-138">**默认字段集**</span><span class="sxs-lookup"><span data-stu-id="56fda-138">**Default Field Set**</span></span>|||  
|<span data-ttu-id="56fda-139">表行为</span><span class="sxs-lookup"><span data-stu-id="56fda-139">Table Behavior</span></span>|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a><span data-ttu-id="56fda-140">配置表属性设置</span><span class="sxs-lookup"><span data-stu-id="56fda-140">To configure table property settings</span></span>  
  
1.  <span data-ttu-id="56fda-141">在模型设计器中的数据视图中，单击某个表（选项卡）；或在关系图视图中，单击某个表头。</span><span class="sxs-lookup"><span data-stu-id="56fda-141">In the model designer, in Data View, click a table (tab), or, in Diagram View, click a table header.</span></span>  
  
2.  <span data-ttu-id="56fda-142">在 **“属性”** 窗口中，单击某个属性，然后键入值或单击其他配置选项的按钮。</span><span class="sxs-lookup"><span data-stu-id="56fda-142">In the **Properties** window, click on a property, and then type a value or click the button for additional configuration options.</span></span>  
  
  
