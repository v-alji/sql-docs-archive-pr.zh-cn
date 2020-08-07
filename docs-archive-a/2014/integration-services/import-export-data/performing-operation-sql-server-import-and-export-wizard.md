---
title: 执行操作（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6cdac605da2288149909a3fb6e9f245e10eebf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588633"
---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a><span data-ttu-id="09708-102">正在执行操作（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="09708-102">Performing Operation (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="09708-103">使用 "**执行操作**" 页可以查看导入/导出操作的进度和结果，并在必要时中断操作。</span><span class="sxs-lookup"><span data-stu-id="09708-103">Use the **Performing Operation** page to view the progress and the results of the import/export operation, and to interrupt the operation if necessary.</span></span>  
  
 <span data-ttu-id="09708-104">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="09708-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="09708-105">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="09708-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="09708-106">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="09708-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="09708-107">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="09708-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="09708-108">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="09708-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="09708-109">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="09708-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="09708-110">选项</span><span class="sxs-lookup"><span data-stu-id="09708-110">Options</span></span>  
 <span data-ttu-id="09708-111">**Action**</span><span class="sxs-lookup"><span data-stu-id="09708-111">**Action**</span></span>  
 <span data-ttu-id="09708-112">显示整个操作过程中的每一步操作。</span><span class="sxs-lookup"><span data-stu-id="09708-112">Displays each action that is part of the operation.</span></span>  
  
 <span data-ttu-id="09708-113">**Status**</span><span class="sxs-lookup"><span data-stu-id="09708-113">**Status**</span></span>  
 <span data-ttu-id="09708-114">显示操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="09708-114">Displays the success or failure of each action.</span></span>  
  
 <span data-ttu-id="09708-115">**Message**</span><span class="sxs-lookup"><span data-stu-id="09708-115">**Message**</span></span>  
 <span data-ttu-id="09708-116">显示操作可能生成的信息性消息和错误消息。</span><span class="sxs-lookup"><span data-stu-id="09708-116">Displays informational and error messages that the action might generate.</span></span>  
  
 <span data-ttu-id="09708-117">**Filter**</span><span class="sxs-lookup"><span data-stu-id="09708-117">**Filter**</span></span>  
 <span data-ttu-id="09708-118">选择是否只希望显示错误、警告或成功的操作。</span><span class="sxs-lookup"><span data-stu-id="09708-118">Choose whether you want to display only errors, warnings, or successful actions.</span></span> <span data-ttu-id="09708-119">可以通过选择 "**显示所有操作**" 来恢复为默认显示。</span><span class="sxs-lookup"><span data-stu-id="09708-119">You can revert to the default display by choosing **Show All Actions**.</span></span>  
  
 <span data-ttu-id="09708-120">**Stop**</span><span class="sxs-lookup"><span data-stu-id="09708-120">**Stop**</span></span>  
 <span data-ttu-id="09708-121">如果需要，使用 "**停止**" 按钮中断操作。</span><span class="sxs-lookup"><span data-stu-id="09708-121">Interrupt the operation, if necessary, by using the **Stop** button.</span></span>  
  
 <span data-ttu-id="09708-122">**Report**</span><span class="sxs-lookup"><span data-stu-id="09708-122">**Report**</span></span>  
 <span data-ttu-id="09708-123">查看结果报表，将报表保存到文件，将报表复制到剪贴板或通过电子邮件发送报表。</span><span class="sxs-lookup"><span data-stu-id="09708-123">View a report of the results, save the report to a file, copy the report to the clipboard, or send the report by e-mail.</span></span>  
  
  
