---
title: 第1课：创建 Azure 存储帐户和容器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 07167c513d2c6ed3ae0f7b431461ee3915047636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577960"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a><span data-ttu-id="1af07-102">第 1 课：创建 Azure 存储帐户和容器</span><span class="sxs-lookup"><span data-stu-id="1af07-102">Lesson 1: Create Azure Storage Account and Container</span></span>
  <span data-ttu-id="1af07-103">必须先创建 Azure 存储帐户和 blob 容器以及共享访问签名，然后才能开始将 SQL Server 数据文件存储在 Azure 存储中。</span><span class="sxs-lookup"><span data-stu-id="1af07-103">Before you can start storing SQL Server data files in Azure Storage, you must first create an Azure Storage account and a blob container, and a shared access signature.</span></span> <span data-ttu-id="1af07-104">第1课逐步讲解登录到 Azure 管理门户、创建存储帐户、blob 容器和共享访问签名的步骤。</span><span class="sxs-lookup"><span data-stu-id="1af07-104">Lesson 1 walks you through the steps of logging into the Azure Management Portal, creating a storage account, a blob container, and a shared access signature.</span></span>  
  
 <span data-ttu-id="1af07-105">默认情况下，只有存储帐户的所有者可访问该帐户内的 Blob、表和队列。</span><span class="sxs-lookup"><span data-stu-id="1af07-105">By default, only the owner of the storage account may access blobs, tables, and queues within that account.</span></span> <span data-ttu-id="1af07-106">若要能够使用此项新的 SQL Server 增强在不共享存储帐户访问密钥的情况下访问这些资源，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1af07-106">To be able to access these resources using this new SQL Server enhancement without sharing the storage account access key, you are required to do these:</span></span>  
  
-   <span data-ttu-id="1af07-107">将容器的权限设置为私有。</span><span class="sxs-lookup"><span data-stu-id="1af07-107">Set the container's permissions to private.</span></span>  
  
-   <span data-ttu-id="1af07-108">创建共享访问签名。</span><span class="sxs-lookup"><span data-stu-id="1af07-108">Create a shared access signature.</span></span> <span data-ttu-id="1af07-109">通过它，可委派对容器、Blob、表或队列资源的受限访问权限，方法为指定间隔，期间这些资源可用，以及客户端将对这些资源拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="1af07-109">It enables you to delegate restricted access to a container, blob, table, or queue resource by specifying the interval for which the resources are available and the permissions that a client will have to it.</span></span>  
  
-   <span data-ttu-id="1af07-110">使用存储的访问策略管理容器或其 Blob 的共享访问签名。</span><span class="sxs-lookup"><span data-stu-id="1af07-110">Use a stored access policy to manage shared access signatures for a container or its blobs.</span></span> <span data-ttu-id="1af07-111">存储的访问策略提供针对共享访问签名的另外一种控制措施，还提供一种撤消这些措施的简单方法。</span><span class="sxs-lookup"><span data-stu-id="1af07-111">The stored access policy gives you an additional measure of control over your shared access signatures and also provides a straightforward means to revoke them.</span></span>  
  
 <span data-ttu-id="1af07-112">有关详细信息，请参阅[管理对 Azure 存储资源的访问](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1af07-112">For more information, see [Manage Access to Azure Storage Resources](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span></span>  
  
## <a name="create-storage-account"></a><span data-ttu-id="1af07-113">创建存储帐户</span><span class="sxs-lookup"><span data-stu-id="1af07-113">Create Storage Account</span></span>  
 <span data-ttu-id="1af07-114">若要在 Azure 管理门户上创建存储帐户，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1af07-114">To create a storage account on the Azure Management Portal, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1af07-115">使用帐户登录到 [Azure 管理门户](https://manage.windowsazure.com) 。</span><span class="sxs-lookup"><span data-stu-id="1af07-115">Log in to the [Azure Management Portal](https://manage.windowsazure.com) using your account.</span></span> <span data-ttu-id="1af07-116">如果没有 Azure 帐户，请访问 [Azure 免费试用版](https://www.windowsazure.com/pricing/free-trial/)。</span><span class="sxs-lookup"><span data-stu-id="1af07-116">If you do not have an Azure account, visit [Azure free trial](https://www.windowsazure.com/pricing/free-trial/).</span></span>  
  
     <span data-ttu-id="1af07-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="1af07-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span></span>  
  
2.  <span data-ttu-id="1af07-118">使用分步说明[创建存储帐户](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="1af07-118">Use the step by step instructions to [create a storage account](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span> <span data-ttu-id="1af07-119">请注意，在创建要用于 Azure 中的 SQL Server 数据文件的存储帐户时，应取消选择或禁用异地复制。</span><span class="sxs-lookup"><span data-stu-id="1af07-119">Note that when creating a storage account to be used for the SQL Server Data Files in Azure feature, you should unselect or disable the geo-replication.</span></span> <span data-ttu-id="1af07-120">这是因为对于参与地理复制的多个 Blob 无法保证写入顺序。</span><span class="sxs-lookup"><span data-stu-id="1af07-120">This is because write order is not guaranteed for multiple blobs participating in geo-replication.</span></span> <span data-ttu-id="1af07-121">如果存储帐户经过地理复制，并且需要恢复，则发生损坏。</span><span class="sxs-lookup"><span data-stu-id="1af07-121">If a storage account is geo-replicated and recovery is required, a corruption occurs.</span></span>  
  
     <span data-ttu-id="1af07-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="1af07-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span></span>  
  
## <a name="create-a-blob-container"></a><span data-ttu-id="1af07-123">创建 Blob 容器</span><span class="sxs-lookup"><span data-stu-id="1af07-123">Create a Blob container</span></span>  
 <span data-ttu-id="1af07-124">在 Azure 中，容器提供一组 blob 的分组。</span><span class="sxs-lookup"><span data-stu-id="1af07-124">In Azure, a container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="1af07-125">所有 Blob 必须都在一个容器中。</span><span class="sxs-lookup"><span data-stu-id="1af07-125">All blobs must be in a container.</span></span> <span data-ttu-id="1af07-126">一个存储帐户可含有无限数量的容器，但必须至少有一个容器。</span><span class="sxs-lookup"><span data-stu-id="1af07-126">A storage account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="1af07-127">一个容器可以存储无限数量的 Blob。</span><span class="sxs-lookup"><span data-stu-id="1af07-127">A container can store an unlimited number of blobs.</span></span> <span data-ttu-id="1af07-128">有关存储大小限制的最新信息，请参阅[如何在 .net 中使用 Azure Blob 存储服务](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)。</span><span class="sxs-lookup"><span data-stu-id="1af07-128">For most up-to-date information on storage size limits, see [How to use the Azure Blob Storage Service in .NET](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span></span>  
  
 <span data-ttu-id="1af07-129">若要在 Azure 中创建容器，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1af07-129">To create a container in Azure, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1af07-130">登录到 [Azure 管理门户](https://manage.windowsazure.com)。</span><span class="sxs-lookup"><span data-stu-id="1af07-130">Log in to the [Azure Management Portal](https://manage.windowsazure.com).</span></span>  
  
2.  <span data-ttu-id="1af07-131">选择存储帐户，单击 "**容器**" 选项卡，然后单击屏幕底部的 "**添加容器**"，这将打开一个新的对话框。</span><span class="sxs-lookup"><span data-stu-id="1af07-131">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen, which opens a new dialog box.</span></span>  
  
3.  <span data-ttu-id="1af07-132">输入容器的名称。</span><span class="sxs-lookup"><span data-stu-id="1af07-132">Enter a name for the container.</span></span>  
  
4.  <span data-ttu-id="1af07-133">选择 "**专用**" 作为 "**访问类型**"。</span><span class="sxs-lookup"><span data-stu-id="1af07-133">Select **Private** for **Access Type**.</span></span> <span data-ttu-id="1af07-134">当你将访问权限设置为 "专用" 时，Azure 帐户所有者只能读取容器和 blob 数据。</span><span class="sxs-lookup"><span data-stu-id="1af07-134">When you set the access to private, the container and blob data can be read by the Azure account owner only.</span></span>  
  
     <span data-ttu-id="1af07-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="1af07-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1af07-136">若要以编程方式创建容器，还可使用 REST API。</span><span class="sxs-lookup"><span data-stu-id="1af07-136">To create a container programmatically, you can also use REST APIs.</span></span> <span data-ttu-id="1af07-137">有关详细信息，请参阅[创建容器](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx)和[Azure 存储服务 REST API 引用](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1af07-137">For more information, see [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) and also [Azure Storage Services REST API Reference](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span></span>  
  
 <span data-ttu-id="1af07-138">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="1af07-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="1af07-139">第2课。在容器上创建策略并生成共享访问签名 &#40;SAS&#41; 密钥</span><span class="sxs-lookup"><span data-stu-id="1af07-139">Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key</span></span>](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
