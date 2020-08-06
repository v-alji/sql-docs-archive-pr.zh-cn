---
title: IRowsetFind 的可比性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ad359ca4957b434c3798d1a441eb0fd57644a59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578867"
---
# <a name="comparability-for-irowsetfind"></a><span data-ttu-id="1ec8b-102">IRowsetFind 的可比性</span><span class="sxs-lookup"><span data-stu-id="1ec8b-102">Comparability for IRowsetFind</span></span>
  <span data-ttu-id="1ec8b-103">IRowsetFind 支持以下比较（仅限日期/时间类型）：</span><span class="sxs-lookup"><span data-stu-id="1ec8b-103">For date/time types only, IRowsetFind supports the following comparisons:</span></span>  
  
-   <span data-ttu-id="1ec8b-104">LT</span><span class="sxs-lookup"><span data-stu-id="1ec8b-104">LT</span></span>  
  
-   <span data-ttu-id="1ec8b-105">LE</span><span class="sxs-lookup"><span data-stu-id="1ec8b-105">LE</span></span>  
  
-   <span data-ttu-id="1ec8b-106">EQ</span><span class="sxs-lookup"><span data-stu-id="1ec8b-106">EQ</span></span>  
  
-   <span data-ttu-id="1ec8b-107">GE</span><span class="sxs-lookup"><span data-stu-id="1ec8b-107">GE</span></span>  
  
-   <span data-ttu-id="1ec8b-108">GT</span><span class="sxs-lookup"><span data-stu-id="1ec8b-108">GT</span></span>  
  
-   <span data-ttu-id="1ec8b-109">NE</span><span class="sxs-lookup"><span data-stu-id="1ec8b-109">NE</span></span>  
  
-   <span data-ttu-id="1ec8b-110">IGNORE</span><span class="sxs-lookup"><span data-stu-id="1ec8b-110">IGNORE</span></span>  
  
 <span data-ttu-id="1ec8b-111">如果试图进行其他任何比较，则将返回 DB_E_BADCOMPAREOP。</span><span class="sxs-lookup"><span data-stu-id="1ec8b-111">If any other comparison is attempted, DB_E_BADCOMPAREOP is returned.</span></span> <span data-ttu-id="1ec8b-112">这与 OLE DB 规范是一致的。</span><span class="sxs-lookup"><span data-stu-id="1ec8b-112">This is consistent with the OLE DB specification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec8b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ec8b-113">See Also</span></span>  
 [<span data-ttu-id="1ec8b-114">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1ec8b-114">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
