---
title: 更新行集中的数据 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: rothja
ms.author: jroth
ms.openlocfilehash: 993cfb67d4e6b72eec7cc0537e9b47371e94af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690591"
---
# <a name="updating-data-in-rowsets"></a><span data-ttu-id="b3495-102">更新行集中的数据</span><span class="sxs-lookup"><span data-stu-id="b3495-102">Updating Data in Rowsets</span></span>
  <span data-ttu-id="b3495-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当使用者更新包含数据的可修改行集时，Native Client OLE DB 提供程序更新数据。</span><span class="sxs-lookup"><span data-stu-id="b3495-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider updates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data when a consumer updates a modifiable rowset that contains that data.</span></span> <span data-ttu-id="b3495-104">当使用者请求支持 IRowsetChange 或 IRowsetUpdate 接口时，将创建一个可修改的行集\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3495-104">A modifiable rowset is created when the consumer requests support for either the **IRowsetChange** or **IRowsetUpdate** interface.</span></span>  
  
 <span data-ttu-id="b3495-105">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序可修改的行集使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 游标来支持行集。</span><span class="sxs-lookup"><span data-stu-id="b3495-105">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider-modifiable rowsets use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset.</span></span> <span data-ttu-id="b3495-106">行集属性 DBPROP_LOCKMODE 更改游标中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并发控制行为，并确定在可更新行集中提取行集的行和生成数据完整性错误的行为。</span><span class="sxs-lookup"><span data-stu-id="b3495-106">The rowset property DBPROP_LOCKMODE alters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency control behavior in cursors and determines the behavior of rowset row fetching and data integrity error generation in updatable rowsets.</span></span>  
  
 <span data-ttu-id="b3495-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持更新前后的行同步。</span><span class="sxs-lookup"><span data-stu-id="b3495-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports row synchronization before or after an update.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3495-108">可使用 IRowChange::SetColumns 设置行对象的一个或多个指定列的值。</span><span class="sxs-lookup"><span data-stu-id="b3495-108">IRowChange::SetColumns is available to set the values of one or more named columns of a row object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3495-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="b3495-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b3495-110">更新 SQL Server 游标中的数据</span><span class="sxs-lookup"><span data-stu-id="b3495-110">Updating Data in SQL Server Cursors</span></span>](updating-data-in-sql-server-cursors.md)  
  
-   [<span data-ttu-id="b3495-111">重新同步行</span><span class="sxs-lookup"><span data-stu-id="b3495-111">Resynchronizing Rows</span></span>](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3495-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3495-112">See Also</span></span>  
 [<span data-ttu-id="b3495-113">行集</span><span class="sxs-lookup"><span data-stu-id="b3495-113">Rowsets</span></span>](rowsets.md)  
  
  
