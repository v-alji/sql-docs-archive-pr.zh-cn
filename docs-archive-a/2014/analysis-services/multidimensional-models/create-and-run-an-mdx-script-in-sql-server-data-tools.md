---
title: 在 SQL Server Data Tools 中创建和运行 MDX 脚本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], scripts
- scripts [Analysis Services], creating
- scripts [MDX], creating
ms.assetid: aa54b8cc-ff3b-4ef6-a64e-11b9e9d7fa11
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0c1088bd9920364d46117624673f27f09cf38b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577891"
---
# <a name="create-and-run-an-mdx-script-in-sql-server-data-tools"></a><span data-ttu-id="3be0c-102">在 SQL Server Data Tools 中创建和运行 MDX 脚本</span><span class="sxs-lookup"><span data-stu-id="3be0c-102">Create and Run an MDX Script in SQL Server Data Tools</span></span>
  <span data-ttu-id="3be0c-103">若要在  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中创建和运行 MDX 脚本，您需要使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 以及已创建并准备好编辑的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3be0c-103">To create and run an MDX Script in  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you need to be in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with a cube already created and ready for editing.</span></span>  
  
### <a name="to-create-a-multidimensional-expressions-mdx-script"></a><span data-ttu-id="3be0c-104">创建多维表达式 (MDX) 脚本</span><span class="sxs-lookup"><span data-stu-id="3be0c-104">To create a Multidimensional Expressions (MDX) script</span></span>  
  
1.  <span data-ttu-id="3be0c-105">打开要为其创建 MDX 脚本的多维数据集，然后在 **“视图”** 下单击 **“计算”**。</span><span class="sxs-lookup"><span data-stu-id="3be0c-105">Open the cube for which you want to create an MDX script, and under **View**, click **Calculations**.</span></span>  
  
2.  <span data-ttu-id="3be0c-106">如果不在 **“脚本视图”** 模式下，则单击 **“脚本视图”** 图标。</span><span class="sxs-lookup"><span data-stu-id="3be0c-106">If you are not in **Script View** mode, click the **Script View** icon.</span></span>  
  
3.  <span data-ttu-id="3be0c-107">在脚本窗口的 CALCULATE 命令下，键入 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="3be0c-107">In the script window, under the CALCULATE command, type an MDX expression.</span></span> <span data-ttu-id="3be0c-108">单击 **“检查语法”** 图标，确认表达式的语法正确无误。</span><span class="sxs-lookup"><span data-stu-id="3be0c-108">Click the **Check Syntax** icon and verify that the expression is syntactically correct.</span></span>  
  
4.  <span data-ttu-id="3be0c-109">若要运行 MDX 脚本，请使用新的 MDX 脚本更改来部署和处理多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3be0c-109">To run the MDX script, deploy and process the cube with the new MDX script changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be0c-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3be0c-110">See Also</span></span>  
 <span data-ttu-id="3be0c-111">[基本 MDX 脚本 &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="3be0c-111">[The Basic MDX Script &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md) </span></span>  
 <span data-ttu-id="3be0c-112">[MDX 脚本编写基础 &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3be0c-112">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="3be0c-113">MDX 脚本编写语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3be0c-113">MDX Scripting Statements &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-statements-mdx)  
  
  
