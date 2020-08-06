---
title: '在 Visual Studio .NET 中创建 Visual c # SMO 项目 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: b78820fafd37675332e6703cabbb87e78bde5864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588463"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a><span data-ttu-id="9a56a-102">在 Visual Studio .NET 中创建 Visual C# SMO 项目</span><span class="sxs-lookup"><span data-stu-id="9a56a-102">Create a Visual C# SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="9a56a-103">本节介绍了如何生成简单的 SMO 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a56a-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="9a56a-104">此示例导入命名空间，这样，程序即可以引用 SMO 类型。</span><span class="sxs-lookup"><span data-stu-id="9a56a-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="9a56a-105">可以选择导入 `Agent` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="9a56a-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="9a56a-106">当编写使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的程序时使用此命名空间。</span><span class="sxs-lookup"><span data-stu-id="9a56a-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="9a56a-107">需要使用 `Common` 命名空间来建立与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的安全连接。</span><span class="sxs-lookup"><span data-stu-id="9a56a-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9a56a-108">使用 `SqlClient` 命名空间处理 SQL 异常错误。</span><span class="sxs-lookup"><span data-stu-id="9a56a-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a><span data-ttu-id="9a56a-109">在 Visual Studio.NET 中创建 Visual c # SMO 项目</span><span class="sxs-lookup"><span data-stu-id="9a56a-109">Creating a Visual C# SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="9a56a-110">启动 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]（或 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]）。</span><span class="sxs-lookup"><span data-stu-id="9a56a-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="9a56a-111">在“文件”菜单中，单击“新建项目”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9a56a-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="9a56a-112">将显示“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="9a56a-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="9a56a-113">在 "**项目类型**" 对话框中，选择 " **Visual c #**"，然后选择 " **Windows**"。</span><span class="sxs-lookup"><span data-stu-id="9a56a-113">In **Project Types** dialog box, select **Visual C#**, and then select **Windows**.</span></span> <span data-ttu-id="9a56a-114">在 " [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 已安装的模板" 窗格中，选择 " **Windows 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="9a56a-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="9a56a-115"> (可选) 在 "**名称**" 字段中，键入新应用程序的名称</span><span class="sxs-lookup"><span data-stu-id="9a56a-115">(Optional) In the **Name** field, type the name of the new application</span></span>  
  
5.  <span data-ttu-id="9a56a-116">选择 Visual C# 应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="9a56a-116">Select the Visual C# application type.</span></span> <span data-ttu-id="9a56a-117">对于下面的示例，请选择 "**控制台应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="9a56a-117">For the examples that follow, select **Console Application**.</span></span>  
  
6.  <span data-ttu-id="9a56a-118">在“项目”菜单中，选择“添加引用”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9a56a-118">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="9a56a-119">此时会显示“添加引用”对话框。</span><span class="sxs-lookup"><span data-stu-id="9a56a-119">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="9a56a-120">单击 "**浏览**"，找到文件夹中的 SMO 程序集 [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] ，然后选择以下文件。</span><span class="sxs-lookup"><span data-stu-id="9a56a-120">Click **Browse**, locate the SMO assemblies in the [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] folder, and then select the following files.</span></span> <span data-ttu-id="9a56a-121">这些文件是构建一个 SMO 应用程序至少需要的文件：</span><span class="sxs-lookup"><span data-stu-id="9a56a-121">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="9a56a-122">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="9a56a-122">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="9a56a-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="9a56a-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="9a56a-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="9a56a-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
     <span data-ttu-id="9a56a-125">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="9a56a-125">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a56a-126">使用 `Ctrl` 键可选择多个文件。</span><span class="sxs-lookup"><span data-stu-id="9a56a-126">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="9a56a-127">添加需要的任何其他 SMO 程序集。</span><span class="sxs-lookup"><span data-stu-id="9a56a-127">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="9a56a-128">例如，如果您要专门对 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 进行编程，则可以添加以下程序集：</span><span class="sxs-lookup"><span data-stu-id="9a56a-128">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="9a56a-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="9a56a-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="9a56a-130">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="9a56a-130">Click **Open**.</span></span>  
  
10. <span data-ttu-id="9a56a-131">在 "**视图**" 菜单上，单击 "**代码**"，或选择 "Program1.cs [Design]" 窗口，然后双击 windows 窗体以显示代码窗口。</span><span class="sxs-lookup"><span data-stu-id="9a56a-131">On the **View** menu, click **Code**.-Or-Select the Program1.cs [Design] Windows and double-click the windows form to show the code window.</span></span>  
  
11. <span data-ttu-id="9a56a-132">在代码的命名空间语句前，键入以下 `using` 语句，以限定 SMO 命名空间中的类型：</span><span class="sxs-lookup"><span data-stu-id="9a56a-132">In the code, before the namespace statement, type the following `using` statements to qualify the types in the SMO namespace:</span></span>  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. <span data-ttu-id="9a56a-133">SMO 在 Microsoft.SqlServer.Management.Smo 下具有各种命名空间，如 Microsoft.SqlServer.Management.Smo.Agent。</span><span class="sxs-lookup"><span data-stu-id="9a56a-133">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="9a56a-134">请根据需要添加这些命名空间。</span><span class="sxs-lookup"><span data-stu-id="9a56a-134">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="9a56a-135">您可以立即添加 SMO 代码。</span><span class="sxs-lookup"><span data-stu-id="9a56a-135">You can now add your SMO code.</span></span>  
  
  
