---
title: 创建同义词 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dc18c9d0d6048c4190ba56725dd332f2dfb629e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576596"
---
# <a name="create-synonyms"></a><span data-ttu-id="4bc6d-102">创建同义词</span><span class="sxs-lookup"><span data-stu-id="4bc6d-102">Create Synonyms</span></span>
  <span data-ttu-id="4bc6d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建同义词。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-103">This topic describes how to create a synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4bc6d-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4bc6d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4bc6d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="4bc6d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4bc6d-107">**若要创建同义词，可使用：**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-107">**To create a synonym, using:**</span></span>  
  
     [<span data-ttu-id="4bc6d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4bc6d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4bc6d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4bc6d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4bc6d-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="4bc6d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4bc6d-111">Security</span><span class="sxs-lookup"><span data-stu-id="4bc6d-111">Security</span></span>  
 <span data-ttu-id="4bc6d-112">若要在给定架构中创建同义词，则用户必须具有 CREATE SYNONYM 权限，并拥有架构或具有 ALTER SCHEMA 权限。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-112">To create a synonym in a given schema, a user must have CREATE SYNONYM permission and either own the schema or have ALTER SCHEMA permission.</span></span> <span data-ttu-id="4bc6d-113">CREATE SYNONYM 权限是可授予的权限。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-113">The CREATE SYNONYM permission is a grantable permission.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4bc6d-114">权限</span><span class="sxs-lookup"><span data-stu-id="4bc6d-114">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4bc6d-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4bc6d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="4bc6d-116">创建同义词</span><span class="sxs-lookup"><span data-stu-id="4bc6d-116">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="4bc6d-117">在 **“对象资源管理器”** 中，展开要创建新视图的数据库。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-117">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="4bc6d-118">右键单击“同义词”文件夹，然后单击“新建同义词...”   。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-118">Right-click the **Synonyms** folder, then click **New Synonym...**.</span></span>  
  
3.  <span data-ttu-id="4bc6d-119">在 **“添加同义词”** 对话框中，输入以下信息。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-119">In the **Add Synonym** dialog box, enter the following information.</span></span>  
  
     <span data-ttu-id="4bc6d-120">**同义词名称**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-120">**Synonym name**</span></span>  
     <span data-ttu-id="4bc6d-121">键入将用于此对象的新名称。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-121">Type the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="4bc6d-122">**同义词架构**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-122">**Synonym schema**</span></span>  
     <span data-ttu-id="4bc6d-123">键入将用于此对象的新名称的架构。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-123">Type the schema of the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="4bc6d-124">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-124">**Server name**</span></span>  
     <span data-ttu-id="4bc6d-125">键入要连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-125">Type the server instance to connect to.</span></span>  
  
     <span data-ttu-id="4bc6d-126">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-126">**Database name**</span></span>  
     <span data-ttu-id="4bc6d-127">键入或选择包含该对象的数据库。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-127">Type or select the database containing the object.</span></span>  
  
     <span data-ttu-id="4bc6d-128">**架构**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-128">**Schema**</span></span>  
     <span data-ttu-id="4bc6d-129">键入或选择该对象所属的架构。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-129">Type or select the schema that owns the object.</span></span>  
  
     <span data-ttu-id="4bc6d-130">**对象类型**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-130">**Object type**</span></span>  
     <span data-ttu-id="4bc6d-131">选择对象的类型。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-131">Select the type of object.</span></span>  
  
     <span data-ttu-id="4bc6d-132">**对象名称**</span><span class="sxs-lookup"><span data-stu-id="4bc6d-132">**Object name**</span></span>  
     <span data-ttu-id="4bc6d-133">键入同义词所引用的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-133">Type the name of the object to which the synonym refers.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4bc6d-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4bc6d-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="4bc6d-135">创建同义词</span><span class="sxs-lookup"><span data-stu-id="4bc6d-135">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="4bc6d-136">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4bc6d-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4bc6d-138">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-138">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4bc6d-139">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4bc6d-139">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4bc6d-140">下面的示例为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的现有表创建一个同义词。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-140">The following example creates a synonym for an existing table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="4bc6d-141">后续示例中将使用该同义词。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-141">The synonym is then used in subsequent examples.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 <span data-ttu-id="4bc6d-142">以下示例将行插入到由 `MyAddressType` 同义词引用的基表。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-142">The following example inserts a row into the base table that is referenced by the `MyAddressType` synonym.</span></span>  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 <span data-ttu-id="4bc6d-143">以下示例说明了如何在动态 SQL 中引用同义词。</span><span class="sxs-lookup"><span data-stu-id="4bc6d-143">The following example demonstrates how a synonym can be referenced in dynamic SQL.</span></span>  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
