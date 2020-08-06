---
title: SQLParamData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: rothja
ms.author: jroth
ms.openlocfilehash: a4e0e8b31a65f28ce83e0d114231bdedd7a35a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590761"
---
# <a name="sqlparamdata"></a><span data-ttu-id="cd638-102">SQLParamData</span><span class="sxs-lookup"><span data-stu-id="cd638-102">SQLParamData</span></span>
  <span data-ttu-id="cd638-103">当 SQLParamData 返回与表值参数关联的*ValuePtrPtr*时，应用程序应调用 SQLPutData 与*StrLen_Or_Ind*。</span><span class="sxs-lookup"><span data-stu-id="cd638-103">When SQLParamData returns the *ValuePtrPtr* associated with a table-valued parameter, the application should call SQLPutData with *StrLen_Or_Ind*.</span></span> <span data-ttu-id="cd638-104">如果*StrLen_Or_Ind*的值大于0，则表示应用程序已准备就绪，可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 收集下一个表值参数行的参数数据。</span><span class="sxs-lookup"><span data-stu-id="cd638-104">If *StrLen_Or_Ind* has a value greater than 0, it means that the application is ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to gather parameter data for the next table-valued parameter row.</span></span> <span data-ttu-id="cd638-105">如果*StrLen_Or_Ind*的值为0，则表示表值参数没有更多的数据行。</span><span class="sxs-lookup"><span data-stu-id="cd638-105">If *StrLen_Or_Ind* has a value of 0, it means there are no more rows of data for the table-valued parameter.</span></span> <span data-ttu-id="cd638-106">有关详细信息，请参阅[表值参数和列值的绑定和数据传输](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)。</span><span class="sxs-lookup"><span data-stu-id="cd638-106">For more information, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="cd638-107">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="cd638-107">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd638-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd638-108">See Also</span></span>  
 <span data-ttu-id="cd638-109">[SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function) </span><span class="sxs-lookup"><span data-stu-id="cd638-109">[SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function) </span></span>  
 [<span data-ttu-id="cd638-110">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="cd638-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
