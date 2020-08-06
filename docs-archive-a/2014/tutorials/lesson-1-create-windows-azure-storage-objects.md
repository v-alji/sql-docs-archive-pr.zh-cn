---
title: 第1课：创建 Azure 存储对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d46c6d22ffd92dbf8035bff140960af8ef56122d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578590"
---
# <a name="lesson-1-create-azure-storage-objects"></a><span data-ttu-id="01629-102">第 1 课：创建 Azure 存储对象</span><span class="sxs-lookup"><span data-stu-id="01629-102">Lesson 1: Create Azure Storage Objects</span></span>
  <span data-ttu-id="01629-103">在云存储中创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份之前，必须先创建存储帐户，然后再创建 Blob 容器。</span><span class="sxs-lookup"><span data-stu-id="01629-103">Before you can create [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups on cloud storage, you must first create a storage account, and then a blob container.</span></span> <span data-ttu-id="01629-104">第1课将指导你完成登录 Azure 管理门户、创建存储帐户和 blob 容器的步骤。</span><span class="sxs-lookup"><span data-stu-id="01629-104">Lesson 1 walks you through the steps of Logging into the Azure Management Portal, creating a storage account and a blob container.</span></span>  
  
## <a name="create-a-storage-account"></a><span data-ttu-id="01629-105">创建存储帐户</span><span class="sxs-lookup"><span data-stu-id="01629-105">Create a storage Account</span></span>  
 <span data-ttu-id="01629-106">若要从 Azure 管理门户创建存储帐户，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="01629-106">To create a storage account from the Azure Management Portal, use the following steps:</span></span>  
  
1.  <span data-ttu-id="01629-107">使用你的帐户登录到 Azure 管理门户。</span><span class="sxs-lookup"><span data-stu-id="01629-107">Log in to the Azure Management Portal using your account.</span></span> <span data-ttu-id="01629-108">如果你没有 Azure 帐户，请[访问 azure 3 个月免费试用版](https://go.microsoft.com/fwlink/?LinkId=271927)。</span><span class="sxs-lookup"><span data-stu-id="01629-108">If you do not have an Azure account, [visit Azure 3-Month free trial](https://go.microsoft.com/fwlink/?LinkId=271927).</span></span>  
  
     <span data-ttu-id="01629-109">![Azure 登录屏幕](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure 登录屏幕")</span><span class="sxs-lookup"><span data-stu-id="01629-109">![Azure Login Screen](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure Login Screen")</span></span>  
  
2.  <span data-ttu-id="01629-110">使用[此处](https://go.microsoft.com/fwlink/?LinkId=271926)详细介绍的分步说明创建存储帐户。</span><span class="sxs-lookup"><span data-stu-id="01629-110">Use the step by step instructions detailed [here](https://go.microsoft.com/fwlink/?LinkId=271926), to create a storage account.</span></span>  
  
3.  <span data-ttu-id="01629-111">浏览到您在上一步中创建的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="01629-111">Browse to the storage account you created in previous step.</span></span> <span data-ttu-id="01629-112">单击网页底部的 "**管理密钥**"。</span><span class="sxs-lookup"><span data-stu-id="01629-112">From the bottom center of the web page, click **MANAGE KEYS**.</span></span> <span data-ttu-id="01629-113">此时将显示帐户信息。</span><span class="sxs-lookup"><span data-stu-id="01629-113">The account information is displayed.</span></span> <span data-ttu-id="01629-114">复制存储帐户名和访问键。</span><span class="sxs-lookup"><span data-stu-id="01629-114">Copy the storage account name, and the Access Keys.</span></span> <span data-ttu-id="01629-115">创建 SQL 存储凭据时需要此信息。</span><span class="sxs-lookup"><span data-stu-id="01629-115">This information is required to create SQL Stored Credentials.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="01629-116">使用此信息来访问存储帐户并创建备份。</span><span class="sxs-lookup"><span data-stu-id="01629-116">uses this information to access the storage account and create backups.</span></span>  
  
     <span data-ttu-id="01629-117">![Azure 存储帐户密钥的屏幕截图](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Azure 存储帐户密钥的屏幕截图")</span><span class="sxs-lookup"><span data-stu-id="01629-117">![Screen shot of Azure Storage Account Keys](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screen shot of Azure Storage Account Keys")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01629-118">还可以使用 REST API 以编程方式创建存储帐户。</span><span class="sxs-lookup"><span data-stu-id="01629-118">You can also create a storage account programmatically using REST APIs.</span></span> <span data-ttu-id="01629-119">有关详细信息，请参阅[创建存储帐户](https://go.microsoft.com/fwlink/?LinkId=271928)。</span><span class="sxs-lookup"><span data-stu-id="01629-119">For more information, see [Create Storage Account](https://go.microsoft.com/fwlink/?LinkId=271928).</span></span>  
  
### <a name="create-a-blob-container"></a><span data-ttu-id="01629-120">创建 Blob 容器</span><span class="sxs-lookup"><span data-stu-id="01629-120">Create a Blob Container</span></span>  
 <span data-ttu-id="01629-121">容器对 Blob 集进行分组。</span><span class="sxs-lookup"><span data-stu-id="01629-121">A container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="01629-122">所有 Blob 必须都在一个容器中。</span><span class="sxs-lookup"><span data-stu-id="01629-122">All blobs must be in a container.</span></span> <span data-ttu-id="01629-123">一个帐户可以包含无限数量的容器，但必须至少具有一个容器。</span><span class="sxs-lookup"><span data-stu-id="01629-123">An account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="01629-124">一个容器可以存储无限数量的 Blob。</span><span class="sxs-lookup"><span data-stu-id="01629-124">A container can store an unlimited number of blobs.</span></span>  
  
 <span data-ttu-id="01629-125">若要创建容器，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="01629-125">To create a Container, use the following steps:</span></span>  
  
1.  <span data-ttu-id="01629-126">选择存储帐户，单击 "**容器**" 选项卡，然后单击屏幕底部的 "**添加容器**"，这将打开一个新的对话框。</span><span class="sxs-lookup"><span data-stu-id="01629-126">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen which opens a new dialog box.</span></span>  
  
     <span data-ttu-id="01629-127">![在管理门户中创建容器](../../2014/tutorials/media/backuptocloud.gif "在管理门户中创建容器")</span><span class="sxs-lookup"><span data-stu-id="01629-127">![Creating a Container in the Management Portal](../../2014/tutorials/media/backuptocloud.gif "Creating a Container in the Management Portal")</span></span>  
  
2.  <span data-ttu-id="01629-128">输入容器的名称。</span><span class="sxs-lookup"><span data-stu-id="01629-128">Enter the name for the container.</span></span> <span data-ttu-id="01629-129">记下您指定的容器名称。</span><span class="sxs-lookup"><span data-stu-id="01629-129">Make a note of the container name you specified.</span></span> <span data-ttu-id="01629-130">此信息用在第 3 课和第 4 课的 T-SQL 语句的 URL（备份文件的路径）中。</span><span class="sxs-lookup"><span data-stu-id="01629-130">This information is used in the URL (path to backup file) in the T-SQL statements in lesson 3 and 4.</span></span>  
  
3.  <span data-ttu-id="01629-131">选择 "专用" 作为 "**访问类型**"。</span><span class="sxs-lookup"><span data-stu-id="01629-131">Select Private for **Access Type**.</span></span> <span data-ttu-id="01629-132">为了保护备份文件的安全，建议您创建专用容器。</span><span class="sxs-lookup"><span data-stu-id="01629-132">We recommend creating private containers for securing your backup files.</span></span>  
  
     <span data-ttu-id="01629-133">![正在创建新的 Blob 容器。](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "正在创建新的 Blob 容器。")</span><span class="sxs-lookup"><span data-stu-id="01629-133">![Creating a new blob container](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Creating a new blob container")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01629-134">即使您选择创建公共容器，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份和还原仍需要对存储帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="01629-134">Authentication to the storage account is required for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore even if you choose to create a public container.</span></span>  
    >   
    >  <span data-ttu-id="01629-135">还可以使用 REST API 以编程方式创建容器。</span><span class="sxs-lookup"><span data-stu-id="01629-135">You can also create a container programmatically using REST APIs.</span></span> <span data-ttu-id="01629-136">有关详细信息，请参阅[创建容器](https://go.microsoft.com/fwlink/?LinkId=271946)。</span><span class="sxs-lookup"><span data-stu-id="01629-136">For more information, see [Create Container](https://go.microsoft.com/fwlink/?LinkId=271946).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="01629-137">下一课</span><span class="sxs-lookup"><span data-stu-id="01629-137">Next Lesson</span></span>  
 <span data-ttu-id="01629-138">[第2课：创建 SQL Server 凭据](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="01629-138">[Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
  
