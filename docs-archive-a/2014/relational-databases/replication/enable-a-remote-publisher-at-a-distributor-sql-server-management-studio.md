---
title: 在分发服务器上启用远程发布服务器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06c85924731b79e8b3c79cfbcc354b5bedf69b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578100"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a><span data-ttu-id="45f65-102">在分发服务器上启用远程发布服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="45f65-102">Enable a Remote Publisher at a Distributor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="45f65-103">可以在 **“发布服务器”** 页上允许发布服务器使用远程分发服务器。</span><span class="sxs-lookup"><span data-stu-id="45f65-103">Enable a Publisher to use a remote Distributor on the **Publishers** page.</span></span> <span data-ttu-id="45f65-104">可在配置分发向导和“分发服务器属性 - \<Distributor>”对话框中使用此页面。</span><span class="sxs-lookup"><span data-stu-id="45f65-104">This page is available in the Configure Distribution Wizard and the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="45f65-105">有关使用该向导和访问该对话框的详细信息，请参阅[配置发布和分发](configure-publishing-and-distribution.md)和[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="45f65-105">For more information about using the wizard and accessing the dialog box, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a><span data-ttu-id="45f65-106">在配置分发向导中启用发布服务器</span><span class="sxs-lookup"><span data-stu-id="45f65-106">To enable a Publisher in the Configure Distribution Wizard</span></span>  
  
1.  <span data-ttu-id="45f65-107">在“配置分发向导”的 **“发布服务器”** 页上单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="45f65-107">On the **Publishers** page of the Configure Distribution Wizard, click **Add**.</span></span>  
  
2.  <span data-ttu-id="45f65-108">单击 **“添加 SQL Server 发布服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="45f65-108">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="45f65-109">有关启用 Oracle 发布服务器以使用分发服务器的信息，请参阅 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="45f65-109">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="45f65-110">在 **“连接到服务器”** 对话框中，指定要使用远程分发服务器的发布服务器的连接信息，再单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="45f65-110">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="45f65-111">在 **“分发服务器密码”** 页的 **“密码”** 和 **“确认密码”** 文本框中，为 **distributor_admin** 帐户指定强密码，复制将使用该密码从发布服务器连接到分发服务器以执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="45f65-111">On the **Distributor Password** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="45f65-112">若要查看并修改发布服务器的设置，请单击属性按钮 (...)。</span><span class="sxs-lookup"><span data-stu-id="45f65-112">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a><span data-ttu-id="45f65-113">在“分发服务器属性”对话框中启用发布服务器</span><span class="sxs-lookup"><span data-stu-id="45f65-113">To enable a Publisher in the Distributor Properties dialog box</span></span>  
  
1.  <span data-ttu-id="45f65-114">在“分发服务器属性 - \<Distributor>”对话框的“发布服务器”页面上，单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="45f65-114">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="45f65-115">单击 **“添加 SQL Server 发布服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="45f65-115">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="45f65-116">有关启用 Oracle 发布服务器以使用分发服务器的信息，请参阅 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="45f65-116">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="45f65-117">在 **“连接到服务器”** 对话框中，指定要使用远程分发服务器的发布服务器的连接信息，再单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="45f65-117">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="45f65-118">在 **“分发服务器”** 页的 **“密码”** 和 **“确认密码”** 文本框中，为 **distributor_admin** 帐户指定强密码，复制将使用该密码从发布服务器连接到分发服务器以执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="45f65-118">On the **Publishers** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="45f65-119">若要查看并修改发布服务器的设置，请单击属性按钮 (...)。</span><span class="sxs-lookup"><span data-stu-id="45f65-119">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45f65-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45f65-120">See Also</span></span>  
 <span data-ttu-id="45f65-121">[配置发布和分发](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="45f65-121">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="45f65-122">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="45f65-122">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="45f65-123">保护分发服务器</span><span class="sxs-lookup"><span data-stu-id="45f65-123">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
