---
title: 使用嵌套表数据作为准确性图表的输入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97d5bbd75d09b1a9e4276c4723ad6986dbabf9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577070"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a><span data-ttu-id="62734-102">使用嵌套表数据作为准确性图表的输入</span><span class="sxs-lookup"><span data-stu-id="62734-102">Using Nested Table Data as an Input for an Accuracy Chart</span></span>
  <span data-ttu-id="62734-103">在使用外部数据测试挖掘模型的准确性时，如果挖掘模型包含嵌套表，则外部数据也必须包含一个事例表和一个关联的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="62734-103">When you test the accuracy of a mining model by using external data, if the mining model contains nested tables, the external data must also contain a case table and an associated nested table.</span></span>  
  
 <span data-ttu-id="62734-104">本主题说明如何处理用于模型测试的嵌套表、如何在模型和外部数据中映射嵌套表和事例表，以及如何将筛选器应用到嵌套表。</span><span class="sxs-lookup"><span data-stu-id="62734-104">This topic describes how to work with nested tables used for model testing, how to map nested and case tables in the mode and in the external data, and how to apply a filter to a nested table.</span></span>  
  
 <span data-ttu-id="62734-105">使用嵌套表时，请记住以下技巧：</span><span class="sxs-lookup"><span data-stu-id="62734-105">When working with nested tables, keep in mind these tips:</span></span>  
  
-   <span data-ttu-id="62734-106">如果选择 **“使用挖掘模型测试事例”** 或 **“使用挖掘结构测试事例”** 选项，则无需指定事例表或嵌套表。</span><span class="sxs-lookup"><span data-stu-id="62734-106">If you select the option **Use mining model test cases** or **Use mining structure test cases**, you do not need to specify a case table or nested table.</span></span> <span data-ttu-id="62734-107">使用这些选项可将测试数据的定义存储在挖掘结构中，且可实现在您创建准确性图表时自动选择测试数据。</span><span class="sxs-lookup"><span data-stu-id="62734-107">With those options, the definition of the test data is stored in the mining structure and the test data is automatically selected when you create the accuracy chart.</span></span>  
  
-   <span data-ttu-id="62734-108">如果数据源中事例表和嵌套表之间的关系已存在，则挖掘结构中的列将自动映射到输入表中的同名列。</span><span class="sxs-lookup"><span data-stu-id="62734-108">If a relationship already exists between the case and nested table in the data source, the columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
-   <span data-ttu-id="62734-109">只有指定了事例表，才可选择嵌套表。</span><span class="sxs-lookup"><span data-stu-id="62734-109">You cannot select a nested table until you have specified the case table.</span></span> <span data-ttu-id="62734-110">此外，只有在挖掘模型也使用事例表和嵌套表结构时，才可以指定嵌套表作为输入。</span><span class="sxs-lookup"><span data-stu-id="62734-110">Also, you cannot specify a nested table as an input unless the mining model also uses a case table and nested table structure.</span></span>  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a><span data-ttu-id="62734-111">使用嵌套表作为准确性图表的输入</span><span class="sxs-lookup"><span data-stu-id="62734-111">Use a nested table as input to an accuracy chart</span></span>  
  
1.  <span data-ttu-id="62734-112">双击挖掘结构以在数据挖掘设计器中将其打开。</span><span class="sxs-lookup"><span data-stu-id="62734-112">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="62734-113">选择“挖掘准确性图表” \*\*\*\* 选项卡，然后选择“输入选择” \*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="62734-113">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="62734-114">在 **“选择要用于准确性图表的数据集”** 中，选择 **“指定其他数据集”** 选项。</span><span class="sxs-lookup"><span data-stu-id="62734-114">In **Select data set to be used for accuracy chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="62734-115">单击 "浏览" 按钮\*\* ( ... ") \*\*从当前服务器上的数据源视图列表中选择外部数据集。</span><span class="sxs-lookup"><span data-stu-id="62734-115">Click the browse button **(...)** to choose the external data set from a list of data source views on the current server.</span></span>  
  
5.  <span data-ttu-id="62734-116">单击“选择事例表” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62734-116">Click **Select Case Table**.</span></span> <span data-ttu-id="62734-117">在 **“选择表”** 对话框中，从包含事例数据的数据源视图中选择事例表，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="62734-117">In the **Select Table** dialog box, choose the table from the data source view that contains the case data, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="62734-118">单击 **“选择嵌套表”**。</span><span class="sxs-lookup"><span data-stu-id="62734-118">Click **Select Nested Table**.</span></span> <span data-ttu-id="62734-119">在 **“选择表”** 对话框中，选择包含嵌套数据的表，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="62734-119">In the **Select Table** dialog box, select the table that contains the nested data, and then click **OK**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="62734-120">如果需要修改嵌套表与事例表之间的关系，请单击 **“修改联接”** 以打开 **“创建关系”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="62734-120">If you need to modify the relationship between the nested table and the case table, click **Modify Join** to open the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62734-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62734-121">See Also</span></span>  
 <span data-ttu-id="62734-122">[选择和映射模型测试数据](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="62734-122">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="62734-123">将筛选器应用于模型测试数据</span><span class="sxs-lookup"><span data-stu-id="62734-123">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
  
