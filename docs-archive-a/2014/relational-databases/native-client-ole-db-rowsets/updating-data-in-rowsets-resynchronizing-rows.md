---
title: 重新同步行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 47c628ae583f3e635f422d5146f64508372a1114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579566"
---
# <a name="resynchronizing-rows"></a><span data-ttu-id="55cd0-102">重新同步行</span><span class="sxs-lookup"><span data-stu-id="55cd0-102">Resynchronizing Rows</span></span>
  <span data-ttu-id="55cd0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序仅**IRowsetResynch**支持支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 游标的行集上的 IRowsetResynch。</span><span class="sxs-lookup"><span data-stu-id="55cd0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IRowsetResynch** on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor-supported rowsets only.</span></span> <span data-ttu-id="55cd0-104">IRowsetResynch 并不是需要时就可用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="55cd0-104">**IRowsetResynch** is not available on demand.</span></span> <span data-ttu-id="55cd0-105">使用者在打开行集前必须请求该接口。</span><span class="sxs-lookup"><span data-stu-id="55cd0-105">The consumer must request the interface before opening the rowset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cd0-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55cd0-106">See Also</span></span>  
 [<span data-ttu-id="55cd0-107">更新行集中的数据</span><span class="sxs-lookup"><span data-stu-id="55cd0-107">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
