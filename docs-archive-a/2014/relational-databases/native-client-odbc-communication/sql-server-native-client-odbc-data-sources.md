---
title: SQL Server Native Client ODBC 数据源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6960118e13f0843640b18056bda655726cbbbd29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586642"
---
# <a name="sql-server-native-client-odbc-data-sources"></a><span data-ttu-id="1c2aa-102">SQL Server Native Client ODBC 数据源</span><span class="sxs-lookup"><span data-stu-id="1c2aa-102">SQL Server Native Client ODBC Data Sources</span></span>
  <span data-ttu-id="1c2aa-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源名称 (DSN) 标识 ODBC 数据源，此数据源包含 ODBC 应用程序连接到特定服务器上的某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库所需要的所有信息。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source name (DSN) identifies an ODBC data source containing all of the information that an ODBC application needs to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a specific server.</span></span> <span data-ttu-id="1c2aa-104">您可以通过两种方法定义 ODBC 数据源名称：</span><span class="sxs-lookup"><span data-stu-id="1c2aa-104">There are two ways you can define an ODBC data source name:</span></span>  
  
-   <span data-ttu-id="1c2aa-105">在客户端计算机上，打开 "控制面板" 中的 "管理工具"，然后双击 " \*\* (ODBC) \*\*中的" 数据源 "。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-105">On a client computer, open Administrative Tools in Control Panel, and double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="1c2aa-106">此时将打开 ODBC 数据源管理器，您可以用它来创建 DSN。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-106">This will open the ODBC Data Source Administrator, which you can use to create a DSN.</span></span>  
  
-   <span data-ttu-id="1c2aa-107">在 ODBC 应用程序中，调用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-107">In an ODBC application, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="1c2aa-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源包含：</span><span class="sxs-lookup"><span data-stu-id="1c2aa-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source contains:</span></span>  
  
-   <span data-ttu-id="1c2aa-109">数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-109">The name of the data source.</span></span>  
  
-   <span data-ttu-id="1c2aa-110">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特定实例所需的任何信息。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-110">Any information needed to connect to a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1c2aa-111">要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特定实例上使用的默认数据库（可选）。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-111">The default database to use on a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (optional).</span></span>  
  
-   <span data-ttu-id="1c2aa-112">相关的设置，如要使用的 ANSI 选项、是否记录性能统计信息等等（可选）。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-112">Settings such as which ANSI options to use, whether to log performance statistics, and so on (optional).</span></span>  
  
 <span data-ttu-id="1c2aa-113">不要求将 ODBC 应用程序连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-113">An ODBC application is not required to connect through a data source.</span></span> <span data-ttu-id="1c2aa-114">然而，应用程序必须向 ODBC 连接函数提供适当的连接信息，否则驱动程序将在 DSN 中查找相同的连接信息。</span><span class="sxs-lookup"><span data-stu-id="1c2aa-114">However, the application must provide the same connectivity information to an ODBC connect function that the driver would otherwise find in a DSN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2aa-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c2aa-115">See Also</span></span>  
 [<span data-ttu-id="1c2aa-116">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="1c2aa-116">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
