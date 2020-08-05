---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: rothja
ms.author: jroth
ms.openlocfilehash: dc3d86229501f80b25fb077788d1835a5f4f5c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581188"
---
# <a name="sqlcancel"></a><span data-ttu-id="30cfb-102">SQLCancel</span><span class="sxs-lookup"><span data-stu-id="30cfb-102">SQLCancel</span></span>
  <span data-ttu-id="30cfb-103">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)主题指出，在 ODBC 2.x 中，如果应用程序在对 `SQLCancel` 语句进行处理时调用，则 `SQLCancel` 具有与选项相同的效果 `SQLFreeStmt` `SQL_CLOSE` ; 仅为完整性定义此行为，应用程序应调用 `SQLFreeStmt` 或 `SQLCloseCursor` 关闭游标。</span><span class="sxs-lookup"><span data-stu-id="30cfb-103">The [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) topic says that in ODBC 2.x, if an application calls `SQLCancel` when no processing is being done on the statement, `SQLCancel` has the same effect as `SQLFreeStmt` with the `SQL_CLOSE` option; this behavior is defined only for completeness and applications should call `SQLFreeStmt` or `SQLCloseCursor` to close cursors.</span></span> <span data-ttu-id="30cfb-104">但是，即使您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 应用程序将 ODBC API 版本设置为 3.5.x 或更高版本，`SQLCancel` 函数也将使用 ODBC 2.x 行为。</span><span class="sxs-lookup"><span data-stu-id="30cfb-104">But even if your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client application sets the ODBC API version to be 3.5.x or later, the `SQLCancel` function will use the ODBC 2.x behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cfb-105">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30cfb-105">See Also</span></span>  
 <span data-ttu-id="30cfb-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span><span class="sxs-lookup"><span data-stu-id="30cfb-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span></span>  
 [<span data-ttu-id="30cfb-107">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="30cfb-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
