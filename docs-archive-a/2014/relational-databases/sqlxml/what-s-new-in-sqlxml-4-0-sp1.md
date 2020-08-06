---
title: SQLXML 4.0 SP1 中的新增功能&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- SQLNCLI, SQLXML
- what's new [SQLXML]
- SQLXML, what's new
- migrating SQLXML applications
- redistributing SQLXML
- SQL Server Native Client, SQLXML
- side-by-side installations [SQLXML]
ms.assetid: 48f7720b-1705-402d-93ce-097ff1737877
author: rothja
ms.author: jroth
ms.openlocfilehash: 880937520385fbe6ce64be3fdfcbbf7d11c73741
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687751"
---
# <a name="what39s-new-in-sqlxml-40-sp1"></a><span data-ttu-id="1b146-102">SQLXML 4.0 SP1 中的新增功能&#39;</span><span class="sxs-lookup"><span data-stu-id="1b146-102">What&#39;s New in SQLXML 4.0 SP1</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="1b146-103">SQLXML 4.0 SP1 包括各种更新和增强功能。</span><span class="sxs-lookup"><span data-stu-id="1b146-103">SQLXML 4.0 SP1 includes various updates and enhancements.</span></span> <span data-ttu-id="1b146-104">本主题简要总结这些更新，并提供一些介绍详细信息的链接供您查看。</span><span class="sxs-lookup"><span data-stu-id="1b146-104">This topic summarizes the updates and provides links to more detailed information, where available.</span></span> <span data-ttu-id="1b146-105">SQLXML 4.0 SP1 提供附加的增强功能，以便支持 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中引入的新数据类型。</span><span class="sxs-lookup"><span data-stu-id="1b146-105">SQLXML 4.0 SP1 provides additional enhancements to support the new data types introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="1b146-106">本主题包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="1b146-106">This topic includes the following subjects:</span></span>  
  
-   <span data-ttu-id="1b146-107">安装 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="1b146-107">Installing SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="1b146-108">并行安装问题</span><span class="sxs-lookup"><span data-stu-id="1b146-108">Side-by-Side Installation Issues</span></span>  
  
-   <span data-ttu-id="1b146-109">SQLXML 4.0 和 MSXML</span><span class="sxs-lookup"><span data-stu-id="1b146-109">SQLXML 4.0 and MSXML</span></span>  
  
-   <span data-ttu-id="1b146-110">再分发 SQLXML 4.0</span><span class="sxs-lookup"><span data-stu-id="1b146-110">Redistributing SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="1b146-111">支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="1b146-111">Support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="1b146-112">支持 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中引入的数据类型</span><span class="sxs-lookup"><span data-stu-id="1b146-112">Support for Data Types Introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span>  
  
-   <span data-ttu-id="1b146-113">SQLXML 4.0 的 XML 大容量加载更改</span><span class="sxs-lookup"><span data-stu-id="1b146-113">XML Bulk Load Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="1b146-114">SQLXML 4.0 的注册表项更改</span><span class="sxs-lookup"><span data-stu-id="1b146-114">Registry Key Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="1b146-115">迁移问题</span><span class="sxs-lookup"><span data-stu-id="1b146-115">Migration Issues</span></span>  
  
## <a name="installing-sqlxml-40-sp1"></a><span data-ttu-id="1b146-116">安装 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="1b146-116">Installing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="1b146-117">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前，SQLXML 4.0 随 SQL Server 一起发布，是所有 SQL Server 版本（SQL Server Express 除外）的默认安装的一部分。</span><span class="sxs-lookup"><span data-stu-id="1b146-117">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with SQL Server and was part of the default installation of all SQL Server versions except for SQL Server Express.</span></span> <span data-ttu-id="1b146-118">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 开始，SQL Server 中不再包括 SQLXML 的最新版本 (SQLXML 4.0 SP1)。</span><span class="sxs-lookup"><span data-stu-id="1b146-118">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in SQL Server.</span></span> <span data-ttu-id="1b146-119">若要安装 SQLXML 4.0 SP1，请从[sqlxml 4.0 sp1 的安装位置进行](https://www.microsoft.com/download/details.aspx?id=30403)下载。</span><span class="sxs-lookup"><span data-stu-id="1b146-119">To install SQLXML 4.0 SP1, download it from [Install Location for SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>  
  
 <span data-ttu-id="1b146-120">SQLXML 4.0 SP1 文件安装在以下位置：</span><span class="sxs-lookup"><span data-stu-id="1b146-120">The SQLXML 4.0 SP1 files are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\SQLXML 4.0\`  
  
> [!NOTE]  
>  <span data-ttu-id="1b146-121">SQLXML 4.0 的所有相应注册表设置都在安装过程中进行。</span><span class="sxs-lookup"><span data-stu-id="1b146-121">All appropriate registry settings for SQLXML 4.0 are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="1b146-122">若要允许 32 位 SQLXML 应用程序在 64 位 Windows 操作系统上的 Windows on Windows (WOW64) 下运行，请运行名为 sqlxml4.msi 的 64 位 SQLXML 4.0 SP1 包，该包可从下载中心找到。</span><span class="sxs-lookup"><span data-stu-id="1b146-122">To allow 32-bit SQLXML applications to run under Windows on Windows (WOW64) on 64-bit Windows operating systems, run the 64-bit SQLXML 4.0 SP1 package, named sqlxml4.msi, which can be found on the Download Center.</span></span>  
  
#### <a name="uninstalling-sqlxml-40-sp1"></a><span data-ttu-id="1b146-123">卸载 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="1b146-123">Uninstalling SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="1b146-124">在 SQLXML 3.0 SP3、SQLXML 4.0 和 SQLXML 4.0 SP1 之间存在共享的注册表项。</span><span class="sxs-lookup"><span data-stu-id="1b146-124">Shared registry keys exist between SQLXML 3.0 SP3, SQLXML 4.0 and SQLXML 4.0 SP1.</span></span> <span data-ttu-id="1b146-125">如果在包含 SQLXML 3.0 SP3 的计算机上卸载 SQLXML 的更高版本，则可能需要重新安装 SQLXML 3.0 SP3。</span><span class="sxs-lookup"><span data-stu-id="1b146-125">If the later versions of SQLXML are uninstalled on the same computer which contains SQLXML 3.0 SP3, you might need to reinstall SQLXML 3.0 SP3.</span></span>  
  
## <a name="side-by-side-installation-issues"></a><span data-ttu-id="1b146-126">并行安装问题</span><span class="sxs-lookup"><span data-stu-id="1b146-126">Side-by-Side Installation Issues</span></span>  
 <span data-ttu-id="1b146-127">SQLXML 4.0 的安装过程不会删除由早期版本的 SQLXML 安装的文件。</span><span class="sxs-lookup"><span data-stu-id="1b146-127">The installation process for SQLXML 4.0 does not remove the files that were installed by earlier versions of SQLXML.</span></span> <span data-ttu-id="1b146-128">因此，您的计算机上可能有适合不同 SQLXML 安装版本的多个 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="1b146-128">Therefore, you can have DLLs for several different version-distinctive installations of SQLXML on your computer.</span></span> <span data-ttu-id="1b146-129">您可以运行并行安装。</span><span class="sxs-lookup"><span data-stu-id="1b146-129">You can run the installations side-by-side.</span></span> <span data-ttu-id="1b146-130">SQLXML 4.0 既包括版本无关的 PROGID，也包括与版本相关的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="1b146-130">SQLXML 4.0 includes both version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="1b146-131">所有生产应用程序都应该使用与版本相关的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="1b146-131">All production applications should use version-dependent PROGIDs.</span></span>  
  
## <a name="sqlxml-40-sp1-and-msxml"></a><span data-ttu-id="1b146-132">SQLXML 4.0 SP1 和 MSXML</span><span class="sxs-lookup"><span data-stu-id="1b146-132">SQLXML 4.0 SP1 and MSXML</span></span>  
 <span data-ttu-id="1b146-133">SQLXML 4.0 不安装 MSXML。</span><span class="sxs-lookup"><span data-stu-id="1b146-133">SQLXML 4.0 does not install MSXML.</span></span> <span data-ttu-id="1b146-134">SQLXML 4.0 使用 MSXML 6.0，它作为 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本安装的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="1b146-134">SQLXML 4.0 uses MSXML 6.0, which is installed as part of the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later installation.</span></span>  
  
## <a name="redistributing-sqlxml-40-sp1"></a><span data-ttu-id="1b146-135">再发行 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="1b146-135">Redistributing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="1b146-136">您可以使用可再发行安装程序包发行 SQLXML 4.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="1b146-136">You can distribute SQLXML 4.0 SP1 using the redistributable installer package.</span></span> <span data-ttu-id="1b146-137">安装多个包（对于用户而言就像是一次安装）的一种方法就是使用链接器和引导程序技术。</span><span class="sxs-lookup"><span data-stu-id="1b146-137">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="1b146-138">有关详细信息，请参阅“Authoring a Custom Bootstrapper Package for Visual Studio 2005”（为 Visual Studio 2005 创作自定义引导程序包）和“添加自定义系统必备”。</span><span class="sxs-lookup"><span data-stu-id="1b146-138">For more information, see Authoring a Custom Bootstrapper Package for Visual Studio 2005 and Adding Custom Prerequisites.</span></span>  
  
 <span data-ttu-id="1b146-139">如果您的应用程序所针对的目标平台并非其开发时所使用的平台，则可以从 Microsoft 下载中心下载针对 x64、Itanium 和 x86 的 sqlncli.msi 版本。</span><span class="sxs-lookup"><span data-stu-id="1b146-139">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="1b146-140">同时还有单独再分发的 MSXML 6.0 (msxml6.msi) 安装程序。</span><span class="sxs-lookup"><span data-stu-id="1b146-140">There are also separate redistribution installation programs for MSXML 6.0 (msxml6.msi).</span></span> <span data-ttu-id="1b146-141">这些程序位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装 CD 的以下位置：</span><span class="sxs-lookup"><span data-stu-id="1b146-141">These can be found on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation CD in the following location:</span></span>  
  
 `%CD%\Setup\`  
  
 <span data-ttu-id="1b146-142">这些安装文件可用于直接从 CD 安装 MSXML 6.0。</span><span class="sxs-lookup"><span data-stu-id="1b146-142">These installation files can be used to install MSXML 6.0 directly from the CD.</span></span> <span data-ttu-id="1b146-143">它们可用于随您的自定义应用程序一起自由地再分发 MSXML 6.0 以及 SQLXML 4.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="1b146-143">They can also be used to freely redistribute MSXML 6.0 along with SQLXML 4.0 SP1 with your own custom applications.</span></span>  
  
 <span data-ttu-id="1b146-144">如果您将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 作为数据访问接口与您的应用程序一起使用，则需要再分发它。</span><span class="sxs-lookup"><span data-stu-id="1b146-144">You will also need to redistribute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client if you are using it as the data provider with your application.</span></span> <span data-ttu-id="1b146-145">有关详细信息，请参阅 [安装 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="1b146-145">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="support-for-sql-server-native-client"></a><span data-ttu-id="1b146-146">支持 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="1b146-146">Support for SQL Server Native Client</span></span>  
 <span data-ttu-id="1b146-147">SQLXML 4.0 支持 SQLOLEDB 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1b146-147">SQLXML 4.0 supports both the SQLOLEDB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers.</span></span> <span data-ttu-id="1b146-148">建议你使用相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client 提供程序， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 开发 native client 是为了支持服务器中随附的任何新数据类型，例如 `Date, Time` `DateTime2` 和中的、和 `dateTimeOffset` 数据类型， [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 并支持 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] native client。</span><span class="sxs-lookup"><span data-stu-id="1b146-148">It is recommended that you use the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is developed to support any new data types that ship in the server, such as the `Date, Time`, `DateTime2`, and `dateTimeOffset` data types in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1b146-149">Native Client 是在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中引入的一种数据访问技术。</span><span class="sxs-lookup"><span data-stu-id="1b146-149">Native Client is a data access technology that was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="1b146-150">它将 SQLOLEDB 访问接口和 SQLODBC 驱动程序合并到一个本机动态链接库 (DLL)，同时还提供一项从 Microsoft 数据访问组件 (MDAC) 分离出来并有所不同的新功能。</span><span class="sxs-lookup"><span data-stu-id="1b146-150">It combines the SQLOLEDB Provider and the SQLODBC Driver into one native dynamic link library (DLL), while also providing new functionality that is separate and distinct from the Microsoft Data Access Components (MDAC).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1b146-151">Native Client 可用于创建新的应用程序，也可以用于增强需要利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引入的新功能但 MDAC 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 中的 SQLOLEDB 和 SQLODBC 不支持的现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="1b146-151">Native Client can be used to create new applications or enhance existing applications that need to take advantage of features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not supported by SQLOLEDB and SQLODBC in MDAC and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="1b146-152">例如，对于使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的 FOR XML 之类的客户端 SQLXML 功能，`xml` Native Client 是必需的。</span><span class="sxs-lookup"><span data-stu-id="1b146-152">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is required for client-side SQLXML features, such as FOR XML, to use the `xml` data type.</span></span> <span data-ttu-id="1b146-153">有关详细信息，请参阅[客户端 XML 格式 &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md)，[使用 ADO 执行 sqlxml 4.0 查询](using-ado-to-execute-sqlxml-4-0-queries.md)，并[SQL Server Native Client 编程](../native-client/sql-server-native-client-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="1b146-153">For more information, see [Client-side XML Formatting &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md), [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md), and [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b146-154">SQLXML 4.0 不完全向后兼容 SQLXML 3.0。</span><span class="sxs-lookup"><span data-stu-id="1b146-154">SQLXML 4.0 is not completely backward compatible with SQLXML 3.0.</span></span> <span data-ttu-id="1b146-155">由于一些 bug 修复和其他功能更改，特别是删除了 SQLXML ISAPI 支持，您不能将 SQLXML 4.0 与 IIS 虚拟目录一起使用。</span><span class="sxs-lookup"><span data-stu-id="1b146-155">Because of some bug fixes and other functional changes, particularly the removal of SQLXML ISAPI support, you cannot use IIS virtual directories with SQLXML 4.0.</span></span> <span data-ttu-id="1b146-156">虽然大多数应用程序稍加修改即可运行，但将它们放到生产环境中随 SQLXML 4.0 一起运行之前，必须先进行测试。</span><span class="sxs-lookup"><span data-stu-id="1b146-156">Although most applications will run with minor modifications, you must test them before putting them into production with SQLXML 4.0.</span></span>  
  
## <a name="support-for-data-types-introduced-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="1b146-157">支持 SQL Server 2005 和 SQL Server 2008 中引入的数据类型</span><span class="sxs-lookup"><span data-stu-id="1b146-157">Support for Data Types Introduced in SQL Server 2005 and SQL Server 2008</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="1b146-158">引入了 `xml` 数据类型，SQLXML 4.0 支持 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="1b146-158">introduced the `xml` data type, and SQLXML 4.0 supports the `xml` data type.</span></span> <span data-ttu-id="1b146-159">有关详细信息，请参阅[SQLXML 4.0 中的 Xml 数据类型支持](xml-data-type-support-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="1b146-159">For more information, see [xml Data Type Support in SQLXML 4.0](xml-data-type-support-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="1b146-160">有关映射 XML 视图、大容量加载 XML 或执行 XML updategram 时，如何使用 SQLXML 中 `xml` 数据类型的示例，请参阅以下主题提供的示例。</span><span class="sxs-lookup"><span data-stu-id="1b146-160">For examples of how to use the `xml` data type in SQLXML when mapping XML views, bulk loading XML or executing XML updategrams, refer to examples provided in the following topics.</span></span>  
  
-   [<span data-ttu-id="1b146-161">XSD 元素和属性到表和列的默认映射</span><span class="sxs-lookup"><span data-stu-id="1b146-161">Default Mapping of XSD Elements and Attributes to Tables and Columns</span></span>](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="1b146-162">通过使用 XML Updategram 插入数据</span><span class="sxs-lookup"><span data-stu-id="1b146-162">Inserting Data by Using XML Updategrams</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="1b146-163">大容量加载 XML 文档的示例</span><span class="sxs-lookup"><span data-stu-id="1b146-163">Examples of Bulk Loading XML Documents</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="1b146-164">引入了 `Date, Time` 、 `DateTime2` 和**DateTimeOffset**数据类型。</span><span class="sxs-lookup"><span data-stu-id="1b146-164">introduced the `Date, Time`, `DateTime2`, and **DateTimeOffset** data types.</span></span> <span data-ttu-id="1b146-165">如果将 SQLXML 4.0 SP1 与 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中随附的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider (SQLNCLI11) 一起使用，SQLXML 4.0 SP1 会将这四种新数据类型作为内置标量类型来使用。</span><span class="sxs-lookup"><span data-stu-id="1b146-165">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider (SQLNCLI11), which ships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="xml-bulk-load-changes-for-sqlxml-40-sp1"></a><span data-ttu-id="1b146-166">SQLXML 4.0 SP1 的 XML 大容量加载更改</span><span class="sxs-lookup"><span data-stu-id="1b146-166">XML Bulk Load Changes for SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="1b146-167">对于 SQLXML 4.0，SchemaGen 溢出字段是使用 `xml` 数据类型创建的。</span><span class="sxs-lookup"><span data-stu-id="1b146-167">For SQLXML 4.0, the SchemaGen overflow field is created using the `xml` data type.</span></span> <span data-ttu-id="1b146-168">有关详细信息，请参阅[SQL SERVER XML 大容量加载对象模型](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="1b146-168">For more information, see [SQL Server XML Bulk Load Object Model](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="1b146-169">如果您以前创建了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 应用程序，现在想使用 SQLXML 4.0，则必须引用 Xblkld4.dll 重新编译该应用程序。</span><span class="sxs-lookup"><span data-stu-id="1b146-169">If you have previously created [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic applications and you want to use SQLXML 4.0, you must recompile the application with reference to Xblkld4.dll.</span></span>  
  
-   <span data-ttu-id="1b146-170">对于 Visual Basic Scripting Edition 应用程序，则必须注册想要使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="1b146-170">For Visual Basic Scripting Edition applications, you must register the DLL you want to use.</span></span> <span data-ttu-id="1b146-171">在下例中，如果您指定版本无关的 PROGID，应用程序将取决于最后注册的 DLL：</span><span class="sxs-lookup"><span data-stu-id="1b146-171">In the following example, if you specify version-independent PROGIDs, the application depends on the last registered DLL:</span></span>  
  
    ```  
    set objBulkLoad = CreateObject("SQLXMLBulkLoad.SQLXMLBulkLoad")   
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1b146-172">与版本相关的 PROGID 是 SQLXMLBulkLoad.SQLXMLBulkLoad.4.0。</span><span class="sxs-lookup"><span data-stu-id="1b146-172">The version-dependent PROGID is SQLXMLBulkLoad.SQLXMLBulkLoad.4.0.</span></span>  
  
## <a name="registry-key-changes-for-sqlxml-40"></a><span data-ttu-id="1b146-173">SQLXML 4.0 的注册表项更改</span><span class="sxs-lookup"><span data-stu-id="1b146-173">Registry Key Changes for SQLXML 4.0</span></span>  
 <span data-ttu-id="1b146-174">在 SQLXML 4.0 中，注册表项已从早期版本更改为以下项：</span><span class="sxs-lookup"><span data-stu-id="1b146-174">In SQLXML 4.0, the registry keys have changed from the earlier releases to the following:</span></span>  
  
 <span data-ttu-id="1b146-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span><span class="sxs-lookup"><span data-stu-id="1b146-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span></span>  
  
 <span data-ttu-id="1b146-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span><span class="sxs-lookup"><span data-stu-id="1b146-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span></span>  
  
 <span data-ttu-id="1b146-177">如果想让这些项在 SQLXML 4.0 中生效，则必须更改设置。</span><span class="sxs-lookup"><span data-stu-id="1b146-177">You must change the settings if you want these keys to be in effect for SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="1b146-178">此外，SQLXML 4.0 还引入了以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="1b146-178">In addition, SQLXML 4.0 introduces the following registry keys:</span></span>  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\ReportErrorsWithSQLInfo`  
  
     <span data-ttu-id="1b146-179">默认情况下，SQLXML 4.0 返回 OLE DB 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供的本机错误信息，而不是高级 SQLXML 错误（与早期版本的 SQLXML 一样）。</span><span class="sxs-lookup"><span data-stu-id="1b146-179">By default, SQLXML 4.0 returns native error information provided by OLE DB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of a high-level SQLXML error (as was the case in earlier versions of SQLXML).</span></span> <span data-ttu-id="1b146-180">如果不想出现此行为，DWORD 类型的注册表项值必须设置为 0（默认值为 1）。</span><span class="sxs-lookup"><span data-stu-id="1b146-180">If you do not want this behavior, the value of this registry key of type DWORD must be set to 0 (default is 1).</span></span>  
  
-   <span data-ttu-id="1b146-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span><span class="sxs-lookup"><span data-stu-id="1b146-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span></span>  
  
     <span data-ttu-id="1b146-182">默认情况下，SQLXML 返回 SQL Server GUID 值，并且没有括号。</span><span class="sxs-lookup"><span data-stu-id="1b146-182">By default, SQLXML return SQL Server GUID values without the enclosing braces.</span></span> <span data-ttu-id="1b146-183">如果希望用大括号返回的 GUID 值 (例如，{*某个 GUID*} ) ，则必须将此注册表项的值设置为 1 (默认值为 0) 。</span><span class="sxs-lookup"><span data-stu-id="1b146-183">If you want the GUID value returned with the braces (for example, {*some GUID*}), value of this registry key must be set to 1 (default is 0).</span></span>  
  
-   <span data-ttu-id="1b146-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span><span class="sxs-lookup"><span data-stu-id="1b146-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span></span>  
  
     <span data-ttu-id="1b146-185">默认情况下，XML 分析器加载数据时，会根据 XML 1.0 规则规范化空格。</span><span class="sxs-lookup"><span data-stu-id="1b146-185">By default, when the XML parser loads the data, white spaces are normalized according to the XML 1.0 rules.</span></span> <span data-ttu-id="1b146-186">这会导致数据中的一些空格字符丢失。</span><span class="sxs-lookup"><span data-stu-id="1b146-186">This results in loss of some of the white space characters in your data.</span></span> <span data-ttu-id="1b146-187">因此，数据的文字表示在分析之后可能会不一样，尽管在语义上数据是一样的。</span><span class="sxs-lookup"><span data-stu-id="1b146-187">Thus, the textual representation of your data may not be the same after parsing, although semantically the data is the same.</span></span>  
  
     <span data-ttu-id="1b146-188">引入该项以便您可以选择是否在数据中保留空格字符。</span><span class="sxs-lookup"><span data-stu-id="1b146-188">This key is introduced so that you can choose to keep the white space characters in the data.</span></span> <span data-ttu-id="1b146-189">如果添加此注册表项并将其值设置为 0，则对于 XML 中的属性值，将返回已编码的空格字符（LF、CR 和制表符）。</span><span class="sxs-lookup"><span data-stu-id="1b146-189">If you add this registry key and set its value to 0, white space characters (LF, CR, and tab) in the XML are returned encoded in case of attribute values.</span></span> <span data-ttu-id="1b146-190">对于元素值，只返回已编码的 CR。</span><span class="sxs-lookup"><span data-stu-id="1b146-190">In case of element values, only CR is returned encoded.</span></span>  
  
     <span data-ttu-id="1b146-191">例如：</span><span class="sxs-lookup"><span data-stu-id="1b146-191">For example:</span></span>  
  
    ```  
    CREATE TABLE T( Col1 int, Col2 nvarchar(100));  
    GO  
    -- Insert data with tab, line feed and carriage return).  
    INSERT INTO T VALUES (1, 'This is a tab    . This is a line feed and CR   
     more text');  
    GO  
    -- Test this query (without the registry key).  
    SELECT * FROM T   
    FOR XML AUTO;  
    -- This is the result (no encoding of special characters).  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
    -- Now add registry key with value 0 and execute the query again.  
    -- Note the encoding for carriage return, line-feed and tab in the attribute value.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
  
    -- Update the query and specify ELEMENTS directive  
    SELECT * FROM T  
    FOR XML AUTO, ELEMENTS  
    -- Only the carriage return is returned encoded.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
       <T>  
          <Col1>1</Col1>  
          <Col2>This is a tab    . This is a line feed and CR   
     more text</Col2>  
       </T>  
    </r>  
    ```  
  
## <a name="migration-issues"></a><span data-ttu-id="1b146-192">迁移问题</span><span class="sxs-lookup"><span data-stu-id="1b146-192">Migration Issues</span></span>  
 <span data-ttu-id="1b146-193">下列问题可能影响您将旧版 SQLXML 应用程序迁移到 SQLXML 4.0。</span><span class="sxs-lookup"><span data-stu-id="1b146-193">The following are issues that could impact migration of your legacy SQLXML applications to SQLXML 4.0.</span></span>  
  
### <a name="ado-and-sqlxml-40-queries"></a><span data-ttu-id="1b146-194">ADO 和 SQLXML 4.0 查询</span><span class="sxs-lookup"><span data-stu-id="1b146-194">ADO and SQLXML 4.0 Queries</span></span>  
 <span data-ttu-id="1b146-195">在 SQLXML 的早期版本中，使用 IIS 虚拟目录和 SQLXML ISAPI 筛选器支持基于 URL 的查询执行。</span><span class="sxs-lookup"><span data-stu-id="1b146-195">In earlier versions of SQLXML, support for URL-based query execution using IIS virtual directories and the SQLXML ISAPI filter was provided.</span></span> <span data-ttu-id="1b146-196">对于使用 SQLXML 4.0 的应用程序来说，此支持不再可用。</span><span class="sxs-lookup"><span data-stu-id="1b146-196">For applications that use SQLXML 4.0, this support is no longer available.</span></span>  
  
 <span data-ttu-id="1b146-197">取而代之的是可以通过在 Microsoft 数据访问组件 (MDAC) 2.6 中首次引入并在后期版本中延续使用的 ActiveX 数据对象 (ADO) 的 SQLXML 扩展，执行 SQLXML 查询、模板和 updategram。</span><span class="sxs-lookup"><span data-stu-id="1b146-197">Instead, SQLXML queries, templates, and updategrams can be executed by using the SQLXML extensions to ActiveX Data Objects (ADO) first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="1b146-198">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="1b146-198">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="supportability-for-sqlxml-30-isapi-and-data-types-introduced-in-sql-server-2005"></a><span data-ttu-id="1b146-199">SQL Server 2005 中引入的 SQLXML 3.0 ISAPI 和数据类型的可支持性</span><span class="sxs-lookup"><span data-stu-id="1b146-199">Supportability for SQLXML 3.0 ISAPI and Data Types Introduced in SQL Server 2005</span></span>  
 <span data-ttu-id="1b146-200">由于 ISAPI 支持已从 SQLXML 4.0 中移除，因此，如果您的解决方案需要中引入的增强型数据类型功能 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] （如[xml 数据类型](/sql/t-sql/xml/xml-transact-sql)或[用户定义数据类型 (Udt) ](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)和基于 Web 的访问），则需要使用其他解决方案（如[SQLXML 托管类](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)或其他类型的 HTTP 处理程序，如 SQL Server 2005 的本机 xml Web 服务）。</span><span class="sxs-lookup"><span data-stu-id="1b146-200">Because ISAPI support has been removed from SQLXML 4.0, if your solution requires the enhanced data typing features introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] such as the [xml data type](/sql/t-sql/xml/xml-transact-sql) or [user-defined data types (UDTs)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) and Web-based access, you will need to use another solution such as [SQLXML managed classes](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) or another type of HTTP handler, such as Native XML Web Services for SQL Server 2005.</span></span>  
  
 <span data-ttu-id="1b146-201">或者，如果不需要这些类型扩展，可以继续使用 SQLXML 3.0 连接到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="1b146-201">Alternately, if you do not require these type extensions, you can continue to use SQLXML 3.0 to connect to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] installations.</span></span> <span data-ttu-id="1b146-202">SQLXML 3.0 ISAPI 支持将针对这些更高版本工作，但不支持或识别 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中引入的 `xml` 数据类型或 UDT 类型支持。</span><span class="sxs-lookup"><span data-stu-id="1b146-202">The SQLXML 3.0 ISAPI support will work against these later versions but does not support or recognize the `xml` data type or UDT type support introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
### <a name="xml-bulk-load-security-changes-for-temporary-files"></a><span data-ttu-id="1b146-203">临时文件的 XML 大容量加载安全更改</span><span class="sxs-lookup"><span data-stu-id="1b146-203">XML Bulk Load Security Changes for Temporary Files</span></span>  
 <span data-ttu-id="1b146-204">对于 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，XML 大容量加载文件的权限授予执行大容量加载操作的用户。</span><span class="sxs-lookup"><span data-stu-id="1b146-204">For SQLXML 4.0 and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XML Bulk Load file permissions are granted to the user executing the bulk load operation.</span></span> <span data-ttu-id="1b146-205">读写权限都继承自文件系统。</span><span class="sxs-lookup"><span data-stu-id="1b146-205">Read and Write permissions are inherited from the file system.</span></span> <span data-ttu-id="1b146-206">在早期版本的 SQLXML 和 SQL Server 中，SQLXML 下的 XML 大容量加载将创建一些任何人都可读的不安全的临时文件。</span><span class="sxs-lookup"><span data-stu-id="1b146-206">In previous releases of SQLXML and SQL Server, XML Bulk Load under SQLXML would create temporary files that were not secured and could be readable by anyone.</span></span>  
  
### <a name="migration-issues-for-client-side-for-xml"></a><span data-ttu-id="1b146-207">客户端 FOR XML 迁移问题</span><span class="sxs-lookup"><span data-stu-id="1b146-207">Migration Issues for Client-Side FOR XML</span></span>  
 <span data-ttu-id="1b146-208">由于执行引擎中的更改， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果在下执行 FOR XML 查询，则可能会在基表的元数据中返回不同的值 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1b146-208">Due to changes in the execution engine, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might return different values in the metadata for a base table than would be returned if the FOR XML query was executed under [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="1b146-209">如果发生这种情况，FOR XML 查询结果的客户端格式设置将有不同的输出，具体因运行查询的版本而异。</span><span class="sxs-lookup"><span data-stu-id="1b146-209">In cases where this occurs, client-side formatting of the FOR XML query results will have differing output depending on which version the query is run against.</span></span>  
  
 <span data-ttu-id="1b146-210">如果使用 SQLXML 3.0 的客户端针对 `xml` 数据类型列执行了一个 FOR XML 查询，结果中的数据将以完全实体化的字符串返回。</span><span class="sxs-lookup"><span data-stu-id="1b146-210">If a FOR XML query is executed client-side using SQLXML 3.0 over an `xml` data type column, the data in the results will come back as a fully entitized string.</span></span> <span data-ttu-id="1b146-211">在 SQLXML 4.0 中，如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) 指定为访问接口，数据将以 XML 返回。</span><span class="sxs-lookup"><span data-stu-id="1b146-211">In SQLXML 4.0, if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) is specified as the provider, the data will be returned as XML.</span></span>  
  
  
