---
title: 使用全文索引向导 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ef8a23c4d85cbe47bf6bdb47eb3f45723f1559d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688784"
---
# <a name="use-the-full-text-indexing-wizard"></a><span data-ttu-id="616e7-102">使用全文索引向导</span><span class="sxs-lookup"><span data-stu-id="616e7-102">Use the Full-Text Indexing Wizard</span></span>
  <span data-ttu-id="616e7-103">全文索引向导可引导您完成一系列步骤，以帮助您创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-103">The Full-Text Indexing Wizard walks you through a series of steps designed to help you create a full-text index.</span></span>  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a><span data-ttu-id="616e7-104">使用全文索引向导</span><span class="sxs-lookup"><span data-stu-id="616e7-104">To use the Full-Text Indexing wizard</span></span>  
  
1.  <span data-ttu-id="616e7-105">在对象资源管理器中，右键单击要对其创建全文索引的表，指向  “全文索引”，然后单击  “定义全文索引”。</span><span class="sxs-lookup"><span data-stu-id="616e7-105">In Object Explorer, right-click the table on which you want to create a full-text index, point to **Full-Text index**, and then click **Define Full-Text Index**.</span></span>  
  
     <span data-ttu-id="616e7-106">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="616e7-106">**Unique Index**</span></span>  
     <span data-ttu-id="616e7-107">从下拉列表中选择索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-107">Select an index from the drop down list.</span></span> <span data-ttu-id="616e7-108">索引必须是唯一且不为 Null 的单键列索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-108">The index must be a single-key-column, unique, non-nullable index.</span></span> <span data-ttu-id="616e7-109">为全文唯一键选择最小的唯一键索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-109">Select the smallest unique key index for the full-text unique key.</span></span> <span data-ttu-id="616e7-110">为了获得最佳性能，建议使用聚集索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-110">For best performance, a clustered index is recommended.</span></span>  
  
     <span data-ttu-id="616e7-111">**可用列**</span><span class="sxs-lookup"><span data-stu-id="616e7-111">**Available Columns**</span></span>  
     <span data-ttu-id="616e7-112">若要在索引中包括某列，请选中该列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="616e7-112">To include a column in the index, select the check box next to the column name.</span></span> <span data-ttu-id="616e7-113">不能够进行全文索引的列显示为灰色，并禁用其复选框。</span><span class="sxs-lookup"><span data-stu-id="616e7-113">Columns that are not eligible for full-text indexing appear in grey with their check boxes disabled.</span></span>  
  
     <span data-ttu-id="616e7-114">**断字符语言**</span><span class="sxs-lookup"><span data-stu-id="616e7-114">**Language for Word Breaker**</span></span>  
     <span data-ttu-id="616e7-115">从下拉列表中选择语言。</span><span class="sxs-lookup"><span data-stu-id="616e7-115">Select a language from the drop-down list.</span></span> <span data-ttu-id="616e7-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将使用此选项为索引标识正确的断字符。</span><span class="sxs-lookup"><span data-stu-id="616e7-116">This choice will be used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to identify the correct word breakers for the index.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="616e7-117">使用断字符在全文索引的数据中标识词的边界。</span><span class="sxs-lookup"><span data-stu-id="616e7-117">uses word breakers to identify word boundaries in the full-text indexed data.</span></span>  
  
     <span data-ttu-id="616e7-118">**类型列**</span><span class="sxs-lookup"><span data-stu-id="616e7-118">**Type Column**</span></span>  
     <span data-ttu-id="616e7-119">选择存储作为全文索引列的文档类型的列名称。</span><span class="sxs-lookup"><span data-stu-id="616e7-119">Select the name of the column that holds the document type of column being full-text indexed.</span></span>  
  
     <span data-ttu-id="616e7-120">只有当 "**可用列**" 列中命名的列为或类型时，才会启用**type 列** `varbinary(max)` `image` 。</span><span class="sxs-lookup"><span data-stu-id="616e7-120">The  **Type Column** is only enabled when the column named in the **Available Columns** column is of type `varbinary(max)` or `image`.</span></span>  
  
     <span data-ttu-id="616e7-121">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="616e7-121">**Statistical Semantics**</span></span>  
     <span data-ttu-id="616e7-122">选择是否为所选列启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-122">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="616e7-123">有关详细信息，请参阅[语义搜索 (SQL Server)](semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="616e7-123">For more information, see [Semantic Search &#40;SQL Server&#41;](semantic-search-sql-server.md).</span></span>  
  
     <span data-ttu-id="616e7-124">如果您在选择 **“统计语义”** 前选择某一 **“语言”**，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将被禁用。</span><span class="sxs-lookup"><span data-stu-id="616e7-124">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="616e7-125">如果你在选择\*\*\*\*“语言”前选择\*\*\*\*“统计语义”，则下拉组合框中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="616e7-125">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
2.  <span data-ttu-id="616e7-126">选择更改跟踪选项。</span><span class="sxs-lookup"><span data-stu-id="616e7-126">Select the change tracking options.</span></span>  
  
     <span data-ttu-id="616e7-127">**自动**</span><span class="sxs-lookup"><span data-stu-id="616e7-127">**Automatically**</span></span>  
     <span data-ttu-id="616e7-128">选中此单选按钮后，当基础数据发生更改时，全文索引将自动更新。</span><span class="sxs-lookup"><span data-stu-id="616e7-128">Select this radio button to have the full-text index updated automatically as changes occur to the underlying data.</span></span>  
  
     <span data-ttu-id="616e7-129">**手动**</span><span class="sxs-lookup"><span data-stu-id="616e7-129">**Manually**</span></span>  
     <span data-ttu-id="616e7-130">如果不希望基础数据发生更改时自动更新全文索引，请选中此单选按钮。</span><span class="sxs-lookup"><span data-stu-id="616e7-130">Select this radio button if you do not want the full-text index to be updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="616e7-131">对基础数据的更改将保留下来。</span><span class="sxs-lookup"><span data-stu-id="616e7-131">Changes to the underlying data are maintained.</span></span> <span data-ttu-id="616e7-132">不过，若要将更改应用到全文索引，必须手动启动或安排此进程。</span><span class="sxs-lookup"><span data-stu-id="616e7-132">However, to apply the changes to the full-text index you must start or schedule this process manually.</span></span>  
  
     <span data-ttu-id="616e7-133">**不跟踪更改**</span><span class="sxs-lookup"><span data-stu-id="616e7-133">**Do not track changes**</span></span>  
     <span data-ttu-id="616e7-134">如果不希望使用基础数据的更改对全文索引进行更新，请选中此单选按钮。</span><span class="sxs-lookup"><span data-stu-id="616e7-134">Select this radio button if you do not want the full-text index to be updated with changes to the underlying data.</span></span>  
  
     <span data-ttu-id="616e7-135">**创建索引时启动完全填充**</span><span class="sxs-lookup"><span data-stu-id="616e7-135">**Start full population when index is created**</span></span>  
     <span data-ttu-id="616e7-136">选中此单选按钮，可以在此向导成功完成后启动完全填充。</span><span class="sxs-lookup"><span data-stu-id="616e7-136">Select this radio button to kick off a full population at the successful completion of this wizard.</span></span> <span data-ttu-id="616e7-137">这将包括在目录中创建全文索引结构，并用全文索引的数据对其进行填充。</span><span class="sxs-lookup"><span data-stu-id="616e7-137">This will consist of creating the full-text index structure in the catalog and populating it with full-text indexed data.</span></span>  
  
3.  <span data-ttu-id="616e7-138">选择目录、索引文件组和非索引字表。</span><span class="sxs-lookup"><span data-stu-id="616e7-138">Select the catalog, index filegroup and stoplist.</span></span>  
  
     <span data-ttu-id="616e7-139">**选择全文目录**</span><span class="sxs-lookup"><span data-stu-id="616e7-139">**Select full-text catalog**</span></span>  
     <span data-ttu-id="616e7-140">从列表中选择全文目录。</span><span class="sxs-lookup"><span data-stu-id="616e7-140">Select a full-text catalog from the list.</span></span> <span data-ttu-id="616e7-141">默认情况下，数据库的默认目录为该列表中选定的项。</span><span class="sxs-lookup"><span data-stu-id="616e7-141">The default catalog for the database will be the selected item by default in the list.</span></span> <span data-ttu-id="616e7-142">如果没有可用的目录，则该列表将处于禁用状态，并且 **“创建新目录”** 复选框将处于选中状态并被禁用。</span><span class="sxs-lookup"><span data-stu-id="616e7-142">If no catalogs are available, the list will be disabled, and the **Create a new catalog** checkbox will be checked and disabled.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="616e7-143">**“创建新目录”**</span><span class="sxs-lookup"><span data-stu-id="616e7-143">**Create a new catalog**</span></span>|<span data-ttu-id="616e7-144">选中此复选框可以创建新的全文目录。</span><span class="sxs-lookup"><span data-stu-id="616e7-144">Select to create a new full-text catalog.</span></span>|  
  
     <span data-ttu-id="616e7-145">**名称**</span><span class="sxs-lookup"><span data-stu-id="616e7-145">**Name**</span></span>  
     <span data-ttu-id="616e7-146">为新的全文目录输入一个名称。</span><span class="sxs-lookup"><span data-stu-id="616e7-146">Enter a name for the new full-text catalog.</span></span>  
  
     <span data-ttu-id="616e7-147">**设置为默认目录**</span><span class="sxs-lookup"><span data-stu-id="616e7-147">**Set as default catalog**</span></span>  
     <span data-ttu-id="616e7-148">选中此项可以将该目录设为此数据库的默认目录。</span><span class="sxs-lookup"><span data-stu-id="616e7-148">Select to make the catalog the default for this database.</span></span>  
  
     <span data-ttu-id="616e7-149">**区分重音**</span><span class="sxs-lookup"><span data-stu-id="616e7-149">**Accent sensitivity**</span></span>  
     <span data-ttu-id="616e7-150">指定新目录是区分重音还是不区分重音。</span><span class="sxs-lookup"><span data-stu-id="616e7-150">Specify whether the new catalog will be accent-sensitive or accent-insensitive.</span></span> <span data-ttu-id="616e7-151">如果数据库区分重音，默认情况下会选中“区分”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="616e7-151">If the database is accent-sensitive, **Sensitive** will be selected by default.</span></span>  
  
     <span data-ttu-id="616e7-152">**选择索引文件组**</span><span class="sxs-lookup"><span data-stu-id="616e7-152">**Select index filegroup**</span></span>  
     <span data-ttu-id="616e7-153">指定对其创建全文索引的文件组。</span><span class="sxs-lookup"><span data-stu-id="616e7-153">Specify the filegroup on which to create the full-text index.</span></span>  
  
     <span data-ttu-id="616e7-154">选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="616e7-154">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="616e7-155">值</span><span class="sxs-lookup"><span data-stu-id="616e7-155">Value</span></span>|<span data-ttu-id="616e7-156">说明</span><span class="sxs-lookup"><span data-stu-id="616e7-156">Description</span></span>|  
    |-----------|-----------------|  
    |**\<default>**|<span data-ttu-id="616e7-157">如果表或视图尚未分区，则选择此值，将与基础表或视图使用相同的文件组。</span><span class="sxs-lookup"><span data-stu-id="616e7-157">If the table or view is not partitioned, select to use the same filegroup as the underlying table or view.</span></span> <span data-ttu-id="616e7-158">如果表或视图已分区，则使用主文件组。</span><span class="sxs-lookup"><span data-stu-id="616e7-158">If the table or view is partitioned, the primary filegroup is used.</span></span>|  
    |<span data-ttu-id="616e7-159">**PRIMARY**</span><span class="sxs-lookup"><span data-stu-id="616e7-159">**PRIMARY**</span></span>|<span data-ttu-id="616e7-160">选择此值可将主文件组用于新全文索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-160">Select to use the primary filegroup for the new full-text index.</span></span>|  
    |<span data-ttu-id="616e7-161">*用户指定的默认文件组*</span><span class="sxs-lookup"><span data-stu-id="616e7-161">*user-specified default filegroup*</span></span>|<span data-ttu-id="616e7-162">如果存在用户定义的默认非索引字表，请从列表选择其名称，可将该文件组用于新全文索引。</span><span class="sxs-lookup"><span data-stu-id="616e7-162">If a user-defined default stoplist exists, select its name from the list to use that filegroup for the new full-text index.</span></span>|  
  
     <span data-ttu-id="616e7-163">**选择全文非索引字表**</span><span class="sxs-lookup"><span data-stu-id="616e7-163">**Select full-text stoplist**</span></span>  
     <span data-ttu-id="616e7-164">指定要用于全文索引的非索引字表，或者禁用非索引字表。</span><span class="sxs-lookup"><span data-stu-id="616e7-164">Specify a stoplist to use for the full-text index, or disable stoplist use.</span></span>  
  
     <span data-ttu-id="616e7-165">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更高版本中，使用称为“非索引字表”的对象在数据库中管理非索引字。</span><span class="sxs-lookup"><span data-stu-id="616e7-165">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="616e7-166">“非索引字表”\*\* 是一个由非索引字组成的列表，这些非索引字在与全文检索关联时会应用于该索引的全文查询。</span><span class="sxs-lookup"><span data-stu-id="616e7-166">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span> <span data-ttu-id="616e7-167">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="616e7-167">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
     <span data-ttu-id="616e7-168">选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="616e7-168">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="616e7-169">值</span><span class="sxs-lookup"><span data-stu-id="616e7-169">Value</span></span>|<span data-ttu-id="616e7-170">说明</span><span class="sxs-lookup"><span data-stu-id="616e7-170">Description</span></span>|  
    |-----------|-----------------|  
    |**\<system>**|<span data-ttu-id="616e7-171">选择此值将对新全文索引使用系统非索引字表。</span><span class="sxs-lookup"><span data-stu-id="616e7-171">Select to use the system stoplist on the new full-text index.</span></span> <span data-ttu-id="616e7-172">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="616e7-172">This is the default</span></span>|  
    |**\<off>**|<span data-ttu-id="616e7-173">选择此值将禁用新全文索引的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="616e7-173">Select to disable stoplists for the new full-text index.</span></span>|  
    |<span data-ttu-id="616e7-174">*用户定义的非索引字表名称*</span><span class="sxs-lookup"><span data-stu-id="616e7-174">*user-defined-stoplist-name*</span></span>|<span data-ttu-id="616e7-175">该列表显示已对数据库创建的用户定义的每个非索引字表（如果有）的名称。</span><span class="sxs-lookup"><span data-stu-id="616e7-175">The list displays the name of each user-defined stoplist, if any, that has been created on the database.</span></span> <span data-ttu-id="616e7-176">选择任何要用于新全文索引的用户定义的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="616e7-176">Select any user-defined stoplist to use for the new full-text index.</span></span>|  
  
4.  <span data-ttu-id="616e7-177">定义填充计划（可选）。</span><span class="sxs-lookup"><span data-stu-id="616e7-177">Optionally, define the population schedule.</span></span> <span data-ttu-id="616e7-178">索引操作将立即开始，除非已将其安排为在将来执行。</span><span class="sxs-lookup"><span data-stu-id="616e7-178">Indexing operations will begin immediately unless they have been scheduled for future execution.</span></span> <span data-ttu-id="616e7-179">此时将立即创建计划，尽管在计划时间之前并不会运行这些计划。</span><span class="sxs-lookup"><span data-stu-id="616e7-179">Schedules will be created immediately, although they will not run until their scheduled time.</span></span>  
  
     <span data-ttu-id="616e7-180">**新建表计划**</span><span class="sxs-lookup"><span data-stu-id="616e7-180">**New Table Schedule**</span></span>  
     <span data-ttu-id="616e7-181">定义表的填充计划。</span><span class="sxs-lookup"><span data-stu-id="616e7-181">Define a population schedule for a table.</span></span>  
  
     <span data-ttu-id="616e7-182">**新建目录计划**</span><span class="sxs-lookup"><span data-stu-id="616e7-182">**New Catalog Schedule**</span></span>  
     <span data-ttu-id="616e7-183">定义全文目录的填充计划。</span><span class="sxs-lookup"><span data-stu-id="616e7-183">Define a population schedule for a full-text catalog.</span></span>  
  
     <span data-ttu-id="616e7-184">**编辑**</span><span class="sxs-lookup"><span data-stu-id="616e7-184">**Edit**</span></span>  
     <span data-ttu-id="616e7-185">编辑计划。</span><span class="sxs-lookup"><span data-stu-id="616e7-185">Edit a schedule.</span></span>  
  
     <span data-ttu-id="616e7-186">**删除**</span><span class="sxs-lookup"><span data-stu-id="616e7-186">**Delete**</span></span>  
     <span data-ttu-id="616e7-187">删除计划。</span><span class="sxs-lookup"><span data-stu-id="616e7-187">Delete a schedule.</span></span>  
  
5.  <span data-ttu-id="616e7-188">查看或控制全文索引向导的进度。</span><span class="sxs-lookup"><span data-stu-id="616e7-188">View or control the progress of the Full-Text Indexing Wizard.</span></span>  
  
     <span data-ttu-id="616e7-189">**Stop**</span><span class="sxs-lookup"><span data-stu-id="616e7-189">**Stop**</span></span>  
     <span data-ttu-id="616e7-190">中断当前操作，并阻止该向导在此会话期间执行后续全文操作。</span><span class="sxs-lookup"><span data-stu-id="616e7-190">Interrupts the current operation and prevents subsequent full-text operations from being performed by the wizard during this session.</span></span>  
  
     <span data-ttu-id="616e7-191">**Report**</span><span class="sxs-lookup"><span data-stu-id="616e7-191">**Report**</span></span>  
     <span data-ttu-id="616e7-192">当执行完所有操作以后，单击此按钮可以访问所执行操作的报告。</span><span class="sxs-lookup"><span data-stu-id="616e7-192">When all of the operations have finished executing, click this button to access a report on the operations performed.</span></span> <span data-ttu-id="616e7-193">您可以查看该报告，将其打印为文件，复制到剪贴板，或用电子邮件发送该报告。</span><span class="sxs-lookup"><span data-stu-id="616e7-193">You can view the report, print it to a file, copy it to the clipboard, or e-mail the report.</span></span>  
  
  
