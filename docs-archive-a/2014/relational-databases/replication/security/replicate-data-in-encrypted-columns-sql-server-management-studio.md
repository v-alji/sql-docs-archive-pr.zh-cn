---
title: 复制加密列中的数据 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689857"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a><span data-ttu-id="224d4-102">复制加密列中的数据 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="224d4-102">Replicate Data in Encrypted Columns (SQL Server Management Studio)</span></span>
  <span data-ttu-id="224d4-103">通过使用复制，您可以发布加密的列数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-103">Replication enables you to publish encrypted column data.</span></span> <span data-ttu-id="224d4-104">若要在订阅服务器上解密并使用此数据，则订阅服务器上也必须有用于在发布服务器上加密该数据的密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-104">To decrypt and use this data at the Subscriber, the key that was used to encrypt the data at the Publisher must also be present on the Subscriber.</span></span> <span data-ttu-id="224d4-105">复制并不提供安全机制来传输加密密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-105">Replication does not provide a secure mechanism to transport encryption keys.</span></span> <span data-ttu-id="224d4-106">您必须在订阅服务器上手动重新创建加密密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-106">You must manually re-create the encryption key at the Subscriber.</span></span> <span data-ttu-id="224d4-107">本主题说明如何在发布服务器上加密列并确保订阅服务器上提供有加密密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-107">This topic shows you how to encrypt a column at the Publisher and make sure that the encryption key is available at the Subscriber.</span></span>  
  
 <span data-ttu-id="224d4-108">基本步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="224d4-108">The basic steps are as follows:</span></span>  
  
1.  <span data-ttu-id="224d4-109">在发布服务器上创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-109">Create the symmetric key at the Publisher.</span></span>  
  
2.  <span data-ttu-id="224d4-110">使用对称密钥加密列数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-110">Encrypt column data with the symmetric key.</span></span>  
  
3.  <span data-ttu-id="224d4-111">发布包含加密列的表。</span><span class="sxs-lookup"><span data-stu-id="224d4-111">Publish the table with the encrypted column.</span></span>  
  
4.  <span data-ttu-id="224d4-112">订阅发布。</span><span class="sxs-lookup"><span data-stu-id="224d4-112">Subscribe to the publication.</span></span>  
  
5.  <span data-ttu-id="224d4-113">初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="224d4-113">Initialize the subscription.</span></span>  
  
6.  <span data-ttu-id="224d4-114">使用与步骤 1 中相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值在订阅服务器上重新创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-114">Recreate the symmetric key at the Subscriber using same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span>  
  
7.  <span data-ttu-id="224d4-115">访问加密列数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-115">Access the encrypted column data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="224d4-116">您应当使用对称密钥来加密列数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-116">You should use a symmetric key to encrypt column data.</span></span> <span data-ttu-id="224d4-117">可以在发布服务器和订阅服务器上采取不同方式为对称密钥本身进行保护。</span><span class="sxs-lookup"><span data-stu-id="224d4-117">The symmetric key itself can be secured by different means at the Publisher and Subscriber.</span></span>  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a><span data-ttu-id="224d4-118">创建和复制加密列数据</span><span class="sxs-lookup"><span data-stu-id="224d4-118">To create and replicate encrypted column data</span></span>  
  
1.  <span data-ttu-id="224d4-119">在发布服务器上，执行 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="224d4-119">At the Publisher, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="224d4-120">KEY_SOURCE 值是很重要的数据，可用来重新创建对称密钥和解密数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-120">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="224d4-121">必须始终安全地存储和传输 KEY_SOURCE。</span><span class="sxs-lookup"><span data-stu-id="224d4-121">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
2.  <span data-ttu-id="224d4-122">执行 [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 以打开新密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-122">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
3.  <span data-ttu-id="224d4-123">使用 [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) 函数在发布服务器上加密列数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-123">Use the [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) function to encrypt column data at the Publisher.</span></span>  
  
4.  <span data-ttu-id="224d4-124">执行 [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 以关闭密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-124">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
5.  <span data-ttu-id="224d4-125">发布包含加密列的表。</span><span class="sxs-lookup"><span data-stu-id="224d4-125">Publish the table that contains the encrypted column.</span></span> <span data-ttu-id="224d4-126">有关详细信息，请参阅 [Create a Publication](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="224d4-126">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="224d4-127">订阅发布。</span><span class="sxs-lookup"><span data-stu-id="224d4-127">Subscribe to the publication.</span></span> <span data-ttu-id="224d4-128">有关详细信息，请参阅[创建请求订阅](../create-a-pull-subscription.md)或[创建推送订阅](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="224d4-128">For more information, see [Create a Pull Subscription](../create-a-pull-subscription.md) or [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
7.  <span data-ttu-id="224d4-129">初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="224d4-129">Initialize the subscription.</span></span> <span data-ttu-id="224d4-130">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="224d4-130">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
8.  <span data-ttu-id="224d4-131">在订阅服务器上，使用与步骤 1 中相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值执行 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="224d4-131">At the Subscriber, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span> <span data-ttu-id="224d4-132">您可以为 ENCRYPTION BY 指定不同的值。</span><span class="sxs-lookup"><span data-stu-id="224d4-132">You can specify a different value for ENCRYPTION BY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="224d4-133">KEY_SOURCE 值是很重要的数据，可用来重新创建对称密钥和解密数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-133">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="224d4-134">必须始终安全地存储和传输 KEY_SOURCE。</span><span class="sxs-lookup"><span data-stu-id="224d4-134">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
9. <span data-ttu-id="224d4-135">执行 [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 以打开新密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-135">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
10. <span data-ttu-id="224d4-136">使用 [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) 函数在订阅服务器上解密复制的数据。</span><span class="sxs-lookup"><span data-stu-id="224d4-136">Use the [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) function to decrypt replicated data at the Subscriber.</span></span>  
  
11. <span data-ttu-id="224d4-137">执行 [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 以关闭密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-137">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="224d4-138">示例</span><span class="sxs-lookup"><span data-stu-id="224d4-138">Example</span></span>  
 <span data-ttu-id="224d4-139">此示例将创建一个对称密钥、一个用来帮助保护对称密钥的证书和一个主密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-139">This example creates a symmetric key, a certificate that is used to help secure the symmetric key, and a master key.</span></span> <span data-ttu-id="224d4-140">这些密钥在发布数据库中创建，</span><span class="sxs-lookup"><span data-stu-id="224d4-140">These keys are created in the publication database.</span></span> <span data-ttu-id="224d4-141">然后可用于在 `SalesOrderHeader` 表中创建加密列 (EncryptedCreditCardApprovalCode)。</span><span class="sxs-lookup"><span data-stu-id="224d4-141">They are then used to create an encrypted column (EncryptedCreditCardApprovalCode) in the `SalesOrderHeader` table.</span></span> <span data-ttu-id="224d4-142">将在 AdvWorksSalesOrdersMerge 发布中发布此列而不是未加密的 CreditCardApprovalCode 列。</span><span class="sxs-lookup"><span data-stu-id="224d4-142">This column is published in the AdvWorksSalesOrdersMerge publication instead of the unencrypted CreditCardApprovalCode column.</span></span> <span data-ttu-id="224d4-143">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="224d4-143">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="224d4-144">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="224d4-144">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a><span data-ttu-id="224d4-145">示例</span><span class="sxs-lookup"><span data-stu-id="224d4-145">Example</span></span>  
 <span data-ttu-id="224d4-146">此示例使用与第一个示例相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值在订阅数据库中重新创建相同的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="224d4-146">This example recreates the same symmetric key in the subscription database using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE from the first example.</span></span> <span data-ttu-id="224d4-147">此示例假设您已初始化 AdvWorksSalesOrdersMerge 发布的订阅以复制加密列。</span><span class="sxs-lookup"><span data-stu-id="224d4-147">This example assumes that you have already initialized a subscription to the AdvWorksSalesOrdersMerge publication to replicate the encrypted column.</span></span> <span data-ttu-id="224d4-148">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="224d4-148">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="224d4-149">如果必须将凭据存储在脚本文件中，则必须在存储和传输过程中保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="224d4-149">If you must store credentials in a script file, you must secure the file during storage and transport to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a><span data-ttu-id="224d4-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="224d4-150">See Also</span></span>  
 <span data-ttu-id="224d4-151">[SQL Server 复制安全性](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="224d4-151">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="224d4-152">在两个服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="224d4-152">Create Identical Symmetric Keys on Two Servers</span></span>](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
