---
title: " (SSAS 表格) 从关系数据源导入 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93bb9ba9ba8d40262e4e90e840dcd15ac6826df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590421"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a><span data-ttu-id="4661e-102">从关系数据源导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="4661e-102">Import from a Relational Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="4661e-103">通过使用表导入向导，你可以从各种关系数据库导入数据。</span><span class="sxs-lookup"><span data-stu-id="4661e-103">You can import data from a variety of relational databases by using the Table Import Wizard.</span></span> <span data-ttu-id="4661e-104">该向导在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的“模型”菜单中提供 \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="4661e-104">The wizard is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Model** menu.</span></span> <span data-ttu-id="4661e-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="4661e-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="4661e-106">有关支持的数据源和提供程序的详细信息，请参阅 [支持的数据源（SSAS 表格）](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="4661e-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="4661e-107">“表导入向导”支持从以下数据源中导入数据：</span><span class="sxs-lookup"><span data-stu-id="4661e-107">The Table Import Wizard supports importing data from the following data sources:</span></span>  
  
 <span data-ttu-id="4661e-108">**关系数据库**</span><span class="sxs-lookup"><span data-stu-id="4661e-108">**Relational Databases**</span></span>  
  
-   <span data-ttu-id="4661e-109">Microsoft SQL Server 数据库</span><span class="sxs-lookup"><span data-stu-id="4661e-109">Microsoft SQL Server database</span></span>  
  
-   <span data-ttu-id="4661e-110">Microsoft SQL Azure</span><span class="sxs-lookup"><span data-stu-id="4661e-110">Microsoft SQL Azure</span></span>  
  
-   <span data-ttu-id="4661e-111">Microsoft Access 数据库</span><span class="sxs-lookup"><span data-stu-id="4661e-111">Microsoft Access database</span></span>  
  
-   <span data-ttu-id="4661e-112">Microsoft SQL Server Parallel Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="4661e-112">Microsoft SQL Server Parallel Data Warehouse</span></span>  
  
-   <span data-ttu-id="4661e-113">Oracle</span><span class="sxs-lookup"><span data-stu-id="4661e-113">Oracle</span></span>  
  
-   <span data-ttu-id="4661e-114">Teradata</span><span class="sxs-lookup"><span data-stu-id="4661e-114">Teradata</span></span>  
  
-   <span data-ttu-id="4661e-115">Sybase</span><span class="sxs-lookup"><span data-stu-id="4661e-115">Sybase</span></span>  
  
-   <span data-ttu-id="4661e-116">Informix</span><span class="sxs-lookup"><span data-stu-id="4661e-116">Informix</span></span>  
  
-   <span data-ttu-id="4661e-117">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="4661e-117">IBM DB2</span></span>  
  
-   <span data-ttu-id="4661e-118">OLE DB/ODBC</span><span class="sxs-lookup"><span data-stu-id="4661e-118">OLE DB/ODBC</span></span>  
  
 <span data-ttu-id="4661e-119">**多维源**</span><span class="sxs-lookup"><span data-stu-id="4661e-119">**Multidimensional Sources**</span></span>  
  
-   <span data-ttu-id="4661e-120">Microsoft SQL Server Analysis Services 多维数据集</span><span class="sxs-lookup"><span data-stu-id="4661e-120">Microsoft SQL Server Analysis Services cube</span></span>  
  
 <span data-ttu-id="4661e-121">“表导入向导”不支持从作为数据源的 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 工作簿导入数据。</span><span class="sxs-lookup"><span data-stu-id="4661e-121">The Table Import Wizard does not support importing data from a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Workbook as a data source.</span></span>  
  
### <a name="to-import-data-from-a-database"></a><span data-ttu-id="4661e-122">从数据库导入数据</span><span class="sxs-lookup"><span data-stu-id="4661e-122">To import data from a database</span></span>  
  
1.  <span data-ttu-id="4661e-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="4661e-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="4661e-124">在 **“连接数据源”** 页中，选择要连接到的数据库的类型，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="4661e-124">On the **Connect to a Data Source** page, select the type of database to connect to, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="4661e-125">执行表导入向导中的步骤。</span><span class="sxs-lookup"><span data-stu-id="4661e-125">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="4661e-126">在后续页上，您可以使用 **“选择表和视图”** 页或在 **“指定 SQL 查询”** 页上创建 SQL 查询来选择特定表和视图或者应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="4661e-126">On subsequent pages, you will be able to select specific tables and views or apply filters by using the **Select Tables and Views** page or by creating a SQL query on **Specify a SQL Query** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4661e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4661e-127">See Also</span></span>  
 <span data-ttu-id="4661e-128">[&#40;SSAS 表格&#41;导入数据](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4661e-128">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="4661e-129">支持的数据源（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="4661e-129">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
