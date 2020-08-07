---
title: 设置工具选项和布局 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96d853a85b8ee4d451c55d7ea59af3755887be22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690967"
---
# <a name="setting-tool-options-and-layout"></a><span data-ttu-id="7b0a1-102">设置工具选项和布局</span><span class="sxs-lookup"><span data-stu-id="7b0a1-102">Setting Tool Options and Layout</span></span>
  <span data-ttu-id="7b0a1-103">您可以设置用于配置数据库引擎优化顾问图形用户界面 (GUI) 在启动时的显示内容、使用的字体以及其他工具功能的选项，从而为您的使用方式提供最佳支持。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-103">You can set options that configure what the Database Engine Tuning Advisor graphical user interface (GUI) displays on startup, the font it uses, and other tool functionality to best support how you use it.</span></span> <span data-ttu-id="7b0a1-104">通过本页的练习将让您熟悉可设置的各选项及其设置方式。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-104">The practices on this page familiarize you with the options you can set, and how to set them.</span></span>  
  
### <a name="set-the-tool-options"></a><span data-ttu-id="7b0a1-105">设置工具选项</span><span class="sxs-lookup"><span data-stu-id="7b0a1-105">Set the tool options</span></span>  
  
1.  <span data-ttu-id="7b0a1-106">启动数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-106">Start the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="7b0a1-107">在 Windows“开始”\*\*\*\* 菜单中，依次指向“所有程序”\*\*\*\*、[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] 和“性能工具”\*\*\*\*，然后单击“数据库引擎优化顾问”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-107">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="7b0a1-108">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-108">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="7b0a1-109">在“选项”\*\*\*\* 对话框中，查看下列选项：</span><span class="sxs-lookup"><span data-stu-id="7b0a1-109">In the **Options** dialog box, view the following options:</span></span>  
  
    -   <span data-ttu-id="7b0a1-110">展开“启动时”\*\*\*\* 列表，查看数据库引擎优化顾问在启动时可显示的内容。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-110">Expand the **On startup** list to view what Database Engine Tuning Advisor can display when it is started.</span></span> <span data-ttu-id="7b0a1-111">默认情况下，选择“显示新会话”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-111">By default, **Show a new session** is selected.</span></span>  
  
    -   <span data-ttu-id="7b0a1-112">单击 "**更改字体**"，查看在 "**常规**" 选项卡上可以为数据库和表的列表选择的字体。在执行优化后，为此选项选择的字体也将用于数据库引擎优化顾问建议网格和报告。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-112">Click **Change Font** to see what fonts you can choose for the lists of databases and tables on the **General** tab. The fonts you choose for this option also are used in Database Engine Tuning Advisor recommendation grids and reports after you have performed tuning.</span></span> <span data-ttu-id="7b0a1-113">默认情况下，数据库引擎优化顾问使用系统字体。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-113">By default, Database Engine Tuning Advisor uses system fonts.</span></span>  
  
    -   <span data-ttu-id="7b0a1-114">“最近使用的列表中的项数”\*\*\*\* 可设置为 **1** 到 **10** 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-114">The **Number of items in most recently used lists** can be set between **1** and **10**.</span></span> <span data-ttu-id="7b0a1-115">此选项设置在单击“文件”\*\*\*\* 菜单上的“最近使用的会话”\*\*\*\* 或“最近使用的文件”\*\*\*\* 时，列表中可以显示的最大项数。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-115">This sets the maximum number of items in the lists displayed by clicking **Recent Sessions** or **Recent Files** on the **File** menu.</span></span> <span data-ttu-id="7b0a1-116">默认情况下，此选项设置为 **4**。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-116">By default, this option is set to **4**.</span></span>  
  
    -   <span data-ttu-id="7b0a1-117">选中“记住我上次的优化选项”\*\*\*\* 时，默认情况下，数据库引擎优化顾问会将为上一优化会话指定的优化选项用于下一优化会话中。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-117">When **Remember my last tuning options** is checked, by default Database Engine Tuning Advisor uses the tuning options you specified for your last tuning session for the next tuning session.</span></span> <span data-ttu-id="7b0a1-118">清除此复选框，以便使用数据库引擎优化顾问优化选项的默认设置。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-118">Clear this check box to use Database Engine Tuning Advisor tuning option defaults.</span></span> <span data-ttu-id="7b0a1-119">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-119">By default, this option is selected.</span></span>  
  
    -   <span data-ttu-id="7b0a1-120">默认情况下，将选中“在永久删除会话之前询问”\*\*\*\*，避免意外删除优化会话。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-120">By default, **Ask before permanently deleting sessions** is checked to avoid accidentally deleting tuning sessions.</span></span>  
  
    -   <span data-ttu-id="7b0a1-121">默认情况下，将选中“在停止会话分析之前询问”\*\*\*\*，避免在数据库引擎优化顾问完成工作负载分析之前意外停止优化会话。</span><span class="sxs-lookup"><span data-stu-id="7b0a1-121">By default, **Ask before stopping session analysis** is checked to avoid accidentally stopping a tuning session before Database Engine Tuning Advisor has finished analyzing a workload.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="7b0a1-122">下一课</span><span class="sxs-lookup"><span data-stu-id="7b0a1-122">Next Lesson</span></span>  
 [<span data-ttu-id="7b0a1-123">第 2 课：使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="7b0a1-123">Lesson 2: Using Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
