---
title: 筛选挖掘结构的源多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61409b4803f43d3ff2634daaba65a92bc343db36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579180"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a><span data-ttu-id="71c7a-102">筛选挖掘结构的源多维数据集</span><span class="sxs-lookup"><span data-stu-id="71c7a-102">Filter the Source Cube for a Mining Structure</span></span>
  <span data-ttu-id="71c7a-103">在创建基于多维模型中的数据 (OLAP 多维数据集) 的挖掘结构时，您可以对该挖掘结构所基于的多维数据集进行*切片*。</span><span class="sxs-lookup"><span data-stu-id="71c7a-103">When you create a mining structure that is based on data in a multidimensional model (an OLAP cube), you can *slice* the cube that the mining structure is based on.</span></span> <span data-ttu-id="71c7a-104">通过切片操作可创建数据子集，作为用于给挖掘模型定型的数据的一种筛选器。</span><span class="sxs-lookup"><span data-stu-id="71c7a-104">Slicing lets you create subsets of data, as a kind of filter on the data that is used to train the mining model.</span></span>  
  
### <a name="to-slice-a-cube"></a><span data-ttu-id="71c7a-105">对多维数据集进行切片</span><span class="sxs-lookup"><span data-stu-id="71c7a-105">To slice a cube</span></span>  
  
1.  <span data-ttu-id="71c7a-106">在的数据挖掘设计器中 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，选择 "**挖掘结构**" 选项卡或 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="71c7a-106">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="71c7a-107">在 "**挖掘模型**" 菜单上，选择 "**定义挖掘结构多维数据集切片**"。</span><span class="sxs-lookup"><span data-stu-id="71c7a-107">On the **Mining Model** menu, select **Define Mining Structure Cube Slice**.</span></span>  
  
     <span data-ttu-id="71c7a-108">此时将打开 "**切片多维数据集**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="71c7a-108">The **Slice Cube** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="71c7a-109">在 "**切片多维数据集**" 对话框的 "**维度**" 列中，选择要筛选的维度。</span><span class="sxs-lookup"><span data-stu-id="71c7a-109">In the **Dimension** column of the **Slice Cube** dialog box, select the dimension that you want to filter.</span></span>  
  
4.  <span data-ttu-id="71c7a-110">使用 "**层次结构**" 列中的列表选择层次结构的级别。</span><span class="sxs-lookup"><span data-stu-id="71c7a-110">Select a level of a hierarchy, using the list in the **Hierarchy** column.</span></span>  
  
5.  <span data-ttu-id="71c7a-111">从 "**运算符**" 列的列表中选择一个运算符，以便在生成筛选条件时使用。</span><span class="sxs-lookup"><span data-stu-id="71c7a-111">Select an operator from the list in the **Operator** column, to use in building the filter condition.</span></span>  
  
6.  <span data-ttu-id="71c7a-112">单击 "**筛选器**" 列中的框。</span><span class="sxs-lookup"><span data-stu-id="71c7a-112">Click the box in the **Filter** column.</span></span>  
  
     <span data-ttu-id="71c7a-113">此时将打开包含层次结构指定级别中的所有成员的对话框。</span><span class="sxs-lookup"><span data-stu-id="71c7a-113">A dialog box opens that contains all the members at the specified level of the hierarchy.</span></span>  
  
7.  <span data-ttu-id="71c7a-114">选择您要进行筛选的成员。</span><span class="sxs-lookup"><span data-stu-id="71c7a-114">Select the member or members on which you want to filter.</span></span>  
  
8.  <span data-ttu-id="71c7a-115">在 "成员" 对话框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="71c7a-115">Click **OK** in the member dialog box.</span></span>  
  
9. <span data-ttu-id="71c7a-116">在 "**切片多维数据集**" 对话框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="71c7a-116">Click **OK** in the **Slice Cube** dialog box.</span></span>  
  
     <span data-ttu-id="71c7a-117">现在根据多维数据集切片的定义对源多维数据集进行筛选。</span><span class="sxs-lookup"><span data-stu-id="71c7a-117">The source cube is now filtered as defined by the cube slice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c7a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71c7a-118">See Also</span></span>  
 <span data-ttu-id="71c7a-119">[挖掘结构任务和操作指南](data-mining/mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="71c7a-119">[Mining Structure Tasks and How-tos](data-mining/mining-structure-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="71c7a-120">创建新的 OLAP 挖掘结构</span><span class="sxs-lookup"><span data-stu-id="71c7a-120">Create a New OLAP Mining Structure</span></span>](data-mining/create-a-new-olap-mining-structure.md)  
  
  
