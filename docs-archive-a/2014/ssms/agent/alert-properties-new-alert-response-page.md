---
title: 警报属性-新建警报 (响应页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34e7f11ff3210ec4fc1835751bc35b140d3fa0ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692109"
---
# <a name="alert-properties-new-alert-response-page"></a><span data-ttu-id="7c0ad-102">警报属性-新建警报 (响应 "页面) </span><span class="sxs-lookup"><span data-stu-id="7c0ad-102">Alert Properties-New Alert (Response Page)</span></span>
  <span data-ttu-id="7c0ad-103">使用此页可以指定要运行的作业，并获取为响应代理警报而通知的操作员列表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-103">Use this page to specify a job that you want to run and to obtain a list of operators to be notified in response to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7c0ad-104">选项</span><span class="sxs-lookup"><span data-stu-id="7c0ad-104">Options</span></span>  
 <span data-ttu-id="7c0ad-105">**执行作业**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-105">**Execute job**</span></span>  
 <span data-ttu-id="7c0ad-106">启用“作业列表”\*\*\*\*、“新建作业”\*\*\*\* 和“查看作业”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-106">Enables the **Job list**, **New job** and **View job** options.</span></span>  
  
 <span data-ttu-id="7c0ad-107">**新建作业**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-107">**New job**</span></span>  
 <span data-ttu-id="7c0ad-108">打开“新建作业”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-108">Open the **New Job** dialog box.</span></span> <span data-ttu-id="7c0ad-109">此按钮在“执行作业”\*\*\*\* 处于未选中状态时不可用。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-109">This button is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="7c0ad-110">**查看作业**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-110">**View job**</span></span>  
 <span data-ttu-id="7c0ad-111">查看或修改所选作业。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-111">View or modify the selected job.</span></span> <span data-ttu-id="7c0ad-112">此选项在“执行作业”\*\*\*\* 处于未选中状态时不可用。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-112">This option is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="7c0ad-113">**通知操作员**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-113">**Notify operators**</span></span>  
 <span data-ttu-id="7c0ad-114">启用可用来添加、删除或更改操作员的控件。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-114">Enables the controls that allow you to add, remove, or change operators.</span></span>  
  
 <span data-ttu-id="7c0ad-115">**操作员列表**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-115">**Operator list**</span></span>  
 <span data-ttu-id="7c0ad-116">列出在发生警报时要获得通知的操作员。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-116">Lists the operators to notify when an alert occurs.</span></span> <span data-ttu-id="7c0ad-117">若要指定通知方法，请选中显示在操作员姓名后面的“电子邮件”\*\*\*\*、“寻呼程序”\*\*\*\* 或“Net send”\*\*\*\* 复选框。此选项在“通知操作员”\*\*\*\* 处于未选中状态时不可用。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-117">To specify a notification method, select the **E-mail**, **Pager**, or **Net send** check box that is displayed after the operator name.This option not available when **Notify operators** is not selected.</span></span>  
  
 <span data-ttu-id="7c0ad-118">**电子邮件**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-118">**E-mail**</span></span>  
 <span data-ttu-id="7c0ad-119">使用电子邮件通知操作员。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-119">Use e-mail to notify the operator.</span></span>  
  
 <span data-ttu-id="7c0ad-120">**寻呼程序**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-120">**Pager**</span></span>  
 <span data-ttu-id="7c0ad-121">使用寻呼电子邮件地址通知操作员。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-121">Use the pager e-mail address to notify the operator.</span></span>  
  
 <span data-ttu-id="7c0ad-122">**Net send**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-122">**Net send**</span></span>  
 <span data-ttu-id="7c0ad-123">使用 **net send** 通知操作员。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-123">Use **net send** to notify the operator.</span></span>  
  
 <span data-ttu-id="7c0ad-124">**New 运算符**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-124">**New operator**</span></span>  
 <span data-ttu-id="7c0ad-125">显示可用于创建新操作员的“新建操作员”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-125">Displays the **New Operator** dialog box, which you can use to create a new operator.</span></span>  
  
 <span data-ttu-id="7c0ad-126">**查看操作员**</span><span class="sxs-lookup"><span data-stu-id="7c0ad-126">**View operator**</span></span>  
 <span data-ttu-id="7c0ad-127">显示当前所选操作员的“属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-127">Displays the **Properties** dialog box for the currently selected operator.</span></span> <span data-ttu-id="7c0ad-128">可以在“操作员属性”对话框上查看和修改操作员属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c0ad-128">You can view and modified operator properties on the **Operator Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c0ad-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c0ad-129">See Also</span></span>  
 <span data-ttu-id="7c0ad-130">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="7c0ad-130">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="7c0ad-131">[使用严重级别创建警报](create-an-alert-using-severity-level.md) </span><span class="sxs-lookup"><span data-stu-id="7c0ad-131">[Create an Alert Using Severity Level](create-an-alert-using-severity-level.md) </span></span>  
 <span data-ttu-id="7c0ad-132">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="7c0ad-132">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="7c0ad-133">[编辑警报](edit-an-alert.md) </span><span class="sxs-lookup"><span data-stu-id="7c0ad-133">[Edit an Alert](edit-an-alert.md) </span></span>  
 [<span data-ttu-id="7c0ad-134">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="7c0ad-134">Delete an Alert</span></span>](delete-an-alert.md)  
  
  
