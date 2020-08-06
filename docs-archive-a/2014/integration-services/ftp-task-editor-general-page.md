---
title: FTP 任务编辑器 ("常规" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cb4ffe2fa44e76890f6b70912f84dbcaa8f2cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579635"
---
# <a name="ftp-task-editor-general-page"></a><span data-ttu-id="09e02-102">FTP 任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="09e02-102">FTP Task Editor (General Page)</span></span>
  <span data-ttu-id="09e02-103">使用 **“FTP 任务编辑器”** 对话框的 **“常规”** 页可以指定连接到与任务通信的 FTP 服务器的 FTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="09e02-103">Use the **General** page of the **FTP Task Editor** dialog box to specify the FTP connection manager that connects to the FTP server that the task communicates with.</span></span> <span data-ttu-id="09e02-104">您还可以命名和描述 FTP 任务。</span><span class="sxs-lookup"><span data-stu-id="09e02-104">You can also name and describe the FTP task.</span></span>  
  
 <span data-ttu-id="09e02-105">若要了解此任务，请参阅 [FTP 任务](control-flow/ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="09e02-105">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="09e02-106">选项</span><span class="sxs-lookup"><span data-stu-id="09e02-106">Options</span></span>  
 <span data-ttu-id="09e02-107">**FtpConnection**</span><span class="sxs-lookup"><span data-stu-id="09e02-107">**FtpConnection**</span></span>  
 <span data-ttu-id="09e02-108">选择现有 FTP 连接管理器，或单击“\<**New connection...**>”以创建连接管理器。</span><span class="sxs-lookup"><span data-stu-id="09e02-108">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09e02-109">FTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="09e02-109">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="09e02-110">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="09e02-110">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="09e02-111">**相关主题**：[FTP 连接管理器](connection-manager/ftp-connection-manager.md)、[FTP 连接管理器编辑器](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="09e02-111">**Related Topics**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="09e02-112">**StopOnFailure**</span><span class="sxs-lookup"><span data-stu-id="09e02-112">**StopOnFailure**</span></span>  
 <span data-ttu-id="09e02-113">指示在 FTP 操作失败时是否终止 FTP 任务。</span><span class="sxs-lookup"><span data-stu-id="09e02-113">Indicate whether the FTP task terminates if an FTP operation fails.</span></span>  
  
 <span data-ttu-id="09e02-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="09e02-114">**Name**</span></span>  
 <span data-ttu-id="09e02-115">为 FTP 任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="09e02-115">Provide a unique name for the FTP task.</span></span> <span data-ttu-id="09e02-116">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="09e02-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09e02-117">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="09e02-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="09e02-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="09e02-118">**Description**</span></span>  
 <span data-ttu-id="09e02-119">键入对 FTP 任务的说明。</span><span class="sxs-lookup"><span data-stu-id="09e02-119">Type a description of the FTP task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e02-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09e02-120">See Also</span></span>  
 <span data-ttu-id="09e02-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="09e02-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="09e02-122">[FTP 任务编辑器 &#40;文件传输页面&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="09e02-122">[FTP Task Editor &#40;File Transfer Page&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span></span>  
 [<span data-ttu-id="09e02-123">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="09e02-123">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
