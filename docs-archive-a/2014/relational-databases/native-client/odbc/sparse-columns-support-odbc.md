---
title: 稀疏列支持 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 076709f3f37e92492f7c3f8c20ee692416d9e867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690586"
---
# <a name="sparse-columns-support-odbc"></a><span data-ttu-id="a4e1d-102">稀疏列支持 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a4e1d-102">Sparse Columns Support (ODBC)</span></span>
  <span data-ttu-id="a4e1d-103">本主题描述对稀疏列的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 支持。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-103">This topic describes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC support for sparse columns.</span></span> <span data-ttu-id="a4e1d-104">有关演示 ODBC 对稀疏列的支持的示例，请参阅对[具有稀疏列的表调用 SQLColumns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-104">For a sample demonstrating ODBC support for sparse columns, see [Call SQLColumns on a Table with Sparse Columns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md).</span></span> <span data-ttu-id="a4e1d-105">有关稀疏列的详细信息，请参阅[SQL Server Native Client 中的稀疏列支持](../features/sparse-columns-support-in-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-105">For more information about sparse columns, see [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).</span></span>  
  
## <a name="statement-metadata"></a><span data-ttu-id="a4e1d-106">语句元数据</span><span class="sxs-lookup"><span data-stu-id="a4e1d-106">Statement Metadata</span></span>  
 <span data-ttu-id="a4e1d-107">应用程序参数描述符 (APD) 字段和 SQL_SOPT_SS_NAME_SCOPE 语句属性接受新增的值 SQL_SS_NAME_SCOPE_EXTENDED 和 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-107">The application parameter descriptor (APD) descriptor field and SQL_SOPT_SS_NAME_SCOPE statement attribute accepts the additional values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span> <span data-ttu-id="a4e1d-108">这些值指定由[SQLColumns](../../native-client-odbc-api/sqlcolumns.md)返回的结果集中包含的列。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-108">These values specify which columns are included in the result set returned by [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span> <span data-ttu-id="a4e1d-109">有关 SQL_SOPT_SS_NAME_SCOPE 的详细信息，请参阅[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-109">For more information about SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="a4e1d-110">新的实现行描述符 (IRD) 是称为 SQL_CA_SS_IS_COLUMN_SET 的只读 SQLSMALLINT 字段，它可以用于确定列是否是 XML `column_set` 值。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-110">A new implementation row descriptor (IRD), a read-only SQLSMALLINT field called SQL_CA_SS_IS_COLUMN_SET, can be used to determine if a column is an XML `column_set` value.</span></span> <span data-ttu-id="a4e1d-111">SQL_CA_SS_IS_COLUMN_SET 接受值 SQL_TRUE 和 SQL_FALSE。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-111">SQL_CA_SS_IS_COLUMN_SET takes the values SQL_TRUE and SQL_FALSE.</span></span>  
  
## <a name="catalog-metadata"></a><span data-ttu-id="a4e1d-112">目录元数据</span><span class="sxs-lookup"><span data-stu-id="a4e1d-112">Catalog Metadata</span></span>  
 <span data-ttu-id="a4e1d-113">向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)的结果集中添加了两个特定列 (SS_IS_SPARSE 和 SS_IS_COLUMN_SET) 。</span><span class="sxs-lookup"><span data-stu-id="a4e1d-113">Two [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific columns (SS_IS_SPARSE and SS_IS_COLUMN_SET) have been added to the result set for [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="odbc-function-support-for-sparse-columns"></a><span data-ttu-id="a4e1d-114">对稀疏列的 ODBC 函数支持</span><span class="sxs-lookup"><span data-stu-id="a4e1d-114">ODBC Function Support for Sparse Columns</span></span>  
 <span data-ttu-id="a4e1d-115">以下 ODBC 函数已进行更新，以便在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中支持稀疏列：</span><span class="sxs-lookup"><span data-stu-id="a4e1d-115">The following ODBC functions have been updated to support sparse columns in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   [<span data-ttu-id="a4e1d-116">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="a4e1d-116">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="a4e1d-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="a4e1d-117">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="a4e1d-118">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="a4e1d-118">SQLGetDescField</span></span>](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [<span data-ttu-id="a4e1d-119">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="a4e1d-119">SQLSetDescField</span></span>](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [<span data-ttu-id="a4e1d-120">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="a4e1d-120">SQLSetStmtAttr</span></span>](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4e1d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4e1d-121">See Also</span></span>  
 [<span data-ttu-id="a4e1d-122">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a4e1d-122">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
