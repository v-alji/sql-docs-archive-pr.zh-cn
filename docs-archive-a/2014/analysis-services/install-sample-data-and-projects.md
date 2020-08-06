---
title: 安装 Analysis Services 多维建模教程的示例数据和项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fc475b25-cbb2-408a-901f-9299299538c5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 196f9bad945c69cbc77d2a5dc41a5333e58b33fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587100"
---
# <a name="install-sample-data-and-projects-for-the-analysis-services-multidimensional-modeling-tutorial"></a><span data-ttu-id="b9e74-102">安装 Analysis Services 多维建模教程的示例数据和项目</span><span class="sxs-lookup"><span data-stu-id="b9e74-102">Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial</span></span>
  <span data-ttu-id="b9e74-103">可使用本主题中提供的说明和链接来安装 Analysis Services 教程中使用的所有数据和项目文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-103">Use the instructions and links provided in this topic to install all of the data and project files used in the Analysis Services Tutorials.</span></span>  
  
## <a name="step-1-install-sql-server-software"></a><span data-ttu-id="b9e74-104">步骤 1：安装 SQL Server 软件</span><span class="sxs-lookup"><span data-stu-id="b9e74-104">Step 1: Install SQL Server Software</span></span>  
 <span data-ttu-id="b9e74-105">本教程中的课程假定您已安装以下软件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-105">The lessons in this tutorial assume that you have the following software installed.</span></span> <span data-ttu-id="b9e74-106">所有以下软件都使用 SQL Server 安装介质进行安装。</span><span class="sxs-lookup"><span data-stu-id="b9e74-106">All of the following software is installed using SQL Server installation media.</span></span> <span data-ttu-id="b9e74-107">为了简化部署，您可以在一台计算机上安装所有功能。</span><span class="sxs-lookup"><span data-stu-id="b9e74-107">For simplicity of deployment, you can install all of the features on a single computer.</span></span> <span data-ttu-id="b9e74-108">若要安装这些功能，请运行 SQL Server 安装程序并从“功能选择”页中选择它们。</span><span class="sxs-lookup"><span data-stu-id="b9e74-108">To install these features, run SQL Server Setup and select them from the Feature Selection page.</span></span> <span data-ttu-id="b9e74-109">有关详细信息，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e74-109">For more information, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="b9e74-110">数据库引擎</span><span class="sxs-lookup"><span data-stu-id="b9e74-110">Database Engine</span></span>  
  
-   <span data-ttu-id="b9e74-111">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="b9e74-111">Analysis Services</span></span>  
  
     <span data-ttu-id="b9e74-112">Analysis Services 仅在以下版本中提供：Evaluation、Enterprise、Business Intelligence、Standard。</span><span class="sxs-lookup"><span data-stu-id="b9e74-112">Analysis Services is available in these editions only: Evaluation, Enterprise, Business Intelligence, Standard.</span></span>  
  
     <span data-ttu-id="b9e74-113">请注意，SQL Server Express 版本不包括 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="b9e74-113">Note that SQL Server Express editions do not include Analysis Services.</span></span> <span data-ttu-id="b9e74-114">如果要免费试用此软件，[请下载 Evaluation Edition](https://go.microsoft.com/fwlink/?LinkId=392824) 。</span><span class="sxs-lookup"><span data-stu-id="b9e74-114">[Download the Evaluation edition](https://go.microsoft.com/fwlink/?LinkId=392824) if you want to try out the software free of charge.</span></span>  
  
     <span data-ttu-id="b9e74-115">默认情况下，Analysis Services 将作为多维实例安装，您可以通过在安装向导的“服务器配置”页中选择“表格服务器模式”来覆盖此实例。</span><span class="sxs-lookup"><span data-stu-id="b9e74-115">By default, Analysis Services is installed as a multidimensional instance, which you can override by choosing Tabular Server Mode in the server configuration page of the Installation Wizard.</span></span> <span data-ttu-id="b9e74-116">如果要同时运行两种服务器模式，请在同一台计算机上重新运行 SQL Server 安装程序，以在另一模式中再安装一个 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="b9e74-116">If you want to run both server modes, rerun SQL Server Setup on the same computer to install a second instance of Analysis Services in the other mode.</span></span>  
  
-   <span data-ttu-id="b9e74-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b9e74-117">SQL Server Management Studio</span></span>  
  
 <span data-ttu-id="b9e74-118">或者，请考虑安装 Excel 以便在您继续执行本教程时浏览您的多维数据。</span><span class="sxs-lookup"><span data-stu-id="b9e74-118">Optionally, consider installing Excel to browse your multidimensional data as you proceed through the tutorial.</span></span> <span data-ttu-id="b9e74-119">通过安装 Excel，可以启用“在 Excel 中分析”\*\*\*\* 功能。该功能可以使用连接到你要生成的多维数据集的数据透视表字段列表来启动 Excel。</span><span class="sxs-lookup"><span data-stu-id="b9e74-119">Installing Excel enables the **Analyze in Excel** feature that starts Excel using a PivotTable field list that is connected to the cube you are building.</span></span> <span data-ttu-id="b9e74-120">建议使用 Excel 来浏览数据，因为您可以快速生成透视报表，并通过它与数据进行交互。</span><span class="sxs-lookup"><span data-stu-id="b9e74-120">Using Excel to browse data is recommended because you can quickly build a pivot report that lets you interact with the data.</span></span>  
  
 <span data-ttu-id="b9e74-121">或者，您可以使用在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中内置的内置 MDX 查询设计器来浏览数据。</span><span class="sxs-lookup"><span data-stu-id="b9e74-121">Alternatively, you can browse data using the built-in MDX query designer that is built into [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b9e74-122">查询设计器将返回相同的数据，除非数据以平面行集的形式表示。</span><span class="sxs-lookup"><span data-stu-id="b9e74-122">The query designer returns the same data, except the data is presented as a flat rowset.</span></span>  
  
## <a name="step-2-download-sql-server-data-tools---business-intelligence-for-visual-studio-2012"></a><span data-ttu-id="b9e74-123">步骤2：下载 SQL Server Data Tools-适用于 Visual Studio 2012 的商业智能</span><span class="sxs-lookup"><span data-stu-id="b9e74-123">Step 2: Download SQL Server Data Tools - Business Intelligence for Visual Studio 2012</span></span>  
 <span data-ttu-id="b9e74-124">在此版本中，SQL Server Data Tools 和其他 SQL Server 功能将分开下载与安装。</span><span class="sxs-lookup"><span data-stu-id="b9e74-124">In this release, SQL Server Data Tools is downloaded and installed separately from other SQL Server features.</span></span> <span data-ttu-id="b9e74-125">用于创建 BI 模型和报表的设计器与项目模板现在作为免费 Web 下载提供。</span><span class="sxs-lookup"><span data-stu-id="b9e74-125">The designers and project templates used to create BI models and reports are now available as a free web download.</span></span>  
  
-   <span data-ttu-id="b9e74-126">[下载 SQL Server Data Tools 的 Business Intelligence 版本](https://go.microsoft.com/fwlink/p/?LinkID=322038)。</span><span class="sxs-lookup"><span data-stu-id="b9e74-126">[Download the Business Intelligence version of SQL Server Data Tools](https://go.microsoft.com/fwlink/p/?LinkID=322038).</span></span> <span data-ttu-id="b9e74-127">文件将保存到 Downloads 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b9e74-127">The file is saved to the Downloads folder.</span></span> <span data-ttu-id="b9e74-128">运行安装程序以安装此工具。</span><span class="sxs-lookup"><span data-stu-id="b9e74-128">Run setup to install the tool.</span></span>  
  
     <span data-ttu-id="b9e74-129">重新启动计算机以完成安装。</span><span class="sxs-lookup"><span data-stu-id="b9e74-129">Reboot the computer to complete the installation.</span></span>  
  
## <a name="step-3-install-databases"></a><span data-ttu-id="b9e74-130">步骤 3：安装数据库</span><span class="sxs-lookup"><span data-stu-id="b9e74-130">Step 3: Install Databases</span></span>  
 <span data-ttu-id="b9e74-131">Analysis Services 多维模型使用您从关系数据库管理系统导入的事务数据。</span><span class="sxs-lookup"><span data-stu-id="b9e74-131">An Analysis Services multidimensional model uses transactional data that you import from a relational database management system.</span></span> <span data-ttu-id="b9e74-132">为了实现本教程教学目的，您将使用以下关系数据库作为数据源。</span><span class="sxs-lookup"><span data-stu-id="b9e74-132">For the purposes of this tutorial, you will use the following relational database as your data source.</span></span>  
  
-   <span data-ttu-id="b9e74-133">**AdventureWorksDW2012** -这是在数据库引擎实例上运行的关系数据仓库。</span><span class="sxs-lookup"><span data-stu-id="b9e74-133">**AdventureWorksDW2012** - This is a relational data warehouse that runs on a Database Engine instance.</span></span> <span data-ttu-id="b9e74-134">它提供了将由您在本教程中生成和部署的 Analysis Services 数据库和项目使用的原始数据。</span><span class="sxs-lookup"><span data-stu-id="b9e74-134">It provides the original data that will be used by the Analysis Services databases and projects that you build and deploy throughout the tutorial.</span></span>  
  
     <span data-ttu-id="b9e74-135">您可以将此示例数据库与 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 和 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]一起使用。</span><span class="sxs-lookup"><span data-stu-id="b9e74-135">You can use this sample database with [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as well as [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
 <span data-ttu-id="b9e74-136">若要安装此数据库，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b9e74-136">To install this database, do the following:</span></span>  
  
1.  <span data-ttu-id="b9e74-137">从 codeplex 上的产品示例页下载 [AdventureWorkDW2012](https://go.microsoft.com/fwlink/p/?LinkID=221770) 数据库。</span><span class="sxs-lookup"><span data-stu-id="b9e74-137">Download the [AdventureWorkDW2012](https://go.microsoft.com/fwlink/p/?LinkID=221770) database from the product samples page on codeplex.</span></span>  
  
     <span data-ttu-id="b9e74-138">数据库文件名称是 AdvntureWorksDW2012_Data.mdf。</span><span class="sxs-lookup"><span data-stu-id="b9e74-138">The database file name is AdvntureWorksDW2012_Data.mdf.</span></span> <span data-ttu-id="b9e74-139">该文件应位于您的计算机上的 Downloads 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b9e74-139">The file should be in the Downloads folder on your computer.</span></span>  
  
2.  <span data-ttu-id="b9e74-140">将 AdventureWorksDW2012_Data.mdf 文件复制到本地 SQL Server 数据库引擎实例的数据目录。</span><span class="sxs-lookup"><span data-stu-id="b9e74-140">Copy the AdventureWorksDW2012_Data.mdf file to the data directory of the local SQL Server Database Engine instance.</span></span> <span data-ttu-id="b9e74-141">默认情况下，该文件位于 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data。</span><span class="sxs-lookup"><span data-stu-id="b9e74-141">By default, it is located at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data.</span></span>  
  
3.  <span data-ttu-id="b9e74-142">启动 SQL Server Management Studio 并连接到数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="b9e74-142">Start SQL Server Management Studio and connect to the Database Engine instance.</span></span>  
  
4.  <span data-ttu-id="b9e74-143">右键单击“数据库”，然后单击“附加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9e74-143">Right-click Databases, click **Attach**.</span></span>  
  
5.  <span data-ttu-id="b9e74-144">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="b9e74-144">Click **Add**.</span></span>  
  
6.  <span data-ttu-id="b9e74-145">选择 **AdventureWorksDW2012_Data.mdf** 数据库文件，并单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9e74-145">Select the **AdventureWorksDW2012_Data.mdf** database file and click **OK**.</span></span> <span data-ttu-id="b9e74-146">如果未列出该文件，请检查 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data 文件夹，以便确保该文件在该路径下存在。</span><span class="sxs-lookup"><span data-stu-id="b9e74-146">If the file is not listed, check the C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data folder to be sure the file is there.</span></span>  
  
7.  <span data-ttu-id="b9e74-147">在数据库详细信息中，删除日志文件条目。</span><span class="sxs-lookup"><span data-stu-id="b9e74-147">In database details, remove the Log file entry.</span></span> <span data-ttu-id="b9e74-148">安装程序假设您具有日志文件，但在示例中没有日志文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-148">The setup program assumes you have a log file, but there is no log file in the sample.</span></span> <span data-ttu-id="b9e74-149">附加数据库时将自动创建新日志文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-149">A new log file will be created automatically when you attach the database.</span></span> <span data-ttu-id="b9e74-150">选择日志文件并单击“删除”\*\*\*\*，然后单击“确定”\*\*\*\* 以只附加主数据库文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-150">Select the log file and click **Remove**, and then click **OK** to attach just the primary database file.</span></span>  
  
## <a name="step-4-grant-database-permissions"></a><span data-ttu-id="b9e74-151">步骤 4：授予数据库权限</span><span class="sxs-lookup"><span data-stu-id="b9e74-151">Step 4: Grant Database Permissions</span></span>  
 <span data-ttu-id="b9e74-152">示例项目使用数据源模拟设置，这些设置可指定导入或处理数据所用的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="b9e74-152">The sample projects use data source impersonation settings that specify the security context under which data is imported or processed.</span></span> <span data-ttu-id="b9e74-153">默认情况下，模拟设置指定用于访问数据的 Analysis Services 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b9e74-153">By default, the impersonation settings specify the Analysis Services service account for accessing the data.</span></span> <span data-ttu-id="b9e74-154">若要使用此默认设置，必须确保 Analysis Services 运行时使用的服务帐户具有对 **AdventureWorksDW2012** 数据库的数据读取器权限。</span><span class="sxs-lookup"><span data-stu-id="b9e74-154">To use this default setting, you must ensure that the service account under which Analysis Services runs has data reader permissions on the **AdventureWorksDW2012** database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9e74-155">出于学习的目的，建议您在 SQL Server 中使用默认服务帐户模拟选项并向服务帐户授予数据读取器权限。</span><span class="sxs-lookup"><span data-stu-id="b9e74-155">For learning purposes, it is recommended that you use the default service account impersonation option and grant data reader permissions to the service account in SQL Server.</span></span> <span data-ttu-id="b9e74-156">尽管提供了其他模拟选项，但并非所有这些选项都适用于处理操作。</span><span class="sxs-lookup"><span data-stu-id="b9e74-156">Although other impersonation options are available, not all of them are suitable for processing operations.</span></span> <span data-ttu-id="b9e74-157">具体而言，使用当前用户的凭据的选项不支持处理操作。</span><span class="sxs-lookup"><span data-stu-id="b9e74-157">Specifically, the option for using the credentials of the current user is not supported for processing.</span></span>  
  
1.  <span data-ttu-id="b9e74-158">确定服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b9e74-158">Determine the service account.</span></span> <span data-ttu-id="b9e74-159">您可以使用 SQL Server 配置管理器或“服务”控制台应用程序来查看帐户信息。</span><span class="sxs-lookup"><span data-stu-id="b9e74-159">You can use SQL Server Configuration Manager or the Services console application to view account information.</span></span> <span data-ttu-id="b9e74-160">如果使用默认帐户将 Analysis Services 作为默认实例安装，则该服务将作为 **NT Service\MSSQLServerOLAPService**运行。</span><span class="sxs-lookup"><span data-stu-id="b9e74-160">If you installed Analysis Services as the default instance, using the default account, the service is running as **NT Service\MSSQLServerOLAPService**.</span></span>  
  
2.  <span data-ttu-id="b9e74-161">在 Management Studio 中，连接到数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="b9e74-161">In Management Studio, connect to the database engine instance.</span></span>  
  
3.  <span data-ttu-id="b9e74-162">展开“安全性”文件夹，右键单击“登录名”，然后选择“新建登录名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9e74-162">Expand the Security folder, right-click Logins and select **New Login**.</span></span>  
  
4.  <span data-ttu-id="b9e74-163">在“常规”页的“登录名”中，键入 **NT Service\MSSQLServerOLAPService** （或运行该服务所用的任何帐户）。</span><span class="sxs-lookup"><span data-stu-id="b9e74-163">On the General page, in Login name, type **NT Service\MSSQLServerOLAPService** (or whatever account the service is running as).</span></span>  
  
5.  <span data-ttu-id="b9e74-164">单击“用户映射”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9e74-164">Click **User Mapping**.</span></span>  
  
6.  <span data-ttu-id="b9e74-165">选中 **AdventureWorksDW2012** 数据库旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="b9e74-165">Select the checkbox next to the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="b9e74-166">角色成员身份应自动包括 **db_datareader** 和 **public**。</span><span class="sxs-lookup"><span data-stu-id="b9e74-166">Role membership should automatically include **db_datareader** and **public**.</span></span> <span data-ttu-id="b9e74-167">单击“确定”\*\*\*\* 接受默认值。</span><span class="sxs-lookup"><span data-stu-id="b9e74-167">Click **OK** to accept the defaults.</span></span>  
  
## <a name="step-5-install-projects"></a><span data-ttu-id="b9e74-168">步骤 5：安装项目</span><span class="sxs-lookup"><span data-stu-id="b9e74-168">Step 5: Install Projects</span></span>  
 <span data-ttu-id="b9e74-169">教程包括一些示例项目，以便您能将您的结果与完成的项目进行比较，或者学习后面的课程。</span><span class="sxs-lookup"><span data-stu-id="b9e74-169">The tutorial includes sample projects so that you can compare your results against a finished project, or start a lesson that is further on in the sequence.</span></span>  
  
 <span data-ttu-id="b9e74-170">第 4 课的项目文件特别重要，因为它不仅为第 4 课而且还为所有后续课程提供了基础。</span><span class="sxs-lookup"><span data-stu-id="b9e74-170">The project file for Lesson 4 is particularly important because it provides the basis for not only that lesson, but all the subsequent lessons that follow.</span></span> <span data-ttu-id="b9e74-171">在之前的项目文件中，按照教程中的步骤操作可得到与完成的项目文件完全一样的副本，而第 4 课的示例项目与此有很大的不同，它包含了在第 1 课到第 3 课中生成的模型中没有的、新的模型信息。</span><span class="sxs-lookup"><span data-stu-id="b9e74-171">In contrast with the previous project files, where the steps in the tutorial result in an exact copy of the completed project files, the Lesson 4 sample project includes new model information that is not found in the model you built in lessons 1 through 3.</span></span> <span data-ttu-id="b9e74-172">第 4 课假定您是下面的下载链接提供的示例项目文件的初学者。</span><span class="sxs-lookup"><span data-stu-id="b9e74-172">Lesson 4 assumes that you are starting with a sample project file that is available in the following download.</span></span>  
  
1.  <span data-ttu-id="b9e74-173">在 codeplex 上的产品示例页中下载 [Analysis Services 教程 SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) 。</span><span class="sxs-lookup"><span data-stu-id="b9e74-173">Download the [Analysis Services Tutorial SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
     <span data-ttu-id="b9e74-174">2012 教程对于 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本有效。</span><span class="sxs-lookup"><span data-stu-id="b9e74-174">The 2012 tutorials are valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
     <span data-ttu-id="b9e74-175">"Analysis Services 教程 SQL Server 2012.zip" 文件将保存到计算机上的 "下载" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b9e74-175">The "Analysis Services Tutorial SQL Server 2012.zip" file will be saved to the Downloads folder on your computer.</span></span>  
  
2.  <span data-ttu-id="b9e74-176">将 .zip 文件移到根驱动器下一级的文件夹（例如 C:\Tutorial）。</span><span class="sxs-lookup"><span data-stu-id="b9e74-176">Move the .zip file to a folder just below the root drive (for example, C:\Tutorial).</span></span> <span data-ttu-id="b9e74-177">如果你尝试在 "下载" 文件夹中解压缩这些文件，则此步骤将会缓解有时会发生的 "路径过长" 错误。</span><span class="sxs-lookup"><span data-stu-id="b9e74-177">This step mitigates the "Path too long" error that sometimes occurs if you attempt to unzip the files in the Downloads folder.</span></span>  
  
3.  <span data-ttu-id="b9e74-178">解压缩示例项目：右键单击该文件，然后选择“全部提取”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9e74-178">Unzip the sample projects: right-click on the file and select **Extract All**.</span></span> <span data-ttu-id="b9e74-179">提取这些文件后，您应该已在计算机上安装以下项目：</span><span class="sxs-lookup"><span data-stu-id="b9e74-179">After you extract the files, you should have the following projects installed on your computer:</span></span>  
  
    -   <span data-ttu-id="b9e74-180">Lesson 1 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-180">Lesson 1 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-181">Lesson 2 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-181">Lesson 2 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-182">Lesson 3 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-182">Lesson 3 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-183">Lesson 4 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-183">Lesson 4 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-184">Lesson 4 Start</span><span class="sxs-lookup"><span data-stu-id="b9e74-184">Lesson 4 Start</span></span>  
  
    -   <span data-ttu-id="b9e74-185">Lesson 5 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-185">Lesson 5 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-186">Lesson 6 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-186">Lesson 6 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-187">Lesson 7 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-187">Lesson 7 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-188">Lesson 8 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-188">Lesson 8 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-189">Lesson 9 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-189">Lesson 9 Complete</span></span>  
  
    -   <span data-ttu-id="b9e74-190">Lesson 10 Complete</span><span class="sxs-lookup"><span data-stu-id="b9e74-190">Lesson 10 Complete</span></span>  
  
4.  <span data-ttu-id="b9e74-191">取消对这些文件的只读权限。</span><span class="sxs-lookup"><span data-stu-id="b9e74-191">Remove the read-only permissions on these files.</span></span> <span data-ttu-id="b9e74-192">右键单击父文件夹“Analysis Services Tutorial SQL Server 2012”，选择“属性”\*\*\*\*，然后清除“只读”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="b9e74-192">Right-click the parent folder, "Analysis Services Tutorial SQL Server 2012", select **Properties**, and clear the checkbox for **Read-only**.</span></span> <span data-ttu-id="b9e74-193">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b9e74-193">Click **OK**.</span></span> <span data-ttu-id="b9e74-194">将更改应用至此文件夹、子文件夹和文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-194">Apply the changes to this folder, subfolders, and files.</span></span>  
  
5.  <span data-ttu-id="b9e74-195">启动 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b9e74-195">Start [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
6.  <span data-ttu-id="b9e74-196">打开与您要使用的课程对应的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-196">Open the solution (.sln) file that corresponds to the lesson you are using.</span></span> <span data-ttu-id="b9e74-197">例如，在名为“Lesson 1 Complete”的文件夹中，您应打开 Analysis Services Tutorial.sln 文件。</span><span class="sxs-lookup"><span data-stu-id="b9e74-197">For example, in the folder named "Lesson 1 Complete", you would open the Analysis Services Tutorial.sln file.</span></span>  
  
7.  <span data-ttu-id="b9e74-198">部署解决方案以验证是否正确设置了数据库权限和服务器位置信息。</span><span class="sxs-lookup"><span data-stu-id="b9e74-198">Deploy the solution to verify that database permissions and server location information is set up correctly.</span></span>  
  
     <span data-ttu-id="b9e74-199">如果 Analysis Services 和数据库引擎是作为默认实例 (MSSQLServer) 安装的，并且所有软件在同一台计算机上运行，则可以单击“生成”菜单上的“部署解决方案”\*\*\*\* 来生成示例项目并将其部署到本地 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="b9e74-199">If Analysis Services and the Database Engine are installed as the default instance (MSSQLServer) and all software is running on the same computer, you can click **Deploy Solution** on the Build menu to build and deploy the sample project to the local Analysis Services instance.</span></span> <span data-ttu-id="b9e74-200">在部署过程中，将从本地数据库引擎实例上的 **AdventureWorksDW2012** 数据库处理（或导入）数据。</span><span class="sxs-lookup"><span data-stu-id="b9e74-200">During deployment, data will be processed (or imported) from the **AdventureWorksDW2012** database on the local Database Engine instance.</span></span> <span data-ttu-id="b9e74-201">将在包含从数据库引擎检索的数据的 Analysis Services 实例上创建新的 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="b9e74-201">A new Analysis Services database will be created on the Analysis Services instance that contains the data retrieved from the Database Engine.</span></span>  
  
     <span data-ttu-id="b9e74-202">如果出现错误，请检查前面关于设置数据库权限的步骤。</span><span class="sxs-lookup"><span data-stu-id="b9e74-202">If you encounter errors, review the previous steps on setting up database permissions.</span></span> <span data-ttu-id="b9e74-203">此外，您还可能需要更改服务器名称。</span><span class="sxs-lookup"><span data-stu-id="b9e74-203">Additionally, you might also need to change server names.</span></span> <span data-ttu-id="b9e74-204">默认服务器名称为 localhost。</span><span class="sxs-lookup"><span data-stu-id="b9e74-204">The default server name is localhost.</span></span> <span data-ttu-id="b9e74-205">如果服务器安装在远程计算机上或作为命名实例安装，必须覆盖默认名称以使用对于您的安装有效的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="b9e74-205">If your servers are installed on remote computers or as named instances, you must override the default to use a server name that is valid for your installation.</span></span> <span data-ttu-id="b9e74-206">此外，如果服务器位于远程计算机上，则可能需要配置 Windows 防火墙以允许对它们进行访问。</span><span class="sxs-lookup"><span data-stu-id="b9e74-206">Furthermore, if the servers are on remote computers, you might need to configure Windows Firewall to allow access to the servers.</span></span>  
  
     <span data-ttu-id="b9e74-207">用于连接到数据库引擎的服务器名称在多维解决方案的数据源对象中指定（《Adventure Works 教程》），并在解决方案资源管理器中可见。</span><span class="sxs-lookup"><span data-stu-id="b9e74-207">The server name for connecting to the database engine is specified in the Data Source object of the multidimensional solution (Adventure Works Tutorial), visible in Solution Explorer.</span></span>  
  
     <span data-ttu-id="b9e74-208">用于连接到 Analysis Services 的服务器名称在项目“属性页”的“部署”选项卡中指定，并且也在解决方案资源管理器中可见。</span><span class="sxs-lookup"><span data-stu-id="b9e74-208">The server name for connecting to Analysis Services is specified in the Deployment tab of the Property Pages of the project, also visible in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="b9e74-209">启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="b9e74-209">Start SQL Server Management Studio.</span></span> <span data-ttu-id="b9e74-210">在 SQL Server Management Studio 中，连接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="b9e74-210">In SQL Server Management Studio, connect to Analysis Services.</span></span> <span data-ttu-id="b9e74-211">验证名为 **Analysis Services Tutorial** 的数据库是否正在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="b9e74-211">Verify that a database named **Analysis Services Tutorial** is running on the server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b9e74-212">下一步</span><span class="sxs-lookup"><span data-stu-id="b9e74-212">Next Step</span></span>  
 <span data-ttu-id="b9e74-213">您现在可以使用本教程了。</span><span class="sxs-lookup"><span data-stu-id="b9e74-213">You are now ready to use the tutorial.</span></span> <span data-ttu-id="b9e74-214">有关如何入门的详细信息，请参阅[多维建模（Adventure Works 教程）](multidimensional-modeling-adventure-works-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e74-214">For more information about how to get started, see [Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e74-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9e74-215">See Also</span></span>  
 <span data-ttu-id="b9e74-216">[从安装向导安装 SQL Server 2014 &#40;安装程序&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="b9e74-216">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="b9e74-217">[将 Windows 防火墙配置为允许 Analysis Services 访问](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) </span><span class="sxs-lookup"><span data-stu-id="b9e74-217">[Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) </span></span>  
 [<span data-ttu-id="b9e74-218">配置 Windows 防火墙以允许 SQL Server 访问</span><span class="sxs-lookup"><span data-stu-id="b9e74-218">Configure the Windows Firewall to Allow SQL Server Access</span></span>](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
