---
title: ODBC 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1069e31f3f8ffaf14dde091d913ff6d9f8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580825"
---
# <a name="odbc-connection-manager"></a><span data-ttu-id="2622c-102">ODBC 连接管理器</span><span class="sxs-lookup"><span data-stu-id="2622c-102">ODBC Connection Manager</span></span>
  <span data-ttu-id="2622c-103">ODBC 连接管理器使得包能够使用开放式数据库连接规范 (ODBC) 连接到多种数据库管理系统。</span><span class="sxs-lookup"><span data-stu-id="2622c-103">An ODBC connection manager enables a package to connect to a variety of database management systems using the Open Database Connectivity specification (ODBC).</span></span>  
  
 <span data-ttu-id="2622c-104">将 ODBC 连接添加到包并设置连接管理器属性时，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建一个连接管理器，并将该连接管理器添加到 `Connections` 包的集合。</span><span class="sxs-lookup"><span data-stu-id="2622c-104">When you add an ODBC connection to a package and set the connection manager properties, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager and adds the connection manager to the `Connections` collection of the package.</span></span> <span data-ttu-id="2622c-105">该连接管理器在运行时决定物理 ODBC 连接。</span><span class="sxs-lookup"><span data-stu-id="2622c-105">At run time the connection manager is resolved as a physical ODBC connection.</span></span>  
  
 <span data-ttu-id="2622c-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `ODBC`。</span><span class="sxs-lookup"><span data-stu-id="2622c-106">The `ConnectionManagerType` property of the connection manager is set to `ODBC`.</span></span>  
  
 <span data-ttu-id="2622c-107">可以用下列方式配置 ODBC 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="2622c-107">You can configure the ODBC connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2622c-108">提供引用用户名或系统数据源名称的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="2622c-108">Provide a connection string that references a user or system data source name.</span></span>  
  
-   <span data-ttu-id="2622c-109">指定要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="2622c-109">Specify the server to connect to.</span></span>  
  
-   <span data-ttu-id="2622c-110">指示在运行时是否保留连接。</span><span class="sxs-lookup"><span data-stu-id="2622c-110">Indicate whether the connection is retained at run time.</span></span>  
  
## <a name="configuration-of-the-odbc-connection-manager"></a><span data-ttu-id="2622c-111">配置 ODBC 连接管理器</span><span class="sxs-lookup"><span data-stu-id="2622c-111">Configuration of the ODBC Connection Manager</span></span>  
 <span data-ttu-id="2622c-112">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="2622c-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2622c-113">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="2622c-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="2622c-114">ODBC 连接管理器 UI 参考</span><span class="sxs-lookup"><span data-stu-id="2622c-114">ODBC Connection Manager UI Reference</span></span>](../odbc-connection-manager-ui-reference.md)  
  
 <span data-ttu-id="2622c-115">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="2622c-115">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2622c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2622c-116">See Also</span></span>  
 [<span data-ttu-id="2622c-117">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="2622c-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
