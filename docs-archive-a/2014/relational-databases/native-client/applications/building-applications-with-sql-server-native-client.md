---
title: 构建具有 SQL Server Native Client 的应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
author: rothja
ms.author: jroth
ms.openlocfilehash: d08fe1042ab1a79f6b48648f5a774b4fbac49ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587776"
---
# <a name="building-applications-with-sql-server-native-client"></a><span data-ttu-id="26b89-102">使用 SQL Server Native Client 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="26b89-102">Building Applications with SQL Server Native Client</span></span>
  <span data-ttu-id="26b89-103">开发使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 库的应用程序时，会出现很多问题。</span><span class="sxs-lookup"><span data-stu-id="26b89-103">When developing an application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library, there are a number of issues that come into play.</span></span> <span data-ttu-id="26b89-104">本节中的主题讨论了多个此类问题，包括如何从 MDAC 升级到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 头文件和库文件，以及可用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的各种连接字符串的概述。</span><span class="sxs-lookup"><span data-stu-id="26b89-104">The topics in this section discuss many of these issues including upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files, and an overview of the various connection strings that can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26b89-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="26b89-105">In This Section</span></span>  
 [<span data-ttu-id="26b89-106">安装 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="26b89-106">Installing SQL Server Native Client</span></span>](installing-sql-server-native-client.md)  
 <span data-ttu-id="26b89-107">讨论如何安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，各种组件安装到的位置以及如何卸载 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="26b89-107">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is installed, the locations that various components are installed to, and how to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="26b89-108">SQL Server Native Client 的组件</span><span class="sxs-lookup"><span data-stu-id="26b89-108">Components of SQL Server Native Client</span></span>](components-of-sql-server-native-client.md)  
 <span data-ttu-id="26b89-109">讨论组成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的组件，包括库、资源、帮助和头文件。</span><span class="sxs-lookup"><span data-stu-id="26b89-109">Discusses the components that make up [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client including library, resource, help, and header files.</span></span>  
  
 [<span data-ttu-id="26b89-110">将连接字符串关键字用于 SQL Server 本机客户端</span><span class="sxs-lookup"><span data-stu-id="26b89-110">Using Connection String Keywords with SQL Server Native Client</span></span>](using-connection-string-keywords-with-sql-server-native-client.md)  
 <span data-ttu-id="26b89-111">讨论通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 连接到数据库时可以使用的各种类型的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="26b89-111">Discusses the various types of connection strings that can be used when connecting to a database through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="26b89-112">使用 SQL Server Native Client 头文件和库文件</span><span class="sxs-lookup"><span data-stu-id="26b89-112">Using the SQL Server Native Client Header and Library Files</span></span>](using-the-sql-server-native-client-header-and-library-files.md)  
 <span data-ttu-id="26b89-113">讨论如何在应用程序中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 头文件和库文件。</span><span class="sxs-lookup"><span data-stu-id="26b89-113">Discusses how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files within an application.</span></span>  
  
 [<span data-ttu-id="26b89-114">将应用程序从 MDAC 更新到 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="26b89-114">Updating an Application to SQL Server Native Client from MDAC</span></span>](updating-an-application-to-sql-server-native-client-from-mdac.md)  
 <span data-ttu-id="26b89-115">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 和 MDAC 之间的区别，以及从 MDAC 升级到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 时应考虑的问题。</span><span class="sxs-lookup"><span data-stu-id="26b89-115">Discusses the differences between [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and MDAC and issues that should be considered when upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="26b89-116">从 SQL Server 2005 Native Client 更新应用程序</span><span class="sxs-lookup"><span data-stu-id="26b89-116">Updating an Application from SQL Server 2005 Native Client</span></span>](updating-an-application-from-sql-server-2005-native-client.md)  
 <span data-ttu-id="26b89-117">讨论从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client 升级到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client 时应该考虑的问题。</span><span class="sxs-lookup"><span data-stu-id="26b89-117">Discusses issues that should be considered when upgrading from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="26b89-118">将 ADO 用于 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="26b89-118">Using ADO with SQL Server Native Client</span></span>](using-ado-with-sql-server-native-client.md)  
 <span data-ttu-id="26b89-119">讨论 ADO 如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 访问和使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="26b89-119">Discusses how ADO can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access and use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
 [<span data-ttu-id="26b89-120">SQL Server Native Client 的支持策略</span><span class="sxs-lookup"><span data-stu-id="26b89-120">Support Policies for SQL Server Native Client</span></span>](support-policies-for-sql-server-native-client.md)  
 <span data-ttu-id="26b89-121">讨论如何将各种数据访问组件与不同版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 一起使用。</span><span class="sxs-lookup"><span data-stu-id="26b89-121">Discusses how various data-access components can be used with different versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="26b89-122">使用 SQL Server Native Client 连接到 Azure SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="26b89-122">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>](connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 <span data-ttu-id="26b89-123">讨论如何使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26b89-123">Discusses how to connect to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b89-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26b89-124">See Also</span></span>  
 <span data-ttu-id="26b89-125">[SQL Server Native Client 编程](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="26b89-125">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="26b89-126">[ODBC 操作指南主题](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="26b89-126">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="26b89-127">OLE DB 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="26b89-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
