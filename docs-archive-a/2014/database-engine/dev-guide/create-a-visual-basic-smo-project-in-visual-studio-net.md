---
title: 在 Visual Studio .NET 中创建 Visual Basic SMO 项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 844d27ab6aadbc972c6282c79adb13e15d55c322
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694111"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a><span data-ttu-id="08356-102">在 Visual Studio .NET 中创建 Visual Basic SMO 项目</span><span class="sxs-lookup"><span data-stu-id="08356-102">Create a Visual Basic SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="08356-103">本节介绍了如何生成简单的 SMO 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="08356-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="08356-104">此示例导入命名空间，这样，程序即可以引用 SMO 类型。</span><span class="sxs-lookup"><span data-stu-id="08356-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="08356-105">可以选择导入 `Agent` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="08356-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="08356-106">当编写使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的程序时使用此命名空间。</span><span class="sxs-lookup"><span data-stu-id="08356-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="08356-107">需要使用 `Common` 命名空间来建立与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的安全连接。</span><span class="sxs-lookup"><span data-stu-id="08356-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="08356-108">使用 `SqlClient` 命名空间处理 SQL 异常错误。</span><span class="sxs-lookup"><span data-stu-id="08356-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a><span data-ttu-id="08356-109">在 Visual Studio .NET 中创建 Visual Basic SMO 项目</span><span class="sxs-lookup"><span data-stu-id="08356-109">Creating a Visual Basic SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="08356-110">启动 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]（或 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]）。</span><span class="sxs-lookup"><span data-stu-id="08356-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="08356-111">在“文件”菜单中，单击“新建项目”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="08356-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="08356-112">将显示“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="08356-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="08356-113">在 "**项目类型**" 对话框中，选择 " **Visual Basic**"，然后选择 " **Windows**"。</span><span class="sxs-lookup"><span data-stu-id="08356-113">In **Project Types** dialog box, select **Visual Basic**, and then select **Windows**.</span></span> <span data-ttu-id="08356-114">在 " [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 已安装的模板" 窗格中选择 "**控制台应用程序"。**</span><span class="sxs-lookup"><span data-stu-id="08356-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Console Application.**</span></span>  
  
4.  <span data-ttu-id="08356-115"> (可选) 在 "**名称**" 字段中，键入新应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="08356-115">(Optional) In the **Name** field, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="08356-116">单击 **"确定"** 加载 " [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 控制台应用程序" 模板。</span><span class="sxs-lookup"><span data-stu-id="08356-116">Click **OK** to load the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] console application template.</span></span>  
  
6.  <span data-ttu-id="08356-117">在“项目”菜单中，选择“添加引用”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="08356-117">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="08356-118">此时会显示“添加引用”对话框。</span><span class="sxs-lookup"><span data-stu-id="08356-118">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="08356-119">单击 "**浏览**"，找到 C:\PROGRAM Files\Microsoft SQL Server\120\SDK\Assemblies 文件夹中的 SMO 程序集，然后选择以下文件。</span><span class="sxs-lookup"><span data-stu-id="08356-119">Click **Browse**, locate the SMO assemblies in the C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies folder, and then select the following files.</span></span> <span data-ttu-id="08356-120">这些文件是构建一个 SMO 应用程序至少需要的文件：</span><span class="sxs-lookup"><span data-stu-id="08356-120">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="08356-121">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="08356-121">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="08356-122">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="08356-122">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
     <span data-ttu-id="08356-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="08356-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="08356-124">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="08356-124">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08356-125">使用 `Ctrl` 键可选择多个文件。</span><span class="sxs-lookup"><span data-stu-id="08356-125">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="08356-126">添加需要的任何其他 SMO 程序集。</span><span class="sxs-lookup"><span data-stu-id="08356-126">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="08356-127">例如，如果您要专门对 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 进行编程，则可以添加以下程序集：</span><span class="sxs-lookup"><span data-stu-id="08356-127">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="08356-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="08356-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="08356-129">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="08356-129">Click **Open**.</span></span>  
  
10. <span data-ttu-id="08356-130">在 "**视图**" 菜单上，单击 "**代码**"，或选择 "Module1" 窗口以显示代码窗口。</span><span class="sxs-lookup"><span data-stu-id="08356-130">On the **View** menu, click **Code**.-Or-Select the Module1.vb window to show the code window.</span></span>  
  
11. <span data-ttu-id="08356-131">在代码的任何声明前，键入以下**Imports**语句以限定 SMO 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="08356-131">In the code, before any declarations, type the following **Imports** statements to qualify the types in the SMO namespace.</span></span>  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. <span data-ttu-id="08356-132">SMO 在 Microsoft.SqlServer.Management.Smo 下具有各种命名空间，如 Microsoft.SqlServer.Management.Smo.Agent。</span><span class="sxs-lookup"><span data-stu-id="08356-132">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="08356-133">请根据需要添加这些命名空间。</span><span class="sxs-lookup"><span data-stu-id="08356-133">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="08356-134">您可以立即添加 SMO 代码。</span><span class="sxs-lookup"><span data-stu-id="08356-134">You can now add your SMO code.</span></span>  
  
  
