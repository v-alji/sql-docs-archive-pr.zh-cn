---
title: 指定列的默认值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 650347c29e1175c5a1fe646fc079478520dc8c6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589455"
---
# <a name="specify-default-values-for-columns"></a><span data-ttu-id="a3e6b-102">指定列的默认值</span><span class="sxs-lookup"><span data-stu-id="a3e6b-102">Specify Default Values for Columns</span></span>
  <span data-ttu-id="a3e6b-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定将在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的列中输入的默认值。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-103">You can specify a default value that will be entered in the column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a3e6b-104">如果您没有分配默认值，并且将该列保留为空白，则：</span><span class="sxs-lookup"><span data-stu-id="a3e6b-104">If you do not assign a default value and the user leaves the column blank, then:</span></span>  
  
-   <span data-ttu-id="a3e6b-105">如果设置了允许空值的选项，则将向该列中插入 NULL。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-105">If you set the option to allow null values, NULL will be inserted into the column.</span></span>  
  
-   <span data-ttu-id="a3e6b-106">如果没有设置允许空值的选项，则该列将保持空白，但在用户为该列提供值之前，他们将无法保存行。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-106">If you do not set the option to allow null values, the column will remain blank, but the user will not be able to save the row until they supply a value for the column.</span></span>  
  
 <span data-ttu-id="a3e6b-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a3e6b-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a3e6b-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a3e6b-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a3e6b-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3e6b-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a3e6b-110">安全性</span><span class="sxs-lookup"><span data-stu-id="a3e6b-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a3e6b-111">**使用以下工具指定默认值：**</span><span class="sxs-lookup"><span data-stu-id="a3e6b-111">**To specify a default value, using:**</span></span>  
  
     [<span data-ttu-id="a3e6b-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3e6b-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a3e6b-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3e6b-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a3e6b-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="a3e6b-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a3e6b-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3e6b-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a3e6b-116">如果“默认值”\*\*\*\* 字段中的项替换绑定的默认值（以不带圆括号的形式显示），则将提示你解除对默认值的绑定，并将其替换为新的默认值。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-116">If your entry in the **Default Value** field replaces a bound default (which is shown without parentheses), you will be prompted to unbind the default and replace it with your new default.</span></span>  
  
-   <span data-ttu-id="a3e6b-117">若要输入文本字符串，请用单引号 (') 将值括起来；不要使用双引号 (")，因为双引号已保留用于带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-117">To enter a text string, enclose the value in single quotation marks ('); do not use double quotation marks (") because they are reserved for quoted identifiers.</span></span>  
  
-   <span data-ttu-id="a3e6b-118">若要输入数值默认值，请输入数值并且不要用引号将值括起来。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-118">To enter a numeric default, enter the number without quotation marks around it.</span></span>  
  
-   <span data-ttu-id="a3e6b-119">若要输入对象/函数，请输入对象/函数的名称并且不要用引号将名称括起来。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-119">To enter an object/function, enter the name of the object/function without quotation marks around it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a3e6b-120">Security</span><span class="sxs-lookup"><span data-stu-id="a3e6b-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a3e6b-121">权限</span><span class="sxs-lookup"><span data-stu-id="a3e6b-121">Permissions</span></span>  
 <span data-ttu-id="a3e6b-122">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-122">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a3e6b-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3e6b-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="a3e6b-124">指定列的默认值</span><span class="sxs-lookup"><span data-stu-id="a3e6b-124">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="a3e6b-125">在“对象资源管理器”\*\*\*\* 中，右键单击要更改其小数位数的列所在的表，再单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-125">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="a3e6b-126">选择要为其指定默认值的列。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-126">Select the column for which you want to specify a default value.</span></span>  
  
3.  <span data-ttu-id="a3e6b-127">在 **“列属性”** 选项卡中，在 **“默认值或绑定”** 属性中输入新的默认值。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-127">In the **Column Properties** tab, enter the new default value in the **Default Value or Binding** property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3e6b-128">若要输入数值默认值，请输入该数字。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-128">To enter a numeric default value, enter the number.</span></span> <span data-ttu-id="a3e6b-129">对于对象或函数，请输入其名称。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-129">For an object or function enter its name.</span></span> <span data-ttu-id="a3e6b-130">对于字母数字默认值，请输入该值，两边用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-130">For an alphanumeric default enter the value inside single quotes.</span></span>  
  
4.  <span data-ttu-id="a3e6b-131">在“文件”菜单上，单击“保存表名称”\*\*\*\*\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-131">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a3e6b-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3e6b-132">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="a3e6b-133">指定列的默认值</span><span class="sxs-lookup"><span data-stu-id="a3e6b-133">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="a3e6b-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a3e6b-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a3e6b-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 <span data-ttu-id="a3e6b-137">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a3e6b-137">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
