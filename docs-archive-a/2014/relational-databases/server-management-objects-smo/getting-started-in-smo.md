---
title: 在 SMO 中入门 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, about SQL Server Management Objects
- SMO [SQL Server], about SQL Server Management Objects
ms.assetid: ecc62702-c0d5-4180-b3c2-16ec5030caa7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d90911932b5f9bfc91368e70e66d2b227a3964f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588465"
---
# <a name="getting-started-in-smo"></a><span data-ttu-id="a4a2a-102">SMO 入门</span><span class="sxs-lookup"><span data-stu-id="a4a2a-102">Getting Started in SMO</span></span>
  <span data-ttu-id="a4a2a-103">本主题包含有关使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象 (SMO) 的入门信息。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-103">This topic contains information about getting started using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="a4a2a-104">SMO 一节面向开发人员。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-104">The SMO section is aimed at developers.</span></span> <span data-ttu-id="a4a2a-105">下面的列表将帮助您找到以下相关信息：SMO 对象层次结构、如何使用 SMO 准备编写程序、如何使用不同的编程语言开始编写 SMO 程序，以及常规和特定的编程任务。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-105">The following list will help you to locate information about the SMO object hierarchy, how to prepare for writing programs in SMO, how to start writing an SMO program in different programming languages, and general and specific programming tasks.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4a2a-106">**SMO 的准备工作**</span><span class="sxs-lookup"><span data-stu-id="a4a2a-106">**Preparing for SMO**</span></span><br /><br /> <span data-ttu-id="a4a2a-107">-   [针对 SMO 的准备](../../database-engine/dev-guide/preparing-to-use-smo.md)通过 sql-dmo 提供有关系统要求、安装和比较的信息。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-107">-   [Preparing for SMO](../../database-engine/dev-guide/preparing-to-use-smo.md) provides information about system requirements, installation, and comparisons with SQL-DMO.</span></span><br /><br /> <span data-ttu-id="a4a2a-108">**对象模型**</span><span class="sxs-lookup"><span data-stu-id="a4a2a-108">**Object Model**</span></span><br /><br /> <span data-ttu-id="a4a2a-109">-[对象模型](smo-object-model.md)描述 SMO 对象层次结构以及对象之间的相互关系。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-109">-   The [Object Model](smo-object-model.md) describes the SMO object hierarchy and how the objects relate to one another.</span></span><br /><br /> <span data-ttu-id="a4a2a-110">**编程语言**</span><span class="sxs-lookup"><span data-stu-id="a4a2a-110">**Programming Languages**</span></span><br /><br /> <span data-ttu-id="a4a2a-111">-   [编程语言](smo-programming-languages.md)介绍编程环境，并包括使用 c # 和 Visual Basic 开始编写 SMO 程序的详细过程。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-111">-   [Programming Languages](smo-programming-languages.md) describes the programming environment and includes detailed procedures to start writing an SMO program in C# and Visual Basic.</span></span>|<span data-ttu-id="a4a2a-112">**使用 SMO 进行常规编程**</span><span class="sxs-lookup"><span data-stu-id="a4a2a-112">**General Programming in SMO**</span></span><br /><br /> <span data-ttu-id="a4a2a-113">-   [Smo 中的常规编程](create-program/creating-smo-programs.md)是使用 smo 编程的简介。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-113">-   [General Programming in SMO](create-program/creating-smo-programs.md) is an introduction to programming with SMO.</span></span> <span data-ttu-id="a4a2a-114">本主题说明如何连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，以及如何使用属性、方法和集合。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-114">This topic describes how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and how to use properties, methods, and collections.</span></span> <span data-ttu-id="a4a2a-115">更高级的主题说明数据类型、事务、设置捕获模式以及事件和异常处理。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-115">More advanced topics describe data types, transactions, setting the capture mode, and event and exception handling.</span></span><br /><br /> <span data-ttu-id="a4a2a-116">**编程特定的任务**</span><span class="sxs-lookup"><span data-stu-id="a4a2a-116">**Programming Specific Tasks**</span></span><br /><br /> <span data-ttu-id="a4a2a-117">-[特定于编程的任务](tasks/programming-specific-tasks.md)部分包含有关如何使用 SMO 来编程特定任务的概念和过程。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-117">-   The [Programming Specific Tasks](tasks/programming-specific-tasks.md) section contains concepts and procedures about how to program specific tasks by using SMO.</span></span> <span data-ttu-id="a4a2a-118">该主题还描述对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的完整编程管理。</span><span class="sxs-lookup"><span data-stu-id="a4a2a-118">The topic also describes complete programmatic management of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
