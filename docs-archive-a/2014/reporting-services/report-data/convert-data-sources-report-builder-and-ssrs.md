---
title: 将嵌入数据源转换为共享 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5827bab564b58e7a2b7922f01a33f550a6f523f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578653"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a><span data-ttu-id="f391f-102">将嵌入数据源转换为共享数据源（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f391f-102">Convert a Data Source from Embedded to Shared (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f391f-103">“报表数据”窗格中的每个数据源都是嵌入且特定于报表的，或者是共享的。</span><span class="sxs-lookup"><span data-stu-id="f391f-103">Each data source in the Report Data pane is embedded and specific to the report or is shared.</span></span> <span data-ttu-id="f391f-104">在报表生成器中，共享数据源将指向报表服务器或 SharePoint 站点上的已发布共享数据源。</span><span class="sxs-lookup"><span data-stu-id="f391f-104">In Report Builder, a shared data source points to a published shared data source on a report server or SharePoint site.</span></span> <span data-ttu-id="f391f-105">在报表设计器中，共享数据源将指向解决方案资源管理器中 **“共享数据源”** 文件夹下的某一共享数据源。</span><span class="sxs-lookup"><span data-stu-id="f391f-105">In Report Designer, a shared data source points to a shared data source in the **Shared Data Sources** folder in Solution Explorer.</span></span>  
  
 <span data-ttu-id="f391f-106">有关嵌入数据源与共享数据源之间的差异的详细信息，请参阅[嵌入和共享的数据连接或数据源（报表生成器和 SSRS）](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f391f-106">For more information about the differences between embedded and shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f391f-107">有关如何创建共享数据源的详细信息，请参阅[创建嵌入或共享数据源 (SSRS)](../create-an-embedded-or-shared-data-source-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f391f-107">For more information on how to create a shared data source, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a><span data-ttu-id="f391f-108">报表设计器</span><span class="sxs-lookup"><span data-stu-id="f391f-108">Report Designer</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="f391f-109">将嵌入数据源转换为共享数据源</span><span class="sxs-lookup"><span data-stu-id="f391f-109">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="f391f-110">在“报表数据”窗格中，右键单击数据源，然后单击“转换为共享数据源”  。</span><span class="sxs-lookup"><span data-stu-id="f391f-110">In the Report Data pane, right-click the data source, and then click **Convert to Shared Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f391f-111">如果“报表数据”窗格不可见，请单击 **“视图”** 菜单上的 **“报表数据”** 。</span><span class="sxs-lookup"><span data-stu-id="f391f-111">If the Report Data pane is not visible, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="f391f-112">如果“报表数据”窗格以浮动窗口形式打开，则请停靠该窗格。</span><span class="sxs-lookup"><span data-stu-id="f391f-112">If the pane opens as a floating window, you can dock it.</span></span> <span data-ttu-id="f391f-113">有关详细信息，请参阅[在报表设计器中停靠“报表数据”窗格 (SSRS)](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f391f-113">For more information, see [Dock the Report Data Pane in Report Designer &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).</span></span>  
  
     <span data-ttu-id="f391f-114">在“报表数据”窗格中，数据源图标将更改为共享数据源图标。</span><span class="sxs-lookup"><span data-stu-id="f391f-114">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span> <span data-ttu-id="f391f-115">在解决方案资源管理器中， **“共享数据源”** 文件夹中会出现一个同名的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="f391f-115">In Solution Explorer, a shared data source with the same name appears under the **Shared Data Source** folder.</span></span>  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="f391f-116">将共享数据源转换为嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="f391f-116">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="f391f-117">在“报表数据”窗格中，右键单击数据源，打开“数据源属性”对话框，然后单击“嵌入连接”   。</span><span class="sxs-lookup"><span data-stu-id="f391f-117">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="f391f-118">输入所需的信息。</span><span class="sxs-lookup"><span data-stu-id="f391f-118">Enter the required information.</span></span>  
  
     <span data-ttu-id="f391f-119">在“报表数据”窗格中，数据源图标将更改为共享数据源图标。</span><span class="sxs-lookup"><span data-stu-id="f391f-119">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="report-builder"></a><span data-ttu-id="f391f-120">报表生成器</span><span class="sxs-lookup"><span data-stu-id="f391f-120">Report Builder</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="f391f-121">将嵌入数据源转换为共享数据源</span><span class="sxs-lookup"><span data-stu-id="f391f-121">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="f391f-122">在“报表数据”窗格中，右键单击数据源以便打开“数据源属性”对话框，然后单击“嵌入连接”   。</span><span class="sxs-lookup"><span data-stu-id="f391f-122">In the Report Data pane, right-click the data source to open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="f391f-123">输入所需的信息。</span><span class="sxs-lookup"><span data-stu-id="f391f-123">Enter the required information.</span></span>  
  
     <span data-ttu-id="f391f-124">在“报表数据”窗格中，数据源图标将更改为共享数据源图标。</span><span class="sxs-lookup"><span data-stu-id="f391f-124">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="f391f-125">将共享数据源转换为嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="f391f-125">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="f391f-126">在“报表数据”窗格中，右键单击数据源，打开“数据源属性”对话框，然后单击“嵌入连接”   。</span><span class="sxs-lookup"><span data-stu-id="f391f-126">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="f391f-127">输入所需的信息。</span><span class="sxs-lookup"><span data-stu-id="f391f-127">Enter the required information.</span></span>  
  
     <span data-ttu-id="f391f-128">在“报表数据”窗格中，数据源图标将更改为共享数据源图标。</span><span class="sxs-lookup"><span data-stu-id="f391f-128">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f391f-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f391f-129">See Also</span></span>  
 <span data-ttu-id="f391f-130">[管理报表数据源](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="f391f-130">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="f391f-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f391f-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
