---
title: 使用 (XEvents) SQL Server 扩展事件监视 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d12d9bc8d6a56702e1b44f8404b25681a1033f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588735"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a><span data-ttu-id="76202-102">使用 SQL Server 扩展事件 (XEvents) 监视 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="76202-102">Use SQL Server Extended Events (XEvents) to Monitor Analysis Services</span></span>
  <span data-ttu-id="76202-103">Analysis Services 通过[扩展事件](../../relational-databases/extended-events/extended-events.md)的使用来提供跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="76202-103">Analysis Services provides tracing capabilities through the usage of [Extended Events](../../relational-databases/extended-events/extended-events.md).</span></span>  
  
 <span data-ttu-id="76202-104">扩展事件是针对服务器系统的高度可伸缩和可配置的事件基础结构。</span><span class="sxs-lookup"><span data-stu-id="76202-104">Extended Events is an event infrastructure that is highly scalable and configurable for server systems.</span></span> <span data-ttu-id="76202-105">扩展事件是使用非常少的性能资源的轻型性能监视系统。</span><span class="sxs-lookup"><span data-stu-id="76202-105">Extended Events is a light weight performance monitoring system that uses very few performance resources.</span></span>  
  
 <span data-ttu-id="76202-106">可以捕获所有 Analysis Services 事件，并将其定位到在[扩展事件](../../relational-databases/extended-events/extended-events.md)中通过 XEvents 定义的特定使用者。</span><span class="sxs-lookup"><span data-stu-id="76202-106">All Analysis Services events can be captured and target to specific consumers, as defined in [Extended Events](../../relational-databases/extended-events/extended-events.md), through XEvents.</span></span>  
  
## <a name="initiating-extended-events-in-analysis-services"></a><span data-ttu-id="76202-107">在 Analysis Services 中启动扩展事件</span><span class="sxs-lookup"><span data-stu-id="76202-107">Initiating Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="76202-108">通过使用如下的 XMLA 创建对象脚本命令启用扩展事件跟踪：</span><span class="sxs-lookup"><span data-stu-id="76202-108">Extended Event tracing is enabled using a similar XMLA create object script command as shown below:</span></span>  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="76202-109">其中，以下元素将由用户根据跟踪需要进行定义：</span><span class="sxs-lookup"><span data-stu-id="76202-109">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="76202-110">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="76202-110">*trace_id*</span></span>  
 <span data-ttu-id="76202-111">定义用于此跟踪的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="76202-111">Defines the unique identifier for this trace.</span></span>  
  
 <span data-ttu-id="76202-112">*跟踪名称*</span><span class="sxs-lookup"><span data-stu-id="76202-112">*trace_name*</span></span>  
 <span data-ttu-id="76202-113">提供给此跟踪的名称；通常是此跟踪的用户可读定义。</span><span class="sxs-lookup"><span data-stu-id="76202-113">The name given to this trace; usually a human readable definition of the trace.</span></span> <span data-ttu-id="76202-114">通常使用 trace_id\*\* 值作为该名称。</span><span class="sxs-lookup"><span data-stu-id="76202-114">It is a common practice to use the *trace_id* value as the name.</span></span>  
  
 <span data-ttu-id="76202-115">*AS_event*</span><span class="sxs-lookup"><span data-stu-id="76202-115">*AS_event*</span></span>  
 <span data-ttu-id="76202-116">要公开的 Analysis Services 事件。</span><span class="sxs-lookup"><span data-stu-id="76202-116">The Analysis Services event to be exposed.</span></span> <span data-ttu-id="76202-117">有关事件名称的详细信息，请参阅 [Analysis Services 跟踪事件](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) 。</span><span class="sxs-lookup"><span data-stu-id="76202-117">See [Analysis Services Trace Events](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) for names of the events.</span></span>  
  
 <span data-ttu-id="76202-118">*data_filename*</span><span class="sxs-lookup"><span data-stu-id="76202-118">*data_filename*</span></span>  
 <span data-ttu-id="76202-119">包含事件数据的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="76202-119">The name of the file that contains the events data.</span></span> <span data-ttu-id="76202-120">该名称以时间戳作为后缀，以免在反复发送跟踪时数据被覆盖。</span><span class="sxs-lookup"><span data-stu-id="76202-120">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
 <span data-ttu-id="76202-121">*元数据文件名*</span><span class="sxs-lookup"><span data-stu-id="76202-121">*metadata_filename*</span></span>  
 <span data-ttu-id="76202-122">包含事件元数据的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="76202-122">The name of the file that contains the events metadata.</span></span> <span data-ttu-id="76202-123">该名称以时间戳作为后缀，以免在反复发送跟踪时数据被覆盖。</span><span class="sxs-lookup"><span data-stu-id="76202-123">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
## <a name="stopping-extended-events-in-analysis-services"></a><span data-ttu-id="76202-124">在 Analysis Services 中停止扩展事件</span><span class="sxs-lookup"><span data-stu-id="76202-124">Stopping Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="76202-125">若要停止扩展事件跟踪对象，您需要使用如下所示的 XMLA 删除对象脚本命令删除该对象：</span><span class="sxs-lookup"><span data-stu-id="76202-125">To stop the Extended Events tracing object you need to delete that object using a similar XMLA delete object script command as shown below:</span></span>  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="76202-126">其中，以下元素将由用户根据跟踪需要进行定义：</span><span class="sxs-lookup"><span data-stu-id="76202-126">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="76202-127">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="76202-127">*trace_id*</span></span>  
 <span data-ttu-id="76202-128">为要删除的跟踪定义唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="76202-128">Defines the unique identifier for the trace to be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76202-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76202-129">See Also</span></span>  
 [<span data-ttu-id="76202-130">扩展事件</span><span class="sxs-lookup"><span data-stu-id="76202-130">Extended Events</span></span>](../../relational-databases/extended-events/extended-events.md)  
  
  
