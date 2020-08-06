---
title: SQLGetStmtAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: rothja
ms.author: jroth
ms.openlocfilehash: f1f9b6a0c0668540b566c9b3d7ede781c97a1dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587374"
---
# <a name="sqlgetstmtattr"></a><span data-ttu-id="08ea7-102">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="08ea7-102">SQLGetStmtAttr</span></span>
  <span data-ttu-id="08ea7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序扩展 SQLGetStmtAttr 以公开特定于驱动程序的语句属性。</span><span class="sxs-lookup"><span data-stu-id="08ea7-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver extends SQLGetStmtAttr to expose driver-specific statement attributes.</span></span>  
  
 <span data-ttu-id="08ea7-104">[SQLSetStmtAttr](sqlsetstmtattr.md)列出了读写属性。</span><span class="sxs-lookup"><span data-stu-id="08ea7-104">[SQLSetStmtAttr](sqlsetstmtattr.md) lists statement attributes that are both read and write.</span></span> <span data-ttu-id="08ea7-105">本主题列出只读语句属性。</span><span class="sxs-lookup"><span data-stu-id="08ea7-105">This topic lists the read only statement attributes.</span></span>  
  
## <a name="sql_sopt_ss_current_command"></a><span data-ttu-id="08ea7-106">SQL_SOPT_SS_CURRENT_COMMAND</span><span class="sxs-lookup"><span data-stu-id="08ea7-106">SQL_SOPT_SS_CURRENT_COMMAND</span></span>  
 <span data-ttu-id="08ea7-107">SQL_SOPT_SS_CURRENT_COMMAND 属性公开命令批处理中的当前命令。</span><span class="sxs-lookup"><span data-stu-id="08ea7-107">The SQL_SOPT_SS_CURRENT_COMMAND attribute exposes the current command of a command batch.</span></span> <span data-ttu-id="08ea7-108">返回一个整数，该整数指定该命令在批处理中的位置。</span><span class="sxs-lookup"><span data-stu-id="08ea7-108">The return is an integer that specifies the location of the command in the batch.</span></span> <span data-ttu-id="08ea7-109">*将 valueptr*值的类型为 SQLLEN。</span><span class="sxs-lookup"><span data-stu-id="08ea7-109">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
## <a name="sql_sopt_ss_nocount_status"></a><span data-ttu-id="08ea7-110">SQL_SOPT_SS_NOCOUNT_STATUS</span><span class="sxs-lookup"><span data-stu-id="08ea7-110">SQL_SOPT_SS_NOCOUNT_STATUS</span></span>  
 <span data-ttu-id="08ea7-111">SQL_SOPT_SS_NOCOUNT_STATUS 特性指示 NOCOUNT 选项的当前设置，该选项控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在调用[SQLRowCount](sqlrowcount.md)时是否报告受语句影响的行数。</span><span class="sxs-lookup"><span data-stu-id="08ea7-111">The SQL_SOPT_SS_NOCOUNT_STATUS attribute indicates the current setting of the NOCOUNT option, which controls whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reports the numbers of rows affected by a statement when [SQLRowCount](sqlrowcount.md) is called.</span></span> <span data-ttu-id="08ea7-112">*将 valueptr*值的类型为 SQLLEN。</span><span class="sxs-lookup"><span data-stu-id="08ea7-112">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
|<span data-ttu-id="08ea7-113">值</span><span class="sxs-lookup"><span data-stu-id="08ea7-113">Value</span></span>|<span data-ttu-id="08ea7-114">说明</span><span class="sxs-lookup"><span data-stu-id="08ea7-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08ea7-115">SQL_NC_OFF</span><span class="sxs-lookup"><span data-stu-id="08ea7-115">SQL_NC_OFF</span></span>|<span data-ttu-id="08ea7-116">NOCOUNT 为 OFF。</span><span class="sxs-lookup"><span data-stu-id="08ea7-116">NOCOUNT is OFF.</span></span> <span data-ttu-id="08ea7-117">SQLRowCount 返回受影响的行数。</span><span class="sxs-lookup"><span data-stu-id="08ea7-117">SQLRowCount returns number of rows affected.</span></span>|  
|<span data-ttu-id="08ea7-118">SQL_NC_ON</span><span class="sxs-lookup"><span data-stu-id="08ea7-118">SQL_NC_ON</span></span>|<span data-ttu-id="08ea7-119">NOCOUNT 为 ON。</span><span class="sxs-lookup"><span data-stu-id="08ea7-119">NOCOUNT is ON.</span></span> <span data-ttu-id="08ea7-120">SQLRowCount 不返回受影响的行数，返回值为0。</span><span class="sxs-lookup"><span data-stu-id="08ea7-120">The number of rows affected is not returned by SQLRowCount and the returned value is 0.</span></span>|  
  
 <span data-ttu-id="08ea7-121">如果 SQLRowCount 返回0，则应用程序应测试 SQL_SOPT_SS_NOCOUNT_STATUS。</span><span class="sxs-lookup"><span data-stu-id="08ea7-121">If SQLRowCount returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="08ea7-122">如果返回 SQL_NC_ON，则 SQLRowCount 的值将仅指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未返回行计数。</span><span class="sxs-lookup"><span data-stu-id="08ea7-122">If SQL_NC_ON is returned, the value of 0 from SQLRowCount only indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has not returned a row count.</span></span> <span data-ttu-id="08ea7-123">如果返回了 SQL_NC_OFF，则表示 NOCOUNT 为 off，并且 SQLRowCount 返回的 0 值表示该语句未影响任何行。</span><span class="sxs-lookup"><span data-stu-id="08ea7-123">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from SQLRowCount indicates that the statement did not affect any rows.</span></span>  
  
 <span data-ttu-id="08ea7-124">当 SQL_SOPT_SS_NOCOUNT_STATUS 为 SQL_NC_OFF 时，应用程序不应显示 SQLRowCount 的值。</span><span class="sxs-lookup"><span data-stu-id="08ea7-124">Applications should not display the value of SQLRowCount when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="08ea7-125">大型批处理或存储过程可能包含多个 SET NOCOUNT 语句，所以不能认定 SQL_SOPT_SS_NOCOUNT_STATUS 保持不变。</span><span class="sxs-lookup"><span data-stu-id="08ea7-125">Large batches or stored procedures can contain multiple SET NOCOUNT statements, so it cannot be assumed that SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="08ea7-126">每次 SQLRowCount 返回0时，应测试此选项。</span><span class="sxs-lookup"><span data-stu-id="08ea7-126">This option should be tested each time SQLRowCount returns 0.</span></span>  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a><span data-ttu-id="08ea7-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="08ea7-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
 <span data-ttu-id="08ea7-128">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT 属性返回查询通知请求的消息文本。</span><span class="sxs-lookup"><span data-stu-id="08ea7-128">The SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT attribute returns the message text for the query notification request.</span></span>  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a><span data-ttu-id="08ea7-129">SQLGetStmtAttr 和表值参数</span><span class="sxs-lookup"><span data-stu-id="08ea7-129">SQLGetStmtAttr and Table-valued Parameters</span></span>  
 <span data-ttu-id="08ea7-130">使用表值参数时，可以调用 SQLGetStmtAttr 来获取应用程序参数描述符 (APD) 中 SQL_SOPT_SS_PARAM_FOCUS 的值。</span><span class="sxs-lookup"><span data-stu-id="08ea7-130">SQLGetStmtAttr can be called to get the value of SQL_SOPT_SS_PARAM_FOCUS in the application parameter descriptor (APD) when working with table-valued parameters.</span></span> <span data-ttu-id="08ea7-131">有关 SQL_SOPT_SS_PARAM_FOCUS 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="08ea7-131">For more information on SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="08ea7-132">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="08ea7-132">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ea7-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08ea7-133">See Also</span></span>  
 <span data-ttu-id="08ea7-134">[SQLSetStmtAttr 函数](https://go.microsoft.com/fwlink/?LinkId=59370) </span><span class="sxs-lookup"><span data-stu-id="08ea7-134">[SQLSetStmtAttr Function](https://go.microsoft.com/fwlink/?LinkId=59370) </span></span>  
 [<span data-ttu-id="08ea7-135">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="08ea7-135">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
