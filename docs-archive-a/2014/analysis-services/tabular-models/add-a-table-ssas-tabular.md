---
title: " (SSAS 表格) 中添加表 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80c22c992a89ed2cb3db84809b47a7cd08cb514
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589228"
---
# <a name="add-a-table-ssas-tabular"></a><span data-ttu-id="20a6e-102">添加表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="20a6e-102">Add a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="20a6e-103">本主题介绍如何从曾将其中数据导入模型的数据源中添加表。</span><span class="sxs-lookup"><span data-stu-id="20a6e-103">This topic describes how to add a table from a data source from which you have previously imported data into your model.</span></span> <span data-ttu-id="20a6e-104">若要添加来自同一数据源的表，您可以使用现有的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="20a6e-104">To add a table from the same data source, you can use the existing data source connection.</span></span> <span data-ttu-id="20a6e-105">建议您在从单个数据源导入任意数量的表时始终使用单个连接。</span><span class="sxs-lookup"><span data-stu-id="20a6e-105">It is recommended you always use a single connection when importing any number of tables from a single data source.</span></span>  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a><span data-ttu-id="20a6e-106">从现有数据源添加表</span><span class="sxs-lookup"><span data-stu-id="20a6e-106">To add a table from an existing data source</span></span>  
  
1.  <span data-ttu-id="20a6e-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="20a6e-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="20a6e-108">在 **“现有连接”** 页中，选择指向要添加的表所在的数据源的连接，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="20a6e-108">On the **Existing Connections** page, select the connection to the data source that has the table you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="20a6e-109">在 **“选择表和视图”** 页上，从数据源中选择要添加到模型中的表。</span><span class="sxs-lookup"><span data-stu-id="20a6e-109">On the **Select Tables and Views** page, select the table from the data source you want to add to your model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20a6e-110">**“选择表和视图”** 页不会将以前导入的表显示为已选中。</span><span class="sxs-lookup"><span data-stu-id="20a6e-110">The **Select Tables and Views** page will not show tables that were previously imported as checked.</span></span>  <span data-ttu-id="20a6e-111">如果使用此连接选择以前曾导入的表，且以前未曾为该表指定不同的友好名称，则将向该友好名称追加一个数字 1。</span><span class="sxs-lookup"><span data-stu-id="20a6e-111">If you select a table that was previously imported using this connection, and you did not give the table a different friendly name, a 1 will be appended to the friendly name.</span></span> <span data-ttu-id="20a6e-112">无需重新选择以前使用此连接导入的任何表。</span><span class="sxs-lookup"><span data-stu-id="20a6e-112">You do not need to re-select any tables that were previously imported by using this connection.</span></span>  
  
4.  <span data-ttu-id="20a6e-113">如有必要，请使用“预览和筛选”以便仅选择特定列或对要导入的数据应用筛选器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="20a6e-113">If necessary, use **Preview & Filter** to select only certain columns or apply filters to the data to be imported.</span></span>  
  
5.  <span data-ttu-id="20a6e-114">单击 **“完成”** 导入新表。</span><span class="sxs-lookup"><span data-stu-id="20a6e-114">Click **Finish** to import the new table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20a6e-115">从单个数据源同时导入多个表时，这些表在数据源中所具备的任何表间关系都将在模型中自动创建。</span><span class="sxs-lookup"><span data-stu-id="20a6e-115">When importing multiple tables at the same time from a single data source, any relationships between those tables at the source will automatically be created in the model.</span></span> <span data-ttu-id="20a6e-116">但如果稍后添加表，则可能需要在模型中手动创建新添加的表和以前导入的表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="20a6e-116">When adding a table later; however, you may need to manually create relationships in the model between newly added tables and the tables that were previously imported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a6e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20a6e-117">See Also</span></span>  
 <span data-ttu-id="20a6e-118">[&#40;SSAS 表格&#41;导入数据](../import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="20a6e-118">[Import Data &#40;SSAS Tabular&#41;](../import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="20a6e-119">删除表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="20a6e-119">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)  
  
  
