---
title: 调用存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: rothja
ms.author: jroth
ms.openlocfilehash: c6fa704e45e4e85b479ae8a40a3e567bea1ec5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693817"
---
# <a name="calling-a-stored-procedure"></a><span data-ttu-id="619ec-102">调用存储过程</span><span class="sxs-lookup"><span data-stu-id="619ec-102">Calling a Stored Procedure</span></span>
  <span data-ttu-id="619ec-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序同时支持 ODBC 调用转义序列和执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程的[EXECUTE](/sql/t-sql/language-elements/execute-transact-sql)语句; odbc call 转义序列是首选方法。</span><span class="sxs-lookup"><span data-stu-id="619ec-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports both the ODBC CALL escape sequence and the [!INCLUDE[tsql](../../includes/tsql-md.md)][EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement for executing stored procedures; the ODBC CALL escape sequence is the preferred method.</span></span> <span data-ttu-id="619ec-104">使用 ODBC 语法使应用程序能检索存储过程的返回代码，还可以对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序进行优化以使用最初为在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的两台计算机间发送远程过程调用 (RPC) 开发的协议。</span><span class="sxs-lookup"><span data-stu-id="619ec-104">Using ODBC syntax enables an application to retrieve the return codes of stored procedures and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is also optimized to use a protocol originally developed for sending remote procedure (RPC) calls between computers running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="619ec-105">此 RPC 协议通过避免在服务器上进行大量参数处理和语句分析来提高性能。</span><span class="sxs-lookup"><span data-stu-id="619ec-105">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="619ec-106">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用带有 ODBC (的命名参数调用存储过程时，请参阅[按 (名称绑定参数) ](https://go.microsoft.com/fwlink/?LinkID=209721)) ，参数名称必须以 " \@ " 字符开头。</span><span class="sxs-lookup"><span data-stu-id="619ec-106">When calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures using named parameters with ODBC (for more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkID=209721)), the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="619ec-107">这是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有的限制。</span><span class="sxs-lookup"><span data-stu-id="619ec-107">This is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="619ec-108">与 Microsoft 数据访问组件 (MDAC) 相比，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序更加严格地遵守此限制。</span><span class="sxs-lookup"><span data-stu-id="619ec-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enforces this restriction more strictly than the Microsoft Data Access Components (MDAC).</span></span>  
  
 <span data-ttu-id="619ec-109">调用过程的 ODBC CALL 转义序列是：</span><span class="sxs-lookup"><span data-stu-id="619ec-109">The ODBC CALL escape sequence for calling a procedure is:</span></span>  
  
 <span data-ttu-id="619ec-110">{[**？ =**]**调用**_procedure_name_[ ( [*参数*] [**，**[*参数*]] ... ) ]}</span><span class="sxs-lookup"><span data-stu-id="619ec-110">{[**?=**]**call**_procedure_name_[([*parameter*][**,**[*parameter*]]...)]}</span></span>  
  
 <span data-ttu-id="619ec-111">其中*procedure_name*指定过程的名称，*参数*指定过程参数。</span><span class="sxs-lookup"><span data-stu-id="619ec-111">where *procedure_name* specifies the name of a procedure and *parameter* specifies a procedure parameter.</span></span> <span data-ttu-id="619ec-112">只有使用 ODBC CALL 转义序列的语句中才支持命名参数。</span><span class="sxs-lookup"><span data-stu-id="619ec-112">Named parameters are only supported in statements using the ODBC CALL escape sequence.</span></span>  
  
 <span data-ttu-id="619ec-113">一个过程可以有零个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="619ec-113">A procedure can have zero or more parameters.</span></span> <span data-ttu-id="619ec-114">它还可以返回值（如语法开头的可选参数标记 ?= 所示）。</span><span class="sxs-lookup"><span data-stu-id="619ec-114">It can also return a value (as indicated by the optional parameter marker ?= at the start of the syntax).</span></span> <span data-ttu-id="619ec-115">如果参数是输入或输入/输出参数，它可以是文字或参数标记。</span><span class="sxs-lookup"><span data-stu-id="619ec-115">If a parameter is an input or an input/output parameter, it can be a literal or a parameter marker.</span></span> <span data-ttu-id="619ec-116">如果参数是输出参数，它必须是参数标记，因为输出是未知的。</span><span class="sxs-lookup"><span data-stu-id="619ec-116">If the parameter is an output parameter, it must be a parameter marker because the output is unknown.</span></span> <span data-ttu-id="619ec-117">执行过程调用语句之前，必须与[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)绑定参数标记。</span><span class="sxs-lookup"><span data-stu-id="619ec-117">Parameter markers must be bound with [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) before the procedure call statement is executed.</span></span>  
  
 <span data-ttu-id="619ec-118">过程调用的输入和输入/输出参数可以省略。</span><span class="sxs-lookup"><span data-stu-id="619ec-118">Input and input/output parameters can be omitted from procedure calls.</span></span> <span data-ttu-id="619ec-119">如果使用括号但不带任何参数调用过程，驱动程序将指示数据源使用第一个参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="619ec-119">If a procedure is called with parentheses but without any parameters, the driver instructs the data source to use the default value for the first parameter.</span></span> <span data-ttu-id="619ec-120">例如：</span><span class="sxs-lookup"><span data-stu-id="619ec-120">For example:</span></span>  
  
 <span data-ttu-id="619ec-121">{**调用** _procedure_name_ \*\* ( ) \*\*}</span><span class="sxs-lookup"><span data-stu-id="619ec-121">{**call** _procedure_name_**( )**}</span></span>  
  
 <span data-ttu-id="619ec-122">如果该过程不具有任何参数，则它可能失败。</span><span class="sxs-lookup"><span data-stu-id="619ec-122">If the procedure does not have any parameters, the procedure can fail.</span></span> <span data-ttu-id="619ec-123">如果不带括号调用过程，驱动程序将不发送任何参数值。</span><span class="sxs-lookup"><span data-stu-id="619ec-123">If a procedure is called without parentheses, the driver does not send any parameter values.</span></span> <span data-ttu-id="619ec-124">例如：</span><span class="sxs-lookup"><span data-stu-id="619ec-124">For example:</span></span>  
  
 <span data-ttu-id="619ec-125">{**call** _procedure_name_}</span><span class="sxs-lookup"><span data-stu-id="619ec-125">{**call** _procedure_name_}</span></span>  
  
 <span data-ttu-id="619ec-126">可以为过程调用中的输入和输入/输出参数指定文字。</span><span class="sxs-lookup"><span data-stu-id="619ec-126">Literals can be specified for input and input/output parameters in procedure calls.</span></span> <span data-ttu-id="619ec-127">例如，过程 InsertOrder 具有五个输入参数。</span><span class="sxs-lookup"><span data-stu-id="619ec-127">For example, the procedure InsertOrder has five input parameters.</span></span> <span data-ttu-id="619ec-128">以下对 InsertOrder 的调用省略了第一个参数，为第二个参数提供文字，为第三、第四、第五个参数使用参数标记。</span><span class="sxs-lookup"><span data-stu-id="619ec-128">The following call to InsertOrder omits the first parameter, provides a literal for the second parameter, and uses a parameter marker for the third, fourth, and fifth parameters.</span></span> <span data-ttu-id="619ec-129">（按顺序对参数编号，从值 1 开始。）</span><span class="sxs-lookup"><span data-stu-id="619ec-129">(Parameters are numbered sequentially, beginning with a value of 1.)</span></span>  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 <span data-ttu-id="619ec-130">请注意如果省略一个参数，分隔该参数与其他参数的逗号必须保留。</span><span class="sxs-lookup"><span data-stu-id="619ec-130">Note that if a parameter is omitted, the comma delimiting it from other parameters must still appear.</span></span> <span data-ttu-id="619ec-131">如果省略输入参数或输入/输出参数，过程会使用该参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="619ec-131">If an input or input/output parameter is omitted, the procedure uses the default value of the parameter.</span></span> <span data-ttu-id="619ec-132">指定输入参数或输入/输出参数默认值的其他方式包括：将绑定到该参数的长度/指示器缓冲区的值设置为 SQL_DEFAULT_PARAM，或使用 DEFAULT 关键字。</span><span class="sxs-lookup"><span data-stu-id="619ec-132">Other ways to specify the default value of an input or input/output parameter are to set the value of the length/indicator buffer bound to the parameter to SQL_DEFAULT_PARAM, or to use the DEFAULT keyword.</span></span>  
  
 <span data-ttu-id="619ec-133">如果省略输入/输出参数，或者如果为该参数提供文字，驱动程序将放弃输出值。</span><span class="sxs-lookup"><span data-stu-id="619ec-133">If an input/output parameter is omitted, or if a literal is supplied for the parameter, the driver discards the output value.</span></span> <span data-ttu-id="619ec-134">同样，如果省略过程返回值的参数标记，驱动程序将放弃返回值。</span><span class="sxs-lookup"><span data-stu-id="619ec-134">Similarly, if the parameter marker for the return value of a procedure is omitted, the driver discards the return value.</span></span> <span data-ttu-id="619ec-135">最后一点，如果应用程序为不返回值的过程指定返回值参数，驱动程序将绑定到该参数的长度/指示器缓冲区的值设置为 SQL_NULL_DATA。</span><span class="sxs-lookup"><span data-stu-id="619ec-135">Finally, if an application specifies a return value parameter for a procedure that does not return a value, the driver sets the value of the length/indicator buffer bound to the parameter to SQL_NULL_DATA.</span></span>  
  
## <a name="delimiters-in-call-statements"></a><span data-ttu-id="619ec-136">CALL 语句中的分隔符</span><span class="sxs-lookup"><span data-stu-id="619ec-136">Delimiters in CALL Statements</span></span>  
 <span data-ttu-id="619ec-137">默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序还支持 ODBC {CALL} 转义序列特有的兼容性选项。</span><span class="sxs-lookup"><span data-stu-id="619ec-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by default also supports a compatibility option specific to the ODBC { CALL } escape sequence.</span></span> <span data-ttu-id="619ec-138">该驱动程序接受仅用一对双引号分隔整个存储过程名称的 CALL 语句：</span><span class="sxs-lookup"><span data-stu-id="619ec-138">The driver accepts CALL statements with only a single set of double quotation marks delimiting the entire stored procedure name:</span></span>  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 <span data-ttu-id="619ec-139">默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序还接受遵循 ISO 规则并用双引号将每个标识符括起来的 CALL 语句：</span><span class="sxs-lookup"><span data-stu-id="619ec-139">By default the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver also accepts CALL statements that follow the ISO rules and enclose each identifier in double quotation marks:</span></span>  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 <span data-ttu-id="619ec-140">不过，使用默认设置运行时，如果标识符包含不遵循 ISO 标准的字符，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序不支持上述任何一种带引号的标识符形式。</span><span class="sxs-lookup"><span data-stu-id="619ec-140">When running with the default settings, however, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using either form of quoted identifier with identifiers that contain characters not specified as legal in identifiers by the ISO standard.</span></span> <span data-ttu-id="619ec-141">例如，驱动程序无法使用带有带引号的标识符的 CALL 语句访问名为 **"Proc"** 的存储过程：</span><span class="sxs-lookup"><span data-stu-id="619ec-141">For example, the driver cannot access a stored procedure named **"My.Proc"** using a CALL statement with quoted identifiers:</span></span>  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 <span data-ttu-id="619ec-142">此语句将被该驱动程序解释为：</span><span class="sxs-lookup"><span data-stu-id="619ec-142">This statement is interpreted by the driver as:</span></span>  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 <span data-ttu-id="619ec-143">服务器引发错误，指出名为**MyDB**的链接服务器不存在。</span><span class="sxs-lookup"><span data-stu-id="619ec-143">The server raises an error that a linked server named **MyDB** does not exist.</span></span>  
  
 <span data-ttu-id="619ec-144">使用带方括号的标识符时则不存在此问题，此语句可以正确地进行解释：</span><span class="sxs-lookup"><span data-stu-id="619ec-144">The issue does not exist when using bracketed identifiers, this statement is interpreted correctly:</span></span>  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a><span data-ttu-id="619ec-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="619ec-145">See Also</span></span>  
 [<span data-ttu-id="619ec-146">运行存储过程</span><span class="sxs-lookup"><span data-stu-id="619ec-146">Running Stored Procedures</span></span>](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
