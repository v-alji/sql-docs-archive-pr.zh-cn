---
title: Oracle CDC 实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2228872b5a190fd416dccaa8062dd79dbc1f7a79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586930"
---
# <a name="the-oracle-cdc-instance"></a><span data-ttu-id="a96d0-102">Oracle CDC 实例</span><span class="sxs-lookup"><span data-stu-id="a96d0-102">The Oracle CDC Instance</span></span>
  <span data-ttu-id="a96d0-103">Oracle CDC 实例是 Oracle CDC 服务为处理从单个 Oracle 源数据库捕获的更改而创建的进程。</span><span class="sxs-lookup"><span data-stu-id="a96d0-103">The Oracle CDC Instance is a process created by the Oracle CDC Service to process changes captured from a single Oracle source database.</span></span> <span data-ttu-id="a96d0-104">Oracle CDC 实例从 **cdc.xdbcdc_config** 表检索其配置并且在 **cdc.xdbcdc_state** 表中维护其状态。</span><span class="sxs-lookup"><span data-stu-id="a96d0-104">The Oracle CDC Instance retrieves its configuration from the **cdc.xdbcdc_config** table and maintains its state in the **cdc.xdbcdc_state** table.</span></span> <span data-ttu-id="a96d0-105">这些表是用于定义 Oracle CDC 实例的 CDC 数据库的一部分。</span><span class="sxs-lookup"><span data-stu-id="a96d0-105">These tables are part of the CDC database, which defines the Oracle CDC Instance.</span></span> <span data-ttu-id="a96d0-106">有关 xdbcdc 数据库和表的详细信息，请参阅 [The CDC Databases](the-oracle-cdc-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a96d0-106">For more information about the xdbcdc database and tables see [The CDC Databases](the-oracle-cdc-service.md).</span></span>  
  
 <span data-ttu-id="a96d0-107">下面介绍 Oracle CDC 实例执行的任务：</span><span class="sxs-lookup"><span data-stu-id="a96d0-107">The following describes the tasks carried out by the Oracle CDC instance:</span></span>  
  
-   <span data-ttu-id="a96d0-108">**处理服务启动验证**：在启动时，CDC 实例从 **xdbcdc_config** 表加载其配置并且执行一系列状态验证，这些验证确保 CDC 实例持久化状态是一致的并且可以开始处理更改。</span><span class="sxs-lookup"><span data-stu-id="a96d0-108">**Handling service startup verification**: When started, the CDC instance loads its configuration from the **xdbcdc_config** table and performs a series of status verifications that ensure that the CDC instance persisted state is consistent and that it can start processing changes.</span></span>  
  
-   <span data-ttu-id="a96d0-109">**准备变更捕获**：在成功通过验证后，Oracle CDC 实例将扫描当前定义的所有捕获实例，并且准备 Oracle LogMiner 查询以及变更捕获所需的其他支持结构。</span><span class="sxs-lookup"><span data-stu-id="a96d0-109">**Preparing for change capture**: When the verification passes successfully, the Oracle CDC Instance scans all of the capture instances currently defined and prepares the Oracle LogMiner queries and other support structures required for change capture.</span></span> <span data-ttu-id="a96d0-110">此外，Oracle 实例将重新加载上次 Oracle CDC 实例运行时保存的内部捕获状态。</span><span class="sxs-lookup"><span data-stu-id="a96d0-110">In addition, the Oracle instance re-loads the internal capture state that was saved the last time the Oracle CDC Instance run.</span></span>  
  
-   <span data-ttu-id="a96d0-111">**捕获来自 Oracle 的更改**：Oracle CDC 实例将通过 Oracle LogMiner 实用工具将来自 Oracle 的更改存入池中，根据事务提交对更改进行排序，然后更改事务中的时间并且将更改写入 CDC 数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更改表中。</span><span class="sxs-lookup"><span data-stu-id="a96d0-111">**Capturing changes from Oracle**: The Oracle CDC Instance pools changes from Oracle by means of the Oracle LogMiner facility, orders them in according to transaction commit, and then changes the time in a transaction and writes them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables in the CDC database.</span></span>  
  
-   <span data-ttu-id="a96d0-112">**处理服务关闭**：CDC Oracle 实例的生命周期由 Oracle CDC 服务管理。</span><span class="sxs-lookup"><span data-stu-id="a96d0-112">**Handling service shutdown**: The life cycle of the Oracle CDC Instance is managed by the Oracle CDC Service.</span></span> <span data-ttu-id="a96d0-113">当 Oracle CDC 实例请求关闭时，它执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="a96d0-113">When the Oracle CDC Instance is requested to shut down, it performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="a96d0-114">停止从 Oracle 事务日志进行的读取。</span><span class="sxs-lookup"><span data-stu-id="a96d0-114">Stops reading from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="a96d0-115">停止将已完成的 Oracle 事务写入 CDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="a96d0-115">Stops writing completed Oracle transactions to the CDC database.</span></span>  
  
    -   <span data-ttu-id="a96d0-116">等待最长 30 秒（如果必要），直到当前事务完成向 CDC 的写入。</span><span class="sxs-lookup"><span data-stu-id="a96d0-116">Waits for up to 30 seconds (if necessary) until the current transaction finishes writing to the CDC database.</span></span> <span data-ttu-id="a96d0-117">如果经过了超过 30 秒的时间，则写入将被取消并且事务将回滚（以便在重新启动 CDC 实例时重试）。</span><span class="sxs-lookup"><span data-stu-id="a96d0-117">If more than 30 seconds pass, the writing is cancelled and transaction is rolled back (to be retried when the CDC instance is restarted).</span></span>  
  
    -   <span data-ttu-id="a96d0-118">在单独的线程中，在 30 秒的上限内尽可能多地将内存中缓存的记录写入临时事务表（按照从最旧的事务到最新的事务的顺序），然后更新 **xdbcdc_state** 表并提交所有更改。</span><span class="sxs-lookup"><span data-stu-id="a96d0-118">In a separate thread, writes as many memory-cached records as possible to the staged transactions table for up to 30 seconds (from the oldest transaction to the newest), then updates the **xdbcdc_state** table and commits all the changes.</span></span>  
  
-   <span data-ttu-id="a96d0-119"> 处理配置更改：针对来自 CDC 服务的配置更改或者通过在 **cdc.xdbcdc_config** 表中检测到新版本来通知 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="a96d0-119">**Handling configuration changes**: The Oracle CDC Instance is notified about configuration changes either from the CDC Service or by detecting a new version in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="a96d0-120">大多数更改不需要重新启动 Oracle CDC 实例（例如，添加或删除捕获实例）。</span><span class="sxs-lookup"><span data-stu-id="a96d0-120">Most changes do not require the restart of the Oracle CDC Instance (for example, adding or removing capture instances).</span></span> <span data-ttu-id="a96d0-121">但是，某些更改（例如更改 Oracle 连接字符串和访问凭据）则要求重新启动 CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="a96d0-121">However, some changes, such as changing the Oracle connection string or access credentials do require the restart of the CDC Instance.</span></span>  
  
-   <span data-ttu-id="a96d0-122">**处理恢复**：在某一 Oracle CDC 实例启动时，其内部状态将从 **xdbcdc_state** 和 **xdbcdc_staged_transactions** 表还原。</span><span class="sxs-lookup"><span data-stu-id="a96d0-122">**Handling recovery**: When an Oracle CDC Instance starts its internal state is restored from the **xdbcdc_state** and the **xdbcdc_staged_transactions** tables.</span></span> <span data-ttu-id="a96d0-123">一旦状态还原后，CDC 实例将照常运行。</span><span class="sxs-lookup"><span data-stu-id="a96d0-123">Once the state is restored, the CDC instance proceeds as usual.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96d0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a96d0-124">See Also</span></span>  
 [<span data-ttu-id="a96d0-125">错误处理</span><span class="sxs-lookup"><span data-stu-id="a96d0-125">Error Handling</span></span>](error-handling.md)  
  
  
