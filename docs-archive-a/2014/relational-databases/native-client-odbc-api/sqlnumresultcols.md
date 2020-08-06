---
title: SQLNumResultCols |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590762"
---
# <a name="sqlnumresultcols"></a><span data-ttu-id="9cab0-102">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="9cab0-102">SQLNumResultCols</span></span>
  <span data-ttu-id="9cab0-103">对于执行的语句， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序不会访问服务器来报告结果集中的列数。</span><span class="sxs-lookup"><span data-stu-id="9cab0-103">For executed statements, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not visit the server to report the number of columns in a result set.</span></span> <span data-ttu-id="9cab0-104">在这种情况下，不 `SQLNumResultCols` 会导致服务器往返。</span><span class="sxs-lookup"><span data-stu-id="9cab0-104">In this case, `SQLNumResultCols` does not cause a server roundtrip.</span></span> <span data-ttu-id="9cab0-105">与[SQLDescribeCol](sqldescribecol.md)和[SQLColAttribute](sqlcolattribute.md)相似， `SQLNumResultCols` 对已准备但未执行的语句调用会生成服务器往返。</span><span class="sxs-lookup"><span data-stu-id="9cab0-105">Like [SQLDescribeCol](sqldescribecol.md) and [SQLColAttribute](sqlcolattribute.md), calling `SQLNumResultCols` on prepared but not executed statements generates a server roundtrip.</span></span>  
  
 <span data-ttu-id="9cab0-106">当某个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或语句批处理返回多个结果行集时，结果集列的个数可能在各个集之间有所变化。</span><span class="sxs-lookup"><span data-stu-id="9cab0-106">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statement batch returns multiple result row sets, it is possible for the number of result set columns to change from one set to another.</span></span> <span data-ttu-id="9cab0-107">`SQLNumResultCols`应为每个集调用。</span><span class="sxs-lookup"><span data-stu-id="9cab0-107">`SQLNumResultCols` should be called for each set.</span></span> <span data-ttu-id="9cab0-108">如果列数有变化，应用程序应该在提取行结果之前重新绑定数据值。</span><span class="sxs-lookup"><span data-stu-id="9cab0-108">When the number of columns changes, the application should rebind data values prior to fetching row results.</span></span> <span data-ttu-id="9cab0-109">有关处理多个结果集返回的详细信息，请参阅[SQLMoreResults](sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="9cab0-109">For more information about handling multiple result set returns, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="9cab0-110">从 "允许 SQLNumResultCols" 开始，数据库引擎中的改进 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可获取预期结果的更准确说明。</span><span class="sxs-lookup"><span data-stu-id="9cab0-110">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLNumResultCols to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="9cab0-111">更准确的结果可能与早期版本的 SQLNumResultCols 返回的值不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9cab0-111">These more accurate results may differ from the values returned by SQLNumResultCols in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9cab0-112">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="9cab0-112">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cab0-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9cab0-113">See Also</span></span>  
 <span data-ttu-id="9cab0-114">[SQLNumResultCols 函数](https://go.microsoft.com/fwlink/?LinkId=59359) </span><span class="sxs-lookup"><span data-stu-id="9cab0-114">[SQLNumResultCols Function](https://go.microsoft.com/fwlink/?LinkId=59359) </span></span>  
 [<span data-ttu-id="9cab0-115">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="9cab0-115">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
