---
title: 从挖掘结构中删除列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ad1de08d57d00fd9798e1ceeddb85d146d7111
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577086"
---
# <a name="remove-columns-from-a-mining-structure"></a><span data-ttu-id="8cbfb-102">从挖掘结构中删除列</span><span class="sxs-lookup"><span data-stu-id="8cbfb-102">Remove Columns from a Mining Structure</span></span>
  <span data-ttu-id="8cbfb-103">在已创建挖掘结构后，可以使用数据挖掘设计器删除挖掘结构中的列。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-103">You can use Data Mining Designer to remove columns from a mining structure after the structure has already been created.</span></span> <span data-ttu-id="8cbfb-104">删除挖掘结构列的原因可能包括以下几种：</span><span class="sxs-lookup"><span data-stu-id="8cbfb-104">Reasons to remove a mining structure column might include the following:</span></span>  
  
-   <span data-ttu-id="8cbfb-105">挖掘结构包含某个列的多个副本并且您想要在模型中避免使用重复数据。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-105">The mining structure contains multiple copies of a column and you want to avoid the use of duplicate data in a model.</span></span>  
  
-   <span data-ttu-id="8cbfb-106">数据应受到保护，但启用了钻取功能。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-106">The data should be protected, but drillthrough has been enabled.</span></span>  
  
-   <span data-ttu-id="8cbfb-107">数据未在建模中使用并且不应处理。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-107">The data is unused in modeling and should not be processed.</span></span>  
  
 <span data-ttu-id="8cbfb-108">从挖掘结构中删除某一列并不会在数据源视图或外部数据中更改该列；只有元数据被删除。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-108">Deleting a column from the mining structure does not change the column in the data source view or in the external data; only metadata is deleted.</span></span> <span data-ttu-id="8cbfb-109">但在您更改在挖掘结构中使用的列时，必须重新处理挖掘结构以及基于该结构的所有模型。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-109">However, when you change the columns used in a mining structure, you must reprocess the structure and any models based on it.</span></span>  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a><span data-ttu-id="8cbfb-110">从挖掘结构中删除列</span><span class="sxs-lookup"><span data-stu-id="8cbfb-110">To remove a column from the mining structure</span></span>  
  
1.  <span data-ttu-id="8cbfb-111">在数据挖掘设计器中选择 **“挖掘结构”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-111">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="8cbfb-112">展开挖掘结构树，以显示所有列。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-112">Expand the tree for the mining structure, to show all the columns.</span></span>  
  
3.  <span data-ttu-id="8cbfb-113">右键单击要删除的列，再选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-113">Right-click the column that you want to delete, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="8cbfb-114">在 **“删除对象”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="8cbfb-114">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbfb-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cbfb-115">See Also</span></span>  
 [<span data-ttu-id="8cbfb-116">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="8cbfb-116">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
