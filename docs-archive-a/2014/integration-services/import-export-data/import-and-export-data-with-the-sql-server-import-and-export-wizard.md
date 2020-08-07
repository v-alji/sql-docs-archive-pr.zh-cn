---
title: SQL Server 导入和导出向导 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c175bd005a9f3b9d55467abbbb278e13dafc521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588629"
---
# <a name="sql-server-import-and-export-wizard"></a><span data-ttu-id="444cb-102">SQL Server 导入和导出向导</span><span class="sxs-lookup"><span data-stu-id="444cb-102">SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="444cb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]导入和导出向导提供了最简单的方法，可用于创建 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将数据从源复制到目标的包。</span><span class="sxs-lookup"><span data-stu-id="444cb-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard offers the simplest method to create a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that copies data from a source to a destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="444cb-104">在 64 位计算机上，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会安装 64 位版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导 (DTSWizard.exe)。</span><span class="sxs-lookup"><span data-stu-id="444cb-104">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="444cb-105">但是，有些数据源（如 Access 或 Excel）只提供 32 位提供程序。</span><span class="sxs-lookup"><span data-stu-id="444cb-105">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="444cb-106">若要使用这些数据源，您可能需要安装并运行 32 位版本的向导。</span><span class="sxs-lookup"><span data-stu-id="444cb-106">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="444cb-107">若要安装 32 位版本的向导，必须在安装过程中选择“客户端工具”或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="444cb-107">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="444cb-108">可以从“开始”菜单、从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或使用命令提示符启动 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="444cb-108">You can start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard from the Start menu, from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], or at the command prompt.</span></span> <span data-ttu-id="444cb-109">有关详细信息，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="444cb-109">For more information, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="444cb-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导可以将数据复制到提供托管 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口或本机 OLE DB 访问接口的任何数据源，也可以从这些数据源复制数据。</span><span class="sxs-lookup"><span data-stu-id="444cb-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard can copy data to and from any data source for which a managed [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or a native OLE DB provider is available.</span></span> <span data-ttu-id="444cb-111">可用访问接口的列表包括下列数据源：</span><span class="sxs-lookup"><span data-stu-id="444cb-111">The list of available providers includes the following data sources:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="444cb-112">平面文件</span><span class="sxs-lookup"><span data-stu-id="444cb-112">Flat files</span></span>  
  
-   <span data-ttu-id="444cb-113">Microsoft Office Access</span><span class="sxs-lookup"><span data-stu-id="444cb-113">Microsoft Office Access</span></span>  
  
-   <span data-ttu-id="444cb-114">Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="444cb-114">Microsoft Office Excel</span></span>  
  
 <span data-ttu-id="444cb-115">启动向导的环境不同，某些向导功能的工作方式也会有所不同：</span><span class="sxs-lookup"><span data-stu-id="444cb-115">Some wizard features work differently, depending on the environment in which you start the wizard:</span></span>  
  
-   <span data-ttu-id="444cb-116">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在中启动导入和导出向导 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，则可以通过选中 "**立即执行**" 复选框来立即运行包。</span><span class="sxs-lookup"><span data-stu-id="444cb-116">If you start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you run the package immediately by selecting the **Execute immediately** check box.</span></span> <span data-ttu-id="444cb-117">默认情况下，此复选框处于选中状态，包会立即运行。</span><span class="sxs-lookup"><span data-stu-id="444cb-117">By default, this check box is selected and the package runs immediately.</span></span>  
  
     <span data-ttu-id="444cb-118">还可以决定是将包保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还是保存到文件系统。</span><span class="sxs-lookup"><span data-stu-id="444cb-118">You can also decide whether to save the package to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to the file system.</span></span> <span data-ttu-id="444cb-119">如果选择保存包，还必须指定包保护级别。</span><span class="sxs-lookup"><span data-stu-id="444cb-119">If you select to save the package, you must also specify a package protection level.</span></span> <span data-ttu-id="444cb-120">有关包保护级别的详细信息，请参阅[对包中敏感数据的访问控制](../security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="444cb-120">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="444cb-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导创建包并复制数据之后，可以使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器通过添加任务、转换和事件驱动的逻辑，打开和更改保存的包。</span><span class="sxs-lookup"><span data-stu-id="444cb-121">After the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard has created the package and copied the data, you can use the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to open and change the saved package by adding tasks, transformations, and event-driven logic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="444cb-122">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，未提供用来保存该向导所创建的包的选项。</span><span class="sxs-lookup"><span data-stu-id="444cb-122">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
-   <span data-ttu-id="444cb-123">如果从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目启动 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 导入和导出向导，则无法将包作为完成向导的步骤来运行。</span><span class="sxs-lookup"><span data-stu-id="444cb-123">If you start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the package cannot be run as a step in completing the wizard.</span></span> <span data-ttu-id="444cb-124">相反，该包将添加到启动该向导的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目中。</span><span class="sxs-lookup"><span data-stu-id="444cb-124">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="444cb-125">然后可以运行包，或者使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器添加任务、转换和事件驱动逻辑从而扩展包。</span><span class="sxs-lookup"><span data-stu-id="444cb-125">You can then run the package or extend it by adding tasks, transformations, and event-driven logic by using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="444cb-126">有关详细信息，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="444cb-126">For more information, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a><span data-ttu-id="444cb-127">导入和导出向导所需的权限</span><span class="sxs-lookup"><span data-stu-id="444cb-127">Permissions Required by the Import and Export Wizard</span></span>  
 <span data-ttu-id="444cb-128">若要成功完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导，您必须至少具有下列权限：</span><span class="sxs-lookup"><span data-stu-id="444cb-128">To complete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard successfully, you must have at least the following permissions:</span></span>  
  
-   <span data-ttu-id="444cb-129">连接到源数据库和目标数据库或文件共享的权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-129">Permissions to connect to the source and destination databases or file shares.</span></span> <span data-ttu-id="444cb-130">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，这需要服务器和数据库的登录权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-130">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], this requires server and database login rights.</span></span>  
  
-   <span data-ttu-id="444cb-131">从源数据库或文件中读取数据的权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-131">Permission to read data from the source database or file.</span></span> <span data-ttu-id="444cb-132">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，这需要对源表和视图具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires SELECT permissions on the source tables and views.</span></span>  
  
-   <span data-ttu-id="444cb-133">向目标数据库或文件写入数据的权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-133">Permissions to write data to the destination database or file.</span></span> <span data-ttu-id="444cb-134">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，这需要对目标表具有 INSERT 权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-134">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires INSERT permissions on the destination tables.</span></span>  
  
-   <span data-ttu-id="444cb-135">如果希望创建新的目标数据库、表或文件，则需要具有创建新的数据库、表或文件的足够权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-135">If you want to create a new destination database or table or file, permissions sufficient to create the new database or table or file.</span></span> <span data-ttu-id="444cb-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，这需要具有 CREATE DATABASE 或 CREATE TABLE 权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires CREATE DATABASE or CREATE TABLE permissions.</span></span>  
  
-   <span data-ttu-id="444cb-137">如果希望保存向导创建的包，则需要具有向 msdb 数据库或文件系统进行写入操作的足够权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-137">If you want to save the package created by the wizard, permissions sufficient to write to the msdb database or to the file system.</span></span> <span data-ttu-id="444cb-138">在中 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，这需要对 msdb 数据库具有 INSERT 权限。</span><span class="sxs-lookup"><span data-stu-id="444cb-138">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], this requires INSERT permissions on the msdb database.</span></span>  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a><span data-ttu-id="444cb-139">在导入和导出向导中映射数据类型</span><span class="sxs-lookup"><span data-stu-id="444cb-139">Mapping Data Types in the Import and Export Wizard</span></span>  
 <span data-ttu-id="444cb-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导提供了最低限度的转换功能。</span><span class="sxs-lookup"><span data-stu-id="444cb-140">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides minimal transformation capabilities.</span></span> <span data-ttu-id="444cb-141">除了支持在新的目标表和目标文件中设置列的名称、数据类型和数据类型属性之外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导不支持任何列级转换。</span><span class="sxs-lookup"><span data-stu-id="444cb-141">Except for setting the name, the data type, and the data type properties of columns in new destination tables and files, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard supports no column-level transformations.</span></span>  
  
 <span data-ttu-id="444cb-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的映射文件来将数据类型从一个数据库版本或系统映射到另一个数据库版本或系统。</span><span class="sxs-lookup"><span data-stu-id="444cb-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard uses the mapping files that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides to map data types from one database version or system to another.</span></span> <span data-ttu-id="444cb-143">例如，它可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 映射到 Oracle。</span><span class="sxs-lookup"><span data-stu-id="444cb-143">For example, it can map from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Oracle.</span></span> <span data-ttu-id="444cb-144">默认情况下，XML 格式的映射文件安装在 C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles 中。</span><span class="sxs-lookup"><span data-stu-id="444cb-144">By default, the mapping files in XML format are installed to C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles.</span></span> <span data-ttu-id="444cb-145">如果业务需要在数据类型之间进行不同的映射，则可以更新映射以影响向导所执行的映射。</span><span class="sxs-lookup"><span data-stu-id="444cb-145">If your business requires different mappings between data types, you can update the mappings to affect the mappings that the wizard performs.</span></span> <span data-ttu-id="444cb-146">例如，如果想要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将数据从传输到 db2 时将**nchar**数据类型映射到 db2**图形**数据类型而不是 db2 **VARGRAPHIC**数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则可以将 SqlClientToIBMDB2.xml 映射文件中的**Nchar**映射更改为使用**图形**而不是**VARGRAPHIC。**</span><span class="sxs-lookup"><span data-stu-id="444cb-146">For example, if you want the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** data type to map to the DB2 **GRAPHIC** data type instead of the DB2 **VARGRAPHIC** data type when transferring data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to DB2, you change the **nchar** mapping in the SqlClientToIBMDB2.xml mapping file to use **GRAPHIC** instead of **VARGRAPHIC.**</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="444cb-147">包括很多常用源和目标组合之间的映射，您可以在映射文件目录中添加新的映射文件，以支持其他源和目标。</span><span class="sxs-lookup"><span data-stu-id="444cb-147">includes mappings between many commonly used source and destination combinations, and you can add new mapping files to the Mapping Files directory to support additional sources and destinations.</span></span> <span data-ttu-id="444cb-148">新的映射文件必须遵守所发布的 XSD 架构，并在源和目标的唯一组合之间进行映射。</span><span class="sxs-lookup"><span data-stu-id="444cb-148">The new mapping files must conform to the published XSD schema and map between a unique combination of source and destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="444cb-149">如果编辑现有映射文件，或者向文件夹中添加新的映射文件，则必须关闭并重新打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，以便识别新的或更改过的文件。</span><span class="sxs-lookup"><span data-stu-id="444cb-149">If you edit an existing mapping file, or add a new mapping file to the folder, you must close and reopen the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for the new or changed files to be recognized.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="444cb-150">外部资源</span><span class="sxs-lookup"><span data-stu-id="444cb-150">External Resources</span></span>  
  
-   <span data-ttu-id="444cb-151">Technet.microsoft.com 上的视频，[将 SQL Server 的数据导出到 Excel (SQL Server 视频) ](https://go.microsoft.com/fwlink/?LinkID=200975)</span><span class="sxs-lookup"><span data-stu-id="444cb-151">Video, [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkID=200975), on technet.microsoft.com</span></span>  
  
-   <span data-ttu-id="444cb-152">CodePlex 示例，[使用向导从 ODBC 导出到平面文件教程：课程包](https://go.microsoft.com/fwlink/?LinkId=217657)，在 msftisprodsamples.codeplex.com 上</span><span class="sxs-lookup"><span data-stu-id="444cb-152">CodePlex sample, [Exporting from ODBC to a Flat File Using a Wizard Tutorial: Lesson Packages](https://go.microsoft.com/fwlink/?LinkId=217657), on msftisprodsamples.codeplex.com</span></span>  
  
  
