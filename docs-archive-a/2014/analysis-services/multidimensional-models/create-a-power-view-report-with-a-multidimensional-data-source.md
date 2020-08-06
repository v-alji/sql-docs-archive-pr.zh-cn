---
title: 使用多维数据源创建 Power View 报表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9b6f4c9-7e1f-4f61-b657-8986e39a6af2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 179bb9eed94cd0dbb579bdb06d630b213339d12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691963"
---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a><span data-ttu-id="d43fa-102">使用多维数据源创建 Power View 报表</span><span class="sxs-lookup"><span data-stu-id="d43fa-102">Create a Power View Report with a Multidimensional Data Source</span></span>
  <span data-ttu-id="d43fa-103">基于多维模型创建 Power View 报表与基于 PowerPivot 工作簿或 Analysis Services 表格模型创建报表没有什么不同。</span><span class="sxs-lookup"><span data-stu-id="d43fa-103">Creating a Power View report based on a multidimensional model is no different than creating a report based on a PowerPivot workbook or an Analysis Services Tabular model.</span></span> <span data-ttu-id="d43fa-104">从 SharePoint 库中的报表数据源连接文件 (.rsds) 创建 Power View 报表。</span><span class="sxs-lookup"><span data-stu-id="d43fa-104">Power View reports are created from a Report Data Source connection file (.rsds) in a SharePoint library.</span></span> <span data-ttu-id="d43fa-105">有关如何创建 .rsds 的详细信息，请参阅 [Create a Report Data Source](create-a-report-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="d43fa-105">For more information about how to create an .rsds, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
 <span data-ttu-id="d43fa-106">在开始之前，您需要知道：</span><span class="sxs-lookup"><span data-stu-id="d43fa-106">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="d43fa-107">SharePoint 库的名称和位置，该库包含到多维模型的共享报表数据源连接 (.rsds)。</span><span class="sxs-lookup"><span data-stu-id="d43fa-107">The name and location of the SharePoint library that contains a shared report data source connection (.rsds) to a multidimensional model.</span></span>  
  
#### <a name="create-a-new-blank-power-view-report"></a><span data-ttu-id="d43fa-108">创建新的空白 Power View 报表</span><span class="sxs-lookup"><span data-stu-id="d43fa-108">Create a new, blank Power View report</span></span>  
  
-   <span data-ttu-id="d43fa-109">在 SharePoint 库中，单击 .rsds 共享报表数据源连接（连接到多维模型的 .rsds）旁边的箭头，然后单击“创建 Power View 报表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d43fa-109">In the SharePoint library, click the arrow next to the .rsds shared report data source connection (the .rsds that connects to the multidimensional model), and then click **Create Power View Report**.</span></span>  
  
  
