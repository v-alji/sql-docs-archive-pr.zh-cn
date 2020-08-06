---
title: Oracle 补充日志记录脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0aa55e71c17574eba9e25e098a3881b0eb4c9e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683000"
---
# <a name="oracle-supplemental-logging-script"></a><span data-ttu-id="22838-102">Oracle 补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="22838-102">Oracle Supplemental Logging Script</span></span>
  <span data-ttu-id="22838-103">此对话框显示 Oracle 补充日志记录脚本。</span><span class="sxs-lookup"><span data-stu-id="22838-103">This dialog box shows the script the Oracle supplemental logging script.</span></span>  
  
 <span data-ttu-id="22838-104">在您准备供使用的 CDC 实例时，CDC 设计器将创建一个 Oracle SQL 脚本，该脚本为要捕获的表设置补充日志记录。</span><span class="sxs-lookup"><span data-stu-id="22838-104">When you prepare a CDC Instance for use, the CDC Designer creates an Oracle SQL script that sets up supplemental logging for the tables to be captured.</span></span> <span data-ttu-id="22838-105">该补充日志记录脚本指示 Oracle 在更新特定表时，它写入事务日志的更改记录应包含所有有关列的数据，而不只是更改的列。</span><span class="sxs-lookup"><span data-stu-id="22838-105">The supplemental logging script tells Oracle that when a specific table is updated, the change records it writes to the transaction log should contain the data of all columns of interest, not just the columns that changed.</span></span>  
  
 <span data-ttu-id="22838-106">根据您的组织中的 Oracle DBA 策略，运行补充日志记录脚本可能要求 Oracle DBA 的审批。</span><span class="sxs-lookup"><span data-stu-id="22838-106">Depending on the Oracle DBA policies in your organization, running the supplemental logging script may require a review and approval by an Oracle DBA.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22838-107">选项</span><span class="sxs-lookup"><span data-stu-id="22838-107">Options</span></span>  
 <span data-ttu-id="22838-108">以下是可用于执行脚本的选项。</span><span class="sxs-lookup"><span data-stu-id="22838-108">The following are the available options for how to execute the script.</span></span>  
  
 <span data-ttu-id="22838-109">**运行脚本**</span><span class="sxs-lookup"><span data-stu-id="22838-109">**Run Script**</span></span>  
 <span data-ttu-id="22838-110">对为 CDC 实例定义的表运行补充日志记录脚本。</span><span class="sxs-lookup"><span data-stu-id="22838-110">Runs the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="22838-111">若要运行该脚本，Oracle 用户必须对要捕获的所有表具有 ALTER TABLE 权限，并且对 DBA_LOG_GROUPS 视图具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="22838-111">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span> <span data-ttu-id="22838-112">此外，Oracle 用户必须具有凭据以便通过所需权限使用 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="22838-112">In addition, the Oracle user must have the credentials for an Oracle database use with the required permissions.</span></span> <span data-ttu-id="22838-113">您可以让程序提示您 Oracle 凭据，然后使用它运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="22838-113">You can let the program prompt you for the Oracle credentials and then have it run the script.</span></span>  
  
 <span data-ttu-id="22838-114">**另存为**</span><span class="sxs-lookup"><span data-stu-id="22838-114">**Save As**</span></span>  
 <span data-ttu-id="22838-115">将脚本保存到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="22838-115">Saves the script to a text file.</span></span> <span data-ttu-id="22838-116">这在 Oracle 数据库管理员 (DBA) 需要检查和执行补充日志记录脚本时很有用，程序会让您将该脚本保存到一个文本文件，您在以后可以通过电子邮件或其他方式将该文件发送给 Oracle DBA 以便执行（通过使用 SQL\*Plus Oracle 实用工具或用于在 Oracle 数据库上运行脚本的其他工具）。</span><span class="sxs-lookup"><span data-stu-id="22838-116">This is used if an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script, the program lets you save the script to a text file that you can later send to the Oracle DBA by email or by other means to be execute later (by using the SQL\*Plus Oracle utility or other tool for running scripts on an Oracle database).</span></span>  
  
 <span data-ttu-id="22838-117">**Copy**</span><span class="sxs-lookup"><span data-stu-id="22838-117">**Copy**</span></span>  
 <span data-ttu-id="22838-118">将脚本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="22838-118">Copies the script to the clipboard.</span></span> <span data-ttu-id="22838-119">在就绪后，在 Oracle 数据库管理员 (DBA) 需要检查和执行补充日志记录脚本时，您可以将该脚本粘贴到您需要的任何位置。</span><span class="sxs-lookup"><span data-stu-id="22838-119">When ready you can paste the script in any location you need in case an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22838-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22838-120">See Also</span></span>  
 <span data-ttu-id="22838-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="22838-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="22838-122">管理 CDC 实例</span><span class="sxs-lookup"><span data-stu-id="22838-122">Manage a CDC Instance</span></span>](manage-a-cdc-instance.md)  
  
  
