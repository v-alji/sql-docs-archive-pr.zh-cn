---
title: 下次提取位置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
ms.openlocfilehash: fcc771eef4acf603148bc4b4318e810b1bd72302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687828"
---
# <a name="next-fetch-position"></a><span data-ttu-id="e0df1-102">下次提取位置</span><span class="sxs-lookup"><span data-stu-id="e0df1-102">Next Fetch Position</span></span>
  <span data-ttu-id="e0df1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序跟踪下一个提取位置，以便对**GetNextRows**方法的调用序列 (无需跳过、方向更改或对**FindNextRow**、 **Seek**或**RestartPosition**方法的干预调用，) 读取整个行集，而无需跳过或重复任何行。</span><span class="sxs-lookup"><span data-stu-id="e0df1-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider keeps track of the next fetch position so that a sequence of calls to the **GetNextRows** method (without skips, changes of direction, or intervening calls to the **FindNextRow**, **Seek**, or **RestartPosition** methods) reads the whole rowset without skipping or repeating any row.</span></span> <span data-ttu-id="e0df1-104">可以通过调用 IRowset::GetNextRows、IRowset::RestartPosition 或 IRowsetIndex::Seek，或通过调用 FindNextRow 且 pBookmark 值为空来更改下次提取位置\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0df1-104">The next fetch position is changed either by calling **IRowset::GetNextRows**, **IRowset::RestartPosition**, or **IRowsetIndex::Seek**, or by calling **FindNextRow** with a null *pBookmark* value.</span></span> <span data-ttu-id="e0df1-105">调用 FindNextRow 且 pBookmark 值不为空时，不会影响下次提取位置\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0df1-105">Calling **FindNextRow** with a nonnull *pBookmark* value does not affect the next fetch position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0df1-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0df1-106">See Also</span></span>  
 [<span data-ttu-id="e0df1-107">提取行</span><span class="sxs-lookup"><span data-stu-id="e0df1-107">Fetching Rows</span></span>](fetching-rows.md)  
  
  
