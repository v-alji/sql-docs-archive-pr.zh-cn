---
title: 准备好的语句的表值参数元数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693810"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a><span data-ttu-id="c5906-102">准备的语句的表值参数元数据</span><span class="sxs-lookup"><span data-stu-id="c5906-102">Table-Valued Parameter Metadata for Prepared Statements</span></span>
  <span data-ttu-id="c5906-103">应用程序可以通过 SQLNumParams 和 SQLDescribeParam 获取已准备的过程调用的元数据。</span><span class="sxs-lookup"><span data-stu-id="c5906-103">An application can obtain metadata for a prepared procedure call through SQLNumParams and SQLDescribeParam.</span></span> <span data-ttu-id="c5906-104">对于表值参数， *DataTypePtr*设置为 SQL_SS_TABLE。</span><span class="sxs-lookup"><span data-stu-id="c5906-104">For table-valued parameters, *DataTypePtr* is set to SQL_SS_TABLE.</span></span> <span data-ttu-id="c5906-105">可以通过 SQLGetDescField 为 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 提供额外的元数据。</span><span class="sxs-lookup"><span data-stu-id="c5906-105">Additional metadata is available through SQLGetDescField for SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME.</span></span>  
  
 <span data-ttu-id="c5906-106">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 可以与 SQLColumns 一起使用，以获取与表值参数关联的表类型的列元数据。</span><span class="sxs-lookup"><span data-stu-id="c5906-106">SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can be used with SQLColumns to obtain column metadata for table types associated with table-valued parameters.</span></span> <span data-ttu-id="c5906-107">在这种情况下，在调用 SQLColumns 之前，必须将 SQL_SOPT_SS_NAME_SCOPE 设置为 SQL_SS_NAME_SCOPE_TABLE_TYPE。</span><span class="sxs-lookup"><span data-stu-id="c5906-107">In this case, SQL_SOPT_SS_NAME_SCOPE must be set to SQL_SS_NAME_SCOPE_TABLE_TYPE before SQLColumns is called.</span></span> <span data-ttu-id="c5906-108">在应用程序检索完表值参数列元数据之后，应将 SQL_SOPT_SS_NAME_SCOPE 设置回原来的默认值 SQL_SS_NAME_SCOPE_TABLE。</span><span class="sxs-lookup"><span data-stu-id="c5906-108">SQL_SOPT_SS_NAME_SCOPE should then be set back to the default value, SQL_SS_NAME_SCOPE_TABLE, when the application has finished retrieving table-valued parameter column metadata.</span></span>  
  
 <span data-ttu-id="c5906-109">也可以将 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 用于 CLR 用户定义类型参数。</span><span class="sxs-lookup"><span data-stu-id="c5906-109">SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can also be used with CLR user-defined type parameters.</span></span>  
  
 <span data-ttu-id="c5906-110">无法获取非存储过程调用的准备的语句的表值参数元数据。</span><span class="sxs-lookup"><span data-stu-id="c5906-110">You cannot obtain table-valued parameter metadata for prepared statements that are not stored procedure calls.</span></span> <span data-ttu-id="c5906-111">如果试图这样做，应用程序将返回错误代码为 SQLSTATE 42000 的 SQL_ERROR，以及消息“语法错误或访问冲突”。</span><span class="sxs-lookup"><span data-stu-id="c5906-111">If you try to do this, the application returns SQL_ERROR with SQLSTATE 42000 and the message "Syntax error or access violation".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5906-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5906-112">See Also</span></span>  
 [<span data-ttu-id="c5906-113">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="c5906-113">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
