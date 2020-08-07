---
title: SQL Server 导入和导出向导 (转换类型（不进行转换检查）) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3874bcad23994fdcf69ade948239760d5c871917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588636"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a><span data-ttu-id="e8b8e-102">转换类型时不进行转换检查（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="e8b8e-102">Convert Types without Conversion Checking (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="e8b8e-103">如果向导找不到一个或多个数据类型转换和映射文件，则使用 "**转换类型而不进行转换检查**" 页可以查看向导执行的映射 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-103">Use the **Convert Types without Conversion Checking** page to review the mappings that the wizard performs when the wizard cannot locate one or more of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type conversion and mapping files.</span></span> <span data-ttu-id="e8b8e-104">此页包含的信息可帮助您识别缺少的文件。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-104">This page includes information that helps you identify the missing file or files.</span></span>  
  
 <span data-ttu-id="e8b8e-105">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="e8b8e-106">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="e8b8e-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="e8b8e-108">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="e8b8e-109">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="e8b8e-110">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e8b8e-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  
