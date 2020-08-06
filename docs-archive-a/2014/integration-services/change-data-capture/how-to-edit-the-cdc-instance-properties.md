---
title: 如何编辑 CDC 实例属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b02785a32fa1f64d5da0c3202acd7916da1e65ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683014"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a><span data-ttu-id="90c51-102">如何编辑 CDC 实例属性</span><span class="sxs-lookup"><span data-stu-id="90c51-102">How to Edit the CDC Instance Properties</span></span>
  <span data-ttu-id="90c51-103">本过程介绍如何使用 CDC 设计器控制台编辑 CDC 实例的配置属性。</span><span class="sxs-lookup"><span data-stu-id="90c51-103">This procedure describes how to use the CDC Designer Console to edit the configuration properties for a CDC instance.</span></span>  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a><span data-ttu-id="90c51-104">编辑 CDC 实例的配置属性</span><span class="sxs-lookup"><span data-stu-id="90c51-104">To edit the CDC instance configuration properties</span></span>  
  
1.  <span data-ttu-id="90c51-105">从 **“开始”** 菜单上，选择 **“CDC 设计器控制台”** 。</span><span class="sxs-lookup"><span data-stu-id="90c51-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="90c51-106">在左侧的窗格中，展开 **“变更数据捕获”** ，然后展开包含您要编辑其属性的实例的服务。</span><span class="sxs-lookup"><span data-stu-id="90c51-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance with the properties that you want to edit.</span></span>  
  
3.  <span data-ttu-id="90c51-107">选择要编辑其属性的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="90c51-107">Select the name of the instance where you want to edit the properties.</span></span>  
  
4.  <span data-ttu-id="90c51-108">从 CDC 设计器控制台右侧的“操作”窗格中，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="90c51-108">From the Actions pane on the right side of the CDC Designer Console, click **Properties**.</span></span>  
  
     <span data-ttu-id="90c51-109">也可以右键单击要编辑其属性的实例，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="90c51-109">You can also right-click the instance where you want to edit the properties and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="90c51-110">在属性编辑器中，在以下选项卡中编辑属性：</span><span class="sxs-lookup"><span data-stu-id="90c51-110">In the Properties editor, edit the properties in the following tabs:</span></span>  
  
    -   <span data-ttu-id="90c51-111">**Oracle**：使用属性编辑器中的 **“Oracle”** 选项卡可对在新建实例向导的“创建 CDC 数据库”页中提供的说明进行更改，以及对 Oracle 日志挖掘数据库连接信息进行更改。</span><span class="sxs-lookup"><span data-stu-id="90c51-111">**Oracle**: Use the **Oracle** tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
         <span data-ttu-id="90c51-112">有关可在此选项卡中编辑的内容的信息，请参阅 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="90c51-112">For information about what you can edit in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
    -   <span data-ttu-id="90c51-113">**表**：使用 **“表”** 选项卡可对您从 Oracle 源数据库中选择的表和列进行更改。</span><span class="sxs-lookup"><span data-stu-id="90c51-113">**Tables**: Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span>  
  
         <span data-ttu-id="90c51-114">有关可在此选项卡中编辑的内容的信息，请参阅 [Edit Tables](edit-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="90c51-114">For information about what you can edit in this tab, see Edit [Edit Tables](edit-tables.md)</span></span>  
  
    -   <span data-ttu-id="90c51-115">**脚本**：使用“脚本”  选项卡可对 Oracle 源数据库运行或重新运行一个设置补充日志记录的脚本。</span><span class="sxs-lookup"><span data-stu-id="90c51-115">**Scripts**: Use the **Scripts** tab to run or re-run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
         <span data-ttu-id="90c51-116">有关可在此选项卡中执行的操作的信息，请参阅 [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md)。</span><span class="sxs-lookup"><span data-stu-id="90c51-116">For information about what you can do in this tab, see [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).</span></span>  
  
    -   <span data-ttu-id="90c51-117">**高级**：使用 **“高级”** 选项卡可以向 CDC 实例添加特殊属性。</span><span class="sxs-lookup"><span data-stu-id="90c51-117">**Advanced**: Use the **Advanced** tab to add special properties to the CDC instance.</span></span>  
  
         <span data-ttu-id="90c51-118">有关可在此选项卡中执行的操作的信息，请参阅 [Edit the Advanced Properties](edit-the-advanced-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="90c51-118">For information about what you can do in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
