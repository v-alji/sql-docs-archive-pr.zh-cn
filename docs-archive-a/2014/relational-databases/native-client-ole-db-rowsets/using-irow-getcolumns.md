---
title: 使用 IRow::GetColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f323dda790946565bc0dbd63c9e1f9d17ac7494b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579561"
---
# <a name="using-irowgetcolumns"></a><span data-ttu-id="7f8e0-102">使用 IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="7f8e0-102">Using IRow::GetColumns</span></span>
  <span data-ttu-id="7f8e0-103">IRow 实现允许对列进行按顺序的只进访问\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f8e0-103">The **IRow** implementation allows forward-only sequential access to the columns.</span></span> <span data-ttu-id="7f8e0-104">可以一次调用 IRow::GetColumns 以访问行中的所有列，也可以多次调用 IRow::GetColumns，每次访问行中的几个列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f8e0-104">You can either access all the columns in the row with a single call to **IRow::GetColumns** or call **IRow::GetColumns** multiple times every time that you access several columns in the row.</span></span>  
  
 <span data-ttu-id="7f8e0-105">对 IRow::GetColumns 的多次调用不应当重叠\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f8e0-105">The multiple calls to **IRow::GetColumns** should not overlap.</span></span> <span data-ttu-id="7f8e0-106">例如，如果对 IRow::GetColumns 的第一次调用检索第 1、2 和 3 列，则对 IRow::GetColumns 的第二次调用应调用第 4、5 和 6 列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f8e0-106">For example, if the first call to **IRow::GetColumns** retrieves columns 1, 2, and 3, the second call to **IRow::GetColumns** should call for columns 4, 5, and 6.</span></span> <span data-ttu-id="7f8e0-107">如果后来对 IRow::GetColumns 的调用发生重叠，则状态标志（DBCOLUMNACCESS 中的 dwstatus 字段）将设置为 DBSTATUS_E_UNAVAILABLE\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f8e0-107">If later calls to **IRow::GetColumns** overlap, the status flag (dwstatus field in DBCOLUMNACCESS) is set to DBSTATUS_E_UNAVAILABLE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8e0-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f8e0-108">See Also</span></span>  
 [<span data-ttu-id="7f8e0-109">使用 IRow 提取单行</span><span class="sxs-lookup"><span data-stu-id="7f8e0-109">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
  
