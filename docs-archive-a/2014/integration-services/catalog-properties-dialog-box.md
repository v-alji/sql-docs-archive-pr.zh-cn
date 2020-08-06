---
title: "\"目录属性\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f1a4a9d7a74e47d609c319f90b07d8ebfdce00e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589848"
---
# <a name="catalog-properties-dialog-box"></a><span data-ttu-id="d3ec1-102">“目录属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d3ec1-102">Catalog Properties Dialog Box</span></span>
  <span data-ttu-id="d3ec1-103">使用“目录属性”对话框可以配置 SSISDB 目录。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-103">Use the Catalog Properties dialog box to configure the SSISDB catalog.</span></span> <span data-ttu-id="d3ec1-104">目录属性定义如何对敏感数据进行加密、如何保留操作和项目版本控制数据以及验证操作何时超时。SSISDB 目录是用于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目、包、参数和环境的中心存储区和管理点。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-104">Catalog properties define how sensitive data is encrypted, how operations and project versioning data is retained, and when validation operations time out. The SSISDB catalog is a central storage and administration point for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, packages, parameters, and environments.</span></span>  
  
 <span data-ttu-id="d3ec1-105">您还可以在 catalog.catalog_property 视图中查看目录属性，并且通过使用 catalog.configure_catalog 存储过程设置属性。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-105">You can also view catalog properties in the catalog.catalog_property view, and set the properties by using the catalog.configure_catalog stored procedure.</span></span> <span data-ttu-id="d3ec1-106">有关详细信息，请参阅 [catalog.catalog_properties（SSISDB 数据库）](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database)和 [catalog.configure_catalog（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-106">For more information, see [catalog.catalog_properties &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) and [catalog.configure_catalog &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).</span></span>  
  
 <span data-ttu-id="d3ec1-107">有关如何创建 SSISDB 目录的信息，请参阅 [创建 SSIS 目录](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-107">For information on how to create the SSISDB catalog, see [Create the SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
 <span data-ttu-id="d3ec1-108">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-108">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="d3ec1-109">打开“目录属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d3ec1-109">Open the Catalog Properties Dialog Box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="d3ec1-110">配置选项</span><span class="sxs-lookup"><span data-stu-id="d3ec1-110">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-catalog-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="d3ec1-111">打开“目录属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d3ec1-111">Open the Catalog Properties Dialog Box</span></span>  
  
1.  <span data-ttu-id="d3ec1-112">打开 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-112">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3ec1-113">连接到 Microsoft SQL Server 数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-113">Connect Microsoft SQL Server Database Engine.</span></span>  
  
3.  <span data-ttu-id="d3ec1-114">在对象资源管理器中，展开“Integration Services”节点，右键单击“SSISDB”，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-114">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="d3ec1-115">配置选项</span><span class="sxs-lookup"><span data-stu-id="d3ec1-115">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="d3ec1-116">选项</span><span class="sxs-lookup"><span data-stu-id="d3ec1-116">Options</span></span>  
 <span data-ttu-id="d3ec1-117">下表描述该对话框中的某些属性以及 catalog.catalog_property 视图中的相应属性。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-117">The following table describes certain properties in the dialog box and the corresponding properties in the catalog.catalog_property view.</span></span>  
  
|<span data-ttu-id="d3ec1-118">属性名称（“目录属性”对话框）</span><span class="sxs-lookup"><span data-stu-id="d3ec1-118">Property Name (Catalog Properties dialog box)</span></span>|<span data-ttu-id="d3ec1-119">属性名称（catalog.catalog_property 视图）</span><span class="sxs-lookup"><span data-stu-id="d3ec1-119">Property Name (catalog.catalog_property view)</span></span>|<span data-ttu-id="d3ec1-120">说明</span><span class="sxs-lookup"><span data-stu-id="d3ec1-120">Description</span></span>|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|<span data-ttu-id="d3ec1-121">加密算法名称</span><span class="sxs-lookup"><span data-stu-id="d3ec1-121">Encryption Algorithm Name</span></span>|<span data-ttu-id="d3ec1-122">ENCRYPTION_CLEANUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d3ec1-122">ENCRYPTION_CLEANUP_ENABLED</span></span>|<span data-ttu-id="d3ec1-123">指定用于对于目录中的敏感参数值进行加密的加密类型。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-123">Specifies the type of encryption that is used to encrypt the sensitive parameter values in the catalog.</span></span> <span data-ttu-id="d3ec1-124">下面是可能的值：</span><span class="sxs-lookup"><span data-stu-id="d3ec1-124">The following are the possible values:</span></span><br /><br /> <span data-ttu-id="d3ec1-125">**DES**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-125">**DES**</span></span><br /><br /> <span data-ttu-id="d3ec1-126">**TRIPLE_DES**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-126">**TRIPLE_DES**</span></span><br /><br /> <span data-ttu-id="d3ec1-127">**TRIPLE_DES_3KEY**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-127">**TRIPLE_DES_3KEY**</span></span><br /><br /> <span data-ttu-id="d3ec1-128">**DESPX**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-128">**DESPX**</span></span><br /><br /> <span data-ttu-id="d3ec1-129">**AES_128**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-129">**AES_128**</span></span><br /><br /> <span data-ttu-id="d3ec1-130">**AES_192**</span><span class="sxs-lookup"><span data-stu-id="d3ec1-130">**AES_192**</span></span><br /><br /> <span data-ttu-id="d3ec1-131">**AES_256** (默认) </span><span class="sxs-lookup"><span data-stu-id="d3ec1-131">**AES_256** (default)</span></span>|  
|<span data-ttu-id="d3ec1-132">验证超时（秒）</span><span class="sxs-lookup"><span data-stu-id="d3ec1-132">Validation Timeout (seconds)</span></span>|<span data-ttu-id="d3ec1-133">VALIDATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3ec1-133">VALIDATION_TIMEOUT</span></span>|<span data-ttu-id="d3ec1-134">指定项目验证或包验证可运行的最大秒数，超过该秒数后运行将停止。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-134">Specify the maxium number of seconds a project validation or a package validation can run before it is stopped.</span></span> <span data-ttu-id="d3ec1-135">默认值为 300 秒。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-135">The default value is 300 seconds.</span></span><br /><br /> <span data-ttu-id="d3ec1-136">执行验证是一个异步操作。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-136">Performing the validation is an asynchronous operation.</span></span> <span data-ttu-id="d3ec1-137">项目或包越大，验证所用的时间就会越长。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-137">The larger the project or package is, the longer it will take to validate.</span></span><br /><br /> <span data-ttu-id="d3ec1-138">有关验证项目和包的信息，请参阅 [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-138">For information on validating projects and packages, see [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md).</span></span>|  
|<span data-ttu-id="d3ec1-139">定期清理日志</span><span class="sxs-lookup"><span data-stu-id="d3ec1-139">Clean Logs Periodically</span></span>|<span data-ttu-id="d3ec1-140">OPERATION_CLEANUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d3ec1-140">OPERATION_CLEANUP_ENABLED</span></span>|<span data-ttu-id="d3ec1-141">将该属性设置为 True 可指示 SQL Server 代理作业“操作清除”运行。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-141">Set the property to True to indicate that the SQL Server Agent job, operations cleanup, runs.</span></span> <span data-ttu-id="d3ec1-142">否则，将该属性设置为 False。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-142">Otherwise, set the property to False.</span></span>|  
|<span data-ttu-id="d3ec1-143">保持期(天)</span><span class="sxs-lookup"><span data-stu-id="d3ec1-143">Retention Period (days)</span></span>|<span data-ttu-id="d3ec1-144">RETENTION_WINDOW</span><span class="sxs-lookup"><span data-stu-id="d3ec1-144">RETENTION_WINDOW</span></span>|<span data-ttu-id="d3ec1-145">指定可允许操作数据的最长时间（天）。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-145">Specify the maximum age of allowable operations data (in days).</span></span> <span data-ttu-id="d3ec1-146">早于该指定天数的数据将由 SQL 代理作业“操作清除”删除。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-146">Data that is older than the specified number of days will be removed by the SQL Agent job, operations cleanup.</span></span>|  
|<span data-ttu-id="d3ec1-147">每个项目的最大版本数</span><span class="sxs-lookup"><span data-stu-id="d3ec1-147">Maximum Number of Versions per Project</span></span>|<span data-ttu-id="d3ec1-148">MAX_PROJECT_VERSIONS</span><span class="sxs-lookup"><span data-stu-id="d3ec1-148">MAX_PROJECT_VERSIONS</span></span>|<span data-ttu-id="d3ec1-149">指定在目录中将存储项目的多少个版本。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-149">Specify how many versions of a project will be stored in the catalog.</span></span> <span data-ttu-id="d3ec1-150">在项目版本清除作业运行时，超过该最大值的项目的更早的版本将被删除。</span><span class="sxs-lookup"><span data-stu-id="d3ec1-150">Older versions of projects that exceed the maximum will be removed when the project version cleanup job runs.</span></span>|  
  
  
