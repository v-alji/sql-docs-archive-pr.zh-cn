---
title: 使用内存中的所有值将数据作为表值参数发送 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), sending data to a stored procedure with all values in memory
ms.assetid: 8b96282f-00d5-4e28-8111-0a87ae6d7781
author: rothja
ms.author: jroth
ms.openlocfilehash: f53e129ea49b1faa08be5247c51b5e74353e2f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693287"
---
# <a name="sending-data-as-a-table-valued-parameter-with-all-values-in-memory-odbc"></a><span data-ttu-id="a5066-102">所有值位于内存中时将数据作为表值参数发送 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a5066-102">Sending Data as a Table-Valued Parameter with All Values in Memory (ODBC)</span></span>
  <span data-ttu-id="a5066-103">本主题描述当所有值都在内存中时，如何将数据作为表值参数发送到存储过程。</span><span class="sxs-lookup"><span data-stu-id="a5066-103">This topic describes how to send data to a stored procedure as a table-valued parameter when all values are in memory.</span></span> <span data-ttu-id="a5066-104">有关演示表值参数的另一个示例，请参阅[将表值参数用于 ODBC&#41;&#40;](table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="a5066-104">For another sample demonstrating table-valued parameters, see [Use Table-Valued Parameters &#40;ODBC&#41;](table-valued-parameters-odbc.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="a5066-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="a5066-105">Prerequisite</span></span>  
 <span data-ttu-id="a5066-106">该过程假定已在服务器上执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="a5066-106">This procedure assumes that the following [!INCLUDE[tsql](../../includes/tsql-md.md)] has been executed on the server:</span></span>  
  
```  
create type TVParam as table(ProdCode integer, Qty integer)  
create procedure TVPOrderEntry(@CustCode varchar(5), @Items TVPParam,   
            @OrdNo integer output, @OrdDate datetime output)  
         as   
         set @OrdDate = GETDATE();  
         insert into TVPOrd (OrdDate, CustCode)   
values (@OrdDate, @CustCode) output OrdNo);   
         select @OrdNo = SCOPE_IDENTITY();   
         insert into TVPItem (OrdNo, ProdCode, Qty)  
select @OrdNo, @Items.ProdCode, @Items.Qty   
from @Items  
```  
  
## <a name="to-send-the-data"></a><span data-ttu-id="a5066-107">发送数据</span><span class="sxs-lookup"><span data-stu-id="a5066-107">To Send the Data</span></span>  
  
1.  <span data-ttu-id="a5066-108">声明 SQL 参数的变量。</span><span class="sxs-lookup"><span data-stu-id="a5066-108">Declare variables for the SQL parameters.</span></span> <span data-ttu-id="a5066-109">这种情况下，表值全都在内存中，因此将表值的列值声明为数组。</span><span class="sxs-lookup"><span data-stu-id="a5066-109">In this case, the table value is held entirely in memory, so values for the columns of the table value are declared as arrays.</span></span>  
  
    ```  
    SQLRETURN r;  
    // Variables for SQL parameters.  
    #define ITEM_ARRAY_SIZE 20  
  
    SQLCHAR CustCode[6];  
    SQLCHAR *TVP = (SQLCHAR *) "TVParam";  
    SQLINTEGER ProdCode[ITEM_ARRAY_SIZE], Qty[ITEM_ARRAY_SIZE];  
    SQLINTEGER OrdNo;  
    char OrdDate[23];  
  
    // Variables for indicator/length variables associated with parameters.  
    SQLLEN cbCustCode, cbTVP, cbProdCode[ITEM_ARRAY_SIZE], cbQty[ITEM_ARRAY_SIZE], cbOrdNo, cbOrdDate;  
    ```  
  
2.  <span data-ttu-id="a5066-110">绑定参数。</span><span class="sxs-lookup"><span data-stu-id="a5066-110">Bind the parameters.</span></span> <span data-ttu-id="a5066-111">使用表值参数时，绑定参数是两阶段进程。</span><span class="sxs-lookup"><span data-stu-id="a5066-111">Binding parameters is a two stage process when table-valued parameters are used.</span></span> <span data-ttu-id="a5066-112">在第一阶段，以正常方式绑定存储过程的步骤参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a5066-112">In the first stage, step parameters for the stored procedure are bound in the normal way, as follows.</span></span>  
  
    ```  
    // Bind parameters for call to TVPOrderEntryDirect.  
    // 1 - Custcode input  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_VARCHAR, SQL_C_CHAR, 5, 0, CustCode, sizeof(CustCode), &cbCustCode);  
  
    // 2 - Items TVP  
    r = SQLBindParameter(hstmt,   
        2,// ParameterNumber  
        SQL_PARAM_INPUT,// InputOutputType  
        SQL_C_DEFAULT,// ValueType   
        SQL_SS_TABLE,// Parametertype  
        ITEM_ARRAY_SIZE,// ColumnSize: For a table-valued parameter this is the row array size.  
        0,// DecimalDigits: For a table-valued parameter this is always 0.   
        TVP,// ParameterValuePtr: For a table-valued parameter this is the type name of the   
    //table-valued parameter, and also a token returned by SQLParamData.  
        SQL_NTS,// BufferLength: For a table-valued parameter this is the length of the type name or SQL_NTS.  
        &cbTVP);// StrLen_or_IndPtr: For a table-valued parameter this is the number of rows actually used.  
  
    // 3 - OrdNo output  
    r = SQLBindParameter(hstmt, 3, SQL_PARAM_OUTPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, &OrdNo,  
       sizeof(SQLINTEGER), &cbOrdNo);  
    // 4 - OrdDate output  
    r = SQLBindParameter(hstmt, 4, SQL_PARAM_OUTPUT,SQL_TYPE_TIMESTAMP, SQL_C_CHAR, 23, 3, &OrdDate,   
       sizeof(OrdDate), &cbOrdDate);  
    ```  
  
3.  <span data-ttu-id="a5066-113">参数绑定的第二阶段是绑定表值参数的列。</span><span class="sxs-lookup"><span data-stu-id="a5066-113">The second stage of parameter binding is to bind the columns for the table-valued parameter.</span></span> <span data-ttu-id="a5066-114">首先将参数焦点设置为表值参数的序号。</span><span class="sxs-lookup"><span data-stu-id="a5066-114">The parameter focus is first set to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="a5066-115">然后使用 SQLBindParameter 来绑定表值的列，方法与它们是存储过程的参数相同，但使用 ParameterNumber 的列序号。</span><span class="sxs-lookup"><span data-stu-id="a5066-115">Then columns of the table value are bound by using SQLBindParameter in the same way as they would be if they were parameters of the stored procedure, but with column ordinals for ParameterNumber.</span></span> <span data-ttu-id="a5066-116">如果有更多表值参数，我们会轮流将焦点设置为每个参数，并绑定它们的列。</span><span class="sxs-lookup"><span data-stu-id="a5066-116">If there were more table-valued parameters, we would set the focus to each in turn and bind their columns.</span></span> <span data-ttu-id="a5066-117">最终，将参数焦点重置为 0。</span><span class="sxs-lookup"><span data-stu-id="a5066-117">Finally, the parameter focus is reset to 0.</span></span>  
  
    ```  
    // Bind columns for the table-valued parameter (param 2).  
    // First set focus on param 2.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 2, SQL_IS_INTEGER);  
  
    // Col 1 - ProdCode  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, ProdCode, sizeof(SQLINTEGER), cbProdCode);  
    // Col 2 - Qty  
    r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, Qty, sizeof(SQLINTEGER), cbQty);  
  
    // Reset param focus.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 0, SQL_IS_INTEGER);  
    ```  
  
4.  <span data-ttu-id="a5066-118">填充参数缓冲区。</span><span class="sxs-lookup"><span data-stu-id="a5066-118">Populate the parameter buffers.</span></span> <span data-ttu-id="a5066-119">`cbTVP` 将设置为要发送到服务器的行数。</span><span class="sxs-lookup"><span data-stu-id="a5066-119">`cbTVP` is set to the number of rows to be sent to the server.</span></span>  
  
    ```  
    // Populate parameters.  
    cbTVP = 0; // Number of rows available for input.  
    strcpy_s((char *) CustCode, sizeof(CustCode), "CUST1"); cbCustCode = SQL_NTS;  
  
    ProdCode[cbTVP] = 1215;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 5;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input  
  
    ProdCode[cbTVP] = 1017;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 2;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input.  
    ```  
  
5.  <span data-ttu-id="a5066-120">调用该过程：</span><span class="sxs-lookup"><span data-stu-id="a5066-120">Call the procedure:</span></span>  
  
    ```  
    // Call the procedure.  
    r = SQLExecDirect(hstmt, (SQLCHAR *) "{call TVPOrderEntry(?, ?, ?, ?)}",SQL_NTS);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5066-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5066-121">See Also</span></span>  
 [<span data-ttu-id="a5066-122">ODBC 表值参数编程示例</span><span class="sxs-lookup"><span data-stu-id="a5066-122">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
  
  
