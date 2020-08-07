---
title: 配置平面文件目标（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2af8a1653d9a1aef0828aa112a25825ed23b8bf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588639"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="88c3e-102">配置平面文件目标（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="88c3e-102">Configure Flat File Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="88c3e-103">使用 "**配置平面文件目标**" 页可以为目标平面文件指定格式设置选项，并在继续操作前预览结果。</span><span class="sxs-lookup"><span data-stu-id="88c3e-103">Use the **Configure Flat File Destination** page to specify formatting options for the destination flat file, and to preview results before continuing.</span></span>  
  
 <span data-ttu-id="88c3e-104">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="88c3e-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="88c3e-105">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="88c3e-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="88c3e-106">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="88c3e-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="88c3e-107">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="88c3e-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="88c3e-108">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="88c3e-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="88c3e-109">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="88c3e-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="88c3e-110">选项</span><span class="sxs-lookup"><span data-stu-id="88c3e-110">Options</span></span>  
 <span data-ttu-id="88c3e-111">**源平面文件**</span><span class="sxs-lookup"><span data-stu-id="88c3e-111">**Source flat file**</span></span>  
 <span data-ttu-id="88c3e-112">目标文件的名称。</span><span class="sxs-lookup"><span data-stu-id="88c3e-112">The name of the destination file.</span></span>  
  
 <span data-ttu-id="88c3e-113">**行分隔符**</span><span class="sxs-lookup"><span data-stu-id="88c3e-113">**Row delimiter**</span></span>  
 <span data-ttu-id="88c3e-114">从行分隔符的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="88c3e-114">Select from the list of delimiters for rows.</span></span>  
  
|<span data-ttu-id="88c3e-115">值</span><span class="sxs-lookup"><span data-stu-id="88c3e-115">Value</span></span>|<span data-ttu-id="88c3e-116">说明</span><span class="sxs-lookup"><span data-stu-id="88c3e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="88c3e-117">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-117">**{CR}{LF}**</span></span>|<span data-ttu-id="88c3e-118">行由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-118">The row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="88c3e-119">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-119">**{CR}**</span></span>|<span data-ttu-id="88c3e-120">行由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-120">The row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="88c3e-121">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-121">**{LF}**</span></span>|<span data-ttu-id="88c3e-122">行由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-122">The row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="88c3e-123">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-123">**Semicolon {;}**</span></span>|<span data-ttu-id="88c3e-124">行由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-124">The row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="88c3e-125">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-125">**Colon {:}**</span></span>|<span data-ttu-id="88c3e-126">行由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-126">The row is delimited by a colon.</span></span>|  
|<span data-ttu-id="88c3e-127">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-127">**Comma {,}**</span></span>|<span data-ttu-id="88c3e-128">行由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-128">The row is delimited by a comma.</span></span>|  
|<span data-ttu-id="88c3e-129">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-129">**Tab {t}**</span></span>|<span data-ttu-id="88c3e-130">行由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-130">The row is delimited by a tab.</span></span>|  
|<span data-ttu-id="88c3e-131">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="88c3e-131">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="88c3e-132">行由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-132">The row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="88c3e-133">**列分隔符**</span><span class="sxs-lookup"><span data-stu-id="88c3e-133">**Column delimiter**</span></span>  
 <span data-ttu-id="88c3e-134">从列分隔符的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="88c3e-134">Select from the list of delimiters for columns.</span></span>  
  
|<span data-ttu-id="88c3e-135">值</span><span class="sxs-lookup"><span data-stu-id="88c3e-135">Value</span></span>|<span data-ttu-id="88c3e-136">说明</span><span class="sxs-lookup"><span data-stu-id="88c3e-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="88c3e-137">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-137">**{CR}{LF}**</span></span>|<span data-ttu-id="88c3e-138">列由回车符和换行符的组合分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-138">The columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="88c3e-139">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-139">**{CR}**</span></span>|<span data-ttu-id="88c3e-140">列由回车符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-140">The columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="88c3e-141">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-141">**{LF}**</span></span>|<span data-ttu-id="88c3e-142">列由换行符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-142">The columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="88c3e-143">**分号 {;}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-143">**Semicolon {;}**</span></span>|<span data-ttu-id="88c3e-144">列由分号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-144">The columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="88c3e-145">**冒号 {:}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-145">**Colon {:}**</span></span>|<span data-ttu-id="88c3e-146">列由冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-146">The columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="88c3e-147">**逗号 {,}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-147">**Comma {,}**</span></span>|<span data-ttu-id="88c3e-148">列由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-148">The columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="88c3e-149">**制表符 {t}**</span><span class="sxs-lookup"><span data-stu-id="88c3e-149">**Tab {t}**</span></span>|<span data-ttu-id="88c3e-150">列由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-150">The columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="88c3e-151">**竖线 {&#124;}** 。</span><span class="sxs-lookup"><span data-stu-id="88c3e-151">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="88c3e-152">列由竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="88c3e-152">The columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="88c3e-153">**预览**</span><span class="sxs-lookup"><span data-stu-id="88c3e-153">**Preview**</span></span>  
 <span data-ttu-id="88c3e-154">在 "**预览数据**" 对话框中查看目标平面文件的所选格式设置选项的结果。</span><span class="sxs-lookup"><span data-stu-id="88c3e-154">View in the **Preview Data** dialog box the results of the selected formatting options for the destination flat file.</span></span>  
  
 <span data-ttu-id="88c3e-155">**编辑转换**</span><span class="sxs-lookup"><span data-stu-id="88c3e-155">**Edit transform**</span></span>  
 <span data-ttu-id="88c3e-156">使用 "**列映射**" 对话框删除行、追加行并配置目标文件中的列。</span><span class="sxs-lookup"><span data-stu-id="88c3e-156">Delete rows, append rows, and configure columns in the destination file by using the **Column Mappings** dialog box.</span></span>  
  
  
