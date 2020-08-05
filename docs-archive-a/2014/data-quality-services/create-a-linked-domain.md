---
title: 创建链接域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.linkeddomain.f1
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 17e91197ecb8cb6ad68769937a8d385d8c73a778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580889"
---
# <a name="create-a-linked-domain"></a><span data-ttu-id="27a1f-102">创建链接域</span><span class="sxs-lookup"><span data-stu-id="27a1f-102">Create a Linked Domain</span></span>
  <span data-ttu-id="27a1f-103">本主题描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的知识库中创建链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-103">This topic describes how to create a linked domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="27a1f-104">链接域可以从先前存在的另一个域创建，并且继承它所链接到的域的所有值、规则和属性，但名称和说明除外。</span><span class="sxs-lookup"><span data-stu-id="27a1f-104">A linked domain is created from another, previously existing domain, and inherits all values, rules, and properties from the domain that it is linked to, with the exception of the name and the description.</span></span> <span data-ttu-id="27a1f-105">您可以将一组链接域作为一个链接域进行管理。</span><span class="sxs-lookup"><span data-stu-id="27a1f-105">You can manage a set of linked domains as one.</span></span> <span data-ttu-id="27a1f-106">通过将一个域链接到另一个域，您可以创建从另一个域继承其内容的域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-106">By linking one domain to the other, you create a domain that inherits its contents from another domain.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="27a1f-107">方案</span><span class="sxs-lookup"><span data-stu-id="27a1f-107">Scenarios</span></span>  
 <span data-ttu-id="27a1f-108">链接域在下列情况下尤其有用。</span><span class="sxs-lookup"><span data-stu-id="27a1f-108">Linked domains are particularly useful in the following scenarios.</span></span>  
  
### <a name="mapping-multiple-fields-to-domains-that-share-values-rules-and-properties"></a><span data-ttu-id="27a1f-109">将多个字段映射到共享值、规则和属性的域</span><span class="sxs-lookup"><span data-stu-id="27a1f-109">Mapping multiple fields to domains that share values, rules, and properties</span></span>  
 <span data-ttu-id="27a1f-110">您无法将两个字段映射到同一个域，但您可以将一个字段映射到一个域，然后将第二个字段映射到已链接到第一个域的域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-110">You cannot map two fields to the same domain, but you could map one field to a domain and then map a second field to a domain linked to the first domain.</span></span> <span data-ttu-id="27a1f-111">这样就将字段映射到具有相同内容和属性（名称和说明除外）的两个不同域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-111">Doing so maps the fields to two different domains that have the same contents and properties (except name and description).</span></span> <span data-ttu-id="27a1f-112">有关详细信息，请参阅 [Map two fields to linked domains](#Map)。</span><span class="sxs-lookup"><span data-stu-id="27a1f-112">For more information, see [Map two fields to linked domains](#Map).</span></span>  
  
### <a name="controlling-data-flow-to-composite-domains"></a><span data-ttu-id="27a1f-113">控制到复合域的数据流</span><span class="sxs-lookup"><span data-stu-id="27a1f-113">Controlling data flow to composite domains</span></span>  
 <span data-ttu-id="27a1f-114">链接域使您能够控制字段与复合域之间的数据流。</span><span class="sxs-lookup"><span data-stu-id="27a1f-114">Linked domains enable you to control the data flow between fields and composite domains.</span></span> <span data-ttu-id="27a1f-115">您可以区分一个字段中的数据何时流向复合域，而另一个非常相似的域中的数据何时不流向复合域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-115">You can differentiate when data from one field flows into a composite domain, and when data from another, very similar field does not flow into the composite domain.</span></span> <span data-ttu-id="27a1f-116">这是通过指定以下内容来实现的：在两个链接域中，一个域是复合域的一部分，而另一个域则不是。</span><span class="sxs-lookup"><span data-stu-id="27a1f-116">You do so by specifying that of two linked domains, one is part of a composite domain, and one is not.</span></span> <span data-ttu-id="27a1f-117">从域角度来看，链接域是完全相同的。</span><span class="sxs-lookup"><span data-stu-id="27a1f-117">From a domain perspective, linked domains are identical.</span></span> <span data-ttu-id="27a1f-118">它们包含同样的知识。</span><span class="sxs-lookup"><span data-stu-id="27a1f-118">They contain the same knowledge.</span></span> <span data-ttu-id="27a1f-119">然而，从复合域的角度来看，链接域是不同的。</span><span class="sxs-lookup"><span data-stu-id="27a1f-119">However, from a composite-domain perspective, linked domains are different.</span></span> <span data-ttu-id="27a1f-120">一个参与复合域；另一个则不参与。</span><span class="sxs-lookup"><span data-stu-id="27a1f-120">One participates in the composite domain; the other does not.</span></span>  
  
 <span data-ttu-id="27a1f-121">例如，一条包含以下字段的记录：Customer First Name、Customer Last Name 和 Father’s First Name。</span><span class="sxs-lookup"><span data-stu-id="27a1f-121">An example is a record that contains the following fields: Customer First Name, Customer Last Name, and Father's First Name.</span></span> <span data-ttu-id="27a1f-122">假设同时将客户的名字和父亲的名字映射到 First Name 域，并使 First Name 域和 Last Name 域成为 Full Name 复合域的组成部分。</span><span class="sxs-lookup"><span data-stu-id="27a1f-122">Suppose you map both customer first name and father's first name to a First Name domain, and make the First Name domain and the Last Name domain a part of a Full Name composite domain.</span></span> <span data-ttu-id="27a1f-123">问题是父亲的名字将添加到复合域，但没有姓氏。</span><span class="sxs-lookup"><span data-stu-id="27a1f-123">The problem is that the father's first name will be added to the composite domain without a last name.</span></span> <span data-ttu-id="27a1f-124">但是，如果将这两个名字字段链接到一个域并链接这两个域，则可以将 Customer First Name 域链接到 Full Name 复合域，但不将 Father’s First Name 字段添加到复合域；从而防止将 Father’s First Name 添加到复合域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-124">If, however, you link each of the two first name fields to a domain, and link the two domains, then you can add the Customer First Name domain to the Full Name composite domain, and not add the Father's First Name field to the composite domain, thereby preventing the Father's First Name from being added to the composite domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="27a1f-125">开始之前</span><span class="sxs-lookup"><span data-stu-id="27a1f-125">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="27a1f-126">先决条件</span><span class="sxs-lookup"><span data-stu-id="27a1f-126">Prerequisites</span></span>  
 <span data-ttu-id="27a1f-127">若要创建链接域，您必须具有知识库和要链接到的现有域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-127">To create a linked domain, you must have a knowledge base and an existing domain that you want to link to.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="27a1f-128">Security</span><span class="sxs-lookup"><span data-stu-id="27a1f-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="27a1f-129">权限</span><span class="sxs-lookup"><span data-stu-id="27a1f-129">Permissions</span></span>  
 <span data-ttu-id="27a1f-130">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能创建链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-130">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a linked domain.</span></span>  
  
##  <a name="create-a-linked-domain"></a><a name="Create"></a><span data-ttu-id="27a1f-131">创建链接域</span><span class="sxs-lookup"><span data-stu-id="27a1f-131">Create a Linked Domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="27a1f-132">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="27a1f-132">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="27a1f-133">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的主屏幕中，打开或创建一个知识库。</span><span class="sxs-lookup"><span data-stu-id="27a1f-133">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="27a1f-134">选择 **“域管理”** 作为活动，然后单击 **“打开”** 或 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="27a1f-134">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="27a1f-135">有关详细信息，请参阅 [创建知识库](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [打开知识库](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="27a1f-135">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="27a1f-136">从 **“域管理”** 页上的 **“域列表”** 中，右键单击您要将新域链接到的域，然后单击 **“创建链接域”**。</span><span class="sxs-lookup"><span data-stu-id="27a1f-136">From the **Domain list** on the **Domain Management** page, right-click the domain that you want to link a new domain to, and then click **Create Linked Domain**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27a1f-137">没有专门用于创造链接域的图标。</span><span class="sxs-lookup"><span data-stu-id="27a1f-137">There is not an icon dedicated to creating a linked domain.</span></span> <span data-ttu-id="27a1f-138">您只能使用上下文菜单中的命令。</span><span class="sxs-lookup"><span data-stu-id="27a1f-138">You can only do so using the command in the context menu.</span></span>  
  
4.  <span data-ttu-id="27a1f-139">在 **“创建域”** 对话框中，输入名称（对知识库唯一）以及说明（最多 256 个字符）。</span><span class="sxs-lookup"><span data-stu-id="27a1f-139">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description of up to 256 characters.</span></span> <span data-ttu-id="27a1f-140">验证所链接到的域的名称是正确的。</span><span class="sxs-lookup"><span data-stu-id="27a1f-140">Verify that the name of the domain linked to is correct.</span></span>  
  
5.  <span data-ttu-id="27a1f-141">单击 **“确定”** 完成创建链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-141">Click **OK** to complete creation of the linked domain.</span></span>  
  
6.  <span data-ttu-id="27a1f-142">如有必要，您可以在“域属性”选项卡中更改链接域的名称或说明。</span><span class="sxs-lookup"><span data-stu-id="27a1f-142">If necessary, you can change the name or description of the linked domain in the Domain Properties tab.</span></span>  
  
7.  <span data-ttu-id="27a1f-143">单击 **“完成”** 以完成域管理活动，如 [结束域管理活动](../../2014/data-quality-services/end-the-domain-management-activity.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="27a1f-143">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="map-two-fields-to-linked-domains"></a><a name="Map"></a><span data-ttu-id="27a1f-144">将两个字段映射到链接域</span><span class="sxs-lookup"><span data-stu-id="27a1f-144">Map two fields to linked domains</span></span>  
  
1.  <span data-ttu-id="27a1f-145">为知识发现活动打开一个知识库，并将此知识库映射到数据库以及表或视图。</span><span class="sxs-lookup"><span data-stu-id="27a1f-145">Open a knowledge base to the knowledge discovery activity, and map the knowledge base to the database and table or view.</span></span>  
  
2.  <span data-ttu-id="27a1f-146">将一个字段映射到域，然后尝试将第二个字段映射到同一个域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-146">Map one field to a domain, and then attempt to map a second field to the same domain.</span></span>  
  
3.  <span data-ttu-id="27a1f-147">在指示域已在使用的弹出式窗口中，单击“是”以创建链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-147">In the popup indicating that the domain is already in use, click Yes to create a linked domain.</span></span>  
  
4.  <span data-ttu-id="27a1f-148">在“创建域”对话框中，输入名称和说明，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="27a1f-148">In the Create Domain dialog box, enter a domain name and description, and then click OK.</span></span>  
  
##  <a name="follow-up-after-creating-a-linked-domain"></a><a name="FollowUp"></a><span data-ttu-id="27a1f-149">跟进：在创建链接域后</span><span class="sxs-lookup"><span data-stu-id="27a1f-149">Follow Up: After Creating a Linked Domain</span></span>  
 <span data-ttu-id="27a1f-150">在创建链接域后，您可以对域执行其他域管理任务，可以执行知识发现以便向域添加知识，或者可以向域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="27a1f-150">After you create a linked domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="27a1f-151">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="27a1f-151">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="behavior-of-a-linked-domain"></a><a name="Behavior"></a><span data-ttu-id="27a1f-152">链接域的行为</span><span class="sxs-lookup"><span data-stu-id="27a1f-152">Behavior of a Linked Domain</span></span>  
 <span data-ttu-id="27a1f-153">可以更改链接域的设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="27a1f-153">You can change the settings for a linked domain as follows:</span></span>  
  
-   <span data-ttu-id="27a1f-154">您可以更改链接域的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="27a1f-154">You can change the name and description of a linked domain.</span></span>  
  
-   <span data-ttu-id="27a1f-155">若要更改 **“数据类型”**、 **“使用前导值”** 或 **“将输出格式设置为”** 属性，请选择链接到的域，然后在该域的 **“域属性”** 选项卡中更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="27a1f-155">To change the domain properties for the **Data Type**, **Use Leading Values**, or **Format Output To** properties, select the domain that you linked to, and change those settings in the **Domain Properties** tab for that domain.</span></span> <span data-ttu-id="27a1f-156">您不能在链接域的属性中更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="27a1f-156">You cannot change those settings in the properties of the linked domain.</span></span> <span data-ttu-id="27a1f-157">有关详细信息，请参阅 [创建域](../../2014/data-quality-services/create-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="27a1f-157">For more information, see [Create a Domain](../../2014/data-quality-services/create-a-domain.md).</span></span>  
  
-   <span data-ttu-id="27a1f-158">可以针对链接域或它链接到的域更改“域管理”页的 **“引用数据”**、 **“域规则”**、 **“域值”** 和 **“基于字词的关系”** 选项卡中的设置，并且这些更改将被另一个域继承。</span><span class="sxs-lookup"><span data-stu-id="27a1f-158">Settings in the **Reference Data**, **Domain Rules**, **Domain Values**, and **Term-based Relations** tabs of the Domain Management page can be changed for either the linked domain or the domain that it was linked to, and the changes will be inherited by the other domain.</span></span>  
  
 <span data-ttu-id="27a1f-159">链接域具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="27a1f-159">Linked domains have the following characteristics:</span></span>  
  
-   <span data-ttu-id="27a1f-160">您不能取消两个域的链接。</span><span class="sxs-lookup"><span data-stu-id="27a1f-160">You cannot unlink two domains.</span></span> <span data-ttu-id="27a1f-161">要删除链接，请删除其中一个链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-161">To remove the link, delete one of the linked domains.</span></span>  
  
-   <span data-ttu-id="27a1f-162">当您在“域管理”页的域列表中选择链接域时，在包含 **“值”** 表的窗格中标识链接域的字符串包括指示该域为链接域的内容。</span><span class="sxs-lookup"><span data-stu-id="27a1f-162">When you select a linked domain in the domain list of the Domain Management page, the string identifying the linked domain in the pane containing the **Value** table contains an indication that the domain is a linked domain.</span></span>  
  
-   <span data-ttu-id="27a1f-163">如果您删除一个域所链接到的域，这两个域都将被删除。</span><span class="sxs-lookup"><span data-stu-id="27a1f-163">If you delete a domain that another domain is linked to, both domains will be deleted.</span></span> <span data-ttu-id="27a1f-164">但是，您可以删除链接域，而不删除所链接到的域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-164">You can, however, delete a linked domain, and the domain linked to will not be deleted.</span></span>  
  
-   <span data-ttu-id="27a1f-165">链接域无法链接到自身已链接到其他域的域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-165">A linked domain cannot be linked to a domain that itself is linked to another domain.</span></span>  
  
-   <span data-ttu-id="27a1f-166">无法为复合域创建链接域或链接复合域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-166">You cannot create a linked domain or a linked composite domain to a composite domain.</span></span>  
  
-   <span data-ttu-id="27a1f-167">当在任意一个“域管理”选项卡上双击链接域时，将打开该域以供编辑，并且名称字符串中指示该域为链接域。</span><span class="sxs-lookup"><span data-stu-id="27a1f-167">When you double-click a linked domain in any of the Domain Management tabs, the domain will be opened to editing with an indication in the name string that it is a linked domain.</span></span>  
  
  
