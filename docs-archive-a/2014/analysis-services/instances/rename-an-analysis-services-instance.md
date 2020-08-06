---
title: 重命名 Analysis Services 实例 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 763986d82dda7424f2187daf401424fd256ddd64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690199"
---
# <a name="rename-an-analysis-services-instance"></a><span data-ttu-id="1f205-102">重命名 Analysis Services 实例</span><span class="sxs-lookup"><span data-stu-id="1f205-102">Rename an Analysis Services Instance</span></span>
  <span data-ttu-id="1f205-103">您可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用 "**重命名实例**" 对话框重命名现有的实例。</span><span class="sxs-lookup"><span data-stu-id="1f205-103">You can rename an existing instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using the **Rename Instance** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f205-104">重命名该实例时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例重命名工具将以提升的权限运行，更新与该实例关联的 Windows 服务名称、安全帐户和注册表项。</span><span class="sxs-lookup"><span data-stu-id="1f205-104">While renaming the instance, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool runs under elevated privileges, updating the Windows service name, security accounts, and registry entries associated with that instance.</span></span> <span data-ttu-id="1f205-105">为确保执行这些操作，请务必以本地系统管理员身份运行此工具。</span><span class="sxs-lookup"><span data-stu-id="1f205-105">To ensure that these actions are performed, be sure to run this tool as a local system administrator.</span></span>  
  
 <span data-ttu-id="1f205-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例重命名工具不会修改为原始实例创建的程序文件夹。</span><span class="sxs-lookup"><span data-stu-id="1f205-106">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool does not modify the program folder that was created for the original instance.</span></span> <span data-ttu-id="1f205-107">请不要修改该程序文件夹名称以便与要重命名的实例匹配。</span><span class="sxs-lookup"><span data-stu-id="1f205-107">Do not modify the program folder name to match the instance you are renaming.</span></span> <span data-ttu-id="1f205-108">更改程序文件夹名称会妨碍安装程序修复或卸载安装软件。</span><span class="sxs-lookup"><span data-stu-id="1f205-108">Changing a program folder name can prevent Setup from repairing or uninstalling the installation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f205-109">群集环境中不支持 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例重命名工具。</span><span class="sxs-lookup"><span data-stu-id="1f205-109">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool is not supported for use in a cluster environment.</span></span>  
  
### <a name="to-rename-an-instance-of-analysis-services"></a><span data-ttu-id="1f205-110">重命名 Analysis Services 的实例</span><span class="sxs-lookup"><span data-stu-id="1f205-110">To rename an instance of Analysis Services</span></span>  
  
1.  <span data-ttu-id="1f205-111">从 C:\Program Files\Microsoft SQL Server\110\tools\binn\managementstudio 启动**实例重命名**工具**asinstancerename.exe**</span><span class="sxs-lookup"><span data-stu-id="1f205-111">Launch the **Instance Rename** tool, **asinstancerename.exe**, from C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.</span></span>  
  
2.  <span data-ttu-id="1f205-112">在 **“重命名实例”** 对话框中，从 **“要重命名的实例”** 列表中选择要重命名的实例。</span><span class="sxs-lookup"><span data-stu-id="1f205-112">In the **Rename Instance** dialog box, in the **Instance to rename** list, select the instance that you want to rename.</span></span>  
  
3.  <span data-ttu-id="1f205-113">在 **“新实例名”** 框中，输入实例的新名称。</span><span class="sxs-lookup"><span data-stu-id="1f205-113">In the **New instance name** box, enter the new name for the instance.</span></span>  
  
4.  <span data-ttu-id="1f205-114">验证用户名和密码是否正确，然后单击 **“重命名”**。</span><span class="sxs-lookup"><span data-stu-id="1f205-114">Verify that the user name and password are correct, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="1f205-115">在名称更改过程中，Analysis Services 实例将会停止并重新启动。</span><span class="sxs-lookup"><span data-stu-id="1f205-115">The Analysis Services instance will be stopped and restarted as part of the name change.</span></span>  
  
### <a name="post-rename-checklist"></a><span data-ttu-id="1f205-116">重命名之后的核对清单</span><span class="sxs-lookup"><span data-stu-id="1f205-116">Post-rename checklist</span></span>  
  
1.  <span data-ttu-id="1f205-117">若要恢复对重命名的实例上运行的数据库的访问，您将需要在 Excel 或其他客户端应用程序中手动更新数据连接。</span><span class="sxs-lookup"><span data-stu-id="1f205-117">To resume access to databases that are running on the renamed instance, you will need to manually update the data connections in Excel or other client applications.</span></span> <span data-ttu-id="1f205-118">还需要检查所有预定义的连接，如可能引用您刚重命名的实例的 Reporting Services 共享数据源、Excel ODC 文件或 BI 语义模型连接文件。</span><span class="sxs-lookup"><span data-stu-id="1f205-118">Also check any predefined connections, such as Reporting Services shared data sources, Excel ODC files, or BI Semantic Model connection files that might reference the instance you just renamed.</span></span> <span data-ttu-id="1f205-119">有关详细信息，请参阅 [连接到 Analysis Services](connect-to-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1f205-119">For more information, see [Connect to Analysis Services](connect-to-analysis-services.md).</span></span>  
  
2.  <span data-ttu-id="1f205-120">更新定期用于备份、同步或处理数据库的 PowerShell 脚本或 AMO 脚本。</span><span class="sxs-lookup"><span data-stu-id="1f205-120">Update PowerShell scripts or AMO scripts that you routinely use to backup, synchronize, or process databases.</span></span>  
  
3.  <span data-ttu-id="1f205-121">更新在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中使用的 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]项目的项目属性。</span><span class="sxs-lookup"><span data-stu-id="1f205-121">Update project properties for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects that you work with in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="1f205-122">对于表格模式服务器实例，务必要更新 model.bim 文件中的 Workspace Server 属性以及项目的 Server 属性。</span><span class="sxs-lookup"><span data-stu-id="1f205-122">For tabular mode server instances, be sure to update the Workspace Server property on the model.bim file, as well as the Server property on the project.</span></span>  
  
4.  <span data-ttu-id="1f205-123">根据您指定服务帐户的方式，您可能需要更新授予对服务的数据访问权限的数据库登录名或文件权限（例如，如果您使用服务帐户来处理数据或访问其他服务器上的链接对象）。</span><span class="sxs-lookup"><span data-stu-id="1f205-123">Depending on how you specified the service account, you might need to update database logins or file permissions that grant data access rights to the service (for example, if you use the service account to process data or access linked objects on another server).</span></span>  
  
     <span data-ttu-id="1f205-124">如果您使用虚拟帐户来设置服务，则需要更新数据库登录名或文件权限。</span><span class="sxs-lookup"><span data-stu-id="1f205-124">Updating a database login or file permissions will be necessary if you used a virtual account to provision the service.</span></span> <span data-ttu-id="1f205-125">虚拟帐户基于实例名称，所以如果您将该实例重命名，虚拟帐户也会同时更新。</span><span class="sxs-lookup"><span data-stu-id="1f205-125">Virtual accounts are based on the instance name, so if you rename the instance, the virtual account is also updated at the same time.</span></span> <span data-ttu-id="1f205-126">这意味着您为之前实例创建的所有以前的登录名或权限都不再有效。</span><span class="sxs-lookup"><span data-stu-id="1f205-126">This means that any previous logins or permissions that you created for the previous instance are no longer valid.</span></span>  
  
     <span data-ttu-id="1f205-127">下面的示例进行了这方面的演示。</span><span class="sxs-lookup"><span data-stu-id="1f205-127">The following example provides an illustration.</span></span> <span data-ttu-id="1f205-128">假设你使用默认虚拟帐户将表格模式服务器安装为名为 "表格" 的实例，从而导致以下配置：</span><span class="sxs-lookup"><span data-stu-id="1f205-128">Suppose you installed a tabular mode server as an instance named "Tabular" using the default virtual account, resulting in the following configuration:</span></span>  
  
    1.  <span data-ttu-id="1f205-129">实例名称 = \<server> \TABULAR</span><span class="sxs-lookup"><span data-stu-id="1f205-129">Instance name = \<server>\TABULAR</span></span>  
  
    2.  <span data-ttu-id="1f205-130">服务名称 = MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="1f205-130">Service name = MSOLAP$TABULAR</span></span>  
  
    3.  <span data-ttu-id="1f205-131">虚拟帐户 = NT Service\ MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="1f205-131">Virtual account = NT Service\ MSOLAP$TABULAR</span></span>  
  
     <span data-ttu-id="1f205-132">现在假定您将该实例重命名为 "TAB2"。</span><span class="sxs-lookup"><span data-stu-id="1f205-132">Now suppose you rename the instance to "TAB2".</span></span> <span data-ttu-id="1f205-133">更改名称后将生成如下配置：</span><span class="sxs-lookup"><span data-stu-id="1f205-133">As a result of the name change, your configuration would now look like the following:</span></span>  
  
    1.  <span data-ttu-id="1f205-134">实例名称 = \<server> \TAB2</span><span class="sxs-lookup"><span data-stu-id="1f205-134">Instance name = \<server>\TAB2</span></span>  
  
    2.  <span data-ttu-id="1f205-135">服务名称 = MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="1f205-135">Service name = MSOLAP$TAB2</span></span>  
  
    3.  <span data-ttu-id="1f205-136">虚拟帐户 = NT Service\ MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="1f205-136">Virtual account = NT Service\ MSOLAP$TAB2</span></span>  
  
     <span data-ttu-id="1f205-137">正如您所看到的，以前授予 "NT Service \ MSOLAP $ 表格" 的数据库和文件权限不再有效。</span><span class="sxs-lookup"><span data-stu-id="1f205-137">As you can see, database and file permissions that were previously granted to "NT Service\ MSOLAP$TABULAR" are no longer valid.</span></span> <span data-ttu-id="1f205-138">若要确保服务执行的任务和操作像以前一样运行，现在需要向 "NT Service \ MSOLAP $ TAB2" 授予新的数据库和文件权限。</span><span class="sxs-lookup"><span data-stu-id="1f205-138">To ensure that tasks and operations performed by the service run as before, you would now need to grant new database and file permissions to "NT Service\ MSOLAP$TAB2".</span></span>  
  
  
