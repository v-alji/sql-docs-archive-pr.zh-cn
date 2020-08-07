---
title: Create Table SQL 语句（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3fc2054711708a27691f2d7219c33749f11b977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588637"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a><span data-ttu-id="b60c5-102">Create Table SQL 语句（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="b60c5-102">Create Table SQL Statement (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="b60c5-103">使用 "**创建表 SQL 语句**" 对话框可以查看自动生成的语句，或根据需要修改该语句。</span><span class="sxs-lookup"><span data-stu-id="b60c5-103">Use the **Create Table SQL Statement** dialog box to view the statement that was generated automatically, or to modify it for your purposes.</span></span> <span data-ttu-id="b60c5-104">如果修改此语句，可能还必须对列映射做相关联的更改，而且此后必须手动维护编辑过的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="b60c5-104">If you modify this statement, you may also have to make associated changes to column mapping, and you will have to maintain the edited SQL statement manually thereafter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="b60c5-105">将基于连接数据源生成一个默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="b60c5-105">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="b60c5-106">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="b60c5-106">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="b60c5-107">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="b60c5-107">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="b60c5-108">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="b60c5-108">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="b60c5-109">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b60c5-109">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="b60c5-110">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="b60c5-110">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="b60c5-111">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="b60c5-111">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="b60c5-112">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="b60c5-112">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="b60c5-113">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="b60c5-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="b60c5-114">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="b60c5-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="b60c5-115">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="b60c5-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b60c5-116">选项</span><span class="sxs-lookup"><span data-stu-id="b60c5-116">Options</span></span>  
 <span data-ttu-id="b60c5-117">**SQL 语句**</span><span class="sxs-lookup"><span data-stu-id="b60c5-117">**SQL statement**</span></span>  
 <span data-ttu-id="b60c5-118">显示自动生成的 SQL 语句，允许对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="b60c5-118">Displays the auto-generated SQL statement and lets it be edited.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b60c5-119">如果要在 SQL 语句中包括回车符，请按 Ctrl+Enter。</span><span class="sxs-lookup"><span data-stu-id="b60c5-119">If you want to include a carriage return in the SQL statement, press CTRL+ENTER.</span></span> <span data-ttu-id="b60c5-120">如果只按 Enter，则对话框将关闭。</span><span class="sxs-lookup"><span data-stu-id="b60c5-120">If you press only ENTER, the dialog box closes.</span></span>  
  
 <span data-ttu-id="b60c5-121">**生成**</span><span class="sxs-lookup"><span data-stu-id="b60c5-121">**Autogenerate**</span></span>  
 <span data-ttu-id="b60c5-122">如果已修改了 SQL 语句，通过单击“自动生成”\*\*\*\* 可以还原默认的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="b60c5-122">Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.</span></span>  
  
  
