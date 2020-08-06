---
title: 从挖掘结构中删除挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589967"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a><span data-ttu-id="fc01a-102">从挖掘结构中删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="fc01a-102">Delete a Mining Model from a Mining Structure</span></span>
  <span data-ttu-id="fc01a-103">您可以使用数据挖掘设计器、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 DMX 语句删除挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="fc01a-103">You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using DMX statements.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="fc01a-104">使用 SQL Server Data Tools 删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="fc01a-104">Delete a mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="fc01a-105">在 **中，选择** “挖掘模型” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡。</span><span class="sxs-lookup"><span data-stu-id="fc01a-105">Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc01a-106">右键单击要删除的模型，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc01a-106">Right-click the model that you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="fc01a-107">将打开 **“删除对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="fc01a-107">The **Delete Objects** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="fc01a-108">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fc01a-108">Click **OK**.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a><span data-ttu-id="fc01a-109">使用 SQL Server Management Studio 删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="fc01a-109">Delete a mining model using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="fc01a-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开包含模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="fc01a-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the model.</span></span>  
  
2.  <span data-ttu-id="fc01a-111">展开 **“挖掘结构”**，然后展开 **“挖掘模型”**。</span><span class="sxs-lookup"><span data-stu-id="fc01a-111">Expand **Mining Structures**, and then expand **Mining Models**.</span></span>  
  
3.  <span data-ttu-id="fc01a-112">右键单击要删除的模型，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc01a-112">Right-click the model you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="fc01a-113">删除模型并不删除定型数据，只删除定型时创建的元数据和所有模式。</span><span class="sxs-lookup"><span data-stu-id="fc01a-113">Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.</span></span>  
  
### <a name="delete-a-mining-model-using-dmx"></a><span data-ttu-id="fc01a-114">使用 DMX 删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="fc01a-114">Delete a mining model using DMX</span></span>  
  
-   [<span data-ttu-id="fc01a-115">删除挖掘模型 (DMX)</span><span class="sxs-lookup"><span data-stu-id="fc01a-115">DROP MINING MODEL &#40;DMX&#41;</span></span>](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a><span data-ttu-id="fc01a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc01a-116">See Also</span></span>  
 [<span data-ttu-id="fc01a-117">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="fc01a-117">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
