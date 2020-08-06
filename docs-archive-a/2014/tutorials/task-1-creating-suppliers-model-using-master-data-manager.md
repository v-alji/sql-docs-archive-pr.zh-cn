---
title: 任务1：使用主数据管理器创建供应商模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6bbbcbff-1ecd-456c-947f-c445c8da673c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f6823c96acb7db77a3daafa895f3353b70af44dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689189"
---
# <a name="task-1-creating-suppliers-model-using-master-data-manager"></a><span data-ttu-id="6b6be-102">任务 1：使用主数据管理器创建供应商模型</span><span class="sxs-lookup"><span data-stu-id="6b6be-102">Task 1: Creating Suppliers Model using Master Data Manager</span></span>
  <span data-ttu-id="6b6be-103">在此任务中，将使用**主数据管理器**在 MDS 中创建名为 "**供应商**" 的模型。</span><span class="sxs-lookup"><span data-stu-id="6b6be-103">In this task, you create a model named **Suppliers** in MDS using **Master Data Manager**.</span></span>  
  
1.  <span data-ttu-id="6b6be-104">导航到 `http://localhost/MDS` 以启动**主数据管理器**。</span><span class="sxs-lookup"><span data-stu-id="6b6be-104">Navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span> <span data-ttu-id="6b6be-105">如果使用其他名称配置了 Web 应用程序或它位于其他网站上，请替换该 URL。</span><span class="sxs-lookup"><span data-stu-id="6b6be-105">Replace the URL if you have configured Web Application with a different name or on a different a web site.</span></span>  
  
     <span data-ttu-id="6b6be-106">![主数据管理器 - 系统管理](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "主数据管理器 - 系统管理")</span><span class="sxs-lookup"><span data-stu-id="6b6be-106">![Master Data Manager - System Administation](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "Master Data Manager - System Administation")</span></span>  
  
2.  <span data-ttu-id="6b6be-107">单击 "**管理任务**" 部分中的 "**系统管理**"。</span><span class="sxs-lookup"><span data-stu-id="6b6be-107">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="6b6be-108">如果看不到 "**添加模型**" 页，请将鼠标悬停在菜单栏上的 "**管理**" 上，单击 "**模型**"，然后单击 "\*\*添加模型 (+) \*\*工具栏按钮以创建模型。</span><span class="sxs-lookup"><span data-stu-id="6b6be-108">If you do not see the **Add Model** page, hover mouse over **Manage** on the menu bar, click **Models**, and then click **Add Model (+)** toolbar button to create a model.</span></span>  
  
     <span data-ttu-id="6b6be-109">![“管理 - 模型”菜单](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "“管理 - 模型”菜单")</span><span class="sxs-lookup"><span data-stu-id="6b6be-109">![Manage - Models Menu](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "Manage - Models Menu")</span></span>  
  
     <span data-ttu-id="6b6be-110">![“添加模型”工具栏按钮](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "“添加模型”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="6b6be-110">![Add Model Toolbat Button](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "Add Model Toolbat Button")</span></span>  
  
4.  <span data-ttu-id="6b6be-111">输入**供应商**作为**型号名称**。</span><span class="sxs-lookup"><span data-stu-id="6b6be-111">Enter **Suppliers** for **Model name**.</span></span>  
  
5.  <span data-ttu-id="6b6be-112">清除 "**创建与模型相同的实体**" 选项。</span><span class="sxs-lookup"><span data-stu-id="6b6be-112">Clear **Create entity with same name as model** option.</span></span> <span data-ttu-id="6b6be-113">稍后将使用**MDS Add-in for Excel**创建实体。</span><span class="sxs-lookup"><span data-stu-id="6b6be-113">You will create an entity later using the **MDS Add-in for Excel**.</span></span>  
  
     <span data-ttu-id="6b6be-114">![“添加模型”页](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "“添加模型”页")</span><span class="sxs-lookup"><span data-stu-id="6b6be-114">![Add Model Page](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "Add Model Page")</span></span>  
  
6.  <span data-ttu-id="6b6be-115">单击工具栏上的 "**保存模型**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="6b6be-115">Click **Save Model** button on the toolbar.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="6b6be-116">下一步</span><span class="sxs-lookup"><span data-stu-id="6b6be-116">Next Step</span></span>  
 [<span data-ttu-id="6b6be-117">任务 2：使用用于 Excel 的 MDS 外接程序将供应商数据上传到 MDS</span><span class="sxs-lookup"><span data-stu-id="6b6be-117">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>](../../2014/tutorials/task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel.md)  
  
  
