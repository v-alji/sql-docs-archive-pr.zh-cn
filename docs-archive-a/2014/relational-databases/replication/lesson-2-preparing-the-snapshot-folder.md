---
title: 第 2 课：准备快照文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d98c7433d0bd50504f20f7f576fcf0b20154c81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692849"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a><span data-ttu-id="4c939-102">第 2 课：准备快照文件夹</span><span class="sxs-lookup"><span data-stu-id="4c939-102">Lesson 2: Preparing the Snapshot Folder</span></span>
  <span data-ttu-id="4c939-103">在本课中，将学习如何配置用于创建和存储发布快照的快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="4c939-103">In this lesson, you will learn to configure the snapshot folder that is used to create and store the publication snapshot.</span></span>  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a><span data-ttu-id="4c939-104">为快照文件夹创建共享并分配权限</span><span class="sxs-lookup"><span data-stu-id="4c939-104">To create a share for the snapshot folder and assign permissions</span></span>  
  
1.  <span data-ttu-id="4c939-105">在 Windows 资源管理器中，定位到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据文件夹。</span><span class="sxs-lookup"><span data-stu-id="4c939-105">In Windows Explorer, navigate to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data folder.</span></span> <span data-ttu-id="4c939-106">默认位置为 C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data。</span><span class="sxs-lookup"><span data-stu-id="4c939-106">The default location is C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="4c939-107">创建名为 **repldata**的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="4c939-107">Create a new folder named **repldata**.</span></span>  
  
3.  <span data-ttu-id="4c939-108">右键单击此文件夹，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c939-108">Right-click this folder and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="4c939-109">在“repldata 属性”\*\*\*\* 对话框的“共享”\*\*\*\* 选项卡上，单击“共享”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c939-109">On the **Sharing** tab in the **repldata Properties** dialog box, click **Share**.</span></span>  
  
5.  <span data-ttu-id="4c939-110">在“文件共享”\*\*\*\* 对话框中，单击“共享”\*\*\*\*，再单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c939-110">In the **File Sharing** dialog box, click **Share**, and then click **Done**.</span></span>  
  
6.  <span data-ttu-id="4c939-111">在 **“安全性”** 选项卡上，单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="4c939-111">On the **Security** tab, click **Edit**.</span></span>  
  
7.  <span data-ttu-id="4c939-112">在“权限”\*\*\*\* 对话框中，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c939-112">In the **Permissions** dialog box, click **Add.**</span></span> <span data-ttu-id="4c939-113">在 "**选择用户、计算机、服务帐户或组**" 文本框中，键入在第1课中创建的快照代理帐户的名称，如 \<_Machine_Name> _**\ repl_snapshot**，其中 \<*Machine_Name> \* 是发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="4c939-113">In the **Select User, Computers, Service Account, or Groups** text box, type the name of the Snapshot Agent account created in Lesson 1, as \<_Machine_Name>_**\repl_snapshot**, where \<*Machine_Name>\* is the name of the Publisher.</span></span> <span data-ttu-id="4c939-114">单击“检查名称”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c939-114">Click **Check Names**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="4c939-115">重复前面的步骤，以将分发代理的权限添加为 \<_Machine_Name> _ **\ repl_distribution**，并将合并代理 \<_Machine_Name> _为**\ repl_merge**。</span><span class="sxs-lookup"><span data-stu-id="4c939-115">Repeat the previous step to add permissions for the Distribution Agent, as \<_Machine_Name>_**\repl_distribution**, and for the Merge Agent as \<_Machine_Name>_**\repl_merge**.</span></span>  
  
9. <span data-ttu-id="4c939-116">验证是否允许以下权限：</span><span class="sxs-lookup"><span data-stu-id="4c939-116">Verify the following permissions are allowed:</span></span>  
  
    -   <span data-ttu-id="4c939-117">repl_snapshot - 完全控制</span><span class="sxs-lookup"><span data-stu-id="4c939-117">repl_snapshot - Full Control</span></span>  
  
    -   <span data-ttu-id="4c939-118">repl_distribution - 读取</span><span class="sxs-lookup"><span data-stu-id="4c939-118">repl_distribution - Read</span></span>  
  
    -   <span data-ttu-id="4c939-119">repl_merge - 读取</span><span class="sxs-lookup"><span data-stu-id="4c939-119">repl_merge - Read</span></span>  
  
10. <span data-ttu-id="4c939-120">单击“确定”\*\*\*\* 关闭“repldata 属性”\*\*\*\* 对话框，并创建 repldata 共享。</span><span class="sxs-lookup"><span data-stu-id="4c939-120">Click **OK** to close the **repldata Properties** dialog box and create the repldata share.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4c939-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="4c939-121">Next Steps</span></span>  
 <span data-ttu-id="4c939-122">您已经成功为快照文件夹配置了共享。</span><span class="sxs-lookup"><span data-stu-id="4c939-122">You have successfully configured the share for the snapshot folder.</span></span> <span data-ttu-id="4c939-123">接下来，您将配置分发。</span><span class="sxs-lookup"><span data-stu-id="4c939-123">Next, you will configure distribution.</span></span> <span data-ttu-id="4c939-124">请参阅 [第 3 课：配置分发](lesson-3-configuring-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="4c939-124">See [Lesson 3: Configuring Distribution](lesson-3-configuring-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c939-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c939-125">See Also</span></span>  
 [<span data-ttu-id="4c939-126">保护快照文件夹</span><span class="sxs-lookup"><span data-stu-id="4c939-126">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
