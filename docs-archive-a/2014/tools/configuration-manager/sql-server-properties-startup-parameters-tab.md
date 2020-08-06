---
title: " (\"启动参数\" 选项卡) SQL Server 属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 16942624-5374-446c-8de4-ee6ed34d6e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66c4b71433face008ba78af93579cf175fb4bed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586032"
---
# <a name="sql-server-properties-startup-parameters-tab"></a><span data-ttu-id="8facc-102">SQL Server 属性（“启动参数”选项卡）</span><span class="sxs-lookup"><span data-stu-id="8facc-102">SQL Server Properties (Startup Parameters Tab)</span></span>
  <span data-ttu-id="8facc-103">使用此对话框可以添加或删除 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的启动参数。</span><span class="sxs-lookup"><span data-stu-id="8facc-103">Use this dialog box to add or remove startup parameters for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="8facc-104">启动参数可能会对 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 性能产生很大影响。</span><span class="sxs-lookup"><span data-stu-id="8facc-104">Startup parameters can have a large effect on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] performance.</span></span> <span data-ttu-id="8facc-105">在添加或更改启动参数前，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的主题“使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务启动选项”。</span><span class="sxs-lookup"><span data-stu-id="8facc-105">Before adding or changing startup parameters, see the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8facc-106">选项</span><span class="sxs-lookup"><span data-stu-id="8facc-106">Options</span></span>  
 <span data-ttu-id="8facc-107">**指定启动参数**</span><span class="sxs-lookup"><span data-stu-id="8facc-107">**Specify a startup parameter**</span></span>  
 <span data-ttu-id="8facc-108">若要添加某一参数，请键入该参数，然后单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="8facc-108">To add a parameter, type the parameter, and then click **Add**.</span></span>  
  
 <span data-ttu-id="8facc-109">若要修改所需的参数之一，请在 **“现有参数”** 框中键入该参数，更改 **“指定启动参数”** 框中的值，然后单击 **“更新”** 。</span><span class="sxs-lookup"><span data-stu-id="8facc-109">To modify one of the required parameters, select the parameter in the **Existing parameters** box, change the values in the **Specify a startup parameter** box, and then click **Update**.</span></span>  
  
 <span data-ttu-id="8facc-110">**“现有参数”**</span><span class="sxs-lookup"><span data-stu-id="8facc-110">**Existing parameters**</span></span>  
 <span data-ttu-id="8facc-111">若要删除某一参数，请选择该参数，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="8facc-111">To remove a parameter, select a parameter, and then click **Remove**.</span></span>  
  
## <a name="parameter-format"></a><span data-ttu-id="8facc-112">参数格式</span><span class="sxs-lookup"><span data-stu-id="8facc-112">Parameter Format</span></span>  
 <span data-ttu-id="8facc-113">不要在参数之间输入分隔符。</span><span class="sxs-lookup"><span data-stu-id="8facc-113">Do not enter a separator between parameters.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8facc-114">配置管理器会自动添加分隔符。</span><span class="sxs-lookup"><span data-stu-id="8facc-114">Configuration Manager automatically adds the separator.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8facc-115">配置管理器将强制以下参数要求。</span><span class="sxs-lookup"><span data-stu-id="8facc-115">Configuration Manager enforces the following parameter requirements.</span></span>  
  
-   <span data-ttu-id="8facc-116">前导空格和尾随空格将会从任何启动参数中删除。</span><span class="sxs-lookup"><span data-stu-id="8facc-116">Leading and trailing spaces are trimmed from any startup parameter.</span></span>  
  
-   <span data-ttu-id="8facc-117">所有启动参数都以短破折号 (-) 开头，且第二个值是字母。</span><span class="sxs-lookup"><span data-stu-id="8facc-117">All startup parameters start with a - (dash) and the second value is a letter.</span></span>  
  
## <a name="required-parameters"></a><span data-ttu-id="8facc-118">必需的参数</span><span class="sxs-lookup"><span data-stu-id="8facc-118">Required Parameters</span></span>  
 <span data-ttu-id="8facc-119">下列参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="8facc-119">The following parameters are required.</span></span> <span data-ttu-id="8facc-120">可以更改这些参数，但不能删除它们。</span><span class="sxs-lookup"><span data-stu-id="8facc-120">They can be changed but not removed.</span></span>  
  
-   <span data-ttu-id="8facc-121">-d 是 **master.mdf** 文件（master 数据库数据文件）的路径。</span><span class="sxs-lookup"><span data-stu-id="8facc-121">-d is the path of the **master.mdf** file (the master database data file).</span></span>  
  
-   <span data-ttu-id="8facc-122">-l 是 **master.ldf** 文件（master 数据库日志文件）的路径。</span><span class="sxs-lookup"><span data-stu-id="8facc-122">-l is the path of the **master.ldf** file (the master database log file).</span></span>  
  
-   <span data-ttu-id="8facc-123">-e 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="8facc-123">-e is the path of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log files.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8facc-124">如果该文件路径参数不正确， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能不会启动。</span><span class="sxs-lookup"><span data-stu-id="8facc-124">If the file path parameters are incorrect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not start.</span></span>  
  
 <span data-ttu-id="8facc-125">有关如何移动 master 数据库的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“移动系统数据库”主题。</span><span class="sxs-lookup"><span data-stu-id="8facc-125">For more information about how to move the master database, see the topic "Moving System Databases" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="8facc-126">可选参数</span><span class="sxs-lookup"><span data-stu-id="8facc-126">Optional Parameters</span></span>  
 <span data-ttu-id="8facc-127">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书的“使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务启动选项”主题中介绍了所有支持的启动参数。</span><span class="sxs-lookup"><span data-stu-id="8facc-127">All of the supported startup parameters are described in the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options," in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="8facc-128">-T*trace#* 的启动参数指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例应该以有效的指定跟踪标志 (*trace#* ) 启动。</span><span class="sxs-lookup"><span data-stu-id="8facc-128">A startup parameter of -T*trace#* indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="8facc-129">跟踪标记用于以非标准行为启动服务器。</span><span class="sxs-lookup"><span data-stu-id="8facc-129">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="8facc-130">有关跟踪标志的详细信息，请参阅[!INCLUDE[tsql](../../includes/tsql-md.md)]联机丛书中的“跟踪标志 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )”主题。</span><span class="sxs-lookup"><span data-stu-id="8facc-130">For more information about trace flags, see the topic "Trace Flags ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8facc-131">您可能会看到在 Internet 上描述的其他未记录的启动参数和跟踪标志。</span><span class="sxs-lookup"><span data-stu-id="8facc-131">You might see additional undocumented startup parameters and trace flags described on the Internet.</span></span> <span data-ttu-id="8facc-132">创建未记录的启动参数和跟踪标志是为了满足某些不常见问题或者强制测试所需的某些条件。</span><span class="sxs-lookup"><span data-stu-id="8facc-132">Undocumented startup parameters and trace flags are created to address uncommon problems or to force certain conditions required for testing.</span></span> <span data-ttu-id="8facc-133">使用未记录的启动参数可能会导致意外结果。</span><span class="sxs-lookup"><span data-stu-id="8facc-133">Using undocumented startup parameters can have unexpected results.</span></span> <span data-ttu-id="8facc-134">除非 Microsoft 客户支持服务部门指示，否则不要使用未记录的参数。</span><span class="sxs-lookup"><span data-stu-id="8facc-134">Do not use undocumented parameters unless directed by Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="8facc-135">下表描述某些常见的可选参数。</span><span class="sxs-lookup"><span data-stu-id="8facc-135">The following list describes some common optional parameters.</span></span>  
  
|<span data-ttu-id="8facc-136">参数</span><span class="sxs-lookup"><span data-stu-id="8facc-136">Parameter</span></span>|<span data-ttu-id="8facc-137">简短说明</span><span class="sxs-lookup"><span data-stu-id="8facc-137">Short description</span></span>|  
|---------------|-----------------------|  
|<span data-ttu-id="8facc-138">-M</span><span class="sxs-lookup"><span data-stu-id="8facc-138">-m</span></span>|<span data-ttu-id="8facc-139">在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8facc-139">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>|  
|<span data-ttu-id="8facc-140">-T1204</span><span class="sxs-lookup"><span data-stu-id="8facc-140">-T1204</span></span>|<span data-ttu-id="8facc-141">返回参与死锁的锁的资源和类型，以及受影响的当前命令。</span><span class="sxs-lookup"><span data-stu-id="8facc-141">Returns the resources and types of locks participating in a deadlock and also the current command affected.</span></span>|  
|<span data-ttu-id="8facc-142">-T1224</span><span class="sxs-lookup"><span data-stu-id="8facc-142">-T1224</span></span>|<span data-ttu-id="8facc-143">基于锁数禁用锁升级。</span><span class="sxs-lookup"><span data-stu-id="8facc-143">Disables lock escalation based on the number of locks.</span></span>|  
|<span data-ttu-id="8facc-144">-T3608</span><span class="sxs-lookup"><span data-stu-id="8facc-144">-T3608</span></span>|<span data-ttu-id="8facc-145">禁止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动启动和恢复除 master 数据库之外的任何数据库。</span><span class="sxs-lookup"><span data-stu-id="8facc-145">Prevents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from automatically starting and recovering any database except the master database.</span></span>|  
|<span data-ttu-id="8facc-146">-T7806</span><span class="sxs-lookup"><span data-stu-id="8facc-146">-T7806</span></span>|<span data-ttu-id="8facc-147">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]上启用专用管理员连接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="8facc-147">Enables a dedicated administrator connection (DAC) on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="8facc-148">某些可选参数可能会更改服务器行为并且可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="8facc-148">Some optional parameters can change server behavior and may affect performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="8facc-149">权限</span><span class="sxs-lookup"><span data-stu-id="8facc-149">Permissions</span></span>  
 <span data-ttu-id="8facc-150">此页的使用被限制为可以在注册表中更改相关条目的用户。</span><span class="sxs-lookup"><span data-stu-id="8facc-150">Use of this page is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="8facc-151">其中包括以下用户。</span><span class="sxs-lookup"><span data-stu-id="8facc-151">This includes the following users.</span></span>  
  
-   <span data-ttu-id="8facc-152">本地管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="8facc-152">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="8facc-153">如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]配置为在域帐户下运行，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 使用该域帐户。</span><span class="sxs-lookup"><span data-stu-id="8facc-153">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
## <a name="books-online-references"></a><span data-ttu-id="8facc-154">联机丛书参考</span><span class="sxs-lookup"><span data-stu-id="8facc-154">Books Online References</span></span>  
 <span data-ttu-id="8facc-155">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动参数的其他信息，请参阅[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“如何配置服务器启动选项（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器）”。</span><span class="sxs-lookup"><span data-stu-id="8facc-155">For additional information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup parameters, see "How to: Configure Server Startup Options ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
