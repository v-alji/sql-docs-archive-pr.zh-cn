---
title: 对 FILESTREAM 数据进行部分更新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 696c1a6421e14568877e24f015e5094395f1051b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692957"
---
# <a name="make-partial-updates-to-filestream-data"></a><span data-ttu-id="62107-102">对 FILESTREAM 数据进行部分更新</span><span class="sxs-lookup"><span data-stu-id="62107-102">Make Partial Updates to FILESTREAM Data</span></span>
  <span data-ttu-id="62107-103">应用程序使用 FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 对 FILESTREAM BLOB 数据进行部分更新。</span><span class="sxs-lookup"><span data-stu-id="62107-103">An application uses FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT to make partial updates to FILESTREAM BLOB data.</span></span> <span data-ttu-id="62107-104">[DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) 函数将此值和从 [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) 返回的句柄传递到 FILESTREAM 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="62107-104">The [DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) function passes this value and the handle that is returned from [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) to the FILESTREAM driver.</span></span> <span data-ttu-id="62107-105">然后，该驱动程序将当前的 FILESTREAM 数据从服务器端强制复制到该句柄所引用的文件。</span><span class="sxs-lookup"><span data-stu-id="62107-105">The driver then forces a server-side copy of the current FILESTREAM data into the file that is referenced by the handle.</span></span> <span data-ttu-id="62107-106">如果应用程序在已写入句柄后发出 FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 值，则保留最后一个写入操作，但之前对该句柄执行的写入操作将丢失。</span><span class="sxs-lookup"><span data-stu-id="62107-106">If the application issues the FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT value after the handle has been written to, the last write operation persists and previous write operations that were made to the handle are lost.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62107-107">FILESTREAM 依赖于 [SMB 协议](https://go.microsoft.com/fwlink/?LinkId=112454) 进行远程访问。</span><span class="sxs-lookup"><span data-stu-id="62107-107">FILESTREAM relies on the [SMB protocol](https://go.microsoft.com/fwlink/?LinkId=112454) for remote access.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62107-108">示例</span><span class="sxs-lookup"><span data-stu-id="62107-108">Example</span></span>  
 <span data-ttu-id="62107-109">下面的示例显示如何使用 `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` 值对插入的 FILESTREAM BLOB 执行部分更新。</span><span class="sxs-lookup"><span data-stu-id="62107-109">The following example shows you how to use the `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` value to perform a partial update of an inserted FILESTREAM BLOB.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62107-110">本示例需要在 [创建启用 FILESTREAM 的数据库](create-a-filestream-enabled-database.md) 和 [创建表以存储 FILESTREAM 数据](create-a-table-for-storing-filestream-data.md)中创建的启用了 FILESTREAM 的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="62107-110">This example requires the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a><span data-ttu-id="62107-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62107-111">See Also</span></span>  
 <span data-ttu-id="62107-112">[使用 OpenSqlFilestream 访问 FILESTREAM 数据](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="62107-112">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="62107-113">为 FILESTREAM 数据创建客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="62107-113">Create Client Applications for FILESTREAM Data</span></span>](create-client-applications-for-filestream-data.md)  
  
  
