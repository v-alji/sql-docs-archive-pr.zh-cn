---
title: 传输错误消息任务编辑器 (消息 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0d626f01e05a30777810b26880da5aedc3e7ad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591952"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a><span data-ttu-id="84b7a-102">传输错误消息任务编辑器（“消息”页）</span><span class="sxs-lookup"><span data-stu-id="84b7a-102">Transfer Error Messages Task Editor (Messages Page)</span></span>
  <span data-ttu-id="84b7a-103">可以使用“传输错误消息任务编辑器”对话框的“消息”页指定属性，以将一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用户定义错误消息从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例复制到另一个实例。</span><span class="sxs-lookup"><span data-stu-id="84b7a-103">Use the **Messages** page of the **Transfer Error Messages Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user-defined error messages from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="84b7a-104">有关此任务的详细信息，请参阅 [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md)。</span><span class="sxs-lookup"><span data-stu-id="84b7a-104">For more information about this task, see [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="84b7a-105">选项</span><span class="sxs-lookup"><span data-stu-id="84b7a-105">Options</span></span>  
 <span data-ttu-id="84b7a-106">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="84b7a-106">**SourceConnection**</span></span>  
 <span data-ttu-id="84b7a-107">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="84b7a-107">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="84b7a-108">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="84b7a-108">**DestinationConnection**</span></span>  
 <span data-ttu-id="84b7a-109">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="84b7a-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="84b7a-110">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="84b7a-110">**IfObjectExists**</span></span>  
 <span data-ttu-id="84b7a-111">选择在目标服务器上已存在同名的错误消息时，该任务是应该覆盖现有的用户定义错误消息还是跳过现有消息，或是失败。</span><span class="sxs-lookup"><span data-stu-id="84b7a-111">Select whether the task should overwrite existing user-defined error messages, skip existing messages, or fail if error messages of the same name already exist on the destination server.</span></span>  
  
 <span data-ttu-id="84b7a-112">**TransferAllErrorMessages**</span><span class="sxs-lookup"><span data-stu-id="84b7a-112">**TransferAllErrorMessages**</span></span>  
 <span data-ttu-id="84b7a-113">选择该任务应将全部用户定义消息还是只有指定的用户定义消息从源服务器复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="84b7a-113">Select whether the task should copy all or only the specified user-defined messages from the source server to the destination server.</span></span>  
  
 <span data-ttu-id="84b7a-114">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="84b7a-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="84b7a-115">值</span><span class="sxs-lookup"><span data-stu-id="84b7a-115">Value</span></span>|<span data-ttu-id="84b7a-116">说明</span><span class="sxs-lookup"><span data-stu-id="84b7a-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84b7a-117">**True**</span><span class="sxs-lookup"><span data-stu-id="84b7a-117">**True**</span></span>|<span data-ttu-id="84b7a-118">复制所有用户定义消息。</span><span class="sxs-lookup"><span data-stu-id="84b7a-118">Copy all user-defined messages.</span></span>|  
|<span data-ttu-id="84b7a-119">**False**</span><span class="sxs-lookup"><span data-stu-id="84b7a-119">**False**</span></span>|<span data-ttu-id="84b7a-120">仅复制指定的用户定义消息。</span><span class="sxs-lookup"><span data-stu-id="84b7a-120">Copy only the specified user-defined messages.</span></span>|  
  
 <span data-ttu-id="84b7a-121">**ErrorMessagesList**</span><span class="sxs-lookup"><span data-stu-id="84b7a-121">**ErrorMessagesList**</span></span>  
 <span data-ttu-id="84b7a-122">单击浏览按钮 (...) 以选择要复制的错误消息  。</span><span class="sxs-lookup"><span data-stu-id="84b7a-122">Click the browse button **(...)** to select the error messages to copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b7a-123">必须先指定 **SourceConnection** ，然后才能选择要复制的错误消息。</span><span class="sxs-lookup"><span data-stu-id="84b7a-123">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
 <span data-ttu-id="84b7a-124">**ErrorMessageLanguagesList**</span><span class="sxs-lookup"><span data-stu-id="84b7a-124">**ErrorMessageLanguagesList**</span></span>  
 <span data-ttu-id="84b7a-125">单击浏览按钮 (...) 以选择将用户定义的错误消息发送到目标服务器所使用的语言  。</span><span class="sxs-lookup"><span data-stu-id="84b7a-125">Click the browse button **(...)** to select the languages for which to copy user-defined error messages to the destination server.</span></span> <span data-ttu-id="84b7a-126">在目标服务器上必须存在 us_english（代码页 1033）版本的消息，才能将其他语言版本的消息传输到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="84b7a-126">A us_english (code page 1033) version of the message must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b7a-127">必须先指定 **SourceConnection** ，然后才能选择要复制的错误消息。</span><span class="sxs-lookup"><span data-stu-id="84b7a-127">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b7a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84b7a-128">See Also</span></span>  
 <span data-ttu-id="84b7a-129">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="84b7a-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="84b7a-130">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="84b7a-130">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="84b7a-131">[传输错误消息任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="84b7a-131">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="84b7a-132">[SMO 连接管理器](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="84b7a-132">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="84b7a-133">[传输错误消息任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="84b7a-133">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="84b7a-134">SMO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="84b7a-134">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
