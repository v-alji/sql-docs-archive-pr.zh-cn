---
title: 维护计划（“报告和记录”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580721"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a><span data-ttu-id="f43fa-102">维护计划（“报告和记录”页）</span><span class="sxs-lookup"><span data-stu-id="f43fa-102">Maintenance Plan (Reporting and Logging Page)</span></span>
  <span data-ttu-id="f43fa-103">使用 **“报告和记录”** 对话框可以配置在执行维护计划时生成的报告和日志。</span><span class="sxs-lookup"><span data-stu-id="f43fa-103">Use the **Reporting and Logging** dialog box to configure the reports and logs that are generated when maintenance plans are executed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f43fa-104">选项</span><span class="sxs-lookup"><span data-stu-id="f43fa-104">Options</span></span>  
 <span data-ttu-id="f43fa-105">**生成文本文件报告**</span><span class="sxs-lookup"><span data-stu-id="f43fa-105">**Generate a text file report**</span></span>  
 <span data-ttu-id="f43fa-106">指定是否希望 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 写入文本文件报告。</span><span class="sxs-lookup"><span data-stu-id="f43fa-106">Specify if you want [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to write a text file report.</span></span>  
  
 <span data-ttu-id="f43fa-107">**创建新文件**</span><span class="sxs-lookup"><span data-stu-id="f43fa-107">**Create a new file**</span></span>  
 <span data-ttu-id="f43fa-108">在每次执行维护计划时创建新的报告文件。</span><span class="sxs-lookup"><span data-stu-id="f43fa-108">Create a new report file for each execution of the maintenance plan.</span></span> <span data-ttu-id="f43fa-109">默认情况下，报告文件写入到承载包含此维护计划的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的计算机，具体位置为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中建立的默认日志文件夹。</span><span class="sxs-lookup"><span data-stu-id="f43fa-109">By default, the report files are written to the computer hosting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains this maintenance plan, in the folder established as the default log folder during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="f43fa-110">若要指定其它文件夹，请在“文件夹”  文本框中输入该文件夹的完整路径，或单击“浏览”按钮 ( **...** ) 并导航到所需的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f43fa-110">To specify a different folder, enter the full path of the folder in the **Folder** text box, or click the browse button (**...**) and navigate to the desired folder.</span></span>  
  
 <span data-ttu-id="f43fa-111">**追加到文件**</span><span class="sxs-lookup"><span data-stu-id="f43fa-111">**Append to file**</span></span>  
 <span data-ttu-id="f43fa-112">将每次执行计划所生成的报告追加到在“文件名”  文本框中指定的文件。</span><span class="sxs-lookup"><span data-stu-id="f43fa-112">Append the report from each plan execution to the file specified in the **File name** text box.</span></span> <span data-ttu-id="f43fa-113">还可以通过单击浏览按钮并从对话框中选择文件来指定文件。</span><span class="sxs-lookup"><span data-stu-id="f43fa-113">You may also specify a file by clicking the browse button and selecting a file from the dialog box.</span></span>  
  
 <span data-ttu-id="f43fa-114">**将报告发送给电子邮件收件人**</span><span class="sxs-lookup"><span data-stu-id="f43fa-114">**Send report to an e-mail recipient**</span></span>  
 <span data-ttu-id="f43fa-115">通过电子邮件传输维护计划执行的结果。</span><span class="sxs-lookup"><span data-stu-id="f43fa-115">Transmit the outcome of a maintenance plan execution via e-mail.</span></span> <span data-ttu-id="f43fa-116">只有启用了数据库邮件并进行适当配置后，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="f43fa-116">This option is only available if Database Mail is enabled and properly configured.</span></span>  
  
 <span data-ttu-id="f43fa-117">**代理操作员**</span><span class="sxs-lookup"><span data-stu-id="f43fa-117">**Agent operator**</span></span>  
 <span data-ttu-id="f43fa-118">从电子邮件收件人列表中选择代理操作员。</span><span class="sxs-lookup"><span data-stu-id="f43fa-118">Select an agent operator from the list who will be the recipient of the e-mail.</span></span> <span data-ttu-id="f43fa-119">只有启用了邮件并进行了正确配置，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="f43fa-119">This option is only available if mail is enabled and properly</span></span>  
  
 <span data-ttu-id="f43fa-120">**记录扩展信息**</span><span class="sxs-lookup"><span data-stu-id="f43fa-120">**Log extended information**</span></span>  
 <span data-ttu-id="f43fa-121">在日志中包括详细信息。</span><span class="sxs-lookup"><span data-stu-id="f43fa-121">Include more information in the log.</span></span> <span data-ttu-id="f43fa-122">包括此选项将增大存储的维护计划历史记录的大小。</span><span class="sxs-lookup"><span data-stu-id="f43fa-122">Including this option will increase the size of the stored maintenance plan history.</span></span>  
  
 <span data-ttu-id="f43fa-123">**在远程服务器上进行日志记录**</span><span class="sxs-lookup"><span data-stu-id="f43fa-123">**Log to remote server**</span></span>  
 <span data-ttu-id="f43fa-124">将维护计划历史记录记录到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="f43fa-124">Logs maintenance plan history to a remote server.</span></span>  
  
 <span data-ttu-id="f43fa-125">**Connection**</span><span class="sxs-lookup"><span data-stu-id="f43fa-125">**Connection**</span></span>  
 <span data-ttu-id="f43fa-126">指定在远程服务器上进行日志记录时使用的连接信息。</span><span class="sxs-lookup"><span data-stu-id="f43fa-126">Specifies the connection information to use when logging to a remote server.</span></span>  
  
 <span data-ttu-id="f43fa-127">**新建**</span><span class="sxs-lookup"><span data-stu-id="f43fa-127">**New**</span></span>  
 <span data-ttu-id="f43fa-128">显示“连接属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="f43fa-128">Displays the **Connection Properties** dialog box.</span></span> <span data-ttu-id="f43fa-129">用于配置在远程服务器上进行日志记录时使用的新连接信息。</span><span class="sxs-lookup"><span data-stu-id="f43fa-129">Used to configure new connection information for logging to a remote server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43fa-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f43fa-130">See Also</span></span>  
 <span data-ttu-id="f43fa-131">[维护计划](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="f43fa-131">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="f43fa-132">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="f43fa-132">Database Mail</span></span>](../database-mail/database-mail.md)  
  
  
