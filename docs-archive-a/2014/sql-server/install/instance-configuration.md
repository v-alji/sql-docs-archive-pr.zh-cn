---
title: 实例配置 |Microsoft Docs
ms.custom: ''
ms.date: 05/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 86a9538e81881a3b42b95447f4264200e2fe9d4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588851"
---
# <a name="instance-configuration"></a><span data-ttu-id="5758e-102">Instance Configuration</span><span class="sxs-lookup"><span data-stu-id="5758e-102">Instance Configuration</span></span>
  <span data-ttu-id="5758e-103">使用 **安装向导的** “实例配置” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 页面可指定是创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的默认实例还是其命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-103">Use the **Instance Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to create a default instance or a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5758e-104">如果尚未安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则除非您指定命名实例，否则将创建默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-104">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not already installed, a default instance will be created unless you specify a named instance.</span></span>  
  
 <span data-ttu-id="5758e-105">每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都由一组具有排列规则及其他选项特定设置的非重复的服务组成。</span><span class="sxs-lookup"><span data-stu-id="5758e-105">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of a distinct set of services that have specific settings for collations and other options.</span></span> <span data-ttu-id="5758e-106">目录结构、注册表结构和服务名称都反映在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中创建的实例名称和特定实例 ID。</span><span class="sxs-lookup"><span data-stu-id="5758e-106">The directory structure, registry structure, and service names all reflect the instance name and a specific instance ID created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="5758e-107">实例是默认实例或命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-107">An instance is either the default instance or a named instance.</span></span> <span data-ttu-id="5758e-108">默认实例名为 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="5758e-108">The default instance name is MSSQLSERVER.</span></span> <span data-ttu-id="5758e-109">不需要客户端指定实例名称便可进行连接。</span><span class="sxs-lookup"><span data-stu-id="5758e-109">It does not require a client to specify the name of the instance to make a connection.</span></span> <span data-ttu-id="5758e-110">命名实例在安装过程中由用户决定。</span><span class="sxs-lookup"><span data-stu-id="5758e-110">A named instance is determined by the user during Setup.</span></span> <span data-ttu-id="5758e-111">您可以将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作为命名实例安装，无需先安装默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-111">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a named instance without installing the default instance first.</span></span> <span data-ttu-id="5758e-112">不论版本如何，一次均只能安装一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-112">Only one installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], regardless of version, can be the default instance at one time.</span></span>  
  
 <span data-ttu-id="5758e-113">**发出!**</span><span class="sxs-lookup"><span data-stu-id="5758e-113">**Alert!**</span></span> <span data-ttu-id="5758e-114">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep，您可以在 **“实例配置”** 页上完成已准备实例时指定实例名称。</span><span class="sxs-lookup"><span data-stu-id="5758e-114">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, you can specify the instance name when you complete a prepared instance on the **Instance Configuration** page.</span></span> <span data-ttu-id="5758e-115">如果在计算机上没有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的现有默认实例，您可以选择将正在完成的已准备实例配置为默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-115">You can choose to configure the prepared instance you are completing as a default instance if there is no existing default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the machine.</span></span>  
  
## <a name="multiple-instances"></a><span data-ttu-id="5758e-116">多个实例</span><span class="sxs-lookup"><span data-stu-id="5758e-116">Multiple Instances</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5758e-117">支持在单个服务器或处理器上存在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，但只能有一个实例为默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-117">supports multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a single server or processor, but only one instance can be the default instance.</span></span> <span data-ttu-id="5758e-118">所有其他实例必须为命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-118">All others must be named instances.</span></span> <span data-ttu-id="5758e-119">一台计算机可同时运行多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，每个实例独立于其他实例运行。</span><span class="sxs-lookup"><span data-stu-id="5758e-119">A computer can run multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrently, and each instance runs independently of other instances.</span></span>  
  
 <span data-ttu-id="5758e-120">有关详细信息，请参阅[SQL Server 的最大容量规范](../maximum-capacity-specifications-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5758e-120">For more information, see [Maximum Capacity Specifications for SQL Server](../maximum-capacity-specifications-for-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5758e-121">选项</span><span class="sxs-lookup"><span data-stu-id="5758e-121">Options</span></span>  
 <span data-ttu-id="5758e-122">仅限故障转移群集实例 - 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集网络名称。</span><span class="sxs-lookup"><span data-stu-id="5758e-122">Failover cluster instances only - Specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster network name.</span></span> <span data-ttu-id="5758e-123">此名称可用来在网络上标识故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-123">This name identifies the failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="5758e-124">默认实例或命名实例 - 当决定是安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例还是命名实例时，请考虑以下信息：</span><span class="sxs-lookup"><span data-stu-id="5758e-124">Default or Named instance - Consider the following information when you decide whether to install a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="5758e-125">如果计划在数据库服务器上安装单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则该实例应为默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-125">If you plan to install a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a database server, it should be a default instance.</span></span>  
  
-   <span data-ttu-id="5758e-126">如果您打算在同一台计算机上安装多个实例，请使用命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-126">Use a named instance for situations where you plan to have multiple instances on the same computer.</span></span> <span data-ttu-id="5758e-127">一台服务器只能承载一个默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-127">A server can host only one default instance.</span></span>  
  
-   <span data-ttu-id="5758e-128">任何安装 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 的应用程序都应将其作为命名实例安装。</span><span class="sxs-lookup"><span data-stu-id="5758e-128">Any application that installs [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] should install it as a named instance.</span></span> <span data-ttu-id="5758e-129">当同一台计算机中安装多个应用程序时，这样可以最大程度地减少冲突。</span><span class="sxs-lookup"><span data-stu-id="5758e-129">This will minimizes conflict when multiple applications are installed on the same computer.</span></span>  
  
 <span data-ttu-id="5758e-130">**默认实例**</span><span class="sxs-lookup"><span data-stu-id="5758e-130">**Default instance**</span></span>  
 <span data-ttu-id="5758e-131">选择该选项可安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-131">Select this option to install a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5758e-132">一台计算机只能托管一个默认实例；所有其他实例必须是命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-132">A computer can host only one default instance; all other instances must be named.</span></span> <span data-ttu-id="5758e-133">但是，如果您已经安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例，则可以向同一台计算机添加 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-133">However, if you have a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed, you can add a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to the same computer.</span></span>  
  
 <span data-ttu-id="5758e-134">**命名实例**</span><span class="sxs-lookup"><span data-stu-id="5758e-134">**Named instance**</span></span>  
 <span data-ttu-id="5758e-135">选择该选项可创建新的命名实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-135">Select this option to create a new named instance.</span></span> <span data-ttu-id="5758e-136">当对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例进行命名时，请注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="5758e-136">Be aware of the following when you name an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="5758e-137">实例名不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="5758e-137">Instance names are not case sensitive.</span></span>  
  
-   <span data-ttu-id="5758e-138">实例名不能以下划线 (_) 开始或结束。</span><span class="sxs-lookup"><span data-stu-id="5758e-138">Instance names cannot start or end with an underscore (_).</span></span>  
  
-   <span data-ttu-id="5758e-139">实例名称不能包含词语“Default”或其他保留关键字。</span><span class="sxs-lookup"><span data-stu-id="5758e-139">Instance names cannot contain the term "Default" or other reserved keywords.</span></span> <span data-ttu-id="5758e-140">如果在实例名中使用了保留关键字，将发生安装错误。</span><span class="sxs-lookup"><span data-stu-id="5758e-140">If a reserved keyword is used in an instance name, a Setup error will occur.</span></span> <span data-ttu-id="5758e-141">有关详细信息，请参阅[保留关键字 &#40;transact-sql&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5758e-141">For more information, see [Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql).</span></span>  
  
-   <span data-ttu-id="5758e-142">如果为实例名称指定 MSSQLServer，将创建默认实例。</span><span class="sxs-lookup"><span data-stu-id="5758e-142">If you specify MSSQLServer for the instance name, a default instance will be created.</span></span>  
  
-   <span data-ttu-id="5758e-143">[!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] 安装始终安装为命名实例“PowerPivot”。</span><span class="sxs-lookup"><span data-stu-id="5758e-143">An installation of [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] is always installed as a named instance of 'PowerPivot'.</span></span> <span data-ttu-id="5758e-144">不能为此功能角色指定不同的实例名称。</span><span class="sxs-lookup"><span data-stu-id="5758e-144">You cannot specify a different instance name for this feature role.</span></span>  
  
-   <span data-ttu-id="5758e-145">实例名限制为 16 个字符。</span><span class="sxs-lookup"><span data-stu-id="5758e-145">Instance names are limited to 16 characters.</span></span>  
  
-   <span data-ttu-id="5758e-146">实例名中的第一个字符必须是字母。</span><span class="sxs-lookup"><span data-stu-id="5758e-146">The first character in the instance name must be a letter.</span></span> <span data-ttu-id="5758e-147">可接受的字母为 Unicode 标准 2.0 定义的那些字母。</span><span class="sxs-lookup"><span data-stu-id="5758e-147">Acceptable letters are those defined by the Unicode Standard 2.0.</span></span> <span data-ttu-id="5758e-148">这些字母包括拉丁字符 a-z、A-Z 和其他语言中的字母字符。</span><span class="sxs-lookup"><span data-stu-id="5758e-148">These include Latin characters a-z, A-Z, and letter characters from other languages.</span></span>  
  
-   <span data-ttu-id="5758e-149">后续字符可以是 Unicode 标准 2.0 定义的字母、源于基本拉丁语或其他国家/地区书写符号的十进制数字、美元符号 ($) 或者下划线 (_)。</span><span class="sxs-lookup"><span data-stu-id="5758e-149">Subsequent characters can be letters defined by the Unicode Standard 2.0, decimal numbers from Basic Latin or other national scripts, the dollar sign ($), or an underscore (_).</span></span>  
  
-   <span data-ttu-id="5758e-150">实例名称中不允许含有空格或其他特殊字符，</span><span class="sxs-lookup"><span data-stu-id="5758e-150">Embedded spaces or other special characters are not allowed in instance names.</span></span> <span data-ttu-id="5758e-151">也不允许存在反斜杠 (\\)、逗号 (,)、冒号 (:)、分号 (;)、单引号 (')、& 号 (&)、连字号 (-) 和 at 符 (@)。</span><span class="sxs-lookup"><span data-stu-id="5758e-151">The backslash (\\), comma (,), colon (:), semi-colon (;), single quote ('), ampersand (&), hyphen (-), and at sign (@) are also not allowed.</span></span>  
  
-   <span data-ttu-id="5758e-152">**只有在当前 Windows 代码页中有效的字符才能用在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称中。如果使用不受支持的 Unicode 字符，将会发生安装错误。**</span><span class="sxs-lookup"><span data-stu-id="5758e-152">**Only characters that are valid in the current Windows code page can be used in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance names. If an unsupported Unicode character is used, a Setup error will occur.**</span></span>  
  
 <span data-ttu-id="5758e-153">**检测到的实例和功能**</span><span class="sxs-lookup"><span data-stu-id="5758e-153">**Detected instances and features**</span></span>  
 <span data-ttu-id="5758e-154">查看正在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的计算机中安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和组件的列表。</span><span class="sxs-lookup"><span data-stu-id="5758e-154">View a list of installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances and components on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running.</span></span>  
  
 <span data-ttu-id="5758e-155">**实例 ID** - 默认情况下，实例名称用作实例 ID。</span><span class="sxs-lookup"><span data-stu-id="5758e-155">**Instance ID** - By default, the instance name is used as the Instance ID.</span></span> <span data-ttu-id="5758e-156">这用于标识 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的安装目录和注册表项。</span><span class="sxs-lookup"><span data-stu-id="5758e-156">This is used to identify installation directories and registry keys for your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5758e-157">默认实例和命名实例都是如此。</span><span class="sxs-lookup"><span data-stu-id="5758e-157">This is the case for default instances and named instances.</span></span> <span data-ttu-id="5758e-158">对于默认实例，实例名称和实例 ID 为 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="5758e-158">For a default instance, the instance name and instance ID would be MSSQLSERVER.</span></span> <span data-ttu-id="5758e-159">若要使用非默认的实例 ID，请在 "**实例 id** " 字段中指定该 id。</span><span class="sxs-lookup"><span data-stu-id="5758e-159">To use a non-default instance ID, specify it in the **Instance ID** field.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5758e-160">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep，在此页上显示的实例 ID 是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 过程的准备映像步骤中指定的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="5758e-160">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, the Instance ID displayed on this page is the Instance ID specified during the prepare image step of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep process.</span></span> <span data-ttu-id="5758e-161">在完成映像步骤中，您将无法指定不同的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="5758e-161">You will not be able to specify a different Instance ID during the complete image step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5758e-162">不支持以下划线 (_) 或包含数字符号 ( # ) 或美元符号 ($) 的实例 Id。</span><span class="sxs-lookup"><span data-stu-id="5758e-162">Instance IDs that begin with an underscore (_) or that contain the number sign (#) or the dollar sign ($) are not supported.</span></span>  
  
 <span data-ttu-id="5758e-163">有关目录、文件位置和实例 ID 命名的详细信息，请参阅[SQL Server 的默认实例和命名实例的文件位置](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5758e-163">For more information about directories, file locations, and instance ID naming, see [File Locations for Default and Named Instances of SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="5758e-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的给定实例的所有组件作为一个单元进行管理。</span><span class="sxs-lookup"><span data-stu-id="5758e-164">All components of a given instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are managed as a unit.</span></span> <span data-ttu-id="5758e-165">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 和升级都将应用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的每个组件。</span><span class="sxs-lookup"><span data-stu-id="5758e-165">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service packs and upgrades will apply to every component of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5758e-166">共用同一实例名称的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件都必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="5758e-166">All components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that share the same instance name must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="5758e-167">版本相同\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5758e-167">**Same version**</span></span>  
  
-   <span data-ttu-id="5758e-168">版本类别相同\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5758e-168">**Same edition**</span></span>  
  
-   <span data-ttu-id="5758e-169">语言设置相同\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5758e-169">**Same language settings**</span></span>  
  
-   <span data-ttu-id="5758e-170">聚集状态相同\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5758e-170">**Same clustered state**</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5758e-171">不能识别群集。</span><span class="sxs-lookup"><span data-stu-id="5758e-171">is not cluster-aware.</span></span>  
  
-   <span data-ttu-id="5758e-172">操作系统相同\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5758e-172">**Same operating system**</span></span>  
  
  
