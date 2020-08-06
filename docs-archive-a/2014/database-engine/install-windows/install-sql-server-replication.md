---
title: 安装 SQL Server 复制 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba941fda1d463e7bb4a26bd2fbb45d2a82ca27b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688163"
---
# <a name="install-sql-server-replication"></a><span data-ttu-id="bd891-102">安装 SQL Server 复制</span><span class="sxs-lookup"><span data-stu-id="bd891-102">Install SQL Server Replication</span></span>
  <span data-ttu-id="bd891-103">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导或通过命令提示符安装复制组件。</span><span class="sxs-lookup"><span data-stu-id="bd891-103">Replication components can be installed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or at a command prompt.</span></span> <span data-ttu-id="bd891-104">请在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或修改现有实例时安装复制组件。</span><span class="sxs-lookup"><span data-stu-id="bd891-104">Install replication when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or when you modify an existing instance.</span></span>  
  
 <span data-ttu-id="bd891-105">安装复制组件后，必须配置服务器才可以使用复制。</span><span class="sxs-lookup"><span data-stu-id="bd891-105">After replication components are installed, you must configure the server before you can use replication.</span></span> <span data-ttu-id="bd891-106">有关详细信息，请参阅 [联机丛书中的](../../relational-databases/replication/configure-distribution.md) 配置分发 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bd891-106">For more information, see [Configure Distribution](../../relational-databases/replication/configure-distribution.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd891-107">如果在修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的现有实例时安装复制组件，则在安装完成后必须停止并重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="bd891-107">If you install replication components when you modify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent after the installation is completed.</span></span> <span data-ttu-id="bd891-108">此操作可帮助确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理能够识别复制代理子系统，并且可以在作业步骤中调用复制代理。</span><span class="sxs-lookup"><span data-stu-id="bd891-108">This action helps ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent recognizes the replication agent subsystems and can call replication agents from job steps.</span></span>  
  
## <a name="installing-replication-by-using-setup"></a><span data-ttu-id="bd891-109">使用安装程序安装复制</span><span class="sxs-lookup"><span data-stu-id="bd891-109">Installing Replication by Using Setup</span></span>  
 <span data-ttu-id="bd891-110">**在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="bd891-110">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="bd891-111">若要安装包括复制管理对象 (RMO) 在内的复制组件，请在安装向导的“功能选择”页上选择“SQL Server 复制”。</span><span class="sxs-lookup"><span data-stu-id="bd891-111">To install replication components, including Replication Management Objects (RMO), select **SQL Server Replication** on the **Feature Selection** page of the Installation Wizard.</span></span>  
  
## <a name="installing-replication-from-the-command-prompt"></a><span data-ttu-id="bd891-112">从命令提示符安装复制</span><span class="sxs-lookup"><span data-stu-id="bd891-112">Installing Replication from the Command Prompt</span></span>  
 <span data-ttu-id="bd891-113">**在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="bd891-113">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="bd891-114">请参阅[从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="bd891-114">See [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd891-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd891-115">See Also</span></span>  
 <span data-ttu-id="bd891-116">[安装 SQL Server 2014](install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd891-116">[Install SQL Server 2014](install-sql-server.md) </span></span>  
 <span data-ttu-id="bd891-117">[从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="bd891-117">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="bd891-118">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="bd891-118">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
