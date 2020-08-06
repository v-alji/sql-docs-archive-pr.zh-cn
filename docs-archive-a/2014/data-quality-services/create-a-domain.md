---
title: 创建域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.createdomain.f1
ms.assetid: 5c4828f5-bd51-4c29-b3de-87b7d2f2d3e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fad6abd795aa9412bb71d251623d92d3e13b889c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578462"
---
# <a name="create-a-domain"></a><span data-ttu-id="2592d-102">创建域</span><span class="sxs-lookup"><span data-stu-id="2592d-102">Create a Domain</span></span>
  <span data-ttu-id="2592d-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中创建域。</span><span class="sxs-lookup"><span data-stu-id="2592d-103">This topic describes how to create a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="2592d-104">域中的值是字段中数据的语义表示形式。</span><span class="sxs-lookup"><span data-stu-id="2592d-104">The values in the domain are a semantic representation of the data in a field.</span></span> <span data-ttu-id="2592d-105">有关域的详细信息，请参阅[管理域](../../2014/data-quality-services/managing-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="2592d-105">For more information on domains, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
 <span data-ttu-id="2592d-106">可以通过两种方法创建新的域。</span><span class="sxs-lookup"><span data-stu-id="2592d-106">There are two ways to create a new domain.</span></span> <span data-ttu-id="2592d-107">第一种方法是在知识发现活动的“映射”步骤期间，当您正在分析数据示例以便将知识添加到新的或现有的知识库中时。</span><span class="sxs-lookup"><span data-stu-id="2592d-107">The first is during the Map step of the knowledge discovery activity, when you are in the process of analyzing a data sample to add knowledge to a new or existing knowledge base.</span></span> <span data-ttu-id="2592d-108">第二种方法是在域管理活动中，当您创建新域（而非更改现有域）时。</span><span class="sxs-lookup"><span data-stu-id="2592d-108">The second is during the domain management activity, when instead of changing an existing domain, you create a new one.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2592d-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="2592d-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="2592d-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="2592d-110">Prerequisites</span></span>  
 <span data-ttu-id="2592d-111">若要创建域，您必须已创建并打开了知识库。</span><span class="sxs-lookup"><span data-stu-id="2592d-111">To create a domain, you must have created and opened a knowledge base.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2592d-112">Security</span><span class="sxs-lookup"><span data-stu-id="2592d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2592d-113">权限</span><span class="sxs-lookup"><span data-stu-id="2592d-113">Permissions</span></span>  
 <span data-ttu-id="2592d-114">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能创建域。</span><span class="sxs-lookup"><span data-stu-id="2592d-114">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to create a domain.</span></span>  
  
##  <a name="create-a-domain-in-the-knowledge-discovery-activity"></a><a name="Discovery"></a> <span data-ttu-id="2592d-115">在知识发现活动中创建域</span><span class="sxs-lookup"><span data-stu-id="2592d-115">Create a Domain in the Knowledge Discovery Activity</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="2592d-116">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2592d-116">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="2592d-117">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开知识库”** ，然后选择知识库；或单击 **“新建知识库”** 并输入新知识库的属性。</span><span class="sxs-lookup"><span data-stu-id="2592d-117">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
3.  <span data-ttu-id="2592d-118">选择 **“知识发现”** 作为活动，然后单击 **“创建”** 以创建新知识库；或单击 **“打开”** 以打开现有知识库。</span><span class="sxs-lookup"><span data-stu-id="2592d-118">Select **Knowledge Discovery** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
4.  <span data-ttu-id="2592d-119">在 **“映射”** 页上，指定到数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="2592d-119">On the **Map** page, specify a connection to the data source.</span></span> <span data-ttu-id="2592d-120">有关详细信息，请参阅 [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="2592d-120">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
5.  <span data-ttu-id="2592d-121">在 **“映射”** 表中，从某个空行的 **“源列”** 列的下拉列表中选择一个源列。</span><span class="sxs-lookup"><span data-stu-id="2592d-121">In the **Mappings** table, select a source column from the drop-down list for the **Source Column** column of an empty row.</span></span> <span data-ttu-id="2592d-122">如果相应的域不存在，请单击 **“创建域”** 图标。</span><span class="sxs-lookup"><span data-stu-id="2592d-122">If no corresponding domain exists, click the **Create a Domain** icon.</span></span>  
  
##  <a name="create-a-domain-in-the-domain-management-activity"></a><a name="DomainManagement"></a> <span data-ttu-id="2592d-123">在域管理活动中创建域</span><span class="sxs-lookup"><span data-stu-id="2592d-123">Create a Domain in the Domain Management Activity</span></span>  
  
1.  <span data-ttu-id="2592d-124">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开知识库”** ，然后选择知识库；或单击 **“新建知识库”** 并输入新知识库的属性。</span><span class="sxs-lookup"><span data-stu-id="2592d-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
2.  <span data-ttu-id="2592d-125">选择 **“域管理”** 作为活动，然后单击 **“创建”** 以创建新知识库；或单击 **“打开”** 以打开现有知识库。</span><span class="sxs-lookup"><span data-stu-id="2592d-125">Select **Domain Management** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
3.  <span data-ttu-id="2592d-126">在 **“域管理”** 页上，单击域列表上方的 **“创建域”** 图标。</span><span class="sxs-lookup"><span data-stu-id="2592d-126">On the **Domain Management** page, click the **Create a Domain** icon above the Domain list.</span></span>  
  
##  <a name="set-domain-properties"></a><a name="Properties"></a><span data-ttu-id="2592d-127">设置域属性</span><span class="sxs-lookup"><span data-stu-id="2592d-127">Set Domain Properties</span></span>  
  
1.  <span data-ttu-id="2592d-128">在 **“创建域”** 对话框中，输入名称（对知识库唯一）以及说明（可多达 256 个字符）。</span><span class="sxs-lookup"><span data-stu-id="2592d-128">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description up to 256 characters.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2592d-129">有关域属性的详细信息，请参阅 [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2592d-129">For more information about domain properties, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
2.  <span data-ttu-id="2592d-130">在 **“数据类型”** 列表中，选择域中值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2592d-130">From the **Data Type** list, select a data type for the values in the domain.</span></span> <span data-ttu-id="2592d-131">数据类型可以是 **String** （默认值）、 **Date**、 **Integer**或 **Decimal**。</span><span class="sxs-lookup"><span data-stu-id="2592d-131">The data type can be **String** (the default), **Date**, **Integer**, or **Decimal**.</span></span>  
  
3.  <span data-ttu-id="2592d-132">选择 **“使用前导值”** 可指定将输出一组同义词中的前导值，而非是其同义词的值。</span><span class="sxs-lookup"><span data-stu-id="2592d-132">Select **Use Leading Values** to specify that the leading value in a group of synonyms will be output instead of a value that is a synonym to it.</span></span> <span data-ttu-id="2592d-133">取消选择 **“使用前导值”** 可指定每个同义词值以其正确或更正形式输出，并且不会被其组的前导值替换。</span><span class="sxs-lookup"><span data-stu-id="2592d-133">Deselect **Use Leading Values** to specify that each synonym value is output in its correct or corrected form, and is not replaced by the leading value for its group.</span></span>  
  
4.  <span data-ttu-id="2592d-134">如果数据类型为 **String**，则选择 **“标准化字符串”** 可删除域值中的特殊字符，这可以改进匹配可能性。</span><span class="sxs-lookup"><span data-stu-id="2592d-134">If the data type is **String**, select **Normalize String** to remove special characters in the domain values, which may improve the likelihood of matches.</span></span>  
  
5.  <span data-ttu-id="2592d-135">从 **“将输出格式设置为”** 下拉列表中，选择在输出域中的数据值时要采用的格式。</span><span class="sxs-lookup"><span data-stu-id="2592d-135">From the **Format Output to** drop-down list, select the formatting that will be applied when the data values in the domain are output.</span></span> <span data-ttu-id="2592d-136">此格式设置特定于在步骤 2 中选择的数据类型，如下面的列表中所示：</span><span class="sxs-lookup"><span data-stu-id="2592d-136">The formatting is specific to the data type selected in step 2, as shown in the following list:</span></span>  
  
    -   <span data-ttu-id="2592d-137">对于字符串值，您可以指定字符串将是输出为大写、小写还是首字母大写。</span><span class="sxs-lookup"><span data-stu-id="2592d-137">For a string value, you can specify that the string be output as upper case, lower case, or capitalized.</span></span>  
  
    -   <span data-ttu-id="2592d-138">对于日期值，您可以指定日、月和年的格式。</span><span class="sxs-lookup"><span data-stu-id="2592d-138">For a date value, you can specify the format of the day, month, and year.</span></span>  
  
    -   <span data-ttu-id="2592d-139">对于整数值，您可以指定要应用的格式掩码的类型。</span><span class="sxs-lookup"><span data-stu-id="2592d-139">For an integer value, you can specify the type of format mask to be applied.</span></span>  
  
    -   <span data-ttu-id="2592d-140">对于小数值，您可以指定要应用的格式掩码的精确性和类型。</span><span class="sxs-lookup"><span data-stu-id="2592d-140">For a decimal value, you can specify the accuracy and the type of format mask to be applied.</span></span>  
  
     <span data-ttu-id="2592d-141">在 **“将输出格式设置为”** 下拉列表中选择 **“无”** 表示不应用列表中的任何格式。</span><span class="sxs-lookup"><span data-stu-id="2592d-141">Selecting **None** in the **Format Output to** drop-down list means none of the formats in the list will be applied.</span></span>  
  
6.  <span data-ttu-id="2592d-142">如果数据类型为 **String**，则在 **“语言”** 下拉列表中，选择您希望应用的拼写检查器的语言版本（如果您启用了拼写检查器）。</span><span class="sxs-lookup"><span data-stu-id="2592d-142">If the data type is **String**, in the **Language** drop-down list, select which language version of the speller you want to apply if you enable the speller.</span></span>  
  
7.  <span data-ttu-id="2592d-143">如果数据类型为 **String**，则选择 **“启用拼写检查器”** 可在填充域时对所有字符串值运行拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="2592d-143">If the data type is **String**, select **Enable Speller** to run the Speller on all string values when populating the domain.</span></span>  
  
8.  <span data-ttu-id="2592d-144">如果数据类型为 **String**，则选择 **“禁用语法错误算法”** 可填充域而不会检查字符串值是否存在语法错误。</span><span class="sxs-lookup"><span data-stu-id="2592d-144">If the data type is **String**, select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span>  
  
9. <span data-ttu-id="2592d-145">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2592d-145">Click **OK**.</span></span>  
  
10. <span data-ttu-id="2592d-146">单击 **“完成”** 以完成域管理活动，如 [结束域管理活动](../../2014/data-quality-services/end-the-domain-management-activity.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="2592d-146">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-domain"></a><a name="FollowUp"></a> <span data-ttu-id="2592d-147">跟进：创建域后</span><span class="sxs-lookup"><span data-stu-id="2592d-147">Follow Up: After Creating a Domain</span></span>  
 <span data-ttu-id="2592d-148">在创建域后，您可以对域执行其他域管理任务，可以执行知识发现以便向域添加知识，或者可以向域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="2592d-148">After you create a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="2592d-149">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="2592d-149">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
