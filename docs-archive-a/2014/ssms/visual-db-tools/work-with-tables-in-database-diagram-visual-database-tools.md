---
title: 使用数据库关系图中的表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f648cd5fd08ed47c6670491ad5b7f3d75b7ead47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588189"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a><span data-ttu-id="94b0e-102">使用数据库关系图中的表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-102">Work with Tables in Database Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="94b0e-103">您可以在表设计器或数据库关系图设计器中修改和创建数据库表。</span><span class="sxs-lookup"><span data-stu-id="94b0e-103">You can modify and create database tables in either Table Designer or Database Diagram Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94b0e-104">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="94b0e-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="94b0e-105">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="94b0e-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="94b0e-106">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="94b0e-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94b0e-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="94b0e-107">In This Section</span></span>  
 [<span data-ttu-id="94b0e-108">向关系图中添加表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-108">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-109">向关系图中添加相关的表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-109">Add Related Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-related-tables-to-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-110">保存关系图中所选的表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-110">Save Selected Tables on a Diagram &#40;Visual Database Tools&#41;</span></span>](save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-111">将表从一个数据库关系图复制到另一个数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-111">Copy Tables from One Database Diagrams to Another &#40;Visual Database Tools&#41;</span></span>](copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-112">从数据库关系图中移除表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-112">Remove Tables from Database Diagrams &#40;Visual Database Tools&#41;</span></span>](remove-tables-from-database-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-113">映射多对多关系 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-113">Map Many-to-Many Relationships &#40;Visual Database Tools&#41;</span></span>](map-many-to-many-relationships-visual-database-tools.md)  
  
 [<span data-ttu-id="94b0e-114">绘制自反关系 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-114">Draw Reflexive Relationships &#40;Visual Database Tools&#41;</span></span>](draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a><span data-ttu-id="94b0e-115">参考</span><span class="sxs-lookup"><span data-stu-id="94b0e-115">Reference</span></span>  
 [<span data-ttu-id="94b0e-116">“添加表”对话框（数据库设计器）(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94b0e-116">Add Table Dialog Box &#40;Database Designer&#41; &#40;Visual Database Tools&#41;</span></span>](add-table-dialog-box-database-designer-visual-database-tools.md)  
  
## <a name="related-sections"></a><span data-ttu-id="94b0e-117">相关章节</span><span class="sxs-lookup"><span data-stu-id="94b0e-117">Related Sections</span></span>  
  
