---
title: 命令参数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591883"
---
# <a name="command-parameters"></a><span data-ttu-id="35eaa-102">命令参数</span><span class="sxs-lookup"><span data-stu-id="35eaa-102">Command Parameters</span></span>
  <span data-ttu-id="35eaa-103">在命令文本中参数用问号字符标记。</span><span class="sxs-lookup"><span data-stu-id="35eaa-103">Parameters are marked in command text with the question mark character.</span></span> <span data-ttu-id="35eaa-104">例如，以下 SQL 语句标记了单个输入参数：</span><span class="sxs-lookup"><span data-stu-id="35eaa-104">For example, the following SQL statement is marked for a single input parameter:</span></span>  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 <span data-ttu-id="35eaa-105">为了通过减少网络流量提高性能， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 除非在执行命令之前调用**ICommandWithParameters：： GetParameterInfo**或**ICommandPrepare：:P 准备**，否则 Native Client OLE DB 提供程序不会自动派生参数信息。</span><span class="sxs-lookup"><span data-stu-id="35eaa-105">To improve performance by reducing network traffic, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically derive parameter information unless **ICommandWithParameters::GetParameterInfo** or **ICommandPrepare::Prepare** is called before executing a command.</span></span> <span data-ttu-id="35eaa-106">这意味着 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不会自动执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="35eaa-106">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically:</span></span>  
  
-   <span data-ttu-id="35eaa-107">验证使用 ICommandWithParameters::SetParameterInfo 指定的数据类型的正确性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-107">Verify the correctness of the data type specified with **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="35eaa-108">将取值函数绑定信息中指定的 DBTYPE 映射到参数的正确 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="35eaa-108">Map from the DBTYPE specified in the accessor binding information to the correct [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter.</span></span>  
  
 <span data-ttu-id="35eaa-109">如果这两个方法指定的数据类型与参数的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型不兼容，那么应用程序在使用该方法时将可能收到错误或产生精度损失。</span><span class="sxs-lookup"><span data-stu-id="35eaa-109">Applications will receive possible errors or loss of precision with either of these methods if they specify data types that are not compatible with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the parameter.</span></span>  
  
 <span data-ttu-id="35eaa-110">若要确保不发生这种情况，应用程序应当：</span><span class="sxs-lookup"><span data-stu-id="35eaa-110">To ensure this does not happen, the application should:</span></span>  
  
-   <span data-ttu-id="35eaa-111">如果硬编码 ICommandWithParameters::SetParameterInfo，则应确保 pwszDataSourceType 与参数的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型匹配\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-111">Ensure that *pwszDataSourceType* matches the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="35eaa-112">如果硬编码取值函数，则应确保绑定到参数的 DBTYPE 值与参数的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型具有相同类型。</span><span class="sxs-lookup"><span data-stu-id="35eaa-112">Ensure that the DBTYPE value being bound to the parameter is of the same type as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding an accessor.</span></span>  
  
-   <span data-ttu-id="35eaa-113">对应用程序进行编码以调用 ICommandWithParameters::GetParameterInfo，以便访问接口可以动态获取参数的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-113">Code the application to call **ICommandWithParameters::GetParameterInfo** so that the provider can obtain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types of the parameters dynamically.</span></span> <span data-ttu-id="35eaa-114">请注意，这会导致与服务器之间额外的网络往返。</span><span class="sxs-lookup"><span data-stu-id="35eaa-114">Note that this causes an extra network round trip to the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35eaa-115">对于包含 FROM 子句的任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE 或 DELETE 语句，对于依赖于包含参数的子查询的任意 SQL 语句，对于在比较和类似表达式中包含参数标记或包含限定谓词的 SQL 语句，或其参数之一为函数参数的查询，访问接口不支持调用 ICommandWithParameters::GetParameterInfo\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-115">The provider does not support calling **ICommandWithParameters::GetParameterInfo** for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE or DELETE statement containing a FROM clause; for any SQL statement depending on a subquery containing parameters; for SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate; or queries where one of the parameters is a parameter to a function.</span></span> <span data-ttu-id="35eaa-116">在对 SQL 语句进行批处理时，对于批处理中第一个语句后的语句中的参数标记，访问接口也不支持调用 ICommandWithParameters::GetParameterInfo\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-116">When processing a batch of SQL statements, the provider also does not support calling **ICommandWithParameters::GetParameterInfo** for parameter markers in statements after the first statement in the batch.</span></span> <span data-ttu-id="35eaa-117">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令中不允许使用注释 (/\* \*/)。</span><span class="sxs-lookup"><span data-stu-id="35eaa-117">Comments (/\* \*/) are not allowed in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="35eaa-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持 SQL 语句命令中的输入参数。</span><span class="sxs-lookup"><span data-stu-id="35eaa-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input parameters in SQL statement commands.</span></span> <span data-ttu-id="35eaa-119">在过程调用命令中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序支持输入参数、输出参数和输入/输出参数。</span><span class="sxs-lookup"><span data-stu-id="35eaa-119">On procedure-call commands, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input, output, and input/output parameters.</span></span> <span data-ttu-id="35eaa-120">输出参数值在运行时（仅当没有行集返回时）或当应用程序用尽返回的所有行集时，返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="35eaa-120">Output parameter values are returned to the application either on execution (only if there are no rowsets returned) or when all returned rowsets are exhausted by the application.</span></span> <span data-ttu-id="35eaa-121">若要确保返回值有效，可使用 IMultipleResults 强制使用行集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35eaa-121">To ensure that returned values are valid, use **IMultipleResults** to force rowset consumption.</span></span>  
  
 <span data-ttu-id="35eaa-122">在 DBPARAMBINDINFO 结构中无需指定存储过程参数的名称。</span><span class="sxs-lookup"><span data-stu-id="35eaa-122">The names of stored procedure parameters need not be specified in a DBPARAMBINDINFO structure.</span></span> <span data-ttu-id="35eaa-123">使用 NULL 作为*pwszName*成员的值，以指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序应忽略参数名，并且仅使用**ICommandWithParameters：： SetParameterInfo**的*rgParamOrdinals*成员中指定的序号。</span><span class="sxs-lookup"><span data-stu-id="35eaa-123">Use NULL for the value of the *pwszName* member to indicate that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider should ignore the parameter name and use only the ordinal specified in the *rgParamOrdinals* member of **ICommandWithParameters::SetParameterInfo**.</span></span> <span data-ttu-id="35eaa-124">如果命令文本中既包含命名参数又包含未命名参数，则必须在所有命名参数之前指定所有未命名参数。</span><span class="sxs-lookup"><span data-stu-id="35eaa-124">If the command text contains both named and unnamed parameters, all of the unnamed parameters must be specified before any named parameters.</span></span>  
  
 <span data-ttu-id="35eaa-125">如果指定了存储过程参数的名称，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将检查该名称，以确保该名称有效。</span><span class="sxs-lookup"><span data-stu-id="35eaa-125">If the name of a stored procedure parameter is specified, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks the name to ensure that it is valid.</span></span> <span data-ttu-id="35eaa-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当 Native Client OLE DB 提供程序从使用者接收到错误的参数名称时，它将返回错误。</span><span class="sxs-lookup"><span data-stu-id="35eaa-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error when it receives an erroneous parameter name from the consumer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35eaa-127">为了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (UDT) 公开对 XML 和用户定义类型的支持， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序实现新的[ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="35eaa-127">To expose support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements a new [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35eaa-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35eaa-128">See Also</span></span>  
 [<span data-ttu-id="35eaa-129">命令</span><span class="sxs-lookup"><span data-stu-id="35eaa-129">Commands</span></span>](commands.md)  
  
  
