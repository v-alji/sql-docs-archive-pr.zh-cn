---
title: 定义分配和其他脚本命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 184c998bb4bd27d077cca78e792a7e7712f87666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589318"
---
# <a name="define-assignments-and-other-script-commands"></a><span data-ttu-id="6bb93-102">定义赋值和其他脚本命令</span><span class="sxs-lookup"><span data-stu-id="6bb93-102">Define Assignments and Other Script Commands</span></span>
  <span data-ttu-id="6bb93-103">在多维数据集设计器的“计算”\*\*\*\* 选项卡上，单击工具栏中的“新建脚本命令”\*\*\*\* 图标以创建空脚本。</span><span class="sxs-lookup"><span data-stu-id="6bb93-103">On the **Calculations** tab of Cube Designer, click the **New ScriptCommand** icon on the toolbar to create an empty script.</span></span> <span data-ttu-id="6bb93-104">创建新脚本时，该脚本最初在 "计算" 选项卡的 "**脚本组织**程序" 窗格中显示为空白。您在 "计算表达式" 窗格中键入的字符将在 "**脚本组织**程序" 中显示为项的名称。</span><span class="sxs-lookup"><span data-stu-id="6bb93-104">When you create a new script, it initially is displayed with a blank title in the **Script Organizer** pane of the Calculations tab. The characters you type in the Calculation Expressions pane will be visible as the name of the item in **Script Organizer**.</span></span> <span data-ttu-id="6bb93-105">因此，您可能要在第一行中键入被注释的名称，以更方便地标识 **“脚本组织程序”** 窗格中的脚本。</span><span class="sxs-lookup"><span data-stu-id="6bb93-105">Therefore, you may want to type a commented name on the first line to more easily identify the script in the **Script Organizer** pane.</span></span> <span data-ttu-id="6bb93-106">有关详细信息，请参阅 [对 Microsoft SQL Server 2005 中的 MDX 脚本编写的介绍](https://go.microsoft.com/fwlink/?LinkId=81892)。</span><span class="sxs-lookup"><span data-stu-id="6bb93-106">For more information, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span> <span data-ttu-id="6bb93-107">有关与 MDX 查询和计算相关的性能问题的详细信息，请参阅[SQL Server 2005 Analysis Services 性能指南](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的 "编写有效的 MDX" 一节。</span><span class="sxs-lookup"><span data-stu-id="6bb93-107">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6bb93-108">当您最初切换到多维数据集设计器的 **“计算”** 选项卡时， **“脚本组织程序”** 窗格将包含具有 CALCULATE 命令的单个脚本。</span><span class="sxs-lookup"><span data-stu-id="6bb93-108">When you initially switch to the **Calculations** tab of Cube Designer, the **Script Organizer** pane contains a single script with a CALCULATE command.</span></span> <span data-ttu-id="6bb93-109">CALCULATE 命令控制多维数据集中单元的聚合，仅当您要手动指定多维数据集的聚合方式时，才应编辑该命令。</span><span class="sxs-lookup"><span data-stu-id="6bb93-109">The CALCULATE command controls the aggregation of the cells in the cube and should be edited only if you intend to manually specify how the cube is to be aggregated.</span></span>  
  
 <span data-ttu-id="6bb93-110">可以使用“计算表达式”窗格以多维表达式 (MDX) 语法生成表达式。</span><span class="sxs-lookup"><span data-stu-id="6bb93-110">You can use the Calculation Expressions pane to build an expression in Multidimensional Expressions (MDX) syntax.</span></span> <span data-ttu-id="6bb93-111">生成表达式时，可以将多维数据集组件、函数和模板从 **“计算工具”** 窗格拖动或复制到“计算表达式”窗格。</span><span class="sxs-lookup"><span data-stu-id="6bb93-111">While you build the expression, you can drag or copy cube components, functions, and templates from the **Calculation Tools** pane to the Calculation Expressions pane.</span></span> <span data-ttu-id="6bb93-112">这种做法可以将项的脚本添加到“计算表达式”窗格中您放置或粘贴的位置。</span><span class="sxs-lookup"><span data-stu-id="6bb93-112">Doing so adds the script for the item to the Calculation Expressions pane in the location that you drop or paste it.</span></span> <span data-ttu-id="6bb93-113">用适当的值替换参数及其分隔符（« 和 »）。</span><span class="sxs-lookup"><span data-stu-id="6bb93-113">Replace arguments and their delimiters (« and ») with the appropriate values.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6bb93-114">当使用“计算表达式”窗格编写包含多个语句的表达式时，请确保 MDX 脚本中除最后一行外的所有行都以分号 (;) 结尾。</span><span class="sxs-lookup"><span data-stu-id="6bb93-114">When writing an expression that contains multiple statements using the Calculation Expressions pane, ensure that all lines except the last line of the MDX script end with a semi-colon (;).</span></span> <span data-ttu-id="6bb93-115">将计算串联为单个 MDX 脚本并且每个脚本后都追加一个分号，以确保 MDX 脚本可以正确编译。</span><span class="sxs-lookup"><span data-stu-id="6bb93-115">Calculations are concatenated into a single MDX script, and each script has a semi-colon appended to it to ensure that the MDX script compiles correctly.</span></span> <span data-ttu-id="6bb93-116">如果您在“计算表达式”窗格中为脚本的最后一行添加分号，多维数据集将会正确生成和部署，但不能对其运行查询。</span><span class="sxs-lookup"><span data-stu-id="6bb93-116">If you add a semi-colon to the last line of the script in the Calculation Expressions pane, the cube will build and deploy correctly but you will be unable to run queries against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb93-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bb93-117">See Also</span></span>  
 [<span data-ttu-id="6bb93-118">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="6bb93-118">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
