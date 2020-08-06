---
title: SQLGetCursorName |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 01ce6e42b4e8753d07309ec7ce298d4f743d4a6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576742"
---
# <a name="sqlgetcursorname"></a><span data-ttu-id="52c24-102">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="52c24-102">SQLGetCursorName</span></span>
  <span data-ttu-id="52c24-103">如果应用程序未指定游标名称，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序会在游标生成时为应用程序生成一个游标名称。</span><span class="sxs-lookup"><span data-stu-id="52c24-103">If the application does not specify a cursor name, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates one for the application upon cursor generation.</span></span> <span data-ttu-id="52c24-104">应用程序可以使用**SQLGetCursorName**来检索用于定位的 UPDATE 和 DELETE 语句的驱动程序定义的游标名称。</span><span class="sxs-lookup"><span data-stu-id="52c24-104">The application can use **SQLGetCursorName** to retrieve the driver-defined cursor name for positioned UPDATE and DELETE statements.</span></span> <span data-ttu-id="52c24-105">应用程序无需调用**SQLSetCursorName**来利用定位的数据操作语句。</span><span class="sxs-lookup"><span data-stu-id="52c24-105">The application does not need to call **SQLSetCursorName** to take advantage of positioned data manipulation statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c24-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52c24-106">See Also</span></span>  
 <span data-ttu-id="52c24-107">[SQLGetCursorName 函数](https://go.microsoft.com/fwlink/?LinkId=59349) </span><span class="sxs-lookup"><span data-stu-id="52c24-107">[SQLGetCursorName Function](https://go.microsoft.com/fwlink/?LinkId=59349) </span></span>  
 [<span data-ttu-id="52c24-108">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="52c24-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
