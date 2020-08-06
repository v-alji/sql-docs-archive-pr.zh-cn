---
title: 异常消息框编程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2425169f838199ce24b4331dd57c74b480adf62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694106"
---
# <a name="exception-message-box-programming"></a><span data-ttu-id="7b947-102">异常消息框编程</span><span class="sxs-lookup"><span data-stu-id="7b947-102">Exception Message Box Programming</span></span>
  <span data-ttu-id="7b947-103">异常消息框是使用安装并由图形组件使用的编程接口 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b947-103">The exception message box is a programmatic interface that is installed with and used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] graphical components.</span></span> <span data-ttu-id="7b947-104">异常消息框是支持的托管程序集，您可以将其用于应用程序中，以显著提高对消息传送的控制，并使用户可以选择保存错误消息内容，以供将来参考和从中获取有关消息的帮助。</span><span class="sxs-lookup"><span data-stu-id="7b947-104">The exception message box is a supported managed assembly that you can use in your applications to provide significantly more control over the messaging experience and to give your users the options to save error message content for later reference and to get help on messages.</span></span> <span data-ttu-id="7b947-105">由于异常消息框可由除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之外的所有 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 版本安装，因此在安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端组件的任何计算机上，无需额外配置即可使用该接口。</span><span class="sxs-lookup"><span data-stu-id="7b947-105">Because the exception message box is installed by all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssEW](../../includes/ssew-md.md)], you can use it with no additional configuration on any computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client components have been installed.</span></span>  
  
 <span data-ttu-id="7b947-106"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 命名空间中的 <xref:Microsoft.SqlServer.MessageBox> 类除具有 <xref:System.Windows.Forms.MessageBox> 类的所有功能外，还具有一些其他功能。</span><span class="sxs-lookup"><span data-stu-id="7b947-106">The <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in the <xref:Microsoft.SqlServer.MessageBox> namespace has all the functionality of the <xref:System.Windows.Forms.MessageBox> class and more.</span></span> <span data-ttu-id="7b947-107">对于可能使用 <xref:System.Windows.Forms.MessageBox> 的任何任务，<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 均为理想之选，专用于很好地处理托管代码异常。</span><span class="sxs-lookup"><span data-stu-id="7b947-107">Ideal for any tasks for which <xref:System.Windows.Forms.MessageBox> may be used, <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> is designed to elegantly handle managed code exceptions.</span></span> <span data-ttu-id="7b947-108">通过异常消息框，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7b947-108">The exception message box allows you to do the following:</span></span>  
  
-   <span data-ttu-id="7b947-109">为多达五个按钮提供自定义按钮文本。</span><span class="sxs-lookup"><span data-stu-id="7b947-109">Provide customized button text for up to five buttons.</span></span> <span data-ttu-id="7b947-110">针对不同文本长度自动调整按钮和对话框的大小。</span><span class="sxs-lookup"><span data-stu-id="7b947-110">Buttons and the dialog box resize automatically for different text lengths.</span></span>  
  
-   <span data-ttu-id="7b947-111">允许用户将消息标题、文本、按钮文本和帮助链接（如果有）轻松复制到剪贴板上，或在电子邮件正文中轻松发送这些信息。</span><span class="sxs-lookup"><span data-stu-id="7b947-111">Allow users to easily copy the message title, text, button text, and help links (if any) to the Clipboard or send this information in an e-mail message.</span></span>  
  
-   <span data-ttu-id="7b947-112">当用户单击**其他信息**时，显示层次结构关系树中的所有基本异常和错误。</span><span class="sxs-lookup"><span data-stu-id="7b947-112">Display all underlying exceptions and errors in a hierarchical relationship tree when users click **Additional Information**.</span></span>  
  
-   <span data-ttu-id="7b947-113">允许用户决定当再次发生同一个异常时是否显示消息。</span><span class="sxs-lookup"><span data-stu-id="7b947-113">Allow users to decide whether to display the message when the same exception occurs again.</span></span>  
  
-   <span data-ttu-id="7b947-114">使用与异常关联的帮助链接访问联机帮助系统。</span><span class="sxs-lookup"><span data-stu-id="7b947-114">Access an online help system by using a help link associated with the exception.</span></span>  
  
 <span data-ttu-id="7b947-115">有关详细信息，请参阅[Program Exception Message Box](../../../2014/database-engine/dev-guide/program-exception-message-box.md)。</span><span class="sxs-lookup"><span data-stu-id="7b947-115">For more information, see [Program Exception Message Box](../../../2014/database-engine/dev-guide/program-exception-message-box.md).</span></span>  
  
  
