---
title: XML 系统存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: rothja
ms.author: jroth
ms.openlocfilehash: 2008294fe5bc532dfb6883656420b4189e4da7b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588370"
---
# <a name="xml-system-stored-procedures"></a><span data-ttu-id="a7a6d-102">XML 系统存储过程</span><span class="sxs-lookup"><span data-stu-id="a7a6d-102">XML System Stored Procedures</span></span>
  <span data-ttu-id="a7a6d-103">SQL Server 提供了下列系统存储过程，可以与 OPENXML 一起使用：</span><span class="sxs-lookup"><span data-stu-id="a7a6d-103">SQL Server provides the following system stored procedures that are used together with OPENXML:</span></span>  
  
-   [<span data-ttu-id="a7a6d-104">sp_xml_preparedocument (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a7a6d-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [<span data-ttu-id="a7a6d-105">sp_xml_removedocument (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a7a6d-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 <span data-ttu-id="a7a6d-106">若要使用 OPENXML 编写查询，必须先通过调用 **sp_xml_preparedocument**来创建 XML 文档的内部表示形式。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-106">To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp_xml_preparedocument**.</span></span> <span data-ttu-id="a7a6d-107">该存储过程将返回 XML 文档的内部表示形式的句柄。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-107">The stored procedure returns a handle to the internal representation of the XML document.</span></span> <span data-ttu-id="a7a6d-108">然后，将此句柄传递到 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-108">This handle is then passed to OPENXML.</span></span> <span data-ttu-id="a7a6d-109">OPENXML 将提供基于 XPath 的文档的行集视图。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-109">OPENXML provides rowset views of the document based on XPaths.</span></span> <span data-ttu-id="a7a6d-110">具体而言，是一个行模式和一个或多个列模式。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-110">Specifically, this is one row pattern and one or more column patterns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7a6d-111">**sp_xml_preparedocument** 返回的文档句柄在会话的持续时间内有效。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-111">The document handle that is returned by **sp_xml_preparedocument** is valid for the duration of the session.</span></span>  
  
 <span data-ttu-id="a7a6d-112">通过调用 **sp_xml_removedocument** 系统存储过程可以从内存中删除 XML 文档的内部表示形式。</span><span class="sxs-lookup"><span data-stu-id="a7a6d-112">The internal representation of an XML document can be removed from memory by calling the **sp_xml_removedocument** system stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a6d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7a6d-113">See Also</span></span>  
 <span data-ttu-id="a7a6d-114">[OPENXML (Transact-SQL)](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7a6d-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="a7a6d-115">OPENXML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a7a6d-115">OPENXML &#40;SQL Server&#41;</span></span>](../xml/openxml-sql-server.md)  
  
  
