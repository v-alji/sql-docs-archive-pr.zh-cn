---
title: SqlDataRecord 对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlDataRecord object
- custom result sets [CLR integration]
ms.assetid: 2ed667fb-749c-4280-a8fb-650643683c8f
author: rothja
ms.author: jroth
ms.openlocfilehash: 87a26f5a2ff5fc6af73a30a7ca28d78c2b5ee52b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581316"
---
# <a name="sqldatarecord-object"></a><span data-ttu-id="07d92-102">SqlDataRecord 对象</span><span class="sxs-lookup"><span data-stu-id="07d92-102">SqlDataRecord Object</span></span>
  <span data-ttu-id="07d92-103">`SqlDataRecord` 对象表示一行数据及其相关元数据。</span><span class="sxs-lookup"><span data-stu-id="07d92-103">The `SqlDataRecord` object represents a single row of data, along with its related metadata.</span></span>  
  
 <span data-ttu-id="07d92-104">托管存储过程可以发送到并非来自于 `SqlDataReader` 的客户端结果集。</span><span class="sxs-lookup"><span data-stu-id="07d92-104">Managed stored procedures may send to the client result sets that are not from a `SqlDataReader`.</span></span> <span data-ttu-id="07d92-105">`SqlDataRecord` 类以及 `SendResultsStart` 对象的 `SendResultsRow`、`SendResultsEnd` 和 `SqlPipe` 方法允许存储过程将自定义结果集发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="07d92-105">The `SqlDataRecord` class, along with `SendResultsStart`, `SendResultsRow`, and `SendResultsEnd` methods of the `SqlPipe` object, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="07d92-106">有关详细信息，请参阅 `Microsoft.SqlServer.Server.SqlDataRecord` .NET FRAMEWORK SDK 文档中的类参考文档。</span><span class="sxs-lookup"><span data-stu-id="07d92-106">For more information, see the `Microsoft.SqlServer.Server.SqlDataRecord` class reference documentation in the .NET Framework SDK documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d92-107">示例</span><span class="sxs-lookup"><span data-stu-id="07d92-107">Example</span></span>  
 <span data-ttu-id="07d92-108">下面的示例创建一个新雇员记录并将其返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="07d92-108">The following example creates a new employee record and returns it to the caller.</span></span>  
  
 <span data-ttu-id="07d92-109">C#</span><span class="sxs-lookup"><span data-stu-id="07d92-109">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void CreateNewRecordProc()  
{  
    // Variables.         
    SqlDataRecord record;  
  
    // Create a new record with the column metadata.  The constructor   
    // is able to accept a variable number of parameters.  
    record = new SqlDataRecord(new SqlMetaData("EmployeeID", SqlDbType.Int),  
                               new SqlMetaData("Surname", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("GivenName", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("StartDate", SqlDbType.DateTime) );  
  
    // Set the record fields.  
    record.SetInt32(0, 0042);  
    record.SetString(1, "Funk");  
    record.SetString(2, "Don");  
    record.SetDateTime(3, new DateTime(2005, 7, 17));  
  
    // Send the record to the calling program.  
    SqlContext.Pipe.Send(record);  
  
}  
```  
  
 <span data-ttu-id="07d92-110">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07d92-110">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  CreateNewRecordVBProc ()  
    ' Variables.  
    Dim record As SqlDataRecord  
  
    ' Create a new record with the column metadata. The constructor is   
    ' able to accept a variable number of parameters  
  
    record = New SqlDataRecord(New SqlMetaData("EmployeeID", SqlDbType.Int), _  
                           New SqlMetaData("Surname", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("GivenName", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("StartDate", SqlDbType.DateTime))  
  
    ' Set the record fields.  
    record.SetInt32(0, 42)  
    record.SetString(1, "Funk")  
    record.SetString(2, "Don")  
    record.SetDateTime(3, New DateTime(2005, 7, 17))  
  
    ' Send the record to the calling program.  
    SqlContext.Pipe.Send(record)  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="07d92-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07d92-111">See Also</span></span>  
 [<span data-ttu-id="07d92-112">SqlPipe 对象</span><span class="sxs-lookup"><span data-stu-id="07d92-112">SqlPipe Object</span></span>](sqlpipe-object.md)  
  
  
