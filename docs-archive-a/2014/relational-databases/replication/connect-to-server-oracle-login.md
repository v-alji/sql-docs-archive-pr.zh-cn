---
title: 连接到服务器 (Oracle)，登录名 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577566"
---
# <a name="connect-to-server-oracle-login"></a><span data-ttu-id="69453-102">连接到服务器 (Oracle)，登录名</span><span class="sxs-lookup"><span data-stu-id="69453-102">Connect to Server (Oracle), Login</span></span>
  <span data-ttu-id="69453-103">使用“连接到服务器”对话框的“登录名”选项卡，指定   分发服务器与 Oracle 发布服务器建立连接时使用的帐户  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="69453-103">Use the **Login** tab of the **Connect to Server** dialog box to specify the account under which connections are made from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher.</span></span> <span data-ttu-id="69453-104">所使用的帐户必须是配置发布服务器期间为复制管理用户架构指定的同一帐户。</span><span class="sxs-lookup"><span data-stu-id="69453-104">You must use the same account as the one specified for the replication administrative user schema during configuration of the Publisher.</span></span> <span data-ttu-id="69453-105">有关详细信息，请参阅[配置 Oracle 发布服务器](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="69453-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="69453-106">选项</span><span class="sxs-lookup"><span data-stu-id="69453-106">Options</span></span>  
 <span data-ttu-id="69453-107">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="69453-107">**Server instance**</span></span>  
 <span data-ttu-id="69453-108">Oracle 发布服务器的透明网络底层 (TNS)，是在配置分发服务器上安装的 Oracle 客户端软件期间指定的。</span><span class="sxs-lookup"><span data-stu-id="69453-108">The Transparent Network Substrate (TNS) name of the Oracle Publisher, which is specified during configuration of the Oracle client software installed on the Distributor.</span></span>  
  
 <span data-ttu-id="69453-109">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="69453-109">**Authentication**</span></span>  
 <span data-ttu-id="69453-110">选择 **“Oracle 标准身份验证”** （建议）或 **“Windows 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="69453-110">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span> <span data-ttu-id="69453-111">如果选择了 **“Windows 身份验证”** ，则：</span><span class="sxs-lookup"><span data-stu-id="69453-111">If you select **Windows Authentication**:</span></span>  
  
-   <span data-ttu-id="69453-112">必须将 Oracle 服务器配置为允许使用 Windows 凭据进行连接。</span><span class="sxs-lookup"><span data-stu-id="69453-112">The Oracle server must be configured to allow connections using Windows credentials.</span></span> <span data-ttu-id="69453-113">有关详细信息，请参阅 Oracle 文档。</span><span class="sxs-lookup"><span data-stu-id="69453-113">For more information, see the Oracle documentation.</span></span>  
  
-   <span data-ttu-id="69453-114">当前的登录帐户必须与为复制管理用户架构指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户相同。</span><span class="sxs-lookup"><span data-stu-id="69453-114">You must be currently logged in with the same [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
 <span data-ttu-id="69453-115">**“登录名”** 和 **“密码”**</span><span class="sxs-lookup"><span data-stu-id="69453-115">**Login** and **Password**</span></span>  
 <span data-ttu-id="69453-116">如果在 **“身份验证”** 选项中选择了 **“Oracle 标准身份验证”** ，请指定要使用的登录名和密码，且必须与为复制管理用户架构指定的登录名和密码相同。</span><span class="sxs-lookup"><span data-stu-id="69453-116">If you selected **Oracle Standard Authentication** for the **Authentication** option, specify the login and password to use, which must be the same as those specified for the replication administrative user schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69453-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69453-117">See Also</span></span>  
 [<span data-ttu-id="69453-118">Oracle 发布的术语词汇表</span><span class="sxs-lookup"><span data-stu-id="69453-118">Glossary of Terms for Oracle Publishing</span></span>](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
