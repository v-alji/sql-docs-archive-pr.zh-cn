---
title: 命令语法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: rothja
ms.author: jroth
ms.openlocfilehash: da5ddb75a5c6fc10db031707b7d97ead71363e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693792"
---
# <a name="command-syntax"></a><span data-ttu-id="5c074-102">命令语法</span><span class="sxs-lookup"><span data-stu-id="5c074-102">Command Syntax</span></span>
  <span data-ttu-id="5c074-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序识别 DBGUID_SQL 宏指定的命令语法。</span><span class="sxs-lookup"><span data-stu-id="5c074-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes command syntax specified by the DBGUID_SQL macro.</span></span> <span data-ttu-id="5c074-104">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序，说明符指示 ODBC SQL、ISO 和的综合 [!INCLUDE[tsql](../../includes/tsql-md.md)] 是有效的语法。</span><span class="sxs-lookup"><span data-stu-id="5c074-104">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the specifier indicates that an amalgam of ODBC SQL, ISO, and [!INCLUDE[tsql](../../includes/tsql-md.md)] is valid syntax.</span></span> <span data-ttu-id="5c074-105">例如，以下 SQL 语句使用 ODBC SQL 转义序列指定 LCASE 字符串函数：</span><span class="sxs-lookup"><span data-stu-id="5c074-105">For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:</span></span>  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 <span data-ttu-id="5c074-106">LCASE 返回一个字符串，将所有大写字母字符转换为相应的小写字母字符。</span><span class="sxs-lookup"><span data-stu-id="5c074-106">LCASE returns a character string, converting all uppercase characters to their lowercase equivalents.</span></span> <span data-ttu-id="5c074-107">ISO 字符串函数 LOWER 执行相同的操作，因此以下 SQL 语句是与上述 ODBC 语句等效的 ISO 命令：</span><span class="sxs-lookup"><span data-stu-id="5c074-107">The ISO string function LOWER performs the same operation, so the following SQL statement is a ISO equivalent to the ODBC statement presented above:</span></span>  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 <span data-ttu-id="5c074-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当指定为命令的文本时，Native Client OLE DB 提供程序成功地处理语句的一种形式。</span><span class="sxs-lookup"><span data-stu-id="5c074-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processes either form of the statement successfully when specified as text for a command.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="5c074-109">存储过程</span><span class="sxs-lookup"><span data-stu-id="5c074-109">Stored Procedures</span></span>  
 <span data-ttu-id="5c074-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider 命令执行存储过程时，请在命令文本中使用 ODBC CALL 转义序列。</span><span class="sxs-lookup"><span data-stu-id="5c074-110">When executing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command, use the ODBC CALL escape sequence in the command text.</span></span> <span data-ttu-id="5c074-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]然后，Native Client OLE DB 提供程序使用的远程过程调用机制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 来优化命令处理。</span><span class="sxs-lookup"><span data-stu-id="5c074-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider then uses the remote procedure call mechanism of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="5c074-112">例如，以下 ODBC SQL 语句是比 [!INCLUDE[tsql](../../includes/tsql-md.md)] 形式更常使用的命令文本：</span><span class="sxs-lookup"><span data-stu-id="5c074-112">For example, the following ODBC SQL statement is preferred command text over the [!INCLUDE[tsql](../../includes/tsql-md.md)] form:</span></span>  
  
-   <span data-ttu-id="5c074-113">ODBC SQL</span><span class="sxs-lookup"><span data-stu-id="5c074-113">ODBC SQL</span></span>  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   <span data-ttu-id="5c074-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5c074-114">Transact-SQL</span></span>  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5c074-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c074-115">See Also</span></span>  
 [<span data-ttu-id="5c074-116">命令</span><span class="sxs-lookup"><span data-stu-id="5c074-116">Commands</span></span>](commands.md)  
  
  
