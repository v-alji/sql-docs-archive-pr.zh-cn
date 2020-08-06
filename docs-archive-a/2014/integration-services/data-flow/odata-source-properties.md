---
title: OData 源属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8139f79ed595ca3e6204f96823f6bc95e6fb40df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693408"
---
# <a name="odata-source-properties"></a><span data-ttu-id="01473-102">OData 源属性</span><span class="sxs-lookup"><span data-stu-id="01473-102">OData Source Properties</span></span>
  <span data-ttu-id="01473-103">在数据流中右键单击“OData 源”并单击“属性”时，将在“属性”窗口中看到“OData 源”组件的属性\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="01473-103">When you right-click **OData Source** in the data flow and click **Properties**, you will see properties for the **OData Source** component in the **Properties** window.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01473-104">属性</span><span class="sxs-lookup"><span data-stu-id="01473-104">Property</span></span>|<span data-ttu-id="01473-105">说明</span><span class="sxs-lookup"><span data-stu-id="01473-105">Description</span></span>|  
|<span data-ttu-id="01473-106">CollectionName</span><span class="sxs-lookup"><span data-stu-id="01473-106">CollectionName</span></span>|<span data-ttu-id="01473-107">要从 OData 服务检索的集合的名称。</span><span class="sxs-lookup"><span data-stu-id="01473-107">Name of the collection you wish to retrieve from the OData service.</span></span> <span data-ttu-id="01473-108">**“CollectionName”** 属性在 **UseResourcePath** 为 False 时使用。</span><span class="sxs-lookup"><span data-stu-id="01473-108">The **CollectionName** property is used when **UseResourcePath** is False.</span></span><br /><br /> <span data-ttu-id="01473-109">此属性能够使用表达式，从而可在运行时设置值。</span><span class="sxs-lookup"><span data-stu-id="01473-109">This property is expression-able, allowing the value to be set at runtime.</span></span> <span data-ttu-id="01473-110">但是，如果集合的元数据与设计时使用的元数据不匹配，会出现验证错误，从而导致数据流执行失败。</span><span class="sxs-lookup"><span data-stu-id="01473-110">However, if the metadata of the collection does not match the metadata that was used at design time, a validation error will occur, causing the data flow execution to fail.</span></span>|  
|<span data-ttu-id="01473-111">DefaultStringLength</span><span class="sxs-lookup"><span data-stu-id="01473-111">DefaultStringLength</span></span>|<span data-ttu-id="01473-112">此值为没有最大长度的字符串列指定默认长度。</span><span class="sxs-lookup"><span data-stu-id="01473-112">This value specifies default length for string columns that have no max length.</span></span><br /><br /> <span data-ttu-id="01473-113">**默认值：** 4000</span><span class="sxs-lookup"><span data-stu-id="01473-113">**Default:** 4000</span></span>|  
|<span data-ttu-id="01473-114">查询</span><span class="sxs-lookup"><span data-stu-id="01473-114">Query</span></span>|<span data-ttu-id="01473-115">OData 查询参数。</span><span class="sxs-lookup"><span data-stu-id="01473-115">The OData query parameters.</span></span> <span data-ttu-id="01473-116">此属性能够使用表达式，可以在运行时设置。</span><span class="sxs-lookup"><span data-stu-id="01473-116">This property is expression-able and can be set at runtime.</span></span>|  
|<span data-ttu-id="01473-117">ResourcePath</span><span class="sxs-lookup"><span data-stu-id="01473-117">ResourcePath</span></span>|<span data-ttu-id="01473-118">在需要指定完整资源路径（而不仅仅是选择集合名称）时使用此属性。</span><span class="sxs-lookup"><span data-stu-id="01473-118">Use this property when you need to specify a full resource path, rather than just selecting a collection name.</span></span> <span data-ttu-id="01473-119">此属性在 **UseResourcePath** 为 True 时使用。</span><span class="sxs-lookup"><span data-stu-id="01473-119">This property is used when **UseResourcePath** is True.</span></span>|  
|<span data-ttu-id="01473-120">UseResourcePath</span><span class="sxs-lookup"><span data-stu-id="01473-120">UseResourcePath</span></span>|<span data-ttu-id="01473-121">设置为 True 时， **ResourcePath** 值追加到基 URL 以确定 OData 馈送位置。</span><span class="sxs-lookup"><span data-stu-id="01473-121">When set to True, the **ResourcePath** value is appended to the base URL to determine the OData feed location.</span></span> <span data-ttu-id="01473-122">设置为 False 时 ，使用 **CollectionName** 值。</span><span class="sxs-lookup"><span data-stu-id="01473-122">When set to False, the **CollectionName** value is used.</span></span><br /><br /> <span data-ttu-id="01473-123">**默认值：** False</span><span class="sxs-lookup"><span data-stu-id="01473-123">**Default:** False</span></span>|  
  
  
