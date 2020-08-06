---
title: 验证多个订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a61e8b5417bf8312998b5051c47545b705b44c00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576623"
---
# <a name="validate-subscriptions"></a><span data-ttu-id="fba60-102">验证多个订阅</span><span class="sxs-lookup"><span data-stu-id="fba60-102">Validate Subscriptions</span></span>
  <span data-ttu-id="fba60-103">可以使用 **“验证多个订阅”** 对话框，指定在下次运行各个订阅的分发代理时应验证对事务发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="fba60-103">Use the **Validate Subscriptions** dialog box to specify that subscriptions to a transactional publication should be validated the next time the Distribution Agent for each subscription runs.</span></span> <span data-ttu-id="fba60-104">验证的结果显示在复制监视器中。</span><span class="sxs-lookup"><span data-stu-id="fba60-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="fba60-105">有关详细信息，请参阅 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="fba60-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fba60-106">选项</span><span class="sxs-lookup"><span data-stu-id="fba60-106">Options</span></span>  
 <span data-ttu-id="fba60-107">**验证所有 SQL Server 订阅**</span><span class="sxs-lookup"><span data-stu-id="fba60-107">**Validate all SQL Server subscriptions**</span></span>  
 <span data-ttu-id="fba60-108">选择此选项将验证此发布的所有 SQL Server 订阅的数据。</span><span class="sxs-lookup"><span data-stu-id="fba60-108">Select to validate data for all SQL Server subscriptions to this publication.</span></span>  
  
 <span data-ttu-id="fba60-109">**验证下列订阅**</span><span class="sxs-lookup"><span data-stu-id="fba60-109">**Validate the following subscriptions**</span></span>  
 <span data-ttu-id="fba60-110">如果不希望验证所有订阅，请选中该选项。</span><span class="sxs-lookup"><span data-stu-id="fba60-110">Select if you do not want to validate all subscriptions.</span></span> <span data-ttu-id="fba60-111">从列表中选择要验证的订阅。</span><span class="sxs-lookup"><span data-stu-id="fba60-111">Select from the list the subscriptions you want to validate.</span></span>  
  
 <span data-ttu-id="fba60-112">**验证选项**</span><span class="sxs-lookup"><span data-stu-id="fba60-112">**Validation Options**</span></span>  
 <span data-ttu-id="fba60-113">单击此项可访问 **“订阅验证选项”** 对话框，使用此对话框可以指定是使用行计数验证还是使用二进制校验和验证。</span><span class="sxs-lookup"><span data-stu-id="fba60-113">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba60-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fba60-114">See Also</span></span>  
 [<span data-ttu-id="fba60-115">验证已复制的数据</span><span class="sxs-lookup"><span data-stu-id="fba60-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
