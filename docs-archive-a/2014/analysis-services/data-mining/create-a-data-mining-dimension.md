---
title: 创建数据挖掘维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 265cf671bbc825258f0b2bd6627690e8c52f252b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682447"
---
# <a name="create-a-data-mining-dimension"></a><span data-ttu-id="27f07-102">创建数据挖掘维度</span><span class="sxs-lookup"><span data-stu-id="27f07-102">Create a Data Mining Dimension</span></span>
  <span data-ttu-id="27f07-103">如果挖掘结构基于 OLAP 多维数据集，则可以创建包含挖掘模型内容的维度。</span><span class="sxs-lookup"><span data-stu-id="27f07-103">If your mining structure is based on an OLAP cube, you can create a dimension that contains the content of the mining model.</span></span> <span data-ttu-id="27f07-104">然后可以将维度合并回源多维数据集。</span><span class="sxs-lookup"><span data-stu-id="27f07-104">You can then incorporate the dimension back into the source cube.</span></span>  
  
 <span data-ttu-id="27f07-105">还可以浏览维度、使用维度浏览模型结果或使用 MDX 查询维度。</span><span class="sxs-lookup"><span data-stu-id="27f07-105">You can also browse the dimension, use it to explore the model results, or query the dimension using MDX.</span></span>  
  
### <a name="to-create-a-data-mining-dimension"></a><span data-ttu-id="27f07-106">创建数据挖掘维度</span><span class="sxs-lookup"><span data-stu-id="27f07-106">To create a data mining dimension</span></span>  
  
1.  <span data-ttu-id="27f07-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的数据挖掘设计器中，选择 **“挖掘结构”** 选项卡或 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="27f07-107">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], select either the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="27f07-108">从 **“挖掘模型”** 菜单中，选择 **“创建数据挖掘维度”**。</span><span class="sxs-lookup"><span data-stu-id="27f07-108">From the **Mining Model** menu, select **Create a Data Mining Dimension**.</span></span>  
  
     <span data-ttu-id="27f07-109">将打开 **“创建数据挖掘维度”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="27f07-109">The **Create Data Mining Dimension** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="27f07-110">在 **“创建数据挖掘维度”** 对话框的 **“模型名称”** 列表中，选择 OLAP 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="27f07-110">In the **Model name** list of the **Create Data Mining Dimension** dialog box, select an OLAP mining model.</span></span>  
  
4.  <span data-ttu-id="27f07-111">在 **“维度名称”** 框中，输入新的数据挖掘维度的名称。</span><span class="sxs-lookup"><span data-stu-id="27f07-111">In the **Dimension name** box, enter a name for the new data mining dimension.</span></span>  
  
5.  <span data-ttu-id="27f07-112">如果要创建包含新的数据挖掘维度的多维数据集，则选择 **“创建多维数据集”**。</span><span class="sxs-lookup"><span data-stu-id="27f07-112">If you want to create a cube that includes the new data mining dimension, select **Create cube**.</span></span> <span data-ttu-id="27f07-113">选择 **“创建多维数据集”** 之后，可以输入多维数据集的新名称。</span><span class="sxs-lookup"><span data-stu-id="27f07-113">After you select **Create cube**, you can enter a new name for the cube.</span></span>  
  
6.  <span data-ttu-id="27f07-114">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27f07-114">Click **OK**.</span></span>  
  
     <span data-ttu-id="27f07-115">这样便可创建数据挖掘维度并将其添加到解决方案资源管理器中的 **“维度”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="27f07-115">The data mining dimension is created and is added to the **Dimensions** folder in Solution Explorer.</span></span> <span data-ttu-id="27f07-116">如果选择了 **“创建多维数据集”**，则也可创建新的多维数据集并将其添加到 **“多维数据集”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="27f07-116">If you selected **Create cube**, a new cube is also created and is added to the **Cubes** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f07-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27f07-117">See Also</span></span>  
 [<span data-ttu-id="27f07-118">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="27f07-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
