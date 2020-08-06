---
title: Invoke-PolicyEvaluation cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 656fdffea191c9cf6fc42d860164bc5af1e04561
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689014"
---
# <a name="invoke-policyevaluation-cmdlet"></a><span data-ttu-id="429be-102">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="429be-102">Invoke-PolicyEvaluation cmdlet</span></span>
  <span data-ttu-id="429be-103">**Invoke-PolicyEvaluation** 是一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet，它用于报告 SQL Server 对象的目标集是否符合一个或多个基于策略的管理策略中指定的条件。</span><span class="sxs-lookup"><span data-stu-id="429be-103">**Invoke-PolicyEvaluation** is a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet that reports whether a target set of SQL Server objects complies with the conditions specified in one or more Policy-Based Management policies.</span></span>  
  
## <a name="using-invoke-policyevaluation"></a><span data-ttu-id="429be-104">使用 Invoke-PolicyEvaluation</span><span class="sxs-lookup"><span data-stu-id="429be-104">Using Invoke-PolicyEvaluation</span></span>  
 <span data-ttu-id="429be-105">**Invoke-PolicyEvaluation** 针对一组 SQL Server 对象（称为目标集）评估一个或多个策略。</span><span class="sxs-lookup"><span data-stu-id="429be-105">**Invoke-PolicyEvaluation** evaluates one or more policies against a set of SQL Server objects called the target set.</span></span> <span data-ttu-id="429be-106">该组目标对象来自目标服务器。</span><span class="sxs-lookup"><span data-stu-id="429be-106">The set of target objects comes from a target server.</span></span> <span data-ttu-id="429be-107">每个策略都定义一些条件，这些条件是目标对象的允许状态。</span><span class="sxs-lookup"><span data-stu-id="429be-107">Each policy defines conditions, which are the allowed states for the target objects.</span></span> <span data-ttu-id="429be-108">例如， **Trustworthy Database** 策略规定 TRUSTWORTHY 数据库属性必须设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="429be-108">For example, the **Trustworthy Database** policy states that the TRUSTWORTHY database property must be set to OFF.</span></span>  
  
 <span data-ttu-id="429be-109">**-AdHocPolicyEvaluationMode** 参数指定所采取的操作：</span><span class="sxs-lookup"><span data-stu-id="429be-109">The **-AdHocPolicyEvaluationMode** parameter specifies the actions taken:</span></span>  
  
 <span data-ttu-id="429be-110">勾选标记</span><span class="sxs-lookup"><span data-stu-id="429be-110">Check</span></span>  
 <span data-ttu-id="429be-111">使用当前登录名的凭据报告目标对象的策略符合情况。</span><span class="sxs-lookup"><span data-stu-id="429be-111">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="429be-112">不重新配置任何对象。</span><span class="sxs-lookup"><span data-stu-id="429be-112">Do no reconfigure any objects.</span></span> <span data-ttu-id="429be-113">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="429be-113">This is the default setting.</span></span>  
  
 <span data-ttu-id="429be-114">CheckSqlScriptAsProxy</span><span class="sxs-lookup"><span data-stu-id="429be-114">CheckSqlScriptAsProxy</span></span>  
 <span data-ttu-id="429be-115">使用 **##MS_PolicyTSQLExecutionLogin##** 代理登录名的凭据，报告目标对象的策略符合情况。</span><span class="sxs-lookup"><span data-stu-id="429be-115">Report the compliance status of the target objects using the credentials of the **##MS_PolicyTSQLExecutionLogin##** proxy login.</span></span> <span data-ttu-id="429be-116">不重新配置任何对象。</span><span class="sxs-lookup"><span data-stu-id="429be-116">Do no reconfigure any objects.</span></span>  
  
 <span data-ttu-id="429be-117">配置</span><span class="sxs-lookup"><span data-stu-id="429be-117">Configure</span></span>  
 <span data-ttu-id="429be-118">使用当前登录名的凭据报告目标对象的策略符合情况。</span><span class="sxs-lookup"><span data-stu-id="429be-118">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="429be-119">重新配置不符合策略的任何可设置的选项和确定性选项。</span><span class="sxs-lookup"><span data-stu-id="429be-119">Reconfigure any settable and deterministic options that are not in compliance with the policies.</span></span>  
  
## <a name="specifying-polices"></a><span data-ttu-id="429be-120">指定策略</span><span class="sxs-lookup"><span data-stu-id="429be-120">Specifying Polices</span></span>  
 <span data-ttu-id="429be-121">您指定策略的方式取决于策略的存储位置。</span><span class="sxs-lookup"><span data-stu-id="429be-121">How you specify a policy depends on where the policy is stored.</span></span> <span data-ttu-id="429be-122">策略能够以两种格式存储：</span><span class="sxs-lookup"><span data-stu-id="429be-122">Policies can be stored in two formats:</span></span>  
  
-   <span data-ttu-id="429be-123">它们可以是存储在策略存储区中的对象，例如数据库引擎的实例。</span><span class="sxs-lookup"><span data-stu-id="429be-123">They can be objects stored in a policy store, such as an instance of the Database Engine.</span></span> <span data-ttu-id="429be-124">可以使用 SQLSERVER:\SQLPolicy 文件夹指定策略在策略存储区中的位置。</span><span class="sxs-lookup"><span data-stu-id="429be-124">You can use the SQLSERVER:\SQLPolicy folder to specify the location of policies in a policy store.</span></span> <span data-ttu-id="429be-125">可以使用 Windows PowerShell cmdlet，根据输入策略的属性对其进行筛选，例如使用 Where-Object 来根据策略类别进行筛选，或者使用 Get-Item 根据策略名称进行筛选。</span><span class="sxs-lookup"><span data-stu-id="429be-125">You can use Windows PowerShell cmdlets to filter the input polices based on their properties, such as using Where-Object to filter on the policy category or Get-Item to filter on policy name.</span></span>  
  
-   <span data-ttu-id="429be-126">它们可以导出为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="429be-126">They can be exported as XML files.</span></span> <span data-ttu-id="429be-127">可以使用文件系统驱动器（如 D:）指定 XML 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="429be-127">You can use a file system drive, such as D:, to specify the location of the XML files.</span></span> <span data-ttu-id="429be-128">可以使用 Windows PowerShell cmdlet（如 Where-Object），根据策略的文件属性（如文件名）对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="429be-128">You can use Windows PowerShell cmdlets such as Where-Object to filter the policies on their file properties, such as file name.</span></span>  
  
 <span data-ttu-id="429be-129">如果策略存储在策略存储区中，则必须传递一组指向要评估的策略的 PSObject。</span><span class="sxs-lookup"><span data-stu-id="429be-129">If the policies are stored in a policy store, you must pass in a set of PSObjects pointing to the policies to be evaluated.</span></span> <span data-ttu-id="429be-130">通常可以通过将 cmdlet（如 Get-Item）的输出用管道命令发送到 **Invoke-PolicyEvaluation**来完成此操作，并且不需要你指定 **-Policy** 参数。</span><span class="sxs-lookup"><span data-stu-id="429be-130">This is typically done by piping the output of a cmdlet such as Get-Item to **Invoke-PolicyEvaluation**, and does not require that you specify the **-Policy** parameter.</span></span> <span data-ttu-id="429be-131">例如，如果已将 Microsoft 最佳实践策略导入到数据库引擎的实例中，则此命令可评估 **数据库状态** 策略：</span><span class="sxs-lookup"><span data-stu-id="429be-131">For example, if you have imported the Microsoft Best Practices policies into your instance of the database engine, this command evaluates the **Database Status** policy:</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="429be-132">此示例显示如何使用 Where-Object 根据策略的 **PolicyCategory** 属性筛选策略存储区中的多个策略。</span><span class="sxs-lookup"><span data-stu-id="429be-132">This example shows using Where-Object to filter multiple policies from a policy store based on their **PolicyCategory** property.</span></span> <span data-ttu-id="429be-133">**Where-Object** 的管道输出中的对象由 **Invoke-PolicyEvaluation**使用。</span><span class="sxs-lookup"><span data-stu-id="429be-133">The objects from the piped output of **Where-Object** is consumed by **Invoke-PolicyEvaluation**.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 <span data-ttu-id="429be-134">如果这些策略存储为 XML 文件，则必须使用 **-Policy** 参数为每个策略提供路径和名称。</span><span class="sxs-lookup"><span data-stu-id="429be-134">If the policies are stored as XML files, you must use the **-Policy** parameter to supply both the path and name for each policy.</span></span> <span data-ttu-id="429be-135">如果在 **-Policy** 参数中未指定路径，那么 **Invoke-PolicyEvaulation** 将使用 **sqlps** 路径的当前设置。</span><span class="sxs-lookup"><span data-stu-id="429be-135">If you do not specify a path in the **-Policy** parameter, **Invoke-PolicyEvaulation** uses the current setting of the **sqlps** path.</span></span> <span data-ttu-id="429be-136">例如，此命令根据您登录名的默认数据库评估随 SQL Server 安装的一个 Microsoft 最佳实践策略：</span><span class="sxs-lookup"><span data-stu-id="429be-136">For example, this command evaluates one of the Microsoft Best Practice policies installed with SQL Server against the default database for your login:</span></span>  
  
```powershell
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="429be-137">此命令执行同样的操作，唯一不同的是它使用当前 **sqlps** 路径来指定策略 XML 文件的位置：</span><span class="sxs-lookup"><span data-stu-id="429be-137">This command does the same thing, only it uses the current **sqlps** path to establish the location of the policy XML file:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="429be-138">此示例显示如何使用 **Get-ChildItem** cmdlet 检索多个策略 XML 文件，并将这些对象用管道命令发送到 **Invoke-PolicyEvaluation**：</span><span class="sxs-lookup"><span data-stu-id="429be-138">This example shows using the **Get-ChildItem** cmdlet to retrieve multiple policy XML files and pipe the objects into **Invoke-PolicyEvaluation**:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a><span data-ttu-id="429be-139">指定目标集</span><span class="sxs-lookup"><span data-stu-id="429be-139">Specifying the Target Set</span></span>  
 <span data-ttu-id="429be-140">使用三个参数指定目标对象集：</span><span class="sxs-lookup"><span data-stu-id="429be-140">Use three parameters to specify the set of target objects:</span></span>  
  
-   <span data-ttu-id="429be-141">**-TargetServerName** 指定包含目标对象的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="429be-141">**-TargetServerName** specifies the instance of SQL Server containing the target objects.</span></span> <span data-ttu-id="429be-142">可在一个字符串中指定这些信息，该字符串应使用为 <xref:System.Data.SqlClient.SqlConnection> 类的 ConnectionString 属性定义的格式。</span><span class="sxs-lookup"><span data-stu-id="429be-142">You can specify the information in a string that uses the format defined for the ConnectionString property of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="429be-143">可以使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 类来生成格式正确的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="429be-143">You can use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to build a correctly formatted connection string.</span></span> <span data-ttu-id="429be-144">还可以创建 <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> 对象并将其传递到 **-TargetServer**使用。</span><span class="sxs-lookup"><span data-stu-id="429be-144">You can also create a <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> object and pass it to **-TargetServer**.</span></span> <span data-ttu-id="429be-145">如果提供只有服务器名称的字符串， **Invoke-PolicyEvaluation** 会使用 Windows 身份验证来连接服务器。</span><span class="sxs-lookup"><span data-stu-id="429be-145">If you supply a string that has only the name of the server, **Invoke-PolicyEvaluation** uses Windows Authentication to connect to the server.</span></span>  
  
-   <span data-ttu-id="429be-146">**-TargetObjects** 的取值为一个对象或对象数组，它们表示目标集中的 SQL Server 对象。</span><span class="sxs-lookup"><span data-stu-id="429be-146">**-TargetObjects** takes an object or array of objects that represent the SQL Server objects in the target set.</span></span> <span data-ttu-id="429be-147">例如，你可以创建 <xref:Microsoft.SqlServer.Management.Smo.Database> 类对象数组，并将其传递到 **-TargetObjects**使用。</span><span class="sxs-lookup"><span data-stu-id="429be-147">For example, you could create an array of <xref:Microsoft.SqlServer.Management.Smo.Database> class objects to pass in to **-TargetObjects**.</span></span>  
  
-   <span data-ttu-id="429be-148">**-TargetExpressions** 的取值为一个字符串，其中包含一个指定目标集中对象的查询表达式。</span><span class="sxs-lookup"><span data-stu-id="429be-148">**-TargetExpressions** takes a string containing a query expression that specifies the objects in the target set.</span></span> <span data-ttu-id="429be-149">查询表达式的格式是以“/”字符隔开的节点。</span><span class="sxs-lookup"><span data-stu-id="429be-149">The query expression is in the form of nodes separated by the '/' character.</span></span> <span data-ttu-id="429be-150">每个节点的格式为 ObjectType[Filter]。</span><span class="sxs-lookup"><span data-stu-id="429be-150">Each node is in the form ObjectType[Filter].</span></span> <span data-ttu-id="429be-151">对象类型是 SQL Server 管理对象中的对象之一 (SMO) 对象层次结构。</span><span class="sxs-lookup"><span data-stu-id="429be-151">Object type is one of the objects in a SQL Server Management Object (SMO) object hierarchy.</span></span> <span data-ttu-id="429be-152">Filter 是一个用于筛选该节点的对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="429be-152">Filter is an expression that filters for objects at that node.</span></span> <span data-ttu-id="429be-153">有关详细信息，请参阅 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)。</span><span class="sxs-lookup"><span data-stu-id="429be-153">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
 <span data-ttu-id="429be-154">指定 **-TargetObjects** 或 **-TargetExpression**，而不是两者。</span><span class="sxs-lookup"><span data-stu-id="429be-154">Specify either **-TargetObjects** or **-TargetExpression**, not both.</span></span>  
  
 <span data-ttu-id="429be-155">此示例使用 Sfc.SqlStoreConnection 对象指定目标服务器：</span><span class="sxs-lookup"><span data-stu-id="429be-155">This example uses an Sfc.SqlStoreConnection object to specify the target server:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 <span data-ttu-id="429be-156">此示例使用 **-TargetExpression** 标识要评估的特定数据库：</span><span class="sxs-lookup"><span data-stu-id="429be-156">This example uses **-TargetExpression** to identify the specific database to evaluate:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a><span data-ttu-id="429be-157">评估 Analysis Services 策略</span><span class="sxs-lookup"><span data-stu-id="429be-157">Evaluating Analysis Services Policies</span></span>  
 <span data-ttu-id="429be-158">若要针对 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例评估策略，必须在 PowerShell 中加载和注册程序集，使用 Analysis Services 连接对象创建变量，并将该变量传递到 **-TargetObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="429be-158">To evaluate policies against an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you must load and register an assembly into PowerShell, create a variable with an Analysis Services connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="429be-159">此示例显示如何评估 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的最佳实践外围应用配置器策略。</span><span class="sxs-lookup"><span data-stu-id="429be-159">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = New-Object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a><span data-ttu-id="429be-160">评估 Reporting Services 策略</span><span class="sxs-lookup"><span data-stu-id="429be-160">Evaluating Reporting Services Policies</span></span>  
 <span data-ttu-id="429be-161">若要评估 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 策略，必须在 PowerShell 中加载和注册程序集，使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 连接对象创建变量，并将该变量传递到 **-TargetObject** 参数中。</span><span class="sxs-lookup"><span data-stu-id="429be-161">To evaluate [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] policies, you must load and register an assembly into PowerShell, create a variable with a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="429be-162">此示例显示如何评估 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]的最佳实践外围应用配置器策略。</span><span class="sxs-lookup"><span data-stu-id="429be-162">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a><span data-ttu-id="429be-163">设置输出的格式</span><span class="sxs-lookup"><span data-stu-id="429be-163">Formatting Output</span></span>  
 <span data-ttu-id="429be-164">默认情况下， **Invoke-PolicyEvaluation** 的输出通过简明报告形式，以可读格式显示在命令提示符窗口中。</span><span class="sxs-lookup"><span data-stu-id="429be-164">By default, the output of **Invoke-PolicyEvaluation** is displayed in the command prompt window as a concise report in human-readable format.</span></span> <span data-ttu-id="429be-165">可以使用 **-OutputXML** 参数来指定 cmdlet，而不是以 XML 文件形式生成详细报告。</span><span class="sxs-lookup"><span data-stu-id="429be-165">You can use the **-OutputXML** parameter to specify that the cmdlet instead produce a detailed report as an XML file.</span></span> <span data-ttu-id="429be-166">**Invoke-PolicyEvaluation** 使用系统建模语言交换格式 (SML-IF) 架构，因此 SML-IF 读取器可以读取该文件。</span><span class="sxs-lookup"><span data-stu-id="429be-166">**Invoke-PolicyEvaluation** uses the Systems Modeling Language Interchange Format (SML-IF) schema so the file can be read by SML-IF readers.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a><span data-ttu-id="429be-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="429be-167">See Also</span></span>  
 [<span data-ttu-id="429be-168">使用数据库引擎 cmdlet</span><span class="sxs-lookup"><span data-stu-id="429be-168">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
