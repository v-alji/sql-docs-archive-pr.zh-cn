---
title: 何时使用 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: rothja
ms.author: jroth
ms.openlocfilehash: f8aeb34525bbe5c1b003e8fd95e7a414025965a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580702"
---
# <a name="when-to-use-sql-server-native-client"></a><span data-ttu-id="92f23-102">何时使用 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="92f23-102">When to Use SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92f23-103">Native Client 是可用于访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中的数据的一种技术。</span><span class="sxs-lookup"><span data-stu-id="92f23-103">Native Client is one technology that you can use to access data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  <span data-ttu-id="92f23-104">有关不同数据访问技术的讨论，请参阅[数据访问技术路线图](https://go.microsoft.com/fwlink/?LinkID=179186)</span><span class="sxs-lookup"><span data-stu-id="92f23-104">For a discussion of the different data-access technologies, see [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186)</span></span>  
  
 <span data-ttu-id="92f23-105">在决定是否使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 作为应用程序的数据访问技术时，应当考虑多种因素。</span><span class="sxs-lookup"><span data-stu-id="92f23-105">When deciding whether to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client as the data access technology of your application, you should consider several factors.</span></span>  
  
 <span data-ttu-id="92f23-106">对于新的应用程序，如果使用的是托管编程语言，如 Microsoft Visual C# 或 Visual Basic，且需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的新功能，那么应当使用用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 .NET Framework 数据访问接口，该接口是用于 .NET Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="92f23-106">For new applications, if you're using a managed programming language such as Microsoft Visual C# or Visual Basic, and you need to access the new features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which is part of the .NET Framework.</span></span>  
  
 <span data-ttu-id="92f23-107">如果要开发基于 COM 的应用程序，且需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中引入的新功能，则应当使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="92f23-107">If you are developing a COM-based application and need to access the new features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="92f23-108">如果不需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能，则可以继续使用 Windows 数据访问组件 (WDAC)。</span><span class="sxs-lookup"><span data-stu-id="92f23-108">If you don't need access to the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use Windows Data Access Components (WDAC).</span></span>  
  
 <span data-ttu-id="92f23-109">对于现有的 OLE DB 和 ODBC 应用程序，主要问题在于是否需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能。</span><span class="sxs-lookup"><span data-stu-id="92f23-109">For existing OLE DB and ODBC applications, the primary issue is whether you need to access the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="92f23-110">如果已有不需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能的成熟应用程序，那么可以继续使用 WDAC。</span><span class="sxs-lookup"><span data-stu-id="92f23-110">If you have a mature application that does not need the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use WDAC.</span></span> <span data-ttu-id="92f23-111">但是，如果确实需要访问这些新功能，如[xml 数据类型](/sql/t-sql/xml/xml-transact-sql)，则应使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="92f23-111">But if you do need to access those new features, such as the [xml data type](/sql/t-sql/xml/xml-transact-sql), you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="92f23-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 MDAC 都支持使用行版本控制的已提交读事务隔离，但只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 支持快照事务隔离。</span><span class="sxs-lookup"><span data-stu-id="92f23-112">Both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC support read committed transaction isolation using row versioning, but only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supports snapshot transaction isolation.</span></span> <span data-ttu-id="92f23-113">（从编程的角度而言，具有行版本控制的已提交读事务隔离等同于已提交读事务。）</span><span class="sxs-lookup"><span data-stu-id="92f23-113">(In programming terms, read committed transaction isolation with row versioning is the same as Read-Committed transaction.)</span></span>  
  
 <span data-ttu-id="92f23-114">有关 Native Client 和 MDAC 之间的差异的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[将应用程序更新为从 MDAC SQL Server Native Client](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)。</span><span class="sxs-lookup"><span data-stu-id="92f23-114">For information about the differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC, see [Updating an Application to SQL Server Native Client from MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f23-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92f23-115">See Also</span></span>  
 <span data-ttu-id="92f23-116">[SQL Server Native Client 编程](../../relational-databases/native-client/sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="92f23-116">[SQL Server Native Client Programming](../../relational-databases/native-client/sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="92f23-117">[ODBC 操作指南主题](../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="92f23-117">[ODBC How-to Topics](../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="92f23-118">OLE DB 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="92f23-118">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
