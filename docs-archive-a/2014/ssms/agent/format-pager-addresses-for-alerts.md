---
title: 设置警报的寻呼地址的格式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471f9a4958f51491b312d89239a2204c907e25e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577206"
---
# <a name="format-pager-addresses-for-alerts"></a><span data-ttu-id="0bc03-102">Format Pager Addresses for Alerts</span><span class="sxs-lookup"><span data-stu-id="0bc03-102">Format Pager Addresses for Alerts</span></span>
  <span data-ttu-id="0bc03-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中设置代理警报的寻呼地址的格式 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0bc03-103">This topic describes how to format pager addresses for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0bc03-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0bc03-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0bc03-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0bc03-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0bc03-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0bc03-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0bc03-107">**若要设置寻呼地址的格式，可使用：**</span><span class="sxs-lookup"><span data-stu-id="0bc03-107">**To format pager addresses, using:**</span></span>  
  
     [<span data-ttu-id="0bc03-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0bc03-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0bc03-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="0bc03-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0bc03-110">Security</span><span class="sxs-lookup"><span data-stu-id="0bc03-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0bc03-111">权限</span><span class="sxs-lookup"><span data-stu-id="0bc03-111">Permissions</span></span>  
 <span data-ttu-id="0bc03-112">默认情况下，只有 **sysadmin** 固定服务器角色的成员才能查看有关警报的信息。</span><span class="sxs-lookup"><span data-stu-id="0bc03-112">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="0bc03-113">其他用户必须被授予 **msdb** 数据库中的 **SQLAgentOperatorRole** 固定数据库角色的权限。</span><span class="sxs-lookup"><span data-stu-id="0bc03-113">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0bc03-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0bc03-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-format-pager-addresses"></a><span data-ttu-id="0bc03-115">设置寻呼地址格式</span><span class="sxs-lookup"><span data-stu-id="0bc03-115">To format pager addresses</span></span>  
  
1.  <span data-ttu-id="0bc03-116">在 **“对象资源管理器”** 中，单击加号以展开包含要发送到寻呼程序的警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="0bc03-116">In **Object Explorer**, click the plus sign to expand the server that contains the alert that you want to send to a pager.</span></span>  
  
2.  <span data-ttu-id="0bc03-117">右键单击**SQL Server 代理**，然后选择 "**属性**"</span><span class="sxs-lookup"><span data-stu-id="0bc03-117">Right-click **SQL Server Agent** and select **Properties**</span></span>  
  
3.  <span data-ttu-id="0bc03-118">在 **“选择页”** 下，选择 **“警报系统”**。</span><span class="sxs-lookup"><span data-stu-id="0bc03-118">Under **Select a page**, select **Alert System**.</span></span>  
  
4.  <span data-ttu-id="0bc03-119">在“寻呼电子邮件的地址格式”\*\*\*\* 字段的“收件人行”\*\*\*\* 和“抄送行”\*\*\*\* 框中，输入寻呼地址的前缀或后缀。</span><span class="sxs-lookup"><span data-stu-id="0bc03-119">In the **To line** and **CC line** boxes of the **Address formatting for pager e-mails** field, enter the pager address prefix or suffix.</span></span> <span data-ttu-id="0bc03-120">发送通知时，将插入操作员的实际寻呼地址。</span><span class="sxs-lookup"><span data-stu-id="0bc03-120">The operator's actual pager address is inserted when a notification is sent.</span></span>  
  
5.  <span data-ttu-id="0bc03-121">在 **“主题”** 框中，输入主题行的前缀或后缀。</span><span class="sxs-lookup"><span data-stu-id="0bc03-121">In the **Subject** box, enter the subject line prefix or suffix.</span></span>  
  
6.  <span data-ttu-id="0bc03-122">选择“在通知页中包含电子邮件的正文部分”\*\*\*\* 复选框，以便在寻呼消息中包含完整电子邮件（与仅包含主题行相对）。</span><span class="sxs-lookup"><span data-stu-id="0bc03-122">Select the **Include body of e-mail in notification page** check box to include the full e-mail message with the pager message (as opposed to the subject line only).</span></span>  
  
7.  <span data-ttu-id="0bc03-123">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0bc03-123">When finished, click **OK**.</span></span>  
  
  
