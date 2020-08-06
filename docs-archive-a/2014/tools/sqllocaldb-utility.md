---
title: SqlLocalDB 实用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfb95cea4365d56c296d14fcc09046cd7eddc0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682488"
---
# <a name="sqllocaldb-utility"></a><span data-ttu-id="9fae7-102">SqlLocalDB 实用工具</span><span class="sxs-lookup"><span data-stu-id="9fae7-102">SqlLocalDB Utility</span></span>
  <span data-ttu-id="9fae7-103">使用 `SqlLocalDB` 实用程序创建 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-103">Use the `SqlLocalDB` utility to create an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)]**LocalDB**.</span></span> <span data-ttu-id="9fae7-104">`SqlLocalDB`实用程序 ( # A0) 是一个简单的命令行工具，可让用户和开发者创建和管理 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-104">The `SqlLocalDB` utility (SqlLocalDB.exe) is a simple command line tool to enable users and developers to create and manage an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="9fae7-105">有关如何使用**LocalDB**的信息，请参阅[SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)。</span><span class="sxs-lookup"><span data-stu-id="9fae7-105">For information about how to use **LocalDB**, see [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fae7-106">语法</span><span class="sxs-lookup"><span data-stu-id="9fae7-106">Syntax</span></span>  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="9fae7-107">参数</span><span class="sxs-lookup"><span data-stu-id="9fae7-107">Arguments</span></span>  
 <span data-ttu-id="9fae7-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [ **-s** ]</span><span class="sxs-lookup"><span data-stu-id="9fae7-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]</span></span>  
 <span data-ttu-id="9fae7-109">新建 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-109">Creates a new of instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="9fae7-110">`SqlLocalDB`使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 参数指定的二进制文件版本 *\<instance-version>* 。</span><span class="sxs-lookup"><span data-stu-id="9fae7-110">`SqlLocalDB` uses the version of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] binaries specified by *\<instance-version>* argument.</span></span> <span data-ttu-id="9fae7-111">版本号以数字格式指定，至少有一个小数点。</span><span class="sxs-lookup"><span data-stu-id="9fae7-111">The version number is specified in numeric format with at least one decimal.</span></span> <span data-ttu-id="9fae7-112">次要版本号 (Service Pack） 是可选的。</span><span class="sxs-lookup"><span data-stu-id="9fae7-112">The minor version numbers (service packs) are optional.</span></span> <span data-ttu-id="9fae7-113">例如，下面的两个版本号均可接受：11.0 或 11.0.1186。</span><span class="sxs-lookup"><span data-stu-id="9fae7-113">For example the following two version numbers are both acceptable: 11.0, or 11.0.1186.</span></span> <span data-ttu-id="9fae7-114">必须在计算机上安装指定的版本。</span><span class="sxs-lookup"><span data-stu-id="9fae7-114">The specified version must be installed on the computer.</span></span> <span data-ttu-id="9fae7-115">如果未指定，版本号默认为实用工具的版本 `SqlLocalDB` 。</span><span class="sxs-lookup"><span data-stu-id="9fae7-115">If not specified, the version number defaults to the version of the `SqlLocalDB` utility.</span></span> <span data-ttu-id="9fae7-116">添加 -s 可启动新的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-116">Adding **-s** starts the new instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="9fae7-117">[ **共享** | **h** ]</span><span class="sxs-lookup"><span data-stu-id="9fae7-117">[ **share** | **h** ]</span></span>  
 <span data-ttu-id="9fae7-118">使用指定的共享名称共享指定的 **LocalDB** 私有实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-118">Shares the specified private instance of **LocalDB** using the specified shared name.</span></span> <span data-ttu-id="9fae7-119">如果省略该用户 SID 或帐户名称，则默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="9fae7-119">If the user SID or account name is omitted, it defaults to the current user.</span></span>  
  
 <span data-ttu-id="9fae7-120">[ **unshared** | **u** ]</span><span class="sxs-lookup"><span data-stu-id="9fae7-120">[ **unshared** | **u** ]</span></span>  
 <span data-ttu-id="9fae7-121">停止共享指定的 **LocalDB**共享实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-121">Stops the sharing of the specified shared instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="9fae7-122">[ **delete** | **d** ] *\<instance-name>*</span><span class="sxs-lookup"><span data-stu-id="9fae7-122">[ **delete** | **d** ] *\<instance-name>*</span></span>  
 <span data-ttu-id="9fae7-123">删除指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-123">Deletes the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span>  
  
 <span data-ttu-id="9fae7-124">[ **start** | **s** ] " *\<instance-name>* "</span><span class="sxs-lookup"><span data-stu-id="9fae7-124">[ **start** | **s** ] "*\<instance-name>*"</span></span>  
 <span data-ttu-id="9fae7-125">启动指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-125">Starts the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="9fae7-126">成功后，该语句返回 **LocalDB**的命名管道地址。</span><span class="sxs-lookup"><span data-stu-id="9fae7-126">When successful the statement returns the named pipe address of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="9fae7-127">[ **stop** | **p** ] *\<instance-name>* [ **-i** ] [ **-k** ]</span><span class="sxs-lookup"><span data-stu-id="9fae7-127">[ **stop** | **p** ] *\<instance-name>* [**-i** ] [**-k** ]</span></span>  
 <span data-ttu-id="9fae7-128">停止指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-128">Stops the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="9fae7-129">添加 **-i**用选项请求关闭实例 `NOWAIT` 。</span><span class="sxs-lookup"><span data-stu-id="9fae7-129">Adding **-i** requests the instance shutdown with the `NOWAIT` option.</span></span> <span data-ttu-id="9fae7-130">添加 -k 可终止实例进程，而无需联系它。</span><span class="sxs-lookup"><span data-stu-id="9fae7-130">Adding **-k** kills the instance process without contacting it.</span></span>  
  
 <span data-ttu-id="9fae7-131">[ **info** | **i** ] [ *\<instance-name>* ]</span><span class="sxs-lookup"><span data-stu-id="9fae7-131">[ **info** | **i** ] [ *\<instance-name>* ]</span></span>  
 <span data-ttu-id="9fae7-132">列出当前用户拥有的所有 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-132">Lists all instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** owned by the current user.</span></span>  
  
 <span data-ttu-id="9fae7-133">\<instance-name> 返回指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]LocalDB 实例的名称、版本、状态（正在运行或已停止）、上次启动时间，以及 LocalDB 的本地管道名称。</span><span class="sxs-lookup"><span data-stu-id="9fae7-133">*\<instance-name>* returns the name, version, state (Running or Stopped), last start time for the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**, and the local pipe name of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="9fae7-134">[ **trace** | **t** ] **on** | **off**</span><span class="sxs-lookup"><span data-stu-id="9fae7-134">[ **trace** | **t** ] **on** | **off**</span></span>  
 <span data-ttu-id="9fae7-135">**上的 trace**启用对 `SqlLocalDB` 当前用户的 API 调用的跟踪。</span><span class="sxs-lookup"><span data-stu-id="9fae7-135">**trace on** enables tracing for the `SqlLocalDB` API calls for the current user.</span></span> <span data-ttu-id="9fae7-136">**trace off** 禁用跟踪。</span><span class="sxs-lookup"><span data-stu-id="9fae7-136">**trace off** disables tracing.</span></span>  
  
 <span data-ttu-id="9fae7-137">**-?**</span><span class="sxs-lookup"><span data-stu-id="9fae7-137">**-?**</span></span>  
 <span data-ttu-id="9fae7-138">返回每个选项的简短说明 `SqlLocalDB` 。</span><span class="sxs-lookup"><span data-stu-id="9fae7-138">Returns brief descriptions of each `SqlLocalDB` option.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fae7-139">备注</span><span class="sxs-lookup"><span data-stu-id="9fae7-139">Remarks</span></span>  
 <span data-ttu-id="9fae7-140">*实例名称* 参数必须遵循 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符规则，或者必须将该参数放入双引号。</span><span class="sxs-lookup"><span data-stu-id="9fae7-140">The *instance name* argument must follow the rules for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers or it must be enclosed in double quotes.</span></span>  
  
 <span data-ttu-id="9fae7-141">执行不带参数的 SqlLocalDB 将返回帮助文档。</span><span class="sxs-lookup"><span data-stu-id="9fae7-141">Executing SqlLocalDB without arguments returns the help text.</span></span>  
  
 <span data-ttu-id="9fae7-142">只能在属于当前已登录用户的实例上执行启动以外的其他操作。</span><span class="sxs-lookup"><span data-stu-id="9fae7-142">Operations other than start can only be performed on an instance belonging to currently logged in user.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9fae7-143">示例</span><span class="sxs-lookup"><span data-stu-id="9fae7-143">Examples</span></span>  
  
### <a name="a-creating-an-instance-of-localdb"></a><span data-ttu-id="9fae7-144">A.</span><span class="sxs-lookup"><span data-stu-id="9fae7-144">A.</span></span> <span data-ttu-id="9fae7-145">创建 LocalDB 实例</span><span class="sxs-lookup"><span data-stu-id="9fae7-145">Creating an Instance of LocalDB</span></span>  
 <span data-ttu-id="9fae7-146">下面的示例使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**二进制文件创建了一个名为** 的 `DEPARTMENT` LocalDB [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 实例，并启动该实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-146">The following example creates an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** named `DEPARTMENT` using the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] binaries and starts the instance.</span></span>  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a><span data-ttu-id="9fae7-147">B.</span><span class="sxs-lookup"><span data-stu-id="9fae7-147">B.</span></span> <span data-ttu-id="9fae7-148">使用 LocalDB 的共享实例</span><span class="sxs-lookup"><span data-stu-id="9fae7-148">Working with a Shared Instance of LocalDB</span></span>  
 <span data-ttu-id="9fae7-149">使用管理员权限打开一个命令提示符。</span><span class="sxs-lookup"><span data-stu-id="9fae7-149">Open a command prompt using Administrator privileges.</span></span>  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 <span data-ttu-id="9fae7-150">执行以下代码，使用 **登录名连接到** LocalDB `NewLogin` 的共享实例。</span><span class="sxs-lookup"><span data-stu-id="9fae7-150">Execute the following code to connect to the shared instance of **LocalDB** using the `NewLogin` login.</span></span>  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fae7-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fae7-151">See Also</span></span>  
 [<span data-ttu-id="9fae7-152">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="9fae7-152">SQL Server 2014 Express LocalDB</span></span>](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
