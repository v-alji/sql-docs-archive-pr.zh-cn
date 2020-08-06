---
title: 教程：数据库引擎入门 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorials [connecting]
- tutorials [Database Engine]
- unable to connect [SQL Server]
- failure to connect [SQL Server]
- connecting tutorial [SQL Server]
ms.assetid: 655e709b-346b-469c-bddc-a5a0238d07e0
author: rothja
ms.author: jroth
ms.openlocfilehash: aaa1fb21c026d064c2b14db73aadc2b82e9c15d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590609"
---
# <a name="tutorial-getting-started-with-the-database-engine"></a><span data-ttu-id="4f34e-102">教程：数据库引擎入门</span><span class="sxs-lookup"><span data-stu-id="4f34e-102">Tutorial: Getting Started with the Database Engine</span></span>
  <span data-ttu-id="4f34e-103">欢迎使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 教程入门。</span><span class="sxs-lookup"><span data-stu-id="4f34e-103">Welcome to the Getting Started with the [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorial.</span></span> <span data-ttu-id="4f34e-104">本教程适用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的新手且已安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]的用户。</span><span class="sxs-lookup"><span data-stu-id="4f34e-104">This tutorial is intended for users who are new to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and who have installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssExpress](../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="4f34e-105">本简明教程有助于您了解如何使用 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4f34e-105">This brief tutorial helps you get started using the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="4f34e-106">学习内容</span><span class="sxs-lookup"><span data-stu-id="4f34e-106">What You Will Learn</span></span>  
 <span data-ttu-id="4f34e-107">本教程介绍了如何使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 从本地计算机或另外一台计算机上连接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4f34e-107">This tutorial shows you how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on both the local computer and from another computer.</span></span>  
  
 <span data-ttu-id="4f34e-108">本教程分为两课：</span><span class="sxs-lookup"><span data-stu-id="4f34e-108">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="4f34e-109">第 1 课：连接到数据库引擎</span><span class="sxs-lookup"><span data-stu-id="4f34e-109">Lesson 1: Connecting to the Database Engine</span></span>](lesson-1-connecting-to-the-database-engine.md)  
 <span data-ttu-id="4f34e-110">在本课中，您将了解如何连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 以及如何允许其他人员进行连接。</span><span class="sxs-lookup"><span data-stu-id="4f34e-110">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] and enable additional people to connect.</span></span>  
  
 [<span data-ttu-id="4f34e-111">第 2 课：从其他计算机进行连接</span><span class="sxs-lookup"><span data-stu-id="4f34e-111">Lesson 2: Connecting from Another Computer</span></span>](lesson-2-connecting-from-another-computer.md)  
 <span data-ttu-id="4f34e-112">在本课中，您将了解如何从第二台计算机连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，包括启用协议、配置端口和配置防火墙设置。</span><span class="sxs-lookup"><span data-stu-id="4f34e-112">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] from a second computer, including enabling protocols, configuring ports, and configuring firewall settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f34e-113">要求</span><span class="sxs-lookup"><span data-stu-id="4f34e-113">Requirements</span></span>  
 <span data-ttu-id="4f34e-114">本教程不需要事先具备其他知识。</span><span class="sxs-lookup"><span data-stu-id="4f34e-114">This tutorial has no knowledge prerequisites.</span></span>  
  
 <span data-ttu-id="4f34e-115">若要使用本教程，您的系统必须安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="4f34e-115">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="4f34e-116">列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="4f34e-116">.</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]<span data-ttu-id="4f34e-117">可以通过运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装程序或者通过从[Microsoft 下载中心](https://go.microsoft.com/fwlink/?LinkId=144346)下载和安装来安装。</span><span class="sxs-lookup"><span data-stu-id="4f34e-117">can be installed by running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup or by downloading and installing from [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=144346).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f34e-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f34e-118">See Also</span></span>  
 [<span data-ttu-id="4f34e-119">教程：SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4f34e-119">Tutorial: SQL Server Management Studio</span></span>](../ssms/tutorials/tutorial-sql-server-management-studio.md)  
  
  
