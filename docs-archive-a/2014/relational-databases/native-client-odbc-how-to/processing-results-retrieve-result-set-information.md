---
title: " (ODBC) 检索结果集信息 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580236"
---
# <a name="retrieve-result-set-information-odbc"></a><span data-ttu-id="2c5e7-102">检索结果集信息 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="2c5e7-102">Retrieve Result Set Information (ODBC)</span></span>
    
### <a name="to-get-information-about-a-result-set"></a><span data-ttu-id="2c5e7-103">获取有关结果集的信息</span><span class="sxs-lookup"><span data-stu-id="2c5e7-103">To get information about a result set</span></span>  
  
1.  <span data-ttu-id="2c5e7-104">调用[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md)可获取结果集中的列数。</span><span class="sxs-lookup"><span data-stu-id="2c5e7-104">Call [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns in the result set.</span></span>  
  
2.  <span data-ttu-id="2c5e7-105">对于结果集中的每个列：</span><span class="sxs-lookup"><span data-stu-id="2c5e7-105">For each column in the result set:</span></span>  
  
    -   <span data-ttu-id="2c5e7-106">调用[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)以获取有关结果列的信息。</span><span class="sxs-lookup"><span data-stu-id="2c5e7-106">Call [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to get information about the result column.</span></span>  
  
     <span data-ttu-id="2c5e7-107">或</span><span class="sxs-lookup"><span data-stu-id="2c5e7-107">Or</span></span>  
  
    -   <span data-ttu-id="2c5e7-108">调用[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md)可获取有关结果列的特定描述符信息。</span><span class="sxs-lookup"><span data-stu-id="2c5e7-108">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) to get specific descriptor information about the result column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5e7-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c5e7-109">See Also</span></span>  
 <span data-ttu-id="2c5e7-110">[处理结果操作指南主题 &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="2c5e7-110">[Processing Results How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="2c5e7-111">确定结果集的特征 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="2c5e7-111">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
