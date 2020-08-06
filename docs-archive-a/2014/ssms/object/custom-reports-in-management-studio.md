---
title: Management Studio 中的自定义报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc93157100738610c8576f0af40e75613c3cff62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576507"
---
# <a name="custom-reports-in-management-studio"></a><span data-ttu-id="06d7a-102">Management Studio 中的自定义报表</span><span class="sxs-lookup"><span data-stu-id="06d7a-102">Custom Reports in Management Studio</span></span>
  <span data-ttu-id="06d7a-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，很多对象资源管理器节点都显示一组由 [!INCLUDE[msCoName](../../includes/msconame-md.md)]创建的标准报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], many Object Explorer nodes display a set of standard reports that are created by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span> <span data-ttu-id="06d7a-104">这些报表汇总了通常请求的服务器信息。</span><span class="sxs-lookup"><span data-stu-id="06d7a-104">These reports summarize typically requested server information.</span></span> <span data-ttu-id="06d7a-105">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 开始，管理员可以从 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中运行使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]创建的自定义报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-105">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2, administrators can run custom reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="06d7a-106">实现</span><span class="sxs-lookup"><span data-stu-id="06d7a-106">Implementation</span></span>  
 <span data-ttu-id="06d7a-107">自定义报表是使用报表定义语言 (RDL) 创建的，并存储为报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="06d7a-107">Custom reports are stored as report definition (.rdl) files and are created by using Report Definition Language (RDL).</span></span> <span data-ttu-id="06d7a-108">RDL 包含 XML 格式的报表的数据检索和布局信息。</span><span class="sxs-lookup"><span data-stu-id="06d7a-108">RDL contains data retrieval and layout information for a report in an XML format.</span></span> <span data-ttu-id="06d7a-109">RDL 是一个开放式架构。</span><span class="sxs-lookup"><span data-stu-id="06d7a-109">RDL is an open schema.</span></span> <span data-ttu-id="06d7a-110">开发人员可以使用其他属性和元素来扩展 RDL。</span><span class="sxs-lookup"><span data-stu-id="06d7a-110">Developers can extend RDL with additional attributes and elements.</span></span> <span data-ttu-id="06d7a-111">报表可以执行位于报表内部的任何有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="06d7a-111">Reports can execute any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within the report.</span></span>  
  
 <span data-ttu-id="06d7a-112">如果将对象资源管理器连接至服务器，并且自定义报表引用了当前所选对象资源管理器节点的报表参数，则该自定义报表可在此节点的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="06d7a-112">If Object Explorer is connected to a server, custom reports can execute in the context of the current Object Explorer selection if the reports reference report parameters of that node.</span></span> <span data-ttu-id="06d7a-113">这样，报表可以使用当前上下文（如当前数据库）或统一的上下文（如在自定义报表包含的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中指定一个专门数据库）。</span><span class="sxs-lookup"><span data-stu-id="06d7a-113">This enables a report to use the current context, such as the current database; or a consistent context, such as specifying a designated database as part of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that is contained in the custom report.</span></span>  
  
## <a name="running-a-custom-report"></a><span data-ttu-id="06d7a-114">运行自定义报表</span><span class="sxs-lookup"><span data-stu-id="06d7a-114">Running a Custom Report</span></span>  
 <span data-ttu-id="06d7a-115">可以在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中通过以下方式运行自定义报表：</span><span class="sxs-lookup"><span data-stu-id="06d7a-115">You can run a custom report in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="06d7a-116">在对象资源管理器中，右键单击一个节点，指向“报表”  ，再左键单击“自定义报表”  。</span><span class="sxs-lookup"><span data-stu-id="06d7a-116">Right-click a node in Object Explorer, point to **Reports** and left-click **Custom Reports**.</span></span> <span data-ttu-id="06d7a-117">在“打开文件”  对话框中，找到包含 .rdl 文件的文件夹，然后打开相应的报表文件。</span><span class="sxs-lookup"><span data-stu-id="06d7a-117">In the **Open File** dialog box, locate a folder that contains .rdl files, and then open the appropriate report file.</span></span>  
  
-   <span data-ttu-id="06d7a-118">在对象资源管理器中，右键单击一个节点，指向“报表”  ，再指向“自定义报表”  ，然后从最近打开的文件列表中选择一个自定义报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-118">Right-click a node in Object Explorer, point to **Reports**, point to **Custom Reports**, and then select a custom report from the most recently used file list.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="06d7a-119">限制</span><span class="sxs-lookup"><span data-stu-id="06d7a-119">Limitations</span></span>  
 <span data-ttu-id="06d7a-120">在使用自定义报表时，请注意以下限制：</span><span class="sxs-lookup"><span data-stu-id="06d7a-120">When you work with custom reports, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="06d7a-121">若要防止意外执行恶意代码，即使配置了文件系统以将 .rdl 文件与 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 相关联，也不能将 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]配置为自动运行报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-121">To prevent the unintended execution of malicious code, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] cannot be configured to automatically run a report, even if the file system is configured to associate .rdl files with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="06d7a-122">不能在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中以编程方式执行报表，也不能通过 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]从命令行中运行报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-122">Reports cannot be programmatically executed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot run from the command line through [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="06d7a-123">可以在没有生成预期值的上下文中运行自定义报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-123">You can run custom reports in a context that does not produce the expected values.</span></span> <span data-ttu-id="06d7a-124">例如，可以在复制未涉及的数据库的上下文中运行有关复制的报表，也可以作为无权访问生成准确报表所需信息的用户运行报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-124">For example, you can run a report about replication in the context of a database that is not involved in replication, or run a report as a user who does not have permission to access information that is required to generate an accurate report.</span></span> <span data-ttu-id="06d7a-125">自定义报表的创建者负责验证报表结构及其上下文。</span><span class="sxs-lookup"><span data-stu-id="06d7a-125">The creator of the custom report is responsible for the validity of the report structure and its context.</span></span>  
  
-   <span data-ttu-id="06d7a-126">不能将自定义报表添加到标准报表列表中。</span><span class="sxs-lookup"><span data-stu-id="06d7a-126">You cannot add a custom report to the list of standard reports.</span></span>  
  
-   <span data-ttu-id="06d7a-127">由报表处理的代码可能会影响服务器性能。</span><span class="sxs-lookup"><span data-stu-id="06d7a-127">The code processed by the report might affect server performance.</span></span>  
  
-   <span data-ttu-id="06d7a-128">自定义报表不支持子报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-128">Custom reports will not support subreports.</span></span>  
  
-   <span data-ttu-id="06d7a-129">不得通过表达式定义报表中每个查询的命令文本。</span><span class="sxs-lookup"><span data-stu-id="06d7a-129">The command text for each query within the report must not be defined through an expression.</span></span>  
  
-   <span data-ttu-id="06d7a-130">命令（查询）中使用的任何查询参数都只能引用单个报表参数，而不能使用任何表达式运算符。</span><span class="sxs-lookup"><span data-stu-id="06d7a-130">Any query parameter that is used in a command (query) can only reference a single report parameter and cannot use any expression operators.</span></span>  
  
-   <span data-ttu-id="06d7a-131">报表命令（查询）只支持“文本”和“存储过程”命令类型。</span><span class="sxs-lookup"><span data-stu-id="06d7a-131">Only Text and Stored Procedure command types are supported for report commands (queries).</span></span>  
  
-   <span data-ttu-id="06d7a-132">报表框架不为查询提供任何参数转义。</span><span class="sxs-lookup"><span data-stu-id="06d7a-132">The report framework does not provide any parameter escaping for the queries.</span></span> <span data-ttu-id="06d7a-133">查询的创建者必须确保他们的查询不会受到 SQL 注入攻击。</span><span class="sxs-lookup"><span data-stu-id="06d7a-133">Query authors must make sure that their queries are free from SQL injection attacks.</span></span>  
  
## <a name="managing-custom-reports"></a><span data-ttu-id="06d7a-134">管理自定义报表</span><span class="sxs-lookup"><span data-stu-id="06d7a-134">Managing Custom Reports</span></span>  
 <span data-ttu-id="06d7a-135">如果用户具有很多自定义报表，建议他们使用具有相应 NTFS 文件系统权限的文件系统文件夹来组织这些报表。</span><span class="sxs-lookup"><span data-stu-id="06d7a-135">We recommend that users who have many custom reports organize them by using file system folders that have appropriate NTFS file system permissions.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="06d7a-136">权限</span><span class="sxs-lookup"><span data-stu-id="06d7a-136">Permissions</span></span>  
 <span data-ttu-id="06d7a-137">自定义报表是使用当前用户的权限运行的。</span><span class="sxs-lookup"><span data-stu-id="06d7a-137">Custom reports run by using the permissions of the current user.</span></span> <span data-ttu-id="06d7a-138">若要防止恶意用户更改报表运行的查询，应将包含报表文件的文件系统文件夹的权限设置为“限制访问”。</span><span class="sxs-lookup"><span data-stu-id="06d7a-138">To prevent a malicious user from changing the queries run by the report, permissions on the file system folder that contains the report files should be set to restrict access.</span></span>  
  
 <span data-ttu-id="06d7a-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务所使用的用户和帐户都要求对包含报表文件的文件系统文件夹具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="06d7a-139">Both the user and the account that is used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service require read access to the file system folder that contains the report files.</span></span>  
  
 <span data-ttu-id="06d7a-140">可以在报表中嵌入任何有效的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命令，但不会执行该命令。</span><span class="sxs-lookup"><span data-stu-id="06d7a-140">Any valid [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] command can be embedded in a report, but the command will not be executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="06d7a-141">可以在报表中嵌入任何有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，并可从报表执行此语句。</span><span class="sxs-lookup"><span data-stu-id="06d7a-141">Any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be embedded in and executed from a report.</span></span> <span data-ttu-id="06d7a-142">如果使用具有较高特权的用户帐户运行报表，则可以不受约束地执行所有这些嵌入的指令。</span><span class="sxs-lookup"><span data-stu-id="06d7a-142">Running a report under a high-privileged user account makes it possible for any of these embedded instructions to execute without challenge.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="06d7a-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06d7a-143">See Also</span></span>  
 <span data-ttu-id="06d7a-144">[将自定义报表添加到 Management Studio](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="06d7a-144">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 <span data-ttu-id="06d7a-145">[取消运行自定义报表警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="06d7a-145">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="06d7a-146">将自定义报告与对象资源管理器节点属性一起使用</span><span class="sxs-lookup"><span data-stu-id="06d7a-146">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
