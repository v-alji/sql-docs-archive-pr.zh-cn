---
title: 预处理选项（Distributed Replay 管理工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7f168d45b03473d958e202bd75116f4519d2fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579924"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a><span data-ttu-id="9980a-102">preprocess 选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="9980a-102">Preprocess Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="9980a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是一个命令行工具，可用于与 Distributed Replay 控制器进行通信。</span><span class="sxs-lookup"><span data-stu-id="9980a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="9980a-104">本主题介绍 **preprocess** 命令行选项和相应的语法。</span><span class="sxs-lookup"><span data-stu-id="9980a-104">This topic describes the **preprocess** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="9980a-105">**preprocess** 选项用于启动预处理阶段。</span><span class="sxs-lookup"><span data-stu-id="9980a-105">The **preprocess** option initiates the preprocess stage.</span></span> <span data-ttu-id="9980a-106">在此阶段，控制器会准备对针对目标服务器进行重播的输入跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="9980a-106">During this stage, the controller prepares the input trace data for replay against the target server.</span></span>

 <span data-ttu-id="9980a-107">![主题链接图标](../../database-engine/media/topic-link.gif "“主题链接”图标") 有关与此管理工具语法结合使用的语法约定的详细信息，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9980a-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="9980a-108">语法</span><span class="sxs-lookup"><span data-stu-id="9980a-108">Syntax</span></span>

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="9980a-109">参数</span><span class="sxs-lookup"><span data-stu-id="9980a-109">Parameters</span></span>
 <span data-ttu-id="9980a-110">**-m** *控制器*指定控制器的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="9980a-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="9980a-111">可以用“`localhost`”或“`.`”指代本地计算机。</span><span class="sxs-lookup"><span data-stu-id="9980a-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="9980a-112">如果未指定 **-m** 参数，则使用本地计算机。</span><span class="sxs-lookup"><span data-stu-id="9980a-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="9980a-113">**-i** *input_trace_file*指定控制器上输入跟踪文件的完整路径，例如 `D:\Mytrace.trc` 。</span><span class="sxs-lookup"><span data-stu-id="9980a-113">**-i** *input_trace_file* Specifies the full path of the input trace file on the controller, such as `D:\Mytrace.trc`.</span></span> <span data-ttu-id="9980a-114">**-i** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9980a-114">The **-i** parameter is required.</span></span>

 <span data-ttu-id="9980a-115">如果同一目录中存在滚动更新文件，则会自动加载并使用这些文件。</span><span class="sxs-lookup"><span data-stu-id="9980a-115">If there are rollover files in the same directory, they will be loaded and used automatically.</span></span> <span data-ttu-id="9980a-116">文件必须遵循文件滚动更新命名约定，例如：`Mytrace.trc`、`Mytrace_1.trc`、`Mytrace_2.trc`、`Mytrace_3.trc`…`Mytrace_n.trc`。</span><span class="sxs-lookup"><span data-stu-id="9980a-116">The files must follow the file rollover naming convention, for example: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.</span></span>

> [!NOTE]
>  <span data-ttu-id="9980a-117">如果要在控制器以外的其他计算机上使用管理工具，则需要将输入跟踪文件复制到控制器上，以便可以对此参数使用本地路径。</span><span class="sxs-lookup"><span data-stu-id="9980a-117">If you are using the administration tool on a different computer than the controller, you will need to copy the input trace files to the controller so that a local path can be used for this parameter.</span></span>

 <span data-ttu-id="9980a-118">**-d** *controller_working_dir*指定控制器上用于存储中间文件的目录。</span><span class="sxs-lookup"><span data-stu-id="9980a-118">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="9980a-119">**-d** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9980a-119">The **-d** parameter is required.</span></span>

 <span data-ttu-id="9980a-120">需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="9980a-120">The following requirements apply:</span></span>

-   <span data-ttu-id="9980a-121">目录必须位于控制器上。</span><span class="sxs-lookup"><span data-stu-id="9980a-121">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="9980a-122">必须指定以驱动器号开头（例如 `c:\WorkingDir`）的完整路径。</span><span class="sxs-lookup"><span data-stu-id="9980a-122">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="9980a-123">路径不能以反斜杠“`\`”结尾。</span><span class="sxs-lookup"><span data-stu-id="9980a-123">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="9980a-124">不支持 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="9980a-124">UNC paths are not supported.</span></span>

 <span data-ttu-id="9980a-125">**-c** *config_file*是预处理配置文件的完整路径;当预处理配置文件存储在其他位置时，用于指定预处理配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="9980a-125">**-c** *config_file* Is the full path of the preprocess configuration file; used to specify the location of the preprocess configuration file when stored in a different location.</span></span> <span data-ttu-id="9980a-126">此参数可以是 UNC 路径，也可以是您运行管理工具的计算机上的本地路径。</span><span class="sxs-lookup"><span data-stu-id="9980a-126">This parameter can be a UNC path, or can reside locally on the computer where you run the administration tool.</span></span>

 <span data-ttu-id="9980a-127">如果不需要筛选，或者不想修改最大空闲时间，则 **-c** 参数不是必需的。</span><span class="sxs-lookup"><span data-stu-id="9980a-127">The **-c** parameter is not required if no filtering is needed, or if you do not want to modify the maximum idle time.</span></span>

 <span data-ttu-id="9980a-128">如果不使用 **-c** 参数，将使用默认预处理配置文件 `DReplay.exe.preprocess.config`。</span><span class="sxs-lookup"><span data-stu-id="9980a-128">Without the **-c** parameter, the default preprocess configuration file, `DReplay.exe.preprocess.config`, is used.</span></span>

 <span data-ttu-id="9980a-129">**-f** *status_interval*指定显示状态消息) 的频率 (以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="9980a-129">**-f** *status_interval* Specifies the frequency (in seconds) at which to display status messages.</span></span>

 <span data-ttu-id="9980a-130">如果未指定 **-f** ，则默认间隔为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="9980a-130">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="9980a-131">示例</span><span class="sxs-lookup"><span data-stu-id="9980a-131">Examples</span></span>
 <span data-ttu-id="9980a-132">在本示例中，预处理阶段采用所有默认设置启动。</span><span class="sxs-lookup"><span data-stu-id="9980a-132">In this example, the preprocess stage is initiated with all of the default settings.</span></span> <span data-ttu-id="9980a-133">值 `localhost` 表示控制器服务与管理工具在同一计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="9980a-133">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span> <span data-ttu-id="9980a-134">*Input_trace_file* 参数指定输入跟踪数据的位置 `c:\mytrace.trc`。</span><span class="sxs-lookup"><span data-stu-id="9980a-134">The *input_trace_file* parameter specifies the location of the input trace data, `c:\mytrace.trc`.</span></span> <span data-ttu-id="9980a-135">由于不涉及跟踪文件筛选，因此必须指定 **-c** 参数。</span><span class="sxs-lookup"><span data-stu-id="9980a-135">Because there is no trace file filtering involved, the **-c** parameter does have to be specified.</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 <span data-ttu-id="9980a-136">在本示例中，启动了预处理阶段并指定了修改过的预处理配置文件。</span><span class="sxs-lookup"><span data-stu-id="9980a-136">In this example, the preprocess stage is initiated and a modified preprocess configuration file is specified.</span></span> <span data-ttu-id="9980a-137">与前面的示例不同， **-c** 参数用于指向修改过的配置文件（如果你将该文件存储在其他位置）。</span><span class="sxs-lookup"><span data-stu-id="9980a-137">Unlike the previous example, the **-c** parameter is used to point to the modified configuration file, if you have stored it in a different location.</span></span> <span data-ttu-id="9980a-138">例如：</span><span class="sxs-lookup"><span data-stu-id="9980a-138">For example:</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 <span data-ttu-id="9980a-139">在修改过的预处理配置文件中，添加了筛选条件以在分布式重播期间筛选掉系统会话。</span><span class="sxs-lookup"><span data-stu-id="9980a-139">In the modified preprocess configuration file, a filter condition is added that filters out system sessions during distributed replay.</span></span> <span data-ttu-id="9980a-140">可通过修改预处理配置文件 `<PreprocessModifiers>` 中的 `DReplay.exe.preprocess.config`元素来添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="9980a-140">The filter is added by modifying the `<PreprocessModifiers>` element in the preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span>

 <span data-ttu-id="9980a-141">下面是修改过的配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="9980a-141">The following shows an example of the modified configuration file:</span></span>

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="9980a-142">权限</span><span class="sxs-lookup"><span data-stu-id="9980a-142">Permissions</span></span>
 <span data-ttu-id="9980a-143">您必须作为交互用户、本地用户或域用户帐户运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="9980a-143">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="9980a-144">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="9980a-144">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="9980a-145">有关详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="9980a-145">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9980a-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9980a-146">See Also</span></span>
 <span data-ttu-id="9980a-147">[Distributed Replay](sql-server-distributed-replay.md) [配置](configure-distributed-replay.md)SQL Server[准备输入跟踪数据](prepare-the-input-trace-data.md)Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="9980a-147">[Prepare the Input Trace Data](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md)</span></span>


