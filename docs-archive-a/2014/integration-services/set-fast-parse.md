---
title: 设置快速分析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6ff2c6ecd536dd5ecc34dceb358ffcf578ff3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576889"
---
# <a name="set-fast-parse"></a><span data-ttu-id="a5b19-102">设置快速分析</span><span class="sxs-lookup"><span data-stu-id="a5b19-102">Set Fast Parse</span></span>
  <span data-ttu-id="a5b19-103">必须为使用快速分析的源或转换的每个列设置快速分析属性。</span><span class="sxs-lookup"><span data-stu-id="a5b19-103">The fast parse property must be set for each column of the source or transformation that uses fast parse.</span></span> <span data-ttu-id="a5b19-104">若要设置该属性，请使用平面文件源和数据转换的高级编辑器。</span><span class="sxs-lookup"><span data-stu-id="a5b19-104">To set the property, use the Advanced editor of the Flat File source and Data Conversion transformation.</span></span>  
  
### <a name="to-set-fast-parse"></a><span data-ttu-id="a5b19-105">设置快速分析</span><span class="sxs-lookup"><span data-stu-id="a5b19-105">To set fast parse</span></span>  
  
1.  <span data-ttu-id="a5b19-106">右键单击平面文件源或数据转换，然后单击“显示高级编辑器”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a5b19-106">Right-click the Flat File source or Data Conversion transformation, and then click **Show Advanced Editor**.</span></span>  
  
2.  <span data-ttu-id="a5b19-107">在 **“高级编辑器”** 对话框中，单击 **“输入属性和输出属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a5b19-107">In the **Advanced Editor** dialog box, click the **Input and Output Properties** tab.</span></span>  
  
3.  <span data-ttu-id="a5b19-108">在 **“输入和输出”** 窗格中，单击要为其启用快速分析的列。</span><span class="sxs-lookup"><span data-stu-id="a5b19-108">In the **Inputs and Outputs** pane, click the column for which you want to enable fast parse.</span></span>  
  
4.  <span data-ttu-id="a5b19-109">在属性窗口中，展开 "**自定义属性**" 节点，然后将 `FastParse` 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a5b19-109">In the Properties window, expand the **Custom Properties** node, and then set the `FastParse` property to `True`.</span></span>  
  
5.  <span data-ttu-id="a5b19-110">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a5b19-110">Click **OK**.</span></span>  
  
  
