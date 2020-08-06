---
title: 处理结果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: rothja
ms.author: jroth
ms.openlocfilehash: b9e5bf00b4d2e554536c9f2ba1a328390b93a8a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589529"
---
# <a name="processing-results"></a><span data-ttu-id="51f40-102">处理结果</span><span class="sxs-lookup"><span data-stu-id="51f40-102">Processing Results</span></span>
  <span data-ttu-id="51f40-103">如果行集对象是由执行命令或直接从访问接口生成的，则使用者需要检索和访问行集中的数据。</span><span class="sxs-lookup"><span data-stu-id="51f40-103">If a rowset object is produced by either the execution of a command or the generation of a rowset object directly from the provider, the consumer needs to retrieve and access data in the rowset.</span></span>  
  
 <span data-ttu-id="51f40-104">行集是使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口能够以表格格式提供数据的核心对象。</span><span class="sxs-lookup"><span data-stu-id="51f40-104">Rowsets are the central objects that enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to expose data in tabular form.</span></span> <span data-ttu-id="51f40-105">从概念上说，行集是指其中的每行都拥有列数据的行的集合。</span><span class="sxs-lookup"><span data-stu-id="51f40-105">Conceptually, a rowset is a set of rows in which each row has column data.</span></span> <span data-ttu-id="51f40-106">行集对象可提供如下接口：IRowset（包含按顺序从行集提取行的方法）、IAccessor（允许定义一组列绑定来说明将表格格式数据绑定到使用者程序变量的方式）、IColumnsInfo（提供有关行集中列的信息）以及 IRowsetInfo（提供有关行集的信息）\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f40-106">A rowset object exposes interfaces such as **IRowset** (contains methods for fetching rows from the rowset sequentially), **IAccessor** (permits the definition of a group of column bindings describing the way tabular data is bound to consumer program variables), **IColumnsInfo** (provides information about columns in the rowset), and **IRowsetInfo** (provides information about rowset).</span></span>  
  
 <span data-ttu-id="51f40-107">使用者可以调用 IRowset::GetData 方法将行集中的一行数据检索到缓冲区中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f40-107">A consumer can call the **IRowset::GetData** method to retrieve a row of data from the rowset into a buffer.</span></span> <span data-ttu-id="51f40-108">在调用 GetData 之前，使用者使用一组 DBBINDING 结构来描述缓冲区\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f40-108">Before **GetData** is called, the consumer describes the buffer using a set of DBBINDING structures.</span></span> <span data-ttu-id="51f40-109">每个绑定都说明了行集中的列在使用者缓冲区中的存储方式并包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="51f40-109">Each binding describes how a column in a rowset is stored in a consumer buffer and contains the following:</span></span>  
  
-   <span data-ttu-id="51f40-110">应用绑定的列（或参数）的序号。</span><span class="sxs-lookup"><span data-stu-id="51f40-110">Ordinal of the column (or parameter) to which the binding applies.</span></span>  
  
-   <span data-ttu-id="51f40-111">有关绑定内容的信息（例如，数据值、数据长度及其绑定状态）。</span><span class="sxs-lookup"><span data-stu-id="51f40-111">Information about what is bound (for example, data value, length of the data, and its binding status).</span></span>  
  
-   <span data-ttu-id="51f40-112">有关缓冲区中到这些部分中每个部分的偏移量的信息。</span><span class="sxs-lookup"><span data-stu-id="51f40-112">Information about what is offset in the buffer to each of these parts.</span></span>  
  
-   <span data-ttu-id="51f40-113">数据值存在于使用者缓冲区中时的长度和类型。</span><span class="sxs-lookup"><span data-stu-id="51f40-113">Length and type of the data values as they exist in the consumer buffer.</span></span>  
  
 <span data-ttu-id="51f40-114">获取数据时，访问接口将使用每个绑定中的信息来确定从使用者缓冲区的何处以及如何检索数据。</span><span class="sxs-lookup"><span data-stu-id="51f40-114">When getting the data, the provider uses information in each binding to determine where and how to retrieve data from the consumer buffer.</span></span> <span data-ttu-id="51f40-115">设置使用者缓冲区中的数据时，访问接口将使用每个绑定中的信息来确定在使用者缓冲区的何处以及如何返回数据。</span><span class="sxs-lookup"><span data-stu-id="51f40-115">When setting data in the consumer buffer, the provider uses information in each binding to determine where and how to return data in the consumer's buffer.</span></span>  
  
 <span data-ttu-id="51f40-116">指定 DBBINDING 结构后，将创建取值函数 (IAccessor::CreateAccessor)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f40-116">After the DBBINDING structures are specified, an accessor is created (**IAccessor::CreateAccessor**).</span></span> <span data-ttu-id="51f40-117">取值函数是一个绑定集合，可用于获取或设置使用者缓冲区中的数据。</span><span class="sxs-lookup"><span data-stu-id="51f40-117">An accessor is a collection of bindings and is used to get or set the data in the consumer buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f40-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51f40-118">See Also</span></span>  
 <span data-ttu-id="51f40-119">[创建 SQL Server Native Client OLE DB 提供程序应用程序](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="51f40-119">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="51f40-120">OLE DB 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="51f40-120">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
