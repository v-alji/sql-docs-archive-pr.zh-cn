---
title: HumanResources.myTeam 示例表 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589081"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a><span data-ttu-id="4b6bf-102">HumanResources.myTeam 示例表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b6bf-102">HumanResources.myTeam Sample Table (SQL Server)</span></span>
  <span data-ttu-id="4b6bf-103">[导入和导出大容量数据](bulk-import-and-export-of-data-sql-server.md) 中的许多代码示例都需要一个名为 **myTeam**的具有特殊用途的测试表。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-103">Many of the code examples in [Importing and Exporting Bulk Data](bulk-import-and-export-of-data-sql-server.md) require a special-purpose test table named **myTeam**.</span></span> <span data-ttu-id="4b6bf-104">您必须在 **数据库的** HumanResources **架构中创建** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 表，才能运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-104">Before you can run the examples, you must create the **myTeam** table in the **HumanResources** schema of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="4b6bf-105">是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的一个示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-105">is one of the sample databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="4b6bf-106">**myTeam** 表包含以下几列。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-106">The **myTeam** table is contains the following columns.</span></span>  
  
|<span data-ttu-id="4b6bf-107">列</span><span class="sxs-lookup"><span data-stu-id="4b6bf-107">Column</span></span>|<span data-ttu-id="4b6bf-108">数据类型</span><span class="sxs-lookup"><span data-stu-id="4b6bf-108">Data type</span></span>|<span data-ttu-id="4b6bf-109">可空性</span><span class="sxs-lookup"><span data-stu-id="4b6bf-109">Nullability</span></span>|<span data-ttu-id="4b6bf-110">说明</span><span class="sxs-lookup"><span data-stu-id="4b6bf-110">Description</span></span>|  
|------------|---------------|-----------------|-----------------|  
|<span data-ttu-id="4b6bf-111">**EmployeeID**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-111">**EmployeeID**</span></span>|`smallint`|<span data-ttu-id="4b6bf-112">非空</span><span class="sxs-lookup"><span data-stu-id="4b6bf-112">Not null</span></span>|<span data-ttu-id="4b6bf-113">行的主键。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-113">Primary key for the rows.</span></span> <span data-ttu-id="4b6bf-114">我的工作组中成员的雇员 ID。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-114">Employee ID of a member of my team.</span></span>|  
|<span data-ttu-id="4b6bf-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-115">**Name**</span></span>|`nvarchar(50)`|<span data-ttu-id="4b6bf-116">非空</span><span class="sxs-lookup"><span data-stu-id="4b6bf-116">Not null</span></span>|<span data-ttu-id="4b6bf-117">我的工作组中成员的名称。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-117">Name of a member of my team.</span></span>|  
|<span data-ttu-id="4b6bf-118">**标题**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-118">**Title**</span></span>|`nvarchar(50)`|<span data-ttu-id="4b6bf-119">Nullable</span><span class="sxs-lookup"><span data-stu-id="4b6bf-119">Nullable</span></span>|<span data-ttu-id="4b6bf-120">我的工作组中雇员的职位。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-120">Title the employee performs on my team.</span></span>|  
|<span data-ttu-id="4b6bf-121">**背景**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-121">**Background**</span></span>|`nvarchar(50)`|<span data-ttu-id="4b6bf-122">非空</span><span class="sxs-lookup"><span data-stu-id="4b6bf-122">Not null</span></span>|<span data-ttu-id="4b6bf-123">上次更新行的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-123">Date and time the row was last updated.</span></span> <span data-ttu-id="4b6bf-124">（默认值）</span><span class="sxs-lookup"><span data-stu-id="4b6bf-124">(Default)</span></span>|  
  
 <span data-ttu-id="4b6bf-125">**创建 HumanResources.myTeam**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-125">**To create HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="4b6bf-126">使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="4b6bf-126">Use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 <span data-ttu-id="4b6bf-127">**填充 HumanResources.myTeam**</span><span class="sxs-lookup"><span data-stu-id="4b6bf-127">**To populate HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="4b6bf-128">执行下列 `INSERT` 语句以在表中填充两行：</span><span class="sxs-lookup"><span data-stu-id="4b6bf-128">Execute following `INSERT` statements to populate the table with two rows:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b6bf-129">这些语句跳过第四列，即 `Background`列。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-129">These statements skip the fourth column, `Background`.</span></span> <span data-ttu-id="4b6bf-130">这样会有默认值。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-130">This has a default value.</span></span> <span data-ttu-id="4b6bf-131">跳过该列使 `INSERT` 语句将该列保留为空。</span><span class="sxs-lookup"><span data-stu-id="4b6bf-131">Skipping this column causes this `INSERT` statement to leave this column blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6bf-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b6bf-132">See Also</span></span>  
 [<span data-ttu-id="4b6bf-133">批量导入和导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b6bf-133">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](bulk-import-and-export-of-data-sql-server.md)  
  
  
