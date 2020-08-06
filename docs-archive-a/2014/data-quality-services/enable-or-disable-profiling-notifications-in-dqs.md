---
title: 在 DQS 中启用或禁用事件探查通知 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b3b5e8cec1cac3eb1ce4357480c0f994a33d4c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689599"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a><span data-ttu-id="7162e-102">在 DQS 中启用或禁用事件探查通知</span><span class="sxs-lookup"><span data-stu-id="7162e-102">Enable or Disable Profiling Notifications in DQS</span></span>
  <span data-ttu-id="7162e-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中启用或禁用事件探查通知。</span><span class="sxs-lookup"><span data-stu-id="7162e-103">This topic describes how to enable or disable profiling notifications in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="7162e-104">默认情况下，在 DQS 中启用了事件探查通知。</span><span class="sxs-lookup"><span data-stu-id="7162e-104">By default, profiling notifications are enabled in DQS.</span></span> <span data-ttu-id="7162e-105">事件探查通知将指出有关数据源的重要事实以及对数据执行的当前活动的效用。</span><span class="sxs-lookup"><span data-stu-id="7162e-105">Profiling notifications tell you important facts about the data source and the effectiveness of the current activity performed on the data.</span></span> <span data-ttu-id="7162e-106">有关详细信息，请参阅 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="7162e-106">For more information, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7162e-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="7162e-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7162e-108">Security</span><span class="sxs-lookup"><span data-stu-id="7162e-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7162e-109">权限</span><span class="sxs-lookup"><span data-stu-id="7162e-109">Permissions</span></span>  
 <span data-ttu-id="7162e-110">您必须对 DQS_MAIN 数据库具有 dqs_administrator 角色才能启用通知。</span><span class="sxs-lookup"><span data-stu-id="7162e-110">You must have the dqs_administrator role on the DQS_MAIN database to enable notifications.</span></span>  
  
##  <a name="enable-or-disable-profiling-notifications"></a><a name="Enable"></a><span data-ttu-id="7162e-111">启用或禁用事件探查通知</span><span class="sxs-lookup"><span data-stu-id="7162e-111">Enable or Disable Profiling Notifications</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7162e-112">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7162e-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7162e-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="7162e-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="7162e-114">接下来，单击 **“常规设置”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7162e-114">Next, click the **General Settings** tab.</span></span>  
  
4.  <span data-ttu-id="7162e-115">取消选中或选中 **“启用通知”** 复选框，以便为 DQS 中的各种活动禁用或启用事件探查通知。</span><span class="sxs-lookup"><span data-stu-id="7162e-115">Clear or select the **Enable Notifications** check box to disable or enable profiling notifications for various activities in DQS.</span></span>  
  
5.  <span data-ttu-id="7162e-116">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="7162e-116">Click **Close**.</span></span>  
  
  
