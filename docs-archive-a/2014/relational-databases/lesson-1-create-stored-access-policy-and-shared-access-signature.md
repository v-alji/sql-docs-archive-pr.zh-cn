---
title: 第 2 课。 在容器上创建策略并生成共享访问签名 (SAS) 密钥 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab209f08d53b25a4791ef675e6fb6b78cab115f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692922"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a><span data-ttu-id="c1739-103">第 2 课。</span><span class="sxs-lookup"><span data-stu-id="c1739-103">Lesson 2.</span></span> <span data-ttu-id="c1739-104">在容器上创建策略并生成共享访问签名 (SAS) 密钥</span><span class="sxs-lookup"><span data-stu-id="c1739-104">Create a policy on container and generate a Shared Access Signature (SAS) key</span></span>
  <span data-ttu-id="c1739-105">在本课中，您将学习如何在 Blob 容器上创建策略以及生成 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="c1739-105">In this lesson, you will learn how to create a policy on the Blob container and also generate a SAS key.</span></span>  
  
 <span data-ttu-id="c1739-106">存储的访问策略在服务器端的共享访问签名之外又增加了一级控制。</span><span class="sxs-lookup"><span data-stu-id="c1739-106">A stored access policy provides an additional level of control over shared access signatures on the server side.</span></span> <span data-ttu-id="c1739-107">共享访问签名是一个 URI，它授予对容器、Blob、队列和表的受限访问权限。</span><span class="sxs-lookup"><span data-stu-id="c1739-107">A shared access signature is a URI that grants restricted access rights to containers, blobs, queues, and tables.</span></span> <span data-ttu-id="c1739-108">使用此项新增强时，需要在容器上创建具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="c1739-108">When using this new enhancement, you need to create a policy on a container with read, write, and list rights.</span></span>  
  
 <span data-ttu-id="c1739-109">可使用以下某种方法创建策略和共享访问签名：</span><span class="sxs-lookup"><span data-stu-id="c1739-109">You can create a policy and a shared access signature by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="c1739-110">Azure REST API 操作：[创建容器](https://msdn.microsoft.com/library/azure/dd179468.aspx)、[设置容器 Acl](https://msdn.microsoft.com/library/azure/dd179391.aspx)和[获取容器 acl](https://msdn.microsoft.com/library/azure/dd179469.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c1739-110">Azure REST API operations: [Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx), [Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx), and [Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx).</span></span>  
  
-   <span data-ttu-id="c1739-111">[CloudBlobContainer. Cloudblobcontainer.getsharedaccesssignature 方法](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature)。</span><span class="sxs-lookup"><span data-stu-id="c1739-111">[CloudBlobContainer.GetSharedAccessSignature Method](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) in the Azure SDK.</span></span>  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   <span data-ttu-id="c1739-112">第三方 Azure 资源管理器工具，如[Azure 存储资源管理器](https://azurestorageexplorer.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="c1739-112">A third-party Azure explorer tool, such as [Azure Storage Explorer](https://azurestorageexplorer.codeplex.com/).</span></span>  
  
 <span data-ttu-id="c1739-113">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="c1739-113">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="c1739-114">第 3 课：创建 SQL Server 凭据</span><span class="sxs-lookup"><span data-stu-id="c1739-114">Lesson 3: Create a SQL Server Credential</span></span>](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
