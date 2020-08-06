---
title: " (SSAS 表格) 的数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6908998b-9302-4a90-976e-770106b48d18
author: minewiskan
ms.author: owend
ms.openlocfilehash: d686d8100e30d7608e8d90f135022bdf46785723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690214"
---
# <a name="data-sources-ssas-tabular"></a><span data-ttu-id="50169-102">数据源（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-102">Data Sources (SSAS Tabular)</span></span>
  <span data-ttu-id="50169-103">数据源提供要包含在表格模型解决方案中的数据。</span><span class="sxs-lookup"><span data-stu-id="50169-103">Data sources provide the data to be included in a tabular model solution.</span></span> <span data-ttu-id="50169-104">您可以将数据从各种源导入您的模型，如关系数据库、数据馈送、多维数据源（如 Analysis Services 多维数据集）以及从文本文件（如 Microsoft Excel 工作簿）。</span><span class="sxs-lookup"><span data-stu-id="50169-104">You can import data into your model from a wide variety of sources such as relational databases, data feeds, multidimensional data sources such as an Analysis Services cube, and from text files such as a Microsoft Excel workbook.</span></span> <span data-ttu-id="50169-105">本节中的主题提供有关您可以从中导入的数据源类型、可以导入的各种数据类型以及说明如何从这些源导入数据的任务的信息。</span><span class="sxs-lookup"><span data-stu-id="50169-105">Topics in this section provide information about the types of data sources you can import from, the various data types you can import, and tasks describing how to import data from those sources.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="50169-106">相关主题和任务</span><span class="sxs-lookup"><span data-stu-id="50169-106">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="50169-107">主题</span><span class="sxs-lookup"><span data-stu-id="50169-107">Topic</span></span>|<span data-ttu-id="50169-108">说明</span><span class="sxs-lookup"><span data-stu-id="50169-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="50169-109">支持的数据源（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-109">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)|<span data-ttu-id="50169-110">本主题提供有关可以从中导入数据的不同数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="50169-110">This topic provides information about the different data sources that you can import data from.</span></span>|  
|[<span data-ttu-id="50169-111">支持的数据类型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-111">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-types-supported-ssas-tabular.md)|<span data-ttu-id="50169-112">本主题提供有关表格模型中支持的各种数据类型的信息。</span><span class="sxs-lookup"><span data-stu-id="50169-112">This topic provides information about the various data types that are supported in a Tabular Model.</span></span>|  
|[<span data-ttu-id="50169-113">模拟（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-113">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)|<span data-ttu-id="50169-114">本主题提供有关模拟的信息，该信息提供在连接到数据源以导入和刷新数据时 Analysis Services 使用的登录凭据。</span><span class="sxs-lookup"><span data-stu-id="50169-114">This topic provides information about impersonation, which provides logon credentials that are used by Analysis Services when connecting to a data source to import and refresh data.</span></span>|  
|[<span data-ttu-id="50169-115">导入数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-115">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)|<span data-ttu-id="50169-116">本节中的任务说明如何从不同的数据源导入数据。</span><span class="sxs-lookup"><span data-stu-id="50169-116">Tasks in this section describe how to import data from different data sources.</span></span>|  
|[<span data-ttu-id="50169-117">处理数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-117">Process Data &#40;SSAS Tabular&#41;</span></span>](process-data-ssas-tabular.md)|<span data-ttu-id="50169-118">本节中的任务说明如何处理（刷新）或更改已导入模型的数据。</span><span class="sxs-lookup"><span data-stu-id="50169-118">Tasks in this section describe how to process (refresh) or change data that has already been imported into a model.</span></span>|  
|[<span data-ttu-id="50169-119">编辑现有数据源连接（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="50169-119">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)|<span data-ttu-id="50169-120">说明如何编辑已创建并用于从源导入数据的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="50169-120">Describes how to edit a data source connection that has already been created and used to import data from a source.</span></span>|  
  
  
