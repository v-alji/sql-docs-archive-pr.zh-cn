---
title: 查看 SQL Server 审核日志 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578767"
---
# <a name="view-a-sql-server-audit-log"></a><span data-ttu-id="26e8b-102">查看 SQL Server 审核日志</span><span class="sxs-lookup"><span data-stu-id="26e8b-102">View a SQL Server Audit Log</span></span>
  <span data-ttu-id="26e8b-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中查看 SQL Server 审核日志。</span><span class="sxs-lookup"><span data-stu-id="26e8b-103">This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="26e8b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="26e8b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="26e8b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="26e8b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="26e8b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="26e8b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="26e8b-107">**若要查看 SQL Server 审核日志，可使用：**</span><span class="sxs-lookup"><span data-stu-id="26e8b-107">**To view a SQL Server audit log, using:**</span></span>  
  
     [<span data-ttu-id="26e8b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26e8b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="26e8b-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="26e8b-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="26e8b-110">Security</span><span class="sxs-lookup"><span data-stu-id="26e8b-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="26e8b-111">权限</span><span class="sxs-lookup"><span data-stu-id="26e8b-111">Permissions</span></span>  
 <span data-ttu-id="26e8b-112">需要 `CONTROL SERVER` 权限。</span><span class="sxs-lookup"><span data-stu-id="26e8b-112">Requires the `CONTROL SERVER` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="26e8b-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26e8b-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-sql-server-audit-log"></a><span data-ttu-id="26e8b-114">查看 SQL Server 审核日志</span><span class="sxs-lookup"><span data-stu-id="26e8b-114">To view a SQL Server audit log</span></span>  
  
1.  <span data-ttu-id="26e8b-115"> 在对象资源管理器中，展开“安全性”文件夹。</span><span class="sxs-lookup"><span data-stu-id="26e8b-115">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="26e8b-116">展开“审核”文件夹。</span><span class="sxs-lookup"><span data-stu-id="26e8b-116">Expand the **Audits** folder.</span></span>  
  
3.  <span data-ttu-id="26e8b-117">右键单击要查看的审核日志，然后选择“查看审核日志”。</span><span class="sxs-lookup"><span data-stu-id="26e8b-117">Right-click the audit log that you want to view and select **View Audit Logs**.</span></span> <span data-ttu-id="26e8b-118">这将打开 "**日志文件查看器-**_server_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="26e8b-118">This opens the **Log File Viewer -**_server_name_ dialog box.</span></span> <span data-ttu-id="26e8b-119">有关详细信息，请参阅 [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="26e8b-119">For more information, see [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).</span></span>  
  
4.  <span data-ttu-id="26e8b-120">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="26e8b-120">When finished, click **Close**.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="26e8b-121">建议通过使用日志文件查看器查看审核日志。</span><span class="sxs-lookup"><span data-stu-id="26e8b-121">recommends viewing the audit log by using the Log File Viewer.</span></span> <span data-ttu-id="26e8b-122">但是，如果你要创建自动监视系统，则可以使用 [sys.fn_get_audit_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) 函数直接读取审核文件中的信息。</span><span class="sxs-lookup"><span data-stu-id="26e8b-122">However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) function.</span></span> <span data-ttu-id="26e8b-123">直接读取该文件将以略有不同的（未处理的）格式返回数据。</span><span class="sxs-lookup"><span data-stu-id="26e8b-123">Reading the file directly returns data in a slightly different (unprocessed) format.</span></span> <span data-ttu-id="26e8b-124">有关详细信息，请参阅**sys.databases fn_get_audit_file**</span><span class="sxs-lookup"><span data-stu-id="26e8b-124">See **sys.fn_get_audit_file** for more information</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e8b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26e8b-125">See Also</span></span>  
 <span data-ttu-id="26e8b-126">[SQL Server Audit（数据库引擎）](sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="26e8b-126">[SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="26e8b-127">将 SQL Server 审核事件写入安全日志</span><span class="sxs-lookup"><span data-stu-id="26e8b-127">Write SQL Server Audit Events to the Security Log</span></span>](write-sql-server-audit-events-to-the-security-log.md)  
  
  
