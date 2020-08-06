---
title: 创建新的关系挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b41dd3ac2e6144011c1b3acde27c4b5829a1661
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578530"
---
# <a name="create-a-new-relational-mining-structure"></a><span data-ttu-id="c7e61-102">创建新的关系挖掘结构</span><span class="sxs-lookup"><span data-stu-id="c7e61-102">Create a New Relational Mining Structure</span></span>
  <span data-ttu-id="c7e61-103">使用数据挖掘向导可以使用关系数据库或其他源中的数据创建新的挖掘结构，然后将该结构和任何相关模型保存到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中。</span><span class="sxs-lookup"><span data-stu-id="c7e61-103">Use the Data Mining Wizard to create a new mining structure, using data from a relational database or other source, and then save the structure and any related models to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="to-create-a-relational-mining-structure"></a><span data-ttu-id="c7e61-104">创建关系挖掘结构</span><span class="sxs-lookup"><span data-stu-id="c7e61-104">To create a relational mining structure</span></span>  
  
1.  <span data-ttu-id="c7e61-105">在解决方案资源管理器中，右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中的“挖掘结构”\*\*\*\* 文件夹，再单击“新建挖掘结构”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c7e61-105">In Solution Explorer, right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure**.</span></span>  
  
     <span data-ttu-id="c7e61-106">此时将打开数据挖掘向导。</span><span class="sxs-lookup"><span data-stu-id="c7e61-106">The Data Mining Wizard opens.</span></span>  
  
2.  <span data-ttu-id="c7e61-107">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="c7e61-108">在 **“选择定义方法”** 页中，选择 **“从现有关系数据库或数据仓库”**，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-108">On the **Select the Definition Method** page, select **From existing relational database or data warehouse**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c7e61-109">在 **“选择数据挖掘技术”** 页中，选择要使用的数据挖掘算法，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-109">On the **Select the Data Mining Technique** page, select the data mining algorithm that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="c7e61-110">有关数据挖掘算法的详细信息，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e61-110">For more information about data mining algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="c7e61-111">在 **“选择数据源视图”** 页中的 **“可用数据源视图”** 下，单击要使用的数据源视图，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-111">On the **Select Data Source View** page, under **Available data source views**, click the data source view that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="c7e61-112">有关创建数据源视图的详细信息，请参阅 [多维模型中的数据源视图](../multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e61-112">For more information about creating a data source view, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
6.  <span data-ttu-id="c7e61-113">在 **“指定表类型”** 页中的 **“输入表”** 下，选择一个事例表和一个嵌套表。</span><span class="sxs-lookup"><span data-stu-id="c7e61-113">On the **Specify Table Types** page, under **Input tables**, select a case table and a nested table.</span></span>  
  
7.  <span data-ttu-id="c7e61-114">在 **“指定定型数据”** 页中的 **“挖掘模型结构”** 下，选择键列、输入列和可预测列。</span><span class="sxs-lookup"><span data-stu-id="c7e61-114">On the **Specify the Training Data** page, under **Mining model structure**, select the key, input, and predictable columns.</span></span>  
  
     <span data-ttu-id="c7e61-115">选择可预测列后，可以单击 **“建议”** 按钮以打开 **“提供相关列建议”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c7e61-115">After you select the predictable column, you can click the **Suggest** button to open the **Suggest Related Columns** dialog box.</span></span> <span data-ttu-id="c7e61-116">在该对话框中，单击 **“确定”** 可以接受建议的列，以将所选列包含到挖掘结构中；也可以在 **“输入”** 列中先更改选择的列，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-116">You can accept the suggested columns by clicking **OK** in this dialog box to include the selected columns in the mining structure, or you can change the selections in the **Input** column first, and then click **OK**.</span></span> <span data-ttu-id="c7e61-117">若要忽略建议，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-117">To ignore the suggestions, click **Cancel**.</span></span>  
  
8.  <span data-ttu-id="c7e61-118">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c7e61-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="c7e61-119">在 **“指定列的内容和数据类型”** 页的 **“挖掘模型结构”** 下，可以调整每列的内容类型和数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7e61-119">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, you can adjust the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7e61-120">您可以单击 **“检测”** 以自动检测列包含的是连续数据还是离散数据。</span><span class="sxs-lookup"><span data-stu-id="c7e61-120">You can click **Detect** to automatically detect whether a column contains continuous or discrete data.</span></span> <span data-ttu-id="c7e61-121">单击该按钮后，系统即会更新 **“内容类型”** 和 **“数据类型”** 两列中的列内容类型和数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7e61-121">After you click this button, the column content and data types will be updated in the **Content Type** and **Data Type** columns.</span></span> <span data-ttu-id="c7e61-122">有关内容类型和数据类型的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)和[数据类型（数据挖掘）](data-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e61-122">For more information about content types and data types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md) and [Data Types &#40;Data Mining&#41;](data-types-data-mining.md).</span></span>  
  
10. <span data-ttu-id="c7e61-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c7e61-123">Click **Next**.</span></span>  
  
11. <span data-ttu-id="c7e61-124">在 **“完成向导”** 页中，为将要创建的挖掘结构和相关的初始挖掘模型提供一个名称，再单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="c7e61-124">On the **Completing the Wizard** page, provide a name for the mining structure and the related initial mining model that will be created, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e61-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7e61-125">See Also</span></span>  
 [<span data-ttu-id="c7e61-126">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="c7e61-126">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
