---
title: 日志属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3761ce3dca232db8968a2a7cba083dcc5554d792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694581"
---
# <a name="log-properties"></a><span data-ttu-id="c9313-102">日志属性</span><span class="sxs-lookup"><span data-stu-id="c9313-102">Log Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c9313-103">支持下表中列出的日志服务器属性</span><span class="sxs-lookup"><span data-stu-id="c9313-103">supports the log server properties listed in the following tables.</span></span> <span data-ttu-id="c9313-104">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c9313-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
## <a name="general"></a><span data-ttu-id="c9313-105">常规</span><span class="sxs-lookup"><span data-stu-id="c9313-105">General</span></span>  
 `File`  
 <span data-ttu-id="c9313-106">一个字符串属性，用于标识服务器日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c9313-106">A string property that identifies the name of the server log file.</span></span> <span data-ttu-id="c9313-107">只有在使用磁盘文件进行日志记录时，此属性才适用，而在使用数据库表进行日志记录时（默认行为）并不适用。</span><span class="sxs-lookup"><span data-stu-id="c9313-107">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="c9313-108">此属性的默认值为 msmdsrv.log。</span><span class="sxs-lookup"><span data-stu-id="c9313-108">The default value for this property is msmdsrv.log.</span></span>  
  
 `FileBufferSize`  
 <span data-ttu-id="c9313-109">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MessageLogs`  
 <span data-ttu-id="c9313-110">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="error-log"></a><span data-ttu-id="c9313-111">错误日志</span><span class="sxs-lookup"><span data-stu-id="c9313-111">Error Log</span></span>  
 <span data-ttu-id="c9313-112">您可以在服务器实例级别设置这些属性以修改其他工具和设计器中显示的“错误配置”的默认值。</span><span class="sxs-lookup"><span data-stu-id="c9313-112">You can set these properties at the server instance level to modify the default values for Error Configuration that appear in other tools and designers.</span></span> <span data-ttu-id="c9313-113">有关详细信息，请参阅[&#40;SSAS-多维&#41;的多维数据集、分区和维度处理的错误配置](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c9313-113">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) and <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> for more information.</span></span>  
  
 <span data-ttu-id="c9313-114">**ErrorLog\ErrorLogFileName**</span><span class="sxs-lookup"><span data-stu-id="c9313-114">**ErrorLog\ErrorLogFileName**</span></span>  
 <span data-ttu-id="c9313-115">在服务器执行处理操作期间使用的一个默认属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-115">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="c9313-116">**ErrorLog\ErrorLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="c9313-116">**ErrorLog\ErrorLogFileSize**</span></span>  
 <span data-ttu-id="c9313-117">在服务器执行处理操作期间使用的一个默认属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-117">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="c9313-118">**ErrorLog\KeyErrorAction**</span><span class="sxs-lookup"><span data-stu-id="c9313-118">**ErrorLog\KeyErrorAction**</span></span>  
 <span data-ttu-id="c9313-119">指定发生 `KeyNotFound` 错误时服务器执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-119">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="c9313-120">对此错误的有效响应包括：</span><span class="sxs-lookup"><span data-stu-id="c9313-120">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="c9313-121">`ConvertToUnknown` 指示服务器将错误键值分配给未知成员。</span><span class="sxs-lookup"><span data-stu-id="c9313-121">`ConvertToUnknown` tells the server to allocate the error key value to the unknown member.</span></span>  
  
-   <span data-ttu-id="c9313-122">`DiscardRecord` 指示服务器排除该记录。</span><span class="sxs-lookup"><span data-stu-id="c9313-122">`DiscardRecord` tells the server to exclude the record.</span></span>  
  
 <span data-ttu-id="c9313-123">**ErrorLog\KeyErrorLogFile**</span><span class="sxs-lookup"><span data-stu-id="c9313-123">**ErrorLog\KeyErrorLogFile**</span></span>  
 <span data-ttu-id="c9313-124">这是用户定义的文件名，必须具有 .log 文件扩展名，位于服务帐户拥有读/写权限的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c9313-124">This is a user-defined filename that must have a .log file extension, located in a folder on which the service account has read-write permissions.</span></span> <span data-ttu-id="c9313-125">此日志文件仅包含处理期间生成的错误。</span><span class="sxs-lookup"><span data-stu-id="c9313-125">This log file will only contain errors generated during processing.</span></span> <span data-ttu-id="c9313-126">如果您需要详细信息，请使用网络流量记录器。</span><span class="sxs-lookup"><span data-stu-id="c9313-126">Use the Flight Recorder if you require more detailed information.</span></span>  
  
 <span data-ttu-id="c9313-127">**ErrorLog\KeyErrorLimit**</span><span class="sxs-lookup"><span data-stu-id="c9313-127">**ErrorLog\KeyErrorLimit**</span></span>  
 <span data-ttu-id="c9313-128">这是在处理失败前服务器将允许的最大数据完整性错误数目。</span><span class="sxs-lookup"><span data-stu-id="c9313-128">This is the maximum number of data integrity errors that the server will allow before failing the processing.</span></span> <span data-ttu-id="c9313-129">值为 -1 表示没有限制。</span><span class="sxs-lookup"><span data-stu-id="c9313-129">A value of -1 indicates that there is no limit.</span></span> <span data-ttu-id="c9313-130">默认值为 0，表示处理在发生第一个错误时停止。</span><span class="sxs-lookup"><span data-stu-id="c9313-130">The default is 0, which means processing stops after the first error occurs.</span></span> <span data-ttu-id="c9313-131">您还可以将其设置为整数。</span><span class="sxs-lookup"><span data-stu-id="c9313-131">You can also set it to a whole number.</span></span>  
  
 <span data-ttu-id="c9313-132">**ErrorLog\KeyErrorLimitAction**</span><span class="sxs-lookup"><span data-stu-id="c9313-132">**ErrorLog\KeyErrorLimitAction**</span></span>  
 <span data-ttu-id="c9313-133">指定键错误数目达到上限时服务器所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-133">Specifies the action taken by the server when the number of key errors has reached the upper limit.</span></span> <span data-ttu-id="c9313-134">对此操作的有效响应包括：</span><span class="sxs-lookup"><span data-stu-id="c9313-134">Valid responses to this action include:</span></span>  
  
-   <span data-ttu-id="c9313-135">`StopProcessing` 指示服务器在达到错误限制时停止处理。</span><span class="sxs-lookup"><span data-stu-id="c9313-135">`StopProcessing` tells the server to stop processing when the error limit is reached.</span></span>  
  
-   <span data-ttu-id="c9313-136">`StopLogging` 指示服务器在达到错误限制时停止记录错误，但允许继续处理。</span><span class="sxs-lookup"><span data-stu-id="c9313-136">`StopLogging` tells the server to stop logging errors when the error limit is reached, but allow processing to continue.</span></span>  
  
 <span data-ttu-id="c9313-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span><span class="sxs-lookup"><span data-stu-id="c9313-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span></span>  
 <span data-ttu-id="c9313-138">指定发生 `KeyNotFound` 错误时服务器执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-138">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="c9313-139">对此错误的有效响应包括：</span><span class="sxs-lookup"><span data-stu-id="c9313-139">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="c9313-140">`IgnoreError` 指示服务器继续处理而不记录错误或一直计数至键错误限制。</span><span class="sxs-lookup"><span data-stu-id="c9313-140">`IgnoreError` tells the server to continue processing without logging the error or counting it towards the key error limit.</span></span> <span data-ttu-id="c9313-141">通过忽略该错误，您可以继续处理而不会增加错误计数或将错误记录至屏幕或日志文件。</span><span class="sxs-lookup"><span data-stu-id="c9313-141">By ignoring the error, you simply allow processing to continue without adding to the error count or logging it to the screen or log file.</span></span> <span data-ttu-id="c9313-142">有关记录具有数据完整性问题，无法添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="c9313-142">The record in question has a data integrity problem and cannot be added to the database.</span></span> <span data-ttu-id="c9313-143">该记录或者将被弃用，或者聚合到未知成员，具有情况由 `KeyErrorAction` 属性确定。</span><span class="sxs-lookup"><span data-stu-id="c9313-143">The record will either be discarded or aggregated to Unknown Member, as determined by the `KeyErrorAction` property.</span></span>  
  
-   <span data-ttu-id="c9313-144">`ReportAndContinue` 指示服务器记录错误、一直将错误计数至键错误限制并继续处理。</span><span class="sxs-lookup"><span data-stu-id="c9313-144">`ReportAndContinue` tells the server to log the error, count it towards the key error limit, and continue processing.</span></span> <span data-ttu-id="c9313-145">触发错误的记录被弃用或转换为未知成员。</span><span class="sxs-lookup"><span data-stu-id="c9313-145">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
-   <span data-ttu-id="c9313-146">`ReportAndStop` 指示服务器记录错误并立即停止处理，而不管键错误限制如何。</span><span class="sxs-lookup"><span data-stu-id="c9313-146">`ReportAndStop` tells the server to log the error and stop processing immediately, regardless of the key error limit.</span></span> <span data-ttu-id="c9313-147">触发错误的记录被弃用或转换为未知成员。</span><span class="sxs-lookup"><span data-stu-id="c9313-147">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
 <span data-ttu-id="c9313-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span><span class="sxs-lookup"><span data-stu-id="c9313-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span></span>  
 <span data-ttu-id="c9313-149">指定发现重复键时服务器所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-149">Specifies the action taken by the server when a duplicate key is found.</span></span> <span data-ttu-id="c9313-150">`IgnoreError`有效值包括用于继续处理（就好像该错误没有发生）的 `ReportAndContinue`、用于记录错误并继续处理的 `ReportAndStop` 以及用于记录错误并立即停止处理（即使错误计数低于错误限制）的 。</span><span class="sxs-lookup"><span data-stu-id="c9313-150">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="c9313-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span><span class="sxs-lookup"><span data-stu-id="c9313-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span></span>  
 <span data-ttu-id="c9313-152">指定在将 Null 键转换为未知成员后服务器所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-152">Specifies the action taken by the server when a null key has been converted to Unknown Member.</span></span> <span data-ttu-id="c9313-153">`IgnoreError`有效值包括用于继续处理（就好像该错误没有发生）的 `ReportAndContinue`、用于记录错误并继续处理的 `ReportAndStop` 以及用于记录错误并立即停止处理（即使错误计数低于错误限制）的 。</span><span class="sxs-lookup"><span data-stu-id="c9313-153">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="c9313-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span><span class="sxs-lookup"><span data-stu-id="c9313-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span></span>  
 <span data-ttu-id="c9313-155">指定 `NullProcessing` 针对维度属性设置为 `Error` 时服务器执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9313-155">Specifies the action taken by the server when `NullProcessing` is set to `Error` for a dimension attribute.</span></span> <span data-ttu-id="c9313-156">给定属性中不允许有 Null 值时，将生成错误。</span><span class="sxs-lookup"><span data-stu-id="c9313-156">An error is generated when a null value is not allowed in a given attribute.</span></span> <span data-ttu-id="c9313-157">此错误配置属性会通知下一步报告该错误，并继续进行处理，直至达到错误限制。</span><span class="sxs-lookup"><span data-stu-id="c9313-157">This error configuration property informs the next step, which is to report the error and continue processing until the error limit is reached.</span></span> <span data-ttu-id="c9313-158">`IgnoreError`有效值包括用于继续处理（就好像该错误没有发生）的 `ReportAndContinue`、用于记录错误并继续处理的 `ReportAndStop` 以及用于记录错误并立即停止处理（即使错误计数低于错误限制）的 。</span><span class="sxs-lookup"><span data-stu-id="c9313-158">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="c9313-159">**ErrorLog\ LogErrorTypes\CalculationError**</span><span class="sxs-lookup"><span data-stu-id="c9313-159">**ErrorLog\ LogErrorTypes\CalculationError**</span></span>  
 <span data-ttu-id="c9313-160">在服务器执行处理操作期间使用的一个默认属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-160">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="c9313-161">**ErrorLog\IgnoreDataTruncation**</span><span class="sxs-lookup"><span data-stu-id="c9313-161">**ErrorLog\IgnoreDataTruncation**</span></span>  
 <span data-ttu-id="c9313-162">在服务器执行处理操作期间使用的一个默认属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-162">A property used as a default during processing operation performed by the server.</span></span>  
  
## <a name="exception"></a><span data-ttu-id="c9313-163">异常</span><span class="sxs-lookup"><span data-stu-id="c9313-163">Exception</span></span>  
 <span data-ttu-id="c9313-164">**Exception\CreateAndSendCrashReports**</span><span class="sxs-lookup"><span data-stu-id="c9313-164">**Exception\CreateAndSendCrashReports**</span></span>  
 <span data-ttu-id="c9313-165">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-165">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-166">**Exception\CrashReportsFolder**</span><span class="sxs-lookup"><span data-stu-id="c9313-166">**Exception\CrashReportsFolder**</span></span>  
 <span data-ttu-id="c9313-167">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-167">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-168">**Exception\SQLDumperFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="c9313-168">**Exception\SQLDumperFlagsOn**</span></span>  
 <span data-ttu-id="c9313-169">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-170">**Exception\SQLDumperFlagsOff**</span><span class="sxs-lookup"><span data-stu-id="c9313-170">**Exception\SQLDumperFlagsOff**</span></span>  
 <span data-ttu-id="c9313-171">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-172">**Exception\MiniDumpFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="c9313-172">**Exception\MiniDumpFlagsOn**</span></span>  
 <span data-ttu-id="c9313-173">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-173">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-174">**Exception\MinidumpErrorList**</span><span class="sxs-lookup"><span data-stu-id="c9313-174">**Exception\MinidumpErrorList**</span></span>  
 <span data-ttu-id="c9313-175">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-175">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="flight-recorder"></a><span data-ttu-id="c9313-176">网络流量记录器</span><span class="sxs-lookup"><span data-stu-id="c9313-176">Flight Recorder</span></span>  
 <span data-ttu-id="c9313-177">**FlightRecorder\Enabled**</span><span class="sxs-lookup"><span data-stu-id="c9313-177">**FlightRecorder\Enabled**</span></span>  
 <span data-ttu-id="c9313-178">一个布尔值属性，它指示是否启用网络流量记录器功能。</span><span class="sxs-lookup"><span data-stu-id="c9313-178">A Boolean property that indicates whether the flight recorder feature is enabled.</span></span>  
  
 <span data-ttu-id="c9313-179">**FlightRecorder\FileSizeMB**</span><span class="sxs-lookup"><span data-stu-id="c9313-179">**FlightRecorder\FileSizeMB**</span></span>  
 <span data-ttu-id="c9313-180">一个有符号 32 位整数属性，它定义网络流量记录器磁盘文件大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="c9313-180">A signed 32-bit integer property that defines the size of the flight recorder disk file, in megabytes.</span></span>  
  
 <span data-ttu-id="c9313-181">**FlightRecorder\LogDurationSec**</span><span class="sxs-lookup"><span data-stu-id="c9313-181">**FlightRecorder\LogDurationSec**</span></span>  
 <span data-ttu-id="c9313-182">一个有符号 32 位整数属性，它定义网络流量记录器的翻转频率（秒）。</span><span class="sxs-lookup"><span data-stu-id="c9313-182">A signed 32-bit integer property that defines the frequency that the flight recorder is rolled over, in seconds.</span></span>  
  
 <span data-ttu-id="c9313-183">**FlightRecorder\SnapshotDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="c9313-183">**FlightRecorder\SnapshotDefinitionFile**</span></span>  
 <span data-ttu-id="c9313-184">一个字符串属性，它定义快照定义文件（该文件包含拍摄快照时向服务器发出的发现命令）的名称。</span><span class="sxs-lookup"><span data-stu-id="c9313-184">A string property that defines the name of the snapshot definition file, containing discover commands that are issued to the server when a snapshot is taken.</span></span>  
  
 <span data-ttu-id="c9313-185">此属性的默认值为空，表示默认文件名为 FlightRecorderSnapshotDef.xml。</span><span class="sxs-lookup"><span data-stu-id="c9313-185">The default value for this property is blank, which in turn defaults to file name FlightRecorderSnapshotDef.xml.</span></span>  
  
 <span data-ttu-id="c9313-186">**FlightRecorder\SnapshotFrequencySec**</span><span class="sxs-lookup"><span data-stu-id="c9313-186">**FlightRecorder\SnapshotFrequencySec**</span></span>  
 <span data-ttu-id="c9313-187">一个有符号 32 位整数属性，它定义快照频率（秒）。</span><span class="sxs-lookup"><span data-stu-id="c9313-187">A signed 32-bit integer property that defines the snapshot frequency, in seconds.</span></span>  
  
 <span data-ttu-id="c9313-188">**FlightRecorder\TraceDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="c9313-188">**FlightRecorder\TraceDefinitionFile**</span></span>  
 <span data-ttu-id="c9313-189">一个字符串属性，它指定网络流量记录器跟踪定义文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c9313-189">A string property that specifies the name of the flight recorder trace definition file.</span></span>  
  
 <span data-ttu-id="c9313-190">此属性的默认值为空，表示默认文件名为 FlightRecorderTraceDef.xml。</span><span class="sxs-lookup"><span data-stu-id="c9313-190">The default value for this property is blank, which in turn defaults to FlightRecorderTraceDef.xml.</span></span>  
  
## <a name="query-log"></a><span data-ttu-id="c9313-191">查询日志</span><span class="sxs-lookup"><span data-stu-id="c9313-191">Query Log</span></span>  
 <span data-ttu-id="c9313-192">**适用于：** 仅限多维服务器模式</span><span class="sxs-lookup"><span data-stu-id="c9313-192">**Applies to:** Multidimensional server mode only</span></span>  
  
 <span data-ttu-id="c9313-193">**QueryLog\QueryLogFileName**</span><span class="sxs-lookup"><span data-stu-id="c9313-193">**QueryLog\QueryLogFileName**</span></span>  
 <span data-ttu-id="c9313-194">一个字符串属性，它指定查询日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c9313-194">A string property that specifies the name of the query log file.</span></span> <span data-ttu-id="c9313-195">只有在使用磁盘文件进行日志记录时，此属性才适用，而在使用数据库表进行日志记录时（默认行为）并不适用。</span><span class="sxs-lookup"><span data-stu-id="c9313-195">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="c9313-196">**QueryLog\QueryLogSampling**</span><span class="sxs-lookup"><span data-stu-id="c9313-196">**QueryLog\QueryLogSampling**</span></span>  
 <span data-ttu-id="c9313-197">一个有符号 32 位整数属性，它指定查询日志抽样率。</span><span class="sxs-lookup"><span data-stu-id="c9313-197">A signed 32-bit integer property that specifies the query log sampling rate.</span></span>  
  
 <span data-ttu-id="c9313-198">此属性的默认值为 10，表示每 10 个服务器查询记录一个。</span><span class="sxs-lookup"><span data-stu-id="c9313-198">The default value for this property is 10, meaning that 1 out of every 10 server queries is logged.</span></span>  
  
 <span data-ttu-id="c9313-199">**QueryLog\QueryLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="c9313-199">**QueryLog\QueryLogFileSize**</span></span>  
 <span data-ttu-id="c9313-200">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-200">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-201">**QueryLog\QueryLogConnectionString**</span><span class="sxs-lookup"><span data-stu-id="c9313-201">**QueryLog\QueryLogConnectionString**</span></span>  
 <span data-ttu-id="c9313-202">一个字符串属性，它指定到查询日志数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="c9313-202">A string property that specifies the connection to the query log database.</span></span>  
  
 <span data-ttu-id="c9313-203">**QueryLog\QueryLogTableName**</span><span class="sxs-lookup"><span data-stu-id="c9313-203">**QueryLog\QueryLogTableName**</span></span>  
 <span data-ttu-id="c9313-204">一个字符串属性，它指定查询日志表的名称。</span><span class="sxs-lookup"><span data-stu-id="c9313-204">A string property that specifies the name of the query log table.</span></span>  
  
 <span data-ttu-id="c9313-205">此属性的默认值为 OlapQueryLog。</span><span class="sxs-lookup"><span data-stu-id="c9313-205">The default value for this property is OlapQueryLog.</span></span>  
  
 <span data-ttu-id="c9313-206">**QueryLog\CreateQueryLogTable**</span><span class="sxs-lookup"><span data-stu-id="c9313-206">**QueryLog\CreateQueryLogTable**</span></span>  
 <span data-ttu-id="c9313-207">一个布尔值属性，它指定是否创建查询日志表。</span><span class="sxs-lookup"><span data-stu-id="c9313-207">A Boolean property that specifies whether to create the query log table.</span></span>  
  
 <span data-ttu-id="c9313-208">此属性的默认值为 false，指示服务器不会自动创建日志表，并且不记录查询事件。</span><span class="sxs-lookup"><span data-stu-id="c9313-208">The default value for this property is false, which indicates the server will not automatically create the log table and will not log query events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9313-209">有关配置查询日志的详细信息，请参阅[Analysis Services 中的日志操作](../instances/log-operations-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c9313-209">For more information about configuring the query log, see [Log operations in Analysis Services](../instances/log-operations-in-analysis-services.md).</span></span>  
  
## <a name="trace"></a><span data-ttu-id="c9313-210">跟踪</span><span class="sxs-lookup"><span data-stu-id="c9313-210">Trace</span></span>  
 <span data-ttu-id="c9313-211">**Trace\TraceBackgroundDistributionPeriod**</span><span class="sxs-lookup"><span data-stu-id="c9313-211">**Trace\TraceBackgroundDistributionPeriod**</span></span>  
 <span data-ttu-id="c9313-212">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-212">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-213">**Trace\TraceBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="c9313-213">**Trace\TraceBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="c9313-214">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-215">**Trace\TraceFileBufferSize**</span><span class="sxs-lookup"><span data-stu-id="c9313-215">**Trace\TraceFileBufferSize**</span></span>  
 <span data-ttu-id="c9313-216">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-216">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-217">**Trace\TraceFileWriteTrailerPeriod**</span><span class="sxs-lookup"><span data-stu-id="c9313-217">**Trace\TraceFileWriteTrailerPeriod**</span></span>  
 <span data-ttu-id="c9313-218">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-219">**Trace\TraceMaxRowsetSize**</span><span class="sxs-lookup"><span data-stu-id="c9313-219">**Trace\TraceMaxRowsetSize**</span></span>  
 <span data-ttu-id="c9313-220">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-221">**Trace\TraceProtocolTraffic**</span><span class="sxs-lookup"><span data-stu-id="c9313-221">**Trace\TraceProtocolTraffic**</span></span>  
 <span data-ttu-id="c9313-222">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-222">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-223">**Trace\TraceQueryResponseTextChunkSize**</span><span class="sxs-lookup"><span data-stu-id="c9313-223">**Trace\TraceQueryResponseTextChunkSize**</span></span>  
 <span data-ttu-id="c9313-224">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-225">**Trace\TraceReportFQDN**</span><span class="sxs-lookup"><span data-stu-id="c9313-225">**Trace\TraceReportFQDN**</span></span>  
 <span data-ttu-id="c9313-226">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-226">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-227">**Trace\TraceRequestParameters**</span><span class="sxs-lookup"><span data-stu-id="c9313-227">**Trace\TraceRequestParameters**</span></span>  
 <span data-ttu-id="c9313-228">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="c9313-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="c9313-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="c9313-230">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="c9313-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9313-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9313-231">See Also</span></span>  
 <span data-ttu-id="c9313-232">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c9313-232">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="c9313-233">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="c9313-233">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
