---
title: 使用 IRow 提取单行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589528"
---
# <a name="fetching-a-single-row-with-irow"></a><span data-ttu-id="b00ee-102">使用 IRow 提取单行</span><span class="sxs-lookup"><span data-stu-id="b00ee-102">Fetching a Single Row with IRow</span></span>
  <span data-ttu-id="b00ee-103">OLE DB 提供程序中的**IRow**接口实现进行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 了简化，以提高性能。</span><span class="sxs-lookup"><span data-stu-id="b00ee-103">The **IRow** interface implementation in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is simplified to increase performance.</span></span> <span data-ttu-id="b00ee-104">IRow 允许直接访问单行对象的列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-104">**IRow** allows direct access to columns of a single row object.</span></span> <span data-ttu-id="b00ee-105">如果预先知道命令执行的结果确实是生成单行，则 IRow 将检索该行的列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-105">If you know beforehand that the result of a command execution will produce exactly one row, **IRow** will retrieve the columns of that row.</span></span> <span data-ttu-id="b00ee-106">如果结果集包括多行，则 IRow 将只显示第一行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-106">If the result set includes multiple rows, **IRow** will expose only the first row.</span></span>  
  
 <span data-ttu-id="b00ee-107">IRow 实现不允许行的任何导航\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-107">The **IRow** implementation does not allow any navigation of the row.</span></span> <span data-ttu-id="b00ee-108">行中的每一列只能访问一次，以下情况例外：可以访问一次列以查找列大小，再次访问以提取数据。</span><span class="sxs-lookup"><span data-stu-id="b00ee-108">Each column in the row is accessed only one time with one exception: A column can be accessed one time to find the column size and again to fetch the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b00ee-109">IRow::Open 只支持打开 DBGUID_STREAM 和 DBGUID_NULL 对象类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-109">**IRow::Open** supports only DBGUID_STREAM and DBGUID_NULL type of objects to be opened.</span></span>  
  
 <span data-ttu-id="b00ee-110">若要使用 ICommand::Execute 方法获得行对象，必须传递 IID_IRow\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-110">To obtain a row object using **ICommand::Execute** method, IID_IRow must be passed.</span></span> <span data-ttu-id="b00ee-111">必须使用 IMultipleResults 接口处理多个结果集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-111">The **IMultipleResults** interface must be used to handle multiple result sets.</span></span> <span data-ttu-id="b00ee-112">IMultipleResults 支持 IRow 和 IRowset\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-112">**IMultipleResults** supports **IRow** and **IRowset**.</span></span> <span data-ttu-id="b00ee-113">IRowset 用于大容量操作\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b00ee-113">**IRowset** is used for bulk operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b00ee-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="b00ee-114">In This Section</span></span>  
  
-   [<span data-ttu-id="b00ee-115">使用 IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="b00ee-115">Using IRow::GetColumns</span></span>](using-irow-getcolumns.md)  
  
-   [<span data-ttu-id="b00ee-116">使用 IRow 提取 BLOB 数据</span><span class="sxs-lookup"><span data-stu-id="b00ee-116">Fetching BLOB Data Using IRow</span></span>](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a><span data-ttu-id="b00ee-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b00ee-117">See Also</span></span>  
 [<span data-ttu-id="b00ee-118">行集</span><span class="sxs-lookup"><span data-stu-id="b00ee-118">Rowsets</span></span>](rowsets.md)  
  
  
