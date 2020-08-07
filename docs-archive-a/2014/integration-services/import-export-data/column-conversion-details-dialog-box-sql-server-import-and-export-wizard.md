---
title: “列转换详细信息”对话框（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9207e76191060c56acad37db734827579a83aae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588643"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="59294-102">“列转换详细信息”对话框（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="59294-102">Column Conversion Details Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="59294-103">使用 "**列转换详细信息**" 对话框可以查看有关单个列的详细转换信息。</span><span class="sxs-lookup"><span data-stu-id="59294-103">Use the **Column Conversion Details** dialog box to review detailed conversion information about an individual column.</span></span> <span data-ttu-id="59294-104">此转换信息包含源和目标中的列的数据类型以及向导将执行的转换。</span><span class="sxs-lookup"><span data-stu-id="59294-104">This conversion information contains the column's data type at the source and the destination, and the conversion that the wizard will perform.</span></span> <span data-ttu-id="59294-105">此页还列出了向导用于确定所需的数据类型转换的数据类型映射文件。</span><span class="sxs-lookup"><span data-stu-id="59294-105">This page also lists the data type mapping files that the wizard uses to determine the data type conversions that are required.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="59294-106">在安装过程中会安装这些数据类型映射文件。</span><span class="sxs-lookup"><span data-stu-id="59294-106">installs these data type mapping files during setup.</span></span>  
  
 <span data-ttu-id="59294-107">**打开“列转换详细信息”对话框**</span><span class="sxs-lookup"><span data-stu-id="59294-107">**To open the Column Conversion Details dialog box**</span></span>  
  
1.  <span data-ttu-id="59294-108">在导入和导出向导的 "**查看数据类型问题**" 页上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 "**表**" 列表中，选择一个表。</span><span class="sxs-lookup"><span data-stu-id="59294-108">On the **Review Data Type Issues** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, in the **Table** list, select a table.</span></span>  
  
2.  <span data-ttu-id="59294-109">在 "**数据类型映射**" 列表中，双击包含要查看其转换详细信息的列的行。</span><span class="sxs-lookup"><span data-stu-id="59294-109">In the **Data type mapping** list, double-click the row that contains the column for which you want to view conversion details.</span></span>  
  
 <span data-ttu-id="59294-110">若要了解有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="59294-110">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="59294-111">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="59294-111">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="59294-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="59294-112">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="59294-113">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="59294-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="59294-114">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="59294-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="59294-115">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="59294-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  
