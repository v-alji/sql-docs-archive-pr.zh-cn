---
title: 在两个服务器上创建相同的对称密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 38eaccffff89b0be7e59f628fcfb9b6e772a02b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693697"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a><span data-ttu-id="92f9c-102">在两个服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="92f9c-102">Create Identical Symmetric Keys on Two Servers</span></span>
  <span data-ttu-id="92f9c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的两台不同的服务器上创建相同的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-103">This topic describes how to create identical symmetric keys on two different servers in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="92f9c-104">为了对密码进行解密，需要用于加密密码的密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-104">In order to decrypt ciphertext, you need the key that was used to encrypt it.</span></span> <span data-ttu-id="92f9c-105">在一个数据库中同时执行加密和解密时，密钥保存在数据库中并可同时用于（取决于权限）加密和解密。</span><span class="sxs-lookup"><span data-stu-id="92f9c-105">When both encryption and decryption occur in a single database, the key is stored in the database and it is available, depending on permissions, for both encryption and decryption.</span></span> <span data-ttu-id="92f9c-106">但在不同的数据库或服务器中执行加密和解密时，保存在一个数据库中的密钥不能用于另一数据库。</span><span class="sxs-lookup"><span data-stu-id="92f9c-106">But when encryption and decryption occur in separate databases or on separate servers, the key stored in one database is not available for use on the second database</span></span>  
  
 <span data-ttu-id="92f9c-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="92f9c-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="92f9c-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="92f9c-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="92f9c-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="92f9c-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="92f9c-110">安全性</span><span class="sxs-lookup"><span data-stu-id="92f9c-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="92f9c-111">使用 Transact-SQL 在两台不同的服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="92f9c-111">To create identical symmetric keys on two different servers, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="92f9c-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="92f9c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="92f9c-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="92f9c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="92f9c-114">创建对称密钥时，必须至少使用以下项之一来对该对称密钥进行加密：证书、密码、对称密钥、非对称密钥或 PROVIDER。</span><span class="sxs-lookup"><span data-stu-id="92f9c-114">When a symmetric key is created, the symmetric key must be encrypted by using at least one of the following: certificate, password, symmetric key, asymmetric key, or PROVIDER.</span></span> <span data-ttu-id="92f9c-115">可使用上述每种类型中的多项对密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="92f9c-115">The key can have more than one encryption of each type.</span></span> <span data-ttu-id="92f9c-116">换言之，可以同时使用多个证书、密码、对称密钥以及非对称密钥对单个对称密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="92f9c-116">In other words, a single symmetric key can be encrypted by using multiple certificates, passwords, symmetric keys, and asymmetric keys at the same time.</span></span>  
  
-   <span data-ttu-id="92f9c-117">当使用密码（而不是数据库主密钥的公钥）对对称密钥进行加密时，便会使用 TRIPLE DES 加密算法。</span><span class="sxs-lookup"><span data-stu-id="92f9c-117">When a symmetric key is encrypted with a password instead of the public key of the database master key, the TRIPLE DES encryption algorithm is used.</span></span> <span data-ttu-id="92f9c-118">因此，用强加密算法（如 AES）创建的密钥本身受较弱算法的保护。</span><span class="sxs-lookup"><span data-stu-id="92f9c-118">Because of this, keys that are created with a strong encryption algorithm, such as AES, are themselves secured by a weaker algorithm.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="92f9c-119">Security</span><span class="sxs-lookup"><span data-stu-id="92f9c-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="92f9c-120">权限</span><span class="sxs-lookup"><span data-stu-id="92f9c-120">Permissions</span></span>  
 <span data-ttu-id="92f9c-121">要求对数据库具有 ALTER ANY SYMMETRIC KEY 权限。</span><span class="sxs-lookup"><span data-stu-id="92f9c-121">Requires ALTER ANY SYMMETRIC KEY permission on the database.</span></span> <span data-ttu-id="92f9c-122">如果指定了 AUTHORIZATION，则要求对数据库用户具有 IMPERSONATE 权限，或者对应用程序角色具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="92f9c-122">If AUTHORIZATION is specified, requires IMPERSONATE permission on the database user or ALTER permission on the application role.</span></span> <span data-ttu-id="92f9c-123">如果使用证书或非对称密钥进行加密，则要求对证书或非对称密钥具有 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="92f9c-123">If encryption is by certificate or asymmetric key, requires VIEW DEFINITION permission on the certificate or asymmetric key.</span></span> <span data-ttu-id="92f9c-124">只有 Windows 登录名、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名和应用程序角色才能拥有对称密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-124">Only Windows logins, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins, and application roles can own symmetric keys.</span></span> <span data-ttu-id="92f9c-125">其他组和角色不能拥有对称密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-125">Groups and roles cannot own symmetric keys.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="92f9c-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92f9c-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a><span data-ttu-id="92f9c-127">在两台不同的服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="92f9c-127">To create identical symmetric keys on two different servers</span></span>  
  
1.  <span data-ttu-id="92f9c-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="92f9c-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="92f9c-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="92f9c-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="92f9c-130">通过运行以下 CREATE MASTER KEY、CREATE CERTIFICATE 和 CREATE SYMMETRIC KEY 语句来创建密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-130">Create a key by running the following CREATE MASTER KEY, CREATE CERTIFICATE, and CREATE SYMMETRIC KEY statements.</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4.  <span data-ttu-id="92f9c-131">连接到一个独立的服务器实例，打开不同的查询窗口，然后运行上述 SQL 语句来在另一台服务器上创建相同的密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-131">Connect to a separate server instance, open a different Query Window, and run the SQL statements above to create the same key on the second server.</span></span>  
  
5.  <span data-ttu-id="92f9c-132">先在第一台服务器上运行以下 OPEN SYMMETRIC KEY 语句和 SELECT 语句，以测试密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-132">Test the keys by first running the OPEN SYMMETRIC KEY statement and the SELECT statement below on the first server.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6.  <span data-ttu-id="92f9c-133">在另一服务器上，将上一个 SELECT 语句的结果作为 `@blob` 的值粘贴到以下代码中，并运行以下代码以验证复制的密钥可对密码进行解密。</span><span class="sxs-lookup"><span data-stu-id="92f9c-133">On the second server, paste the result of the previous SELECT statement into the following code as the value of `@blob` and run the following code to verify that the duplicate key can decrypt the ciphertext.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7.  <span data-ttu-id="92f9c-134">在两个服务器上关闭对称密钥。</span><span class="sxs-lookup"><span data-stu-id="92f9c-134">Close the symmetric key on both servers.</span></span>  
  
    ```  
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 <span data-ttu-id="92f9c-135">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="92f9c-135">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="92f9c-136">CREATE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92f9c-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="92f9c-137">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92f9c-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="92f9c-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92f9c-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="92f9c-139">ENCRYPTBYKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92f9c-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [<span data-ttu-id="92f9c-140">DECRYPTBYKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92f9c-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)  
  
-   [<span data-ttu-id="92f9c-141">OPEN SYMMETRIC KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92f9c-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
