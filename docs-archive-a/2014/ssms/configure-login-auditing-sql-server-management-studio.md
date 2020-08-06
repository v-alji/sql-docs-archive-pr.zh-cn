---
title: 配置登录审核 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7e05f6c254e098a67a5ce00435c009cd450af44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591048"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a><span data-ttu-id="45dea-102">配置登录审核 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="45dea-102">Configure Login Auditing (SQL Server Management Studio)</span></span>
  <span data-ttu-id="45dea-103">本主题介绍如何在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中配置登录审核以便监视登录 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]活动。</span><span class="sxs-lookup"><span data-stu-id="45dea-103">This topic describes how to configure login auditing in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] to monitor [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] login activity.</span></span> <span data-ttu-id="45dea-104">可以将登录审核配置为在发生以下事件时向错误日志中写入信息。</span><span class="sxs-lookup"><span data-stu-id="45dea-104">Login auditing can be configured to write to the error log on the following events.</span></span>  
  
-   <span data-ttu-id="45dea-105">登录失败</span><span class="sxs-lookup"><span data-stu-id="45dea-105">Failed logins</span></span>  
  
-   <span data-ttu-id="45dea-106">登录成功</span><span class="sxs-lookup"><span data-stu-id="45dea-106">Successful logins</span></span>  
  
-   <span data-ttu-id="45dea-107">成功和失败的登录</span><span class="sxs-lookup"><span data-stu-id="45dea-107">Both failed and successful logins</span></span>  
  
 <span data-ttu-id="45dea-108">必须先重新启动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，此选项才能生效。</span><span class="sxs-lookup"><span data-stu-id="45dea-108">You must restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before this option will take effect.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45dea-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45dea-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-login-auditing"></a><span data-ttu-id="45dea-110">配置登录审核</span><span class="sxs-lookup"><span data-stu-id="45dea-110">To configure login auditing</span></span>  
  
1.  <span data-ttu-id="45dea-111">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，使用对象资源管理器连接至 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="45dea-111">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="45dea-112">在对象资源管理器中，右键单击服务器名称，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="45dea-112">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="45dea-113">在“安全性”  页上的“登录名审核”  下，单击所需选项，然后关闭“服务器属性”  页。</span><span class="sxs-lookup"><span data-stu-id="45dea-113">On the **Security** page, under **Login** auditing, click the desired option and close the **Server Properties** page.</span></span>  
  
4.  <span data-ttu-id="45dea-114">在对象资源管理器中，右键单击服务器名称，然后单击“重启”  。</span><span class="sxs-lookup"><span data-stu-id="45dea-114">In Object Explorer, right-click the server name, and then click **Restart**.</span></span>  
  
  
