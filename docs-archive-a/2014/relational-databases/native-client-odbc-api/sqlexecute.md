---
title: SQLExecute |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: rothja
ms.author: jroth
ms.openlocfilehash: 514436c65ef103cafae2189a03b560255b447eda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581177"
---
# <a name="sqlexecute"></a><span data-ttu-id="4fecd-102">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="4fecd-102">SQLExecute</span></span>
  <span data-ttu-id="4fecd-103">如果语句属性 SQL_SOPT_SS_PARAM_FOCUS 未设置为0，则 SQLExecute 将返回 SQL_ERROR 并生成具有 SQLSTATE = HY024 的诊断记录和消息 "属性值无效，SQL_SOPT_SS_PARAM_FOCUS (在执行时必须为零) "。</span><span class="sxs-lookup"><span data-stu-id="4fecd-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not set to 0, SQLExecute will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="4fecd-104">有关 SQL_SOPT_SS_PARAM_FOCUS 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="4fecd-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fecd-105">备注</span><span class="sxs-lookup"><span data-stu-id="4fecd-105">Remarks</span></span>  
 <span data-ttu-id="4fecd-106">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="4fecd-106">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fecd-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fecd-107">See Also</span></span>  
 <span data-ttu-id="4fecd-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span><span class="sxs-lookup"><span data-stu-id="4fecd-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span></span>  
 [<span data-ttu-id="4fecd-109">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="4fecd-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
