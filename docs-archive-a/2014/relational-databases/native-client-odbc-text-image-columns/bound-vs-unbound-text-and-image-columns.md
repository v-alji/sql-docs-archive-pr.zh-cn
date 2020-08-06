---
title: 绑定与未绑定的 Text 和 Image 列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: rothja
ms.author: jroth
ms.openlocfilehash: 20a91d26ac8c2d1201386cb19bde13b49a3dbada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693812"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a><span data-ttu-id="08caa-102">绑定与未绑定的 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="08caa-102">Bound vs. Unbound Text and Image Columns</span></span>
  <span data-ttu-id="08caa-103">使用服务器游标时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序会经过优化，以便在执行**SQLFetch**时不传输未绑定的**text**、 **ntext**或**image**列的数据。</span><span class="sxs-lookup"><span data-stu-id="08caa-103">When using server cursors, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is optimized to not transmit the data for unbound **text**, **ntext**, or **image** columns at the time **SQLFetch** is performed.</span></span> <span data-ttu-id="08caa-104">在应用程序为列发出[SQLGetData](../native-client-odbc-api/sqlgetdata.md)之前，不会实际从服务器中检索**text**、 **ntext**或**image**数据。</span><span class="sxs-lookup"><span data-stu-id="08caa-104">The **text**, **ntext**, or **image** data is not actually retrieved from the server until the application issues [SQLGetData](../native-client-odbc-api/sqlgetdata.md) for the column.</span></span>  
  
 <span data-ttu-id="08caa-105">许多应用程序都可以编写，这样用户只需在游标中上下滚动，就不会显示**text**、 **ntext**或**image**数据。</span><span class="sxs-lookup"><span data-stu-id="08caa-105">Many applications can be written so that no **text**, **ntext**, or **image** data is displayed while a user is simply scrolling up and down in a cursor.</span></span> <span data-ttu-id="08caa-106">当用户选择行来获取更多详细信息时，应用程序可以调用**SQLGetData**来检索**text**、 **ntext**或**image**数据。</span><span class="sxs-lookup"><span data-stu-id="08caa-106">When a user selects a row to get more detail, the application can then call **SQLGetData** to retrieve the **text**, **ntext**, or **image** data.</span></span> <span data-ttu-id="08caa-107">这会阻止为用户未选择的任何行传输**text**、 **ntext**或**image**数据，从而防止传输极大量的数据。</span><span class="sxs-lookup"><span data-stu-id="08caa-107">This will prevent transmitting the **text**, **ntext**, or **image** data for any of the rows the user does not select, and can therefore prevent the transmission of very large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08caa-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08caa-108">See Also</span></span>  
 <span data-ttu-id="08caa-109">[管理文本和图像列](managing-text-and-image-columns.md) </span><span class="sxs-lookup"><span data-stu-id="08caa-109">[Managing Text and Image Columns](managing-text-and-image-columns.md) </span></span>  
 [<span data-ttu-id="08caa-110">游标行为</span><span class="sxs-lookup"><span data-stu-id="08caa-110">Cursor Behaviors</span></span>](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
