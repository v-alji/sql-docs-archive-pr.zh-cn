---
title: 批处理方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c778da186fdbbfaed17b9635d9ca7309a369552b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590036"
---
# <a name="batching-methods"></a><span data-ttu-id="1f015-102">批处理方法</span><span class="sxs-lookup"><span data-stu-id="1f015-102">Batching Methods</span></span>
  <span data-ttu-id="1f015-103">通过在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中使用 SOAP 标头，您可以在单个操作中包含多个 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="1f015-103">The use of SOAP headers in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables you to include multiple Web service methods in a single operation.</span></span> <span data-ttu-id="1f015-104">方法在单个数据库事务的作用域中按照调用它们的顺序运行。</span><span class="sxs-lookup"><span data-stu-id="1f015-104">Methods run within the scope of a single database transaction, in the order in which they are called.</span></span>  
  
 <span data-ttu-id="1f015-105">回滚是使用多方法批处理操作的一个优势。</span><span class="sxs-lookup"><span data-stu-id="1f015-105">Rollback is one advantage of using multiple-method batch operations.</span></span> <span data-ttu-id="1f015-106">如果在运行某一批处理时对于任何方法调用出现错误，报表服务器将停止运行此批处理并回滚任何先前的操作。</span><span class="sxs-lookup"><span data-stu-id="1f015-106">If an error occurs on any of the method calls while a batch is running, the report server stops running the batch and rolls back any previous operations.</span></span> <span data-ttu-id="1f015-107">当某个方法调用依赖于成功完成该批处理中的其他方法调用时，这一点很有用。</span><span class="sxs-lookup"><span data-stu-id="1f015-107">This is useful when a method call depends on the successful completion of other method calls in that batch.</span></span>  
  
 <span data-ttu-id="1f015-108">Web 服务对于多方法批处理操作不提供锁定语义。</span><span class="sxs-lookup"><span data-stu-id="1f015-108">The Web service does not provide locking semantics for multiple-method batch operations.</span></span> <span data-ttu-id="1f015-109">在向服务器发送消息并且调用 Execute 命令之前，将不锁定报表服务器数据库中的行进行更新。</span><span class="sxs-lookup"><span data-stu-id="1f015-109">Rows in the report server database are not locked for updating until the message is sent to the server and the Execute command is called.</span></span>  
  
 <span data-ttu-id="1f015-110">此外，没有并发控制来保证数据库自上次读取数据之后尚未发生变化。</span><span class="sxs-lookup"><span data-stu-id="1f015-110">There are also no concurrency controls to guarantee that the database has not changed since the data was last read.</span></span> <span data-ttu-id="1f015-111">如果两个客户端修改同一项，当参数仍然有效（例如，尚未重命名该项）时，最后一次更新将成功。</span><span class="sxs-lookup"><span data-stu-id="1f015-111">If two clients modify the same item, the last update succeeds if the parameters are still valid (for example, the item has not been renamed).</span></span>  
  
 <span data-ttu-id="1f015-112">以下示例调用 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 方法三次，并将这些调用作为单个批处理运行。</span><span class="sxs-lookup"><span data-stu-id="1f015-112">The following example calls the <xref:ReportService2005.ReportingService2005.CreateFolder%2A> method three times and runs these calls as a single batch.</span></span> <span data-ttu-id="1f015-113">如果对于 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 的任何调用失败，将取消整个批处理。</span><span class="sxs-lookup"><span data-stu-id="1f015-113">If any of the calls to <xref:ReportService2005.ReportingService2005.CreateFolder%2A> fail, the entire batch is canceled.</span></span>  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f015-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f015-114">See Also</span></span>  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 <span data-ttu-id="1f015-115">[SSRS&#41;&#40;技术参考](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1f015-115">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="1f015-116">使用 Reporting Services SOAP 标头</span><span class="sxs-lookup"><span data-stu-id="1f015-116">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
