---
title: " (SSAS 表格) 中删除表格 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
ms.openlocfilehash: c72fa90426440c1be84318a15cf0d761ef16aca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589215"
---
# <a name="delete-a-table-ssas-tabular"></a><span data-ttu-id="83a59-102">删除表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="83a59-102">Delete a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="83a59-103">在模型设计器中，您可以删除不再需要的模型工作区数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="83a59-103">In the model designer, you can delete tables in your model workspace database that you no longer need.</span></span> <span data-ttu-id="83a59-104">删除表并不影响原始源数据，只会影响你已导入并且正在使用的数据。</span><span class="sxs-lookup"><span data-stu-id="83a59-104">Deleting a table does not affect the original source data, only the data that you imported and were working with.</span></span> <span data-ttu-id="83a59-105">您无法撤消对表的删除。</span><span class="sxs-lookup"><span data-stu-id="83a59-105">You cannot undo the deletion of a table.</span></span>  
  
### <a name="to-delete-a-table"></a><span data-ttu-id="83a59-106">删除表</span><span class="sxs-lookup"><span data-stu-id="83a59-106">To delete a table</span></span>  
  
-   <span data-ttu-id="83a59-107">对于想要删除的表，右键单击模型设计器底部的选项卡，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="83a59-107">Right-click the tab at the bottom of the model designer for the table that you want to delete, and then click **Delete**.</span></span>  
  
## <a name="considerations-when-deleting-tables"></a><span data-ttu-id="83a59-108">删除表时的注意事项</span><span class="sxs-lookup"><span data-stu-id="83a59-108">Considerations when Deleting Tables</span></span>  
  
-   <span data-ttu-id="83a59-109">在您删除一个表时，该表位于其上的整个选项卡都将被删除。</span><span class="sxs-lookup"><span data-stu-id="83a59-109">When you delete a table, the entire tab that the table was on is deleted.</span></span>  
  
-   <span data-ttu-id="83a59-110">如果任何度量值与该表相关联，则也将删除该度量值的定义。</span><span class="sxs-lookup"><span data-stu-id="83a59-110">If any measures were associated with that table, the definition of the measure will also be deleted.</span></span>  
  
-   <span data-ttu-id="83a59-111">如果您使用该表创建了任何计算列，则也删除该表中的列；其他表中使用已删除表中的列的任何计算列将显示一个错误。</span><span class="sxs-lookup"><span data-stu-id="83a59-111">If you created any calculated columns using that table, columns in that table are also deleted; any calculated columns in other tables that use columns from the deleted table will display an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a59-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83a59-112">See Also</span></span>  
 [<span data-ttu-id="83a59-113">表和列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="83a59-113">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tables-and-columns-ssas-tabular.md)  
  
  
