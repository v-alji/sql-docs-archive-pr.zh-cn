---
title: 生成筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0e484c89c97d3f32f3e41197800202f796a25d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578083"
---
# <a name="generate-filters"></a><span data-ttu-id="31c5d-102">生成筛选器</span><span class="sxs-lookup"><span data-stu-id="31c5d-102">Generate Filters</span></span>
  <span data-ttu-id="31c5d-103">使用 **“生成筛选器”** 对话框，可以对合并发布中某一个表定义行筛选器；然后，复制会自动将筛选器扩展到通过外键关系相关的其他表。</span><span class="sxs-lookup"><span data-stu-id="31c5d-103">The **Generate Filters** dialog box allows you to define a row filter on one table in a merge publication; replication then automatically extends the filter to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="31c5d-104">例如，如果对 Customer 表定义筛选器，使其仅包含与法国客户有关的数据，则复制将扩展该筛选器，以便相关的 Orders 表和 Order Details 表仅包含与法国客户相关的信息。</span><span class="sxs-lookup"><span data-stu-id="31c5d-104">For example, if you define a filter on a customer table so that it only contains data on French customers, replication extends that filter so that related orders and order details tables contain only information related to French customers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="31c5d-105">选项</span><span class="sxs-lookup"><span data-stu-id="31c5d-105">Options</span></span>  
 <span data-ttu-id="31c5d-106">使用此对话框可以创建表的行筛选器，包括三个步骤。</span><span class="sxs-lookup"><span data-stu-id="31c5d-106">This dialog box involves a three-step process to create a row filter on a table.</span></span> <span data-ttu-id="31c5d-107">然后，将筛选器扩展到与筛选的表通过主键和外键关系相关的表。</span><span class="sxs-lookup"><span data-stu-id="31c5d-107">The filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span> <span data-ttu-id="31c5d-108">例如，假设有三个表： **Customer**、 **SalesOrderHeader**和 **SalesOrderDetail**，其中 **Customer** 表与 **SalesOrderHeader**表之间有关系， **SalesOrderHeader** 表与 **SalesOrderDetail**表之间有关系，将行筛选器应用于 **Customer**表，则复制会将该筛选器扩展到 **SalesOrderHeader** 表和 **SalesOrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="31c5d-108">For example, given the three tables **Customer**, **SalesOrderHeader**, and **SalesOrderDetail**, with a relationship between **Customer** and **SalesOrderHeader**, and a relationship between **SalesOrderHeader** and **SalesOrderDetail**, apply a row filter to **Customer**, and replication extends that filter to **SalesOrderHeader** and **SalesOrderDetail**.</span></span>  
  
1.  <span data-ttu-id="31c5d-109">**选择要筛选的表。**</span><span class="sxs-lookup"><span data-stu-id="31c5d-109">**Select the table to filter.**</span></span>  
  
     <span data-ttu-id="31c5d-110">从下拉列表框中选择表。</span><span class="sxs-lookup"><span data-stu-id="31c5d-110">Select a table from the drop-down list box.</span></span> <span data-ttu-id="31c5d-111">只有在 **“项目”** 页上所选择的表才会出现在列表框中。</span><span class="sxs-lookup"><span data-stu-id="31c5d-111">Tables appear in the list box only if they were selected on the **Articles** page.</span></span>  
  
2.  <span data-ttu-id="31c5d-112">**完成筛选语句以标识订阅服务器所要接收的表行。**</span><span class="sxs-lookup"><span data-stu-id="31c5d-112">**Complete the filter statement to identify which table rows Subscribers will receive.**</span></span>  
  
     <span data-ttu-id="31c5d-113">定义新的筛选语句。</span><span class="sxs-lookup"><span data-stu-id="31c5d-113">Define a new filter statement.</span></span> <span data-ttu-id="31c5d-114">**“列”** 列表框列出了要从 **“选择要筛选的表”** 中选择的表中发布的所有列。</span><span class="sxs-lookup"><span data-stu-id="31c5d-114">The **Columns** list box lists all the columns that you are publishing from the table you selected in **Select the table to filter**.</span></span> <span data-ttu-id="31c5d-115">**“筛选语句”** 文本区域包括默认的文本，其格式为：</span><span class="sxs-lookup"><span data-stu-id="31c5d-115">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     <span data-ttu-id="31c5d-116">此文本无法更改；请使用标准的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法在 WHERE 关键字后键入筛选子句。</span><span class="sxs-lookup"><span data-stu-id="31c5d-116">This text cannot be changed; type the filter clause after the WHERE keyword using standard [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="31c5d-117">为提高性能，建议您不要在参数化行筛选子句中对列名应用函数，如 `LEFT([MyColumn]) = SUSER_SNAME()`。</span><span class="sxs-lookup"><span data-stu-id="31c5d-117">For performance reasons, we recommended that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="31c5d-118">如果在筛选子句中使用 HOST_NAME 并覆盖 HOST_NAME 值，则可能需要使用 CONVERT 转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="31c5d-118">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="31c5d-119">有关此情况的最佳实践的详细信息，请参阅主题 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)中的“覆盖 HOST_NAME() 值”一节。</span><span class="sxs-lookup"><span data-stu-id="31c5d-119">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  <span data-ttu-id="31c5d-120">**指定将从此表接收数据的订阅数。**</span><span class="sxs-lookup"><span data-stu-id="31c5d-120">**Specify how many subscriptions will receive data from this table.**</span></span>  
  
     <span data-ttu-id="31c5d-121">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="31c5d-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="31c5d-122">通过合并复制，可以指定最适合您的数据和应用程序的分区类型。</span><span class="sxs-lookup"><span data-stu-id="31c5d-122">Merge replication allows you to specify the type of partitions that are best suited to your data and application.</span></span> <span data-ttu-id="31c5d-123">如果选择 **“此表中的行将仅转到一个订阅”** ，则合并复制将设置不重叠分区选项。</span><span class="sxs-lookup"><span data-stu-id="31c5d-123">If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option.</span></span> <span data-ttu-id="31c5d-124">不重叠分区与预计算分区协同工作以提高性能，使用不重叠分区可以将与预计算分区相关联的上载开销降至最低。</span><span class="sxs-lookup"><span data-stu-id="31c5d-124">Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions.</span></span> <span data-ttu-id="31c5d-125">使用的参数化筛选器和联接筛选器越复杂，不重叠分区的性能优势就越明显。</span><span class="sxs-lookup"><span data-stu-id="31c5d-125">The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex.</span></span> <span data-ttu-id="31c5d-126">如果选择此选项，则必须确保对数据分区时不能将行复制到多个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="31c5d-126">If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="31c5d-127">有关详细信息，请参阅主题 [参数化行筛选器](merge/parameterized-filters-parameterized-row-filters.md)中的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="31c5d-127">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="31c5d-128">添加筛选器之后，请单击 **“确定”** 退出并关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="31c5d-128">After you have added a filter, click **OK** to exit and close the dialog box.</span></span> <span data-ttu-id="31c5d-129">将对照 SELECT 子句中的表分析并运行指定的筛选器。</span><span class="sxs-lookup"><span data-stu-id="31c5d-129">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="31c5d-130">如果筛选语句有语法错误或其他问题，将会通知您编辑该筛选语句。</span><span class="sxs-lookup"><span data-stu-id="31c5d-130">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
 <span data-ttu-id="31c5d-131">分析该语句之后，复制将创建必要的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="31c5d-131">After the statement is parsed, replication creates the necessary join filters.</span></span> <span data-ttu-id="31c5d-132">如果您尚未对运行此向导的发布服务器配置分发服务器，系统将会提示您进行配置。</span><span class="sxs-lookup"><span data-stu-id="31c5d-132">If you have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c5d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31c5d-133">See Also</span></span>  
 <span data-ttu-id="31c5d-134">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="31c5d-134">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="31c5d-135">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="31c5d-135">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="31c5d-136">[筛选已发布数据](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="31c5d-136">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="31c5d-137">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="31c5d-137">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="31c5d-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="31c5d-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="31c5d-139">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="31c5d-139">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
