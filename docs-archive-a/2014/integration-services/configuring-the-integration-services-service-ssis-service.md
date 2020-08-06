---
title: " (SSIS 服务配置 Integration Services 服务) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70c41377a2c302e1a021c6ade2a9d487579fa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692489"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a><span data-ttu-id="3f23d-102">配置 Integration Services 服务（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="3f23d-102">Configuring the Integration Services Service (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="3f23d-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="3f23d-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] <span data-ttu-id="3f23d-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="3f23d-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3f23d-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="3f23d-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="3f23d-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务使用某个配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="3f23d-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service relies on a configuration file for its settings.</span></span> <span data-ttu-id="3f23d-107">默认情况下，此配置文件的名称为 MsDtsSrvr.ini.xml，该文件位于%ProgramFiles%\Microsoft SQL Server\120\dts\binn。文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3f23d-107">By default, the name for this configuration file is MsDtsSrvr.ini.xml, and the file is located in the folder, %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.</span></span>  
  
 <span data-ttu-id="3f23d-108">通常，您不必对此配置文件进行任何更改，也不必更改文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="3f23d-108">Typically, you do not have to make any changes to this configuration file, nor do you have to change the file's default location.</span></span> <span data-ttu-id="3f23d-109">但是，如果包存储在 [!INCLUDE[ssDE](../includes/ssde-md.md)]的某个命名实例或远程实例中，或存储在 [!INCLUDE[ssDE](../includes/ssde-md.md)]的多个实例中，则必须修改该配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f23d-109">However, you will have to modify the configuration file if your packages are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)], or in multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="3f23d-110">此外，如果您将配置文件移到默认位置之外的位置，则必须修改指定该文件位置的注册表项。</span><span class="sxs-lookup"><span data-stu-id="3f23d-110">Also, if you move the configuration file to a location other than the default location, you will have to modify the Registry key that specifies the file location.</span></span>  
  
## <a name="configuration-file-contents"></a><span data-ttu-id="3f23d-111">配置文件内容</span><span class="sxs-lookup"><span data-stu-id="3f23d-111">Configuration File Contents</span></span>  
 <span data-ttu-id="3f23d-112">安装 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]时，安装过程会创建并安装 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f23d-112">When you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the setup process creates and installs the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="3f23d-113">此配置文件包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="3f23d-113">This configuration file contains the following settings:</span></span>  
  
-   <span data-ttu-id="3f23d-114">服务停止时将向包发送停止命令。</span><span class="sxs-lookup"><span data-stu-id="3f23d-114">Packages are sent a stop command when the service stops.</span></span>  
  
-   <span data-ttu-id="3f23d-115">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的对象资源管理器中为 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 显示的根文件夹是 MSDB 和“文件系统”文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f23d-115">The root folders to display for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in Object Explorer of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] are the MSDB and File System folders.</span></span>  
  
-   <span data-ttu-id="3f23d-116">服务所管理的文件系统中的包 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 位于%PROGRAMFILES%\MICROSOFT SQL Server\120\DTS\Packages. 中。</span><span class="sxs-lookup"><span data-stu-id="3f23d-116">The packages in the file system that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages are located in %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.</span></span>  
  
 <span data-ttu-id="3f23d-117">此配置文件还指定哪个 msdb 数据库包含将由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务管理的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-117">This configuration file also specifies which msdb database contains the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service will manage.</span></span> <span data-ttu-id="3f23d-118">默认情况下， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务配置为管理 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例的 msdb 数据库中的包，该实例与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]同时安装。</span><span class="sxs-lookup"><span data-stu-id="3f23d-118">By default, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3f23d-119">如果未同时安装 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例，则 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务可配置为管理本地默认 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例的 msdb 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-119">If an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
### <a name="default-configuration-file-example"></a><span data-ttu-id="3f23d-120">默认配置文件示例</span><span class="sxs-lookup"><span data-stu-id="3f23d-120">Default Configuration File Example</span></span>  
 <span data-ttu-id="3f23d-121">下面的示例显示了指定以下设置的默认配置文件：</span><span class="sxs-lookup"><span data-stu-id="3f23d-121">The following example shows a default configuration file that specifies the following settings:</span></span>  
  
-   <span data-ttu-id="3f23d-122">当 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务停止时包停止运行。</span><span class="sxs-lookup"><span data-stu-id="3f23d-122">Packages stop running when the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service stops.</span></span>  
  
-   <span data-ttu-id="3f23d-123">包存储的根文件夹在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中为 MSDB 和“文件系统”。</span><span class="sxs-lookup"><span data-stu-id="3f23d-123">The root folders for package storage in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are MSDB and File System.</span></span>  
  
-   <span data-ttu-id="3f23d-124">该服务管理存储在本地默认 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的 msdb 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-124">The service manages packages that are stored in the msdb database of the local, default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3f23d-125">该服务管理存储在文件系统的“包”文件夹中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-125">The service manages packages that are stored in the file system in the Packages folder.</span></span>  
  
 <span data-ttu-id="3f23d-126">**默认配置文件示例**</span><span class="sxs-lookup"><span data-stu-id="3f23d-126">**Example of a Default Configuration File**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a><span data-ttu-id="3f23d-127">配置文件的修改</span><span class="sxs-lookup"><span data-stu-id="3f23d-127">Modification of the Configuration File</span></span>  
 <span data-ttu-id="3f23d-128">可以通过修改配置文件来达到以下目的：允许包在服务停止时继续运行；在对象资源管理器中显示其他根文件夹；或者指定文件系统中的一个不同文件夹或其他文件夹由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务进行管理。</span><span class="sxs-lookup"><span data-stu-id="3f23d-128">You can modify the configuration file to allow packages to continue running if the service stops, to display additional root folders in Object Explorer, or to specify a different folder or additional folders in the file system to be managed by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="3f23d-129">例如，可以创建 `SqlServerFolder` 类型的其他根文件夹来管理其他[!INCLUDE[ssDE](../includes/ssde-md.md)]实例的 msdb 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-129">For example, you can create additional root folders of type, `SqlServerFolder`, to manage packages in the msdb databases of additional instances of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f23d-130">某些字符在文件夹名称中无效。</span><span class="sxs-lookup"><span data-stu-id="3f23d-130">Some characters are not valid in folder names.</span></span> <span data-ttu-id="3f23d-131">文件夹名称的有效字符由 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 类 **System.IO.Path** 和 **GetInvalidFilenameChars** 字段决定。</span><span class="sxs-lookup"><span data-stu-id="3f23d-131">Valid characters for folder names are determined by the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] class **System.IO.Path** and the **GetInvalidFilenameChars** field.</span></span> <span data-ttu-id="3f23d-132">**GetInvalidFilenameChars** 字段提供了不能在传递给 **Path** 类成员的路径字符串参数中指定的特定于平台的字符数组。</span><span class="sxs-lookup"><span data-stu-id="3f23d-132">The **GetInvalidFilenameChars** field provides a platform-specific array of characters that cannot be specified in path string arguments passed to members of the **Path** class.</span></span> <span data-ttu-id="3f23d-133">无效的字符集会因文件系统的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="3f23d-133">The set of invalid characters can vary by file system.</span></span> <span data-ttu-id="3f23d-134">通常，无效字符为引号 (")、小于号 (<) 字符和竖线 (|) 字符。</span><span class="sxs-lookup"><span data-stu-id="3f23d-134">Typically, invalid characters are the quotation mark ("), less than (<) character, and pipe (|) character.</span></span>  
  
 <span data-ttu-id="3f23d-135">但是，您必须修改配置文件，才能管理存储在 [!INCLUDE[ssDE](../includes/ssde-md.md)]的某个命名实例或远程实例中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-135">However, you will have to modify the configuration file to manage packages that are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="3f23d-136">如果不更新配置文件，则无法在 **中使用** 对象资源管理器 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 来查看存储在该命名实例或远程实例的 msdb 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="3f23d-136">If you do not update the configuration file, you cannot use **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view packages that are stored in the msdb database on the named instance or the remote instance.</span></span> <span data-ttu-id="3f23d-137">如果尝试使用 **对象资源管理器** 查看这些包，将收到以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="3f23d-137">If you try to use **Object Explorer** to view these packages, you receive the following error message:</span></span>  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 <span data-ttu-id="3f23d-138">若要修改 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的配置文件，可使用文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="3f23d-138">To modify the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, you use a text editor.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f23d-139">修改了服务配置文件后，必须重新启动该服务才能使用更新后的服务配置。</span><span class="sxs-lookup"><span data-stu-id="3f23d-139">After you modify the service configuration file, you must restart the service to use the updated service configuration.</span></span>  
  
### <a name="modified-configuration-file-example"></a><span data-ttu-id="3f23d-140">经过修改的配置文件示例</span><span class="sxs-lookup"><span data-stu-id="3f23d-140">Modified Configuration File Example</span></span>  
 <span data-ttu-id="3f23d-141">下面的示例显示了经过修改的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f23d-141">The following example shows a modified configuration file for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3f23d-142">此文件用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 命名实例 `InstanceName` ，该实例在 `ServerName`服务器上。</span><span class="sxs-lookup"><span data-stu-id="3f23d-142">This file is for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] called `InstanceName` on a server named `ServerName`.</span></span>  
  
 <span data-ttu-id="3f23d-143">**经过修改的 SQL Server 命名实例配置文件的示例**</span><span class="sxs-lookup"><span data-stu-id="3f23d-143">**Example of a Modified Configuration File for a Named Instance of SQL Server**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a><span data-ttu-id="3f23d-144">配置文件位置的修改</span><span class="sxs-lookup"><span data-stu-id="3f23d-144">Modification of the Configuration File Location</span></span>  
<span data-ttu-id="3f23d-145">注册表 HKEY_LOCAL_MACHINE 项**\SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\ServiceConfigFile**指定了服务使用的配置文件的位置和名称 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f23d-145">The Registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** specifies the location and name for the configuration file that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses.</span></span> <span data-ttu-id="3f23d-146">注册表项的默认值是**C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**。</span><span class="sxs-lookup"><span data-stu-id="3f23d-146">The default value of the Registry key is **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**.</span></span> <span data-ttu-id="3f23d-147">可以更新该注册表项的值，以使配置文件使用其他名称和位置。</span><span class="sxs-lookup"><span data-stu-id="3f23d-147">You can update the value of the Registry key to use a different name and location for the configuration file.</span></span> <span data-ttu-id="3f23d-148">请注意，对于 SQL Server) ，路径中的版本号 (120 [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 将有所不同，具体取决于 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="3f23d-148">Note that the version number in the path (120 for SQL Server  [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) will vary depending on the SQL Server version.</span></span> 
  
  
> [!CAUTION]  
>  <span data-ttu-id="3f23d-149">如果注册表编辑不当，可能会导致严重问题并需要重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="3f23d-149">Incorrectly editing the Registry can cause serious problems that may require you to reinstall your operating system.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="3f23d-150">不能保证可以解决因注册表编辑不当而导致的问题。</span><span class="sxs-lookup"><span data-stu-id="3f23d-150">cannot guarantee that problems resulting from editing the Registry incorrectly can be resolved.</span></span> <span data-ttu-id="3f23d-151">编辑注册表之前，请备份所有重要数据。</span><span class="sxs-lookup"><span data-stu-id="3f23d-151">Before editing the Registry, back up any valuable data.</span></span> <span data-ttu-id="3f23d-152">有关如何备份、还原和编辑注册表的信息，请参阅 [!INCLUDE[msCoName](../includes/msconame-md.md)] 知识库文章 [Microsoft Windows 注册表说明](https://support.microsoft.com/kb/256986)。</span><span class="sxs-lookup"><span data-stu-id="3f23d-152">For information about how to back up, restore, and edit the Registry, see the [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base article, [Description of the Microsoft Windows registry](https://support.microsoft.com/kb/256986).</span></span>  
  
 <span data-ttu-id="3f23d-153">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务在启动时加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f23d-153">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service loads the configuration file when the service is started.</span></span> <span data-ttu-id="3f23d-154">对注册表项进行任何更改都需要重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="3f23d-154">Any changes to the Registry entry require that the service be restarted.</span></span>  
  
  
