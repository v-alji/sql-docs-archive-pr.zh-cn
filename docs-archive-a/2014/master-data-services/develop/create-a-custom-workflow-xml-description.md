---
title: 自定义工作流 XML 说明 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77906426ddb901ec422367bf30aabef2e532ad06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591923"
---
# <a name="custom-workflow-xml-description-master-data-services"></a><span data-ttu-id="ac120-102">自定义工作流 XML 说明 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ac120-102">Custom Workflow XML Description (Master Data Services)</span></span>
  <span data-ttu-id="ac120-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ，当工作流启动时，SQL SERVER MDS Workflow Integration Service 会调用[WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))方法。</span><span class="sxs-lookup"><span data-stu-id="ac120-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="ac120-104">此方法将有关触发工作流业务规则的项的元数据和数据作为 XML 块接收。</span><span class="sxs-lookup"><span data-stu-id="ac120-104">This method receives metadata and data about the item that triggered the workflow business rule as a block of XML.</span></span> <span data-ttu-id="ac120-105">有关实现工作流处理程序的代码示例，请参阅[自定义工作流示例 &#40;Master Data Services&#41;](create-a-custom-workflow-example.md)。</span><span class="sxs-lookup"><span data-stu-id="ac120-105">For example code that implements a workflow handler, see [Custom Workflow Example &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).</span></span>  
  
 <span data-ttu-id="ac120-106">下面的示例说明发送到工作流处理程序的 XML 可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="ac120-106">The following example shows what the XML that is sent to the workflow handler might look like:</span></span>  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 <span data-ttu-id="ac120-107">下表描述此 XML 所包含的一些标记：</span><span class="sxs-lookup"><span data-stu-id="ac120-107">The following table describes some of the tags contained in this XML:</span></span>  
  
|<span data-ttu-id="ac120-108">标记</span><span class="sxs-lookup"><span data-stu-id="ac120-108">Tag</span></span>|<span data-ttu-id="ac120-109">说明</span><span class="sxs-lookup"><span data-stu-id="ac120-109">Description</span></span>|  
|---------|-----------------|  
|\<Type>|<span data-ttu-id="ac120-110">在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的“工作流类型”文本框中输入的文本，用于标识要加载的自定义工作流程序集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac120-110">The text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to identify which custom workflow assembly to load.</span></span>|  
|\<SendData>|<span data-ttu-id="ac120-111">由 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中的“消息中包括成员数据”复选框控制的一个布尔值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac120-111">A Boolean value controlled by the **Include member data in the message** checkbox in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="ac120-112">如果值为1，则表示 \<MemberData> 发送部分; 否则， \<MemberData> 不会发送部分。</span><span class="sxs-lookup"><span data-stu-id="ac120-112">A value of 1 means that the \<MemberData> section is sent; otherwise the \<MemberData> section is not sent.</span></span>|  
|<span data-ttu-id="ac120-113"><Server_URL></span><span class="sxs-lookup"><span data-stu-id="ac120-113"><Server_URL></span></span>|<span data-ttu-id="ac120-114">在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中的“工作流站点”文本框中输入的文本\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac120-114">The text you entered in the **Workflow site** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|<span data-ttu-id="ac120-115"><Action_ID></span><span class="sxs-lookup"><span data-stu-id="ac120-115"><Action_ID></span></span>|<span data-ttu-id="ac120-116">在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中的“工作流名称”文本框中输入的文本\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac120-116">The text you entered in the **Workflow name** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|\<MemberData>|<span data-ttu-id="ac120-117">包含触发工作流操作的成员的数据。</span><span class="sxs-lookup"><span data-stu-id="ac120-117">Contains the data of the member that triggered the workflow action.</span></span> <span data-ttu-id="ac120-118">仅当的值为1时才包括 \<SendData> 。</span><span class="sxs-lookup"><span data-stu-id="ac120-118">This is included only if the value of \<SendData> is 1.</span></span>|  
|\<Enter*xxx*>|<span data-ttu-id="ac120-119">这组标记包含有关创建成员的元数据，例如，何时创建该成员或该成员的创建者。</span><span class="sxs-lookup"><span data-stu-id="ac120-119">This set of tags contains metadata about the creation of the member, such as when it was created and who created it.</span></span>|  
|\<LastChg*xxx*>|<span data-ttu-id="ac120-120">这组标记包含有关对成员所作最后更改的元数据，例如，所作更改及更改者。</span><span class="sxs-lookup"><span data-stu-id="ac120-120">This set of tags contains metadata about the last change made to the member, such as when the change was made and who made it.</span></span>|  
|\<Name>|<span data-ttu-id="ac120-121">已更改的成员的第一个属性。</span><span class="sxs-lookup"><span data-stu-id="ac120-121">The first attribute of the member that was changed.</span></span> <span data-ttu-id="ac120-122">此示例成员仅包含 Name 和 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="ac120-122">This example member contains only Name and Code attributes.</span></span>|  
|\<Code>|<span data-ttu-id="ac120-123">已更改的成员的下一个属性。</span><span class="sxs-lookup"><span data-stu-id="ac120-123">The next attribute of the member that was changed.</span></span> <span data-ttu-id="ac120-124">如果此示例成员包含更多属性，它们将遵循这一属性。</span><span class="sxs-lookup"><span data-stu-id="ac120-124">If this example member contained more attributes, they would follow this one.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac120-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac120-125">See Also</span></span>  
 <span data-ttu-id="ac120-126">[Master Data Services 创建自定义工作流 &#40;&#41;](create-a-custom-workflow-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ac120-126">[Create a Custom Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md) </span></span>  
 [<span data-ttu-id="ac120-127">自定义工作流示例 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ac120-127">Custom Workflow Example &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-example.md)  
  
  
