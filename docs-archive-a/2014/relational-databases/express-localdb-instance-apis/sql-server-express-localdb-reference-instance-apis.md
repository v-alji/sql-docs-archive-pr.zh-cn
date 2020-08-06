---
title: SQL Server Express LocalDB 实例 API 参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5934bc5159998db22d7c560b31457524773e74eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682835"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a><span data-ttu-id="613d5-102">SQL Server Express LocalDB 实例 API 参考</span><span class="sxs-lookup"><span data-stu-id="613d5-102">SQL Server Express LocalDB Instance API Reference</span></span>
  <span data-ttu-id="613d5-103">在传统的、基于服务的 SQL Server 世界里，安装在单台计算机上的各 SQL Server 实例是物理分隔的；也就是说，每个实例都必须单独进行安装和删除，具有单独的一组二进制代码，并且在单独的服务进程下运行。</span><span class="sxs-lookup"><span data-stu-id="613d5-103">In the traditional, service-based SQL Server world, individual SQL Server instances installed on a single computer are physically separated; that is, each instance must be installed and removed separately, has a separate set of binaries, and runs under a separate service process.</span></span> <span data-ttu-id="613d5-104">SQL Server 实例名称用于指定用户要连接的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-104">The SQL Server instance name is used to specify which SQL Server instance the user wants to connect to.</span></span>  
  
 <span data-ttu-id="613d5-105">SQL Server Express LocalDB 实例 API 使用简化的 "轻型" 实例模型。</span><span class="sxs-lookup"><span data-stu-id="613d5-105">The SQL Server Express LocalDB instance API uses a simplified, "light" instance model.</span></span> <span data-ttu-id="613d5-106">尽管各个 LocalDB 实例在磁盘和注册表中是单独分开的，但它们使用同一组共享 LocalDB 二进制代码。</span><span class="sxs-lookup"><span data-stu-id="613d5-106">Although individual LocalDB instances are separated on the disk and in the registry, they use the same set of shared LocalDB binaries.</span></span> <span data-ttu-id="613d5-107">此外，LocalDB 不使用服务；LocalDB 实例是通过 LocalDB 实例 API 调用按需启动的。</span><span class="sxs-lookup"><span data-stu-id="613d5-107">Moreover, LocalDB does not use services; LocalDB instances are launched on demand through LocalDB instance API calls.</span></span> <span data-ttu-id="613d5-108">在 LocalDB 中，实例名称用于指定用户要使用的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-108">In LocalDB, the instance name is used to specify which of the LocalDB instances the user wants to work with.</span></span>  
  
 <span data-ttu-id="613d5-109">LocalDB 实例始终由单个用户所有，并且仅在此用户的上下文中可见且可访问，除非已启用实例共享。</span><span class="sxs-lookup"><span data-stu-id="613d5-109">A LocalDB instance is always owned by a single user and is visible and accessible only from this user's context, unless instance sharing is enabled.</span></span>  
  
 <span data-ttu-id="613d5-110">尽管从技术上说 LocalDB 实例与传统 SQL Server 实例不同，但它们的目标用途是类似的。</span><span class="sxs-lookup"><span data-stu-id="613d5-110">Although technically LocalDB instances are not the same as traditional SQL Server instances, their intended use is similar.</span></span> <span data-ttu-id="613d5-111">它们被称为*实例*来强调这种相似性，并使它们对 SQL Server 用户更加直观。</span><span class="sxs-lookup"><span data-stu-id="613d5-111">They are called *instances* to emphasize this similarity and to make them more intuitive to SQL Server users.</span></span>  
  
 <span data-ttu-id="613d5-112">LocalDB 支持两种类型的实例：自动实例 (AI) 和命名实例 (NI)。</span><span class="sxs-lookup"><span data-stu-id="613d5-112">LocalDB supports two kinds of instances: automatic instances (AI) and named instances (NI).</span></span> <span data-ttu-id="613d5-113">LocalDB 实例的标识符为实例名称。</span><span class="sxs-lookup"><span data-stu-id="613d5-113">The identifier for a LocalDB instance is the instance name.</span></span>  
  
## <a name="automatic-localdb-instances"></a><span data-ttu-id="613d5-114">自动 LocalDB 实例</span><span class="sxs-lookup"><span data-stu-id="613d5-114">Automatic LocalDB Instances</span></span>  
 <span data-ttu-id="613d5-115">自动 LocalDB 实例为 "公共";它们是为用户自动创建和管理的，可供任何应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="613d5-115">Automatic LocalDB instances are "public"; they are created and managed automatically for the user and can be used by any application.</span></span> <span data-ttu-id="613d5-116">在用户计算机上安装的每个 LocalDB 版本都存在一个自动 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-116">One automatic LocalDB instance exists for every version of LocalDB that is installed on the user's computer.</span></span>  
  
 <span data-ttu-id="613d5-117">自动 LocalDB 实例提供无缝的实例管理。</span><span class="sxs-lookup"><span data-stu-id="613d5-117">Automatic LocalDB instances provide seamless instance management.</span></span> <span data-ttu-id="613d5-118">用户不需要创建该实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-118">The user does not need to create the instance.</span></span> <span data-ttu-id="613d5-119">这使用户能够轻松地安装应用程序，并迁移到不同的计算机。</span><span class="sxs-lookup"><span data-stu-id="613d5-119">This enables users to easily install applications and to migrate to different computers.</span></span> <span data-ttu-id="613d5-120">如果目标计算机已安装指定版本的 LocalDB，则该计算机也提供此版本的自动 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-120">If the target computer has the specified version of LocalDB installed, the automatic LocalDB instance for that version is also available on that computer.</span></span>  
  
### <a name="automatic-instance-management"></a><span data-ttu-id="613d5-121">自动实例管理</span><span class="sxs-lookup"><span data-stu-id="613d5-121">Automatic Instance Management</span></span>  
 <span data-ttu-id="613d5-122">用户无需创建自动 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-122">A user does not need to create an automatic LocalDB instance.</span></span> <span data-ttu-id="613d5-123">如果在用户的计算机上提供了指定版本的 LocalDB，则在第一次使用实例时会延迟创建实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-123">The instance is lazily created the first time the instance is used, provided that the specified version of LocalDB is available on the user's computer.</span></span> <span data-ttu-id="613d5-124">从用户的角度来看，如果存在 LocalDB 二进制文件，则始终存在自动实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-124">From the user's point of view, the automatic instance is always present if the LocalDB binaries are present.</span></span>  
  
 <span data-ttu-id="613d5-125">其他实例管理操作（如删除、共享和取消共享）也适应于自动实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-125">Other instance management operations, such as Delete, Share, and Unshare, also work for automatic instances.</span></span> <span data-ttu-id="613d5-126">尤其是，删除自动实例可以高效地重置实例，这样，在下一个启动操作时将重新创建此实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-126">In particular, deleting an automatic instance effectively resets the instance, which will be re-created on the next Start operation.</span></span> <span data-ttu-id="613d5-127">如果系统数据库已损坏，则可能需要删除自动实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-127">Deleting an automatic instance may be required if the system databases become corrupted.</span></span>  
  
### <a name="automatic-instance-naming-rules"></a><span data-ttu-id="613d5-128">自动实例命名规则</span><span class="sxs-lookup"><span data-stu-id="613d5-128">Automatic Instance Naming Rules</span></span>  
 <span data-ttu-id="613d5-129">自动 LocalDB 实例具有属于保留命名空间的特殊实例名称模式。</span><span class="sxs-lookup"><span data-stu-id="613d5-129">Automatic LocalDB instances have a special pattern for the instance name that belongs to a reserved namespace.</span></span> <span data-ttu-id="613d5-130">这对于防止名称与命名 LocalDB 实例发生冲突至关重要。</span><span class="sxs-lookup"><span data-stu-id="613d5-130">This is necessary to prevent name conflicts with named LocalDB instances.</span></span>  
  
 <span data-ttu-id="613d5-131">自动实例名称是前面带有单个 "v" 字符的 LocalDB 基线发布版本号。</span><span class="sxs-lookup"><span data-stu-id="613d5-131">The automatic instance name is the LocalDB baseline release version number preceded by a single "v" character.</span></span> <span data-ttu-id="613d5-132">这看起来像 "v"，两个数字之间有一个句点;例如，11.0 或 V 12.00。</span><span class="sxs-lookup"><span data-stu-id="613d5-132">This looks like "v" plus two numbers with a period between them; for example, v11.0 or V12.00.</span></span>  
  
 <span data-ttu-id="613d5-133">非法自动实例名称的示例如下：</span><span class="sxs-lookup"><span data-stu-id="613d5-133">Examples of illegal automatic instance names are:</span></span>  
  
-   <span data-ttu-id="613d5-134">11.0 (缺少开头的 "v" 字符) </span><span class="sxs-lookup"><span data-stu-id="613d5-134">11.0 (missing the "v" character at the beginning)</span></span>  
  
-   <span data-ttu-id="613d5-135">v11（缺少句点和版本的第二个数字）</span><span class="sxs-lookup"><span data-stu-id="613d5-135">v11 (missing a period and the second number of the version)</span></span>  
  
-   <span data-ttu-id="613d5-136">v11.</span><span class="sxs-lookup"><span data-stu-id="613d5-136">v11.</span></span> <span data-ttu-id="613d5-137">（缺少版本的第二个数字）</span><span class="sxs-lookup"><span data-stu-id="613d5-137">(missing the second number of the version)</span></span>  
  
-   <span data-ttu-id="613d5-138">v11.0.1.2（版本号超出两个部分）</span><span class="sxs-lookup"><span data-stu-id="613d5-138">v11.0.1.2 (version number has more than two parts)</span></span>  
  
## <a name="named-localdb-instances"></a><span data-ttu-id="613d5-139">命名的 LocalDB 实例</span><span class="sxs-lookup"><span data-stu-id="613d5-139">Named LocalDB Instances</span></span>  
 <span data-ttu-id="613d5-140">命名的 LocalDB 实例为 "private";实例由负责创建和管理该实例的单个应用程序所拥有。</span><span class="sxs-lookup"><span data-stu-id="613d5-140">Named LocalDB instances are "private"; an instance is owned by a single application that is responsible for creating and managing the instance.</span></span> <span data-ttu-id="613d5-141">命名的 LocalDB 实例提供隔离并改进性能。</span><span class="sxs-lookup"><span data-stu-id="613d5-141">Named LocalDB instances provide isolation and improve performance.</span></span>  
  
### <a name="named-instance-creation"></a><span data-ttu-id="613d5-142">创建命名实例</span><span class="sxs-lookup"><span data-stu-id="613d5-142">Named Instance Creation</span></span>  
 <span data-ttu-id="613d5-143">用户必须通过 LocalDB 管理 API 显式创建命名实例，或通过托管应用程序的 app.config 文件隐式创建命名实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-143">The user must create named instances explicitly through the LocalDB management API, or implicitly through the app.config file for a managed application.</span></span> <span data-ttu-id="613d5-144">托管应用程序也可以使用 API。</span><span class="sxs-lookup"><span data-stu-id="613d5-144">A managed application may also use the API.</span></span>  
  
 <span data-ttu-id="613d5-145">每个命名实例都具有关联的 LocalDB 版本；也就是说，它指向指定的一组 LocalDB 二进制代码。</span><span class="sxs-lookup"><span data-stu-id="613d5-145">Each named instance has an associated LocalDB version; that is, it points to a specified set of LocalDB binaries.</span></span> <span data-ttu-id="613d5-146">命名实例的版本是在实例创建过程中设置的。</span><span class="sxs-lookup"><span data-stu-id="613d5-146">The version for the named instance is set during the instance creation process.</span></span>  
  
### <a name="named-instance-naming-rules"></a><span data-ttu-id="613d5-147">命名实例命名规则</span><span class="sxs-lookup"><span data-stu-id="613d5-147">Named Instance Naming Rules</span></span>  
 <span data-ttu-id="613d5-148">LocalDB 实例名称最多可包含 128 个字符（该限制由 `sysname` 数据类型指定）。</span><span class="sxs-lookup"><span data-stu-id="613d5-148">A LocalDB instance name can have up to a total of 128 characters (the limit is imposed by the `sysname` data type).</span></span> <span data-ttu-id="613d5-149">这与传统 SQL Server 实例名称相比有显著差异，后者限制为 16 个 ASCII 字符的 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="613d5-149">This is a significant difference compared to traditional SQL Server instance names, which are limited to NetBIOS names of 16 ASCII characters.</span></span> <span data-ttu-id="613d5-150">这种差异的原因是 LocalDB 将数据库视为文件，因此表示基于文件的语义，因此，用户可以更加自由地选择实例名称。</span><span class="sxs-lookup"><span data-stu-id="613d5-150">The reason for this difference is that LocalDB treats databases as files, and therefore implies file-based semantics, so it's intuitive for users to have more freedom in choosing instance names.</span></span>  
  
 <span data-ttu-id="613d5-151">LocalDB 实例名称可包含在文件名组分内合法的任何 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="613d5-151">A LocalDB instance name can contain any Unicode characters that are legal within the filename component.</span></span> <span data-ttu-id="613d5-152">文件名组件中的非法字符通常包含以下字符： ASCII/Unicode 字符1到31、引号 ( ") 、小于 (\<), greater than (>) 、管道 (|) 、退格 ( \b) 、tab ( \t) 、冒号 (： ) 、星号 ( \* ) 、问号 (？ ) 、反斜杠 () 、问号 ( \\ /) 。</span><span class="sxs-lookup"><span data-stu-id="613d5-152">Illegal characters in a filename component generally include the following characters: ASCII/Unicode characters 1 through 31, as well as quote ("), less than (\<), greater than (>), pipe (|), backspace (\b), tab (\t), colon (:), asterisk (\*), question mark (?), backslash (\\), and forward slash (/).</span></span> <span data-ttu-id="613d5-153">请注意，允许使用 Null 字符 (\ 0)，因为它用于终止字符串；第一个 Null 字符之后的任何字符都将忽略。</span><span class="sxs-lookup"><span data-stu-id="613d5-153">Note that the null character (\0) is allowed because it is used for string termination; everything after the first null character will be ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="613d5-154">非法字符列表取决于操作系统，并且可能在将来的版本中更改。</span><span class="sxs-lookup"><span data-stu-id="613d5-154">The list of illegal characters may depend on the operating system and may change in future releases.</span></span>  
  
 <span data-ttu-id="613d5-155">实例名称中的前导和尾随空格都将被忽略，并将进行修整。</span><span class="sxs-lookup"><span data-stu-id="613d5-155">Leading and trailing white spaces in instance names are ignored and will be trimmed.</span></span>  
  
 <span data-ttu-id="613d5-156">若要避免命名冲突，命名 LocalDB 实例的名称不能遵循自动实例的命名模式，如前面的 "自动实例命名规则" 中所述。</span><span class="sxs-lookup"><span data-stu-id="613d5-156">To avoid naming conflicts, named LocalDB instances cannot have a name that follows the naming pattern for automatic instances, as described earlier in "Automatic Instance Naming Rules."</span></span> <span data-ttu-id="613d5-157">尝试使用遵循自动实例命名模式的名称创建命名实例会有效地创建默认实例。</span><span class="sxs-lookup"><span data-stu-id="613d5-157">An attempt to create a named instance with a name that follows the automatic instance naming pattern effectively creates a default instance.</span></span>  
  
## <a name="sql-server-express-localdb-reference-topics"></a><span data-ttu-id="613d5-158">SQL Server Express LocalDB 参考主题</span><span class="sxs-lookup"><span data-stu-id="613d5-158">SQL Server Express LocalDB Reference Topics</span></span>  
 [<span data-ttu-id="613d5-159">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="613d5-159">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
 <span data-ttu-id="613d5-160">提供用于查找 LocalDB 实例 API 的头文件信息和注册表项。</span><span class="sxs-lookup"><span data-stu-id="613d5-160">Provides header file information and registry keys for finding the LocalDB instance API.</span></span>  
  
 [<span data-ttu-id="613d5-161">命令行管理工具：SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="613d5-161">Command-Line Management Tool: SqlLocalDB.exe</span></span>](command-line-management-tool-sqllocaldb-exe.md)  
 <span data-ttu-id="613d5-162">介绍 SqlLocalDB.exe，这是一个从命令行管理 LocalDB 实例的工具。</span><span class="sxs-lookup"><span data-stu-id="613d5-162">Describes SqlLocalDB.exe, a tool for managing LocalDB instances from the command line.</span></span>  
  
 [<span data-ttu-id="613d5-163">LocalDBCreateInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-163">LocalDBCreateInstance Function</span></span>](localdbcreateinstance-function.md)  
 <span data-ttu-id="613d5-164">描述创建新的 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-164">Describes the function to create a new LocalDB instance.</span></span>  
  
 [<span data-ttu-id="613d5-165">LocalDBDeleteInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-165">LocalDBDeleteInstance Function</span></span>](localdbdeleteinstance-function.md)  
 <span data-ttu-id="613d5-166">描述删除 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-166">Describes the function to remove a LocalDB instance.</span></span>  
  
 [<span data-ttu-id="613d5-167">LocalDBFormatMessage 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-167">LocalDBFormatMessage Function</span></span>](localdbformatmessage-function.md)  
 <span data-ttu-id="613d5-168">描述返回 LocalDB 错误的本地化说明的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-168">Describes the function to return the localized description for a LocalDB error.</span></span>  
  
 [<span data-ttu-id="613d5-169">LocalDBGetInstanceInfo 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-169">LocalDBGetInstanceInfo Function</span></span>](localdbgetinstanceinfo-function.md)  
 <span data-ttu-id="613d5-170">描述获取有关 LocalDB 实例的信息的函数，如该实例是否存在、版本信息、是否正在运行等。</span><span class="sxs-lookup"><span data-stu-id="613d5-170">Describes the function to get information for a LocalDB instance, such as whether it exists, version information, whether it is running, and so on.</span></span>  
  
 [<span data-ttu-id="613d5-171">LocalDBGetInstances 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-171">LocalDBGetInstances Function</span></span>](localdbgetinstances-function.md)  
 <span data-ttu-id="613d5-172">描述返回具有指定版本的所有 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-172">Describes the function to return all the LocalDB instances with a specified version.</span></span>  
  
 [<span data-ttu-id="613d5-173">LocalDBGetVersionInfo 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-173">LocalDBGetVersionInfo Function</span></span>](localdbgetversioninfo-function.md)  
 <span data-ttu-id="613d5-174">描述返回指定的 LocalDB 版本的信息的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-174">Describes the function to return information for a specified LocalDB version.</span></span>  
  
 [<span data-ttu-id="613d5-175">LocalDBGetVersions 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-175">LocalDBGetVersions Function</span></span>](localdbgetversions-function.md)  
 <span data-ttu-id="613d5-176">描述返回计算机上可用的所有 LocalDB 版本的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-176">Describes the function to return all LocalDB versions available on a computer.</span></span>  
  
 [<span data-ttu-id="613d5-177">LocalDBShareInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-177">LocalDBShareInstance Function</span></span>](localdbshareinstance-function.md)  
 <span data-ttu-id="613d5-178">描述共享指定的 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-178">Describes the function to share a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="613d5-179">LocalDBStartInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-179">LocalDBStartInstance Function</span></span>](localdbstartinstance-function.md)  
 <span data-ttu-id="613d5-180">描述启动指定的 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-180">Describes the function to start a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="613d5-181">LocalDBStartTracing 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-181">LocalDBStartTracing Function</span></span>](localdbstarttracing-function.md)  
 <span data-ttu-id="613d5-182">描述为用户启用 API 跟踪的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-182">Describes the function to enable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="613d5-183">LocalDBStopInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-183">LocalDBStopInstance Function</span></span>](localdbstopinstance-function.md)  
 <span data-ttu-id="613d5-184">描述停止指定的 LocalDB 实例运行的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-184">Describes the function to stop a specified LocalDB instance from running.</span></span>  
  
 [<span data-ttu-id="613d5-185">LocalDBStopTracing 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-185">LocalDBStopTracing Function</span></span>](localdbstoptracing-function.md)  
 <span data-ttu-id="613d5-186">描述为用户禁用 API 跟踪的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-186">Describes the function to disable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="613d5-187">LocalDBUnshareInstance 函数</span><span class="sxs-lookup"><span data-stu-id="613d5-187">LocalDBUnshareInstance Function</span></span>](localdbunshareinstance-function.md)  
 <span data-ttu-id="613d5-188">描述停止共享指定的 LocalDB 实例的函数。</span><span class="sxs-lookup"><span data-stu-id="613d5-188">Describes the function to stop sharing a specified LocalDB instance.</span></span>  
  
  
