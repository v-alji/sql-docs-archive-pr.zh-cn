---
title: 在 SMO 中配置 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6da1bca0aec650c01553b42bc2f3628b0bf7282e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692837"
---
# <a name="configuring-sql-server-in-smo"></a><span data-ttu-id="8a39d-102">在 SMO 中配置 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a39d-102">Configuring SQL Server in SMO</span></span>
  <span data-ttu-id="8a39d-103">在 SMO 中， <xref:Microsoft.SqlServer.Management.Smo.Information> 对象、 <xref:Microsoft.SqlServer.Management.Smo.Settings> 对象、对象 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 和对象都 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 包含实例的设置和信息 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-103">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Information> object, the <xref:Microsoft.SqlServer.Management.Smo.Settings> object, the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object, and the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object contain settings and information for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8a39d-104">具有许多描述已安装的实例的行为的属性。</span><span class="sxs-lookup"><span data-stu-id="8a39d-104">has numerous properties that describe the behavior of the installed instance.</span></span> <span data-ttu-id="8a39d-105">这些属性描述了启动选项、服务器默认值、文件和目录、系统和处理器信息、产品和版本、连接信息、内存选项、语言和排序规则选择以及身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="8a39d-105">The properties describe the startup options, the server defaults, files and directories, system and processor information, product and versions, connection information, memory options, language and collation selections, and the authentication mode.</span></span>  
  
## <a name="sql-server-configuration"></a><span data-ttu-id="8a39d-106">SQL Server 配置</span><span class="sxs-lookup"><span data-stu-id="8a39d-106">SQL Server Configuration</span></span>  
 <span data-ttu-id="8a39d-107"><xref:Microsoft.SqlServer.Management.Smo.Information> 对象属性包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的相关信息，例如处理器和平台。</span><span class="sxs-lookup"><span data-stu-id="8a39d-107">The <xref:Microsoft.SqlServer.Management.Smo.Information> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], such as processor and platform.</span></span>  
  
 <span data-ttu-id="8a39d-108"><xref:Microsoft.SqlServer.Management.Smo.Settings> 对象属性包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8a39d-108">The <xref:Microsoft.SqlServer.Management.Smo.Settings> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a39d-109">除邮件配置文件和服务器帐户之外，还可以修改默认的数据库文件和目录。</span><span class="sxs-lookup"><span data-stu-id="8a39d-109">The default database file and directory can be modified in addition to the Mail Profile and the Server Account.</span></span> <span data-ttu-id="8a39d-110">这些属性在连接持续时间内一直保留。</span><span class="sxs-lookup"><span data-stu-id="8a39d-110">These properties remain for the duration of the connection.</span></span>  
  
 <span data-ttu-id="8a39d-111"><xref:Microsoft.SqlServer.Management.Smo.UserOptions> 对象属性包含与算术、ANSI 标准和事务相关的当前连接行为的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8a39d-111">The <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object properties contain information about the current connections behavior relating to arithmetic, ANSI standards, and transactions.</span></span>  
  
 <span data-ttu-id="8a39d-112">还存在由 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 对象表示的一组配置选项。</span><span class="sxs-lookup"><span data-stu-id="8a39d-112">There is also a set of configuration options that is represented by the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object.</span></span> <span data-ttu-id="8a39d-113">它包含表示可通过 `sp_configure` 存储过程进行修改的选项的一组属性。</span><span class="sxs-lookup"><span data-stu-id="8a39d-113">It contains a set of properties that represent the options that can be modified by the `sp_configure` stored procedure.</span></span> <span data-ttu-id="8a39d-114">"**优先级提升**"、"**恢复间隔**" 和 "**网络数据包大小**" 等选项控制实例的性能 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-114">Options such as **Priority Boost**, **Recovery Interval** and **Network Packet Size**control the performance of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a39d-115">其中的许多选项可以进行动态更改，但在某些情况下，其值需要先配置，在重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例后才发生更改。</span><span class="sxs-lookup"><span data-stu-id="8a39d-115">Many of these options can be changed dynamically, but in some cases the value is first configured and then changed when the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="8a39d-116">每个配置选项都对应一个 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 对象属性。</span><span class="sxs-lookup"><span data-stu-id="8a39d-116">There is a <xref:Microsoft.SqlServer.Management.Smo.Configuration> object property for every configuration option.</span></span> <span data-ttu-id="8a39d-117">使用 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 对象，可以修改全局配置设置。</span><span class="sxs-lookup"><span data-stu-id="8a39d-117">Using the <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> object you can modify the global configuration setting.</span></span> <span data-ttu-id="8a39d-118">许多属性都有最大值和最小值，这些值也存储为 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 属性。</span><span class="sxs-lookup"><span data-stu-id="8a39d-118">Many properties have maximum and minimum values that are also stored as <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> properties.</span></span> <span data-ttu-id="8a39d-119">这些属性要求 <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> 方法将更改提交到的实例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-119">These properties require the <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> method to commit the change to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8a39d-120"><xref:Microsoft.SqlServer.Management.Smo.Configuration> 对象中的所有配置选项都必须由系统管理员进行更改。</span><span class="sxs-lookup"><span data-stu-id="8a39d-120">All of the configuration options in the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object must be changed by the system administrator.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8a39d-121">示例</span><span class="sxs-lookup"><span data-stu-id="8a39d-121">Examples</span></span>  
 <span data-ttu-id="8a39d-122">对于下列代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a39d-122">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="8a39d-123">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="8a39d-123">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a><span data-ttu-id="8a39d-124">在 Visual Basic 中修改 SQL Server 配置选项</span><span class="sxs-lookup"><span data-stu-id="8a39d-124">Modifying SQL Server Configuration Options in Visual Basic</span></span>  
 <span data-ttu-id="8a39d-125">此代码示例说明如何在 Visual Basic .NET 中更新配置选项。</span><span class="sxs-lookup"><span data-stu-id="8a39d-125">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="8a39d-126">它还检索并显示指定配置选项的最大值和最小值的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8a39d-126">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="8a39d-127">最后，程序会通知用户是否已进行了动态更改，或者是否存储了更改直到重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例后再予以应用。</span><span class="sxs-lookup"><span data-stu-id="8a39d-127">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a><span data-ttu-id="8a39d-128">在 Visual Basic 中修改 SQL Server 设置</span><span class="sxs-lookup"><span data-stu-id="8a39d-128">Modifying SQL Server Settings in Visual Basic</span></span>  
 <span data-ttu-id="8a39d-129">此代码示例显示有关和中的实例的信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> ，并 <xref:Microsoft.SqlServer.Management.Smo.Settings> 修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和对象属性中的设置 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-129">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="8a39d-130">在此示例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 对象和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 对象都有一个 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-130">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="8a39d-131">您可以分别运行这两个对象的 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-131">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a><span data-ttu-id="8a39d-132">在 Visual C# 中修改 SQL Server 设置</span><span class="sxs-lookup"><span data-stu-id="8a39d-132">Modifying SQL Server Settings in Visual C#</span></span>  
 <span data-ttu-id="8a39d-133">此代码示例显示有关和中的实例的信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> ，并 <xref:Microsoft.SqlServer.Management.Smo.Settings> 修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和对象属性中的设置 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-133">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="8a39d-134">在此示例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 对象和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 对象都有一个 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-134">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="8a39d-135">您可以分别运行这两个对象的 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-135">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a><span data-ttu-id="8a39d-136">在 PowerShell 中修改 SQL Server 设置</span><span class="sxs-lookup"><span data-stu-id="8a39d-136">Modifying SQL Server Settings in PowerShell</span></span>  
 <span data-ttu-id="8a39d-137">此代码示例显示有关和中的实例的信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> ，并 <xref:Microsoft.SqlServer.Management.Smo.Settings> 修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和对象属性中的设置 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8a39d-137">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="8a39d-138">在此示例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 对象和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 对象都有一个 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-138">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="8a39d-139">您可以分别运行这两个对象的 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8a39d-139">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a><span data-ttu-id="8a39d-140">在 PowerShell 中修改 SQL Server 配置选项</span><span class="sxs-lookup"><span data-stu-id="8a39d-140">Modifying SQL Server Configuration Options in PowerShell</span></span>  
 <span data-ttu-id="8a39d-141">此代码示例说明如何在 Visual Basic .NET 中更新配置选项。</span><span class="sxs-lookup"><span data-stu-id="8a39d-141">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="8a39d-142">它还检索并显示指定配置选项的最大值和最小值的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8a39d-142">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="8a39d-143">最后，程序会通知用户是否已进行了动态更改，或者是否存储了更改直到重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例后再予以应用。</span><span class="sxs-lookup"><span data-stu-id="8a39d-143">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = Get-Item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {
   "Configuration option has been updated."  
 }  
Else  
 {  
    "Configuration option will be updated when SQL Server is restarted."  
 }  
```  
