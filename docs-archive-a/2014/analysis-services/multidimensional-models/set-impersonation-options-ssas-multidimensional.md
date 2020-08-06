---
title: 设置 (SSAS-多维) 的模拟选项 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.impersonationinfo.f1
helpviewer_keywords:
- Impersonation Information dialog box
ms.assetid: 8e127f72-ef23-44ad-81e6-3dd58981770e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b9a8526ff4b8a6dd6f68d13817e427ec70d1953
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588718"
---
# <a name="set-impersonation-options-ssas---multidimensional"></a><span data-ttu-id="ad9cf-102">设置模拟选项（SSAS - 多维）</span><span class="sxs-lookup"><span data-stu-id="ad9cf-102">Set Impersonation Options (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="ad9cf-103">在 Analysis Services 模型中创建 `data source` 对象时，您必须配置的一个设置是模拟选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-103">When creating a `data source` object in an Analysis Services model, one of the settings that you must configure is an impersonation option.</span></span> <span data-ttu-id="ad9cf-104">此选项确定 Analysis Services 在执行与连接相关的本地操作（如加载 OLE DB 数据访问接口或在支持漫游配置文件的环境中解析用户配置文件信息）时是否采用特定 Windows 用户帐户的标识。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-104">This option determines whether Analysis Services assumes the identity of a specific Windows user account when performing local operations related to the connection, such as loading an OLE DB data provider or resolving user profile information in environments that support roaming profiles.</span></span>  
  
 <span data-ttu-id="ad9cf-105">对于使用 Windows 身份验证的连接，模拟选项还确定对外部数据源执行查询的用户标识。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-105">For connections that use Windows authentication, the impersonation option also determines the user identity under which queries execute on the external data source.</span></span> <span data-ttu-id="ad9cf-106">例如，如果你将模拟选项设置为 **contoso\dbuser**，则在处理期间用于检索数据的查询将以数据库服务器上的 **contoso\dbuser** 身份执行。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-106">For example, if you set the impersonation option to **contoso\dbuser**, queries used to retrieve data during processing will execute as **contoso\dbuser** on the database server.</span></span>  
  
 <span data-ttu-id="ad9cf-107">本主题说明在配置数据源对象时如何在 **“模拟信息”** 对话框中设置模拟选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-107">This topic explains how to set impersonation options in the **Impersonation Information** dialog box when configuring a data source object.</span></span>  
  
## <a name="set-impersonation-options-in-sql-server-data-tools"></a><span data-ttu-id="ad9cf-108">在 SQL Server Data Tools 中设置模拟选项</span><span class="sxs-lookup"><span data-stu-id="ad9cf-108">Set impersonation options in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="ad9cf-109">在解决方案资源管理器中双击某一数据源以便打开数据源设计器。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-109">Double-click a data source in Solution Explorer to open Data Source Designer.</span></span>  
  
2.  <span data-ttu-id="ad9cf-110">在数据源设计器中单击 **“模拟信息”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-110">Click the **Impersonation Information** tab in Data Source Designer.</span></span>  
  
3.  <span data-ttu-id="ad9cf-111">选择本主题的 [模拟选项](#bkmk_options) 中所述的一个选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-111">Choose an option described in [Impersonation options](#bkmk_options) in this topic.</span></span>  
  
## <a name="set-impersonation-options-in-management-studio"></a><span data-ttu-id="ad9cf-112">在 Management Studio 中设置模拟选项</span><span class="sxs-lookup"><span data-stu-id="ad9cf-112">Set impersonation options in Management Studio</span></span>  
 <span data-ttu-id="ad9cf-113">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，通过针对这些对话框的以下属性单击省略号 (**...**) 按钮，打开“模拟信息”\*\*\*\* 对话框：</span><span class="sxs-lookup"><span data-stu-id="ad9cf-113">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open the **Impersonation Information** dialog box by clicking the ellipsis (**...**) button for the following properties of these dialog boxes:</span></span>  
  
-   <span data-ttu-id="ad9cf-114">**“数据库属性”** 对话框（通过“数据源模拟信息”属性）。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-114">**Database Properties** dialog box, through the Data Source Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="ad9cf-115">**“数据源属性”** 对话框（通过“模拟信息”属性）。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-115">**Data Source Properties** dialog box, through the Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="ad9cf-116">**“程序集属性”** 对话框（通过“模拟信息”属性）。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-116">**Assembly Properties** dialog box, through the Impersonation Info property.</span></span>  
  
##  <a name="impersonation-options"></a><a name="bkmk_options"></a> <span data-ttu-id="ad9cf-117">模拟选项</span><span class="sxs-lookup"><span data-stu-id="ad9cf-117">Impersonation options</span></span>  
 <span data-ttu-id="ad9cf-118">对话框中的所有选项都可用，但并非所有选项都适合每种情况。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-118">All options are available in the dialog box, but not all options are appropriate for every scenario.</span></span> <span data-ttu-id="ad9cf-119">使用以下信息来确定最适合于您的情况的选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-119">Use the following information to determine the best option for your scenario.</span></span>  
  
 <span data-ttu-id="ad9cf-120">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="ad9cf-120">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="ad9cf-121">选择此选项以使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象使用按以下格式指定的 Windows 用户帐户的安全凭据： *\<Domain name>***\\***\<User account name>* 。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-121">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of a Windows user account specified in this format: *\<Domain name>***\\***\<User account name>*.</span></span>  
  
 <span data-ttu-id="ad9cf-122">选择此选项可使用一个专用的最小权限的 Windows 用户标识，该用户标识是您为数据访问目的而专门创建的。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-122">Choose this option to use a dedicated, least-privilege Windows user identity that you have created specifically for data access purposes.</span></span> <span data-ttu-id="ad9cf-123">例如，如果您定期创建用于检索在报表中使用的数据的通用帐户，则可以在此处指定该帐户。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-123">For example, if you routinely create a general purpose account for retrieving data used in reports, you can specify that account here.</span></span>  
  
 <span data-ttu-id="ad9cf-124">对于多维数据库，指定的凭据将用于执行处理、ROLAP 查询、外部绑定、本地多维数据集、挖掘模型、远程分区、链接对象以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-124">For multidimensional databases, the specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="ad9cf-125">对于表格数据库，指定的凭据将用于执行处理、针对关系数据存储区（使用 DirectQuery）运行的查询、外部绑定、远程分区以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-125">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), out-of-line bindings, remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="ad9cf-126">对于 DMX OPENQUERY 语句，则忽略此选项，并且将使用当前用户的凭据而不是指定用户帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-126">For DMX OPENQUERY statements, this option is ignored and the credentials of the current user will be used rather than the specified user account.</span></span>  
  
 <span data-ttu-id="ad9cf-127">**使用服务帐户**</span><span class="sxs-lookup"><span data-stu-id="ad9cf-127">**Use the service account**</span></span>  
 <span data-ttu-id="ad9cf-128">选择此选项将使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象使用与管理该对象的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务相关联的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-128">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="ad9cf-129">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-129">This is the default option.</span></span> <span data-ttu-id="ad9cf-130">在以前的版本中，这是唯一可以使用的选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-130">In previous releases, this was the only option you could use.</span></span> <span data-ttu-id="ad9cf-131">若要在服务级别而不是单独的用户帐户级别监视数据访问，您可能会愿意选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-131">You might prefer this option to monitor data access at the service level rather than individual user accounts.</span></span>  
  
 <span data-ttu-id="ad9cf-132">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，根据您使用的不同操作系统，服务帐户可能是 NetworkService 或为特定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例创建的内置虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-132">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], depending on the operating system you are using, the service account might be NetworkService or a built-in virtual account created for a specific [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="ad9cf-133">如果您为使用 Windows 身份验证的连接选择服务帐户，请记住要为此帐户创建数据库登录名并授予读取权限，因为它将用于在处理期间检索数据。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-133">If you choose the service account for a connection that uses Windows authentication, remember to create a database login for this account and grant read permissions, as it will be used to retrieve data during processing.</span></span> <span data-ttu-id="ad9cf-134">有关服务帐户的详细信息，请参阅 [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-134">For more information about the service account, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad9cf-135">使用数据库身份验证时，如果正在 Analysis Services 的专用虚拟帐户下运行服务，应选择 **“使用服务帐户”** 模拟选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-135">When using database authentication, you should choose the **Use the service account** impersonation option if the service is running under the dedicated virtual account for Analysis Services.</span></span> <span data-ttu-id="ad9cf-136">此帐户将具有访问本地文件的权限。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-136">This account will have permissions to access local files.</span></span> <span data-ttu-id="ad9cf-137">如果服务以 NetworkService 身份运行，最好使用具有 **“允许在本地登录”** 权限的最小权限的 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-137">If the service runs as NetworkService, a better alternative is to use a least privilege Windows user account that has **Allow log on locally** permissions.</span></span> <span data-ttu-id="ad9cf-138">根据您提供的帐户，您可能还需要授予对 Analysis Services 程序文件夹的文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-138">Depending on the account you provide, you might also need to grant file access permissions on the Analysis Services program folder.</span></span>  
  
 <span data-ttu-id="ad9cf-139">对于多维数据库，服务帐户凭据将用于处理、ROLAP 查询、远程分区、链接对象以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-139">For multidimensional databases, the service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="ad9cf-140">对于表格数据库，指定的凭据将用于执行处理、针对关系数据存储区（使用 DirectQuery）运行的查询、远程分区以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-140">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="ad9cf-141">对于 DMX OPENQUERY 语句、本地多维数据集和挖掘模型，即使您选择服务帐户选项，也将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-141">For DMX OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used even if you choose the service account option.</span></span> <span data-ttu-id="ad9cf-142">外部绑定不支持此服务帐户选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-142">The service account option is not supported for out-of-line bindings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad9cf-143">如果服务帐户不具有对 Analysis Services 实例的管理员权限，在处理多维数据集的数据挖掘模型时会出错。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-143">Errors can occur when processing a data mining model from a cube if the service account does not have administrator permissions on the Analysis Services instance.</span></span> <span data-ttu-id="ad9cf-144">有关详细信息，请参阅 [挖掘结构：数据源是 OLAP 多维数据集时的处理问题](https://go.microsoft.com/fwlink/?LinkId=251610)。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-144">For more information, see [Mining Structure: Issue while Processing when DataSource is OLAP Cube](https://go.microsoft.com/fwlink/?LinkId=251610).</span></span>  
  
 <span data-ttu-id="ad9cf-145">**使用当前用户的凭据**</span><span class="sxs-lookup"><span data-stu-id="ad9cf-145">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="ad9cf-146">选择此选项将使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象使用当前用户的安全凭据来处理外部绑定、DMX OPENQUERY、本地多维数据集和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-146">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span>  
  
 <span data-ttu-id="ad9cf-147">对于表格数据库，不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-147">This option is not supported for tabular databases.</span></span>  
  
 <span data-ttu-id="ad9cf-148">使用外部绑定的本地多维数据集和处理除外，多维数据库不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-148">With the exception of local cubes and processing using out-of-line bindings, this option is not supported for multidimensional databases.</span></span>  
  
 <span data-ttu-id="ad9cf-149">“默认值”\*\*\*\* 或“继承”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ad9cf-149">**Default** or **Inherit**</span></span>  
 <span data-ttu-id="ad9cf-150">此对话框对于在数据库级别设置的模拟选项使用“默认值”\*\*\*\*；而对于在数据源级别设置的模拟选项使用“继承”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-150">The dialog box uses **Default** for the impersonation options set at the database level and **Inherit** for impersonation options set at the data source level.</span></span>  
  
 <span data-ttu-id="ad9cf-151">**数据源-Inherit 选项**</span><span class="sxs-lookup"><span data-stu-id="ad9cf-151">**Data Sources - Inherit Option**</span></span>  
  
 <span data-ttu-id="ad9cf-152">在数据源级别， **“继承”** 指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 应使用父对象的模拟选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-152">At the data source level, **Inherit** specifies that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should use the impersonation option of the parent object.</span></span> <span data-ttu-id="ad9cf-153">在多维模型中，父对象是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-153">In a multidimensional model, the parent object is the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="ad9cf-154">通过选择 **“继承”** 选项，您可为此数据源以及属于同一个数据库的其他数据源集中管理模拟设置。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-154">Choosing the **Inherit** option lets you centrally manage the impersonation settings for this and other data sources that are part of the same database.</span></span> <span data-ttu-id="ad9cf-155">为使此选项有意义，请在数据库级别选择一个特定的 Windows 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-155">For this option to be meaningful, choose a specific Windows user name and password at the database level.</span></span> <span data-ttu-id="ad9cf-156">否则，结合对数据源使用 **“继承”** 以及对数据库使用 **“默认值”** 等效于使用服务帐户选项。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-156">Otherwise, the combination of **Inherit** on the data source and **Default** on the database are equivalent to using service account option.</span></span>  
  
 <span data-ttu-id="ad9cf-157">要在数据库级别指定 Windows 用户名和密码，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ad9cf-157">To specify a Windows user name and password at the database level, do the following:</span></span>  
  
1.  <span data-ttu-id="ad9cf-158">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中右键单击该数据库并选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-158">Right-click the database in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ad9cf-159">在 **“数据源模拟信息”** 中，指定 Windows 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-159">In **Data Source Impersonation Info**, specify a Windows user name and password.</span></span>  
  
3.  <span data-ttu-id="ad9cf-160">右键单击每个数据源并查看其属性，以便确保每个数据源都在使用“继承”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-160">Right-click each data source and view its properties to ensure that each one is using the **Inherit** option.</span></span>  
  
 <span data-ttu-id="ad9cf-161">有关数据库级别的默认设置的详细信息，请参阅[设置多维数据库属性 (Analysis Services)](set-multidimensional-database-properties-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-161">For more information about default settings at the database level, see [Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md).</span></span>  
  
 <span data-ttu-id="ad9cf-162">**数据库-默认选项**</span><span class="sxs-lookup"><span data-stu-id="ad9cf-162">**Databases - Default option**</span></span>  
  
 <span data-ttu-id="ad9cf-163">对于表格数据库， **“默认值”** 意味着使用服务帐户。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-163">For tabular databases, **Default** means use the service account.</span></span>  
  
 <span data-ttu-id="ad9cf-164">对于多维数据库， **“默认值”** 意味着使用服务帐户，并将当前用户用于数据挖掘操作。</span><span class="sxs-lookup"><span data-stu-id="ad9cf-164">For multidimensional databases, **Default** means use the service account, and current user for data mining operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9cf-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad9cf-165">See Also</span></span>  
 <span data-ttu-id="ad9cf-166">[&#40;SSAS 多维&#41;创建数据源](create-a-data-source-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="ad9cf-166">[Create a Data Source &#40;SSAS Multidimensional&#41;](create-a-data-source-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="ad9cf-167">[设置数据源属性 &#40;SSAS 多维&#41;](set-data-source-properties-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="ad9cf-167">[Set Data Source Properties &#40;SSAS Multidimensional&#41;](set-data-source-properties-ssas-multidimensional.md) </span></span>  
 [<span data-ttu-id="ad9cf-168">DirectQuery 部署方案 &#40;SSAS 表格&#41;</span><span class="sxs-lookup"><span data-stu-id="ad9cf-168">DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;</span></span>](../directquery-deployment-scenarios-ssas-tabular.md)  
  
  
