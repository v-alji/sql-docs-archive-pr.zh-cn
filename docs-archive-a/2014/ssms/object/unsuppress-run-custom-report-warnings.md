---
title: 启用运行自定义报表警告 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
ms.openlocfilehash: 725362ff7f8a6c282529f652e8813a8083257eb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682638"
---
# <a name="unsuppress-run-custom-report-warnings"></a><span data-ttu-id="8d668-102">启用运行自定义报表警告</span><span class="sxs-lookup"><span data-stu-id="8d668-102">Unsuppress Run Custom Report Warnings</span></span>
  <span data-ttu-id="8d668-103">对于自定义报表，有两个警告对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-103">There are two warning dialog boxes for custom reports.</span></span> <span data-ttu-id="8d668-104">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中取消显示这些对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-104">This topic describes how to unsuppress the display of these boxes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8d668-105">默认情况下，在运行自定义报表之前会显示“运行自定义报表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-105">By default, the **Run Custom Reports** dialog box appears before a custom report runs.</span></span> <span data-ttu-id="8d668-106">如果选中“请不要再显示此警告”  复选框，将不再显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-106">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span> <span data-ttu-id="8d668-107">此外，在默认情况下，如果打开一个自定义报表然后单击链接打开另外一个自定义报表，则也将显示此“运行自定义报表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-107">Also by default, the **Run Custom Reports** dialog box appears when you open a custom report and then click a link to open another custom report.</span></span> <span data-ttu-id="8d668-108">此对话框显示钻取自定义报表文件的填写路径。</span><span class="sxs-lookup"><span data-stu-id="8d668-108">This dialog box displays the fill path to the drill-through custom report file.</span></span> <span data-ttu-id="8d668-109">如果选中“请不要再显示此警告”  复选框，将不再显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="8d668-109">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8d668-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8d668-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a><span data-ttu-id="8d668-111">启用主自定义报表警告对话框</span><span class="sxs-lookup"><span data-stu-id="8d668-111">To unsuppress the main custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="8d668-112">连接到 \<*Server*> \\ < *Share* >| \<*Drive*> \Documents and Settings \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml。</span><span class="sxs-lookup"><span data-stu-id="8d668-112">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="8d668-113">右键单击 `reports.xml` ，然后单击 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="8d668-113">Right-click `reports.xml`, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="8d668-114">将\*\* \<SuppressWarning> true \</SuppressWarning> 更改 \<SuppressWarning> 为 \</SuppressWarning> false\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d668-114">Change**\<SuppressWarning>true\</SuppressWarning> to \<SuppressWarning>false\</SuppressWarning>**.</span></span>  
  
4.  <span data-ttu-id="8d668-115">重新启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d668-115">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a><span data-ttu-id="8d668-116">启用钻取自定义报表警告对话框</span><span class="sxs-lookup"><span data-stu-id="8d668-116">To unsuppress the drill-through custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="8d668-117">连接到 \<*Server*> \\ < *Share* >| \<*Drive*> \Documents and Settings \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml。</span><span class="sxs-lookup"><span data-stu-id="8d668-117">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="8d668-118">右键单击 `reports.xml` ，然后单击 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="8d668-118">Right-click `reports.xml`, and click **Edit**.</span></span>  
  
3.  <span data-ttu-id="8d668-119">将\*\* \<SuppressDrillthroughWarning> true \</SuppressDrillthroughWarning> 更改 \<SuppressDrillthroughWarning> 为 \</SuppressDrillthroughWarning> false\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d668-119">Change **\<SuppressDrillthroughWarning>true\</SuppressDrillthroughWarning>to \<SuppressDrillthroughWarning>false\</SuppressDrillthroughWarning>**.</span></span>  
  
4.  <span data-ttu-id="8d668-120">重新启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d668-120">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d668-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d668-121">See Also</span></span>  
 <span data-ttu-id="8d668-122">[Management Studio 中的自定义报表](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8d668-122">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="8d668-123">[将自定义报表添加到 Management Studio](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8d668-123">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 [<span data-ttu-id="8d668-124">将自定义报告与对象资源管理器节点属性一起使用</span><span class="sxs-lookup"><span data-stu-id="8d668-124">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
