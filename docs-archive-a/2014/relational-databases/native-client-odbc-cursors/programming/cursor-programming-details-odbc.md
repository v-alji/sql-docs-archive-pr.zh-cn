---
title: ODBC)  (的游标编程详细信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4108e195c16d321578a70852dd990f4f8d658832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580255"
---
# <a name="cursor-programming-details-odbc"></a><span data-ttu-id="d7ce8-102">游标编程详细信息 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d7ce8-102">Cursor Programming Details (ODBC)</span></span>
  <span data-ttu-id="d7ce8-103">选择正确的游标类型可提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="d7ce8-103">Choosing the correct cursor type can improve application performance.</span></span> <span data-ttu-id="d7ce8-104">在某些条件下，当请求的游标类型不支持执行的 SQL 语句时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以隐式转换游标类型。</span><span class="sxs-lookup"><span data-stu-id="d7ce8-104">Under certain conditions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may implicitly convert a cursor type when you execute an SQL statement that is not supported by the cursor type you requested.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7ce8-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="d7ce8-105">In This Section</span></span>  
  
-   [<span data-ttu-id="d7ce8-106">ODBC&#41;的隐式游标转换 &#40;</span><span class="sxs-lookup"><span data-stu-id="d7ce8-106">Implicit Cursor Conversions &#40;ODBC&#41;</span></span>](implicit-cursor-conversions-odbc.md)  
  
-   [<span data-ttu-id="d7ce8-107">通过 ODBC 游标使用自动提取</span><span class="sxs-lookup"><span data-stu-id="d7ce8-107">Using Autofetch with ODBC Cursors</span></span>](using-autofetch-with-odbc-cursors.md)  
  
-   [<span data-ttu-id="d7ce8-108">ODBC&#41;&#40;快速只进游标</span><span class="sxs-lookup"><span data-stu-id="d7ce8-108">Fast Forward-Only Cursors &#40;ODBC&#41;</span></span>](fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7ce8-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7ce8-109">See Also</span></span>  
 [<span data-ttu-id="d7ce8-110">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="d7ce8-110">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
