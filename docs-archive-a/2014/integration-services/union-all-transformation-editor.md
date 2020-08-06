---
title: Union All 转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7e84c106767aa897b2e419b51ca5b5c538501cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578935"
---
# <a name="union-all-transformation-editor"></a><span data-ttu-id="f432f-102">Union All 转换编辑器</span><span class="sxs-lookup"><span data-stu-id="f432f-102">Union All Transformation Editor</span></span>
  <span data-ttu-id="f432f-103">可以使用 **“Union All 转换编辑器”** 对话框，将多个输入行集合并到单个输出行集中。</span><span class="sxs-lookup"><span data-stu-id="f432f-103">Use the **Union All Transformation Editor** dialog box to merge several input rowsets into a single output rowset.</span></span> <span data-ttu-id="f432f-104">通过在数据流中包含 Union All 转换，可以从多个数据流合并数据、通过嵌套 Union All 转换来创建复杂数据集、以及在更正数据中的错误之后重新合并行。</span><span class="sxs-lookup"><span data-stu-id="f432f-104">By including the Union All transformation in a data flow, you can merge data from multiple data flows, create complex datasets by nesting Union All transformations, and re-merge rows after you correct errors in the data.</span></span>  
  
 <span data-ttu-id="f432f-105">若要了解有关 Union All 转换的详细信息，请参阅 [Union All Transformation](data-flow/transformations/union-all-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="f432f-105">To learn more about the Union All transformation, see [Union All Transformation](data-flow/transformations/union-all-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f432f-106">选项</span><span class="sxs-lookup"><span data-stu-id="f432f-106">Options</span></span>  
 <span data-ttu-id="f432f-107">**输出列名称**</span><span class="sxs-lookup"><span data-stu-id="f432f-107">**Output Column Name**</span></span>  
 <span data-ttu-id="f432f-108">为每一列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="f432f-108">Type an alias for each column.</span></span> <span data-ttu-id="f432f-109">默认值为第一个（引用）输入中输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="f432f-109">The default is the name of the input column from the first (reference) input; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="f432f-110">**Union All 输入 1**</span><span class="sxs-lookup"><span data-stu-id="f432f-110">**Union All Input 1**</span></span>  
 <span data-ttu-id="f432f-111">从第一个（引用）输入中可用输入列的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="f432f-111">Select from the list of available input columns in the first (reference) input.</span></span> <span data-ttu-id="f432f-112">映射的列的元数据必须匹配。</span><span class="sxs-lookup"><span data-stu-id="f432f-112">The metadata of mapped columns must match.</span></span>  
  
 <span data-ttu-id="f432f-113">**Union All 输入 n**</span><span class="sxs-lookup"><span data-stu-id="f432f-113">**Union All Input n**</span></span>  
 <span data-ttu-id="f432f-114">从第二个或其他输入中可用输入列的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="f432f-114">Select from the list of available input columns in the second and additional inputs.</span></span> <span data-ttu-id="f432f-115">映射的列的元数据必须匹配。</span><span class="sxs-lookup"><span data-stu-id="f432f-115">The metadata of mapped columns must match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f432f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f432f-116">See Also</span></span>  
 <span data-ttu-id="f432f-117">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f432f-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f432f-118">[使用 Union All 转换来合并数据](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f432f-118">[Merge Data by Using the Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span></span>  
 <span data-ttu-id="f432f-119">[合并转换](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f432f-119">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="f432f-120">合并联接转换</span><span class="sxs-lookup"><span data-stu-id="f432f-120">Merge Join Transformation</span></span>](data-flow/transformations/merge-join-transformation.md)  
  
  
