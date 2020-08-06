---
title: 缓存转换编辑器 (映射 "页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetransmap.f1
ms.assetid: ffd53f18-9646-458a-a84a-f2467d601ea5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb31e479ea98133da34dcbf257d59e70f4ffe8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589850"
---
# <a name="cache-transformation-editor-mappings-page"></a><span data-ttu-id="7417e-102">缓存转换编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="7417e-102">Cache Transformation Editor (Mappings Page)</span></span>
  <span data-ttu-id="7417e-103">可以使用 **“缓存转换编辑器”** 的 **“映射”** 页，将“缓存转换”转换中的输入列映射到缓存连接管理器中的目标列。</span><span class="sxs-lookup"><span data-stu-id="7417e-103">Use the **Mappings** page of the **Cache Transformation Editor** to map the input columns in the Cache Transform transformation to destination columns in the Cache connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7417e-104">每个输入列都必须映射到目标列，而且二者的列数据类型必须匹配。</span><span class="sxs-lookup"><span data-stu-id="7417e-104">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="7417e-105">否则， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 设计器将显示一则错误消息。</span><span class="sxs-lookup"><span data-stu-id="7417e-105">Otherwise, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
 <span data-ttu-id="7417e-106">若要了解有关缓存转换的详细信息，请参阅 [Cache Transform](data-flow/transformations/cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="7417e-106">To learn more about the Cache Transform, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
 <span data-ttu-id="7417e-107">若要了解有关缓存连接管理器的详细信息，请参阅 [Cache Connection Manager](connection-manager/cache-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7417e-107">To learn more about the Cache connection manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7417e-108">选项</span><span class="sxs-lookup"><span data-stu-id="7417e-108">Options</span></span>  
 <span data-ttu-id="7417e-109">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="7417e-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="7417e-110">查看可用输入列的列表。</span><span class="sxs-lookup"><span data-stu-id="7417e-110">View the list of available input columns.</span></span> <span data-ttu-id="7417e-111">使用拖放操作将可用输入列映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="7417e-111">Use a drag-and-drop operation to map available input columns to destination columns.</span></span>  
  
 <span data-ttu-id="7417e-112">还可以用键盘通过以下方法将输入列映射到目标列：突出显示 **“可用输入列”** 表中的某一列，按菜单键，然后选择 **“通过匹配名称映射项”**。</span><span class="sxs-lookup"><span data-stu-id="7417e-112">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="7417e-113">**可用目标列**</span><span class="sxs-lookup"><span data-stu-id="7417e-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="7417e-114">查看可用目标列的列表。</span><span class="sxs-lookup"><span data-stu-id="7417e-114">View the list of available destination columns.</span></span> <span data-ttu-id="7417e-115">使用拖放操作将可用目标列映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="7417e-115">Use a drag-and-drop operation to map available destination columns to input columns.</span></span>  
  
 <span data-ttu-id="7417e-116">还可以用键盘通过以下方法将输入列映射到目标列：突出显示 **“可用目标列”** 表中的某一列，按菜单键，然后选择 **“通过匹配名称映射项”**。</span><span class="sxs-lookup"><span data-stu-id="7417e-116">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Destination Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="7417e-117">**输入列**</span><span class="sxs-lookup"><span data-stu-id="7417e-117">**Input Column**</span></span>  
 <span data-ttu-id="7417e-118">查看本主题中以前选择的输入列。</span><span class="sxs-lookup"><span data-stu-id="7417e-118">View input columns selected earlier in this topic.</span></span> <span data-ttu-id="7417e-119">可以通过使用 **“可用输入列”** 列表来更改映射。</span><span class="sxs-lookup"><span data-stu-id="7417e-119">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="7417e-120">**目标列**</span><span class="sxs-lookup"><span data-stu-id="7417e-120">**Destination Column**</span></span>  
 <span data-ttu-id="7417e-121">查看每个可用的目标列。</span><span class="sxs-lookup"><span data-stu-id="7417e-121">View each available destination column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7417e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7417e-122">See Also</span></span>  
 [<span data-ttu-id="7417e-123">缓存转换编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="7417e-123">Cache Transformation Editor &#40;Connection Manager Page&#41;</span></span>](../../2014/integration-services/cache-transformation-editor-connection-manager-page.md)  
  
  
