---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580709"
---
# <a name="sqlfreehandle"></a><span data-ttu-id="74f45-102">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="74f45-102">SQLFreeHandle</span></span>
  <span data-ttu-id="74f45-103">在手动提交模式中，对具有打开的事务的语句句柄调用**SQLFreeHandle**会导致对数据库的挂起的更改回滚。</span><span class="sxs-lookup"><span data-stu-id="74f45-103">In manual-commit mode, calling **SQLFreeHandle** on a statement handle with an open transaction causes a rollback of pending changes to the database.</span></span> <span data-ttu-id="74f45-104">对语句句柄调用**SQLFreeHandle**将始终关闭任何打开的游标，并放弃挂起的结果，释放与该语句句柄关联的所有资源。</span><span class="sxs-lookup"><span data-stu-id="74f45-104">Calling **SQLFreeHandle** on a statement handle always closes any open cursors and discards pending results, freeing all resources associated with the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f45-105">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74f45-105">See Also</span></span>  
 <span data-ttu-id="74f45-106">[SQLFreeHandle 函数](https://go.microsoft.com/fwlink/?LinkId=59345) </span><span class="sxs-lookup"><span data-stu-id="74f45-106">[SQLFreeHandle Function](https://go.microsoft.com/fwlink/?LinkId=59345) </span></span>  
 [<span data-ttu-id="74f45-107">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="74f45-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
