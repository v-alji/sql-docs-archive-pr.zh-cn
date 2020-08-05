---
title: 更改 (SSAS 表格) 的表、列或行筛选器映射 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: d8a597fb51804ea12caace63f3308b07bffc5899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580899"
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a><span data-ttu-id="d2f51-102">更改表、列或行筛选器映射（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="d2f51-102">Change table, column, or row filter mappings (SSAS Tabular)</span></span>
  <span data-ttu-id="d2f51-103">本主题介绍如何使用 **中的** “编辑表属性” [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]对话框来更改表、列或行筛选器映射。</span><span class="sxs-lookup"><span data-stu-id="d2f51-103">This topic describes how to change table, column, or row filter mappings by using the **Edit Table Properties** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="d2f51-104">根据您最初是通过从列表中选择表还是通过使用 SQL 查询导入数据的， **“编辑表属性”** 对话框中的选项将有所不同。</span><span class="sxs-lookup"><span data-stu-id="d2f51-104">Options in the **Edit Table Properties** dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span> <span data-ttu-id="d2f51-105">如果最初是通过从列表中选择数据来导入数据的，则 **“编辑表属性”** 对话框将显示“表预览”模式。</span><span class="sxs-lookup"><span data-stu-id="d2f51-105">If you originally imported the data by selecting from a list, the **Edit Table Properties** dialog box displays the Table Preview mode.</span></span> <span data-ttu-id="d2f51-106">这种模式仅显示源表的一个子集，即前五十行。</span><span class="sxs-lookup"><span data-stu-id="d2f51-106">This mode displays only a subset limited to the first fifty rows of the source table.</span></span> <span data-ttu-id="d2f51-107">如果最初是通过使用 SQL 语句来导入数据的，则 **“编辑表属性”** 对话框仅显示一条 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="d2f51-107">If you originally imported the data by using a SQL statement, the **Edit Table Properties** dialog box only displays a SQL statement.</span></span> <span data-ttu-id="d2f51-108">通过使用 SQL 查询语句，您可以通过设计筛选器或手动编辑 SQL 语句来检索行的子集。</span><span class="sxs-lookup"><span data-stu-id="d2f51-108">Using a SQL query statement, you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="d2f51-109">如果您将源更改为与当前表具有不同列的表，将显示一条消息以警告您列不相同。</span><span class="sxs-lookup"><span data-stu-id="d2f51-109">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="d2f51-110">然后，您必须选择要放在当前表中的列，并单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="d2f51-110">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="d2f51-111">您可以通过选中表左侧的复选框来替换整个表。</span><span class="sxs-lookup"><span data-stu-id="d2f51-111">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2f51-112">如果表有多个分区，则无法使用“编辑表属性”对话框更改行筛选器映射。</span><span class="sxs-lookup"><span data-stu-id="d2f51-112">If your table has more than one partition, you cannot use the Edit Table Properties dialog box to change row filter mappings.</span></span> <span data-ttu-id="d2f51-113">若要更改具有多个分区的表的行筛选器映射，请使用分区管理器。</span><span class="sxs-lookup"><span data-stu-id="d2f51-113">To change row filter mappings for tables with multiple partitions, use Partition Manager.</span></span> <span data-ttu-id="d2f51-114">有关详细信息，请参阅 [分区（SSAS 表格）](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f51-114">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a><span data-ttu-id="d2f51-115">更改表、列或行筛选器映射</span><span class="sxs-lookup"><span data-stu-id="d2f51-115">To change table, column, or row filter mappings</span></span>  
  
1.  <span data-ttu-id="d2f51-116">在模型设计器中，依次单击表、 **“表”** 菜单和 **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="d2f51-116">In the model designer, click the table, then click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="d2f51-117">在 **“编辑表属性”** 对话框中，找到包含筛选条件的列，然后单击列标题右侧的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="d2f51-117">In the **Edit Table Properties** dialog box, locate the column that contains the criteria you want to filter on, and then click the down arrow at the right of the column heading.</span></span>  
  
3.  <span data-ttu-id="d2f51-118">在 **“自动筛选”** 菜单中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="d2f51-118">In the **AutoFilter** menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="d2f51-119">在列值的列表中，选择或清除作为筛选依据的一个或多个值，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="d2f51-119">In the list of column values, select or clear one or more values to filter by, and then click OK.</span></span>  
  
         <span data-ttu-id="d2f51-120">如果值的数目极多，则可能无法在列表中显示各个项。</span><span class="sxs-lookup"><span data-stu-id="d2f51-120">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="d2f51-121">此时您将看到消息“项过多，无法显示。”</span><span class="sxs-lookup"><span data-stu-id="d2f51-121">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="d2f51-122">单击“数字筛选器”\*\*\*\* 或“文本筛选器”\*\*\*\*（根据列类型），然后单击比较运算符命令（如“等于”），或单击“自定义筛选器”。</span><span class="sxs-lookup"><span data-stu-id="d2f51-122">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as Equals), or click Custom Filter.</span></span> <span data-ttu-id="d2f51-123">在 **“自定义筛选器”** 对话框中，创建筛选器，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="d2f51-123">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
         <span data-ttu-id="d2f51-124">如果您执行了错误的操作并需要重新开始，请单击 **“清除行筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="d2f51-124">If you make a mistake and need to start over, click **Clear Row Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f51-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2f51-125">See Also</span></span>  
 [<span data-ttu-id="d2f51-126">“编辑表属性”对话框 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="d2f51-126">Edit Table Properties Dialog Box &#40;SSAS&#41;</span></span>](../edit-table-properties-dialog-box-ssas.md)  
  
  
