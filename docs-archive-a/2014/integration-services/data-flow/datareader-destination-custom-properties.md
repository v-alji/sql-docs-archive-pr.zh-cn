---
title: DataReader 目标自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62b6f628614d533e1bebcce071ce4761e73e08f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587518"
---
# <a name="datareader-destination-custom-properties"></a><span data-ttu-id="456d4-102">DataReader 目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="456d4-102">DataReader Destination Custom Properties</span></span>
  <span data-ttu-id="456d4-103">DataReader 目标具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="456d4-103">The DataReader destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="456d4-104">下表介绍了 DataReader 目标的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="456d4-104">The following table describes the custom properties of the DataReader destination.</span></span> <span data-ttu-id="456d4-105">除 `DataReader` 以外的所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="456d4-105">All properties except for `DataReader` are read/write.</span></span>  
  
|<span data-ttu-id="456d4-106">属性名称</span><span class="sxs-lookup"><span data-stu-id="456d4-106">Property name</span></span>|<span data-ttu-id="456d4-107">数据类型</span><span class="sxs-lookup"><span data-stu-id="456d4-107">Data Type</span></span>|<span data-ttu-id="456d4-108">说明</span><span class="sxs-lookup"><span data-stu-id="456d4-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="456d4-109">DataReader</span><span class="sxs-lookup"><span data-stu-id="456d4-109">DataReader</span></span>|<span data-ttu-id="456d4-110">String</span><span class="sxs-lookup"><span data-stu-id="456d4-110">String</span></span>|<span data-ttu-id="456d4-111">DataReader 目标的类名。</span><span class="sxs-lookup"><span data-stu-id="456d4-111">The class name of the DataReader destination.</span></span>|  
|<span data-ttu-id="456d4-112">FailOnTimeout</span><span class="sxs-lookup"><span data-stu-id="456d4-112">FailOnTimeout</span></span>|<span data-ttu-id="456d4-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="456d4-113">Boolean</span></span>|<span data-ttu-id="456d4-114">指示发生 `ReadTimeout` 时是否失败。</span><span class="sxs-lookup"><span data-stu-id="456d4-114">Indicates whether to fail when a `ReadTimeout` occurs.</span></span> <span data-ttu-id="456d4-115">此属性的默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="456d4-115">The default value of this property is **False**.</span></span>|  
|<span data-ttu-id="456d4-116">ReadTimeout</span><span class="sxs-lookup"><span data-stu-id="456d4-116">ReadTimeout</span></span>|<span data-ttu-id="456d4-117">Integer</span><span class="sxs-lookup"><span data-stu-id="456d4-117">Integer</span></span>|<span data-ttu-id="456d4-118">超时发生之前的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="456d4-118">The number of milliseconds before a time-out occurs.</span></span> <span data-ttu-id="456d4-119">此属性的默认值为 30000（30 秒）。</span><span class="sxs-lookup"><span data-stu-id="456d4-119">The default value of this property is 30000 (30 seconds).</span></span>|  
  
 <span data-ttu-id="456d4-120">DataReader 目标的输入和输入列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="456d4-120">The input and the input columns of the DataReader destination have no custom properties.</span></span>  
  
 <span data-ttu-id="456d4-121">有关详细信息，请参阅 [DataReader Destination](datareader-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="456d4-121">For more information, see [DataReader Destination](datareader-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456d4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="456d4-122">See Also</span></span>  
 [<span data-ttu-id="456d4-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="456d4-123">Common Properties</span></span>](../common-properties.md)  
  
  
