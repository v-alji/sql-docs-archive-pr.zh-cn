---
title: " (Analysis Services) 授予服务器管理员权限 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
ms.openlocfilehash: 822227ae89f4f219a055bcc0d6d6b0a228f7964b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689669"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a><span data-ttu-id="aa7e1-102">授予服务器管理员权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="aa7e1-102">Grant Server Administrator Permissions (Analysis Services)</span></span>
  <span data-ttu-id="aa7e1-103">对于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中的所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象和数据，该实例中的服务器管理员角色的成员具有无限访问权限。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-103">Members of the Server administrator role within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] have unrestricted access to all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects and data in that instance.</span></span> <span data-ttu-id="aa7e1-104">用户必须是服务器管理员角色的成员才能执行任何服务器范围内的任务，如创建或处理数据库、修改服务器属性或启动跟踪（处理事件除外）。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-104">A user must be a member of the Server administrator role to perform any server-wide task, such as creating or processing a database, modifying server properties, or launching a trace (other than for processing events).</span></span>

 <span data-ttu-id="aa7e1-105">安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 时将建立角色成员身份。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-105">Role membership is established when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is installed.</span></span> <span data-ttu-id="aa7e1-106">在设置服务器时，运行安装程序的用户可以将他或他自己添加到该角色，或添加其他用户。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-106">The user running the Setup program can add him or herself to the role, or add another user, when provisioning the server.</span></span> <span data-ttu-id="aa7e1-107">可以使用以下步骤将角色成员身份修改为安装后任务。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-107">You can modify role membership as a post-installation task using the following procedure.</span></span>

## <a name="modify-server-role-membership"></a><span data-ttu-id="aa7e1-108">修改服务器角色成员身份</span><span class="sxs-lookup"><span data-stu-id="aa7e1-108">Modify Server Role Membership</span></span>

1.  <span data-ttu-id="aa7e1-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，在对象资源管理器中右键单击实例名称，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and then right-click the instance name in Object Explorer and then click **Properties**.</span></span>

2.  <span data-ttu-id="aa7e1-110">在 **“选择页”** 窗格中单击 **“安全性”** ，然后单击页底部的 **“添加”** 以将一个或多个 Windows 用户或组添加到服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-110">Click **Security** in the **Select a Page** pane, and then click **Add** at the bottom of the page to add one or more Windows users or groups to the server role.</span></span>

     <span data-ttu-id="aa7e1-111">![Management Studio 中的“添加用户”对话框](../media/ssas-serveradminadd.png "Management Studio 中的“添加用户”对话框")</span><span class="sxs-lookup"><span data-stu-id="aa7e1-111">![Add users dialog box in management studio](../media/ssas-serveradminadd.png "Add users dialog box in management studio")</span></span>

 <span data-ttu-id="aa7e1-112">安装时，SQL Server 安装程序需要您指定至少一个用户帐户为 Analysis Services 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-112">At installation time, SQL Server Setup requires that you specify at least one user account as the Analysis Services system administrator.</span></span>

 <span data-ttu-id="aa7e1-113">默认情况下，还将为本地 Administrators 组的成员授予 Analysis Server 中的管理权限。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-113">By default, members of the local Administrators group are also granted administrative rights in Analysis Server.</span></span> <span data-ttu-id="aa7e1-114">虽然未显式授予本地组 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务管理员角色中的成员身份，但是本地管理员可创建数据库、添加用户和权限以及执行系统管理员允许的任何其他任务。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-114">Although the local group is not explicitly granted membership in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role, local administrators can create databases, add users and permissions, and perform any other task allowed to system administrators.</span></span> <span data-ttu-id="aa7e1-115">此行为是可配置的。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-115">This behavior is configurable.</span></span> <span data-ttu-id="aa7e1-116">它由 `BuiltinAdminsAreServerAdmins` 服务器属性确定，该属性默认设置为**true** 。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-116">It is determined by the `BuiltinAdminsAreServerAdmins` server property, which is set to **true** by default.</span></span> <span data-ttu-id="aa7e1-117">您可在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中更改此属性。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-117">You can change this property in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="aa7e1-118">有关详细信息，请参阅 [Security Properties](../server-properties/security-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-118">For more information, see [Security Properties](../server-properties/security-properties.md).</span></span>

 <span data-ttu-id="aa7e1-119">您还可以使用分析管理对象 (AMO) 来管理服务器角色。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-119">You can also manage server roles by using Analysis Management Objects (AMO).</span></span> <span data-ttu-id="aa7e1-120">有关详细信息，请参阅[使用分析管理对象 (AMO) 进行开发](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)。</span><span class="sxs-lookup"><span data-stu-id="aa7e1-120">For more information, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa7e1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa7e1-121">See Also</span></span>
 <span data-ttu-id="aa7e1-122">[授权 &#40;Analysis Services&#41;安全角色的对象和操作的访问权限](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [&#40;Analysis Services 多维数据&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="aa7e1-122">[Authorizing access to objects and operations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [Security Roles  &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span></span>


