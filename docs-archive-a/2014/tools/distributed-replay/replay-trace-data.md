---
title: 重播跟踪数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 19ff5285-fb9d-4fd1-97c4-ec72c311c384
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6c929d7c617ba4dc496eedabaccbbe50da32d08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577986"
---
# <a name="replay-trace-data"></a><span data-ttu-id="0d6d4-102">重播跟踪数据</span><span class="sxs-lookup"><span data-stu-id="0d6d4-102">Replay Trace Data</span></span>
  <span data-ttu-id="0d6d4-103">准备好输入跟踪数据之后，可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 功能启动分布式重播。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-103">You can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature after you have prepared the input trace data.</span></span> <span data-ttu-id="0d6d4-104">有关详细信息，请参阅 [准备输入跟踪数据](prepare-the-input-trace-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-104">For more information, see [Prepare the Input Trace Data](prepare-the-input-trace-data.md).</span></span>  
  
 <span data-ttu-id="0d6d4-105">使用管理工具 **replay** 选项启动分布式重播的事件重播阶段。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-105">Use the administration tool **replay** option to initiate the event replay stage of the distributed replay.</span></span> <span data-ttu-id="0d6d4-106">此阶段包含两个部分：跟踪数据调度和分布式重播的启动与同步。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-106">This stage consists of two parts: the trace data dispatch and the starting and synchronizing of the distributed replay.</span></span>  
  
 <span data-ttu-id="0d6d4-107">![分布式事件重播](../../database-engine/media/eventreplay.gif "分布式事件重播")</span><span class="sxs-lookup"><span data-stu-id="0d6d4-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span></span>  
  
 <span data-ttu-id="0d6d4-108">您可以以两种顺序模式之一重播跟踪数据：压力模式或同步模式。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-108">You can replay trace data in one of two sequencing modes: stress mode or synchronization mode.</span></span> <span data-ttu-id="0d6d4-109">默认行为是在压力模式下重播跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-109">The default behavior is to replay trace data in stress mode.</span></span> <span data-ttu-id="0d6d4-110">有关事件重播阶段和顺序模式的详细信息，请参阅 [SQL Server Distributed Replay](sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-110">For more information about the event replay stage and sequencing modes, see [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d6d4-111">输入跟踪数据必须在与分布式重播兼容的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中捕获。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-111">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="0d6d4-112">输入跟踪数据还必须与要对其重播跟踪数据的目标服务器兼容。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-112">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="0d6d4-113">有关版本要求的详细信息，请参阅 [Distributed Replay Requirements](distributed-replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-113">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-replay-the-trace"></a><span data-ttu-id="0d6d4-114">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="0d6d4-114">To replay the trace</span></span>  
  
1.  <span data-ttu-id="0d6d4-115">**（可选）修改重播配置设置**：若要修改重播配置设置（如排序模式和各种缩放值），必须修改基于 XML 的重播配置文件 `DReplay.exe.replay.config` 的 `<ReplayOptions>` 元素。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-115">**(Optional) Modify replay configuration settings**: If you want to modify the replay configuration settings, such as the sequencing mode and various scaling values, you must modify the `<ReplayOptions>` element of the XML-based replay configuration file `DReplay.exe.replay.config`.</span></span> <span data-ttu-id="0d6d4-116">还可以修改 `<OutputOptions>` 元素以指定输出设置，例如是否记录行计数。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-116">You can also modify the `<OutputOptions>` element to specify output settings, such as whether to record the row count.</span></span> <span data-ttu-id="0d6d4-117">如果要修改重播配置文件，建议您修改副本而非原始版本。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-117">If you modify the replay configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="0d6d4-118">若要修改设置，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="0d6d4-118">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="0d6d4-119">制作默认重播配置文件 `DReplay.exe.replay.config`的副本并重命名此新文件。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-119">Make a copy of the default replay configuration file, `DReplay.exe.replay.config`, and rename the new file.</span></span> <span data-ttu-id="0d6d4-120">默认重播配置文件位于管理工具安装文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-120">The default replay configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="0d6d4-121">在新的配置文件中修改重播配置设置。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-121">Modify the replay configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="0d6d4-122">启动事件重播阶段（下一步）时，使用“重播”选项的 *config_file* 参数指定修改后的配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-122">When initiating the event replay stage (the next step), use the *config_file* parameter of the **replay** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="0d6d4-123">有关重播配置文件的详细信息，请参阅 [配置分布式重播](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-123">For more information about the replay configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="0d6d4-124">**启动事件重播阶段**：若要启动分布式重播，必须使用 replay 选项运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-124">**Initiate the event replay stage**: To start the distributed replay, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="0d6d4-125">有关详细信息，请参阅[重播选项（分布式重播管理工具）](replay-option-distributed-replay-administration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-125">For more information, see [Replay Option &#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="0d6d4-126">打开 Windows 命令提示符实用工具 (`CMD.exe`)，然后导航到分布式重播管理工具 (`DReplay.exe`) 的安装位置。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-126">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="0d6d4-127">（可选）如果控制器服务不是在运行管理工具的计算机上运行，则使用 *controller* 参数 **-m**指定控制器。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-127">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="0d6d4-128">使用 *controller_working_directory* 参数 **-d**指定在预处理阶段，中间文件在控制器上的保存位置。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-128">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file was saved on the controller during the preprocess stage.</span></span>  
  
    4.  <span data-ttu-id="0d6d4-129">（可选）使用 **-o** 参数捕获每个客户端上结果跟踪文件中的重播活动。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-129">(Optional) Use the **-o** parameter to capture the replay activity in a result trace file on each client.</span></span>  
  
    5.  <span data-ttu-id="0d6d4-130">（可选）使用 *target_server* 参数 **-s**指定分布式重播客户端应在其中重播跟踪工作负荷的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-130">(Optional) Use the *target_server* parameter, **-s**, to specify the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where the distributed replay clients should replay the trace workload.</span></span> <span data-ttu-id="0d6d4-131">如果使用 `<Server>` 元素指定重播配置文件的 `<ReplayOptions>` 元素中的目标服务器，则此参数不是必需的。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-131">This parameter is not required if you used the `<Server>` element to specify the target server in the `<ReplayOptions>` element of the replay configuration file.</span></span>  
  
    6.  <span data-ttu-id="0d6d4-132">使用 *clients* 参数 **-w**指定应参与重播的分布式重播客户端。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-132">Use the *clients* parameter, **-w**, to specify the distributed replay clients that should participate in the replay.</span></span> <span data-ttu-id="0d6d4-133">列出客户端计算机名称，由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-133">List the client computer names, separated by commas.</span></span> <span data-ttu-id="0d6d4-134">注意：不允许使用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-134">Note: IP addresses are not allowed.</span></span>  
  
    7.  <span data-ttu-id="0d6d4-135">（可选）使用 *config_file* 参数 **-c**指定重播配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-135">(Optional) Use the *config_file* parameter, **-c**, to specify location of the replay configuration file.</span></span> <span data-ttu-id="0d6d4-136">如果您修改了默认重播配置文件的副本，则使用此参数来指向新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-136">Use this parameter to point to the new configuration file if you have modified a copy of the default replay configuration file.</span></span>  
  
    8.  <span data-ttu-id="0d6d4-137">（可选）使用 *status_interval* 参数 **-f**指定是否希望管理工具以 30 秒之外的其他频率显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-137">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency other than 30 seconds.</span></span>  
  
     <span data-ttu-id="0d6d4-138">例如，下面的语法在控制器服务所在的同一计算机上启动重播阶段，使用位于 `c:\WorkingDir`的控制器工作目录，捕获每个参与客户端上的重播活动，使用客户端 `client1` 和 `client2` 执行重播，并从位于 `c:\modifiedreplay.config`的经过修改的重播配置文件中获得其余的重播配置设置：</span><span class="sxs-lookup"><span data-stu-id="0d6d4-138">For example, the following syntax initiates the replay stage on the same computer as the controller service, uses a controller working directory located at `c:\WorkingDir`, captures the replay activity on each participating client, uses clients `client1` and `client2` to perform the replay, and obtains the remaining replay configuration settings from a modified replay configuration file located at `c:\modifiedreplay.config`:</span></span>  
  
     `dreplay replay -d c:\WorkingDir -o -w client1,client2 -c c:\modifiedreplay.config`  
  
3.  <span data-ttu-id="0d6d4-139">完成分布式重播时，管理工具将返回摘要信息。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-139">When the distributed replay has finished, the administration tool returns summary information.</span></span> <span data-ttu-id="0d6d4-140">如果指定 **-o** 选项，则重播活动已保存在每个客户端上的结果跟踪文件中。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-140">If you specified the **-o** option, the replay activity has been saved in result trace files on each client.</span></span> <span data-ttu-id="0d6d4-141">有关结果跟踪文件的详细信息，请参阅 [查看重播结果](review-the-replay-results.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d4-141">For more information about the result trace files, see [Review the Replay Results](review-the-replay-results.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6d4-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d6d4-142">See Also</span></span>  
 <span data-ttu-id="0d6d4-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="0d6d4-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="0d6d4-144">[管理工具命令行选项（Distributed Replay 实用工具）](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0d6d4-144">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="0d6d4-145">配置 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="0d6d4-145">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
