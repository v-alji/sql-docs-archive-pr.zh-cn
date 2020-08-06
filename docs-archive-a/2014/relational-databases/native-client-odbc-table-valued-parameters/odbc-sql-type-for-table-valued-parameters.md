---
title: 用于表值参数的 ODBC SQL 类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: rothja
ms.author: jroth
ms.openlocfilehash: c8ed46bf117c9158ae5b60c10ebd89e3d348f77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589555"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a><span data-ttu-id="6e0bb-102">表值参数的 ODBC SQL 类型</span><span class="sxs-lookup"><span data-stu-id="6e0bb-102">ODBC SQL Type for Table-Valued Parameters</span></span>
  <span data-ttu-id="6e0bb-103">对表值参数的支持是通过新的 ODBC SQL 类型 SQL_SS_TABLE 提供的。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-103">Support for table-valued parameters is provided by a new ODBC SQL type, SQL_SS_TABLE.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e0bb-104">备注</span><span class="sxs-lookup"><span data-stu-id="6e0bb-104">Remarks</span></span>  
 <span data-ttu-id="6e0bb-105">不能将 SQL_SS_TABLE 转换为任何其他 ODBC 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-105">SQL_SS_TABLE cannot be converted to any other ODBC or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="6e0bb-106">如果 SQL_SS_TABLE 在 SQLBindParameter 的*ValueType*参数中用作 C 数据类型，或者尝试将应用程序参数描述符中的 SQL_DESC_TYPE 设置 () 记录转换为 SQL_SS_TABLE，则返回 SQL_ERROR 并使用 SQLSTATE = HY003 生成的诊断记录 "应用程序缓冲区类型无效"。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-106">If SQL_SS_TABLE is used as a C data type in the *ValueType* parameter of SQLBindParameter, or an attempt is made to set SQL_DESC_TYPE in an application parameter descriptor (APD) record to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="6e0bb-107">如果在 IPD 记录中将 SQL_DESC_TYPE 设置为 SQL_SS_TABLE，并且对应的应用程序参数描述符记录不为 SQL_C_DEFAULT，则会返回 SQL_ERROR，并生成带有 SQLSTATE=HY003 的诊断记录“应用程序缓冲区类型无效”。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-107">If SQL_DESC_TYPE is set to SQL_SS_TABLE in an IPD record and the corresponding application parameter descriptor record is not SQL_C_DEFAULT, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span> <span data-ttu-id="6e0bb-108">SQLSetDescField、SQLSetDescRec 或 SQLBindParameter 的*ParameterType*可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-108">This can occur with the *ParameterType* of a SQLSetDescField, SQLSetDescRec or SQLBindParameter.</span></span>  
  
 <span data-ttu-id="6e0bb-109">如果在调用 SQLGetData 时 SQL_SS_TABLE 了*TargetType*参数，则返回 SQL_ERROR，并生成包含 SQLSTATE = HY003，"应用程序缓冲区类型无效" 的诊断记录。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-109">If the *TargetType* parameter is SQL_SS_TABLE when calling SQLGetData, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="6e0bb-110">不能将表值参数列作为 SQL_SS_TABLE 类型绑定。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-110">A table-valued parameter column cannot be bound as type SQL_SS_TABLE.</span></span> <span data-ttu-id="6e0bb-111">如果 `SQLBindParameter` 在将*ParameterType*设置为 SQL_SS_TABLE 的情况下调用，将返回 SQL_ERROR，并生成包含 SQLSTATE = HY004 "SQL 数据类型无效" 的诊断记录。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-111">If `SQLBindParameter` is called with *ParameterType* set to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY004, "Invalid SQL data type".</span></span> <span data-ttu-id="6e0bb-112">SQLSetDescField 和 SQLSetDescRec 也会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-112">This can also occur with SQLSetDescField and SQLSetDescRec.</span></span>  
  
 <span data-ttu-id="6e0bb-113">表值参数列值与参数和结果列具有相同的数据转换选项。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-113">Table-valued parameter column values have the same data conversion options as parameters and result columns.</span></span>  
  
 <span data-ttu-id="6e0bb-114">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本中只能将表值参数用作输入参数。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-114">A table-valued parameter can only be an input parameter in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="6e0bb-115">如果尝试通过 SQLBindParameter 或 SQLSetDescField 将 SQL_DESC_PARAMETER_TYPE 设置为 SQL_PARAM_INPUT 以外的值，则返回 SQL_ERROR，并将诊断记录添加到 SQLSTATE = HY105 的语句和消息 "参数类型无效"。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-115">If an attempt is made to set SQL_DESC_PARAMETER_TYPE to a value other than SQL_PARAM_INPUT via SQLBindParameter or SQLSetDescField, SQL_ERROR is returned and a diagnostic record is added to the statement with SQLSTATE=HY105 and the message "Invalid parameter type".</span></span>  
  
 <span data-ttu-id="6e0bb-116">表值参数列无法在*StrLen_or_IndPtr*中使用 SQL_DEFAULT_PARAM，因为表值参数不支持每行的默认值。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-116">Table-valued parameter columns cannot use SQL_DEFAULT_PARAM in *StrLen_or_IndPtr*, because per-row default values are not supported with table-valued parameters.</span></span> <span data-ttu-id="6e0bb-117">应用程序可以改为将 SQL_CA_SS_COL_HAS_DEFAULT_VALUE 列属性设置为 1。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-117">Instead, an application can set the column attribute SQL_CA_SS_COL_HAS_DEFAULT_VALUE to 1.</span></span> <span data-ttu-id="6e0bb-118">这表示该列的所有行均具有默认值。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-118">This means that the column will have default values for all rows.</span></span> <span data-ttu-id="6e0bb-119">如果*StrLen_or_IndPtr*设置为 SQL_DEFAULT_PARAM，则 SQLExecute 或 SQLExecDirect 将返回 SQL_ERROR，并且将使用 SQLSTATE = HY090 和消息 "字符串或缓冲区长度无效" 将诊断记录添加到语句中。</span><span class="sxs-lookup"><span data-stu-id="6e0bb-119">If *StrLen_or_IndPtr* is set to SQL_DEFAULT_PARAM, SQLExecute or SQLExecDirect will return SQL_ERROR, and a diagnostic record will be added to the statement with SQLSTATE=HY090 and the message "Invalid string or buffer length".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e0bb-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e0bb-120">See Also</span></span>  
 [<span data-ttu-id="6e0bb-121">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="6e0bb-121">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
