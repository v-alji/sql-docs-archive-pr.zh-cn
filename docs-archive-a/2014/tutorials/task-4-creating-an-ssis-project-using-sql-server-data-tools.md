---
title: 任务4：使用 SQL Server Data Tools 创建 SSIS 项目 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07976dbd2c84b1385d79ce3f4ce4f616e0f706b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690245"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a><span data-ttu-id="23767-102">任务 4：使用 SQL Server Data Tools 创建 SSIS 项目</span><span class="sxs-lookup"><span data-stu-id="23767-102">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>
  <span data-ttu-id="23767-103">在此任务中，你将通过使用**SQL Server Data Tools**来创建 SSIS 项目，以自动执行清理和匹配的供应商数据。</span><span class="sxs-lookup"><span data-stu-id="23767-103">In this task, you create an SSIS project by using **SQL Server Data Tools** to automate cleansing and matching supplier data.</span></span>

1.  <span data-ttu-id="23767-104">启动 **SQL Server Data Tools**。</span><span class="sxs-lookup"><span data-stu-id="23767-104">Launch **SQL Server Data Tools**.</span></span> <span data-ttu-id="23767-105">单击 "开始"，指向 "**所有程序**"，展开**Microsoft SQL Server 2012**"，然后单击" **SQL Server Data Tools**"。</span><span class="sxs-lookup"><span data-stu-id="23767-105">Click Start, point to **All Programs**, expand **Microsoft SQL Server 2012**, and click **SQL Server Data Tools**.</span></span>

2.  <span data-ttu-id="23767-106">在 **“文件”** 菜单中，指向 **“新建”**，然后单击 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="23767-106">On the **File** menu, point to **New**, and click **Project**.</span></span>

3.  <span data-ttu-id="23767-107">在 "**已安装的模板**" 窗格中展开 "**商业智能**"，然后选择**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="23767-107">Expand **Business Intelligence** in the **Installed Templates** pane, and select **Integration Services**.</span></span>

     <span data-ttu-id="23767-108">![Visual Studio -“新建项目”对话框](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio -“新建项目”对话框")</span><span class="sxs-lookup"><span data-stu-id="23767-108">![Visual Studio - New Project Dialog Box](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - New Project Dialog Box")</span></span>

4.  <span data-ttu-id="23767-109">在**项目类型列表**中选择 " **Integration Services 项目**"。</span><span class="sxs-lookup"><span data-stu-id="23767-109">Select **Integration Services Project** in the **list of project types**.</span></span>

5.  <span data-ttu-id="23767-110">键入**CleanseAndCurateSuppliers**作为**名称**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="23767-110">Type **CleanseAndCurateSuppliers** for **Name** and click **OK**.</span></span>

6.  <span data-ttu-id="23767-111">在**解决方案资源管理器**"窗口中，右键单击 **.dtsx** ，然后选择"**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="23767-111">In **Solution Explorer** window, right-click **Package.dtsx** and select **Rename**.</span></span> <span data-ttu-id="23767-112">如果看不到**解决方案资源管理器**窗口，请单击菜单栏上的 "**视图**"，然后单击 "**解决方案资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="23767-112">If you don't see **Solution Explorer** window, click **View** on the menu bar and click **Solution Explorer**.</span></span>

     <span data-ttu-id="23767-113">![Package.dtsx -“重命名”菜单](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx -“重命名”菜单")</span><span class="sxs-lookup"><span data-stu-id="23767-113">![Package.dtsx - Rename Menu](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Rename Menu")</span></span>

7.  <span data-ttu-id="23767-114">键入**cleanseandcurate.cleanse supplier data.guid** ，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="23767-114">Type **CleanseAndCurate.dtsx** and press **ENTER**.</span></span> <span data-ttu-id="23767-115">请确保该**扩展**保持为 " **.dtsx**"。</span><span class="sxs-lookup"><span data-stu-id="23767-115">Make sure that the **extension** remains **.dtsx**.</span></span>

## <a name="next-step"></a><span data-ttu-id="23767-116">下一步</span><span class="sxs-lookup"><span data-stu-id="23767-116">Next Step</span></span>
 [<span data-ttu-id="23767-117">任务 5：添加数据流任务</span><span class="sxs-lookup"><span data-stu-id="23767-117">Task 5: Adding Data Flow Task</span></span>](task-5-adding-data-flow-task.md)


