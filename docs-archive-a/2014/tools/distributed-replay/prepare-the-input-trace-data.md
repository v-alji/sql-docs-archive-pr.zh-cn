---
title: 准备输入跟踪数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c14fd3d2-5770-47c2-a851-cc13ddbc9bf5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c13dddcf29f93940fa4eae6b2849dcfb278ae3b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690980"
---
# <a name="prepare-the-input-trace-data"></a><span data-ttu-id="8cf88-102">准备输入跟踪数据</span><span class="sxs-lookup"><span data-stu-id="8cf88-102">Prepare the Input Trace Data</span></span>
  <span data-ttu-id="8cf88-103">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 功能开始分布式重播之前，必须先从 Distributed Replay 管理工具启动预处理阶段以准备输入跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="8cf88-103">Before you can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature, you must prepare the input trace data by initiating the preprocess stage from the distributed replay administration tool.</span></span> <span data-ttu-id="8cf88-104">在预处理阶段，分布式重播控制器处理跟踪数据并生成一个中间文件：</span><span class="sxs-lookup"><span data-stu-id="8cf88-104">In the preprocess stage, the distributed replay controller processes the trace data and generates an intermediate file:</span></span>  
  
 <span data-ttu-id="8cf88-105">![Distributed Replay 预处理阶段](../../database-engine/media/preprocess.gif "Distributed Replay 预处理阶段")</span><span class="sxs-lookup"><span data-stu-id="8cf88-105">![Distributed replay preprocess stage](../../database-engine/media/preprocess.gif "Distributed replay preprocess stage")</span></span>  
  
 <span data-ttu-id="8cf88-106">有关预处理阶段的详细信息，请参阅 [SQL Server Distributed Replay](sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf88-106">For more information about the preprocess stage, see [SQL Server Distributed Replay](sql-server-distributed-replay.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cf88-107">输入跟踪数据必须在与分布式重播兼容的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中捕获。</span><span class="sxs-lookup"><span data-stu-id="8cf88-107">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="8cf88-108">输入跟踪数据还必须与要对其重播跟踪数据的目标服务器兼容。</span><span class="sxs-lookup"><span data-stu-id="8cf88-108">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="8cf88-109">有关版本要求的详细信息，请参阅 [Distributed Replay Requirements](distributed-replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf88-109">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-prepare-the-input-trace-data"></a><span data-ttu-id="8cf88-110">准备输入跟踪数据</span><span class="sxs-lookup"><span data-stu-id="8cf88-110">To prepare the input trace data</span></span>  
  
1.  <span data-ttu-id="8cf88-111">**（可选）修改预处理配置设置**：若要修改预处理配置设置（例如，是否筛选系统会话或配置最长空闲时间），必须修改基于 XML 的预处理配置文件 `DReplay.exe.preprocess.config` 的 `<PreprocessModifiers>` 元素。</span><span class="sxs-lookup"><span data-stu-id="8cf88-111">**(Optional) Modify preprocess configuration settings**: If you want to modify the preprocess configuration settings, such as whether to filter system sessions or to configure the maximum idle time, you must modify the `<PreprocessModifiers>` element of the XML-based preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span> <span data-ttu-id="8cf88-112">在修改预处理配置文件时，建议您修改副本而非原始文件。</span><span class="sxs-lookup"><span data-stu-id="8cf88-112">If you modify the preprocess configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="8cf88-113">若要修改设置，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8cf88-113">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8cf88-114">制作默认预处理配置文件 `DReplay.exe.preprocess.config`的副本并重命名此新文件。</span><span class="sxs-lookup"><span data-stu-id="8cf88-114">Make a copy of the default preprocess configuration file, `DReplay.exe.preprocess.config`, and rename the new file.</span></span> <span data-ttu-id="8cf88-115">默认预处理配置文件位于管理工具安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="8cf88-115">The default preprocess configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="8cf88-116">在新配置文件中修改预处理配置设置。</span><span class="sxs-lookup"><span data-stu-id="8cf88-116">Modify the preprocess configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="8cf88-117">启动预处理阶段（下一步）时，使用 *preprocess* 选项的 **config_file** 参数指定修改过的配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="8cf88-117">When initiating the preprocess stage (the next step), use the *config_file* parameter of the **preprocess** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="8cf88-118">有关预处理配置文件的详细信息，请参阅 [配置 Distributed Replay](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf88-118">For more information about the preprocess configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="8cf88-119">**启动预处理阶段**：若要准备输入跟踪数据，必须使用“预处理”选项运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="8cf88-119">**Initiate the preprocess stage**: To prepare the input trace data, you must run the administration tool with the **preprocess** option.</span></span> <span data-ttu-id="8cf88-120">有关详细信息，请参阅[预处理选项（Distributed Replay 管理工具）](preprocess-option-distributed-replay-administration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf88-120">For more information, see [Preprocess Option &#40;Distributed Replay Administration Tool&#41;](preprocess-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="8cf88-121">打开 Windows 命令提示符实用工具 (`CMD.exe`)，然后导航到分布式重播管理工具 (`DReplay.exe`) 的安装位置。</span><span class="sxs-lookup"><span data-stu-id="8cf88-121">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="8cf88-122">（可选）如果控制器服务不是在运行管理工具的计算机上运行，则使用 *controller* 参数 **-m**指定控制器。</span><span class="sxs-lookup"><span data-stu-id="8cf88-122">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="8cf88-123">使用 *input_trace_file* 参数 **-i**指定输入跟踪文件的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="8cf88-123">Use the *input_trace_file* parameter, **-i**, to specify the location and name of the input trace files.</span></span>  
  
    4.  <span data-ttu-id="8cf88-124">使用 *controller_working_directory* 参数 **-d**指定中间文件应保存在控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="8cf88-124">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file should be saved on the controller.</span></span>  
  
    5.  <span data-ttu-id="8cf88-125">（可选）使用 *config_file* 参数 **-c**指定预处理配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="8cf88-125">(Optional) Use the *config_file* parameter, **-c**, to specify location of the preprocess configuration file.</span></span> <span data-ttu-id="8cf88-126">如果您修改了默认预处理配置文件的副本，则使用此参数来指向新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="8cf88-126">Use this parameter to point to the new configuration file if you have modified a copy of the default preprocess configuration file.</span></span>  
  
    6.  <span data-ttu-id="8cf88-127">（可选）使用 *status_interval* 参数 **-f**指定是否希望管理工具以 30 秒之外的其他频率显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="8cf88-127">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency different than 30 seconds.</span></span>  
  
     <span data-ttu-id="8cf88-128">例如，在与控制器服务相同的计算机上为位于 `c:\trace1.trc`中的跟踪文件、位于 `c:\WorkingDir` 中的控制器工作目录以及在默认 30 秒时显示的状态消息启动预处理阶段时，需要使用以下语法： `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span><span class="sxs-lookup"><span data-stu-id="8cf88-128">For example, initiating the preprocess stage on the same computer as the controller service, for a trace file located at `c:\trace1.trc`, a controller working directory located at `c:\WorkingDir` , and a status message displayed at the default value of 30 seconds, requires the syntax: `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span></span>  
  
3.  <span data-ttu-id="8cf88-129">预处理阶段完成后，中间文件将存储在控制器的工作目录中。</span><span class="sxs-lookup"><span data-stu-id="8cf88-129">After the preprocess stage is complete, the intermediate file is stored in the controller working directory.</span></span> <span data-ttu-id="8cf88-130">若要启动事件重播阶段，必须使用 **replay** 选项运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="8cf88-130">To initiate the event replay stage, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="8cf88-131">有关详细信息，请参阅 [重播跟踪数据](replay-trace-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf88-131">For more information, see [Replay Trace Data](replay-trace-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf88-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cf88-132">See Also</span></span>  
 <span data-ttu-id="8cf88-133">[SQL Server 分布式重播](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="8cf88-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="8cf88-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="8cf88-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="8cf88-135">[管理工具命令行选项（Distributed Replay 实用工具）](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8cf88-135">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="8cf88-136">配置 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="8cf88-136">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
