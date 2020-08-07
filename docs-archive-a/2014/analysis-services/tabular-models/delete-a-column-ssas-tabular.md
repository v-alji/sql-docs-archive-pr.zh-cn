---
title: 删除 (SSAS 表格) 的列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06af0b7fd9879661db95bb2073cced545bb4eef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587619"
---
# <a name="delete-a-column-ssas-tabular"></a><span data-ttu-id="706ce-102">删除列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="706ce-102">Delete a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="706ce-103">本主题说明如何从表格模型表中删除列。</span><span class="sxs-lookup"><span data-stu-id="706ce-103">This topic describes how to delete a column from a tabular model table.</span></span>  
  
## <a name="delete-a-model-table-column"></a><span data-ttu-id="706ce-104">删除模型表列</span><span class="sxs-lookup"><span data-stu-id="706ce-104">Delete a Model Table Column</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="706ce-105">从模型表中删除列不会删除分区查询定义中的列。</span><span class="sxs-lookup"><span data-stu-id="706ce-105">Deleting a column from a model table does not delete the column from a partition query definition.</span></span> <span data-ttu-id="706ce-106">如果要删除的列是分区的一部分，则您必须手动从分区查询定义中删除该列。</span><span class="sxs-lookup"><span data-stu-id="706ce-106">If the column you are deleting is part of a partition, you must manually delete the column from the partition query definition.</span></span> <span data-ttu-id="706ce-107">从分区查询定义中删除该列失败将导致查询该列并返回数据，但在处理操作期间，不会将这些数据填入模型表。</span><span class="sxs-lookup"><span data-stu-id="706ce-107">Failure to delete the column from the partition query definition will cause the column to be queried and data returned, but not populated to the model table, during processing operations.</span></span> <span data-ttu-id="706ce-108">有关详细信息，请参阅 [分区（SSAS 表格）](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="706ce-108">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-delete-a-model-table-column"></a><span data-ttu-id="706ce-109">删除模型表列</span><span class="sxs-lookup"><span data-stu-id="706ce-109">To delete a model table column</span></span>  
  
-   <span data-ttu-id="706ce-110">在模型设计器中，在包含要删除的列的表中，右键单击该列，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="706ce-110">In the model designer, in the table that contains the column you want to delete, right-click on the column, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a><span data-ttu-id="706ce-111">使用“表属性”对话框删除模型表列</span><span class="sxs-lookup"><span data-stu-id="706ce-111">To delete a model table column by using the Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="706ce-112">在模型设计器中，依次单击包含要删除的列的表、 **“表”** 菜单和  **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="706ce-112">In the model designer, click on the table which contains the column you want to delete, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="706ce-113">在“列名来自”中，选择“模型”（如果与源不同，则使用模型表列名）。\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="706ce-113">In **Column names from**, select **Model** (*to use model table column names, if different from source*).</span></span>  
  
3.  <span data-ttu-id="706ce-114">在 **“编辑表属性”** 对话框的表预览窗口中，取消选中要删除的列，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="706ce-114">In the **Edit Table Properties** dialog box, in the table preview window, uncheck the column you want to delete, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706ce-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="706ce-115">See Also</span></span>  
 <span data-ttu-id="706ce-116">[将列添加到 &#40;SSAS 表格&#41;的表](add-columns-to-a-table-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="706ce-116">[Add Columns to a Table &#40;SSAS Tabular&#41;](add-columns-to-a-table-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="706ce-117">分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="706ce-117">Partitions &#40;SSAS Tabular&#41;</span></span>](partitions-ssas-tabular.md)  
  
  
