---
title: DAC 对 SQL Server 对象和版本的支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], supported objects
- objects [SQL Server], data-tier applications
ms.assetid: b1b78ded-16c0-4d69-8657-ec57925e68fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa1ea498f603992ce2a62b51d95e74e0f9a9c584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589687"
---
# <a name="dac-support-for-sql-server-objects-and-versions"></a><span data-ttu-id="b0d53-102">对 SQL Server 对象和版本的 DAC 支持</span><span class="sxs-lookup"><span data-stu-id="b0d53-102">DAC Support For SQL Server Objects and Versions</span></span>
  <span data-ttu-id="b0d53-103">数据层应用程序 (DAC) 支持最常用的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="b0d53-103">A data-tier application (DAC) supports the most commonly used [!INCLUDE[ssDE](../../includes/ssde-md.md)] objects.</span></span>  
  
 <span data-ttu-id="b0d53-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b0d53-104">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="b0d53-105">支持的 SQL Server 对象</span><span class="sxs-lookup"><span data-stu-id="b0d53-105">Supported SQL Server Objects</span></span>](#SupportedObjects)  
  
-   [<span data-ttu-id="b0d53-106">各 SQL Server 版本的数据层应用程序支持</span><span class="sxs-lookup"><span data-stu-id="b0d53-106">Data-tier Application Support by the Versions of SQL Server</span></span>](#SupportByVersion)  
  
-   [<span data-ttu-id="b0d53-107">数据部署限制</span><span class="sxs-lookup"><span data-stu-id="b0d53-107">Data Deployment Limitations</span></span>](#DeploymentLimitations)  
  
-   [<span data-ttu-id="b0d53-108">部署操作的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="b0d53-108">Additional Considerations for Deployment Actions</span></span>](#Considerations)  
  
##  <a name="supported-sql-server-objects"></a><a name="SupportedObjects"></a> <span data-ttu-id="b0d53-109">支持的 SQL Server 对象</span><span class="sxs-lookup"><span data-stu-id="b0d53-109">Supported SQL Server Objects</span></span>  
 <span data-ttu-id="b0d53-110">当编写或编辑数据层应用程序时，只能在其中指定支持的对象。</span><span class="sxs-lookup"><span data-stu-id="b0d53-110">Only supported objects can be specified in a data-tier application as it is being authored or edited.</span></span> <span data-ttu-id="b0d53-111">对于包含在 DAC 中不支持的对象的现有数据库，无法从其提取、注册或导入 DAC。</span><span class="sxs-lookup"><span data-stu-id="b0d53-111">You cannot extract, register, or import a DAC from an existing database that contains objects that are not supported in a DAC.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="b0d53-112">支持 DAC 中的以下对象。</span><span class="sxs-lookup"><span data-stu-id="b0d53-112">supports the following objects in a DAC.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0d53-113">DATABASE ROLE</span><span class="sxs-lookup"><span data-stu-id="b0d53-113">DATABASE ROLE</span></span>|<span data-ttu-id="b0d53-114">FUNCTION：内联表值</span><span class="sxs-lookup"><span data-stu-id="b0d53-114">FUNCTION: Inline Table-valued</span></span>|  
|<span data-ttu-id="b0d53-115">FUNCTION：多语句表值</span><span class="sxs-lookup"><span data-stu-id="b0d53-115">FUNCTION: Multistatement Table-valued</span></span>|<span data-ttu-id="b0d53-116">FUNCTION：标量</span><span class="sxs-lookup"><span data-stu-id="b0d53-116">FUNCTION: Scalar</span></span>|  
|<span data-ttu-id="b0d53-117">INDEX：聚集</span><span class="sxs-lookup"><span data-stu-id="b0d53-117">INDEX: Clustered</span></span>|<span data-ttu-id="b0d53-118">索引：非聚集</span><span class="sxs-lookup"><span data-stu-id="b0d53-118">INDEX: Nonclustered</span></span>|  
|<span data-ttu-id="b0d53-119">INDEX：特殊</span><span class="sxs-lookup"><span data-stu-id="b0d53-119">INDEX: Spacial</span></span>|<span data-ttu-id="b0d53-120">INDEX：唯一</span><span class="sxs-lookup"><span data-stu-id="b0d53-120">INDEX: Unique</span></span>|  
|<span data-ttu-id="b0d53-121">LOGIN</span><span class="sxs-lookup"><span data-stu-id="b0d53-121">LOGIN</span></span>|<span data-ttu-id="b0d53-122">权限</span><span class="sxs-lookup"><span data-stu-id="b0d53-122">Permissions</span></span>|  
|<span data-ttu-id="b0d53-123">角色成员资格</span><span class="sxs-lookup"><span data-stu-id="b0d53-123">Role Memberships</span></span>|<span data-ttu-id="b0d53-124">SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b0d53-124">SCHEMA</span></span>|  
|<span data-ttu-id="b0d53-125">统计信息</span><span class="sxs-lookup"><span data-stu-id="b0d53-125">Statistics</span></span>|<span data-ttu-id="b0d53-126">STORED PROCEDURE：Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0d53-126">STORED PROCEDURE: Transact-SQL</span></span>|  
|<span data-ttu-id="b0d53-127">同义词</span><span class="sxs-lookup"><span data-stu-id="b0d53-127">Synonyms</span></span>|<span data-ttu-id="b0d53-128">TABLE：检查约束</span><span class="sxs-lookup"><span data-stu-id="b0d53-128">TABLE: Check Constraint</span></span>|  
|<span data-ttu-id="b0d53-129">TABLE：排序规则</span><span class="sxs-lookup"><span data-stu-id="b0d53-129">TABLE: Collation</span></span>|<span data-ttu-id="b0d53-130">TABLE：列，包括计算列</span><span class="sxs-lookup"><span data-stu-id="b0d53-130">TABLE: Column, including computed columns</span></span>|  
|<span data-ttu-id="b0d53-131">TABLE：约束，默认值</span><span class="sxs-lookup"><span data-stu-id="b0d53-131">TABLE: Constraint, Default</span></span>|<span data-ttu-id="b0d53-132">TABLE：约束，外键</span><span class="sxs-lookup"><span data-stu-id="b0d53-132">TABLE: Constraint, Foreign Key</span></span>|  
|<span data-ttu-id="b0d53-133">TABLE：约束，索引</span><span class="sxs-lookup"><span data-stu-id="b0d53-133">TABLE: Constraint, Index</span></span>|<span data-ttu-id="b0d53-134">TABLE：约束，主键</span><span class="sxs-lookup"><span data-stu-id="b0d53-134">TABLE: Constraint, Primary Key</span></span>|  
|<span data-ttu-id="b0d53-135">TABLE：约束，唯一</span><span class="sxs-lookup"><span data-stu-id="b0d53-135">TABLE: Constraint, Unique</span></span>|<span data-ttu-id="b0d53-136">TRIGGER：DML</span><span class="sxs-lookup"><span data-stu-id="b0d53-136">TRIGGER: DML</span></span>|  
|<span data-ttu-id="b0d53-137">类型：HIERARCHYID、GEOMETRY、GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="b0d53-137">TYPE: HIERARCHYID, GEOMETRY, GEOGRAPHY</span></span>|<span data-ttu-id="b0d53-138">TYPE：用户定义数据类型</span><span class="sxs-lookup"><span data-stu-id="b0d53-138">TYPE: User-defined Data Type</span></span>|  
|<span data-ttu-id="b0d53-139">TYPE：用户定义表类型</span><span class="sxs-lookup"><span data-stu-id="b0d53-139">TYPE: User-defined Table Type</span></span>|<span data-ttu-id="b0d53-140">USER</span><span class="sxs-lookup"><span data-stu-id="b0d53-140">USER</span></span>|  
|<span data-ttu-id="b0d53-141">VIEW</span><span class="sxs-lookup"><span data-stu-id="b0d53-141">VIEW</span></span>||  
  
##  <a name="data-tier-application-support-by-the-versions-of-sql-server"></a><a name="SupportByVersion"></a><span data-ttu-id="b0d53-142">数据层应用程序支持的版本 SQL Server</span><span class="sxs-lookup"><span data-stu-id="b0d53-142">Data-tier Application Support by the Versions of SQL Server</span></span>  
 <span data-ttu-id="b0d53-143">各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本具有针对 DAC 操作的不同级别的支持。</span><span class="sxs-lookup"><span data-stu-id="b0d53-143">The versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have different levels of support for DAC operations.</span></span> <span data-ttu-id="b0d53-144">某一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本支持的所有 DAC 操作均受到该版本的所有次级版本的支持。</span><span class="sxs-lookup"><span data-stu-id="b0d53-144">All of the DAC operations supported by a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported by all editions of that version.</span></span>  
  
 <span data-ttu-id="b0d53-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例支持以下 DAC 操作：</span><span class="sxs-lookup"><span data-stu-id="b0d53-145">Instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] support the following DAC operations:</span></span>  
  
-   <span data-ttu-id="b0d53-146">所有支持的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都支持导出和提取。</span><span class="sxs-lookup"><span data-stu-id="b0d53-146">Export and extract are supported on all supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b0d53-147">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 和所有版本的 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]和 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]都支持所有操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-147">All operations are supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] and all versions of [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span>  
  
-   <span data-ttu-id="b0d53-148">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) 或更高版本以及 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 或更高版本上支持所有操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-148">All operations are supported on [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) or later, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 or later.</span></span>  
  
 <span data-ttu-id="b0d53-149">DAC Framework 包含用于生成和处理 DAC 包和导出文件的客户端工具。</span><span class="sxs-lookup"><span data-stu-id="b0d53-149">The DAC Framework comprises the client-side tools for building and processing DAC packages and export files.</span></span> <span data-ttu-id="b0d53-150">以下产品包括 DAC Framework</span><span class="sxs-lookup"><span data-stu-id="b0d53-150">The following products include the DAC Framework</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="b0d53-151">和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 包括 DAC Framework 3.0，它支持所有 DAC 操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-151">and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] includes DAC Framework 3.0, which supports all DAC operations.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="b0d53-152">SP1 和 Visual Studio 2010 SP1 包括了 DAC Framework 1.1，它支持除了导出和导入之外的所有 DAC 操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-152">SP1 and Visual Studio 2010 SP1 included DAC Framework 1.1, which supports all DAC operations except export and import.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="b0d53-153">和 Visual Studio 2010 包括了 DAC Framework 1.0，它支持除了导出、导入和就地升级之外的所有 DAC 操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-153">and Visual Studio 2010 included DAC Framework 1.0, which supports all DAC operations except export, import, and in-place upgrade.</span></span>  
  
-   <span data-ttu-id="b0d53-154">来自 SQL Server 或 Visual Studio 的早期版本的客户端工具不支持 DAC 操作。</span><span class="sxs-lookup"><span data-stu-id="b0d53-154">The client tools from earlier versions of SQL Server or Visual Studio do not support DAC operations.</span></span>  
  
 <span data-ttu-id="b0d53-155">使用某一 DAC Framework 版本生成的 DAC 包或导出文件无法由早期版本的 DAC Framework 处理。</span><span class="sxs-lookup"><span data-stu-id="b0d53-155">A DAC package or export file built with one version of the DAC Framework cannot be processed by an earlier version of the DAC Framework.</span></span> <span data-ttu-id="b0d53-156">例如，使用 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 客户端工具提取的 DAC 包无法使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 客户端工具进行部署。</span><span class="sxs-lookup"><span data-stu-id="b0d53-156">For example, a DAC package extracted using the [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] client tools cannot be deployed using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools.</span></span>  
  
 <span data-ttu-id="b0d53-157">使用某一 DAC Framework 版本生成的 DAC 包或导出文件可由任何更高版本的 DAC Framework 处理。</span><span class="sxs-lookup"><span data-stu-id="b0d53-157">A DAC package or export file built with one version of the DAC Framework can be processed by any later version of the DAC Framework.</span></span> <span data-ttu-id="b0d53-158">例如，使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 客户端工具提取的 DAC 包可使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 或更高版本客户端工具进行部署。</span><span class="sxs-lookup"><span data-stu-id="b0d53-158">For example, a DAC package extracted using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools can be deployed using either the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 or higher client tools.</span></span>  
  
##  <a name="data-deployment-limitations"></a><a name="DeploymentLimitations"></a><span data-ttu-id="b0d53-159">数据部署限制</span><span class="sxs-lookup"><span data-stu-id="b0d53-159">Data Deployment Limitations</span></span>  
 <span data-ttu-id="b0d53-160">请注意 SQL Server 2012 SP1 中 DAC Framework 数据部署引擎的以下这些保真度限制。</span><span class="sxs-lookup"><span data-stu-id="b0d53-160">Note these fidelity limitations in the DAC Framework data deployment engine in SQL Server 2012 SP1.</span></span> <span data-ttu-id="b0d53-161">这些限制适用于以下 DAC Framework 操作：部署或发布 .dacpac 文件，以及导入 .bacpac 文件。</span><span class="sxs-lookup"><span data-stu-id="b0d53-161">The limitations apply to the following DAC Framework actions: deploy or publish a .dacpac file, and import a .bacpac file.</span></span>  
  
1.  <span data-ttu-id="b0d53-162">sql_variant 列中特定条件和基类型的元数据丢失。</span><span class="sxs-lookup"><span data-stu-id="b0d53-162">Loss of metadata for certain conditions and base types within sql_variant columns.</span></span> <span data-ttu-id="b0d53-163">在受影响的情况下，你将会看到一条包含以下消息的警告：  **由 DAC Framework 部署时不保留 sql_variant 列中使用的特定数据类型的特定属性。**</span><span class="sxs-lookup"><span data-stu-id="b0d53-163">In the affected cases, you will see a warning with the following message:  **Certain properties on certain data types used within a sql_variant column are not preserved when deployed by the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="b0d53-164">MONEY、SMALLMONEY、NUMERIC、DECIMAL 基类型：不保留精度。</span><span class="sxs-lookup"><span data-stu-id="b0d53-164">MONEY, SMALLMONEY, NUMERIC, DECIMAL base types:  Precision is not preserved.</span></span>  
  
        -   <span data-ttu-id="b0d53-165">精度为 38 的 DECIMAL/NUMERIC 基类型：“TotalBytes”sql_variant 元数据始终设置为 21。</span><span class="sxs-lookup"><span data-stu-id="b0d53-165">DECIMAL/NUMERIC base types with precision 38:  the "TotalBytes" sql_variant metadata is always set to 21.</span></span>  
  
    -   <span data-ttu-id="b0d53-166">所有文本基类型：对所有文本应用数据库的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="b0d53-166">All text base types:  The database default collation is applied for all text.</span></span>  
  
    -   <span data-ttu-id="b0d53-167">BINARY 基类型：不保留最大长度属性。</span><span class="sxs-lookup"><span data-stu-id="b0d53-167">BINARY base types:  Max length property is not preserved.</span></span>  
  
    -   <span data-ttu-id="b0d53-168">TIME、DATETIMEOFFSET 基类型：精度始终设置为 7。</span><span class="sxs-lookup"><span data-stu-id="b0d53-168">TIME, DATETIMEOFFSET base types:  Precision is always set to 7.</span></span>  
  
2.  <span data-ttu-id="b0d53-169">sql_variant 列中的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="b0d53-169">Loss of data within sql_variant columns.</span></span> <span data-ttu-id="b0d53-170">在受影响的情况下，您将会看到一条包含以下消息的警告：  **当 DAC Framework 部署小数位数超过 3 的 sql_variant DATETIME2 中的值时，将会发生数据丢失。部署期间，将 DATETIME2 值限定为等于 3 的小数位数。**</span><span class="sxs-lookup"><span data-stu-id="b0d53-170">In the affected case, you will see a warning with the following message:  **There will be data loss when a value in a sql_variant DATETIME2 column with scale greater than 3 is deployed by the DAC Framework. The DATETIME2 value is limited to a scale equal to 3 during deployment.**</span></span>  
  
    -   <span data-ttu-id="b0d53-171">小数位数大于 3 的 DATETIME2 基类型：小数位数限定为等于 3。</span><span class="sxs-lookup"><span data-stu-id="b0d53-171">DATETIME2 base type with scale greater than 3:  scale is limited to equal 3.</span></span>  
  
3.  <span data-ttu-id="b0d53-172">针对 sql_variant 列中以下条件的部署操作失败。</span><span class="sxs-lookup"><span data-stu-id="b0d53-172">Deployment operation fails for the following conditions within sql_variant columns.</span></span> <span data-ttu-id="b0d53-173">在受影响的情况下，您将会看到一条包含以下消息的对话框：  **由于 DAC Framework 中的数据限制，操作失败。**</span><span class="sxs-lookup"><span data-stu-id="b0d53-173">In the affected cases, you will see a dialog with the following message:  **Operation failed due to data limitations in the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="b0d53-174">DATETIME2、SMALLDATETIME 和 DATE 基类型：值超出 DATETIME 范围 - 例如，年份小于 1753。</span><span class="sxs-lookup"><span data-stu-id="b0d53-174">DATETIME2, SMALLDATETIME and DATE base types:  If the value is outside of DATETIME range - for example, the year is less than 1753.</span></span>  
  
    -   <span data-ttu-id="b0d53-175">DECIMAL、NUMERIC 基类型：值的精度大于 28。</span><span class="sxs-lookup"><span data-stu-id="b0d53-175">DECIMAL, NUMERIC base type:  when precision of the value is greater than 28.</span></span>  
  
##  <a name="additional-considerations-for-deployment-actions"></a><a name="Considerations"></a> <span data-ttu-id="b0d53-176">有关部署操作的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="b0d53-176">Additional Considerations for Deployment Actions</span></span>  
 <span data-ttu-id="b0d53-177">请注意以下有关 DAC Framework 数据部署操作的注意事项：</span><span class="sxs-lookup"><span data-stu-id="b0d53-177">Note the following considerations for DAC Framework data deployment actions:</span></span>  
  
-   <span data-ttu-id="b0d53-178">**提取/导出**使用 DAC 框架从数据库创建包的操作-例如，提取 .dacpac 文件，导出 bacpac 文件-这些限制并不适用。</span><span class="sxs-lookup"><span data-stu-id="b0d53-178">**Extract/Export** - On actions that use the DAC Framework to create a package from a database - for example, extract a .dacpac file, export a .bacpac file - these limitations do not apply.</span></span> <span data-ttu-id="b0d53-179">该包中的数据是源数据库中数据的完全保真表示形式。</span><span class="sxs-lookup"><span data-stu-id="b0d53-179">The data in the package is a full-fidelity representation of the data in the source database.</span></span> <span data-ttu-id="b0d53-180">如果该包中存在其中任意条件，则提取/导出日志将包含通过上述消息所提供问题的摘要。</span><span class="sxs-lookup"><span data-stu-id="b0d53-180">If any of these conditions are present in the package, the extract/export log will contain a summary of the issues via the messages noted above.</span></span> <span data-ttu-id="b0d53-181">这将向用户警告他们所创建的包存在潜在数据部署问题。</span><span class="sxs-lookup"><span data-stu-id="b0d53-181">This is to warn the user of potential data deployment issues with the package they created.</span></span> <span data-ttu-id="b0d53-182">用户也将会在日志中看到以下摘要消息：  **这些限制不影响 DAC Framework 创建的 DAC 包中存储的数据类型和值的保真度; 它们只适用于因将 DAC 包部署到数据库而产生的数据类型和值。有关受影响的数据以及如何绕开此限制的详细信息，请参阅** [此主题](https://go.microsoft.com/fwlink/?LinkId=267086)。</span><span class="sxs-lookup"><span data-stu-id="b0d53-182">The user will also see the following summary message in the log:  **These limitations do not affect the fidelity of the data types and values stored in the DAC package created by the DAC Framework; they only apply to the data types and values resulting from deploying a DAC package to a database. For more information about the data that is affected and how to work around this limitation, see** [this topic](https://go.microsoft.com/fwlink/?LinkId=267086).</span></span>  
  
-   <span data-ttu-id="b0d53-183">**部署/发布/导入** - 对于使用 DAC Framework 将包部署到数据库的操作（例如，部署或发布 .dacpac 文件，以及导入 .bacpac 文件），这些限制适用。</span><span class="sxs-lookup"><span data-stu-id="b0d53-183">**Deploy/Publish/Import** - On actions that use the DAC Framework to deploy a package to a database, like to deploy or publish a .dacpac file, and import a .bacpac file, these limitations do apply.</span></span> <span data-ttu-id="b0d53-184">目标数据库中生成的数据不能包含包中数据的完全保真表示形式。</span><span class="sxs-lookup"><span data-stu-id="b0d53-184">The data that results in the target database may not contain a full-fidelity representation of the data in the package.</span></span> <span data-ttu-id="b0d53-185">部署/导入日志将对出现问题的每个实例都显示一条上述消息。</span><span class="sxs-lookup"><span data-stu-id="b0d53-185">The Deploy/Import log will contain a message, noted above, for every instance the issue is encountered.</span></span> <span data-ttu-id="b0d53-186">操作将因错误而被阻止 - 请参阅上述类别 3 - 但将继续显示其他警告。</span><span class="sxs-lookup"><span data-stu-id="b0d53-186">The operation will be blocked by errors - see category 3 above - but will proceed with the other warnings.</span></span>  
  
     <span data-ttu-id="b0d53-187">有关此情况下受影响的数据以及如何在部署/发布/导入操作中绕开此限制的详细信息，请参阅 [此主题](https://go.microsoft.com/fwlink/?LinkId=267087)。</span><span class="sxs-lookup"><span data-stu-id="b0d53-187">For more information about the data that is affected in this scenario and how to work around this limitation for deploy/publish/import actions, see [this topic](https://go.microsoft.com/fwlink/?LinkId=267087).</span></span>  
  
-   <span data-ttu-id="b0d53-188">**解决方法**-提取和导出操作会将完全保真 BCP 数据文件写入 .dacpac 或 bacpac 文件。</span><span class="sxs-lookup"><span data-stu-id="b0d53-188">**Workarounds** - Extract and export operations will write full-fidelity BCP data files into the .dacpac or .bacpac files.</span></span> <span data-ttu-id="b0d53-189">若要避免限制，请使用 SQL Server BCP.exe 命令行实用工具将完全保真数据从 DAC 包部署到目标数据库。</span><span class="sxs-lookup"><span data-stu-id="b0d53-189">To avoid limitations, use the SQL Server BCP.exe command line utility to deploy full-fidelity data to a target database from a DAC package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d53-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0d53-190">See Also</span></span>  
 [<span data-ttu-id="b0d53-191">数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="b0d53-191">Data-tier Applications</span></span>](data-tier-applications.md)  
  
  
