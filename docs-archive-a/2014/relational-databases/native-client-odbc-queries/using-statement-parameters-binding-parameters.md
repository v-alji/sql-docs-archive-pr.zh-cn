---
title: 绑定参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3402a7efce43d0ce94a20c93504ac1dcb2c7b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577592"
---
# <a name="binding-parameters"></a><span data-ttu-id="13187-102">绑定参数</span><span class="sxs-lookup"><span data-stu-id="13187-102">Binding Parameters</span></span>
  <span data-ttu-id="13187-103">在执行 SQL 语句前，该语句中的每个参数标记都必须与应用程序中的某个变量关联或绑定到某个变量。</span><span class="sxs-lookup"><span data-stu-id="13187-103">Each parameter marker in an SQL statement must be associated, or bound, to a variable in the application before the statement can be executed.</span></span> <span data-ttu-id="13187-104">这是通过调用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)函数来完成的。</span><span class="sxs-lookup"><span data-stu-id="13187-104">This is done by calling the [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) function.</span></span> <span data-ttu-id="13187-105">**SQLBindParameter**介绍了程序变量 (地址、C 数据类型等) 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="13187-105">**SQLBindParameter** describes the program variable (address, C data type, and so on) to the driver.</span></span> <span data-ttu-id="13187-106">它还通过指示其序数值来标识参数标记，然后描述它所表示的 SQL 对象的特点（SQL 数据类型、精度等）。</span><span class="sxs-lookup"><span data-stu-id="13187-106">It also identifies the parameter marker by indicating its ordinal value and then describes the characteristics of the SQL object it represents (SQL data type, precision, and so on).</span></span>

 <span data-ttu-id="13187-107">在执行语句前，可以随时绑定或重新绑定参数标记。</span><span class="sxs-lookup"><span data-stu-id="13187-107">Parameter markers can be bound or rebound at any time before a statement is executed.</span></span> <span data-ttu-id="13187-108">直到发生下列事件之一时，参数绑定才会失效：</span><span class="sxs-lookup"><span data-stu-id="13187-108">A parameter binding remains in effect until one of the following occurs:</span></span>

-   <span data-ttu-id="13187-109">如果调用[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)并将*Option*参数设置为 SQL_RESET_PARAMS 将释放所有绑定到语句句柄的参数。</span><span class="sxs-lookup"><span data-stu-id="13187-109">A call to [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the *Option* parameter set to SQL_RESET_PARAMS frees all parameters bound to the statement handle.</span></span>

-   <span data-ttu-id="13187-110">如果调用**SQLBindParameter** ，并将*ParameterNumber*设置为绑定参数标记的序号，将自动释放以前的绑定。</span><span class="sxs-lookup"><span data-stu-id="13187-110">A call to **SQLBindParameter** with *ParameterNumber* set to the ordinal of a bound parameter marker automatically releases the previous binding.</span></span>

 <span data-ttu-id="13187-111">应用程序还可以将参数绑定到程序变量数组以成批处理 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="13187-111">An application can also bind parameters to arrays of program variables to process an SQL statement in batches.</span></span> <span data-ttu-id="13187-112">数组绑定有两种不同的类型：</span><span class="sxs-lookup"><span data-stu-id="13187-112">There are two types of array binding:</span></span>

-   <span data-ttu-id="13187-113">当每个参数绑定到自身的变量数组时，将完成按列绑定。</span><span class="sxs-lookup"><span data-stu-id="13187-113">Column-wise binding is done when each individual parameter is bound to its own array of variables.</span></span>

     <span data-ttu-id="13187-114">通过调用 SQL_ATTR_PARAM_BIND_TYPE [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) *，并将\*\*将 valueptr*设置为 SQL_PARAM_BIND_BY_COLUMN 来指定按列绑定。</span><span class="sxs-lookup"><span data-stu-id="13187-114">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to SQL_PARAM_BIND_BY_COLUMN.</span></span>

-   <span data-ttu-id="13187-115">当 SQL 语句中的所有参数作为一个单元绑定到包含这些参数的各个变量的结构数组时，将完成按行绑定。</span><span class="sxs-lookup"><span data-stu-id="13187-115">Row-wise binding is done when all of the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>

     <span data-ttu-id="13187-116">通过调用**SQLSetStmtAttr**并将*属性*设置为 SQL_ATTR_PARAM_BIND_TYPE，并将*将 valueptr*设置为包含程序变量的结构的大小，可以指定按行绑定。</span><span class="sxs-lookup"><span data-stu-id="13187-116">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to the size of the structure holding the program variables.</span></span>

 <span data-ttu-id="13187-117">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将字符或二进制字符串参数发送到服务器时，它会将值填充到在**SQLBindParameter** *ColumnSize*参数中指定的长度。</span><span class="sxs-lookup"><span data-stu-id="13187-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sends character or binary string parameters to the server, it pads the values to the length specified in **SQLBindParameter** *ColumnSize* parameter.</span></span> <span data-ttu-id="13187-118">如果 ODBC 2.x 应用程序为*ColumnSize*指定0，则驱动程序将参数值填充到数据类型的精度。</span><span class="sxs-lookup"><span data-stu-id="13187-118">If an ODBC 2.x application specifies 0 for *ColumnSize*, the driver pads the parameter value to the precision of the data type.</span></span> <span data-ttu-id="13187-119">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器时，精度为 8000；连接到早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，精度为 255。</span><span class="sxs-lookup"><span data-stu-id="13187-119">The precision is 8000 when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers, 255 when connected to earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13187-120">变体列的*ColumnSize*以字节为单位。</span><span class="sxs-lookup"><span data-stu-id="13187-120">*ColumnSize* is in bytes for variant columns.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13187-121">支持为存储过程参数定义名称。</span><span class="sxs-lookup"><span data-stu-id="13187-121">supports defining names for stored procedure parameters.</span></span> <span data-ttu-id="13187-122">ODBC 3.5 还支持在调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程时使用的命名参数。</span><span class="sxs-lookup"><span data-stu-id="13187-122">ODBC 3.5 also introduced support for named parameters used when calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="13187-123">此支持可用于：</span><span class="sxs-lookup"><span data-stu-id="13187-123">This support can be used to:</span></span>

-   <span data-ttu-id="13187-124">调用存储过程，并向为该存储过程定义的参数的子集提供值。</span><span class="sxs-lookup"><span data-stu-id="13187-124">Call a stored procedure and provide values for a subset of the parameters defined for the stored procedure.</span></span>

-   <span data-ttu-id="13187-125">以不同于创建存储过程时指定的顺序指定应用程序中的参数。</span><span class="sxs-lookup"><span data-stu-id="13187-125">Specify the parameters in a different order in the application than the order specified when the stored procedure was created.</span></span>

 <span data-ttu-id="13187-126">仅当使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` 语句或 ODBC 调用转义序列执行存储过程时，才支持命名参数。</span><span class="sxs-lookup"><span data-stu-id="13187-126">Named parameters are only supported when using the [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` statement or the ODBC CALL escape sequence to execute a stored procedure.</span></span>

 <span data-ttu-id="13187-127">如果为某一存储过程参数设置 `SQL_DESC_NAME`，则查询中的所有存储过程参数也应设置 `SQL_DESC_NAME`。</span><span class="sxs-lookup"><span data-stu-id="13187-127">If `SQL_DESC_NAME` is set for a stored procedure parameter, all stored procedure parameters in the query should also set `SQL_DESC_NAME`.</span></span>  <span data-ttu-id="13187-128">如果在存储过程调用中使用了文本（其中参数已 `SQL_DESC_NAME` 设置），则文本应使用格式 *"name* = *value*"，其中*name*是存储过程参数名称 (例如 @p1) 。</span><span class="sxs-lookup"><span data-stu-id="13187-128">If literals are used in stored procedure calls, where parameters have `SQL_DESC_NAME` set, the literals should use the format *'name*=*value*', where *name* is the stored procedure parameter name (for example, @p1).</span></span> <span data-ttu-id="13187-129">有关详细信息，请参阅[按名称绑定参数 (命名参数) ](https://go.microsoft.com/fwlink/?LinkId=167215)。</span><span class="sxs-lookup"><span data-stu-id="13187-129">For more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkId=167215).</span></span>

## <a name="see-also"></a><span data-ttu-id="13187-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13187-130">See Also</span></span>
 [<span data-ttu-id="13187-131">使用语句参数</span><span class="sxs-lookup"><span data-stu-id="13187-131">Using Statement Parameters</span></span>](using-statement-parameters.md)


