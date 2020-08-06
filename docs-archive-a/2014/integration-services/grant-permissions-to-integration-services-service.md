---
title: 向 Integration Services 服务授予权限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e7ab0c2f482e5a0b1bfeaa06f38ec5a886420a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578327"
---
# <a name="grant-permissions-to-integration-services-service"></a><span data-ttu-id="f401c-102">授予 Integration Services 服务权限</span><span class="sxs-lookup"><span data-stu-id="f401c-102">Grant Permissions to Integration Services Service</span></span>
  <span data-ttu-id="f401c-103">在以前版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，在您安装了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 后，默认情况下 Users 组中的所有用户都已对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="f401c-103">In previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], by default when you installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] all users in the Users group had access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="f401c-104">在您安装当前版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时，用户无权访问 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f401c-104">When you install the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], users do not have access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="f401c-105">该服务默认是安全的。</span><span class="sxs-lookup"><span data-stu-id="f401c-105">The service is secure by default.</span></span> <span data-ttu-id="f401c-106">在安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 后，管理员必须授予对服务的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f401c-106">After [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is installed, the administrator must grant access to the service.</span></span>  
  
### <a name="to-grant-access-to-the-integration-services-service"></a><span data-ttu-id="f401c-107">授予对 Integration Services 服务的访问权限</span><span class="sxs-lookup"><span data-stu-id="f401c-107">To grant access to the Integration Services service</span></span>  
  
1.  <span data-ttu-id="f401c-108">运行 Dcomcnfg.exe。</span><span class="sxs-lookup"><span data-stu-id="f401c-108">Run Dcomcnfg.exe.</span></span> <span data-ttu-id="f401c-109">Dcomcnfg.exe 提供用于修改注册表中的某些设置的用户界面。</span><span class="sxs-lookup"><span data-stu-id="f401c-109">Dcomcnfg.exe provides a user interface for modifying certain settings in the registry.</span></span>  
  
2.  <span data-ttu-id="f401c-110">在“组件服务”\*\*\*\* 对话框中，展开“组件服务 > 计算机 > 我的电脑 > DCOM 配置”节点。</span><span class="sxs-lookup"><span data-stu-id="f401c-110">In the **Component Services** dialog, expand the Component Services > Computers > My Computer > DCOM Config node.</span></span>  
  
3.  <span data-ttu-id="f401c-111">右键单击**Microsoft SQL Server Integration Services 12.0**"，然后单击"**属性**"。</span><span class="sxs-lookup"><span data-stu-id="f401c-111">Right-click **Microsoft SQL Server Integration Services 12.0**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f401c-112">在 **“安全性”** 选项卡上，在 **“启动和激活权限”** 区域中单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="f401c-112">On the **Security** tab, click **Edit** in the **Launch and Activation Permissions** area.</span></span>  
  
5.  <span data-ttu-id="f401c-113">添加用户并分配适当的权限，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f401c-113">Add users and assign appropriate permissions, and then click Ok.</span></span>  
  
6.  <span data-ttu-id="f401c-114">对于访问权限重复步骤 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="f401c-114">Repeat steps 4 - 5 for Access Permissions.</span></span>  
  
7.  <span data-ttu-id="f401c-115">重新启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="f401c-115">Restart SQL Server Management Studio.</span></span>  
  
8.  <span data-ttu-id="f401c-116">重新启动 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f401c-116">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Service.</span></span>  
  
  
