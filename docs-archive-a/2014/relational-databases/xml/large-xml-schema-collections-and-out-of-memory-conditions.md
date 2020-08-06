---
title: 大型 XML 架构集合和内存不足的情况 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694362"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a><span data-ttu-id="927c4-102">大型 XML 架构集合和内存不足的情况</span><span class="sxs-lookup"><span data-stu-id="927c4-102">Large XML Schema Collections and Out-of-Memory Conditions</span></span>
  <span data-ttu-id="927c4-103">当对大型 XML 架构集合调用内置 XML_SCHEMA_NAMESPACE() 函数时或当您试图删除大型 XML 架构集合时，可能会出现内存不足的情况。</span><span class="sxs-lookup"><span data-stu-id="927c4-103">During a call to the built-in XML_SCHEMA_NAMESPACE() function on a large XML schema collection, or when you try to drop large XML schema collections, an out-of-memory condition may occur.</span></span> <span data-ttu-id="927c4-104">可以使用以下解决方法来处理这种情况：</span><span class="sxs-lookup"><span data-stu-id="927c4-104">The following are solutions you can use to handle this:</span></span>  
  
-   <span data-ttu-id="927c4-105">在系统负荷较少时，请使用 DROP_XML_SCHEMA_COLLECTION 命令。</span><span class="sxs-lookup"><span data-stu-id="927c4-105">When the system load is light, use the DROP_XML_SCHEMA_COLLECTION command.</span></span> <span data-ttu-id="927c4-106">如果该命令执行失败，则请使用 ALTER DATABASE 语句将数据库置于单用户模式，然后再次尝试 DROP XML SCHEMA COLLECTION 命令。</span><span class="sxs-lookup"><span data-stu-id="927c4-106">If this fails, put the database in single-user mode by using the ALTER DATABASE statement and trying DROP XML SCHEMA COLLECTION again.</span></span> <span data-ttu-id="927c4-107">如果 XML 架构集合存在于 **master**、 **model**或 **tempdb**中，则单用户模式还要求重启服务器。</span><span class="sxs-lookup"><span data-stu-id="927c4-107">If the XML schema collection exists in **master**, **model**, or **tempdb**, a server restart is required for single-user mode.</span></span>  
  
-   <span data-ttu-id="927c4-108">当调用 XML_SCHEMA_NAMESPACE 时，您可以尝试检索单个 XML 架构命名空间，或者您也可以在系统负荷更少时尝试调用，或者您还可以在单用户模式下尝试调用。</span><span class="sxs-lookup"><span data-stu-id="927c4-108">When you call the XML_SCHEMA_NAMESPACE, you can try to retrieve a single XML schema namespace, you can try the call when the system load is lighter, or you can try the call in single-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927c4-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="927c4-109">See Also</span></span>  
 [<span data-ttu-id="927c4-110">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="927c4-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
