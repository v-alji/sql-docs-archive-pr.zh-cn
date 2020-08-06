---
title: 指定架构选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691178"
---
# <a name="specify-schema-options"></a><span data-ttu-id="3cf16-102">指定架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-102">Specify Schema Options</span></span>
  <span data-ttu-id="3cf16-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定架构选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-103">This topic describes how to specify schema options in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3cf16-104">在发布表或视图时，可以控制为发布的对象复制的对象创建选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-104">When you are publishing a table or view, you can control the object creation options that are replicated for the published object.</span></span> <span data-ttu-id="3cf16-105">创建项目时可以设置这些选项，还可以在以后更改它们。</span><span class="sxs-lookup"><span data-stu-id="3cf16-105">You can set these option when the article is created, and you can also change them at a later time.</span></span> <span data-ttu-id="3cf16-106">如果没有为某项目显式指定这些选项，将定义默认的选项集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-106">If you do not explicitly specify these options for an article, a default set of options will be defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cf16-107">使用复制存储过程时的默认架构选项可能与使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]添加项目时的默认选项不同。</span><span class="sxs-lookup"><span data-stu-id="3cf16-107">The default schema options when using replication stored procedures may differ from the default options when articles are added using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3cf16-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3cf16-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3cf16-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3cf16-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3cf16-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3cf16-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3cf16-111">建议</span><span class="sxs-lookup"><span data-stu-id="3cf16-111">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="3cf16-112">**指定架构选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="3cf16-112">**To specify schema options, using:**</span></span>  
  
     [<span data-ttu-id="3cf16-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3cf16-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3cf16-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3cf16-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3cf16-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="3cf16-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3cf16-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3cf16-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3cf16-117">如果在创建发布后更改架构选项，则必须生成新的快照。</span><span class="sxs-lookup"><span data-stu-id="3cf16-117">If you change schema options after a publication is created, you must generate a new snapshot.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3cf16-118">建议</span><span class="sxs-lookup"><span data-stu-id="3cf16-118">Recommendations</span></span>  
  
-   <span data-ttu-id="3cf16-119">有关架构选项的完整列表，请参阅 sp_addarticle 的\*\* \@ schema_option\*\*参数[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)和[sp_addmergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-119">For the complete list of schema options, see the **\@schema_option** parameter of [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3cf16-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3cf16-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3cf16-121">在“项目属性 - \<Article>”对话框的“属性”选项卡上指定架构选项，例如是否将约束和触发器复制到订阅服务器 。</span><span class="sxs-lookup"><span data-stu-id="3cf16-121">Specify schema options, such as whether to copy constraints and triggers to Subscribers, on the **Properties** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="3cf16-122">此选项卡可在新建发布向导和“发布属性 - \<Publication>”对话框中获得。</span><span class="sxs-lookup"><span data-stu-id="3cf16-122">This tab is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="3cf16-123">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-schema-options"></a><span data-ttu-id="3cf16-124">指定架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-124">To specify schema options</span></span>  
  
1.  <span data-ttu-id="3cf16-125">在“新建发布”向导或“发布属性 - \<Publication>”对话框的“项目”页面上，选择一个项目，然后单击“项目属性”  。</span><span class="sxs-lookup"><span data-stu-id="3cf16-125">On the **Articles** Page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="3cf16-126">选择要将架构选项更改应用于哪些项目：</span><span class="sxs-lookup"><span data-stu-id="3cf16-126">Select which articles schema option changes should apply to:</span></span>  
  
    -   <span data-ttu-id="3cf16-127">单击“设置突出显示的 \<ObjectType> 项目的属性”以启动“项目属性 - \<ObjectName>”对话框；在此对话框中进行的属性更改仅应用于在“项目”页上的对象窗格中突出显示的对象。  </span><span class="sxs-lookup"><span data-stu-id="3cf16-127">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="3cf16-128">单击“设置所有 \<ObjectType> 项目的属性”以启动“所有 \<ObjectType> 项目的属性”对话框；在此对话框中进行的属性更改应用于“项目”页面上对象窗格中该类型的所有对象，包括尚未选择进行发布的对象  。</span><span class="sxs-lookup"><span data-stu-id="3cf16-128">Click **Set Properties of All \<ObjectType> Articles** to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3cf16-129">在“所有 \<ObjectType> 项目的属性”对话框中进行的属性更改会替代之前在“项目属性 - \<ObjectName>”对话框中进行的任何更改。 </span><span class="sxs-lookup"><span data-stu-id="3cf16-129">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="3cf16-130">例如，若要为某对象类型的所有项目设置一些默认值，但还希望为单个对象设置一些属性，请首先设置所有项目的默认值。</span><span class="sxs-lookup"><span data-stu-id="3cf16-130">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="3cf16-131">然后再设置单个对象的属性。</span><span class="sxs-lookup"><span data-stu-id="3cf16-131">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="3cf16-132">在“项目属性 - \<Article>”对话框的“属性”选项卡的“将对象和设置复制到订阅服务器”和“目标对象”部分中，为各选项指定值   。</span><span class="sxs-lookup"><span data-stu-id="3cf16-132">In the **Copy Objects and Settings to Subscriber** and **Destination Object** sections of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify values for the options.</span></span>  
  
4.  <span data-ttu-id="3cf16-133">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3cf16-133">Modify any properties if necessary, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="3cf16-134">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="3cf16-134">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3cf16-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3cf16-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="3cf16-136">架构选项指定为十六进制值，该值为一个或多个选项的 [|（位或）](/sql/t-sql/language-elements/bitwise-or-transact-sql) 结果。</span><span class="sxs-lookup"><span data-stu-id="3cf16-136">Schema options are specified as a hexadecimal value that is the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more options.</span></span> <span data-ttu-id="3cf16-137">有关详细信息，请参阅 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 和 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-137">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cf16-138">必须先将架构选项值从 **binary** 转换为 **int** ，才能执行位运算。</span><span class="sxs-lookup"><span data-stu-id="3cf16-138">You must convert schema option values from **binary** to **int** before performing a bitwise operation.</span></span> <span data-ttu-id="3cf16-139">有关详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-139">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3cf16-140">为快照或事务发布定义项目时指定架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-140">To specify schema options when defining an article for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3cf16-141">在发布服务器上，对发布数据库执行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-141">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="3cf16-142">指定项目所属的**发布的名称、项目 \@ \*\* \*\* \@ 的**名称、要发布的数据库对象\*\* \@ source_object**、 \*\* \@ 类型**的数据库对象类型，以及\*\* \@ schema_option\*\*的一个或多个架构选项的[| (位或) ](/sql/t-sql/language-elements/bitwise-or-transact-sql)结果。</span><span class="sxs-lookup"><span data-stu-id="3cf16-142">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, the type of database object for **\@type**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="3cf16-143">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-143">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a><span data-ttu-id="3cf16-144">为合并发布定义项目时指定架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-144">To specify schema options when defining an article for a merge publication</span></span>  
  
1.  <span data-ttu-id="3cf16-145">在发布服务器上，对发布数据库执行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-145">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="3cf16-146">指定项目所属的**发布的名称、项目 \@ **的名称、要为** \@ source_object**发布的数据库对象， \*\* \@ **以及** \@ Schema_option\*\*的一个或多个架构选项的[| (按位或) ](/sql/t-sql/language-elements/bitwise-or-transact-sql)结果。</span><span class="sxs-lookup"><span data-stu-id="3cf16-146">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="3cf16-147">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-147">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3cf16-148">更改快照发布或事务发布中的现有项目的架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-148">To change schema options for an existing article in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3cf16-149">在发布服务器上，对发布数据库执行 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-149">At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="3cf16-150">指定项目所属的\*\* \@ 发布的名称，并指定\*\* \*\* \@ 项目的项目名称。\*\*</span><span class="sxs-lookup"><span data-stu-id="3cf16-150">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="3cf16-151">记下结果集中 **schema_option** 列的值。</span><span class="sxs-lookup"><span data-stu-id="3cf16-151">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="3cf16-152">使用步骤 1 中的值和所需的架构选项值执行 [&（按位与）](/sql/t-sql/language-elements/bitwise-and-transact-sql)运算，以确定是否设置了此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-152">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="3cf16-153">如果结果为 **0**，则表示未设置此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-153">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="3cf16-154">如果结果为选项值，则表示已设置此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-154">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="3cf16-155">如果未设置此选项，则使用步骤 1 中的值和所需的架构选项值执行 [|（位或）](/sql/t-sql/language-elements/bitwise-or-transact-sql) 运算。</span><span class="sxs-lookup"><span data-stu-id="3cf16-155">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="3cf16-156">在发布服务器上，对发布数据库执行 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-156">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="3cf16-157">指定项目所属的**发布的名称、项目 \@ \*\* \*\* \@ 的项目名称、** \*\* \@ 属性**的**schema_option**的值，以及** \@ 值\*\*的步骤3中的十六进制结果。</span><span class="sxs-lookup"><span data-stu-id="3cf16-157">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="3cf16-158">运行快照代理以生成新快照。</span><span class="sxs-lookup"><span data-stu-id="3cf16-158">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="3cf16-159">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-159">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a><span data-ttu-id="3cf16-160">为合并发布中的现有项目更改架构选项</span><span class="sxs-lookup"><span data-stu-id="3cf16-160">To change schema options for an existing article in a merge publication</span></span>  
  
1.  <span data-ttu-id="3cf16-161">在发布服务器上，对发布数据库执行 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-161">At the Publisher on the publication database, execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="3cf16-162">指定项目所属的\*\* \@ 发布的名称，并指定\*\* \*\* \@ 项目的项目名称。\*\*</span><span class="sxs-lookup"><span data-stu-id="3cf16-162">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="3cf16-163">记下结果集中 **schema_option** 列的值。</span><span class="sxs-lookup"><span data-stu-id="3cf16-163">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="3cf16-164">使用步骤 1 中的值和所需的架构选项值执行 [&（按位与）](/sql/t-sql/language-elements/bitwise-and-transact-sql)运算，以确定是否设置了此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-164">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="3cf16-165">如果结果为 **0**，则表示未设置此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-165">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="3cf16-166">如果结果为选项值，则表示已设置此选项。</span><span class="sxs-lookup"><span data-stu-id="3cf16-166">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="3cf16-167">如果未设置此选项，则使用步骤 1 中的值和所需的架构选项值执行 [|（位或）](/sql/t-sql/language-elements/bitwise-or-transact-sql) 运算。</span><span class="sxs-lookup"><span data-stu-id="3cf16-167">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="3cf16-168">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-168">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="3cf16-169">指定项目所属的**发布的名称、项目 \@ \*\* \*\* \@ 的项目名称、** \*\* \@ 属性**的**schema_option**的值，以及** \@ 值\*\*的步骤3中的十六进制结果。</span><span class="sxs-lookup"><span data-stu-id="3cf16-169">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="3cf16-170">运行快照代理以生成新快照。</span><span class="sxs-lookup"><span data-stu-id="3cf16-170">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="3cf16-171">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-171">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf16-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cf16-172">See Also</span></span>  
 <span data-ttu-id="3cf16-173">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="3cf16-173">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="3cf16-174">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="3cf16-174">Article Options for Transactional Replication</span></span>](../transactional/article-options-for-transactional-replication.md)  
  
  
