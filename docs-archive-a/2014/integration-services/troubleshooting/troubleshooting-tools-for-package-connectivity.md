---
title: 工具包连接疑难解答 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1baac9af5a30fdc0f5b15e8ac56eb5badacc0edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689511"
---
# <a name="troubleshooting-tools-package-connectivity"></a><span data-ttu-id="61a0a-102">对包连接进行故障排除的工具</span><span class="sxs-lookup"><span data-stu-id="61a0a-102">Troubleshooting Tools Package Connectivity</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="61a0a-103">包括一些功能和工具，您可以利用它们对在包和包从其提取和加载数据的数据源之间的连接进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="61a0a-103">includes features and tools that you can use to troubleshoot connectivity between packages and the data sources from which packages extract and load data.</span></span>  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a><span data-ttu-id="61a0a-104">外部数据访问接口问题的故障排除</span><span class="sxs-lookup"><span data-stu-id="61a0a-104">Troubleshooting Issues with External Data Providers</span></span>  
 <span data-ttu-id="61a0a-105">很多包在与外部数据访问接口交互时会失败。</span><span class="sxs-lookup"><span data-stu-id="61a0a-105">Many packages fail during interactions with external data providers.</span></span> <span data-ttu-id="61a0a-106">但是，这些访问接口返回到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的消息经常无法提供足够的信息来对交互开始进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="61a0a-106">However, the messages that those providers return to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] frequently do not provide enough information to start troubleshooting the interaction.</span></span> <span data-ttu-id="61a0a-107">为了满足此故障排除的需要， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含日志记录消息，这些消息可用来对包与外部数据源的交互进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="61a0a-107">To address this troubleshooting need, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes logging messages that you can use to troubleshoot a package's interaction with external data sources.</span></span>  
  
-   <span data-ttu-id="61a0a-108">**启用日志记录并选择包的“诊断”事件可以看到故障排除消息**。</span><span class="sxs-lookup"><span data-stu-id="61a0a-108">**Enable logging and select the package's Diagnostic event to see the troubleshooting messages**.</span></span> <span data-ttu-id="61a0a-109">下列 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件能够在每次对外部数据访问接口的调用前后向日志写入消息：</span><span class="sxs-lookup"><span data-stu-id="61a0a-109">The following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components are capable of writing a message to the log before and after every call to an external data provider:</span></span>  
  
    -   <span data-ttu-id="61a0a-110">OLE DB 连接管理器、OLE DB 源以及 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="61a0a-110">OLE DB connection manager, OLE DB source, and OLE DB destination</span></span>  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="61a0a-111">连接管理器和 ADO NET 源</span><span class="sxs-lookup"><span data-stu-id="61a0a-111">connection manager and ADO NET source</span></span>  
  
    -   <span data-ttu-id="61a0a-112">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="61a0a-112">Execute SQL task</span></span>  
  
    -   <span data-ttu-id="61a0a-113">查找转换、OLE DB 命令转换和渐变维度转换</span><span class="sxs-lookup"><span data-stu-id="61a0a-113">Lookup transformation, OLE DB Command transformation, and Slowly Changing Dimension transformation</span></span>  
  
     <span data-ttu-id="61a0a-114">日志记录消息包括正被调用的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="61a0a-114">The log messages include the name of the method being called.</span></span> <span data-ttu-id="61a0a-115">例如，这些日志消息可能包括 OLE DB `Open` 对象的 `Connection` 方法或 `ExecuteNonQuery` 对象的 `Command` 方法。</span><span class="sxs-lookup"><span data-stu-id="61a0a-115">For example, these log messages might include the `Open` method of an OLE DB `Connection` object or the `ExecuteNonQuery` method of a `Command` object.</span></span> <span data-ttu-id="61a0a-116">该消息具有以下格式，其中 '%1!s!'</span><span class="sxs-lookup"><span data-stu-id="61a0a-116">The messages have the following format, where '%1!s!'</span></span> <span data-ttu-id="61a0a-117">是方法信息的占位符：</span><span class="sxs-lookup"><span data-stu-id="61a0a-117">is a placeholder for the method information:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     <span data-ttu-id="61a0a-118">若要对与外部数据提供程序的交互进行故障排除，请检查日志，以查看每个“之前”消息 (`ExternalRequest_pre`) 是否都具有相对应的“之后”消息 (`ExternalRequest_post`)。</span><span class="sxs-lookup"><span data-stu-id="61a0a-118">To troubleshoot the interaction with the external data provider, review the log to see whether every "before" message (`ExternalRequest_pre`) has a corresponding "after" message (`ExternalRequest_post`).</span></span> <span data-ttu-id="61a0a-119">如果没有对应的“之后”消息，就会知道外部数据访问接口不会按预期方式回应。</span><span class="sxs-lookup"><span data-stu-id="61a0a-119">If there is no corresponding "after" message, you know that the external data provider did not respond as expected.</span></span>  
  
     <span data-ttu-id="61a0a-120">下面的示例显示了包含这些日志记录消息的日志中的一些示例行：</span><span class="sxs-lookup"><span data-stu-id="61a0a-120">The following example shows some sample rows from a log that contains these logging messages:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61a0a-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61a0a-121">See Also</span></span>  
 <span data-ttu-id="61a0a-122">[包开发的故障排除工具](troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="61a0a-122">[Troubleshooting Tools for Package Development](troubleshooting-tools-for-package-development.md) </span></span>  
 [<span data-ttu-id="61a0a-123">包执行的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="61a0a-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  
