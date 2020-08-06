---
title: 字符数据的自动转换 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: rothja
ms.author: jroth
ms.openlocfilehash: 91dd1714d553f201c1cab78bbca77d2445b42923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693829"
---
# <a name="autotranslation-of-character-data"></a><span data-ttu-id="44c49-102">字符数据的自动转换</span><span class="sxs-lookup"><span data-stu-id="44c49-102">Autotranslation of Character Data</span></span>
  <span data-ttu-id="44c49-103">字符数据（如使用 SQL_C_CHAR 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**CHAR**、 **varchar**或**text**数据类型存储在中的数据）声明的字符数据只能表示有限数量的字符。</span><span class="sxs-lookup"><span data-stu-id="44c49-103">Character data, such as ANSI character variables declared with SQL_C_CHAR or data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **char**, **varchar**, or **text** data types, can represent only a limited number of characters.</span></span> <span data-ttu-id="44c49-104">对于每个字符使用一个字节进行存储的字符数据，它只能表示 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="44c49-104">Character data stored using one byte per character can only represent 256 characters.</span></span> <span data-ttu-id="44c49-105">使用客户端计算机的 ANSI 代码页 (ACP) 解释存储在 SQL_C_CHAR 变量中的值。</span><span class="sxs-lookup"><span data-stu-id="44c49-105">The values stored in SQL_C_CHAR variables are interpreted using the ANSI code page (ACP) of the client computer.</span></span> <span data-ttu-id="44c49-106">使用服务器上的**char**、 **varchar**或**text**数据类型存储的值将使用服务器的 ACP 进行计算。</span><span class="sxs-lookup"><span data-stu-id="44c49-106">The values stored using **char**, **varchar**, or **text** data types on the server are evaluated using the ACP of the server.</span></span>  
  
 <span data-ttu-id="44c49-107">如果服务器和客户端具有相同的 ACP，则在解释 SQL_C_CHAR、 **CHAR**、 **varchar**或**text**对象中存储的值时，它们没有任何问题。</span><span class="sxs-lookup"><span data-stu-id="44c49-107">If both the server and the client have the same ACP, then they have no problems in interpreting the values stored in SQL_C_CHAR, **char**, **varchar**, or **text** objects.</span></span> <span data-ttu-id="44c49-108">如果服务器和客户端具有不同的 Acp，则从客户端 SQL_C_CHAR 的数据可能会在服务器上解释为不同的字符（如果在**CHAR**、 **varchar**或**text**列、变量或参数中使用）。</span><span class="sxs-lookup"><span data-stu-id="44c49-108">If the server and client have different ACPs, then SQL_C_CHAR data from the client may be interpreted as a different character on the server if it is used in **char**, **varchar**, or **text** columns, variables, or parameters.</span></span> <span data-ttu-id="44c49-109">例如，包含值0xA5 的字符字节被解释为字符？？。</span><span class="sxs-lookup"><span data-stu-id="44c49-109">For example, a character byte containing the value 0xA5 is interpreted as the character ??</span></span> <span data-ttu-id="44c49-110">在使用代码页437的计算机上，并将其解释为日元符号 (？？在运行代码页1252的计算机上 ) 。</span><span class="sxs-lookup"><span data-stu-id="44c49-110">on a computer using code page 437 and is interpreted as the yen sign (??) on a computer running code page 1252.</span></span>  
  
 <span data-ttu-id="44c49-111">Unicode 数据在存储时每个字符使用两个字节。</span><span class="sxs-lookup"><span data-stu-id="44c49-111">Unicode data is stored using two bytes per character.</span></span> <span data-ttu-id="44c49-112">Unicode 规范涵盖所有扩展字符，因此每一 Unicode 字符都会在所有计算机上解释为相同的字符。</span><span class="sxs-lookup"><span data-stu-id="44c49-112">All extended characters are covered by the Unicode specification, so all Unicode characters are interpreted the same by all computers.</span></span>  
  
 <span data-ttu-id="44c49-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序的 AutoTranslate 功能尝试最大程度地减少在客户端和具有不同代码页的服务器之间移动字符数据的问题。</span><span class="sxs-lookup"><span data-stu-id="44c49-113">The AutoTranslate feature of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to minimize the problems in moving character data between a client and a server that have different code pages.</span></span> <span data-ttu-id="44c49-114">可以在[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)的连接字符串中设置 AutoTranslate，也可以在[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)的配置字符串中设置，也可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 ODBC 管理器为 Native Client ODBC 驱动程序配置数据源时设置。</span><span class="sxs-lookup"><span data-stu-id="44c49-114">AutoTranslate can be set in the connect string of [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), in the configuration string of [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), or when configuring data sources for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver using ODBC Administrator.</span></span>  
  
 <span data-ttu-id="44c49-115">如果将 AutoTranslate 设置为 "no"，则不会对客户端上的 SQL_C_CHAR 变量和数据库中的**CHAR**、 **varchar**或**text**列、变量或参数之间移动的数据进行转换 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44c49-115">When AutoTranslate is set to "no", no conversions are done on data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="44c49-116">如果数据包含扩展字符并且客户端和服务器计算机使用不同的代码页，则位模式在这两台计算机上会得到不同的解释。</span><span class="sxs-lookup"><span data-stu-id="44c49-116">The bit patterns may be interpreted differently on the client and server computers if the data contains extended characters and the two computers have different code pages.</span></span> <span data-ttu-id="44c49-117">如果这两台计算机使用相同的代码页，则数据将得到相同的解释。</span><span class="sxs-lookup"><span data-stu-id="44c49-117">The data will be interpreted the same if both computers have the same code page.</span></span>  
  
 <span data-ttu-id="44c49-118">当 AutoTranslate 设置为 "yes" 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序使用 Unicode 来转换客户端上 SQL_C_CHAR 变量和数据库中的**CHAR**、 **varchar**或**text**列、变量或参数之间移动的数据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="44c49-118">When AutoTranslate is set to "yes", the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses Unicode to convert data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="44c49-119">将数据从客户端上的 SQL_C_CHAR 变量发送到数据库中的**CHAR**、 **varchar**或**text**列、变量或参数时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，ODBC 驱动程序将首先使用客户端的 ACP 从 SQL_C_CHAR 转换为 unicode，然后使用服务器的 ACP 将 unicode 转换回字符。</span><span class="sxs-lookup"><span data-stu-id="44c49-119">When data is sent from an SQL_C_CHAR variable on the client to a **char**, **varchar**, or **text** column, variable, or parameter in an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the ODBC driver first converts from SQL_C_CHAR to Unicode using the ACP of the client, then from Unicode back to character using the ACP of the server.</span></span>  
  
-   <span data-ttu-id="44c49-120">将数据从数据库中的**char**、 **varchar**或**text**列、变量或参数发送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 到客户端上的 SQL_C_CHAR 变量时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序首先使用服务器的 ACP 将字符转换为 Unicode，然后使用客户端的 ACP 将 Unicode 转换回 SQL_C_CHAR。</span><span class="sxs-lookup"><span data-stu-id="44c49-120">When data is sent from a **char**, **varchar**, or **text** column, variable, or parameter in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a SQL_C_CHAR variable on the client, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver first converts from character to Unicode using the ACP of the server, then from Unicode back to SQL_C_CHAR using the ACP of the client.</span></span>  
  
 <span data-ttu-id="44c49-121">由于所有这些转换都是通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在客户端上执行的 Native CLIENT ODBC 驱动程序来完成的，因此服务器 ACP 必须是客户端计算机上安装的代码页之一。</span><span class="sxs-lookup"><span data-stu-id="44c49-121">Because all of these conversions are done by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver executing on the client, the server ACP must be one of the code pages installed on the client computer.</span></span>  
  
 <span data-ttu-id="44c49-122">通过 Unicode 对字符进行转换可确保存在于两个代码页中的所有字符都能得到正确的转换。</span><span class="sxs-lookup"><span data-stu-id="44c49-122">Making the character conversions through Unicode ensures the proper conversion of all characters that exist in both code pages.</span></span> <span data-ttu-id="44c49-123">但是，如果存在于其中一个代码页的某个字符在另一个代码页中不存在，则该字符在目标代码页中将无法表示。</span><span class="sxs-lookup"><span data-stu-id="44c49-123">If a character exists in one code page but not another, however, then the character cannot be represented in the target code page.</span></span> <span data-ttu-id="44c49-124">例如，代码页1252具有注册商标符号 (？？) ，而代码页437则不这样做。</span><span class="sxs-lookup"><span data-stu-id="44c49-124">For example, code page 1252 has the registered trademark symbol (??), while code page 437 does not.</span></span>  
  
 <span data-ttu-id="44c49-125">AutoTranslate 设置对以下转换没有任何影响：</span><span class="sxs-lookup"><span data-stu-id="44c49-125">The AutoTranslate setting has no effect on these conversions:</span></span>  
  
-   <span data-ttu-id="44c49-126">在字符 SQL_C_CHAR 客户端变量和 Unicode **nchar**、 **nvarchar**或**ntext**列、变量或参数之间移动数据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44c49-126">Moving data between character SQL_C_CHAR client variables and Unicode **nchar**, **nvarchar**, or **ntext** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="44c49-127">SQL_C_WCHAR 客户端变量和数据库中的字符**char**、 **varchar**或**text**列、变量或参数之间移动数据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44c49-127">Moving data between Unicode SQL_C_WCHAR client variables and character **char**, **varchar**, or **text** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="44c49-128">在数据从字符移动到 Unicode 时，始终必须对其进行转换。</span><span class="sxs-lookup"><span data-stu-id="44c49-128">Data always must be converted when moved from character to Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c49-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44c49-129">See Also</span></span>  
 <span data-ttu-id="44c49-130">[&#40;ODBC&#41;处理结果](processing-results-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="44c49-130">[Processing Results &#40;ODBC&#41;](processing-results-odbc.md) </span></span>  
 [<span data-ttu-id="44c49-131">排序规则和 Unicode 支持</span><span class="sxs-lookup"><span data-stu-id="44c49-131">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
