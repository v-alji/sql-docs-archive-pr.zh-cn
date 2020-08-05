---
title: SQL Server Compact Edition 连接管理器编辑器 (所有页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f881d63de5435426475c3aed4b666870d706b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580784"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a><span data-ttu-id="cf900-102">SQL Server Compact Edition 连接管理器编辑器（“全部”页）</span><span class="sxs-lookup"><span data-stu-id="cf900-102">SQL Server Compact Edition Connection Manager Editor (All Page)</span></span>
  <span data-ttu-id="cf900-103">可以使用 **“SQL Server Compact Edition 连接管理器”** 对话框，指定连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库时使用的属性。</span><span class="sxs-lookup"><span data-stu-id="cf900-103">Use the **SQL Server Compact Edition Connection Manager** dialog box to specify properties for connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="cf900-104">若要了解有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition 连接管理器的详细信息，请参阅 [SQL Server Compact Edition 连接管理器](connection-manager/sql-server-compact-edition-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cf900-104">To learn more about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition connection manager, see [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf900-105">选项</span><span class="sxs-lookup"><span data-stu-id="cf900-105">Options</span></span>  
 <span data-ttu-id="cf900-106">**自动收缩阈值**</span><span class="sxs-lookup"><span data-stu-id="cf900-106">**AutoShrink Threshold**</span></span>  
 <span data-ttu-id="cf900-107">指定运行自动收缩进程前， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库中允许使用的可用空间大小（以百分比表示）。</span><span class="sxs-lookup"><span data-stu-id="cf900-107">Specify the amount of free space, as a percentage, that is allowed in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database before the autoshrink process runs.</span></span>  
  
 <span data-ttu-id="cf900-108">**默认锁升级**</span><span class="sxs-lookup"><span data-stu-id="cf900-108">**Default Lock Escalation**</span></span>  
 <span data-ttu-id="cf900-109">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库在尝试升级锁之前获取的数据库锁的数量。</span><span class="sxs-lookup"><span data-stu-id="cf900-109">Specify the number of database locks that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database acquires before it tries to escalate locks.</span></span>  
  
 <span data-ttu-id="cf900-110">**默认锁超时值**</span><span class="sxs-lookup"><span data-stu-id="cf900-110">**Default Lock Timeout**</span></span>  
 <span data-ttu-id="cf900-111">指定事务等待锁的默认时间间隔（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="cf900-111">Specify the default interval, in milliseconds, that a transaction will wait for a lock.</span></span>  
  
 <span data-ttu-id="cf900-112">**刷新间隔**</span><span class="sxs-lookup"><span data-stu-id="cf900-112">**Flush Interval**</span></span>  
 <span data-ttu-id="cf900-113">指定提交的事务将数据刷新到磁盘的时间间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="cf900-113">Specify the interval, in seconds, between committed transactions to flush data to disk.</span></span>  
  
 <span data-ttu-id="cf900-114">**区域设置标识符**</span><span class="sxs-lookup"><span data-stu-id="cf900-114">**Locale Identifier**</span></span>  
 <span data-ttu-id="cf900-115">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库的区域设置 ID (LCID)。</span><span class="sxs-lookup"><span data-stu-id="cf900-115">Specify the Locale ID (LCID) of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="cf900-116">**最大缓冲区大小**</span><span class="sxs-lookup"><span data-stu-id="cf900-116">**Max Buffer Size**</span></span>  
 <span data-ttu-id="cf900-117">指定在将数据刷新到磁盘之前 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 使用的最大内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="cf900-117">Specify the maximum amount of memory, in kilobytes, that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact uses before flushing data to disk.</span></span>  
  
 <span data-ttu-id="cf900-118">**最大数据库大小**</span><span class="sxs-lookup"><span data-stu-id="cf900-118">**Max Database Size**</span></span>  
 <span data-ttu-id="cf900-119">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库的最大大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="cf900-119">Specify the maximum size, in megabytes, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="cf900-120">**模式**</span><span class="sxs-lookup"><span data-stu-id="cf900-120">**Mode**</span></span>  
 <span data-ttu-id="cf900-121">指定打开 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库的文件模式。</span><span class="sxs-lookup"><span data-stu-id="cf900-121">Specify the file mode in which to open the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="cf900-122">此属性的默认值为 **“读写”**。</span><span class="sxs-lookup"><span data-stu-id="cf900-122">The default value for this property is **Read Write**.</span></span>  
  
 <span data-ttu-id="cf900-123">“模式”选项包含四个值，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="cf900-123">The Mode option has four values, as described in the following table.</span></span>  
  
|<span data-ttu-id="cf900-124">值</span><span class="sxs-lookup"><span data-stu-id="cf900-124">Value</span></span>|<span data-ttu-id="cf900-125">说明</span><span class="sxs-lookup"><span data-stu-id="cf900-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf900-126">**只读**</span><span class="sxs-lookup"><span data-stu-id="cf900-126">**Read Only**</span></span>|<span data-ttu-id="cf900-127">指定对数据库的只读访问。</span><span class="sxs-lookup"><span data-stu-id="cf900-127">Specifies read-only access to the database.</span></span>|  
|<span data-ttu-id="cf900-128">**读写**</span><span class="sxs-lookup"><span data-stu-id="cf900-128">**Read Write**</span></span>|<span data-ttu-id="cf900-129">指定对数据库的读/写权限。</span><span class="sxs-lookup"><span data-stu-id="cf900-129">Specifies read/write permission to the database.</span></span>|  
|<span data-ttu-id="cf900-130">**独占**</span><span class="sxs-lookup"><span data-stu-id="cf900-130">**Exclusive**</span></span>|<span data-ttu-id="cf900-131">指定对数据库的排他访问。</span><span class="sxs-lookup"><span data-stu-id="cf900-131">Specifies exclusive access to the database.</span></span>|  
|<span data-ttu-id="cf900-132">**共享读取**</span><span class="sxs-lookup"><span data-stu-id="cf900-132">**Shared Read**</span></span>|<span data-ttu-id="cf900-133">指定其他用户可以同时读取该数据库。</span><span class="sxs-lookup"><span data-stu-id="cf900-133">Specifies that other users can read from the database at the same time.</span></span>|  
  
 <span data-ttu-id="cf900-134">**Persist Security Info**</span><span class="sxs-lookup"><span data-stu-id="cf900-134">**Persist Security Info**</span></span>  
 <span data-ttu-id="cf900-135">指定安全信息是否作为连接字符串的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="cf900-135">Specify whether security information is returned as part of the connection string.</span></span> <span data-ttu-id="cf900-136">此选项的默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="cf900-136">The default value for this option is **False**.</span></span>  
  
 <span data-ttu-id="cf900-137">**临时文件目录**</span><span class="sxs-lookup"><span data-stu-id="cf900-137">**Temp File Directory**</span></span>  
 <span data-ttu-id="cf900-138">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 临时数据库文件的位置。</span><span class="sxs-lookup"><span data-stu-id="cf900-138">Specify the location of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact temporary database file.</span></span>  
  
 <span data-ttu-id="cf900-139">**数据源**</span><span class="sxs-lookup"><span data-stu-id="cf900-139">**Data Source**</span></span>  
 <span data-ttu-id="cf900-140">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="cf900-140">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="cf900-141">**密码**</span><span class="sxs-lookup"><span data-stu-id="cf900-141">**Password**</span></span>  
 <span data-ttu-id="cf900-142">输入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 数据库的密码。</span><span class="sxs-lookup"><span data-stu-id="cf900-142">Enter the password for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf900-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf900-143">See Also</span></span>  
 <span data-ttu-id="cf900-144">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cf900-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="cf900-145">SQL Server Compact Edition 连接管理器编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="cf900-145">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
