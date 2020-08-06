---
title: 百分比抽样转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4dbd96ab952b6c88bdaa7bf56a0a2f1b3585c57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578286"
---
# <a name="percentage-sampling-transformation-editor"></a><span data-ttu-id="f633a-102">百分比抽样转换编辑器</span><span class="sxs-lookup"><span data-stu-id="f633a-102">Percentage Sampling Transformation Editor</span></span>
  <span data-ttu-id="f633a-103">可以使用 **“百分比抽样转换编辑器”** 对话框，使用指定的行百分比将部分输入拆分成样本。</span><span class="sxs-lookup"><span data-stu-id="f633a-103">Use the **Percentage Sampling Transformation Editor** dialog box to split part of an input into a sample using a specified percentage of rows.</span></span> <span data-ttu-id="f633a-104">此转换将输入分成两个单独的输出。</span><span class="sxs-lookup"><span data-stu-id="f633a-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="f633a-105">若要了解有关百分比抽样转换的详细信息，请参阅 [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="f633a-105">To learn more about the percentage sampling transformation, see [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f633a-106">选项</span><span class="sxs-lookup"><span data-stu-id="f633a-106">Options</span></span>  
 <span data-ttu-id="f633a-107">**行百分比**</span><span class="sxs-lookup"><span data-stu-id="f633a-107">**Percentage of rows**</span></span>  
 <span data-ttu-id="f633a-108">指定输入中要用作样本的行百分比。</span><span class="sxs-lookup"><span data-stu-id="f633a-108">Specify the percentage of rows in the input to use as a sample.</span></span>  
  
 <span data-ttu-id="f633a-109">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="f633a-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="f633a-110">**样本的输出名称**</span><span class="sxs-lookup"><span data-stu-id="f633a-110">**Sample output name**</span></span>  
 <span data-ttu-id="f633a-111">为包含抽样行的输出提供唯一名称。</span><span class="sxs-lookup"><span data-stu-id="f633a-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="f633a-112">所提供的名称将显示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中。</span><span class="sxs-lookup"><span data-stu-id="f633a-112">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="f633a-113">**未选中部分的输出名称**</span><span class="sxs-lookup"><span data-stu-id="f633a-113">**Unselected output name**</span></span>  
 <span data-ttu-id="f633a-114">为包含非抽样行的输出提供唯一名称。</span><span class="sxs-lookup"><span data-stu-id="f633a-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="f633a-115">所提供的名称将显示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中。</span><span class="sxs-lookup"><span data-stu-id="f633a-115">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="f633a-116">**使用以下随机种子**</span><span class="sxs-lookup"><span data-stu-id="f633a-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="f633a-117">指定随机数生成器的抽样种子，转换将使用该种子来创建样本。</span><span class="sxs-lookup"><span data-stu-id="f633a-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="f633a-118">建议只在开发和测试过程中使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f633a-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="f633a-119">如果未指定随机种子，转换将使用 Microsoft Windows 的时钟周期计数。</span><span class="sxs-lookup"><span data-stu-id="f633a-119">The transformation uses the Microsoft Windows tick count if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f633a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f633a-120">See Also</span></span>  
 <span data-ttu-id="f633a-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f633a-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="f633a-122">行抽样转换</span><span class="sxs-lookup"><span data-stu-id="f633a-122">Row Sampling Transformation</span></span>](data-flow/transformations/row-sampling-transformation.md)  
  
  
