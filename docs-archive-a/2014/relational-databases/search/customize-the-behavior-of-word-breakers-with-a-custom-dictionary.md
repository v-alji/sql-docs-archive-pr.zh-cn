---
title: 使用自定义字典自定义断字符的行为 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fb02a47da20134925d9b2486ea0c08091af4aa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689840"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a><span data-ttu-id="22cd7-102">使用自定义词典自定义断字符的行为</span><span class="sxs-lookup"><span data-stu-id="22cd7-102">Customize the Behavior of Word Breakers with a Custom Dictionary</span></span>
  <span data-ttu-id="22cd7-103">您可以通过创建特定于语言的自定义字典文件，为特定的语言自定义断字符的行为。</span><span class="sxs-lookup"><span data-stu-id="22cd7-103">You can customize the behavior of the word breaker for a particular language by creating a language-specific custom dictionary file.</span></span> <span data-ttu-id="22cd7-104">例如，您可以禁止断字符断开某些字词或模式。</span><span class="sxs-lookup"><span data-stu-id="22cd7-104">For example, you can prevent the word breaker from breaking certain terms or patterns.</span></span>  
  
 <span data-ttu-id="22cd7-105">有关详细信息，请参阅下列 SharePoint 文章：</span><span class="sxs-lookup"><span data-stu-id="22cd7-105">For more information, see the following SharePoint article:</span></span>  
  
 [<span data-ttu-id="22cd7-106">创建自定义字典 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="22cd7-106">Create a custom dictionary (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 <span data-ttu-id="22cd7-107">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请将自定义字典文件放置于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="22cd7-107">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], place custom dictionary files in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 <span data-ttu-id="22cd7-108">在创建或更改自定义字典文件后，使用以下命令重新启动 SQL 全文筛选器后台程序启动器：</span><span class="sxs-lookup"><span data-stu-id="22cd7-108">After creating or changing custom dictionary files, restart the SQL Full-text Daemon Launcher with the following command:</span></span>  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
