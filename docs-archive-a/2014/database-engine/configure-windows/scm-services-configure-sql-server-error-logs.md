---
title: 配置 SQL Server 错误日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591589"
---
# <a name="configure-sql-server-error-logs"></a><span data-ttu-id="93a19-102">配置 SQL Server 错误日志</span><span class="sxs-lookup"><span data-stu-id="93a19-102">Configure SQL Server Error Logs</span></span>
  <span data-ttu-id="93a19-103">本主题介绍如何查看或修改回收 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志的方式。</span><span class="sxs-lookup"><span data-stu-id="93a19-103">This topic describes how to view or modify the way [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs are recycled.</span></span>  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a><span data-ttu-id="93a19-104">打开“配置 SQL Server 错误日志”对话框</span><span class="sxs-lookup"><span data-stu-id="93a19-104">To open the Configure SQL Server Error Logs dialog box</span></span>  
  
1.  <span data-ttu-id="93a19-105">在对象资源管理器中，展开 SQL Server 的实例，展开“管理”，右键单击“SQL Server 日志”，再单击“配置”。</span><span class="sxs-lookup"><span data-stu-id="93a19-105">In Object Explorer, expand the instance of SQL Server, expand **Management**, right-click **SQL Server Logs**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="93a19-106">在 **“配置 SQL Server 错误日志”** 对话框中，从以下选项中进行选择。</span><span class="sxs-lookup"><span data-stu-id="93a19-106">In the **Configure SQL Server Error Logs** dialog box, choose from the following options.</span></span>  
  
     <span data-ttu-id="93a19-107">**限制错误日志文件在回收之前的数目**</span><span class="sxs-lookup"><span data-stu-id="93a19-107">**Limit the number of the error log files before they are recycled**</span></span>  
     <span data-ttu-id="93a19-108">若选中此选项，将限制在错误日志回收前可以创建的错误日志数。</span><span class="sxs-lookup"><span data-stu-id="93a19-108">Check to limit the number of error logs created before they are recycled.</span></span> <span data-ttu-id="93a19-109">每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时都将创建新的错误日志。</span><span class="sxs-lookup"><span data-stu-id="93a19-109">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="93a19-110">将保留前六个日志的备份，除非选中此选项并在下面指定一个不同的最大错误日志文件数。</span><span class="sxs-lookup"><span data-stu-id="93a19-110">retains backups of the previous six logs, unless you check this option, and specify a different maximum number of error log files below.</span></span>  
  
     <span data-ttu-id="93a19-111">**最大错误日志文件数**</span><span class="sxs-lookup"><span data-stu-id="93a19-111">**Maximum number of error log files**</span></span>  
     <span data-ttu-id="93a19-112">指定错误日志文件回收前创建的最大错误日志文件数。</span><span class="sxs-lookup"><span data-stu-id="93a19-112">Specify the maximum number of error log files created before they are recycled.</span></span> <span data-ttu-id="93a19-113">默认值为 6，即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在回收备份日志前保留的以前备份日志的数量。</span><span class="sxs-lookup"><span data-stu-id="93a19-113">The default is 6, which is the number of previous backup logs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains before recycling them.</span></span>  
  
  
