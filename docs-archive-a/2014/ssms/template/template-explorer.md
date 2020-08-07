---
title: 模板资源管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.wb.templates.f1
- sql12.swb.templates.explorer.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7ee1e6261c759580df3a836f9cc4b500a77ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588208"
---
# <a name="template-explorer"></a><span data-ttu-id="4c9b7-102">Template Explorer</span><span class="sxs-lookup"><span data-stu-id="4c9b7-102">Template Explorer</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c9b7-103">提供了多种模板。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-103">provides a variety of templates.</span></span> <span data-ttu-id="4c9b7-104">模板即包含 SQL 脚本的样板文件，可用于在数据库中创建对象。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-104">Templates are boilerplate files containing SQL scripts that help you create objects in a database.</span></span> <span data-ttu-id="4c9b7-105">首次打开模板资源管理器时，会在 C:\Users 的用户文件夹中的 "AppData\Roaming\Microsoft\SQL Server Management Studio\120\templates 下" 下放置模板的副本。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-105">The first time the template explorer is opened, a copy of the templates are placed in the user's folder in C:\Users, under AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates.</span></span>  
  
 <span data-ttu-id="4c9b7-106">您可以在模板资源管理器中浏览可用模板，然后打开该模板以便将代码纳入代码编辑器窗口中。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-106">You can browse the available templates in Template Explorer, then open a template to incorporate the code into a code editor window.</span></span> <span data-ttu-id="4c9b7-107">也可以创建自定义模板。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-107">You can also create custom templates.</span></span>  
  
## <a name="benefits-of-templates"></a><span data-ttu-id="4c9b7-108">模板的优点</span><span class="sxs-lookup"><span data-stu-id="4c9b7-108">Benefits of Templates</span></span>  
 <span data-ttu-id="4c9b7-109">模板适用于解决方案、项目和各种类型的代码编辑器。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-109">Templates are available for solutions, projects, and various types of code editors.</span></span> <span data-ttu-id="4c9b7-110">模板可用于创建对象，如数据库、表、视图、索引、存储过程、触发器、统计信息和函数。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-110">Templates are available to create objects like databases, tables, views, indexes, stored procedures, triggers, statistics, and functions.</span></span> <span data-ttu-id="4c9b7-111">此外，通过创建用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的扩展属性、链接服务器、登录名、角色、用户和模板，有些模板还可以帮助您管理服务器。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-111">In addition, there are templates that help you to manage your server by creating extended properties, linked servers, logins, roles, users, and templates for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4c9b7-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供的模板脚本包含了可以帮助您自定义代码的参数。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-112">The template scripts provided with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain parameters to help you customize the code.</span></span> <span data-ttu-id="4c9b7-113">打开模板后，使用“替换模板参数”  对话框可以将值插入到脚本中。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-113">When you open a template, Use the **Replace Template Parameters** dialog box to insert values into the script.</span></span>  
  
 <span data-ttu-id="4c9b7-114">为频繁执行的任务创建自定义模板。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-114">Create custom templates for tasks you perform frequently.</span></span> <span data-ttu-id="4c9b7-115">将自定义脚本组织到现有文件夹中，或创建一个新的文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-115">Organize your custom scripts into the existing folders or create a new folder structure.</span></span>  
  
 <span data-ttu-id="4c9b7-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器还支持代码段，可通过在特定位置右键单击将代码段插入到脚本中的该位置。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query editor also supports code snippets, which can be inserted at specific locations in a script by right-clicking at that location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4c9b7-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4c9b7-117">Related Tasks</span></span>  
 <span data-ttu-id="4c9b7-118">参考以下主题可以开始使用模板。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-118">Use the following topics to get started with templates</span></span>  
  
|<span data-ttu-id="4c9b7-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="4c9b7-119">**Description**</span></span>|<span data-ttu-id="4c9b7-120">**主题**</span><span class="sxs-lookup"><span data-stu-id="4c9b7-120">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="4c9b7-121">介绍如何将模板中的代码合并到代码编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-121">Describes how to incorporate the code from a template into a code editor window.</span></span>|[<span data-ttu-id="4c9b7-122">打开模板</span><span class="sxs-lookup"><span data-stu-id="4c9b7-122">Open a Template</span></span>](open-a-template.md)|  
|<span data-ttu-id="4c9b7-123">介绍如何在代码编辑器中打开模板后替换模板参数值。</span><span class="sxs-lookup"><span data-stu-id="4c9b7-123">Describes how to replace template parameter values after opening a template in a code editor.</span></span>|[<span data-ttu-id="4c9b7-124">替换模板参数</span><span class="sxs-lookup"><span data-stu-id="4c9b7-124">Replace Template Parameters</span></span>](replace-template-parameters.md)|  
  
  
