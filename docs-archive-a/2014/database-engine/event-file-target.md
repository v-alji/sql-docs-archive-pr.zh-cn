---
title: 事件文件目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- event file target
- file target [SQL Server extended events]
- targets [SQL Server extended events], file target
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1a64236b3874543982be5abbd8e60d8169082a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690046"
---
# <a name="event-file-target"></a><span data-ttu-id="06d63-102">Event File Target</span><span class="sxs-lookup"><span data-stu-id="06d63-102">Event File Target</span></span>
  <span data-ttu-id="06d63-103">事件文件目标是可将完整的缓冲区写入磁盘的目标。</span><span class="sxs-lookup"><span data-stu-id="06d63-103">The event file target is a target that writes complete buffers to disk.</span></span>  
  
 <span data-ttu-id="06d63-104">下表描述了配置事件文件目标时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="06d63-104">The following table describes the available options for configuring the event file target.</span></span>  
  
|<span data-ttu-id="06d63-105">选项</span><span class="sxs-lookup"><span data-stu-id="06d63-105">Option</span></span>|<span data-ttu-id="06d63-106">允许的值</span><span class="sxs-lookup"><span data-stu-id="06d63-106">Allowed values</span></span>|<span data-ttu-id="06d63-107">说明</span><span class="sxs-lookup"><span data-stu-id="06d63-107">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="06d63-108">filename</span><span class="sxs-lookup"><span data-stu-id="06d63-108">filename</span></span>|<span data-ttu-id="06d63-109">任何不超过 260 个字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="06d63-109">Any string up to 260 characters.</span></span> <span data-ttu-id="06d63-110">此值是必需的。</span><span class="sxs-lookup"><span data-stu-id="06d63-110">This value is required.</span></span>|<span data-ttu-id="06d63-111">文件位置和文件名。</span><span class="sxs-lookup"><span data-stu-id="06d63-111">The file location and filename.</span></span><br /><br /> <span data-ttu-id="06d63-112">可以使用任何文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="06d63-112">You can use any filename extension.</span></span>|  
|<span data-ttu-id="06d63-113">max_file_size</span><span class="sxs-lookup"><span data-stu-id="06d63-113">max_file_size</span></span>|<span data-ttu-id="06d63-114">任何 64 位的整数。</span><span class="sxs-lookup"><span data-stu-id="06d63-114">Any 64 bit integer.</span></span> <span data-ttu-id="06d63-115">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="06d63-115">This value is optional.</span></span>|<span data-ttu-id="06d63-116">文件的最大大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="06d63-116">The maximum file size in megabytes (MB).</span></span> <span data-ttu-id="06d63-117">如果未指定 max_file_size，则文件将一直增长到磁盘变满为止。</span><span class="sxs-lookup"><span data-stu-id="06d63-117">If max_file_size is not specified, the file will grow until the disk is full.</span></span> <span data-ttu-id="06d63-118">默认文件大小为 1GB。</span><span class="sxs-lookup"><span data-stu-id="06d63-118">The default file size is 1GB.</span></span><br /><br /> <span data-ttu-id="06d63-119">max_file_size 必须大于会话缓冲区的当前大小。</span><span class="sxs-lookup"><span data-stu-id="06d63-119">max_file_size must be larger than the current size of the session buffers.</span></span> <span data-ttu-id="06d63-120">否则，文件目标将无法初始化，并报告 max_file_size 无效。</span><span class="sxs-lookup"><span data-stu-id="06d63-120">If it is not, the file target will fail to initialize, reporting that the max_file_size is invalid.</span></span> <span data-ttu-id="06d63-121">若要查看缓冲区的当前大小，请查询 [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) 动态管理视图中的 buffer_size 列。</span><span class="sxs-lookup"><span data-stu-id="06d63-121">To view the current size of the buffers, query the buffer_size column in the [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) dynamic management view.</span></span><br /><br /> <span data-ttu-id="06d63-122">如果默认文件大小小于会话缓冲区大小，建议将 max_file_size 设置为 [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) 目录视图中的 max_memory 列中指定的值。</span><span class="sxs-lookup"><span data-stu-id="06d63-122">If the default file size is smaller than the session buffer size, we recommend setting max_file_size to the value specified in the max_memory column in the [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) catalog view.</span></span><br /><br /> <span data-ttu-id="06d63-123">将 max_file_size 的大小设置为大于会话缓冲区大小时，它可能会向下舍入到最近的会话缓冲区大小的倍数。</span><span class="sxs-lookup"><span data-stu-id="06d63-123">When max_file_size is set to a size larger than the size of the session buffers, it may be rounded down to the nearest multiple of the session buffer size.</span></span> <span data-ttu-id="06d63-124">这样所产生的目标文件的大小可能小于指定值 max_file_size。</span><span class="sxs-lookup"><span data-stu-id="06d63-124">This may create a target file that is smaller than the specified value of max_file_size.</span></span> <span data-ttu-id="06d63-125">例如，如果缓冲区大小为 100MB 并且 max_file_size 设置为 150MB，则因为在剩余的 50MB 空间中无法放下第二个缓冲区，生成的文件的大小会向下舍入到 100MB。</span><span class="sxs-lookup"><span data-stu-id="06d63-125">For example, if the buffer size is 100MB and max_file_size is set to 150MB, the resultant file size is rounded down to 100MB because a second buffer would not fit in the remaining 50MB of space.</span></span><br /><br /> <span data-ttu-id="06d63-126">如果默认文件大小小于会话缓冲区大小，建议将 max_file_size 设置为 [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) 目录视图中的 max_memory 列中的值。</span><span class="sxs-lookup"><span data-stu-id="06d63-126">If the default file size is smaller than the session buffer size, we recommend setting max_file_size to the value in the max_memory column in the [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) catalog view.</span></span>|  
|<span data-ttu-id="06d63-127">max_rollover_files</span><span class="sxs-lookup"><span data-stu-id="06d63-127">max_rollover_files</span></span>|<span data-ttu-id="06d63-128">任何 32 位的整数。</span><span class="sxs-lookup"><span data-stu-id="06d63-128">Any 32 bit integer.</span></span> <span data-ttu-id="06d63-129">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="06d63-129">This value is optional.</span></span>|<span data-ttu-id="06d63-130">文件系统中可保留的最多文件数。</span><span class="sxs-lookup"><span data-stu-id="06d63-130">The maximum number of files to retain in the file system.</span></span> <span data-ttu-id="06d63-131">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="06d63-131">The default value is 5.</span></span>|  
|<span data-ttu-id="06d63-132">增量</span><span class="sxs-lookup"><span data-stu-id="06d63-132">increment</span></span>|<span data-ttu-id="06d63-133">任何 32 位的整数。</span><span class="sxs-lookup"><span data-stu-id="06d63-133">Any 32 bit integer.</span></span> <span data-ttu-id="06d63-134">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="06d63-134">This value is optional.</span></span>|<span data-ttu-id="06d63-135">文件的增量 (MB)。</span><span class="sxs-lookup"><span data-stu-id="06d63-135">The incremental growth, in megabytes (MB), for the file.</span></span> <span data-ttu-id="06d63-136">如果未指定，则增量的默认值为会话缓冲区大小的两倍。</span><span class="sxs-lookup"><span data-stu-id="06d63-136">If unspecified, the default value for increment is twice the session buffer size.</span></span>|  
  
 <span data-ttu-id="06d63-137">第一次创建事件文件目标时，会在指定的文件名后面附加 _0\_ 以及一个长整型值。</span><span class="sxs-lookup"><span data-stu-id="06d63-137">The first time that an event file target is created, the filename you specify is appended with _0\_ and a long integer value.</span></span> <span data-ttu-id="06d63-138">此整数值计算为1601年1月1日到创建该文件的日期和时间之间的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="06d63-138">The integer value is calculated as the number of milliseconds between January 1, 1601 and the date and time the file is created.</span></span> <span data-ttu-id="06d63-139">后续的回滚文件也将使用此格式。</span><span class="sxs-lookup"><span data-stu-id="06d63-139">Subsequent rollover files also use this format.</span></span> <span data-ttu-id="06d63-140">通过检查该长整型值，可以确定最新的文件。</span><span class="sxs-lookup"><span data-stu-id="06d63-140">From examining the value of the long integer, you can determine the most current file.</span></span> <span data-ttu-id="06d63-141">以下示例演示了文件的命名方式。在该方案中，将文件名选项指定为 C:\OutputFiles\MyOutput.xel：</span><span class="sxs-lookup"><span data-stu-id="06d63-141">The following example illustrates how files are named in a scenario where you specify the filename option as C:\OutputFiles\MyOutput.xel:</span></span>  
  
-   <span data-ttu-id="06d63-142">创建的第一个文件 - C:\OutputFiles\MyOutput_0_128500310259380000.xel</span><span class="sxs-lookup"><span data-stu-id="06d63-142">first file created - C:\OutputFiles\MyOutput_0_128500310259380000.xel</span></span>  
  
-   <span data-ttu-id="06d63-143">第一个滚动更新文件 - C:\OutputFiles\MyOutput_0_128505831770890000.xel</span><span class="sxs-lookup"><span data-stu-id="06d63-143">first rollover file - C:\OutputFiles\MyOutput_0_128505831770890000.xel</span></span>  
  
-   <span data-ttu-id="06d63-144">第二个滚动更新文件 - C:\OutputFiles\MyOutput_0_132410772966237000.xel</span><span class="sxs-lookup"><span data-stu-id="06d63-144">second rollover file - C:\OutputFiles\MyOutput_0_132410772966237000.xel</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="06d63-145">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="06d63-145">Adding the Target to a Session</span></span>  
 <span data-ttu-id="06d63-146">若要将事件文件目标添加到扩展事件会话，在创建或更改事件会话时，应包括下面的语句，并将 *file_name* 替换为所需的文件名和路径：</span><span class="sxs-lookup"><span data-stu-id="06d63-146">To add the event file target to an Extended Events session, you would include the following statements when you create or alter an event session, replacing *file_name* with the desired file name and path:</span></span>  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="06d63-147">查看目标输出</span><span class="sxs-lookup"><span data-stu-id="06d63-147">Reviewing the Target Output</span></span>  
 <span data-ttu-id="06d63-148">若要查看文件目标的输出，必须使用 sys.fn_xe_file_target_read_file 功能。</span><span class="sxs-lookup"><span data-stu-id="06d63-148">To review the output from the file target, you must use the sys.fn_xe_file_target_read_file function.</span></span> <span data-ttu-id="06d63-149">建议您将数据转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="06d63-149">We recommend that you cast the data as XML.</span></span> <span data-ttu-id="06d63-150">你可以使用下面的语法，并将 *file_name* 替换为在添加目标时指定的文件名和路径：</span><span class="sxs-lookup"><span data-stu-id="06d63-150">You can use the following syntax, replacing *file_name* with the file name and path that you specified when you added the target:</span></span>  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="06d63-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06d63-151">See Also</span></span>  
 <span data-ttu-id="06d63-152">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="06d63-152">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="06d63-153">[sys. fn_xe_file_target_read_file &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="06d63-153">[sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql) </span></span>  
 <span data-ttu-id="06d63-154">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="06d63-154">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="06d63-155">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06d63-155">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
