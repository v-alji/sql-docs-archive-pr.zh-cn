---
title: 在 SQL Server 中使用用户定义的类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- user-defined types [CLR integration], queries
- UDTs [CLR integration], queries
- user-defined types [CLR integration], Transact-SQL
- UDTs [CLR integration], Transact-SQL
- queries [CLR integration]
ms.assetid: 807376fb-1f1a-4f2a-8cf8-a622c5858634
author: rothja
ms.author: jroth
ms.openlocfilehash: c9fed9ad4e73102eadd1374ff87d2a46d0ff4126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688950"
---
# <a name="working-with-user-defined-types-in-sql-server"></a><span data-ttu-id="a6f68-102">使用 SQL Server 中的用户定义类型</span><span class="sxs-lookup"><span data-stu-id="a6f68-102">Working with User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="a6f68-103">您可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 通过使用常规查询语法，从语言中 (UDT) 功能访问用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="a6f68-103">You can access user-defined type (UDT) functionality in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[tsql](../../includes/tsql-md.md)] language by using regular query syntax.</span></span> <span data-ttu-id="a6f68-104">UDT 可以用在数据库对象的定义中，作为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批、函数和存储过程中的变量，以及作为函数和存储过程中的参数。</span><span class="sxs-lookup"><span data-stu-id="a6f68-104">UDTs can be used in the definition of database objects, as variables in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, in functions and stored procedures, and as arguments in functions and stored procedures.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6f68-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="a6f68-105">In This Section</span></span>  
 [<span data-ttu-id="a6f68-106">定义 UDT 表和列</span><span class="sxs-lookup"><span data-stu-id="a6f68-106">Defining UDT Tables and Columns</span></span>](working-with-user-defined-types-defining-udt-tables-and-columns.md)  
 <span data-ttu-id="a6f68-107">介绍如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在表中创建 UDT 列。</span><span class="sxs-lookup"><span data-stu-id="a6f68-107">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a UDT column in a table.</span></span>  
  
 [<span data-ttu-id="a6f68-108">操作 UDT 数据</span><span class="sxs-lookup"><span data-stu-id="a6f68-108">Manipulating UDT Data</span></span>](working-with-user-defined-types-manipulating-udt-data.md)  
 <span data-ttu-id="a6f68-109">介绍如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中处理 UDT 数据。</span><span class="sxs-lookup"><span data-stu-id="a6f68-109">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to work with UDT data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f68-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6f68-110">See Also</span></span>  
 [<span data-ttu-id="a6f68-111">CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="a6f68-111">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
