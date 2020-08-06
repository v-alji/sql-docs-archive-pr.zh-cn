---
title: SQL Server ADO.NET 中特定于进程的扩展 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: 37d8aedc1d8f93739c2e9386665adfc67b43e312
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590868"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a><span data-ttu-id="17843-102">SQL Server 进程内专用的 ADO.NET 扩展</span><span class="sxs-lookup"><span data-stu-id="17843-102">SQL Server In-Process Specific Extensions to ADO.NET</span></span>
  <span data-ttu-id="17843-103">主要有四种专门在进程内使用的 ADO.NET 功能性扩展。</span><span class="sxs-lookup"><span data-stu-id="17843-103">There are four main functional extensions to ADO.NET that are specifically for in-process use.</span></span> <span data-ttu-id="17843-104">下列主题将详细地介绍这些扩展功能。</span><span class="sxs-lookup"><span data-stu-id="17843-104">The following topics will cover these extensions in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17843-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="17843-105">In This Section</span></span>  
 [<span data-ttu-id="17843-106">SqlContext 对象</span><span class="sxs-lookup"><span data-stu-id="17843-106">SqlContext Object</span></span>](sqlcontext-object.md)  
 <span data-ttu-id="17843-107">该类通过提取在进程内执行托管代码的 SQL Server 例程的调用方上下文来提供对其他扩展功能的访问。</span><span class="sxs-lookup"><span data-stu-id="17843-107">This class provides access to the other extensions by abstracting the context of a caller of a SQL Server routine that executes managed code in-process.</span></span>  
  
 [<span data-ttu-id="17843-108">SqlPipe 对象</span><span class="sxs-lookup"><span data-stu-id="17843-108">SqlPipe Object</span></span>](sqlpipe-object.md)  
 <span data-ttu-id="17843-109">该类包含向客户端发送表格式结果和消息的例程。</span><span class="sxs-lookup"><span data-stu-id="17843-109">This class contains routines to send tabular results and messages to the client.</span></span>  
  
 [<span data-ttu-id="17843-110">SqlTriggerContext 对象</span><span class="sxs-lookup"><span data-stu-id="17843-110">SqlTriggerContext Object</span></span>](sqltriggercontext-object.md)  
 <span data-ttu-id="17843-111">该类提供触发器运行所在的上下文的信息。</span><span class="sxs-lookup"><span data-stu-id="17843-111">This class provides information on the context in which a trigger is run.</span></span>  
  
 [<span data-ttu-id="17843-112">SqlDataRecord 对象</span><span class="sxs-lookup"><span data-stu-id="17843-112">SqlDataRecord Object</span></span>](sqldatarecord-object.md)  
 <span data-ttu-id="17843-113">SqlDataRecord 类表示一行数据及其相关元数据，并允许存储过程将自定义结果集返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="17843-113">The SqlDataRecord class represents a single row of data, along with its related metadata, and allows stored procedures to return custom result sets to the client.</span></span>  
  
  
