---
title: 角色和权限 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e6098a51afde04164e3ef0dfa5e5297457b4440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587177"
---
# <a name="roles-and-permissions-reporting-services"></a><span data-ttu-id="0360d-102">角色和权限 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="0360d-102">Roles and Permissions (Reporting Services)</span></span>
  <span data-ttu-id="0360d-103">Reporting Services 提供身份验证子系统和基于角色的授权模型。</span><span class="sxs-lookup"><span data-stu-id="0360d-103">Reporting Services provides an authentication subsystem and role-based authorization model.</span></span> <span data-ttu-id="0360d-104">身份验证和授权模型取决于相应的报表服务器是在本机模式下运行还是在 SharePoint 模式下运行。</span><span class="sxs-lookup"><span data-stu-id="0360d-104">Authentication and authorization models vary depending on whether the report server runs in native mode or SharePoint mode.</span></span> <span data-ttu-id="0360d-105">如果报表服务器是 SharePoint 部署的一部分，则 SharePoint 权限将确定哪些用户对此报表服务器具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="0360d-105">If the report server is part of a SharePoint deployment, SharePoint permissions determine who has access to the report server.</span></span>  
  
## <a name="identity-and-access-control-for-native-mode"></a><span data-ttu-id="0360d-106">本机模式下的标识和访问控制</span><span class="sxs-lookup"><span data-stu-id="0360d-106">Identity and Access Control for Native Mode</span></span>  
 <span data-ttu-id="0360d-107">默认的身份验证基于 Windows 身份验证和集成安全性。</span><span class="sxs-lookup"><span data-stu-id="0360d-107">Default authentication is based on Windows Authentication and integrated security.</span></span> <span data-ttu-id="0360d-108">可以更改身份验证设置以允许报表服务器对不同的身份验证请求作出响应，甚至可以用您提供的自定义身份验证扩展插件替换默认安全功能。</span><span class="sxs-lookup"><span data-stu-id="0360d-108">You can change the authentication settings to allow the report server to respond to different authentication requests, or even replace the default security features with a custom authentication extension that you provide.</span></span>  
  
 <span data-ttu-id="0360d-109">授权基于分配给主体的角色。</span><span class="sxs-lookup"><span data-stu-id="0360d-109">Authorization is based on roles that you assign to a principle.</span></span> <span data-ttu-id="0360d-110">每个角色由一组相关任务组成，这些任务又由一组相关操作组成。</span><span class="sxs-lookup"><span data-stu-id="0360d-110">Each role consists of a set of related tasks, which are in turn composed of related operations.</span></span> <span data-ttu-id="0360d-111">例如， **“管理报表”** 任务授予对以下报表服务器操作的访问权限：查看报表、添加报表、更新报表、删除报表、计划报表和更新报表属性。</span><span class="sxs-lookup"><span data-stu-id="0360d-111">For example, the **Manage reports** task grants access to the following report server operations: view reports, add report, update report, delete report, schedule report, and update report properties.</span></span>  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a><span data-ttu-id="0360d-112">SharePoint 模式下的标识和访问控制</span><span class="sxs-lookup"><span data-stu-id="0360d-112">Identity and Access Control for SharePoint Mode</span></span>  
 <span data-ttu-id="0360d-113">在 SharePoint 集成模式下，身份验证和授权都在请求到达报表服务器之前在 SharePoint 站点处理。</span><span class="sxs-lookup"><span data-stu-id="0360d-113">In SharePoint integrated mode, authentication and authorization are handled on the SharePoint site, before requests reach the report server.</span></span> <span data-ttu-id="0360d-114">根据身份验证的配置方式，来自 SharePoint 站点的请求包含安全标记或可信用户名。</span><span class="sxs-lookup"><span data-stu-id="0360d-114">Depending on how you configure authentication, requests from a SharePoint site include a security token or a trusted user name.</span></span> <span data-ttu-id="0360d-115">为 SharePoint 用户和组设置的权限授予对置于 SharePoint 库中的报表服务器项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0360d-115">Permissions that you set for SharePoint users and groups authorize access to report server items that are placed in SharePoint libraries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0360d-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="0360d-116">In This Section</span></span>  
 [<span data-ttu-id="0360d-117">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="0360d-117">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
 <span data-ttu-id="0360d-118">介绍基于角色的授权模型，该模型提供对内容和操作的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0360d-118">Describes the role-based authorization model that provides access to content and operations.</span></span>  
  
 [<span data-ttu-id="0360d-119">在 SharePoint 站点上授予对报表服务器项的权限</span><span class="sxs-lookup"><span data-stu-id="0360d-119">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 <span data-ttu-id="0360d-120">说明如何使用 SharePoint 组、权限级别和权限来控制对报表服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0360d-120">Explains how SharePoint groups, permission levels, and permissions are used to control access to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0360d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0360d-121">See Also</span></span>  
 <span data-ttu-id="0360d-122">[针对报表服务器的身份验证](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0360d-122">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 [<span data-ttu-id="0360d-123">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="0360d-123">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
