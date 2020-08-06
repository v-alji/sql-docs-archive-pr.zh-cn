---
title: 定义事实关系和事实关系属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689059"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a><span data-ttu-id="a6537-102">定义事实关系和事实关系属性</span><span class="sxs-lookup"><span data-stu-id="a6537-102">Define a Fact Relationship and Fact Relationship Properties</span></span>
  <span data-ttu-id="a6537-103">在定义新的多维数据集维度或新的度量值组时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将试图检测是否存在事实维度关系，然后将维度用法设置为 `Fact`。</span><span class="sxs-lookup"><span data-stu-id="a6537-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a fact dimension relationship exists and then set the dimension usage setting to `Fact`.</span></span> <span data-ttu-id="a6537-104">您可以在多维数据集设计器的 **“维度用法”** 选项卡中查看或编辑事实维度关系。</span><span class="sxs-lookup"><span data-stu-id="a6537-104">You can view or edit a fact dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="a6537-105">维度与度量值组之间的事实关系具有以下约束：</span><span class="sxs-lookup"><span data-stu-id="a6537-105">The fact relationship between a dimension and a measure group has the following constraints:</span></span>  
  
-   <span data-ttu-id="a6537-106">一个多维数据集维度与一个特定的度量值组只能具有一种事实关系。</span><span class="sxs-lookup"><span data-stu-id="a6537-106">A cube dimension can have only one fact relationship to a particular measure group.</span></span>  
  
-   <span data-ttu-id="a6537-107">一个多维数据集维度可以与多个度量值组分别具有单独的事实关系。</span><span class="sxs-lookup"><span data-stu-id="a6537-107">A cube dimension can have separate fact relationships to multiple measure groups.</span></span>  
  
-   <span data-ttu-id="a6537-108">关系的粒度属性必须是维度的键属性（例如事务号）。</span><span class="sxs-lookup"><span data-stu-id="a6537-108">The granularity attribute for the relationship must be the key attribute (such as Transaction Number) for the dimension.</span></span> <span data-ttu-id="a6537-109">这将在维度和事实数据表中的事实之间创建一对一的关系。</span><span class="sxs-lookup"><span data-stu-id="a6537-109">This creates a one-to-one relationship between the dimension and facts in the fact table.</span></span>  
  
  
