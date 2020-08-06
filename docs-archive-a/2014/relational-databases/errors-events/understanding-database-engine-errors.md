---
title: 了解数据库引擎错误 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa8747066433488a8517d2931ad51f082075a66f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587390"
---
# <a name="understanding-database-engine-errors"></a><span data-ttu-id="6bbf1-102">了解数据库引擎错误</span><span class="sxs-lookup"><span data-stu-id="6bbf1-102">Understanding Database Engine Errors</span></span>
  <span data-ttu-id="6bbf1-103">由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 引起的错误具有下表所述的属性。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-103">Errors raised by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] have the attributes described in the following table.</span></span>  
  
|<span data-ttu-id="6bbf1-104">Attribute</span><span class="sxs-lookup"><span data-stu-id="6bbf1-104">Attribute</span></span>|<span data-ttu-id="6bbf1-105">说明</span><span class="sxs-lookup"><span data-stu-id="6bbf1-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6bbf1-106">错误号</span><span class="sxs-lookup"><span data-stu-id="6bbf1-106">Error number</span></span>|<span data-ttu-id="6bbf1-107">每个错误消息具有唯一的错误号。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-107">Each error message has a unique error number.</span></span>|  
|<span data-ttu-id="6bbf1-108">错误消息字符串</span><span class="sxs-lookup"><span data-stu-id="6bbf1-108">Error message string</span></span>|<span data-ttu-id="6bbf1-109">错误消息包含关于错误原因的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-109">The error message contains diagnostic information about the cause of the error.</span></span> <span data-ttu-id="6bbf1-110">许多错误消息都有替换变量，其中插入了一些信息，如生成错误的对象名称。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-110">Many error messages have substitution variables in which information, such as the name of the object generating the error, is inserted.</span></span>|  
|<span data-ttu-id="6bbf1-111">严重性</span><span class="sxs-lookup"><span data-stu-id="6bbf1-111">Severity</span></span>|<span data-ttu-id="6bbf1-112">严重性指示错误的严重程度。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-112">The severity indicates how serious the error is.</span></span> <span data-ttu-id="6bbf1-113">严重性较低的错误，如 1 级或 2 级，为信息性消息或低级警告。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-113">Errors that have a low severity, such as 1 or 2, are information messages or low-level warnings.</span></span> <span data-ttu-id="6bbf1-114">严重性较高的错误指示需要尽快解决的问题。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-114">Errors that have a high severity indicate problems that should be addressed as soon as possible.</span></span> <span data-ttu-id="6bbf1-115">有关错误严重性的详细信息，请参阅 [数据库引擎错误严重性](database-engine-error-severities.md)。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-115">For more information about severities, see [Database Engine Error Severities](database-engine-error-severities.md).</span></span>|  
|<span data-ttu-id="6bbf1-116">状态</span><span class="sxs-lookup"><span data-stu-id="6bbf1-116">State</span></span>|<span data-ttu-id="6bbf1-117">某些错误消息可能在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]代码中多处出现。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-117">Some error messages can be raised at multiple points in the code for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6bbf1-118">例如，几种不同情况下都可能引发 1105 错误。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-118">For example, an 1105 error can be raised for several different conditions.</span></span> <span data-ttu-id="6bbf1-119">每个引发错误的特定情况都分配唯一的状态代码。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-119">Each specific condition that raises an error assigns a unique state code.</span></span><br /><br /> <span data-ttu-id="6bbf1-120">查看包含已知问题信息的数据库时，如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库，可以使用状态号确定所记录的问题是否与曾遇到的错误相同。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-120">When you are viewing databases that contain information about known issues, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base, you can use the state number to determine whether the recorded issue is the same as the error you have encountered.</span></span> <span data-ttu-id="6bbf1-121">例如，如果一篇知识库文章说明状态为 2 的 1105 错误，而接收到的 1105 错误消息状态为 3，则错误原因可能不同于文章所报告的原因。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-121">For example, if a Knowledge Base Article describes an 1105 error that has a state of 2 and the 1105 error message you received had a state of 3, the error probably has a different cause than the one reported in the article.</span></span><br /><br /> <span data-ttu-id="6bbf1-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 支持工程师也可以用错误中的状态代码在源代码中查找产生错误的位置。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-122">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] support engineer can also use the state code from an error to find the location in the source code where that error code is being raised.</span></span> <span data-ttu-id="6bbf1-123">此信息可能会获取诊断问题所需的更多信息。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-123">This information might provide additional ideas on how to diagnose the problem.</span></span>|  
|<span data-ttu-id="6bbf1-124">过程名称</span><span class="sxs-lookup"><span data-stu-id="6bbf1-124">Procedure name</span></span>|<span data-ttu-id="6bbf1-125">出现错误的存储过程或触发器的名称。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-125">Is the name of the stored procedure or trigger in which the error has occurred.</span></span>|  
|<span data-ttu-id="6bbf1-126">行号</span><span class="sxs-lookup"><span data-stu-id="6bbf1-126">Line number</span></span>|<span data-ttu-id="6bbf1-127">指示在批处理、存储过程、触发器或函数中生成错误的语句。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-127">Indicates which statement in a batch, stored procedure, trigger, or function generated the error.</span></span>|  
  
 <span data-ttu-id="6bbf1-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中所有系统和用户定义的错误消息都包含在 **sys.messages** 目录视图中。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-128">All system and user-defined error messages in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] are contained in the **sys.messages** catalog view.</span></span> <span data-ttu-id="6bbf1-129">可以使用 RAISERROR 语句将用户定义的错误返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-129">You can use the RAISERROR statement to return user-defined errors to an application.</span></span>  
  
 <span data-ttu-id="6bbf1-130">所有数据库 API（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SQLClient 命名空间、ActiveX 数据对象 (ADO)、OLE DB 和开放式数据库连接 (ODBC)）都会报告基本错误属性。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-130">All database APIs, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** namespace, ActiveX Data Objects (ADO), OLE DB, and Open Database Connectivity (ODBC), report the basic error attributes.</span></span> <span data-ttu-id="6bbf1-131">此信息包括错误号和消息字符串。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-131">This information includes the error number and message string.</span></span> <span data-ttu-id="6bbf1-132">但是，并非所有 API 都报告所有其他错误属性。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-132">However, not all the APIs report all the other error attributes.</span></span>  
  
 <span data-ttu-id="6bbf1-133">可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码中使用一些函数（如相关 CATCH 块作用域内的 ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY 和 ERROR_STATE），来获得关于发生在 TRY…CATCH 结构的 TRY 块作用域内的错误信息。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-133">Information about an error that occurs in the scope of the TRY block of a TRY...CATCH construct can be obtained in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by using functions such as ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE in the scope of the associated CATCH block.</span></span> <span data-ttu-id="6bbf1-134">有关详细信息，请参阅 [TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-134">For more information, see [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6bbf1-135">示例</span><span class="sxs-lookup"><span data-stu-id="6bbf1-135">Examples</span></span>  
 <span data-ttu-id="6bbf1-136">下面的示例将查询 `sys.messages` 目录视图以返回具有英文文本 ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] ) 的`1033`中所有系统和用户定义错误消息的列表。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-136">The following example queries the `sys.messages` catalog view to return a list of all system and user-defined error messages in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that have English text (`1033`).</span></span>  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 <span data-ttu-id="6bbf1-137">有关详细信息，请参阅 [sys.messages (Transact-SQL)](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)。</span><span class="sxs-lookup"><span data-stu-id="6bbf1-137">For more information, see [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbf1-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bbf1-138">See Also</span></span>  
 <span data-ttu-id="6bbf1-139">[sys.messages (Transact-SQL)](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span></span>  
 <span data-ttu-id="6bbf1-140">[RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-141">[@@ERROR (Transact-SQL)](/sql/t-sql/functions/error-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-142">[TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-143">[ERROR_LINE (Transact-SQL)](/sql/t-sql/functions/error-line-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-144">[ERROR_MESSAGE (Transact-SQL)](/sql/t-sql/functions/error-message-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-145">[ERROR_NUMBER (Transact-SQL)](/sql/t-sql/functions/error-number-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-146">[ERROR_PROCEDURE (Transact-SQL)](/sql/t-sql/functions/error-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span></span>  
 <span data-ttu-id="6bbf1-147">[ERROR_SEVERITY (Transact-SQL)](/sql/t-sql/functions/error-severity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bbf1-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span></span>  
 [<span data-ttu-id="6bbf1-148">ERROR_STATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6bbf1-148">ERROR_STATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-state-transact-sql)  
  
  
