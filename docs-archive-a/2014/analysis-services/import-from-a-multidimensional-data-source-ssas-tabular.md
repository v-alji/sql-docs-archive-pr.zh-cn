---
title: " (SSAS 表格) 从多维数据源导入 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b26cc8ed7237f87fa5e23c6a2fd47e18de2c165
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590973"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a><span data-ttu-id="5a6b8-102">从多维数据源导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5a6b8-102">Import from a Multidimensional Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="5a6b8-103">可以使用 Analysis Services 多维数据集数据库作为表格模型的数据源。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-103">You can use an Analysis Services cube database as a data source for a tabular model.</span></span> <span data-ttu-id="5a6b8-104">为了从 Analysis Services 多维数据集导入数据，必须定义一个 MDX 查询以选择要导入的数据。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-104">In order to import data from an Analysis Services cube, you must define an MDX Query to select data to import.</span></span>  
  
 <span data-ttu-id="5a6b8-105">SQL Server Analysis Services 数据库包含的任意数据都可以导入到模型。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-105">Any data that is contained in a SQL Server Analysis Services database can be imported into a model.</span></span> <span data-ttu-id="5a6b8-106">可以提取维度的全部或一部分，也可以从多维数据集中获取切片和聚合，如当年的销售额总和（逐月列出）等。但是，应记住从多维数据集导入的所有数据都是平展的。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-106">You can extract all or part of a dimension, or get slices and aggregates from the cube, such as the sum of sales, month by month, for the current year, etc. However, you should keep in mind all data that you import from a cube is flattened.</span></span> <span data-ttu-id="5a6b8-107">因此，如果定义一个查询针对多个维度检索度量值，则在数据导入时，每个维度将单独占用一列。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-107">Therefore, if you define a query that retrieves measures along multiple dimensions, the data will be imported with each dimension in a separate column.</span></span>  
  
 <span data-ttu-id="5a6b8-108">Analysis Services 多维数据集版本必须是 SQL Server 2005、SQL Server 2008、SQL Server 2008 R2、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]或 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-108">Analysis Services cubes must be version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a><span data-ttu-id="5a6b8-109">从 Analysis Services 多维数据集导入数据</span><span class="sxs-lookup"><span data-stu-id="5a6b8-109">To import data from an Analysis Services cube</span></span>  
  
1.  <span data-ttu-id="5a6b8-110">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="5a6b8-111">在 **“连接到数据源”** 页中，选择 **Microsoft Analysis Services**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-111">On the **Connect to a Data Source** page, select **Microsoft Analysis Services**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="5a6b8-112">执行表导入向导中的步骤。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-112">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="5a6b8-113">可以在 **“指定 MDX 查询”** 页上指定 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-113">You will be able to specify an MDX query on the **Specify a MDX Query** page.</span></span> <span data-ttu-id="5a6b8-114">若要使用 MDX 查询设计器，请在“指定 MDX 查询”页上单击 **“设计”**。</span><span class="sxs-lookup"><span data-stu-id="5a6b8-114">To use the MDX Query Designer, on the Specify a MDX Query page, click **Design**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6b8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a6b8-115">See Also</span></span>  
 <span data-ttu-id="5a6b8-116">[&#40;SSAS 表格&#41;导入数据](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5a6b8-116">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="5a6b8-117">支持的数据源（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5a6b8-117">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
