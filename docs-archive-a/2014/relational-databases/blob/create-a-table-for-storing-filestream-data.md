---
title: 创建表以存储 FILESTREAM 数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 484d7b58ce949df79dc7e17ee4dc7307b70c0154
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689438"
---
# <a name="create-a-table-for-storing-filestream-data"></a><span data-ttu-id="36d35-102">创建表以存储 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="36d35-102">Create a Table for Storing FILESTREAM Data</span></span>
  <span data-ttu-id="36d35-103">本主题说明如何创建表以存储 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="36d35-103">This topic shows how to create a table for storing FILESTREAM data.</span></span>  
  
 <span data-ttu-id="36d35-104">如果数据库具有 FILESTREAM 文件组，则可以创建或修改表以存储 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="36d35-104">When the database has a FILESTREAM filegroup, you can create or modify tables to store FILESTREAM data.</span></span> <span data-ttu-id="36d35-105">若要指定某个列包含 FILESTREAM 数据，请创建一个 `varbinary(max)` 列并添加 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="36d35-105">To specify that a column contains FILESTREAM data, you create a `varbinary(max)` column and add the FILESTREAM attribute.</span></span>  
  
### <a name="to-create-a-table-to-store-filestream-data"></a><span data-ttu-id="36d35-106">创建表以存储 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="36d35-106">To create a table to store FILESTREAM data</span></span>  
  
1.  <span data-ttu-id="36d35-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，单击 **“新建查询”** 以显示查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="36d35-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="36d35-108">将下面示例的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码复制到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="36d35-108">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code from the following example into the Query Editor.</span></span> <span data-ttu-id="36d35-109">此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码可创建一个启用了 FILESTREAM 的表，称为 Records。</span><span class="sxs-lookup"><span data-stu-id="36d35-109">This [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled table called Records.</span></span>  
  
3.  <span data-ttu-id="36d35-110">若要创建该表，请单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="36d35-110">To create the table, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36d35-111">示例</span><span class="sxs-lookup"><span data-stu-id="36d35-111">Example</span></span>  
 <span data-ttu-id="36d35-112">下面的代码示例说明了如何创建一个名为 `Records`的表。</span><span class="sxs-lookup"><span data-stu-id="36d35-112">The following code example shows how to create a table that is named `Records`.</span></span> <span data-ttu-id="36d35-113">`Id` 列是一个 `ROWGUIDCOL` 列，通过 Win32 API 使用 FILESTREAM 数据时需要使用该列。</span><span class="sxs-lookup"><span data-stu-id="36d35-113">The `Id` column is a `ROWGUIDCOL` column and is required to use FILESTREAM data with Win32 APIs.</span></span> <span data-ttu-id="36d35-114">`SerialNumber` 列是一个 `UNIQUE INTEGER`列。</span><span class="sxs-lookup"><span data-stu-id="36d35-114">The `SerialNumber` column is a `UNIQUE INTEGER`.</span></span> <span data-ttu-id="36d35-115">`Chart` 列是一个 `FILESTREAM` 列，用于在文件系统中存储 `Chart` 。</span><span class="sxs-lookup"><span data-stu-id="36d35-115">The `Chart` column is a `FILESTREAM` column and is used to store the `Chart` in the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36d35-116">本示例是在 [创建启用了 FILESTREAM 的数据库](create-a-filestream-enabled-database.md)中创建的 Archive 数据库。</span><span class="sxs-lookup"><span data-stu-id="36d35-116">This example refers to the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_createtable)]  
  
## <a name="see-also"></a><span data-ttu-id="36d35-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36d35-117">See Also</span></span>  
 <span data-ttu-id="36d35-118">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36d35-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 [<span data-ttu-id="36d35-119">ALTER TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="36d35-119">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
