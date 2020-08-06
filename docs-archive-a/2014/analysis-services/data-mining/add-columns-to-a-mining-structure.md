---
title: 向挖掘结构中添加列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 093d78b36ab3aae6600b890a8137025c9dc9134e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588760"
---
# <a name="add-columns-to-a-mining-structure"></a><span data-ttu-id="f668c-102">向挖掘结构中添加列</span><span class="sxs-lookup"><span data-stu-id="f668c-102">Add Columns to a Mining Structure</span></span>
  <span data-ttu-id="f668c-103">在数据挖掘向导中定义了挖掘结构后，可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的数据挖掘设计器在挖掘结构中添加列。</span><span class="sxs-lookup"><span data-stu-id="f668c-103">Use Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to add columns to a mining structure after you have defined it in the Data Mining Wizard.</span></span> <span data-ttu-id="f668c-104">您可以添加用于定义挖掘结构的数据源视图中存在的任何列。</span><span class="sxs-lookup"><span data-stu-id="f668c-104">You can add any column that exists in the data source view that was used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f668c-105">您可以向挖掘结构中添加列的多个副本；不过，应避免在同一个模型中使用列的多个实例，以避免源列和派生列之间发生错误关联。</span><span class="sxs-lookup"><span data-stu-id="f668c-105">You can add multiple copies of columns to a mining structure; however, you should avoid using more than one instance of the column within the same model, to avoid false correlations between the source and the derived column.</span></span>  
  
### <a name="to-add-a-column-to-a-mining-structure"></a><span data-ttu-id="f668c-106">向挖掘结构中添加列</span><span class="sxs-lookup"><span data-stu-id="f668c-106">To add a column to a mining structure</span></span>  
  
1.  <span data-ttu-id="f668c-107">在数据挖掘设计器中选择 **“挖掘结构”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f668c-107">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="f668c-108">右键单击挖掘结构并选择“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f668c-108">Right-click the mining structure and select **Add a Column**.</span></span>  
  
     <span data-ttu-id="f668c-109">**“选择列”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="f668c-109">The **Select a Column** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f668c-110">在 **“源表”** 下，从数据源视图中选择列所在的表。</span><span class="sxs-lookup"><span data-stu-id="f668c-110">Under **Source table**, select the table in the data source view where the column resides.</span></span>  
  
4.  <span data-ttu-id="f668c-111">在 **“源列”** 下，选择要添加到挖掘结构中的列。</span><span class="sxs-lookup"><span data-stu-id="f668c-111">Under **Source column**, select the column that you want to add to the mining structure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="f668c-112">如果您添加的列已经存在，则结构中将会包含一个副本，并在其名称后追加“1”。</span><span class="sxs-lookup"><span data-stu-id="f668c-112">If you add a column that already exists, a copy will be included in the structure, and the name appended with a "1".</span></span> <span data-ttu-id="f668c-113">在挖掘结构列的 **“名称”** 属性中键入新名称，可以更改已复制列的名称，使之更具说明性。</span><span class="sxs-lookup"><span data-stu-id="f668c-113">You can change the name of the copied column to something more descriptive by typing a new name in the **Name** property of the mining structure column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f668c-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f668c-114">See Also</span></span>  
 [<span data-ttu-id="f668c-115">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="f668c-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
