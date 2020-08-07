---
title: 处理挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d25a927ae61ee5ffadf4ca21073a1c04cdb542
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690881"
---
# <a name="process-a-mining-structure"></a><span data-ttu-id="0725a-102">处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0725a-102">Process a Mining Structure</span></span>
  <span data-ttu-id="0725a-103">必须先部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目并处理挖掘结构和挖掘模型，然后才能浏览或使用与挖掘结构关联的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="0725a-103">Before you can browse or work with the mining models that are associated with a mining structure, you have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span> <span data-ttu-id="0725a-104">此外，如果更改了挖掘结构或挖掘模型，则系统会提示您重新对其进行部署和处理。</span><span class="sxs-lookup"><span data-stu-id="0725a-104">Also, if you make a change to the mining structure or mining models, you will be prompted to redeploy and process them.</span></span> <span data-ttu-id="0725a-105">处理 **中数据挖掘设计器的** “挖掘结构” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 选项卡中的结构时，也会处理所有关联的模型。</span><span class="sxs-lookup"><span data-stu-id="0725a-105">Processing the structure in the **Mining Structure** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] processes all the associated models.</span></span>  
  
 <span data-ttu-id="0725a-106">可以使用这些工具处理挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="0725a-106">You can process a mining structure by using these tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   <span data-ttu-id="0725a-107">XMLA：“处理”命令</span><span class="sxs-lookup"><span data-stu-id="0725a-107">XMLA: Process command</span></span>  
  
 <span data-ttu-id="0725a-108">有关如何处理单个模型的信息，请参阅 [处理挖掘模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="0725a-108">For information about how to process individual models, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a><span data-ttu-id="0725a-109">使用 SQL Server Data Tools 处理挖掘结构和所有关联的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="0725a-109">To process a mining structure and all associated mining models using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="0725a-110">从 **中的** “挖掘模型” **菜单项中，选择** “处理挖掘结构和所有模型” [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0725a-110">Select **Process Mining Structure and All Models** from the **Mining Model** menu item in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
     <span data-ttu-id="0725a-111">如果更改了结构，则在处理模型之前，系统会提示您重新部署该结构。</span><span class="sxs-lookup"><span data-stu-id="0725a-111">If you made changes to the structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="0725a-112">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="0725a-112">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="0725a-113">在 "**处理挖掘结构 \<structure> -** " 对话框中单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="0725a-113">Click **Run** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
     <span data-ttu-id="0725a-114">**“处理进度”** 对话框将打开以显示有关模型处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0725a-114">The **Process Progress** dialog box opens to display the details of model processing.</span></span>  
  
3.  <span data-ttu-id="0725a-115">模型处理完成后，在 **“处理进度”** 对话框中单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="0725a-115">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="0725a-116">在 "**处理挖掘结构 \<structure> -** " 对话框中单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="0725a-116">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0725a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0725a-117">See Also</span></span>  
 [<span data-ttu-id="0725a-118">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="0725a-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
