---
title: " (ODBC) 中删除数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e8acd6414b39b317ff0fcfe1b7b9fbab38ae0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580237"
---
# <a name="delete-a-data-source-odbc"></a><span data-ttu-id="76ca2-102">删除数据源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="76ca2-102">Delete a Data Source (ODBC)</span></span>
  <span data-ttu-id="76ca2-103">您可以使用 ODBC 管理器删除数据源，通过使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) 以编程方式 (; 或者通过删除文件 (如果文件数据源名称) 来删除文件。</span><span class="sxs-lookup"><span data-stu-id="76ca2-103">You can delete a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by deleting a file (if a file data source name).</span></span>  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="76ca2-104">通过使用 ODBC 管理器删除数据源</span><span class="sxs-lookup"><span data-stu-id="76ca2-104">To delete a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="76ca2-105">在 "**控制面板**" 中，打开 "**管理工具**"，然后双击 " \*\* (ODBC) \*\*中的" 数据源 "。</span><span class="sxs-lookup"><span data-stu-id="76ca2-105">In **Control Panel**, open **Administrative Tools**, and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="76ca2-106">或者，也可以从命令提示符处运行 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="76ca2-106">Alternatively, you can run odbcad32.exe from the command prompt.</span></span>  
  
2.  <span data-ttu-id="76ca2-107">单击 "**用户 dsn**"、"**系统 dsn**" 或 "**文件 dsn** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="76ca2-107">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="76ca2-108">单击要删除的数据源。</span><span class="sxs-lookup"><span data-stu-id="76ca2-108">Click the data source to delete.</span></span>  
  
4.  <span data-ttu-id="76ca2-109">单击 "**删除**"，然后确认删除。</span><span class="sxs-lookup"><span data-stu-id="76ca2-109">Click **Remove**, and then confirm the deletion.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ca2-110">示例</span><span class="sxs-lookup"><span data-stu-id="76ca2-110">Example</span></span>  
 <span data-ttu-id="76ca2-111">若要以编程方式删除数据源，请使用 ODBC_REMOVE_DSN 或 ODBC_REMOVE_SYS_DSN 作为第二个参数来调用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 。</span><span class="sxs-lookup"><span data-stu-id="76ca2-111">To programmatically delete a data source, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) using either ODBC_REMOVE_DSN or ODBC_REMOVE_SYS_DSN as the second parameter.</span></span>  
  
 <span data-ttu-id="76ca2-112">以下示例显示如何以编程方式删除数据源。</span><span class="sxs-lookup"><span data-stu-id="76ca2-112">The following sample shows how you can programmatically delete a data source.</span></span>  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="76ca2-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76ca2-113">See Also</span></span>  
 [<span data-ttu-id="76ca2-114">配置 SQL Server ODBC 驱动程序操作指南主题</span><span class="sxs-lookup"><span data-stu-id="76ca2-114">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
