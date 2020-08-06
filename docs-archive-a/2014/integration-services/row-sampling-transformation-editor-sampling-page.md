---
title: 行抽样转换编辑器 (抽样页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687983"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a><span data-ttu-id="ab2cb-102">行抽样转换编辑器（“抽样”页）</span><span class="sxs-lookup"><span data-stu-id="ab2cb-102">Row Sampling Transformation Editor (Sampling Page)</span></span>
  <span data-ttu-id="ab2cb-103">可以使用 **“行抽样转换编辑器”** 对话框，使用指定行数将部分输入拆分成样本。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-103">Use the **Row Sampling Transformation Editor** dialog box to split a portion of an input into a sample using a specified number of rows.</span></span> <span data-ttu-id="ab2cb-104">此转换将输入分成两个单独的输出。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="ab2cb-105">若要了解有关行抽样转换的详细信息，请参阅 [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-105">To learn more about the Row Sampling transformation, see [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab2cb-106">选项</span><span class="sxs-lookup"><span data-stu-id="ab2cb-106">Options</span></span>  
 <span data-ttu-id="ab2cb-107">**行数**</span><span class="sxs-lookup"><span data-stu-id="ab2cb-107">**Number of rows**</span></span>  
 <span data-ttu-id="ab2cb-108">指定输入中要用作样本的行数。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-108">Specify the number of rows from the input to use as a sample.</span></span>  
  
 <span data-ttu-id="ab2cb-109">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="ab2cb-110">**样本的输出名称**</span><span class="sxs-lookup"><span data-stu-id="ab2cb-110">**Sample output name**</span></span>  
 <span data-ttu-id="ab2cb-111">为包含抽样行的输出提供唯一名称。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="ab2cb-112">所提供的名称将在 SSIS 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-112">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="ab2cb-113">**未选中部分的输出名称**</span><span class="sxs-lookup"><span data-stu-id="ab2cb-113">**Unselected output name**</span></span>  
 <span data-ttu-id="ab2cb-114">为包含非抽样行的输出提供唯一名称。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="ab2cb-115">所提供的名称将在 SSIS 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-115">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="ab2cb-116">**使用以下随机种子**</span><span class="sxs-lookup"><span data-stu-id="ab2cb-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="ab2cb-117">指定随机数生成器的抽样种子，转换将使用该种子来创建样本。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="ab2cb-118">建议只在开发和测试过程中使用此选项。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="ab2cb-119">如果未指定随机种子，则转换将使用 Microsoft Windows 的时钟周期计数作为种子。</span><span class="sxs-lookup"><span data-stu-id="ab2cb-119">The transformation uses the Microsoft Windows tick count as a seed if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2cb-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab2cb-120">See Also</span></span>  
 <span data-ttu-id="ab2cb-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ab2cb-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="ab2cb-122">百分比抽样转换</span><span class="sxs-lookup"><span data-stu-id="ab2cb-122">Percentage Sampling Transformation</span></span>](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
