---
title: 创建数据库主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
ms.reviewer: carlrab
ms.openlocfilehash: cb8305d9d5a3c72e6dffafd231f21110a5abdd14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693696"
---
# <a name="create-a-database-master-key"></a><span data-ttu-id="11f31-102">创建数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="11f31-102">Create a Database Master Key</span></span>

<span data-ttu-id="11f31-103">本主题说明如何 `master` 使用在中的数据库中创建数据库主密钥 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="11f31-103">This topic describes how to create a database master key in the `master` database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>

<span data-ttu-id="11f31-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="11f31-104">**In This Topic**</span></span>

- <span data-ttu-id="11f31-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="11f31-105">**Before you begin:**</span></span>

  [<span data-ttu-id="11f31-106">安全性</span><span class="sxs-lookup"><span data-stu-id="11f31-106">Security</span></span>](#Security)

- [<span data-ttu-id="11f31-107">使用 Transact-SQL 创建数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="11f31-107">To create a database master key using Transact-SQL</span></span>](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="11f31-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="11f31-108">Before You Begin</span></span>

### <a name="security"></a><a name="Security"></a> <span data-ttu-id="11f31-109">Security</span><span class="sxs-lookup"><span data-stu-id="11f31-109">Security</span></span>

#### <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="11f31-110">权限</span><span class="sxs-lookup"><span data-stu-id="11f31-110">Permissions</span></span>

<span data-ttu-id="11f31-111">要求对数据库具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="11f31-111">Requires CONTROL permission on the database.</span></span>

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="11f31-112">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="11f31-112">Using Transact-SQL</span></span>

### <a name="to-create-a-database-master-key"></a><span data-ttu-id="11f31-113">创建数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="11f31-113">To create a database master key</span></span>

1. <span data-ttu-id="11f31-114">选择密码来对存储于该数据库中的主密钥副本进行加密。</span><span class="sxs-lookup"><span data-stu-id="11f31-114">Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span>
2. <span data-ttu-id="11f31-115">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="11f31-115">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>
3. <span data-ttu-id="11f31-116">展开“系统数据库”，右键单击 `master`，然后单击“新建查询” 。</span><span class="sxs-lookup"><span data-stu-id="11f31-116">Expand **System Databases**, right-click `master` and then click **New Query**.</span></span>
4. <span data-ttu-id="11f31-117">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="11f31-117">Copy and paste the following example into the query window and click **Execute**.</span></span>

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

<span data-ttu-id="11f31-118">有关详细信息，请参阅 [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="11f31-118">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>
