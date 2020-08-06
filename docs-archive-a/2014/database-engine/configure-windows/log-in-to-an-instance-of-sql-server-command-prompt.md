---
title: 登录到 SQL Server 实例（命令提示符）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 32028a30786117f2cafa76150867a0e726b07cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577832"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a><span data-ttu-id="2815d-102">登录到 SQL Server 实例（命令提示符）</span><span class="sxs-lookup"><span data-stu-id="2815d-102">Log In to an Instance of SQL Server (Command Prompt)</span></span>
  <span data-ttu-id="2815d-103">本主题介绍如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sqlcmd **实用工具测试与** 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="2815d-103">This topic describes how to test connectivity to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the **sqlcmd** utility.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a><span data-ttu-id="2815d-104">登录到 SQL Server 的默认实例</span><span class="sxs-lookup"><span data-stu-id="2815d-104">To log in to the default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="2815d-105">从命令提示符输入以下命令，使用 Windows 身份验证进行连接：</span><span class="sxs-lookup"><span data-stu-id="2815d-105">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a><span data-ttu-id="2815d-106">登录到 SQL Server 的命名实例</span><span class="sxs-lookup"><span data-stu-id="2815d-106">To log in to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="2815d-107">从命令提示符输入以下命令，使用 Windows 身份验证进行连接：</span><span class="sxs-lookup"><span data-stu-id="2815d-107">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2815d-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2815d-108">See Also</span></span>  
 <span data-ttu-id="2815d-109">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2815d-109">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="2815d-110">osql 实用工具</span><span class="sxs-lookup"><span data-stu-id="2815d-110">osql Utility</span></span>](../../tools/osql-utility.md)  
  
  
