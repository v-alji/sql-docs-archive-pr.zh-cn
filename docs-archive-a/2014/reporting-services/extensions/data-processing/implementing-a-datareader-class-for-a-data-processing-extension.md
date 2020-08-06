---
title: 为数据处理扩展插件实现 DataReader 类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c9e55741c72d624b7149435ced90550135d8b4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693634"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a><span data-ttu-id="8d787-102">为数据处理扩展插件实现 DataReader 类</span><span class="sxs-lookup"><span data-stu-id="8d787-102">Implementing a DataReader Class for a Data Processing Extension</span></span>
  <span data-ttu-id="8d787-103">DataReader 对象使客户端可以从数据源检索只读、只进的数据流  。</span><span class="sxs-lookup"><span data-stu-id="8d787-103">The **DataReader** object enables a client to retrieve a read-only, forward-only stream of data from a data source.</span></span> <span data-ttu-id="8d787-104">结果作为查询执行返回，并且存储于客户端上的网络缓冲区中，直到使用 DataReader 类的读取方法请求它们   。</span><span class="sxs-lookup"><span data-stu-id="8d787-104">Results are returned as the query executes and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader** class.</span></span> <span data-ttu-id="8d787-105">要创建 DataReader 类，请实现 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>，并可以选择实现 <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>。</span><span class="sxs-lookup"><span data-stu-id="8d787-105">To create a **DataReader** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and optionally implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>.</span></span> <span data-ttu-id="8d787-106">使用 DataReader 对象可以从多方面提高应用程序性能，包括可以在数据可用时立刻检索数据，而非等待返回整个查询结果，以及在内存中每次只存储一行（默认情况下），从而降低系统开销  。</span><span class="sxs-lookup"><span data-stu-id="8d787-106">Using a **DataReader** object increases application performance both by retrieving data as soon as it is available, rather than waiting for the entire results of the query to be returned, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="8d787-107">在创建 Command 类的某一实例后，通过调用 Command.ExecuteReader 创建一个 DataReader 对象，以便从数据源检索行    。</span><span class="sxs-lookup"><span data-stu-id="8d787-107">After creating an instance of your **Command** class, you create a **DataReader** object by calling **Command.ExecuteReader** to retrieve rows from the data source.</span></span> <span data-ttu-id="8d787-108">DataReader 实现必须提供两个基本的功能：对通过执行某一命令获取的结果集进行只进访问，以及访问每一行内的列类型、名称和值  。</span><span class="sxs-lookup"><span data-stu-id="8d787-108">The **DataReader** implementation must provide two basic capabilities: forward-only access over the result sets obtained by executing a command and access to the column types, names, and values within each row.</span></span> <span data-ttu-id="8d787-109">客户端使用 DataReader 对象的读取方法从查询的结果获取某一行   。</span><span class="sxs-lookup"><span data-stu-id="8d787-109">Clients use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span>  
  
 <span data-ttu-id="8d787-110">在报表设计器中，DataReader 对象用于检索字段列表以及与结果集有关的架构信息  。</span><span class="sxs-lookup"><span data-stu-id="8d787-110">In Report Designer, your **DataReader** object is used to retrieve a list of fields as well as schema information about the result set.</span></span> <span data-ttu-id="8d787-111">这是通过实现 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 接口的 GetName、GetValue、GetFieldType 和 GetOrdinal 方法实现的。</span><span class="sxs-lookup"><span data-stu-id="8d787-111">This is accomplished by implementing the **GetName**, **GetValue**, **GetFieldType,** and **GetOrdinal** methods of the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interface.</span></span>  
  
 <span data-ttu-id="8d787-112"><xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> 接口可用于提供与结果集有关的特定聚合信息。</span><span class="sxs-lookup"><span data-stu-id="8d787-112">The <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> interface allows you to supply specific aggregation information about your result set.</span></span> <span data-ttu-id="8d787-113">有关示例 DataReader 类实现，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="8d787-113">For a sample **DataReader** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d787-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d787-114">See Also</span></span>  
 <span data-ttu-id="8d787-115">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8d787-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="8d787-116">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="8d787-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="8d787-117">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="8d787-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
