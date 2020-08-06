---
title: 开发人员&#39;指南 (数据库引擎) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server Database Engine]
- Database Engine [SQL Server], development
ms.assetid: 7638f46c-9e66-48e6-9a9b-425e0b788311
author: rothja
ms.author: jroth
ms.openlocfilehash: e1f8c8022422def83229b72c6b6a061f12755328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590862"
---
# <a name="developer39s-guide-database-engine"></a><span data-ttu-id="af5ec-102">开发人员&#39;指南 (数据库引擎) </span><span class="sxs-lookup"><span data-stu-id="af5ec-102">Developer&#39;s Guide (Database Engine)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="af5ec-103">提供了大量用于开发、管理和控制数据库应用程序的工具。</span><span class="sxs-lookup"><span data-stu-id="af5ec-103">provides a rich set of tools for developing, administering, and controlling database applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af5ec-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="af5ec-104">In This Section</span></span>  
 [<span data-ttu-id="af5ec-105">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="af5ec-105">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
 <span data-ttu-id="af5ec-106">说明 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows .NET Framework 的公共语言运行时 (CLR) 组件如何与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 集成。</span><span class="sxs-lookup"><span data-stu-id="af5ec-106">Describes the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af5ec-107">这表示您可以使用任何 .NET Framework 语言（包括 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#）编写存储过程、触发器、用户定义类型、用户定义函数、用户定义聚合和流式表值函数。</span><span class="sxs-lookup"><span data-stu-id="af5ec-107">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 [<span data-ttu-id="af5ec-108">SQL Server Native Client 编程</span><span class="sxs-lookup"><span data-stu-id="af5ec-108">SQL Server Native Client Programming</span></span>](native-client/sql-server-native-client-programming.md)  
 <span data-ttu-id="af5ec-109">说明如何使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 新建应用程序或增强现有应用程序，使这些应用程序能够利用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 新增功能，例如多个活动结果集 (MARS)、用户定义数据类型 (UDT)、查询通知、快照隔离和 XML 数据类型支持。</span><span class="sxs-lookup"><span data-stu-id="af5ec-109">Describes how [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client can be used to create new applications or enhance existing applications to take advantage of new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features such as multiple active result sets (MARS), user-defined data types (UDT), query notifications, snapshot isolation, and XML data type support.</span></span>  
  
 [<span data-ttu-id="af5ec-110">SQLXML 4.0 编程概念</span><span class="sxs-lookup"><span data-stu-id="af5ec-110">SQLXML 4.0 Programming Concepts</span></span>](sqlxml/sqlxml-4-0-programming-concepts.md)  
 <span data-ttu-id="af5ec-111">说明 SQLXML 的最新版本，该版本提供与 SQLXML 3.0 相同的功能，另外还提供附加的更新以容纳随 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 引入的新功能，如 xml 数据类型。</span><span class="sxs-lookup"><span data-stu-id="af5ec-111">Describes the latest version of SQLXML, which delivers the same functionality as SQLXML 3.0 as well as additional updates to accommodate new features introduced in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], such as the xml data type.</span></span>  
  
 [<span data-ttu-id="af5ec-112">用于配置管理的 WMI 提供程序的概念</span><span class="sxs-lookup"><span data-stu-id="af5ec-112">WMI Provider for Configuration Management Concepts</span></span>](wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
 <span data-ttu-id="af5ec-113">描述用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Microsoft 管理控制台 (MMC) 和 Configuration Manager 的 Configuration Manager 管理单元的已发布层 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="af5ec-113">Describes a published layer that is used with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager snap-in for Microsoft Management Console (MMC) and the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="af5ec-114">它提供了一种统一的方式，用于与管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器所请求注册表操作的 API 调用进行连接，并可对选定的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务提供增强的控制和操作。</span><span class="sxs-lookup"><span data-stu-id="af5ec-114">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
 [<span data-ttu-id="af5ec-115">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="af5ec-115">WMI Provider for Server Events Concepts</span></span>](wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
 <span data-ttu-id="af5ec-116">说明如何使用 Windows Management Instrumentation (WMI) 在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中监视事件。</span><span class="sxs-lookup"><span data-stu-id="af5ec-116">Describes how to use Windows Management Instrumentation (WMI) to monitor events in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="af5ec-117">SQL Server 管理对象 (SMO) 编程指南</span><span class="sxs-lookup"><span data-stu-id="af5ec-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
 <span data-ttu-id="af5ec-118">包含有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理对象 (SMO) 的信息，它是专为对管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 所涉及的各个方面进行编程而设计的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="af5ec-118">Contains information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO), a collection of objects that are designed for programming all aspects of managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="af5ec-119">数据库引擎扩展存储过程编程</span><span class="sxs-lookup"><span data-stu-id="af5ec-119">Database Engine Extended Stored Procedure Programming</span></span>](database-engine-extended-stored-procedure-programming.md)  
 <span data-ttu-id="af5ec-120">说明如何使用扩展存储过程用编程语言（例如 C）创建自己的外部例程。</span><span class="sxs-lookup"><span data-stu-id="af5ec-120">Describes how to use extended stored procedures to create your own external routines in a programming language such as C.</span></span>  
  
 [<span data-ttu-id="af5ec-121">数据收集器编程</span><span class="sxs-lookup"><span data-stu-id="af5ec-121">Data Collector Programming</span></span>](../database-engine/dev-guide/data-collector-programming.md)  
 <span data-ttu-id="af5ec-122">说明数据收集器对象模型。</span><span class="sxs-lookup"><span data-stu-id="af5ec-122">Describes the Data Collector object model.</span></span>  
  
 [<span data-ttu-id="af5ec-123">异常消息框编程</span><span class="sxs-lookup"><span data-stu-id="af5ec-123">Exception Message Box Programming</span></span>](../database-engine/dev-guide/exception-message-box-programming.md)  
 <span data-ttu-id="af5ec-124">说明如何在应用程序中使用异常消息框编程接口，以提高对消息传送的控制，并使用户可以选择保存错误消息内容以供将来参考和从中获取有关消息的帮助。</span><span class="sxs-lookup"><span data-stu-id="af5ec-124">Describes how you can use the exception message box programmatic interface in your applications to provide more control over the messaging experience, to give your users the option to save error message content for later reference, and to get help with messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5ec-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af5ec-125">See Also</span></span>  
 <span data-ttu-id="af5ec-126">[数据挖掘编程](../analysis-services/dev-guide/data-mining-programming.md) </span><span class="sxs-lookup"><span data-stu-id="af5ec-126">[Data Mining Programming](../analysis-services/dev-guide/data-mining-programming.md) </span></span>  
 <span data-ttu-id="af5ec-127">[开发人员指南 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span><span class="sxs-lookup"><span data-stu-id="af5ec-127">[Developer's Guide &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span></span>  
 <span data-ttu-id="af5ec-128">[开发人员指南 &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="af5ec-128">[Developer's Guide &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="af5ec-129">[开发人员指南 &#40;复制&#41;](replication/concepts/replication-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="af5ec-129">[Developer's Guide &#40;Replication&#41;](replication/concepts/replication-developer-documentation.md) </span></span>  
 [<span data-ttu-id="af5ec-130">开发人员指南 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="af5ec-130">Developer's Guide &#40;Reporting Services&#41;</span></span>](../reporting-services/reporting-services-developer-documentation.md)  
  
  
