---
title: 导入基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d83ed589e147c61b1692447aacb17535f18a5c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578174"
---
# <a name="import-a-policy-based-management-policy"></a><span data-ttu-id="e44f0-102">导入基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="e44f0-102">Import a Policy-Based Management Policy</span></span>
  <span data-ttu-id="e44f0-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中导入基于策略的管理策略实例。</span><span class="sxs-lookup"><span data-stu-id="e44f0-103">This topic describes how to import a Policy-Based Management policy instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e44f0-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e44f0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e44f0-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e44f0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e44f0-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e44f0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e44f0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e44f0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e44f0-108">**若要导入策略实例，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e44f0-108">**To import a policy instance, using:**</span></span>  
  
     [<span data-ttu-id="e44f0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e44f0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e44f0-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="e44f0-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e44f0-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e44f0-111">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e44f0-112">附带可用于监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的策略。</span><span class="sxs-lookup"><span data-stu-id="e44f0-112">ships with policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e44f0-113">默认情况下，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]中未安装这些策略；不过，可以从默认安装位置 C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033 导入这些策略。</span><span class="sxs-lookup"><span data-stu-id="e44f0-113">By default, these policies are not installed on the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], but they can be imported from the default location of C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e44f0-114">Security</span><span class="sxs-lookup"><span data-stu-id="e44f0-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e44f0-115">权限</span><span class="sxs-lookup"><span data-stu-id="e44f0-115">Permissions</span></span>  
 <span data-ttu-id="e44f0-116">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="e44f0-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e44f0-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e44f0-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-import-a-policy-instance"></a><span data-ttu-id="e44f0-118">导入策略实例</span><span class="sxs-lookup"><span data-stu-id="e44f0-118">To import a policy instance</span></span>  
  
1.  <span data-ttu-id="e44f0-119">在“对象资源管理器”  中，单击加号以展开新导入的策略实例要存储到的服务器。</span><span class="sxs-lookup"><span data-stu-id="e44f0-119">In **Object Explorer**, click the plus sign to expand the server where the newly-imported policy instance will reside.</span></span>  
  
2.  <span data-ttu-id="e44f0-120">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e44f0-120">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e44f0-121">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="e44f0-121">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="e44f0-122">右键单击“策略”  文件夹，然后选择“导入策略”  。</span><span class="sxs-lookup"><span data-stu-id="e44f0-122">Right-click the **Policies** folder and select **Import Policy**.</span></span>  
  
5.  <span data-ttu-id="e44f0-123">在“导入”  对话框中，键入该文件的路径和名称；或者使用“浏览”按钮 ( **...** ) 查找包含策略的 XML 文件，然后选择该文件。</span><span class="sxs-lookup"><span data-stu-id="e44f0-123">In the **Import** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the XML file that contains the policy, and then select the file.</span></span> <span data-ttu-id="e44f0-124">有关 **“导入”** 对话框中可用选项的详细信息，请参阅 [Import Policies Dialog Box](import-policies-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="e44f0-124">For more information on the available options in the **Import** dialog box, see [Import Policies Dialog Box](import-policies-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="e44f0-125">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e44f0-125">When finished, click **OK**.</span></span>  
  
  
