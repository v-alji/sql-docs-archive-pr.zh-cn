---
title: 书签 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: rothja
ms.author: jroth
ms.openlocfilehash: be8e5486e5a442ddafa133a9cbd3f408d30a50d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692364"
---
# <a name="bookmarks"></a><span data-ttu-id="587fb-102">书签</span><span class="sxs-lookup"><span data-stu-id="587fb-102">Bookmarks</span></span>
  <span data-ttu-id="587fb-103">书签支持使用者快速返回到某行。</span><span class="sxs-lookup"><span data-stu-id="587fb-103">Bookmarks let consumers quickly return to a row.</span></span> <span data-ttu-id="587fb-104">利用书签，使用者可以根据书签值对行进行随机访问。</span><span class="sxs-lookup"><span data-stu-id="587fb-104">With bookmarks, consumers can access rows randomly based on the bookmark value.</span></span> <span data-ttu-id="587fb-105">行集中的列 0 为书签列。</span><span class="sxs-lookup"><span data-stu-id="587fb-105">The bookmark column is column 0 in the rowset.</span></span> <span data-ttu-id="587fb-106">使用者可将绑定结构的 dwFlag 字段值设置为 DBCOLUMNSINFO_ISBOOKMARK，以指示将该列用作书签。</span><span class="sxs-lookup"><span data-stu-id="587fb-106">The consumer sets the dwFlag field value of the binding structure to DBCOLUMNSINFO_ISBOOKMARK to indicate that the column is used as a bookmark.</span></span> <span data-ttu-id="587fb-107">使用者还可将行集属性 DBPROP_BOOKMARKS 设置为 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="587fb-107">The consumer also sets the rowset property DBPROP_BOOKMARKS to VARIANT_TRUE.</span></span> <span data-ttu-id="587fb-108">这样可使行集中包含列 0。</span><span class="sxs-lookup"><span data-stu-id="587fb-108">This lets column 0 be present in the rowset.</span></span> <span data-ttu-id="587fb-109">然后，可使用 IRowsetLocate::GetRowsAt 方法提取行（起始行的位置为书签加上一个偏移量得到的位置）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="587fb-109">The **IRowsetLocate::GetRowsAt** method is then used to fetch rows, starting with the row specified as an offset from a bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587fb-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="587fb-110">See Also</span></span>  
 [<span data-ttu-id="587fb-111">行集</span><span class="sxs-lookup"><span data-stu-id="587fb-111">Rowsets</span></span>](rowsets.md)  
  
  
