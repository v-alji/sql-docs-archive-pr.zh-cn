---
title: 指定合并项目冲突解决程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca32ef4936f31ca5c75dfc2df1eb965d17f7b039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690513"
---
# <a name="specify-a-merge-article-resolver"></a><span data-ttu-id="94b4b-102">指定合并项目冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-102">Specify a Merge Article Resolver</span></span>
  <span data-ttu-id="94b4b-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定合并项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-103">This topic describes how to specify a merge article resolver in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="94b4b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="94b4b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="94b4b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="94b4b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="94b4b-106">建议</span><span class="sxs-lookup"><span data-stu-id="94b4b-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="94b4b-107">**指定合并项目冲突解决程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="94b4b-107">**To specify a merge article resolver, using:**</span></span>  
  
     [<span data-ttu-id="94b4b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94b4b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="94b4b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="94b4b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="94b4b-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="94b4b-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="94b4b-111">建议</span><span class="sxs-lookup"><span data-stu-id="94b4b-111">Recommendations</span></span>  
  
-   <span data-ttu-id="94b4b-112">合并复制允许使用下列类型的项目冲突解决程序：</span><span class="sxs-lookup"><span data-stu-id="94b4b-112">Merge replication allows the following types of article resolvers:</span></span>  
  
    -   <span data-ttu-id="94b4b-113">默认冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-113">The default resolver.</span></span> <span data-ttu-id="94b4b-114">默认冲突解决程序的行为取决于订阅是客户端订阅还是服务器订阅。</span><span class="sxs-lookup"><span data-stu-id="94b4b-114">The behavior of the default resolver depends on whether the subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="94b4b-115">有关如何指定订阅类型的详细信息，请参阅[指定合并订阅类型和冲突解决优先级 (SQL Server Management Studio)](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-115">For more information about specifying subscription type, see [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).</span></span>  
  
    -   <span data-ttu-id="94b4b-116">您编写的自定义冲突解决程序，可以是业务逻辑处理程序（以托管代码编写）或基于 COM 的自定义冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-116">A custom resolver you have written, which can be a business logic handler (written in managed code) or a custom COM-based resolver.</span></span> <span data-ttu-id="94b4b-117">有关详细信息，请参阅 [高级合并复制冲突的检测和解决](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-117">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="94b4b-118">如果需要实现针对复制的每一行而非只是针对冲突行执行的自定义逻辑，请参阅 [为合并项目实现业务逻辑处理程序](../implement-a-business-logic-handler-for-a-merge-article.md)中指定合并项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-118">If you need to implement custom logic that is executed for each replicated row, not just for conflicting rows, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="94b4b-119">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 附带的基于 COM 的标准冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-119">A standard COM-based resolver, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="94b4b-120">若要使用默认冲突解决程序以外的其他冲突解决程序，必须将该冲突解决程序复制到运行合并代理的计算机并对其进行注册（如果使用的是业务逻辑处理程序，还必须在发布服务器上注册）。</span><span class="sxs-lookup"><span data-stu-id="94b4b-120">To use a resolver other than the default resolver, you must copy the resolver to the computer on which the Merge Agent runs and register it (if you are using a business logic handler, it must also be registered at the Publisher).</span></span> <span data-ttu-id="94b4b-121">合并代理可以运行于：</span><span class="sxs-lookup"><span data-stu-id="94b4b-121">The Merge Agent runs at:</span></span>  
  
    -   <span data-ttu-id="94b4b-122">分发服务器，对于推送订阅</span><span class="sxs-lookup"><span data-stu-id="94b4b-122">The Distributor for a push subscription</span></span>  
  
    -   <span data-ttu-id="94b4b-123">订阅服务器，对于请求订阅</span><span class="sxs-lookup"><span data-stu-id="94b4b-123">The Subscriber for a pull subscription</span></span>  
  
    -   <span data-ttu-id="94b4b-124">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) 服务器，对于使用 Web 同步的请求订阅</span><span class="sxs-lookup"><span data-stu-id="94b4b-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) server for a pull subscription that uses Web synchronization</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="94b4b-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94b4b-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="94b4b-126">注册冲突解决程序之后，在“项目属性 - \<Article>”对话框（可在新建发布向导和“发布属性 - \<Publication>”对话框中使用）的“冲突解决程序”选项卡上指定项目应使用该冲突解决程序。  </span><span class="sxs-lookup"><span data-stu-id="94b4b-126">After the resolver is registered, specify that an article should use the resolver on the **Resolver** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="94b4b-127">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-127">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-resolver"></a><span data-ttu-id="94b4b-128">指定冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-128">To specify a resolver</span></span>  
  
1.  <span data-ttu-id="94b4b-129">在新建发布向导或“发布属性 - \<Publication>”对话框的“项目” 页上，选择一个表。</span><span class="sxs-lookup"><span data-stu-id="94b4b-129">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table.</span></span>  
  
2.  <span data-ttu-id="94b4b-130">单击 **“项目属性”** ，再单击 **“设置突出显示的表项目的属性”** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-130">Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="94b4b-131">在“项目属性 - \<Article>”页上，单击“冲突解决程序”选项卡 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-131">On the **Article Properties - \<Article>** page, click the **Resolver** tab.</span></span>  
  
4.  <span data-ttu-id="94b4b-132">选择 **“使用自定义冲突解决程序（已在分发服务器上注册）”** ，然后在列表中单击冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-132">Select **Use a custom resolver (registered at the Distributor)**, and then in the list, click the resolver.</span></span>  
  
5.  <span data-ttu-id="94b4b-133">如果冲突解决程序需要输入信息（例如列名），请在 **“输入冲突解决程序所需的信息”** 文本框中指定。</span><span class="sxs-lookup"><span data-stu-id="94b4b-133">If the resolver requires input (such as a column name), specify it in the **Enter information needed by the resolver** text box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="94b4b-134">对需要冲突解决程序的每个项目重复此过程。</span><span class="sxs-lookup"><span data-stu-id="94b4b-134">Repeat this process for each article that requires a resolver.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="94b4b-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="94b4b-135">Using Transact-SQL</span></span>  
  
#### <a name="to-register-a-custom-conflict-resolver"></a><span data-ttu-id="94b4b-136">注册自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-136">To register a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="94b4b-137">如果打算注册您自己的自定义冲突解决程序，请创建以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="94b4b-137">If you plan to register your own custom conflict resolver, create one of the following types:</span></span>  
  
    -   <span data-ttu-id="94b4b-138">作为业务逻辑处理程序的基于托管代码的冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-138">Managed code-based resolver as a business logic handler.</span></span> <span data-ttu-id="94b4b-139">有关详细信息，请参阅 [为合并项目实现业务逻辑处理程序](../implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-139">For more information, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="94b4b-140">基于存储过程的冲突解决程序和基于 COM 的冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-140">Stored procedure-based resolver and COM-based resolver.</span></span> <span data-ttu-id="94b4b-141">有关详细信息，请参阅 [为合并项目实现自定义冲突解决程序](../implement-a-custom-conflict-resolver-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-141">For more information, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
2.  <span data-ttu-id="94b4b-142">若要确定所需冲突解决程序是否已注册，请在发布服务器上对任意数据库执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-142">To determine if the desired resolver is already registered, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) at the Publisher on any database.</span></span> <span data-ttu-id="94b4b-143">这将显示自定义冲突解决程序的说明以及在分发服务器上注册的每个基于 COM 的冲突解决程序的类标识符 (CLSID)，或者显示在分发服务器上注册的每个业务逻辑处理程序的托管程序集相关信息。</span><span class="sxs-lookup"><span data-stu-id="94b4b-143">This displays a description of the custom resolver as well as the class identifier (CLSID) for each COM-based resolver registered at the Distributor or information on the managed assembly for each business logic handler registered at the Distributor.</span></span>  
  
3.  <span data-ttu-id="94b4b-144">如果尚未注册所需的自定义解决程序，请在分发服务器上执行 [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-144">If the desired custom resolver is not already registered, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="94b4b-145">指定冲突解决程序的名称 **@article_resolver** ; 对于业务逻辑处理程序，这是程序集的友好名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-145">Specify a name for the resolver for **@article_resolver**; for a business logic handler, this is the friendly name of the assembly.</span></span> <span data-ttu-id="94b4b-146">对于基于 COM 的冲突解决程序，请指定的 DLL 的 CLSID **@resolver_clsid** ，对于业务逻辑处理程序，请将的值指定为，为指定 `true` **@is_dotnet_assembly** 程序集的名称， **@dotnet_assembly_name** 并为替代的类指定完全限定的名称 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-146">For COM-based resolvers, specify the CLSID of the DLL for **@resolver_clsid**, and for a business logic handler, specify a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="94b4b-147">如果业务逻辑处理程序程序集未部署在与合并代理可执行文件相同的目录中、与同步启动合并代理的应用程序相同的目录中，或在全局程序集缓存 (GAC) ，则需要使用的程序集名称指定完整路径 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-147">If a business logic handler assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span>  
  
4.  <span data-ttu-id="94b4b-148">如果冲突解决程序是基于 COM 的冲突解决程序，则：</span><span class="sxs-lookup"><span data-stu-id="94b4b-148">If the resolver is a COM-based resolver:</span></span>  
  
    -   <span data-ttu-id="94b4b-149">将自定义冲突解决程序 DLL 复制到分发服务器（对于推送订阅）或订阅服务器（对于请求订阅）。</span><span class="sxs-lookup"><span data-stu-id="94b4b-149">Copy the custom resolver DLL to the Distributor for push subscriptions or to the Subscriber for pull subscriptions.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="94b4b-150">自定义冲突解决程序位于 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM 目录中。</span><span class="sxs-lookup"><span data-stu-id="94b4b-150">custom resolvers can be found in the [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM directory.</span></span>  
  
    -   <span data-ttu-id="94b4b-151">使用 regsvr32.exe 向操作系统注册自定义冲突解决程序 DLL。</span><span class="sxs-lookup"><span data-stu-id="94b4b-151">Use regsvr32.exe to register the custom resolver DLL with the operating system.</span></span> <span data-ttu-id="94b4b-152">例如，从命令提示符处执行以下命令可注册 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 累加性冲突解决程序：</span><span class="sxs-lookup"><span data-stu-id="94b4b-152">For example, executing the following from the command prompt registers the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver:</span></span>  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  <span data-ttu-id="94b4b-153">如果冲突解决程序为业务逻辑处理程序，则将程序集部署在与合并代理可执行文件相同的文件夹中 ( # A0) ，与调用合并代理的应用程序相同的文件夹中，或部署在步骤3中为参数指定的文件夹中 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-153">If the resolver is a business logic handler, deploy the assembly in the same folder as the Merge Agent executable (replmerg.exe), in the same folder as an application that invokes the Merge Agent, or in the folder specified for the **@dotnet_assembly_name** parameter in step 3.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="94b4b-154">合并代理可执行文件的默认安装位置为 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM。</span><span class="sxs-lookup"><span data-stu-id="94b4b-154">The default installation location of the Merge Agent executable is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a><span data-ttu-id="94b4b-155">定义合并项目时指定自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-155">To specify a custom resolver when defining a merge article</span></span>  
  
1.  <span data-ttu-id="94b4b-156">如果您打算使用自定义冲突解决程序，请通过上述过程创建和注册冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-156">If you plan to use a custom conflict resolver, create and register the resolver using the above procedure.</span></span>  
  
2.  <span data-ttu-id="94b4b-157">在发布服务器上执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，并记下所需自定义冲突解决程序在结果集的 **value** 字段中的名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-157">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of result set.</span></span>  
  
3.  <span data-ttu-id="94b4b-158">在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-158">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="94b4b-159">使用参数指定步骤2中的冲突解决程序的名称 **@article_resolver** ，并为自定义解析程序指定任何所需的输入 **@resolver_info** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-159">Specify the name of the resolver from step 2 for **@article_resolver** and any required input to the custom resolver using the **@resolver_info** parameter.</span></span> <span data-ttu-id="94b4b-160">对于基于存储过程的自定义冲突解决 **@resolver_info** 程序，为存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-160">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="94b4b-161">有关 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 提供的冲突解决程序所需输入内容的详细信息，请参阅 [Microsoft 基于 COM 的冲突解决程序](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-161">For more information about required input for resolvers supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a><span data-ttu-id="94b4b-162">为现有合并项目指定或更改自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-162">To specify or change a custom resolver for an existing merge article</span></span>  
  
1.  <span data-ttu-id="94b4b-163">若要确定是否已为项目定义自定义冲突解决程序，或要获取冲突解决程序的名称，请执行 [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-163">To determine if a custom resolver has been defined for an article, or to get the name of the resolver, execute [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="94b4b-164">如果已为项目定义自定义冲突解决程序，则其名称将显示在 **article_resolver** 字段中。</span><span class="sxs-lookup"><span data-stu-id="94b4b-164">If there is a custom resolver defined for the article, its name will be displayed in the **article_resolver** field.</span></span> <span data-ttu-id="94b4b-165">为冲突解决程序提供的任何输入内容都将显示在结果集的 **resolver_info** 字段中。</span><span class="sxs-lookup"><span data-stu-id="94b4b-165">Any input supplied to the resolver will be displayed in the **resolver_info** field of the result set.</span></span>  
  
2.  <span data-ttu-id="94b4b-166">在发布服务器上执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，并记下所需自定义冲突解决程序在结果集的 **value** 字段中的名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-166">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of the result set.</span></span>  
  
3.  <span data-ttu-id="94b4b-167">在发布服务器上，对发布数据库执行 [sp_changemergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-167">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="94b4b-168">将 **article_resolver**的值指定为 **@property**（包括业务逻辑处理程序的完整路径），并为 **@value**中指定合并项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-168">Specify a value of **article_resolver**, including the full path for business logic handlers, for **@property**, and the name of the desired custom resolver from step 2 for **@value**.</span></span>  
  
4.  <span data-ttu-id="94b4b-169">若要更改自定义冲突解决程序所需的任何输入内容，请再次执行 [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-169">To change any required input for the custom resolver, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="94b4b-170">将 **resolver_info** @is_dotnet_assembly **@property** 并为 **@value**中指定合并项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="94b4b-170">Specify a value of **resolver_info** for **@property** and any required input to the custom resolver for **@value**.</span></span> <span data-ttu-id="94b4b-171">对于基于存储过程的自定义冲突解决 **@resolver_info** 程序，为存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-171">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="94b4b-172">有关所需输入内容的详细信息，请参阅 [Microsoft 基于 COM 的冲突解决程序](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-172">For more information about required input, see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a><span data-ttu-id="94b4b-173">撤消注册自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-173">To unregister a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="94b4b-174">在发布服务器上执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，并记下要删除的自定义冲突解决程序在结果集的 **value** 字段中的名称。</span><span class="sxs-lookup"><span data-stu-id="94b4b-174">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the custom resolver to remove in the **value** field of the result set.</span></span>  
  
2.  <span data-ttu-id="94b4b-175">在分发服务器上执行 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="94b4b-175">Execute [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="94b4b-176">为提供步骤1中自定义冲突解决程序的完整名称 **@article_resolver** 。</span><span class="sxs-lookup"><span data-stu-id="94b4b-176">Specify the full name of the custom resolver from step 1 for **@article_resolver**.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="94b4b-177">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="94b4b-177">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="94b4b-178">本示例创建了一个新项目，并指定当发生冲突时，将使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 平均化冲突解决程序计算 **UnitPrice** 列的平均值。</span><span class="sxs-lookup"><span data-stu-id="94b4b-178">This example creates a new article and specifies that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver be used to calculate the average of the **UnitPrice** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 <span data-ttu-id="94b4b-179">本示例更改了一个项目以指定当发生冲突时，将使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 累加性冲突解决程序计算 **UnitsOnOrder** 列的总和。</span><span class="sxs-lookup"><span data-stu-id="94b4b-179">This example changes an article to specify using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver to calculate the sum of the **UnitsOnOrder** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a><span data-ttu-id="94b4b-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94b4b-180">See Also</span></span>  
 <span data-ttu-id="94b4b-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="94b4b-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="94b4b-182">为合并项目实现业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="94b4b-182">Implement a Business Logic Handler for a Merge Article</span></span>](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
