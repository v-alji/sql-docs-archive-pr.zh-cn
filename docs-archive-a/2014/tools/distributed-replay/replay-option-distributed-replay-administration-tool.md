---
title: 重播选项（Distributed Replay 管理工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693152"
---
# <a name="replay-option-distributed-replay-administration-tool"></a><span data-ttu-id="a044b-102">重播选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="a044b-102">Replay Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="a044b-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是一个命令行工具，可用于与 Distributed Replay 控制器进行通信。</span><span class="sxs-lookup"><span data-stu-id="a044b-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="a044b-104">本主题介绍 **replay** 命令行选项和相应的语法。</span><span class="sxs-lookup"><span data-stu-id="a044b-104">This topic describes the **replay** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="a044b-105">**replay** 选项启动事件重播阶段，在该阶段中，控制器将重播数据调度到指定客户端，启动分布式重播并同步客户端。</span><span class="sxs-lookup"><span data-stu-id="a044b-105">The **replay** option initiates the event replay stage, in which the controller dispatches replay data to the specified clients, launches the distributed replay and synchronizes the clients.</span></span> <span data-ttu-id="a044b-106">每个参与重播的客户端可以选择记录重播活动并在本地保存结果跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="a044b-106">Optionally, each client participating in the replay can record the replay activity and save a result trace file locally.</span></span>

 <span data-ttu-id="a044b-107">![主题链接图标](../../database-engine/media/topic-link.gif "“主题链接”图标") 有关与此管理工具语法结合使用的语法约定的详细信息，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a044b-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="a044b-108">语法</span><span class="sxs-lookup"><span data-stu-id="a044b-108">Syntax</span></span>

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="a044b-109">参数</span><span class="sxs-lookup"><span data-stu-id="a044b-109">Parameters</span></span>
 <span data-ttu-id="a044b-110">**-m** *控制器*指定控制器的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a044b-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="a044b-111">可以用“`localhost`”或“`.`”指代本地计算机。</span><span class="sxs-lookup"><span data-stu-id="a044b-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="a044b-112">如果未指定 **-m** 参数，则使用本地计算机。</span><span class="sxs-lookup"><span data-stu-id="a044b-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="a044b-113">**-d** *controller_working_dir*指定控制器上用于存储中间文件的目录。</span><span class="sxs-lookup"><span data-stu-id="a044b-113">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="a044b-114">**-d** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="a044b-114">The **-d** parameter is required.</span></span>

 <span data-ttu-id="a044b-115">需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="a044b-115">The following requirements apply:</span></span>

-   <span data-ttu-id="a044b-116">目录必须位于控制器上。</span><span class="sxs-lookup"><span data-stu-id="a044b-116">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="a044b-117">必须指定以驱动器号开头（例如 `c:\WorkingDir`）的完整路径。</span><span class="sxs-lookup"><span data-stu-id="a044b-117">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="a044b-118">路径不能以反斜杠“`\`”结尾。</span><span class="sxs-lookup"><span data-stu-id="a044b-118">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="a044b-119">不支持 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="a044b-119">UNC paths are not supported.</span></span>

 <span data-ttu-id="a044b-120">**-o**捕获客户端的重播活动，并将其保存到由 `<ResultDirectory>` 客户端配置文件中的元素指定的路径中的结果跟踪文件中 `DReplayClient.xml` 。</span><span class="sxs-lookup"><span data-stu-id="a044b-120">**-o** Captures the clients' replay activity and saves it to a result trace file in the path specified by the `<ResultDirectory>` element in the client configuration file, `DReplayClient.xml`.</span></span>

 <span data-ttu-id="a044b-121">如果 -o 参数未指定，结果跟踪文件就不会生成。</span><span class="sxs-lookup"><span data-stu-id="a044b-121">When the **-o** parameter is not specified, the result trace file is not generated.</span></span> <span data-ttu-id="a044b-122">在重播结束时，控制台输出将返回摘要信息，但不提供其他重播统计信息。</span><span class="sxs-lookup"><span data-stu-id="a044b-122">The console output returns summary information at the end of replay, but no other replay statistics are available.</span></span>

 <span data-ttu-id="a044b-123">**-s** *target_server*指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 应对其重播分布式工作负荷的目标实例。</span><span class="sxs-lookup"><span data-stu-id="a044b-123">**-s** *target_server* Specifies the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that the distributed workload should be replayed against.</span></span> <span data-ttu-id="a044b-124">必须以 **server_name[\instance name]** 格式指定此参数。</span><span class="sxs-lookup"><span data-stu-id="a044b-124">You must specify this parameter in the format **server_name[\instance name]**.</span></span>

 <span data-ttu-id="a044b-125">不能使用“`localhost`”或“`.`”作为目标服务器。</span><span class="sxs-lookup"><span data-stu-id="a044b-125">You cannot use "`localhost`" or "`.`" as the target server.</span></span>

 <span data-ttu-id="a044b-126">如果重播配置文件 **的** 部分指定了 `<Server>` 元素，则不需要 `<ReplayOptions>` -s `DReplay.exe.replay.config`参数。</span><span class="sxs-lookup"><span data-stu-id="a044b-126">The **-s** parameter is not required if the `<Server>` element is specified in the `<ReplayOptions>` section of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="a044b-127">如果使用 **-s** 参数，则将忽略重播配置文件 `<Server>` 部分中的 `<ReplayOptions>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a044b-127">If the **-s** parameter is used, the `<Server>` element in the `<ReplayOptions>` section of the replay configuration file will be ignored.</span></span>

 <span data-ttu-id="a044b-128">**-w** *客户端*此必需的参数是一个逗号分隔的列表， (不含空格的) 指定应参与分布式重播的客户端的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a044b-128">**-w** *clients* This required parameter is a comma-separated list (without spaces) that specifies the computer names of clients that should participate in the distributed replay.</span></span> <span data-ttu-id="a044b-129">不允许使用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a044b-129">IP addresses are not allowed.</span></span> <span data-ttu-id="a044b-130">注意，客户端必须已向控制器注册。</span><span class="sxs-lookup"><span data-stu-id="a044b-130">Be aware that the clients must already be registered with the controller.</span></span>

> [!NOTE]
>  <span data-ttu-id="a044b-131">当客户端服务启动时，每个客户端都向客户端配置文件中指定的控制器注册。</span><span class="sxs-lookup"><span data-stu-id="a044b-131">Each client registers with the controller that is specified in the client configuration file when the client service starts.</span></span>

 <span data-ttu-id="a044b-132">**-c** *config_file*是重播配置文件的完整路径;用于指定存储在其他位置的位置。</span><span class="sxs-lookup"><span data-stu-id="a044b-132">**-c** *config_file* Is the full path of the replay configuration file; used to specify the location when it is stored in a different location.</span></span>

 <span data-ttu-id="a044b-133">若要使用重播配置文件 **的默认值，则不需要** -c `DReplay.exe.replay.config`参数。</span><span class="sxs-lookup"><span data-stu-id="a044b-133">The **-c** parameter is not required if you want to use the default values of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="a044b-134">**-f** *status_interval*指定显示状态的频率 (以秒为) 单位）。</span><span class="sxs-lookup"><span data-stu-id="a044b-134">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="a044b-135">如果未指定 **-f** ，则默认间隔为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="a044b-135">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="a044b-136">示例</span><span class="sxs-lookup"><span data-stu-id="a044b-136">Examples</span></span>
 <span data-ttu-id="a044b-137">在本例中，分布式重播从修改的重播配置文件 `DReplay.exe.replay.config`派生其大部分行为。</span><span class="sxs-lookup"><span data-stu-id="a044b-137">In this example, the distributed replay derives much of its behavior from a modified replay configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="a044b-138">**-m** 参数指定名为 `controller1` 的计算机充当控制器。</span><span class="sxs-lookup"><span data-stu-id="a044b-138">The **-m** parameter specifies that a computer named `controller1` acts as the controller.</span></span> <span data-ttu-id="a044b-139">当控制器服务在另一台计算机上运行时，必须指定计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a044b-139">The computer name must be specified when the controller service is running on a different computer.</span></span>

-   <span data-ttu-id="a044b-140">**-d** 参数指定中间文件在控制器上的位置 `c:\WorkingDir`。</span><span class="sxs-lookup"><span data-stu-id="a044b-140">The **-d** parameter specifies the location of the intermediate file on the controller, `c:\WorkingDir`.</span></span>

-   <span data-ttu-id="a044b-141">**-o** 参数指定每个指定的客户端捕获重播活动并将其保存到结果跟踪文件中。</span><span class="sxs-lookup"><span data-stu-id="a044b-141">The **-o** parameter specifies that each specified client capture the replay activity and save it to a result trace file.</span></span> <span data-ttu-id="a044b-142">注意：可使用配置文件中的 `<ResultTrace>` 元素指定是否记录行计数和结果集。</span><span class="sxs-lookup"><span data-stu-id="a044b-142">Note: The `<ResultTrace>` element in the configuration file can be used to specify if row count and result set be recorded.</span></span>

-   <span data-ttu-id="a044b-143">**-w** 参数指定计算机 `client1` 到 `client4` 作为客户端参与分布式重播。</span><span class="sxs-lookup"><span data-stu-id="a044b-143">The **-w** parameter specifies that computers `client1` through `client4` participate as clients in the distributed replay.</span></span>

-   <span data-ttu-id="a044b-144">**-c** 参数用来指向修改过的配置文件 `DReplay.exe.replay.config`。</span><span class="sxs-lookup"><span data-stu-id="a044b-144">The **-c** parameter is used to point to the modified configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="a044b-145">因为重播配置文件 **的** 元素中指定了 `<Server>` 元素，所以不需要 `<ReplayOptions>` -s `DReplay.exe.replay.config`参数。</span><span class="sxs-lookup"><span data-stu-id="a044b-145">The **-s** parameter is not required because the `<Server>` element is specified in the `<ReplayOptions>` element of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="a044b-146">当管理工具从不是控制器的计算机运行时，使用下面的语法启动事件重播阶段：</span><span class="sxs-lookup"><span data-stu-id="a044b-146">The event replay stage is initiated with the following syntax, when the administration tool is run from a different computer than the controller:</span></span>

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 <span data-ttu-id="a044b-147">若要指定同步顺序模式，应将 `<SequencingMode>` 文件的 `DReplay.exe.replay.config` 元素设置为与 `synchronization`值相等。</span><span class="sxs-lookup"><span data-stu-id="a044b-147">To specify a synchronous sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `synchronization`.</span></span> <span data-ttu-id="a044b-148">重播配置文件的 `<ResultTrace>` 部分经过修改以指定记录行计数。</span><span class="sxs-lookup"><span data-stu-id="a044b-148">The `<ResultTrace>` section of the replay configuration file is modified to specify that row count be recorded.</span></span> <span data-ttu-id="a044b-149">以下 XML 示例显示了这些更改：</span><span class="sxs-lookup"><span data-stu-id="a044b-149">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 <span data-ttu-id="a044b-150">若要指定压力顺序模式，应将 `<SequencingMode>` 文件的 `DReplay.exe.replay.config` 元素设置为与 `stress`值相等。</span><span class="sxs-lookup"><span data-stu-id="a044b-150">To specify a stress sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `stress`.</span></span> <span data-ttu-id="a044b-151">`<ConnectTimeScale>` 和 `<ThinkTimeScale>` 元素设置为值 `50` （以指定 50%）。</span><span class="sxs-lookup"><span data-stu-id="a044b-151">The `<ConnectTimeScale>` and `<ThinkTimeScale>` elements are set to the value `50` (to specify 50 percent).</span></span> <span data-ttu-id="a044b-152">有关连接时间和思考时间的详细信息，请参阅 [Configure Distributed Replay](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="a044b-152">For more information about connect time and think time, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span> <span data-ttu-id="a044b-153">以下 XML 示例显示了这些更改：</span><span class="sxs-lookup"><span data-stu-id="a044b-153">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="a044b-154">权限</span><span class="sxs-lookup"><span data-stu-id="a044b-154">Permissions</span></span>
 <span data-ttu-id="a044b-155">您必须作为交互用户、本地用户或域用户帐户运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="a044b-155">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="a044b-156">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="a044b-156">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="a044b-157">有关详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a044b-157">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a044b-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a044b-158">See Also</span></span>
 <span data-ttu-id="a044b-159">[重播跟踪数据](replay-trace-data.md)[查看重播结果](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md)使用 Distributed Replay[配置 Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay 论坛](https://social.technet.microsoft.com/Forums/sl/sqldru/)[使用 SQL Server](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1) [负载测试 Distributed Replay 第2部分](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)</span><span class="sxs-lookup"><span data-stu-id="a044b-159">[Replay Trace Data](replay-trace-data.md) [Review the Replay Results](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay Forum](https://social.technet.microsoft.com/Forums/sl/sqldru/) [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span></span>


