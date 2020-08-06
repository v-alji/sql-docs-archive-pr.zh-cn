---
title: Oracle 发布服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db52b93b3d260ff58a151e7238bbbe065bc47bc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577544"
---
# <a name="oracle-publisher"></a><span data-ttu-id="b62ce-102">Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="b62ce-102">Oracle Publisher</span></span>
  <span data-ttu-id="b62ce-103">从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许使用快照和事务复制从 Oracle 数据库发布数据。</span><span class="sxs-lookup"><span data-stu-id="b62ce-103">Beginning with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to publish data from an Oracle database using snapshot and transactional replication.</span></span> <span data-ttu-id="b62ce-104">有关详细信息，请参阅 [Oracle 发布概述](non-sql/oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b62ce-104">For more information, see [Oracle Publishing Overview](non-sql/oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="b62ce-105">Oracle 发布服务器必须使用远程 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器；必须在安装和测试必需的 Oracle 网络软件之后在该服务器上运行此向导。</span><span class="sxs-lookup"><span data-stu-id="b62ce-105">The Oracle Publisher must use a remote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor; this wizard must be run on that server after the necessary Oracle networking software has been installed and tested.</span></span> <span data-ttu-id="b62ce-106">有关详细信息，请参阅[配置 Oracle 发布服务器](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="b62ce-106">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b62ce-107">如果其他管理员将 Oracle 数据库配置为发布服务器，那么在单击 **“下一步”** 后，将提示您输入用于连接到 Oracle 数据库的复制登录密码。</span><span class="sxs-lookup"><span data-stu-id="b62ce-107">If another administrator configured the Oracle database as a Publisher, after clicking **Next** you will be prompted to enter the password for the replication login used to connect to the Oracle database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b62ce-108">随后会在您的登录名和 Oracle 数据库的链接服务器连接之间创建映射。</span><span class="sxs-lookup"><span data-stu-id="b62ce-108">will then create a mapping between your login and the linked server connection to the Oracle database.</span></span> <span data-ttu-id="b62ce-109">以后连接到 Oracle 数据库时无需输入密码。</span><span class="sxs-lookup"><span data-stu-id="b62ce-109">You will not be required to enter a password for subsequent connections to the Oracle database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b62ce-110">选项</span><span class="sxs-lookup"><span data-stu-id="b62ce-110">Options</span></span>  
 <span data-ttu-id="b62ce-111">**Oracle 发布服务器**</span><span class="sxs-lookup"><span data-stu-id="b62ce-111">**Oracle Publishers**</span></span>  
 <span data-ttu-id="b62ce-112">从列表中选择 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b62ce-112">Select an Oracle Publisher from the list.</span></span> <span data-ttu-id="b62ce-113">此列表包含一些特定的 Oracle 发布服务器，这些服务器以前已被配置为使用运行向导的服务器作为其分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b62ce-113">This list contains Oracle Publishers that have previously been configured to use the server against which the wizard is running as their Distributor.</span></span> <span data-ttu-id="b62ce-114">如果列表为空，或您希望使用的 Oracle 发布服务器不在列表中，那么请单击 **“添加 Oracle 发布服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="b62ce-114">If the list is empty, or the Oracle Publisher you want to use is not in the list, click **Add Oracle Publisher**.</span></span>  
  
 <span data-ttu-id="b62ce-115">**“添加 Oracle 发布服务器”**</span><span class="sxs-lookup"><span data-stu-id="b62ce-115">**Add Oracle Publisher**</span></span>  
 <span data-ttu-id="b62ce-116">单击此项可启动 **“分发服务器属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b62ce-116">Click to launch the **Distributor Properties** dialog box.</span></span> <span data-ttu-id="b62ce-117">在此对话框中，单击 **“添加”** ，再单击 **“添加 Oracle 发布服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="b62ce-117">In this dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span> <span data-ttu-id="b62ce-118">在 **“连接到服务器”** 对话框中，指定 Oracle 服务器名称，以及复制管理用户架构的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="b62ce-118">In the **Connect to Server** dialog box, specify the Oracle server name, and the login and password for the replication administrative user schema.</span></span> <span data-ttu-id="b62ce-119">有关详细信息，请参阅[连接到服务器 (Oracle) - 登录名](connect-to-server-oracle-login.md)。</span><span class="sxs-lookup"><span data-stu-id="b62ce-119">For more information, see [Connect to Server &#40;Oracle&#41;, Login](connect-to-server-oracle-login.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b62ce-120">如果运行向导的服务器尚未被配置为分发服务器，那么将会提示您立即进行配置。</span><span class="sxs-lookup"><span data-stu-id="b62ce-120">If the server against which the wizard is running has not yet been configured as a Distributor, you are prompted to configure it now.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62ce-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b62ce-121">See Also</span></span>  
 [<span data-ttu-id="b62ce-122">从 Oracle 数据库创建发布</span><span class="sxs-lookup"><span data-stu-id="b62ce-122">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   

  
  
