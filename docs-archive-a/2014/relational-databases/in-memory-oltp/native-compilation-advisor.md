---
title: 本机编译顾问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: b2182d89489af5da8bc3b85b89484fbbf72e4dfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693870"
---
# <a name="native-compilation-advisor"></a><span data-ttu-id="fc545-102">本机编译顾问</span><span class="sxs-lookup"><span data-stu-id="fc545-102">Native Compilation Advisor</span></span>
  <span data-ttu-id="fc545-103">事务性能报告工具 (参阅[确定表或存储过程是否应移植到内存中 OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) 通知您数据库中哪些解释的存储过程在移植到使用本机编译时将会受益。</span><span class="sxs-lookup"><span data-stu-id="fc545-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which interpreted stored procedures in your database will benefit if ported to use native compilation.</span></span> <span data-ttu-id="fc545-104">在您标识要移植到使用本机编译的存储过程后，可以使用本机编译顾问来帮助您将已解释的存储过程迁移到本地编译。</span><span class="sxs-lookup"><span data-stu-id="fc545-104">After you identify a stored procedure that you would like to port to use native compilation, you can use the native compilation advisor to help you migrate the interpreted stored procedure to native compilation.</span></span> <span data-ttu-id="fc545-105">有关本机编译的存储过程的详细信息，请参阅 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="fc545-105">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="fc545-106">开始时，连接至包含已解释的存储过程的实例。</span><span class="sxs-lookup"><span data-stu-id="fc545-106">To begin, connect to the instance that contains the interpreted stored procedure.</span></span> <span data-ttu-id="fc545-107">您可以连接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="fc545-107">You can connect to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="fc545-108">但是，如果您想要使用该顾问执行迁移操作，则必须连接到启用了内存中 OLTP 功能的 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="fc545-108">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="fc545-109">有关内存中 OLTP 要求的详细信息，请参阅 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="fc545-109">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="fc545-110">有关迁移方法的信息，请参阅 [内存中 OLTP - 常见的工作负荷模式和迁移注意事项](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fc545-110">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a><span data-ttu-id="fc545-111">使用本机编译顾问的演练</span><span class="sxs-lookup"><span data-stu-id="fc545-111">Walkthrough Using the Native Compilation Advisor</span></span>  
 <span data-ttu-id="fc545-112">在 **对象资源管理器**中，右键单击要转换的存储过程，然后选择 **“本机编译顾问”** 。</span><span class="sxs-lookup"><span data-stu-id="fc545-112">In **Object Explorer**, right click the stored procedure you want to convert, and select **Native Compilation Advisor**.</span></span> <span data-ttu-id="fc545-113">这将显示 **“存储过程本机编译顾问”** 的欢迎使用页。</span><span class="sxs-lookup"><span data-stu-id="fc545-113">This will display the welcome page for the **Stored Procedure Native Compilation Advisor**.</span></span> <span data-ttu-id="fc545-114">单击“下一步”以继续。</span><span class="sxs-lookup"><span data-stu-id="fc545-114">Click **Next** to continue.</span></span>  
  
### <a name="stored-procedure-validation"></a><span data-ttu-id="fc545-115">存储过程验证</span><span class="sxs-lookup"><span data-stu-id="fc545-115">Stored Procedure Validation</span></span>  
 <span data-ttu-id="fc545-116">此页将报告存储过程是否使用与本机编译不兼容的任何构造。</span><span class="sxs-lookup"><span data-stu-id="fc545-116">This page will report if the stored procedure uses any constructs that are not compatible with native compilation.</span></span> <span data-ttu-id="fc545-117">您可以单击 **“下一步”** 查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc545-117">You can click **Next** to see details.</span></span> <span data-ttu-id="fc545-118">如果存在与本机编译不兼容的构造，可以单击 **“下一步”** 查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc545-118">If there are constructs that are not compatible with native compilation, you can click **Next** to see details.</span></span>  
  
### <a name="stored-procedure-validation-result"></a><span data-ttu-id="fc545-119">存储过程验证结果</span><span class="sxs-lookup"><span data-stu-id="fc545-119">Stored Procedure Validation Result</span></span>  
 <span data-ttu-id="fc545-120">如果存在与本机编译不兼容的构造，则 **“存储过程验证结果”** 页将显示详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc545-120">If there are constructs that are not compatible with native compilation, the **Stored Procedure Validation Result** page will display details.</span></span> <span data-ttu-id="fc545-121">你可以生成报表（单击“生成报表”）、退出“本机编译顾问”以及更新你的代码以便它与本机编译兼容。</span><span class="sxs-lookup"><span data-stu-id="fc545-121">You can generate a report (click **Generate Report**), exit the **Native Compilation Advisor**, and update your code so that it is compatible with native compilation.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="fc545-122">代码示例</span><span class="sxs-lookup"><span data-stu-id="fc545-122">Code Sample</span></span>  
 <span data-ttu-id="fc545-123">下面的示例显示了一个已解释的存储过程以及针对本机编译的等效存储过程。</span><span class="sxs-lookup"><span data-stu-id="fc545-123">The following sample shows an interpreted stored procedure and the equivalent stored procedure for native compilation.</span></span> <span data-ttu-id="fc545-124">该示例假定名为 c:\data 的目录。</span><span class="sxs-lookup"><span data-stu-id="fc545-124">The sample assumes a directory called c:\data.</span></span>  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc545-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc545-125">See Also</span></span>  
 [<span data-ttu-id="fc545-126">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="fc545-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
