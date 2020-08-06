---
title: 数据事件探查任务编辑器（常规页）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cfcdf472f817d3dd688a5f867ac74d46835ab91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587963"
---
# <a name="data-profiling-task-editor-general-page"></a><span data-ttu-id="0e409-102">数据事件探查任务编辑器（常规页）</span><span class="sxs-lookup"><span data-stu-id="0e409-102">Data Profiling Task Editor (General Page)</span></span>
  <span data-ttu-id="0e409-103">可以使用 **“数据事件探查任务编辑器”** 的 **“常规”** 页配置以下选项：</span><span class="sxs-lookup"><span data-stu-id="0e409-103">Use the **General** page of the **Data Profiling Task Editor** to configure the following options:</span></span>  
  
-   <span data-ttu-id="0e409-104">指定配置文件输出的目标。</span><span class="sxs-lookup"><span data-stu-id="0e409-104">Specify the destination for the profile output.</span></span>  
  
-   <span data-ttu-id="0e409-105">使用默认设置可简化对单个表或视图进行事件探查的任务。</span><span class="sxs-lookup"><span data-stu-id="0e409-105">Use the default settings to simplify the task of profiling a single table or view.</span></span>  
  
 <span data-ttu-id="0e409-106">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="0e409-106">For more information about how to use the Data Profiling task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="0e409-107">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="0e409-107">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
 <span data-ttu-id="0e409-108">**打开“数据事件探查任务编辑器”的“常规”页**</span><span class="sxs-lookup"><span data-stu-id="0e409-108">**To open the General page of the Data Profiling Task Editor**</span></span>  
  
1.  <span data-ttu-id="0e409-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开具有该数据事件探查任务的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="0e409-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that has the Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="0e409-110">在“控制流”  选项卡上，双击数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="0e409-110">On the **Control Flow** tab, double-click the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="0e409-111">在 **“数据事件探查任务编辑器”** 中，单击 **“常规”** 。</span><span class="sxs-lookup"><span data-stu-id="0e409-111">In the **Data Profiling Task Editor**, click **General**.</span></span>  
  
## <a name="data-profiling-options"></a><span data-ttu-id="0e409-112">数据事件探查选项</span><span class="sxs-lookup"><span data-stu-id="0e409-112">Data Profiling Options</span></span>  
 <span data-ttu-id="0e409-113">**超时**</span><span class="sxs-lookup"><span data-stu-id="0e409-113">**Timeout**</span></span>  
 <span data-ttu-id="0e409-114">指定一个秒数，在这段时间之后数据事件探查任务应超时并停止运行。</span><span class="sxs-lookup"><span data-stu-id="0e409-114">Specify the number of seconds after which the Data Profiling task should timeout and stop running.</span></span> <span data-ttu-id="0e409-115">默认值为 0，表示无超时。</span><span class="sxs-lookup"><span data-stu-id="0e409-115">The default value is 0, which indicates no timeout.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="0e409-116">目标选项</span><span class="sxs-lookup"><span data-stu-id="0e409-116">Destination Options</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0e409-117">输出文件可能包含有关数据库的敏感数据和数据库所包含的数据。</span><span class="sxs-lookup"><span data-stu-id="0e409-117">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="0e409-118">有关如何使此文件更加安全的建议，请参阅 [对包使用的文件的访问](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="0e409-118">For suggestions about how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="0e409-119">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="0e409-119">**DestinationType**</span></span>  
 <span data-ttu-id="0e409-120">指定将数据配置文件输出保存到文件，还是保存到变量：</span><span class="sxs-lookup"><span data-stu-id="0e409-120">Specify whether to save the data profile output to a file or a variable:</span></span>  
  
|<span data-ttu-id="0e409-121">值</span><span class="sxs-lookup"><span data-stu-id="0e409-121">Value</span></span>|<span data-ttu-id="0e409-122">说明</span><span class="sxs-lookup"><span data-stu-id="0e409-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e409-123">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="0e409-123">**FileConnection**</span></span>|<span data-ttu-id="0e409-124">将配置文件输出保存到文件，位置为文件连接管理器中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="0e409-124">Save the profile output to a file in the location that is specified in a File connection manager.</span></span><br /><br /> <span data-ttu-id="0e409-125">注意：请在“目标”选项中指定要使用的文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="0e409-125">Note: You specify which File connection manager to use in the **Destination** option.</span></span>|  
|<span data-ttu-id="0e409-126">**变量**</span><span class="sxs-lookup"><span data-stu-id="0e409-126">**Variable**</span></span>|<span data-ttu-id="0e409-127">将配置文件输出保存到包变量。</span><span class="sxs-lookup"><span data-stu-id="0e409-127">Save the profile output to a package variable.</span></span><br /><br /> <span data-ttu-id="0e409-128">注意：请在“目标”选项中指定要使用的包变量。</span><span class="sxs-lookup"><span data-stu-id="0e409-128">Note: You specify which package variable to use in the **Destination** option.</span></span>|  
  
 <span data-ttu-id="0e409-129">**目标**</span><span class="sxs-lookup"><span data-stu-id="0e409-129">**Destination**</span></span>  
 <span data-ttu-id="0e409-130">指定哪个文件连接管理器或包变量包含数据配置文件输出：</span><span class="sxs-lookup"><span data-stu-id="0e409-130">Specify which File connection manager or package variable contains the data profile output:</span></span>  
  
-   <span data-ttu-id="0e409-131">如果将 **“目标类型”** 选项设置为 **“文件连接”** ，则 **“目标”** 选项显示可用文件连接服务器。</span><span class="sxs-lookup"><span data-stu-id="0e409-131">If the **DestinationType** option is set to **FileConnection**, the **Destination** option displays the available File connection managers.</span></span> <span data-ttu-id="0e409-132">选择其中某个连接管理器，或选择“\<New File connection>”创建新的文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="0e409-132">Select one of these connection managers, or select \<New File connection> to create a new File connection manager.</span></span>  
  
-   <span data-ttu-id="0e409-133">如果将 **“目标类型”** 选项设置为 **“变量”** ，则 **“目标”** 选项显示 **“目标”** 列表中可用的包变量。</span><span class="sxs-lookup"><span data-stu-id="0e409-133">If the **DestinationType** option is set to **Variable**, the **Destination** option displays the available package variables in the **Destination** list.</span></span> <span data-ttu-id="0e409-134">选择其中某个变量，或选择“\<New Variable>创建新变量。</span><span class="sxs-lookup"><span data-stu-id="0e409-134">Select one of these variables, or select \<New Variable> to create a new variable.</span></span>  
  
 <span data-ttu-id="0e409-135">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="0e409-135">**OverwriteDestination**</span></span>  
 <span data-ttu-id="0e409-136">如果输出文件已经存在，则指定是否将其覆盖。</span><span class="sxs-lookup"><span data-stu-id="0e409-136">Specify whether to overwrite the output file if it already exists.</span></span> <span data-ttu-id="0e409-137">默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="0e409-137">The default value is **False**.</span></span> <span data-ttu-id="0e409-138">只有在“目标类型”选项设置为“文件连接”时才使用此属性的值。</span><span class="sxs-lookup"><span data-stu-id="0e409-138">The value of this property is used only when the DestinationType option is set to FileConnection.</span></span> <span data-ttu-id="0e409-139">当“目标类型”选项设置为变量时，任务将始终覆盖该变量以前的值。</span><span class="sxs-lookup"><span data-stu-id="0e409-139">When the DestinationType option is set to Variable, the task always overwrites the previous value of the variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0e409-140">如果尝试多次运行数据事件探查任务时，不更改输出文件名或将 **OverwriteDestination** 属性的值更改为 **True**，则该任务将以输出文件已存在的消息失败。</span><span class="sxs-lookup"><span data-stu-id="0e409-140">If you try to run the Data Profiling task more than once without changing the output file name or changing the value of the **OverwriteDestination** property to **True**, the task fails with the message that the output file already exists.</span></span>  
  
## <a name="other-options"></a><span data-ttu-id="0e409-141">其他选项</span><span class="sxs-lookup"><span data-stu-id="0e409-141">Other Options</span></span>  
 <span data-ttu-id="0e409-142">**快速配置文件**</span><span class="sxs-lookup"><span data-stu-id="0e409-142">**Quick Profile**</span></span>  
 <span data-ttu-id="0e409-143">显示“单个表快速配置文件窗体”  。</span><span class="sxs-lookup"><span data-stu-id="0e409-143">Display the **Single Table Quick Profile Form**.</span></span> <span data-ttu-id="0e409-144">此窗体使用默认设置简化了探查单个表或视图的任务。</span><span class="sxs-lookup"><span data-stu-id="0e409-144">This form simplifies the task of profiling a single table or view by using default settings.</span></span> <span data-ttu-id="0e409-145">有关详细信息，请参阅 [单个表快速配置文件窗体（数据事件探查任务）](single-table-quick-profile-form-data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="0e409-145">For more information, see [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md).</span></span>  
  
 <span data-ttu-id="0e409-146">**打开配置文件查看器**</span><span class="sxs-lookup"><span data-stu-id="0e409-146">**Open Profile Viewer**</span></span>  
 <span data-ttu-id="0e409-147">打开数据配置文件查看器。</span><span class="sxs-lookup"><span data-stu-id="0e409-147">Opens the Data Profile Viewer.</span></span> <span data-ttu-id="0e409-148">独立数据配置文件查看器显示数据事件探查任务的数据配置文件输出。</span><span class="sxs-lookup"><span data-stu-id="0e409-148">The stand-alone Data Profile Viewer displays data profile output from the Data Profiling task.</span></span> <span data-ttu-id="0e409-149">可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包内运行数据事件探查任务并计算数据配置文件之后，查看这些数据配置文件输出。</span><span class="sxs-lookup"><span data-stu-id="0e409-149">You can view the data profile output after you have run the Data Profiling task inside the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e409-150">还可以通过在文件夹 \<drive>:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 中运行 DataProfileViewer.exe 来打开数据配置文件查看器。</span><span class="sxs-lookup"><span data-stu-id="0e409-150">You can also open the Data Profile Viewer by running the DataProfileViewer.exe in the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e409-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e409-151">See Also</span></span>  
 <span data-ttu-id="0e409-152">[单个表快速配置文件窗体（数据事件探查任务）](single-table-quick-profile-form-data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="0e409-152">[Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md) </span></span>  
 [<span data-ttu-id="0e409-153">数据事件探查任务编辑器（“配置文件请求”页）</span><span class="sxs-lookup"><span data-stu-id="0e409-153">Data Profiling Task Editor &#40;Profile Requests Page&#41;</span></span>](data-profiling-task-editor-profile-requests-page.md)  
  
  
