---
title: 添加或替换数据库镜像见证服务器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dd14ace23956ceef114f1f032b5d4db5febcec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579780"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a><span data-ttu-id="fd81c-102">添加或替换数据库镜像见证服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fd81c-102">Add or Replace a Database Mirroring Witness (SQL Server Management Studio)</span></span>
  <span data-ttu-id="fd81c-103">如果数据库镜像端点使用 Windows 身份验证，则可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 添加或替换见证服务器。</span><span class="sxs-lookup"><span data-stu-id="fd81c-103">If the database mirroring endpoints use Windows Authentication,, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add or replace a witness.</span></span> <span data-ttu-id="fd81c-104">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中添加见证服务器还会将运行模式更改为具有自动故障转移功能的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="fd81c-104">Adding a witness in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] also changes the operating mode to high-safety mode with automatic failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd81c-105">我们极力建议将见证服务器置于独立于每个伙伴的单独计算机中。</span><span class="sxs-lookup"><span data-stu-id="fd81c-105">We strongly recommend that the witness reside on a separate computer from either of the partners.</span></span> <span data-ttu-id="fd81c-106">见证服务器所用服务帐户必须位于主体服务器实例和镜像服务器实例所用服务帐户所在的域中，或者必须位于可信域中。</span><span class="sxs-lookup"><span data-stu-id="fd81c-106">The service account used by the witness must be in the same domain as the service accounts used by the principal and mirror server instances, or it must be in a trusted domain.</span></span>  
  
### <a name="to-add-or-replace-a-witness"></a><span data-ttu-id="fd81c-107">添加或替换见证服务器</span><span class="sxs-lookup"><span data-stu-id="fd81c-107">To Add or Replace a Witness</span></span>  
  
1.  <span data-ttu-id="fd81c-108">连接到主体服务器实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="fd81c-108">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="fd81c-109">展开 **“数据库”** ，然后选择要为其添加或替换见证服务器的会话的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="fd81c-109">Expand **Databases**, and select the principal database of the session to which you are adding or replacing a witness.</span></span>  
  
3.  <span data-ttu-id="fd81c-110">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-110">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="fd81c-111">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="fd81c-111">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="fd81c-112">单击 **“配置安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-112">Click **Configure Security**.</span></span>  
  
5.  <span data-ttu-id="fd81c-113">如果显示 **“配置数据库镜像安全向导”** 欢迎屏幕，则请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-113">If the **Configure Database Mirroring Security Wizard** welcome screen appears, click **Next**.</span></span>  
  
6.  <span data-ttu-id="fd81c-114">在 **“包括见证服务器”** 对话框中，单击 **“是”** ，再单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-114">In the **Include Witness Server** dialog box, click **Yes**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="fd81c-115">在 **“选择要配置的服务器”** 对话框中，将自动选中 **“见证服务器实例”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="fd81c-115">In the **Choose Servers to Configure** dialog box, the **Witness server instance** check box is automatically checked.</span></span> <span data-ttu-id="fd81c-116">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-116">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="fd81c-117">在 **“主体服务器实例”** 对话框中，保留现有的端口和端点。</span><span class="sxs-lookup"><span data-stu-id="fd81c-117">On the **Principal Server Instance** dialog box, keep the existing port and endpoint.</span></span> <span data-ttu-id="fd81c-118">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="fd81c-119">在 **“见证服务器实例”** 对话框中，单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-119">On the **Witness Server Instance** dialog box, click **Connect**.</span></span>  
  
10. <span data-ttu-id="fd81c-120">在“连接到服务器”对话框的“服务器名称”字段中，指定见证服务器实例，并使用 Windows 身份验证（默认设置）。</span><span class="sxs-lookup"><span data-stu-id="fd81c-120">In the **Connect to Server** dialog box, specify the witness server instance in the **Server name** field, and use Windows Authentication (the default).</span></span> <span data-ttu-id="fd81c-121">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-121">Click **Connect**.</span></span>  
  
11. <span data-ttu-id="fd81c-122">建立连接之后，便会在 **“见证服务器实例”** 对话框中显示见证服务器实例的侦听器端口和数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="fd81c-122">Once a connection is established, the listener port and database mirroring endpoint of the witness server instance are displayed on the **Witness Server Instance** dialog box.</span></span> <span data-ttu-id="fd81c-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-123">Click **Next**.</span></span>  
  
12. <span data-ttu-id="fd81c-124">**“服务帐户”** 对话框包含主体服务器实例、镜像服务器实例和见证服务器实例的域服务帐户字段。</span><span class="sxs-lookup"><span data-stu-id="fd81c-124">The **Service Accounts** dialog box contains fields for the domain service accounts of the principal, mirror, and witness server instances.</span></span>  
  
    -   <span data-ttu-id="fd81c-125">如果服务器实例全部使用相同的服务帐户，则请将这些字段保留为空白。</span><span class="sxs-lookup"><span data-stu-id="fd81c-125">If the server instances all use the same service account, leave the fields blank.</span></span>  
  
    -   <span data-ttu-id="fd81c-126">如果见证服务器实例所用的服务帐户不同于两个伙伴所用的服务帐户，则请使用以下帐户名填充 **“主体”** 、 **“镜像”** 和 **“见证服务器”** 字段：</span><span class="sxs-lookup"><span data-stu-id="fd81c-126">If the witness server instance uses a different service account from either of the partners, fill in the **Principal**, **Mirror**, and **Witness** fields with the account name:</span></span>  
  
         <span data-ttu-id="fd81c-127">*DOMAINNAME* **\\** *username*</span><span class="sxs-lookup"><span data-stu-id="fd81c-127">*DOMAINNAME* **\\** *username*</span></span>  
  
         <span data-ttu-id="fd81c-128">域名必须大写。</span><span class="sxs-lookup"><span data-stu-id="fd81c-128">The domain name must be in upper case.</span></span>  
  
     <span data-ttu-id="fd81c-129">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-129">Click **Next**.</span></span>  
  
13. <span data-ttu-id="fd81c-130">在 **“完成该向导”** 摘要屏幕中，检查见证服务器配置（可选），再单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="fd81c-130">On the **Complete the Wizard** summary screen, optionally, verify the witness configuration, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="fd81c-131">完成之后，该向导将返回到 **“数据库属性”** 对话框，此对话框的 **“见证服务器”** 字段中现在显示见证服务器的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="fd81c-131">On finishing, the wizard returns you to the **Database Properties** dialog box where the server network address of the witness now appears in **Witness** field.</span></span> <span data-ttu-id="fd81c-132">此外，还会自动选中“具有自动故障转移功能的高安全模式(同步)”，使用见证服务器时需要此选项。</span><span class="sxs-lookup"><span data-stu-id="fd81c-132">Also, **High-safety mode with automatic failover (synchronous)**, which is required with a witness, is automatically selected.</span></span>  
  
     <span data-ttu-id="fd81c-133">若要启用见证服务器并将会话更改为具有自动故障转移功能的高安全性模式，请单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="fd81c-133">To enable the witness and change the session to high-safety mode with automatic failover, Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd81c-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd81c-134">See Also</span></span>  
 <span data-ttu-id="fd81c-135">[数据库镜像见证服务器](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="fd81c-135">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="fd81c-136">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd81c-136">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="fd81c-137">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="fd81c-137">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="fd81c-138">[使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="fd81c-138">[Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span></span>  
 [<span data-ttu-id="fd81c-139">数据库镜像见证服务器</span><span class="sxs-lookup"><span data-stu-id="fd81c-139">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
