---
title: " (DTA) 的工作负荷元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20184760c3fcb5eed6c02b8f8fd9b63f5586c9af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581078"
---
# <a name="workload-element-dta"></a><span data-ttu-id="c5b9a-102">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-102">Workload Element (DTA)</span></span>
  <span data-ttu-id="c5b9a-103">指定要用于优化会话的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-103">Specifies the workload to be used for a tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b9a-104">语法</span><span class="sxs-lookup"><span data-stu-id="c5b9a-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c5b9a-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="c5b9a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="c5b9a-106">特征</span><span class="sxs-lookup"><span data-stu-id="c5b9a-106">Characteristic</span></span>|<span data-ttu-id="c5b9a-107">说明</span><span class="sxs-lookup"><span data-stu-id="c5b9a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c5b9a-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="c5b9a-108">**Data type and length**</span></span>|<span data-ttu-id="c5b9a-109">无。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-109">None.</span></span>|  
|<span data-ttu-id="c5b9a-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="c5b9a-110">**Default value**</span></span>|<span data-ttu-id="c5b9a-111">无。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-111">None.</span></span>|  
|<span data-ttu-id="c5b9a-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="c5b9a-112">**Occurrence**</span></span>|<span data-ttu-id="c5b9a-113">对于每个 `DTAInput` 元素必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-113">Required once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c5b9a-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="c5b9a-114">Element Relationships</span></span>  
  
|<span data-ttu-id="c5b9a-115">关系</span><span class="sxs-lookup"><span data-stu-id="c5b9a-115">Relationship</span></span>|<span data-ttu-id="c5b9a-116">元素</span><span class="sxs-lookup"><span data-stu-id="c5b9a-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c5b9a-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="c5b9a-117">**Parent element**</span></span>|[<span data-ttu-id="c5b9a-118">启动并使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="c5b9a-118">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|<span data-ttu-id="c5b9a-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="c5b9a-119">**Child elements**</span></span>|[<span data-ttu-id="c5b9a-120">文件元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-120">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)<br /><br /> [<span data-ttu-id="c5b9a-121">工作负荷的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-121">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)<br /><br /> [<span data-ttu-id="c5b9a-122">EventString 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-122">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="c5b9a-123">备注</span><span class="sxs-lookup"><span data-stu-id="c5b9a-123">Remarks</span></span>  
 <span data-ttu-id="c5b9a-124">工作负荷是对要优化的一个或多个数据库执行的一组 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-124">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="c5b9a-125">数据库引擎优化顾问可以将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、跟踪文件和跟踪表用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-125">The Database Engine Tuning Advisor can use [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, trace files, and trace tables as workloads.</span></span>  
  
 <span data-ttu-id="c5b9a-126">如果在 XML 输入文件中指定了一个工作负荷，同时又使用 **dta** 工具在命令行中指定了一个工作负荷，则将使用命令行中指定的工作负荷进行优化。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-126">If you specify a workload in an XML input file and a workload on the command line with the **dta** tool, the workload specified on the command line will be used for tuning.</span></span> <span data-ttu-id="c5b9a-127">命令行中指定的所有优化选项的优先级均高于 XML 输入文件中指定的优化选项。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-127">All tuning options specified on the command line override those that are specified in an XML input file.</span></span> <span data-ttu-id="c5b9a-128">唯一的例外情况是：在计算模式下，在 XML 输入文件中输入用户指定的配置。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-128">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="c5b9a-129">例如，如果在 XML 输入文件的 `Configuration` 元素中输入了一个配置，同时在优化选项中指定了 `EvaluateConfiguration` 元素，则 XML 输入文件中指定的优化选项将覆盖命令提示行中输入的任何优化选项。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-129">For example, if a configuration is entered in the `Configuration` element of the XML input file and the `EvaluateConfiguration` element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered at the command line.</span></span>  
  
 <span data-ttu-id="c5b9a-130">必须为每个优化会话指定一个工作负荷。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-130">One workload must be specified for each tuning session.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b9a-131">示例</span><span class="sxs-lookup"><span data-stu-id="c5b9a-131">Example</span></span>  
 <span data-ttu-id="c5b9a-132">下面的代码示例为元素指定**MyDatabase. workload. mydatabase.mydbowner.tuningtable001**跟踪表。 `Workload`</span><span class="sxs-lookup"><span data-stu-id="c5b9a-132">The following code example specifies the **MyDatabase.MyDBOwner.TuningTable001** trace table for the `Workload` element.</span></span> <span data-ttu-id="c5b9a-133">使用带有 SQL Server 事件探查器的优化模板创建 **TuningTable001** ，并将该跟踪输出另存为一个表。</span><span class="sxs-lookup"><span data-stu-id="c5b9a-133">The **TuningTable001** was created by using the Tuning template with SQL Server Profiler and saving the trace output as a table.</span></span>  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5b9a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5b9a-134">See Also</span></span>  
 [<span data-ttu-id="c5b9a-135">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="c5b9a-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
