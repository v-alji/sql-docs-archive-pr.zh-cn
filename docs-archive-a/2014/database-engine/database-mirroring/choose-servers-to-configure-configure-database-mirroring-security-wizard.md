---
title: 选择要配置的服务器（配置数据库镜像安全向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18e36f5c8ec020b3859dc847d1bbfc019817bcd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579775"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a><span data-ttu-id="4f514-102">选择要配置的服务器（配置数据库镜像安全向导）</span><span class="sxs-lookup"><span data-stu-id="4f514-102">Choose Servers to Configure (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="4f514-103">使用此页可以指定当前要配置的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="4f514-103">Use this page to specify which server instances you want to configure now.</span></span> <span data-ttu-id="4f514-104">必须至少选择一个服务器实例，才能继续本向导。</span><span class="sxs-lookup"><span data-stu-id="4f514-104">You must select at least one server instance before continuing the wizard.</span></span>  
  
 <span data-ttu-id="4f514-105">如果清除了某个服务器实例的复选框，向导将不会对该实例做任何更改。</span><span class="sxs-lookup"><span data-stu-id="4f514-105">If you clear the check box for a server instance, the wizard will not make any changes to it.</span></span> <span data-ttu-id="4f514-106">但是，向导会要求您输入该实例的有关信息，并将此信息保存在其他服务器实例的配置中。</span><span class="sxs-lookup"><span data-stu-id="4f514-106">The wizard, however, will ask you to enter information about that instance and save this information as part of the configuration of the other server instances.</span></span> <span data-ttu-id="4f514-107">例如，如果清除了见证服务器实例的复选框，向导会要求您输入见证服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户，因为必须创建该帐户的登录名，作为安全配置的一部分保存在主体和镜像服务器实例中。</span><span class="sxs-lookup"><span data-stu-id="4f514-107">For example, if you clear the check box for the witness server instance, the wizard will ask you to enter the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the witness because a login for that account must be created as part of the security configuration saved at the principal and mirror server instances.</span></span>  
  
 <span data-ttu-id="4f514-108">**使用 SQL Server Management Studio 配置数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="4f514-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="4f514-109">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4f514-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="4f514-110">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4f514-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="4f514-111">选项</span><span class="sxs-lookup"><span data-stu-id="4f514-111">Options</span></span>  
 <span data-ttu-id="4f514-112">**主体服务器实例**</span><span class="sxs-lookup"><span data-stu-id="4f514-112">**Principal server instance**</span></span>  
 <span data-ttu-id="4f514-113">选择该选项可以配置主体服务器的安全性。</span><span class="sxs-lookup"><span data-stu-id="4f514-113">Select to configure security for the principal server.</span></span>  
  
 <span data-ttu-id="4f514-114">**镜像服务器实例**</span><span class="sxs-lookup"><span data-stu-id="4f514-114">**Mirror server instance**</span></span>  
 <span data-ttu-id="4f514-115">选择该选项可以配置镜像服务器的安全性。</span><span class="sxs-lookup"><span data-stu-id="4f514-115">Select to configure security for the mirror server.</span></span>  
  
 <span data-ttu-id="4f514-116">**见证服务器实例**</span><span class="sxs-lookup"><span data-stu-id="4f514-116">**Witness server instance**</span></span>  
 <span data-ttu-id="4f514-117">选择该选项可以配置见证服务器（如果存在）的安全性。</span><span class="sxs-lookup"><span data-stu-id="4f514-117">Select to configure security for the witness server (if present).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f514-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f514-118">See Also</span></span>  
 <span data-ttu-id="4f514-119">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="4f514-119">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="4f514-120">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4f514-120">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
