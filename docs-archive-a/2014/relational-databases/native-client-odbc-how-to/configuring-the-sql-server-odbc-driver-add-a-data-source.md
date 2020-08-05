---
title: " (ODBC) 中添加数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: rothja
ms.author: jroth
ms.openlocfilehash: 519990e9dd9d84f75c4efc6c76b910f0a359f52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580239"
---
# <a name="add-a-data-source-odbc"></a><span data-ttu-id="b82c4-102">添加数据源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="b82c4-102">Add a Data Source (ODBC)</span></span>
  <span data-ttu-id="b82c4-103">您可以使用 ODBC 管理器添加数据源，通过使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) 或创建文件以编程方式 (。</span><span class="sxs-lookup"><span data-stu-id="b82c4-103">You can add a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by creating a file.</span></span>  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="b82c4-104">使用 ODBC 管理器添加数据源</span><span class="sxs-lookup"><span data-stu-id="b82c4-104">To add a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="b82c4-105">从 "**控制面板**" 中，访问 "**管理工具**"，然后\*\* (ODBC) \*\*上的 "数据源"。</span><span class="sxs-lookup"><span data-stu-id="b82c4-105">From the **Control Panel**, access **Administrative Tools** and then **Data Sources (ODBC)**.</span></span> <span data-ttu-id="b82c4-106">或者，可以调用 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="b82c4-106">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="b82c4-107">单击 "**用户 dsn**"、"**系统 dsn**" 或 "**文件 dsn** " 选项卡，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="b82c4-107">Click the **User DSN**, **System DSN**, or **File DSN** tab, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="b82c4-108">单击 " **SQL Server**"，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="b82c4-108">Click **SQL Server**, and then click **Finish**.</span></span>  
  
4.  <span data-ttu-id="b82c4-109">完成创建到 SQL Server 的新数据源向导中的步骤。</span><span class="sxs-lookup"><span data-stu-id="b82c4-109">Complete the Steps in the Create a New Data Source to SQL Server Wizard.</span></span>  
  
### <a name="to-add-a-data-source-programmatically"></a><span data-ttu-id="b82c4-110">以编程方式添加数据源</span><span class="sxs-lookup"><span data-stu-id="b82c4-110">To add a data source programmatically</span></span>  
  
1.  <span data-ttu-id="b82c4-111">调用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) ，并将第二个参数设置为 ODBC_ADD_DSN 或 ODBC_ADD_SYS_DSN。</span><span class="sxs-lookup"><span data-stu-id="b82c4-111">Call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) with the second parameter set to either ODBC_ADD_DSN or ODBC_ADD_SYS_DSN.</span></span>  
  
### <a name="to-add-a-file-data-source"></a><span data-ttu-id="b82c4-112">添加文件数据源</span><span class="sxs-lookup"><span data-stu-id="b82c4-112">To add a file data source</span></span>  
  
1.  <span data-ttu-id="b82c4-113">使用连接字符串中的 SAVEFILE = file_name 参数调用[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 。</span><span class="sxs-lookup"><span data-stu-id="b82c4-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) with a SAVEFILE=file_name parameter in the connect string.</span></span> <span data-ttu-id="b82c4-114">如果连接成功，则 ODBC 驱动程序将使用 SAVEFILE 参数指向的位置中的连接参数创建一个文件数据源。</span><span class="sxs-lookup"><span data-stu-id="b82c4-114">If the connect is successful, the ODBC driver creates a file data source with the connection parameters in the location pointed to by the SAVEFILE parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82c4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b82c4-115">See Also</span></span>  
 [<span data-ttu-id="b82c4-116">配置 SQL Server ODBC 驱动程序操作指南主题</span><span class="sxs-lookup"><span data-stu-id="b82c4-116">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
