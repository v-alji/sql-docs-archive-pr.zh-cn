---
title: ISO 选项的效果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 79deff1d77f4020aa7484629bac78d360ed7691f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577606"
---
# <a name="effects-of-iso-options"></a><span data-ttu-id="ba310-102">ISO 选项的作用</span><span class="sxs-lookup"><span data-stu-id="ba310-102">Effects of ISO Options</span></span>
  <span data-ttu-id="ba310-103">ODBC 标准与 ISO 标准十分相似，而且 ODBC 应用程序期望 ODBC 驱动程序能提供标准行为。</span><span class="sxs-lookup"><span data-stu-id="ba310-103">The ODBC standard is closely matched to the ISO standard, and ODBC applications expect standard behavior from an ODBC driver.</span></span> <span data-ttu-id="ba310-104">为了使其行为符合 ODBC 标准中定义的行为， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序始终使用其连接 SQL Server 版本中提供的任何 ISO 选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-104">To make its behavior conform more closely with that defined in the ODBC standard, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver always uses any ISO options available in the version of SQL Server with which it connects.</span></span>  
  
 <span data-ttu-id="ba310-105">当 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT odbc 驱动程序连接到实例时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，服务器会检测到客户端正在使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client odbc 驱动程序并在上设置了几个选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-105">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server detects that the client is using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and sets several options on.</span></span>  
  
 <span data-ttu-id="ba310-106">驱动程序将自己发出这些语句；ODBC 应用程序不会做任何工作以请求它们。</span><span class="sxs-lookup"><span data-stu-id="ba310-106">The driver issues these statements itself; the ODBC application does nothing to request them.</span></span> <span data-ttu-id="ba310-107">设置这些选项可提高使用驱动程序的 ODBC 应用程序的可移植性，因为服务器的行为将与 ISO 标准保持一致。</span><span class="sxs-lookup"><span data-stu-id="ba310-107">Setting these options allows ODBC applications using the driver to be more portable because the server behavior then matches the ISO standard.</span></span>  
  
 <span data-ttu-id="ba310-108">基于 DB-Library 的应用程序通常不会打开这些选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-108">DB-Library-based applications generally do not turn these options on.</span></span> <span data-ttu-id="ba310-109">当运行相同的 SQL 语句时，在 ODBC 或 DB-LIBRARY 客户端之间观察不同行为的站点不应假定这一点指向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序的问题。</span><span class="sxs-lookup"><span data-stu-id="ba310-109">Sites observing different behavior between ODBC or DB-Library clients when running the same SQL statement should not assume this points to a problem with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="ba310-110">它们应该首先使用与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序所用的相同的 SET 选项在 db-library 环境中重新运行该语句。</span><span class="sxs-lookup"><span data-stu-id="ba310-110">They should first rerun the statement in the DB-Library environment with the same SET options as would be used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="ba310-111">由于用户和应用程序可能会随时打开和关闭 SET 选项，存储过程和触发器的开发人员还应分别在上面列出的 SET 选项处于打开和关闭状态的情况下对其存储过程和触发器进行认真测试。</span><span class="sxs-lookup"><span data-stu-id="ba310-111">Because SET options can be turned on and off at any time by users and applications, developers of stored procedures and triggers should also take care to test their procedures and triggers with the SET options listed above turned both on and off.</span></span> <span data-ttu-id="ba310-112">这可以确保存储过程和触发器正常工作，而无论特定连接在调用过程和触发器时打开哪些选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-112">This ensures that the procedures and triggers work correctly regardless of which options a particular connection may have set on when they invoke the procedure or trigger.</span></span> <span data-ttu-id="ba310-113">如果存储过程或触发器需要对这些选项之一进行特殊设置，则应该在触发器或存储过程的开始处发出 SET 语句。</span><span class="sxs-lookup"><span data-stu-id="ba310-113">Triggers or stored procedures that require a particular setting for one of these options should issue a SET statement at the start of the trigger or stored procedure.</span></span> <span data-ttu-id="ba310-114">此 SET 语句仅在触发器或存储过程执行期间保持有效；过程或触发器结束后，即会还原原始设置。</span><span class="sxs-lookup"><span data-stu-id="ba310-114">This SET statement remains in effect only for the execution of the trigger or stored procedure; when the procedure or trigger ends, the original setting is restored.</span></span>  
  
 <span data-ttu-id="ba310-115">在连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例时，还会打开第四个 SET 选项 (CONCAT_NULL_YIELDS_NULL)。</span><span class="sxs-lookup"><span data-stu-id="ba310-115">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a fourth SET option, CONCAT_NULL_YIELDS_NULL, is also set on.</span></span> <span data-ttu-id="ba310-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]如果在数据源中或在[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)或[SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)中指定了 AnsiNPW = NO，则 Native Client ODBC 驱动程序不会将这些选项设置为 on。</span><span class="sxs-lookup"><span data-stu-id="ba310-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not set these options on if AnsiNPW=NO is specified in the data source or on either [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) or [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).</span></span>  
  
 <span data-ttu-id="ba310-117">与前面提到的 ISO 选项一样， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序不会在数据源中或在**SQLDriverConnect**或**SQLBrowseConnect**中指定 QuotedID = NO 时打开 QUOTED_IDENTIFIER 选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-117">Like the ISO options noted earlier, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not turn the QUOTED_IDENTIFIER option on if QuotedID=NO is specified in the data source or on either **SQLDriverConnect** or **SQLBrowseConnect**.</span></span>  
  
 <span data-ttu-id="ba310-118">若要使驱动程序能够了解 SET 选项的当前状态，ODBC 应用程序不应使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET 语句设置这些选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-118">To allow the driver to know the current state of SET options, ODBC applications should not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET statement to set these options.</span></span> <span data-ttu-id="ba310-119">它们只应使用数据源或连接选项设置这些选项。</span><span class="sxs-lookup"><span data-stu-id="ba310-119">They should only set these options using either the data source or the connection options.</span></span> <span data-ttu-id="ba310-120">如果应用程序发出 SET 语句，则驱动程序可能会生成错误的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ba310-120">If the application issues SET statements, the driver can generate incorrect SQL statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba310-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba310-121">See Also</span></span>  
 <span data-ttu-id="ba310-122">[&#40;ODBC&#41;执行语句](executing-statements-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="ba310-122">[Executing Statements &#40;ODBC&#41;](executing-statements-odbc.md) </span></span>  
 <span data-ttu-id="ba310-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span><span class="sxs-lookup"><span data-stu-id="ba310-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span></span>  
 [<span data-ttu-id="ba310-124">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="ba310-124">SQLBrowseConnect</span></span>](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
