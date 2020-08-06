---
title: 使用配置文件安装 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a2f09ad6253762fe5b525f6c918931f4806c84c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688159"
---
# <a name="install-sql-server-2014-using-a-configuration-file"></a><span data-ttu-id="ed661-102">使用配置文件安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="ed661-102">Install SQL Server 2014 Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ed661-103">安装程序提供了基于系统默认值和运行时输入生成配置文件的功能。</span><span class="sxs-lookup"><span data-stu-id="ed661-103">Setup provides the ability to generate a configuration file based upon the system default and run-time inputs.</span></span> <span data-ttu-id="ed661-104">可以使用配置文件在整个企业中部署具有相同配置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed661-104">You can use the configuration file to deploy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] throughout the enterprise with the same configuration.</span></span> <span data-ttu-id="ed661-105">通过创建一个启动 Setup.exe 的批处理文件，还可以使企业范围内的手动安装得以标准化。</span><span class="sxs-lookup"><span data-stu-id="ed661-105">You can also standardize manual installations throughout the enterprise, by creating a batch file that launches Setup.exe.</span></span>  
  
 <span data-ttu-id="ed661-106">安装程序仅支持通过命令提示符使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-106">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="ed661-107">下面列出了在使用配置文件时参数的处理顺序：</span><span class="sxs-lookup"><span data-stu-id="ed661-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="ed661-108">配置文件覆盖包中的默认值</span><span class="sxs-lookup"><span data-stu-id="ed661-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="ed661-109">命令行的值覆盖配置文件中的值</span><span class="sxs-lookup"><span data-stu-id="ed661-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="ed661-110">配置文件可以用来跟踪每个安装的参数和值。</span><span class="sxs-lookup"><span data-stu-id="ed661-110">The configuration file can be used to track the parameters and values for each installation.</span></span> <span data-ttu-id="ed661-111">这使得配置文件适合用于对安装进行验证和审核。</span><span class="sxs-lookup"><span data-stu-id="ed661-111">This makes the configuration file useful for verifying and auditing the installations.</span></span>  
  
## <a name="configuration-file-structure"></a><span data-ttu-id="ed661-112">配置文件结构</span><span class="sxs-lookup"><span data-stu-id="ed661-112">Configuration File Structure</span></span>  
 <span data-ttu-id="ed661-113">ConfigurationFile.ini 文件是一个文本文件，其中具有参数（名称/值对）和描述性注释。</span><span class="sxs-lookup"><span data-stu-id="ed661-113">The ConfigurationFile.ini file is a text file with parameters (name/value pair) and descriptive comments.</span></span>  
  
 <span data-ttu-id="ed661-114">下面是 ConfigurationFile.ini 文件的一个示例：</span><span class="sxs-lookup"><span data-stu-id="ed661-114">The following is an example of a ConfigurationFile.ini file:</span></span>  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### <a name="how-to-generate-a-configuration-file"></a><span data-ttu-id="ed661-115">如何生成配置文件</span><span class="sxs-lookup"><span data-stu-id="ed661-115">How to generate a configuration file</span></span>  
  
1.  <span data-ttu-id="ed661-116">插入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质，</span><span class="sxs-lookup"><span data-stu-id="ed661-116">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="ed661-117">然后双击根文件夹中的 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="ed661-117">From the root folder, double-click Setup.exe.</span></span> <span data-ttu-id="ed661-118">若要从网络共享进行安装，请找到共享中的根文件夹，然后双击 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="ed661-118">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ed661-119">Express Edition 安装程序不会自动创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-119">Express Edition setup does not create a configuration file automatically.</span></span> <span data-ttu-id="ed661-120">以下命令将启动安装程序并创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-120">The following command will start  setup and create a configuration file.</span></span>  
    >   
    >  <span data-ttu-id="ed661-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span><span class="sxs-lookup"><span data-stu-id="ed661-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span></span>  
  
2.  <span data-ttu-id="ed661-122">按照向导操作，直到出现 **“准备安装”** 页。</span><span class="sxs-lookup"><span data-stu-id="ed661-122">Follow the wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="ed661-123">配置文件的路径是在 **“准备安装”** 页的配置文件路径部分中指定的。</span><span class="sxs-lookup"><span data-stu-id="ed661-123">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span> <span data-ttu-id="ed661-124">有关如何安装的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装&#41;](install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="ed661-124">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="ed661-125">取消安装并且不要真正完成安装，以便生成 INI 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-125">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ed661-126">安装程序基础结构将写出已运行操作的所有适当参数，但不包括密码等敏感信息。</span><span class="sxs-lookup"><span data-stu-id="ed661-126">The setup infrastructure writes out all the appropriate parameters for the actions that were run, with the exception of sensitive information such as passwords.</span></span> <span data-ttu-id="ed661-127">/IAcceptSQLServerLicenseTerms 参数也不写出到配置文件，它要求修改配置文件或在命令提示符下提供一个值。</span><span class="sxs-lookup"><span data-stu-id="ed661-127">The /IAcceptSQLServerLicenseTerms parameter is also not written out to the configuration file and requires either a modification of the configuration file or a value to be supplied at the command prompt.</span></span> <span data-ttu-id="ed661-128">有关详细信息，请参阅 [从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="ed661-128">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="ed661-129">另外，对于通常不通过命令提示符提供值的布尔参数，值将包括在内。</span><span class="sxs-lookup"><span data-stu-id="ed661-129">In addition, a value is included for Boolean parameters where a value is usually not supplied through the command prompt.</span></span>  
  
## <a name="using-the-configuration-file-to-install-ssnoversion"></a><span data-ttu-id="ed661-130">使用配置文件安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed661-130">Using the Configuration File to Install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="ed661-131">只能在命令行安装中使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-131">You can only use the configuration file on command-line installations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed661-132">如果需要对配置文件进行更改，建议您创建一个副本并对副本进行操作。</span><span class="sxs-lookup"><span data-stu-id="ed661-132">If you need to make changes to the configuration file, we recommend that you make a copy and work with the copy.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-install-a-stand-alone-ssnoversion-instance"></a><span data-ttu-id="ed661-133">如何使用配置文件安装独立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例</span><span class="sxs-lookup"><span data-stu-id="ed661-133">How to use a configuration file to install a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance</span></span>  
  
-   <span data-ttu-id="ed661-134">通过命令提示符运行安装，然后使用 *ConfigurationFile* 参数提供 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-134">Run the installation through the command prompt and supply the ConfigurationFile.ini using the *ConfigurationFile* parameter.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-prepare-and-complete-an-image-of-a-stand-alone-ssnoversion-instance-sysprep"></a><span data-ttu-id="ed661-135">如何使用配置文件准备和完成独立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的映像 (SysPrep)</span><span class="sxs-lookup"><span data-stu-id="ed661-135">How to use a configuration file to prepare and complete an image of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (SysPrep)</span></span>  
  
1.  <span data-ttu-id="ed661-136">准备一个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并在同一计算机上配置它们。</span><span class="sxs-lookup"><span data-stu-id="ed661-136">To prepare one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and configure them on the same machine.</span></span>  
  
    -   <span data-ttu-id="ed661-137">从安装中心的“高级”页运行“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的独立实例的映像准备”，并捕获准备映像配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-137">Run **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="ed661-138">将同一个准备映像配置文件用作准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多个实例的模板。</span><span class="sxs-lookup"><span data-stu-id="ed661-138">Use the same prepare image configuration file as a template to prepare more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="ed661-139">从安装中心的“高级”页运行“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已准备独立实例的映像完成”，以便在计算机上配置准备的实例。</span><span class="sxs-lookup"><span data-stu-id="ed661-139">Run **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center to configure a prepared instances on the machine.</span></span>  
  
2.  <span data-ttu-id="ed661-140">使用 Windows SysPrep 工具准备操作系统的映像，包括未配置的、已准备的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="ed661-140">To prepare an image of the operating system including an unconfigured prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], using Windows SysPrep tool.</span></span>  
  
    -   <span data-ttu-id="ed661-141">从安装中心的“高级”页运行“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的独立实例的映像准备”，并捕获准备映像配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-141">Run the **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the Advanced page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="ed661-142">从安装中心的“高级”页运行“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已准备独立实例的映像完成”，但在捕获完全的配置文件之后，在“已准备好完成”页上取消它。</span><span class="sxs-lookup"><span data-stu-id="ed661-142">Run the **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center, but cancel it on the **Ready to Complete** page after capturing the complete configuration file.</span></span>  
  
    -   <span data-ttu-id="ed661-143">可以将完全的映像配置文件随 Windows 映像一起存储，以便自动执行已准备实例的配置。</span><span class="sxs-lookup"><span data-stu-id="ed661-143">The complete image configuration file can be stored with the Windows image for automating the configuration of the prepared instances.</span></span>  
  
#### <a name="how-to-install-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="ed661-144">如何使用配置文件安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集</span><span class="sxs-lookup"><span data-stu-id="ed661-144">How to install a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="ed661-145">“集成安装”选项（在一个节点上创建单节点故障转移群集并在其他节点上运行 AddNode）：</span><span class="sxs-lookup"><span data-stu-id="ed661-145">Integrated Install option (create a single node failover cluster on a node and for additional nodes, run AddNode on them):</span></span>  
  
    -   <span data-ttu-id="ed661-146">运行“安装故障转移群集”选项，并捕获列出所有安装设置的配置文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-146">Run the "Install a Failover Cluster" option and capture the configuration file that lists all the installation settings.</span></span>  
  
    -   <span data-ttu-id="ed661-147">通过提供 *ConfigurationFile* 配置文件参数运行命令行故障转移群集安装。</span><span class="sxs-lookup"><span data-stu-id="ed661-147">Run the command-line failover cluster install by supplying the *ConfigurationFile* parameter.</span></span>  
  
    -   <span data-ttu-id="ed661-148">在要添加的其他节点上，运行 AddNode 以捕获适用于现有故障转移群集的 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-148">On an additional node to be added, run AddNode to capture the ConfigurationFile.ini file applicable to the existing failover cluster.</span></span>  
  
    -   <span data-ttu-id="ed661-149">通过使用 ConfigurationFile 参数提供相同的配置文件，在将要加入故障转移群集的所有其他节点上运行命令行 AddNode。</span><span class="sxs-lookup"><span data-stu-id="ed661-149">Run the command-line AddNode on all the additional nodes that will join the failover cluster, by supplying the same configuration file using the ConfigurationFile parameter.</span></span>  
  
2.  <span data-ttu-id="ed661-150">高级安装选项（在所有故障转移群集节点上准备故障转移群集，接着在准备好所有节点后，在拥有共享磁盘的节点上运行完成）：</span><span class="sxs-lookup"><span data-stu-id="ed661-150">Advanced install option (prepare failover cluster on all failover cluster nodes, then, after preparing all the nodes, run complete on the node that owns the shared disk):</span></span>  
  
    -   <span data-ttu-id="ed661-151">在其中一个节点上运行 **Prepare** ，然后捕获 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-151">Run **Prepare** on one of the nodes, and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="ed661-152">在将为故障转移群集准备的所有节点上，为安装程序提供相同的 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-152">Supply the same ConfigurationFile.ini file to Setup on all the nodes that will be prepared for the failover cluster.</span></span>  
  
    -   <span data-ttu-id="ed661-153">准备好所有节点后，在拥有共享磁盘的节点上运行完成故障转移群集操作，然后捕获 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-153">After all the nodes have been prepared, run a complete failover cluster operation on the node that owns the shared disk and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="ed661-154">接着，您可以提供此 ConfigurationFile.ini 文件以完成故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="ed661-154">You can then supply this ConfigurationFile.ini file to complete the failover cluster.</span></span>  
  
#### <a name="how-to-add-or-remove-a-node-to-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="ed661-155">如何使用配置文件在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集中添加或删除节点</span><span class="sxs-lookup"><span data-stu-id="ed661-155">How to add or remove a node to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
-   <span data-ttu-id="ed661-156">如果您有以前用来在故障转移群集中添加或删除节点的配置文件，可以重复使用这个文件来添加或删除其他节点。</span><span class="sxs-lookup"><span data-stu-id="ed661-156">If you have a configuration file that was previously used to add a node to or remove a node from a failover cluster, you can reuse that same file to add or remove additional nodes.</span></span>  
  
#### <a name="how-to-upgrade-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="ed661-157">如何使用配置文件升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集</span><span class="sxs-lookup"><span data-stu-id="ed661-157">How to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="ed661-158">在被动节点上运行升级，然后捕获 ConfigurationFile.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="ed661-158">Run upgrade on the passive node and capture the ConfigurationFile.ini file.</span></span> <span data-ttu-id="ed661-159">您可以通过执行真正的升级，或者可以通过在升级过程结束时退出而不进行真正的升级来达到此目的。</span><span class="sxs-lookup"><span data-stu-id="ed661-159">You can do this either by performing the actual upgrade, or exiting at the end without doing the actual upgrade.</span></span>  
  
2.  <span data-ttu-id="ed661-160">在要升级的其他节点上，提供 ConfigurationFile.ini 文件以完成升级过程。</span><span class="sxs-lookup"><span data-stu-id="ed661-160">On all the additional nodes to be upgraded, supply the ConfigurationFile.ini file to complete the process.</span></span>  
  
## <a name="sample-syntax"></a><span data-ttu-id="ed661-161">示例语法</span><span class="sxs-lookup"><span data-stu-id="ed661-161">Sample Syntax</span></span>  
 <span data-ttu-id="ed661-162">下面提供了有关如何使用配置文件的一些示例：</span><span class="sxs-lookup"><span data-stu-id="ed661-162">Following are some examples on how to use the configuration file:</span></span>  
  
-   <span data-ttu-id="ed661-163">在命令提示符处指定配置文件：</span><span class="sxs-lookup"><span data-stu-id="ed661-163">To specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   <span data-ttu-id="ed661-164">在命令提示符处而不是配置文件中指定密码：</span><span class="sxs-lookup"><span data-stu-id="ed661-164">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed661-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed661-165">See Also</span></span>  
 <span data-ttu-id="ed661-166">[从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="ed661-166">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="ed661-167">[SQL Server 故障转移群集安装](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span><span class="sxs-lookup"><span data-stu-id="ed661-167">[SQL Server Failover Cluster Installation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span></span>  
 [<span data-ttu-id="ed661-168">升级 SQL Server 故障转移群集</span><span class="sxs-lookup"><span data-stu-id="ed661-168">Upgrade a SQL Server Failover Cluster</span></span>](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
