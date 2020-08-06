---
title: 定义常规关系和常规关系属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4f49e219a85d5577fb1acddfe14e7afd3b105d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590397"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a><span data-ttu-id="f1362-102">定义常规关系和常规关系属性</span><span class="sxs-lookup"><span data-stu-id="f1362-102">Define a Regular Relationship and Regular Relationship Properties</span></span>
  <span data-ttu-id="f1362-103">在定义新的多维数据集维度或新的度量值组时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将试图检测是否存在常规关系并将维度用法设置为 `Regular`。</span><span class="sxs-lookup"><span data-stu-id="f1362-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a regular relationship exists and then set the dimension usage setting to `Regular`.</span></span> <span data-ttu-id="f1362-104">您可以在多维数据集设计器的 **“维度用法”** 选项卡中查看或编辑常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="f1362-104">You can view or edit a regular dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span>  
  
 <span data-ttu-id="f1362-105">当您定义多维数据集维度与度量值组的关系时，也会指定该关系的粒度属性。</span><span class="sxs-lookup"><span data-stu-id="f1362-105">When you define the relationship of a cube dimension to a measure group, you also specify the granularity attribute for that relationship.</span></span> <span data-ttu-id="f1362-106">粒度属性定义了该维度在多维数据集中可用的最低详细级别，此粒度属性通常是指维度的键属性。</span><span class="sxs-lookup"><span data-stu-id="f1362-106">The granularity attribute defines the lowest level of detail available in the cube for that dimension, which is generally the key attribute for the dimension.</span></span> <span data-ttu-id="f1362-107">但是，有时您可能希望将特定度量值组中特定多维数据集维度的粒度设置为其他粒度。</span><span class="sxs-lookup"><span data-stu-id="f1362-107">However, sometimes you may want to set the granularity of a particular cube dimension in a particular measure group to a different grain.</span></span> <span data-ttu-id="f1362-108">例如，如果您正在使用“销售配额”或“预算”度量值组，则可能希望将“时间”维度的粒度属性设置为“月”属性，而不是“日”属性。</span><span class="sxs-lookup"><span data-stu-id="f1362-108">For example, you may want to set the granularity attribute for the Time dimension to the Month attribute instead of to the Day attribute, if you are using a Sales Quotas or a Budget measure group.</span></span> <span data-ttu-id="f1362-109">当您将粒度属性指定为键属性以外的属性时，必须确保维度中的所有其他属性都能通过属性关系直接或间接地链接到该属性。</span><span class="sxs-lookup"><span data-stu-id="f1362-109">When you specify the granularity attribute to be an attribute other than the key attribute, you must guarantee that all other attributes in the dimension are directly or indirectly linked to this other attribute through attribute relationships.</span></span> <span data-ttu-id="f1362-110">如果不能， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将无法正确地聚合数据。</span><span class="sxs-lookup"><span data-stu-id="f1362-110">If not, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will be unable to aggregate data correctly.</span></span>  
  
  
