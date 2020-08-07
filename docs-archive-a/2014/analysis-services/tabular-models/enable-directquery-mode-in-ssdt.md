---
title: " (SSAS 表格) 启用 DirectQuery 设计模式 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ccd2dc88f447e78f6558565a89accc341eac37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587616"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a><span data-ttu-id="90f86-102">启用 DirectQuery 设计模式（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="90f86-102">Enable DirectQuery Design Mode (SSAS Tabular)</span></span>
  <span data-ttu-id="90f86-103">若要在 DirectQuery 模式下创建模型，您必须首先更改设计时环境，以便该环境支持 DirectQuery 模式的用户。</span><span class="sxs-lookup"><span data-stu-id="90f86-103">To create a model in DirectQuery mode, you must first change the design-time environment so that it supports the user of DirectQuery mode.</span></span> <span data-ttu-id="90f86-104">当您这样做时，该设计器还将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="90f86-104">When you do so, the designer will also do the following:</span></span>  
  
-   <span data-ttu-id="90f86-105">启用 DirectQuery 部署属性。</span><span class="sxs-lookup"><span data-stu-id="90f86-105">Enable the use of the DirectQuery deployment properties.</span></span>  
  
-   <span data-ttu-id="90f86-106">更改工作区数据库，以便在使用缓存进行设计的混合模式下运行。</span><span class="sxs-lookup"><span data-stu-id="90f86-106">Change the workspace database to run in a hybrid mode that uses the cache for designing.</span></span> <span data-ttu-id="90f86-107">在您实际部署该模型时，该模式将更改回您在项目部署属性中指定的任何值。</span><span class="sxs-lookup"><span data-stu-id="90f86-107">When you actually deploy the model, the mode will be changed back to whatever value you specified in the project deployment properties.</span></span>  
  
-   <span data-ttu-id="90f86-108">禁用与 DirectQuery 模式不兼容的设计功能。</span><span class="sxs-lookup"><span data-stu-id="90f86-108">Disable design features that are incompatible with DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="90f86-109">验证现有模型。</span><span class="sxs-lookup"><span data-stu-id="90f86-109">Validate the existing model.</span></span>  
  
 <span data-ttu-id="90f86-110">此过程描述如何在设计器中启用 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="90f86-110">This procedure describes how to enable DirectQuery mode in the designer.</span></span>  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a><span data-ttu-id="90f86-111">在模型中启用 DirectQuery</span><span class="sxs-lookup"><span data-stu-id="90f86-111">To enable use of DirectQuery in a model</span></span>  
  
1.  <span data-ttu-id="90f86-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="90f86-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the solution file.</span></span>  
  
2.  <span data-ttu-id="90f86-113">在对象资源管理器中，双击 Model.bim 文件。</span><span class="sxs-lookup"><span data-stu-id="90f86-113">In Object Explorer, double-click the Model.bim file.</span></span>  
  
3.  <span data-ttu-id="90f86-114">在 **“属性”** 窗格中，将属性 **DirectQueryMode**更改为 **On**。</span><span class="sxs-lookup"><span data-stu-id="90f86-114">In the **Properties** pane, change the property, **DirectQueryMode**, to **On**.</span></span>  
  
4.  <span data-ttu-id="90f86-115">如果有错误，则在 Visual Studio 中打开**错误列表**并解决任何会阻止模型切换到 DirectQuery 模式的问题。</span><span class="sxs-lookup"><span data-stu-id="90f86-115">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being switched to DirectQuery mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f86-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90f86-116">See Also</span></span>  
 [<span data-ttu-id="90f86-117">DirectQuery 模式（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="90f86-117">DirectQuery Mode &#40;SSAS Tabular&#41;</span></span>](directquery-mode-ssas-tabular.md)  
  
  
