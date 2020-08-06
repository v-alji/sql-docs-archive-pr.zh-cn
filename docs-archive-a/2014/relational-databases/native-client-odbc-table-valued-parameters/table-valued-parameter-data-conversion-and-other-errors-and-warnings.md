---
title: 表值参数数据转换和其他错误和警告 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b9ba7f91b54548e096bbe47da6e01ba562f59d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577589"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a><span data-ttu-id="c8beb-102">表值参数数据转换及其他错误和警告</span><span class="sxs-lookup"><span data-stu-id="c8beb-102">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>
  <span data-ttu-id="c8beb-103">表值参数列值可按照与其他列和参数值相同的方式在客户端和服务器数据类型之间转换。</span><span class="sxs-lookup"><span data-stu-id="c8beb-103">Table-valued parameter column values can be converted between client and server data types in the same way as other column and parameter values.</span></span> <span data-ttu-id="c8beb-104">但是由于表值参数可以包含多个列和多个行，所以必须能够标识出现错误的实际值，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="c8beb-104">But because a table-valued parameter can contain multiple columns and multiple rows, it is important to be able to identify the actual value where the error occurred.</span></span>  
  
 <span data-ttu-id="c8beb-105">当在表值参数列中检测到错误或警告时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 将生成诊断记录。</span><span class="sxs-lookup"><span data-stu-id="c8beb-105">When an error or warning is detected in a table-valued parameter column, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will generate a diagnostic record.</span></span> <span data-ttu-id="c8beb-106">错误消息将包含表值参数的参数编号，以及列序号和行号。</span><span class="sxs-lookup"><span data-stu-id="c8beb-106">The error message will contain the parameter number of the table-valued parameter, plus the column ordinal and row number.</span></span> <span data-ttu-id="c8beb-107">应用程序还可以使用诊断记录中的诊断字段 SQL_DIAG_SS_TABLE_COLUMN_NUMBER 和 SQL_DIAG_SS_TABLE_ROW_NUMBER 确定与错误和警告关联的值。</span><span class="sxs-lookup"><span data-stu-id="c8beb-107">An application can also use the diagnostic fields SQL_DIAG_SS_TABLE_COLUMN_NUMBER and SQL_DIAG_SS_TABLE_ROW_NUMBER within diagnostic records to determine which values are associated with errors and warnings.</span></span> <span data-ttu-id="c8beb-108">这些诊断字段在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="c8beb-108">These diagnostic fields are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span>  
  
 <span data-ttu-id="c8beb-109">诊断记录的 SQLSTATE 和消息部分将在所有其他方面符合现有的 ODBC 行为。</span><span class="sxs-lookup"><span data-stu-id="c8beb-109">The SQLSTATE and message components of diagnostic records will conform to existing ODBC behavior in all other respects.</span></span> <span data-ttu-id="c8beb-110">也就是说，除了参数、行和列标识信息外，错误消息对于表值参数具有相同的值，这与非表值参数的值相同。</span><span class="sxs-lookup"><span data-stu-id="c8beb-110">That is, except for the parameter, row, and column identification information, error messages have the same values for table-valued parameters as they would for non-table-valued parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8beb-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8beb-111">See Also</span></span>  
 [<span data-ttu-id="c8beb-112">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="c8beb-112">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
