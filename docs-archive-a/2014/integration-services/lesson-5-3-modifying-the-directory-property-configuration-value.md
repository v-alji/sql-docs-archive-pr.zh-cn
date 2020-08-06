---
title: 步骤 3：修改目录属性配置值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579627"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a><span data-ttu-id="6f2ea-102">步骤 3：修改目录属性配置值</span><span class="sxs-lookup"><span data-stu-id="6f2ea-102">Step 3: Modifying the Directory Property Configuration Value</span></span>
  <span data-ttu-id="6f2ea-103">在此任务中，将针对包级变量 `User::varFolderName`的 Value 属性，修改存储在 SSISTutorial.dtsConfig 文件中的配置设置。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-103">In this task, you will modify the configuration setting, stored in the SSISTutorial.dtsConfig file, for the Value property of the package-level variable `User::varFolderName`.</span></span> <span data-ttu-id="6f2ea-104">该变量可以更新 Foreach 循环容器的 Directory 属性。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-104">The variable updates the Directory property of the Foreach Loop container.</span></span> <span data-ttu-id="6f2ea-105">修改后的值将指向在 `New Sample Data` 上一任务中创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-105">The modified value will point to the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="6f2ea-106">修改了配置设置并运行包以后，该变量将使用从配置文件填充的值（而不是包中最初配置的目录值），来更新 Directory 属性。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-106">After you modify the configuration setting and run the package, the Directory property will be updated by the variable, using the value populated from the configuration file instead of the directory value originally configured in the package.</span></span>  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a><span data-ttu-id="6f2ea-107">修改目录属性的配置设置</span><span class="sxs-lookup"><span data-stu-id="6f2ea-107">To modify the configuration setting of the Directory property</span></span>  
  
1.  <span data-ttu-id="6f2ea-108">在记事本或其他文本编辑器中，找到并打开在前一个任务中使用包配置向导创建的 SSISTutorial.dtsConfig 配置文件。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-108">In Notepad or any other text editor, locate and open the SSISTutorial.dtsConfig configuration file that you created by using the Package Configuration Wizard in the previous task.</span></span>  
  
2.  <span data-ttu-id="6f2ea-109">更改**ConfiguredValue**元素的值，使其与 `New Sample Data` 在上一任务中创建的文件夹的路径匹配。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-109">Change the value of the **ConfiguredValue** element to match the path of the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="6f2ea-110">请不要将路径用引号括起来。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-110">Do not surround the path in quotes.</span></span> <span data-ttu-id="6f2ea-111">如果 `New Sample Data` 文件夹在驱动器的根级别 (例如，C： \\) ，则更新的 XML 应类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="6f2ea-111">If the `New Sample Data` folder is at the root level of your drive (for example, C:\\), the updated XML should be similar to the following sample:</span></span>  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     <span data-ttu-id="6f2ea-112">当然，标题信息、、 `GeneratedBy` `GeneratedFromPackageID` 和**GeneratedDate**在文件中将有所不同。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-112">The heading information, `GeneratedBy`, `GeneratedFromPackageID`, and **GeneratedDate** will be different in your file, of course.</span></span> <span data-ttu-id="6f2ea-113">要注意的元素是 `Configuration` 元素。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-113">The element to note is the `Configuration` element.</span></span> <span data-ttu-id="6f2ea-114">变量 `Value` 的 `User::varFolderName` 属性现在包含 C:\New Sample Data。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-114">The `Value` property of the variable, `User::varFolderName`, now contains C:\New Sample Data.</span></span>  
  
3.  <span data-ttu-id="6f2ea-115">保存更改，再关闭文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="6f2ea-115">Save the change, and then close the text editor.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6f2ea-116">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6f2ea-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6f2ea-117">步骤 4：测试第 5 课教程包</span><span class="sxs-lookup"><span data-stu-id="6f2ea-117">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
