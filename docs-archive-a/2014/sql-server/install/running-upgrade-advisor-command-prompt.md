---
title: " (命令提示符下运行升级顾问) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577220"
---
# <a name="running-upgrade-advisor-command-prompt"></a><span data-ttu-id="95c21-102">运行升级顾问（命令提示符）</span><span class="sxs-lookup"><span data-stu-id="95c21-102">Running Upgrade Advisor (Command Prompt)</span></span>
  <span data-ttu-id="95c21-103">使用**UpgradeAdvisorWizardCmd**实用工具从命令提示符运行升级顾问。</span><span class="sxs-lookup"><span data-stu-id="95c21-103">Use the **UpgradeAdvisorWizardCmd** utility to run Upgrade Advisor from the command prompt.</span></span> <span data-ttu-id="95c21-104">可以选择以 XML 格式或以逗号分隔值文件来接收结果。</span><span class="sxs-lookup"><span data-stu-id="95c21-104">You can choose to receive results in XML format or in a file with comma-separated values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c21-105">语法</span><span class="sxs-lookup"><span data-stu-id="95c21-105">Syntax</span></span>  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="95c21-106">参数</span><span class="sxs-lookup"><span data-stu-id="95c21-106">Arguments</span></span>  
 <span data-ttu-id="95c21-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="95c21-107">**-?**</span></span>  
 <span data-ttu-id="95c21-108">显示命令的语法。</span><span class="sxs-lookup"><span data-stu-id="95c21-108">Displays the command syntax.</span></span>  
  
 <span data-ttu-id="95c21-109">**-Read-configfile** _filename_</span><span class="sxs-lookup"><span data-stu-id="95c21-109">**-ConfigFile** _filename_</span></span>  
 <span data-ttu-id="95c21-110">XML 文件的路径名和文件名，其中包含运行**UpgradeAdvisorWizardCmd**实用程序时要使用的设置。</span><span class="sxs-lookup"><span data-stu-id="95c21-110">Is the path name and file name of an XML file that contains settings to use when you run the **UpgradeAdvisorWizardCmd** utility.</span></span>  
  
 <span data-ttu-id="95c21-111">*<server_info>*</span><span class="sxs-lookup"><span data-stu-id="95c21-111">*<server_info>*</span></span>  
 <span data-ttu-id="95c21-112">指定要分析的计算机和实例。</span><span class="sxs-lookup"><span data-stu-id="95c21-112">Specifies which computer and instance to analyze.</span></span> <span data-ttu-id="95c21-113">如果不使用配置文件，则使用这些选项。</span><span class="sxs-lookup"><span data-stu-id="95c21-113">Use these options if you are not using a configuration file.</span></span>  
  
 <span data-ttu-id="95c21-114">*<server_info>* 可以是以下四个参数的任意组合：</span><span class="sxs-lookup"><span data-stu-id="95c21-114">*<server_info>* can be any combination of the following four arguments:</span></span>  
  
 <span data-ttu-id="95c21-115">**-服务器** _server_name_</span><span class="sxs-lookup"><span data-stu-id="95c21-115">**-Server** _server_name_</span></span>  
 <span data-ttu-id="95c21-116">指定要分析的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-116">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="95c21-117">这可以是本地计算机（默认值）或远程计算机。</span><span class="sxs-lookup"><span data-stu-id="95c21-117">This can be the local computer, which is the default value, or a remote computer.</span></span>  
  
 <span data-ttu-id="95c21-118">**-Instance** _instance_name_</span><span class="sxs-lookup"><span data-stu-id="95c21-118">**-Instance** _instance_name_</span></span>  
 <span data-ttu-id="95c21-119">指定要分析的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-119">Specifies the name of the instance to analyze.</span></span> <span data-ttu-id="95c21-120">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-120">There is no default value.</span></span> <span data-ttu-id="95c21-121">如果未指定此参数， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 则不会扫描。</span><span class="sxs-lookup"><span data-stu-id="95c21-121">If you do not specify this parameter, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not scanned.</span></span> <span data-ttu-id="95c21-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例的值是 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="95c21-122">The value for a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is MSSQLSERVER.</span></span> <span data-ttu-id="95c21-123">对于命名实例，使用实例名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-123">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="95c21-124">**-ASInstance**  _AS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="95c21-124">**-ASInstance**  _AS_instance_name_</span></span>  
 <span data-ttu-id="95c21-125">指定要分析的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-125">Specifies the name of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="95c21-126">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-126">There is no default value.</span></span> <span data-ttu-id="95c21-127">如果不指定此值，则不会扫描 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95c21-127">If you do not specify this value, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="95c21-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 默认实例的值是 MSSQLServerOLAPService。</span><span class="sxs-lookup"><span data-stu-id="95c21-128">The value for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is MSSQLServerOLAPService.</span></span> <span data-ttu-id="95c21-129">对于命名实例，使用实例名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-129">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="95c21-130">**-RSInstance**  _RS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="95c21-130">**-RSInstance**  _RS_instance_name_</span></span>  
 <span data-ttu-id="95c21-131">指定要分析的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-131">Specifies the name of the instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="95c21-132">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-132">There is no default value.</span></span> <span data-ttu-id="95c21-133">如果不指定此值，则不会扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95c21-133">If you do not specify this value, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="95c21-134">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 默认实例的值是 ReportServer。</span><span class="sxs-lookup"><span data-stu-id="95c21-134">The value for a default instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is ReportServer.</span></span> <span data-ttu-id="95c21-135">对于命名实例，使用实例名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-135">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="95c21-136">**-SqlUser** _login_id_</span><span class="sxs-lookup"><span data-stu-id="95c21-136">**-SqlUser** _login_id_</span></span>  
 <span data-ttu-id="95c21-137">如果使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则此值是升级顾问将用于连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="95c21-137">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, this value is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that Upgrade Advisor will use to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="95c21-138">如果不指定登录名，则使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="95c21-138">If you do not specify a login, Windows Authentication is used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="95c21-139">**-SqlPassword** _密码_</span><span class="sxs-lookup"><span data-stu-id="95c21-139">**-SqlPassword** _password_</span></span>  
 <span data-ttu-id="95c21-140">如果使用 **-SqlUser**参数，请使用此参数指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="95c21-140">If you use the **-SqlUser** argument, use this argument to specify the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="95c21-141">**-CSV**</span><span class="sxs-lookup"><span data-stu-id="95c21-141">**-CSV**</span></span>  
 <span data-ttu-id="95c21-142">指定除了标准 XML 结果外还将结果以逗号分隔值写入到 .csv 文件中。</span><span class="sxs-lookup"><span data-stu-id="95c21-142">Specifies to provide results as comma-separated values to a .csv file in addition to the standard XML results.</span></span> <span data-ttu-id="95c21-143">结果将写入 "我的文档" \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级 Advisor\110\Reports 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="95c21-143">Results are written to the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports folder.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="95c21-144">返回值</span><span class="sxs-lookup"><span data-stu-id="95c21-144">Return Values</span></span>  
 <span data-ttu-id="95c21-145">下表显示**UpgradeAdvisorWizardCmd**返回的值。</span><span class="sxs-lookup"><span data-stu-id="95c21-145">The following table shows the values that **UpgradeAdvisorWizardCmd** returns.</span></span>  
  
|<span data-ttu-id="95c21-146">值</span><span class="sxs-lookup"><span data-stu-id="95c21-146">Value</span></span>|<span data-ttu-id="95c21-147">说明</span><span class="sxs-lookup"><span data-stu-id="95c21-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="95c21-148">0</span><span class="sxs-lookup"><span data-stu-id="95c21-148">0</span></span>|<span data-ttu-id="95c21-149">成功完成分析，找不到任何升级问题。</span><span class="sxs-lookup"><span data-stu-id="95c21-149">Analysis succeeded, no upgrade issues found.</span></span>|  
|<span data-ttu-id="95c21-150">正整数</span><span class="sxs-lookup"><span data-stu-id="95c21-150">positive integer</span></span>|<span data-ttu-id="95c21-151">成功完成分析，找到升级问题。</span><span class="sxs-lookup"><span data-stu-id="95c21-151">Analysis succeeded, upgrade issues found.</span></span>|  
|<span data-ttu-id="95c21-152">负整数</span><span class="sxs-lookup"><span data-stu-id="95c21-152">negative integer</span></span>|<span data-ttu-id="95c21-153">分析失败。</span><span class="sxs-lookup"><span data-stu-id="95c21-153">Analysis failed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c21-154">备注</span><span class="sxs-lookup"><span data-stu-id="95c21-154">Remarks</span></span>  
 <span data-ttu-id="95c21-155">可在一个 XML 配置文件中提供运行分析所需的所有信息（[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证用户名和密码除外）。</span><span class="sxs-lookup"><span data-stu-id="95c21-155">All information that is required to run the analysis, other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user names and passwords, can be provided in an XML configuration file.</span></span> <span data-ttu-id="95c21-156">此 XML 配置文件记录在模板中。</span><span class="sxs-lookup"><span data-stu-id="95c21-156">This XML configuration file is documented in the template.</span></span> <span data-ttu-id="95c21-157">如果不使用配置文件，则可以通过指定计算机名和实例名使用默认设置分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中所有安装的组件。</span><span class="sxs-lookup"><span data-stu-id="95c21-157">If you do not use a configuration file, you can analyze all installed components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using default settings by specifying computer names and instance names.</span></span> <span data-ttu-id="95c21-158">有关默认配置文件设置的说明，请参阅本主题后面的“元素说明”表。</span><span class="sxs-lookup"><span data-stu-id="95c21-158">See the "Element Descriptions" table later in this topic for a description of the default configuration file settings.</span></span>  
  
## <a name="configuration-file-template"></a><span data-ttu-id="95c21-159">配置文件模板</span><span class="sxs-lookup"><span data-stu-id="95c21-159">Configuration File Template</span></span>  
 <span data-ttu-id="95c21-160">可使用以下 XML 作为模板来创建自己的配置文件。</span><span class="sxs-lookup"><span data-stu-id="95c21-160">Use the following XML as a template for creating your own configuration files.</span></span> <span data-ttu-id="95c21-161">您可以修改模板，以满足组织的需要。</span><span class="sxs-lookup"><span data-stu-id="95c21-161">You can modify the template to meet the needs of your organization.</span></span>  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a><span data-ttu-id="95c21-162">元素说明</span><span class="sxs-lookup"><span data-stu-id="95c21-162">Element Descriptions</span></span>  
  
|<span data-ttu-id="95c21-163">标记</span><span class="sxs-lookup"><span data-stu-id="95c21-163">Tag</span></span>|<span data-ttu-id="95c21-164">定义</span><span class="sxs-lookup"><span data-stu-id="95c21-164">Definition</span></span>|<span data-ttu-id="95c21-165">出现次数</span><span class="sxs-lookup"><span data-stu-id="95c21-165">Occurrence</span></span>|  
|---------|----------------|----------------|  
|`Configuration`|<span data-ttu-id="95c21-166">升级顾问配置文件的父元素。</span><span class="sxs-lookup"><span data-stu-id="95c21-166">Parent element for Upgrade Advisor configuration file.</span></span>|<span data-ttu-id="95c21-167">每个配置文件必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-167">Required once per configuration file.</span></span>|  
|`Server`|<span data-ttu-id="95c21-168">要分析的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-168">Name of the server to analyze.</span></span>|<span data-ttu-id="95c21-169">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-169">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-170">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="95c21-170">The default value is the local computer.</span></span>|  
|`Instance`|<span data-ttu-id="95c21-171">要分析的[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-171">Name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance to analyze.</span></span>|<span data-ttu-id="95c21-172">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-172">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-173">默认值为默认实例。</span><span class="sxs-lookup"><span data-stu-id="95c21-173">The default value is the default instance.</span></span><br /><br /> <span data-ttu-id="95c21-174">如果服务器上存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元素或 `IntegrationServices` 元素，则每个配置文件必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-174">Required once per configuration file, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] element or an `IntegrationServices` element is present on the server.</span></span>|  
|`Components`|<span data-ttu-id="95c21-175">包含指定要分析的组件的元素。</span><span class="sxs-lookup"><span data-stu-id="95c21-175">Contains elements that specify which components to analyze.</span></span>|<span data-ttu-id="95c21-176">每个配置文件必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-176">Required once per configuration file.</span></span>|  
|`SQLServer`|<span data-ttu-id="95c21-177">包含[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的分析设置。</span><span class="sxs-lookup"><span data-stu-id="95c21-177">Contains analysis settings for an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|<span data-ttu-id="95c21-178">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-178">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-179">如果未指定，则不会分析 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-179">If not specified, [!INCLUDE[ssDE](../../includes/ssde-md.md)] databases are not analyzed.</span></span>|  
|<span data-ttu-id="95c21-180">`Databases` 元素的 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="95c21-180">`Databases` for `SQLServer` element</span></span>|<span data-ttu-id="95c21-181">包含要分析的数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="95c21-181">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="95c21-182">对于每个 `SQLServer` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-182">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="95c21-183">如果此元素不存在，则分析实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-183">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="95c21-184">`Database` 元素的 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="95c21-184">`Database` for `SQLServer` element</span></span>|<span data-ttu-id="95c21-185">指定要分析的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-185">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="95c21-186">如果 `Databases` 元素存在，则必须出现一次或多次。</span><span class="sxs-lookup"><span data-stu-id="95c21-186">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="95c21-187">如果 `Database` 元素包含值“\*”，则分析实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-187">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="95c21-188">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-188">There is no default value.</span></span>|  
|`TraceFiles`|<span data-ttu-id="95c21-189">包含要分析的跟踪文件的列表。</span><span class="sxs-lookup"><span data-stu-id="95c21-189">Contains a list of trace files to analyze.</span></span>|<span data-ttu-id="95c21-190">对于每个 `SQLServer` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-190">Optional once per `SQLServer` element.</span></span>|  
|`TraceFile`|<span data-ttu-id="95c21-191">指定要分析的跟踪文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-191">Specifies the path and name of a trace file to analyze.</span></span>|<span data-ttu-id="95c21-192">如果 `TraceFiles` 元素存在，则必须出现一次或多次。</span><span class="sxs-lookup"><span data-stu-id="95c21-192">Required once or more if the `TraceFiles` element is present.</span></span> <span data-ttu-id="95c21-193">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-193">There is no default value.</span></span>|  
|`BatchFiles`|<span data-ttu-id="95c21-194">包含要分析的批处理文件的列表。</span><span class="sxs-lookup"><span data-stu-id="95c21-194">Contains a list of batch files to analyze.</span></span>|<span data-ttu-id="95c21-195">对于每个 `SQLServer` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-195">Optional once per `SQLServer` element.</span></span>|  
|`BatchFile`|<span data-ttu-id="95c21-196">指定要分析的批处理文件。</span><span class="sxs-lookup"><span data-stu-id="95c21-196">Specifies a batch file to analyze.</span></span> <span data-ttu-id="95c21-197">可以是多个文件。</span><span class="sxs-lookup"><span data-stu-id="95c21-197">Can be multiple.</span></span>|<span data-ttu-id="95c21-198">如果 `BatchFiles` 元素存在，则必须出现一次或多次。</span><span class="sxs-lookup"><span data-stu-id="95c21-198">Required once or more if the `BatchFiles` element is present.</span></span> <span data-ttu-id="95c21-199">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-199">There is no default value.</span></span>|  
|`BatchSeparator`|<span data-ttu-id="95c21-200">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 批处理文件中使用的批处理分隔符。</span><span class="sxs-lookup"><span data-stu-id="95c21-200">Specifies the batch separator used in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch files.</span></span>|<span data-ttu-id="95c21-201">对于每个 `SQLServer` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-201">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="95c21-202">默认值为 GO。</span><span class="sxs-lookup"><span data-stu-id="95c21-202">The default value is GO.</span></span>|  
|`AnalysisServices`|<span data-ttu-id="95c21-203">包含 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的分析设置。</span><span class="sxs-lookup"><span data-stu-id="95c21-203">Contains analysis settings for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="95c21-204">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-204">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-205">如果未指定，则不会分析 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-205">If not specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases are not analyzed.</span></span>|  
|`ASInstance`|<span data-ttu-id="95c21-206">指定实例的名称 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95c21-206">Specifies the name of an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="95c21-207">每个 `AnalysisServices` 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-207">Required once per `AnalysisServices` element.</span></span> <span data-ttu-id="95c21-208">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-208">There is no default value.</span></span>|  
|<span data-ttu-id="95c21-209">`Databases` 元素的 `Analysis Services`</span><span class="sxs-lookup"><span data-stu-id="95c21-209">`Databases` for `Analysis Services` element</span></span>|<span data-ttu-id="95c21-210">包含要分析的数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="95c21-210">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="95c21-211">对于每个 `AnalysisServices` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-211">Optional once per `AnalysisServices` element.</span></span> <span data-ttu-id="95c21-212">如果此元素不存在，则分析实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-212">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="95c21-213">`Database` 元素的 `AnalysisServices`</span><span class="sxs-lookup"><span data-stu-id="95c21-213">`Database` for `AnalysisServices` element</span></span>|<span data-ttu-id="95c21-214">指定要分析的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="95c21-214">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="95c21-215">如果 `Databases` 元素存在，则必须出现一次或多次。</span><span class="sxs-lookup"><span data-stu-id="95c21-215">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="95c21-216">如果 `Database` 元素包含值“\*”，则分析实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="95c21-216">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="95c21-217">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-217">There is no default value.</span></span>|  
|`ReportingServices`|<span data-ttu-id="95c21-218">指定对 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 运行分析。</span><span class="sxs-lookup"><span data-stu-id="95c21-218">Specifies to run analysis against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="95c21-219">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-219">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-220">如果未指定，则不会分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95c21-220">If not specified, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not analyzed.</span></span>|  
|`RSInstance`|<span data-ttu-id="95c21-221">指定实例的名称 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95c21-221">Specifies the name of an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="95c21-222">每个 `ReportingServices` 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-222">Required once per `ReportingServices` element.</span></span> <span data-ttu-id="95c21-223">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-223">There is no default value.</span></span>|  
|`IntegrationServices`|<span data-ttu-id="95c21-224">包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的分析设置。</span><span class="sxs-lookup"><span data-stu-id="95c21-224">Contains analysis settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|<span data-ttu-id="95c21-225">每个配置文件可以出现一次。</span><span class="sxs-lookup"><span data-stu-id="95c21-225">Optional once per configuration file.</span></span> <span data-ttu-id="95c21-226">如果未指定，则不会分析 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95c21-226">If not specified, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is not analyzed.</span></span>|  
|`PackagePath`|<span data-ttu-id="95c21-227">指定一组 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的路径。</span><span class="sxs-lookup"><span data-stu-id="95c21-227">Specifies the path of a set of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>|<span data-ttu-id="95c21-228">对于每个 `IntegrationServices` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="95c21-228">Optional once per `IntegrationServices` element.</span></span> <span data-ttu-id="95c21-229">如果此元素不存在，则会在实例上进行分析， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而不会分析外部存储的包。</span><span class="sxs-lookup"><span data-stu-id="95c21-229">If this element is not present, analysis occurs on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and no externally stored packages are analyzed.</span></span> <span data-ttu-id="95c21-230">无默认值。</span><span class="sxs-lookup"><span data-stu-id="95c21-230">There is no default value.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="95c21-231">示例</span><span class="sxs-lookup"><span data-stu-id="95c21-231">Examples</span></span>  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a><span data-ttu-id="95c21-232">A.</span><span class="sxs-lookup"><span data-stu-id="95c21-232">A.</span></span> <span data-ttu-id="95c21-233">使用配置文件运行升级顾问</span><span class="sxs-lookup"><span data-stu-id="95c21-233">Run Upgrade Advisor Using a Configuration File</span></span>  
 <span data-ttu-id="95c21-234">下面的示例演示如何通过使用指定分析内容的配置文件从命令提示符运行升级顾问。</span><span class="sxs-lookup"><span data-stu-id="95c21-234">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file that specifies what to analyze.</span></span> <span data-ttu-id="95c21-235">本例使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95c21-235">This example uses Windows Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a><span data-ttu-id="95c21-236">B.</span><span class="sxs-lookup"><span data-stu-id="95c21-236">B.</span></span> <span data-ttu-id="95c21-237">使用默认配置设置运行升级顾问</span><span class="sxs-lookup"><span data-stu-id="95c21-237">Run Upgrade Advisor Using Default Configuration Settings</span></span>  
 <span data-ttu-id="95c21-238">下面的示例演示如何通过使用默认配置设置和 Windows 身份验证从命令提示符运行升级顾问。</span><span class="sxs-lookup"><span data-stu-id="95c21-238">The following example shows how to run Upgrade Advisor from the command prompt by using default configuration settings and Windows Authentication.</span></span>  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a><span data-ttu-id="95c21-239">C.</span><span class="sxs-lookup"><span data-stu-id="95c21-239">C.</span></span> <span data-ttu-id="95c21-240">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证运行升级顾问</span><span class="sxs-lookup"><span data-stu-id="95c21-240">Run Upgrade Advisor Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication</span></span>  
 <span data-ttu-id="95c21-241">下面的示例演示如何通过使用配置文件从命令提示符运行升级顾问。</span><span class="sxs-lookup"><span data-stu-id="95c21-241">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file.</span></span> <span data-ttu-id="95c21-242">本例指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户名和密码以连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="95c21-242">This example specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name and password to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a><span data-ttu-id="95c21-243">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95c21-243">See Also</span></span>  
 <span data-ttu-id="95c21-244">[解决升级问题](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="95c21-244">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="95c21-245">[使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="95c21-245">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="95c21-246">&#40;用户界面运行升级顾问&#41;</span><span class="sxs-lookup"><span data-stu-id="95c21-246">Running Upgrade Advisor &#40;User Interface&#41;</span></span>](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
