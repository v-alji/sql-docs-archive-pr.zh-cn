---
title: SQL Server 参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691497"
---
# <a name="sql-server-parameters"></a><span data-ttu-id="5f360-102">SQL Server 参数</span><span class="sxs-lookup"><span data-stu-id="5f360-102">SQL Server Parameters</span></span>
  <span data-ttu-id="5f360-103">在该页上，设置分析器将用于[!INCLUDE[ssDE](../../includes/ssde-md.md)]分析的参数。</span><span class="sxs-lookup"><span data-stu-id="5f360-103">On this page, set parameters that the analyzer will use for [!INCLUDE[ssDE](../../includes/ssde-md.md)] analysis.</span></span> <span data-ttu-id="5f360-104">您可以分析一个、多个或所有数据库，分析通过使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]创建的跟踪文件，以及 SQL 批处理文件。</span><span class="sxs-lookup"><span data-stu-id="5f360-104">You can analyze one, several, or all databases, analyze trace files that were created by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and analyze SQL batch files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f360-105">只有提交要分析的跟踪文件或 SQL 批处理文件时，才能检测到某些升级问题。</span><span class="sxs-lookup"><span data-stu-id="5f360-105">Some upgrade issues can be detected only if you submit trace files or SQL batch files to be analyzed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5f360-106">选项</span><span class="sxs-lookup"><span data-stu-id="5f360-106">Options</span></span>  
 <span data-ttu-id="5f360-107">**要分析的数据库**</span><span class="sxs-lookup"><span data-stu-id="5f360-107">**Database(s) to analyze**</span></span>  
 <span data-ttu-id="5f360-108">若要分析所有数据库，请选中 "**所有数据库**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="5f360-108">To analyze all databases, select the **All databases** check box.</span></span> <span data-ttu-id="5f360-109">若要分析多个数据库，请选中相应的每个数据库旁边的复选框以将其包括在扫描范围内。</span><span class="sxs-lookup"><span data-stu-id="5f360-109">To analyze a selection of databases, select the check box next to each database to include in the scan.</span></span>  
  
 <span data-ttu-id="5f360-110">**分析跟踪文件**</span><span class="sxs-lookup"><span data-stu-id="5f360-110">**Analyze trace file(s)**</span></span>  
 <span data-ttu-id="5f360-111">选中此复选框可分析文件系统中的跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="5f360-111">Select this check box to analyze trace files in the file system.</span></span>  
  
 <span data-ttu-id="5f360-112">**跟踪文件的路径**</span><span class="sxs-lookup"><span data-stu-id="5f360-112">**Path to trace file(s)**</span></span>  
 <span data-ttu-id="5f360-113">可分析一个或多个文件。</span><span class="sxs-lookup"><span data-stu-id="5f360-113">You can analyze one or more files.</span></span> <span data-ttu-id="5f360-114">您可以浏览到某个位置并选择多个文件，也可以提供多个文件名。</span><span class="sxs-lookup"><span data-stu-id="5f360-114">You can browse to a location and select multiple files, or you can provide multiple file names.</span></span> <span data-ttu-id="5f360-115">请使用每个文件的完整路径名，将文件名包括在内，并用竖线字符 (|) 分隔各项。</span><span class="sxs-lookup"><span data-stu-id="5f360-115">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="5f360-116">如果启用 **)  (分析跟踪文件**，则在输入路径名称和文件名之前，将禁用 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="5f360-116">If you enable **Analyze trace file(s)**, **Next** is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="5f360-117">**分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])  (的批处理文件**</span><span class="sxs-lookup"><span data-stu-id="5f360-117">**Analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="5f360-118">选中此复选框可分析文件系统中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理文件。</span><span class="sxs-lookup"><span data-stu-id="5f360-118">Select this check box to analyze [!INCLUDE[tsql](../../includes/tsql-md.md)] batch files in the file system.</span></span>  
  
 <span data-ttu-id="5f360-119">\*\*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]批处理文件的路径 (s) \*\*</span><span class="sxs-lookup"><span data-stu-id="5f360-119">**Path to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="5f360-120">可分析一个或多个批处理文件。</span><span class="sxs-lookup"><span data-stu-id="5f360-120">You can analyze one or more batch files.</span></span> <span data-ttu-id="5f360-121">可先浏览到某个位置然后选择多个文件，或者可提供多个文件名。</span><span class="sxs-lookup"><span data-stu-id="5f360-121">You can browse to a location and select multiple files, or you can type multiple file names.</span></span> <span data-ttu-id="5f360-122">请使用每个文件的完整路径名，将文件名包括在内，并用竖线字符 (|) 分隔各项。</span><span class="sxs-lookup"><span data-stu-id="5f360-122">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="5f360-123">如果启用 **)  (分析 SQL 批处理文件**，则在输入路径名称和文件名之前，将禁用 "**下一步**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="5f360-123">If you enable **Analyze SQL batch file(s)**, the **Next** button is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="5f360-124">**SQL 批处理分隔符**</span><span class="sxs-lookup"><span data-stu-id="5f360-124">**SQL Batch Separator**</span></span>  
 <span data-ttu-id="5f360-125">用于分隔成批的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的文本。</span><span class="sxs-lookup"><span data-stu-id="5f360-125">The text that is used to separate batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="5f360-126">默认值为 "**开始**"。</span><span class="sxs-lookup"><span data-stu-id="5f360-126">The default value is **GO**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f360-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f360-127">See Also</span></span>  
 <span data-ttu-id="5f360-128">[使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="5f360-128">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="5f360-129">升级顾问用户界面参考</span><span class="sxs-lookup"><span data-stu-id="5f360-129">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
