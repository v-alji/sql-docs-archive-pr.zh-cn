---
title: 使用钻取检索 (MDX) 的源数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5601a3ddfa7075ed53330e12c260af88648db990
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587055"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a><span data-ttu-id="9a294-102">使用 DRILLTHROUGH 检索源数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="9a294-102">Using DRILLTHROUGH to Retrieve Source Data (MDX)</span></span>
  <span data-ttu-id="9a294-103">多维表达式 (MDX) 使用 [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)语句从多维数据集单元的源数据中检索行集。</span><span class="sxs-lookup"><span data-stu-id="9a294-103">Multidimensional Expressions (MDX) uses the [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)statement to retrieve a rowset from the source data for a cube cell.</span></span>  
  
 <span data-ttu-id="9a294-104">为了对多维数据集运行 `DRILLTHROUGH` 语句，必须为该多维数据集定义钻取操作。</span><span class="sxs-lookup"><span data-stu-id="9a294-104">In order to run a `DRILLTHROUGH` statement on a cube, a drillthrough action must be defined for that cube.</span></span> <span data-ttu-id="9a294-105">若要定义钻取操作，请在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]的多维数据集设计器中，在 **“操作”** 窗格的工具栏上单击 **“新建钻取操作”**。</span><span class="sxs-lookup"><span data-stu-id="9a294-105">To define a drillthrough action, in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], in Cube Designer, on the **Actions** pane, on the toolbar, click **New Drillthrough Action**.</span></span> <span data-ttu-id="9a294-106">在新的钻取操作中，指定 `DRILLTHROUGH` 语句返回的操作名称、目标、条件以及列。</span><span class="sxs-lookup"><span data-stu-id="9a294-106">In the new drillthrough action, specify the action name, target, condition, and the columns that are returned by a `DRILLTHROUGH` statement.</span></span>  
  
## <a name="drillthrough-statement-syntax"></a><span data-ttu-id="9a294-107">DRILLTHROUGH 语句的语法</span><span class="sxs-lookup"><span data-stu-id="9a294-107">DRILLTHROUGH Statement Syntax</span></span>  
 <span data-ttu-id="9a294-108">`DRILLTHROUGH` 语句使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="9a294-108">The `DRILLTHROUGH` statement uses the following syntax:</span></span>  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 <span data-ttu-id="9a294-109">`SELECT` 子句标识包含要检索的源数据的多维数据集单元。</span><span class="sxs-lookup"><span data-stu-id="9a294-109">The `SELECT` clause identifies the cube cell that contains the source data to be retrieved.</span></span> <span data-ttu-id="9a294-110">此 `SELECT` 子句与普通 MDX `SELECT` 语句基本相同，不同之处在于在 `SELECT` 子句中，只能在每个轴上指定一个成员。</span><span class="sxs-lookup"><span data-stu-id="9a294-110">This `SELECT` clause is the same to an ordinary MDX `SELECT` statement, except that in the `SELECT` clause only one member can be specified on each axis.</span></span> <span data-ttu-id="9a294-111">如果在一个轴上指定了多个成员，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="9a294-111">If more than one member is specified on an axis, an error occurs.</span></span>  
  
 <span data-ttu-id="9a294-112">`<Max_Rows>` 语法指定返回的每个行集中的最大行数。</span><span class="sxs-lookup"><span data-stu-id="9a294-112">The `<Max_Rows>` syntax specifies the maximum number of the rows in each returned rowset.</span></span> <span data-ttu-id="9a294-113">如果用于连接数据源的 OLE DB 访问接口不支持 `DBPROP_MAXROWS`，`<Max_Rows>` 设置将被忽略。</span><span class="sxs-lookup"><span data-stu-id="9a294-113">If the OLE DB provider that is used to connect to the data source does not support `DBPROP_MAXROWS`, the `<Max_Rows>` setting is ignored.</span></span>  
  
 <span data-ttu-id="9a294-114">`<First_Rowset>` 语法标识最先返回其行集的分区。</span><span class="sxs-lookup"><span data-stu-id="9a294-114">The `<First_Rowset>` syntax identifies the partition whose rowset is returned first.</span></span>  
  
 <span data-ttu-id="9a294-115">`<Return_Columns>` 语法标识要返回的基础数据库列。</span><span class="sxs-lookup"><span data-stu-id="9a294-115">The `<Return_Columns>` syntax identifies the underlying database columns to be returned.</span></span>  
  
## <a name="drillthrough-statement-example"></a><span data-ttu-id="9a294-116">DRILLTHROUGH 语句的示例</span><span class="sxs-lookup"><span data-stu-id="9a294-116">DRILLTHROUGH Statement Example</span></span>  
 <span data-ttu-id="9a294-117">下面的示例说明了 `DRILLTHROUGH` 语句的使用。</span><span class="sxs-lookup"><span data-stu-id="9a294-117">The following example demonstrates the use of the `DRILLTHROUGH` statement.</span></span> <span data-ttu-id="9a294-118">在此示例中，DRILLTHROUGH 语句沿着 Stores 维度（切片器轴）查询 Store 维度、Product 维度和 Time 维度的叶，然后返回部门度量值组、部门 ID 和员工的名字。</span><span class="sxs-lookup"><span data-stu-id="9a294-118">In this example, the DRILLTHROUGH statement queries the leaves of the Store, Product, and Time dimensions along the Stores dimension (the slicer axis), and then returns the department measure group, department ID, and employee's first name.</span></span>  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a294-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a294-119">See Also</span></span>  
 [<span data-ttu-id="9a294-120">操作数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="9a294-120">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
