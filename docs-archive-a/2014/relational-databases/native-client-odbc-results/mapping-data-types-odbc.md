---
title: 将数据类型映射 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: rothja
ms.author: jroth
ms.openlocfilehash: 545e738afb6b3283b2ff2f3830921da8ed13202f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693825"
---
# <a name="mapping-data-types-odbc"></a><span data-ttu-id="204ed-102">映射数据类型 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="204ed-102">Mapping Data Types (ODBC)</span></span>
  <span data-ttu-id="204ed-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将 SQL 数据类型映射到 ODBC sql 数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types to ODBC SQL data types.</span></span> <span data-ttu-id="204ed-104">以下部分讨论 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 数据类型以及它们映射到的 ODBC SQL 数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-104">The sections below discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types and the ODBC SQL data types to which they map.</span></span> <span data-ttu-id="204ed-105">此外，还讨论 ODBC SQL 数据类型和它们对应的 ODBC C 数据类型，以及支持的和默认的转换。</span><span class="sxs-lookup"><span data-stu-id="204ed-105">They also discuss the ODBC SQL data types and their corresponding ODBC C data types, and the supported and default conversions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="204ed-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Timestamp**数据类型映射到 SQL_BINARY 或 SQL_VARBINARY ODBC 数据类型，因为**时间戳**列中的值不是**datetime**值，而是\*\*BINARY (8) **或**VARBINARY (8) \*\*指示行的活动顺序的值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="204ed-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** data type maps to the SQL_BINARY or SQL_VARBINARY ODBC data type because the values in **timestamp** columns are not **datetime** values, but **binary(8)** or **varbinary(8)** values that indicate the sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity on the row.</span></span> <span data-ttu-id="204ed-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序遇到字节数为奇数的 SQL_C_WCHAR (Unicode) 值，则将截断尾随奇数字节。</span><span class="sxs-lookup"><span data-stu-id="204ed-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters a SQL_C_WCHAR (Unicode) value that is an odd number of bytes, the trailing odd byte is truncated.</span></span>  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a><span data-ttu-id="204ed-108">在 ODBC 中处理 sql_variant 数据类型</span><span class="sxs-lookup"><span data-stu-id="204ed-108">Dealing with sql_variant Data Type in ODBC</span></span>  
 <span data-ttu-id="204ed-109">**Sql_variant**数据类型列可以包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (lob) 之外的任何数据类型，例如**text**、 **ntext**和**image**。</span><span class="sxs-lookup"><span data-stu-id="204ed-109">The **sql_variant** data type column can contain any of the data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except large objects (LOBs), such as **text**, **ntext**, and **image**.</span></span> <span data-ttu-id="204ed-110">例如，列可能包含某些行的**smallint**值、其他行的**float**值，以及余数中的**char/nchar**值。</span><span class="sxs-lookup"><span data-stu-id="204ed-110">For example, the column could contain **smallint** values for some rows, **float** values for other rows, and **char/nchar** values in the remainder.</span></span>  
  
 <span data-ttu-id="204ed-111">**Sql_variant**的数据类型类似于 Microsoft Visual Basic 中的**variant**数据类型??。</span><span class="sxs-lookup"><span data-stu-id="204ed-111">The **sql_variant** data type is similar to the **Variant** data type in Microsoft Visual Basic??.</span></span>  
  
### <a name="retrieving-data-from-the-server"></a><span data-ttu-id="204ed-112">从服务器检索数据</span><span class="sxs-lookup"><span data-stu-id="204ed-112">Retrieving Data from the Server</span></span>  
 <span data-ttu-id="204ed-113">ODBC 没有变体类型的概念，因此限制在中使用 ODBC 驱动程序的**sql_variant**数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="204ed-113">ODBC does not have a concept of variant types, limiting the use of the **sql_variant** data type with an ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="204ed-114">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，如果指定了 binding，则**sql_variant**数据类型必须绑定到其中一个已记录的 ODBC 数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if binding is specified, the **sql_variant** data type must be bound to one of the documented ODBC data types.</span></span> <span data-ttu-id="204ed-115">**SQL_CA_SS_VARIANT_TYPE**，特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序的新属性将向用户返回**sql_variant**列中的实例的数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-115">**SQL_CA_SS_VARIANT_TYPE**, a new attribute specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, returns the data type of an instance in the **sql_variant** column to the user.</span></span>  
  
 <span data-ttu-id="204ed-116">如果未指定绑定，则可以使用[SQLGetData](../native-client-odbc-api/sqlgetdata.md)函数来确定**sql_variant**列中的实例的数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-116">If no binding is specified, the [SQLGetData](../native-client-odbc-api/sqlgetdata.md) function can be used to determine the data type of an instance in the **sql_variant** column.</span></span>  
  
 <span data-ttu-id="204ed-117">若要检索**sql_variant**数据，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="204ed-117">To retrieve **sql_variant** data follow these steps.</span></span>  
  
1.  <span data-ttu-id="204ed-118">调用**SQLFetch**以定位到检索到的行。</span><span class="sxs-lookup"><span data-stu-id="204ed-118">Call **SQLFetch** to position to the row retrieved.</span></span>  
  
2.  <span data-ttu-id="204ed-119">调用**SQLGetData**，指定类型 SQL_C_BINARY，并指定0作为数据长度。</span><span class="sxs-lookup"><span data-stu-id="204ed-119">Call **SQLGetData**, specifying SQL_C_BINARY for the type and 0 for the data length.</span></span> <span data-ttu-id="204ed-120">这会强制驱动程序读取**sql_variant**标头。</span><span class="sxs-lookup"><span data-stu-id="204ed-120">This forces the driver to read the **sql_variant** header.</span></span> <span data-ttu-id="204ed-121">标头在**sql_variant**列中提供该实例的数据类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-121">The header provides the data type of that instance in the **sql_variant** column.</span></span> <span data-ttu-id="204ed-122">**SQLGetData**返回该值)  (的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="204ed-122">**SQLGetData** returns the size (in bytes) of the value.</span></span>  
  
3.  <span data-ttu-id="204ed-123">通过将**SQL_CA_SS_VARIANT_TYPE**指定为其属性值来调用[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) 。</span><span class="sxs-lookup"><span data-stu-id="204ed-123">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) by specifying **SQL_CA_SS_VARIANT_TYPE** as its attribute value.</span></span> <span data-ttu-id="204ed-124">此函数将**sql_variant**列中的实例的 C 数据类型返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="204ed-124">This function will return the C data type of the instance in the **sql_variant** column to the client.</span></span>  
  
 <span data-ttu-id="204ed-125">以下是演示上述步骤的代码片段。</span><span class="sxs-lookup"><span data-stu-id="204ed-125">Here is a code segment showing the preceding steps.</span></span>  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 <span data-ttu-id="204ed-126">如果用户使用[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)创建绑定，则驱动程序将读取元数据和数据。</span><span class="sxs-lookup"><span data-stu-id="204ed-126">If the user creates the binding using [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), the driver reads the metadata and the data.</span></span> <span data-ttu-id="204ed-127">然后，驱动程序将这些数据转换为在绑定中指定的适当 ODBC 类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-127">The driver then converts the data to the appropriate ODBC type specified in the binding.</span></span>  
  
### <a name="sending-data-to-the-server"></a><span data-ttu-id="204ed-128">将数据发送到服务器</span><span class="sxs-lookup"><span data-stu-id="204ed-128">Sending Data to the Server</span></span>  
 <span data-ttu-id="204ed-129">**SQL_SS_VARIANT**，特定于 NATIVE Client ODBC 驱动程序的一种新数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于发送到**sql_variant**列的数据。</span><span class="sxs-lookup"><span data-stu-id="204ed-129">**SQL_SS_VARIANT**, a new data type specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, is used for data sent to an **sql_variant** column.</span></span> <span data-ttu-id="204ed-130">使用参数将数据发送到服务器时 (例如，插入 TableName 值 (?,? ) # A3， [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)用于指定参数信息，包括 C 类型和相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型。</span><span class="sxs-lookup"><span data-stu-id="204ed-130">When sending data to the server using parameters (for example, INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) is used to specify the parameter information including the C type and the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="204ed-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序会将 C 数据类型转换为相应的**sql_variant**子类型之一。</span><span class="sxs-lookup"><span data-stu-id="204ed-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will convert the C data type to one of the appropriate **sql_variant** subtypes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204ed-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="204ed-132">See Also</span></span>  
 [<span data-ttu-id="204ed-133">&#40;ODBC&#41;处理结果</span><span class="sxs-lookup"><span data-stu-id="204ed-133">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
