---
title: 数据源名称和64位操作系统 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579552"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a><span data-ttu-id="c2c71-102">数据源名称和 64 位操作系统</span><span class="sxs-lookup"><span data-stu-id="c2c71-102">Data Source Names and 64-Bit Operating Systems</span></span>
  <span data-ttu-id="c2c71-103">如果您要将某一应用程序构建为在 64 位操作系统上运行的 32 位应用程序并运行该应用程序，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="c2c71-103">To build and run an application as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2c71-104">备注</span><span class="sxs-lookup"><span data-stu-id="c2c71-104">Remarks</span></span>  
 <span data-ttu-id="c2c71-105">64 位 Windows 操作系统具有以下两个 odbcad32.exe 文件：</span><span class="sxs-lookup"><span data-stu-id="c2c71-105">A 64-bit Windows operating system has two odbcad32.exe files:</span></span>  
  
-   <span data-ttu-id="c2c71-106">%SystemRoot%\system32\odbcad32.exe 用于为 64 位应用程序创建和维护数据源名称。</span><span class="sxs-lookup"><span data-stu-id="c2c71-106">%SystemRoot%\system32\odbcad32.exe is used to create and maintain data source names for 64-bit applications.</span></span>  
  
-   <span data-ttu-id="c2c71-107">%SystemRoot%\SysWOW64\odbcad32.exe 用于为 32 位应用程序（包括在 64 位操作系统上运行的 32 位应用程序）创建和维护数据源名称。</span><span class="sxs-lookup"><span data-stu-id="c2c71-107">%SystemRoot%\SysWOW64\odbcad32.exe is used to create and maintain data source names for 32-bit applications, including 32-bit applications that run on 64-bit operating systems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c71-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2c71-108">See Also</span></span>  
 [<span data-ttu-id="c2c71-109">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c2c71-109">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
