---
title: Database Mail XPs 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33ee15e862e0992f39373ec30275040c4fcacc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588018"
---
# <a name="database-mail-xps-server-configuration-option"></a><span data-ttu-id="60c0c-102">Database Mail XPs 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="60c0c-102">Database Mail XPs Server Configuration Option</span></span>
  <span data-ttu-id="60c0c-103">使用 **DatabaseMail XPs** 选项可以在此服务器上启用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="60c0c-103">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="60c0c-104">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="60c0c-104">The possible values are:</span></span>  
  
-   <span data-ttu-id="60c0c-105">**0** 表示数据库邮件不可用（默认值）。</span><span class="sxs-lookup"><span data-stu-id="60c0c-105">**0** indicating Database Mail is not available (default).</span></span>  
  
-   <span data-ttu-id="60c0c-106">**1** 表示数据库邮件可用。</span><span class="sxs-lookup"><span data-stu-id="60c0c-106">**1** indicating Database Mail is available.</span></span>  
  
 <span data-ttu-id="60c0c-107">该设置立即生效，无需停止并重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="60c0c-107">The setting takes effect immediately without a server stop and restart.</span></span>  
  
 <span data-ttu-id="60c0c-108">启用数据库邮件后，必须配置一个数据库邮件主机数据库，才能使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="60c0c-108">After enabling Database Mail, you must configure a Database Mail host database to use Database Mail.</span></span>  
  
 <span data-ttu-id="60c0c-109">使用 **数据库邮件配置向导** 配置数据库邮件可以启用 **msdb** 数据库中的数据库邮件扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="60c0c-109">Configuring Database Mail using the **Database Mail Configuration Wizard** enables the Database Mail extended stored procedures in the **msdb** database.</span></span> <span data-ttu-id="60c0c-110">如果你使用的是 **数据库邮件配置向导**，则不需要使用下面的 **sp_configure** 示例。</span><span class="sxs-lookup"><span data-stu-id="60c0c-110">If you use the **Database Mail Configuration Wizard**, you do not have to use the **sp_configure** example below.</span></span>  
  
 <span data-ttu-id="60c0c-111">将 **Database Mail XPs** 选项设置为 0 可以防止启动数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="60c0c-111">Setting the **Database Mail XPs** option to 0 prevents Database Mail from starting.</span></span> <span data-ttu-id="60c0c-112">如果该选项设置为 0 时数据库邮件正在运行，则其将继续运行并发送邮件，直到数据库邮件空闲时间达到 **DatabaseMailExeMinimumLifeTime** 选项中配置的时间。</span><span class="sxs-lookup"><span data-stu-id="60c0c-112">If it is running when the option is set to 0, it continues to run and send mail until it is idle for the time configured in the **DatabaseMailExeMinimumLifeTime** option.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="60c0c-113">示例</span><span class="sxs-lookup"><span data-stu-id="60c0c-113">Examples</span></span>  
 <span data-ttu-id="60c0c-114">以下示例启用了 Database Mail 扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="60c0c-114">The following example enables the Database Mail extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="60c0c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60c0c-115">See Also</span></span>  
 [<span data-ttu-id="60c0c-116">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="60c0c-116">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
