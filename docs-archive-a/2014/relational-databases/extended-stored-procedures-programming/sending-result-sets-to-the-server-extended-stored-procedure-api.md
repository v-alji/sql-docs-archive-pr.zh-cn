---
title: 将结果集发送到服务器 (扩展存储过程 API) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576766"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a><span data-ttu-id="9dd0c-102">将结果集发送到服务器（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="9dd0c-102">Sending Result Sets to the Server (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="9dd0c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="9dd0c-104">将结果集发送到时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，扩展存储过程应调用相应的 API，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9dd0c-104">When sending a result set to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the extended stored procedure should call the appropriate API as follows:</span></span>  
  
-   <span data-ttu-id="9dd0c-105">**Srv_sendmsg**函数可以在所有行之前或之后以任意顺序调用， (如果已使用**srv_sendrow**发送了任何) 。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-105">The **srv_sendmsg** function may be called in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="9dd0c-106">在向客户端发送完成状态之前，必须将所有消息发送到客户端**srv_senddone**。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-106">All messages must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="9dd0c-107">对于发送到客户端的每行调用一次 srv_sendrow 函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-107">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="9dd0c-108">必须先将所有行发送到客户端，然后才能将任何消息、状态值或完成状态与**srv_sendmsg**、 **srv_pfield**的**srv_status**参数或**srv_senddone**一起发送。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-108">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, the **srv_status** argument of **srv_pfield**, or **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="9dd0c-109">如果发送的行尚未使用**srv_describe**定义其所有列，则会导致应用程序引发信息性错误消息并向客户端返回失败消息。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-109">Sending a row that has not had all its columns defined with **srv_describe** causes the application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="9dd0c-110">在此情况下，将不发送该行。</span><span class="sxs-lookup"><span data-stu-id="9dd0c-110">In this case, the row is not sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd0c-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9dd0c-111">See Also</span></span>  
 [<span data-ttu-id="9dd0c-112">创建扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="9dd0c-112">Creating Extended Stored Procedures</span></span>](creating-extended-stored-procedures.md)  
  
  
