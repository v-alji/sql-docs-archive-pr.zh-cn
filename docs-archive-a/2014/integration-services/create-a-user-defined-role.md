---
title: 创建用户定义的角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ee905c2636e20315c2180a6be8f8e40f76d5f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580806"
---
# <a name="create-a-user-defined-role"></a><span data-ttu-id="e4112-102">创建用户定义的角色</span><span class="sxs-lookup"><span data-stu-id="e4112-102">Create a User-Defined Role</span></span>
    
### <a name="to-create-a-user-defined-role"></a><span data-ttu-id="e4112-103">创建用户定义角色</span><span class="sxs-lookup"><span data-stu-id="e4112-103">To create a user-defined role</span></span>  
  
1.  <span data-ttu-id="e4112-104">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e4112-104">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4112-105">在 **“视图”** 菜单上，单击 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="e4112-105">Click **Object Explorer** on the **View** menu.</span></span>  
  
3.  <span data-ttu-id="e4112-106">在对象资源管理器工具栏上，单击 **“连接”** ，再单击 **“数据库引擎”** 。</span><span class="sxs-lookup"><span data-stu-id="e4112-106">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
4.  <span data-ttu-id="e4112-107">在 **“连接到服务器”** 对话框中，提供服务器名，并选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="e4112-107">In the **Connect to Server** dialog box, provide a server name and select an authentication mode.</span></span> <span data-ttu-id="e4112-108">可以使用句点 (.)、(local) 或 `localhost` 来指示本地服务器。</span><span class="sxs-lookup"><span data-stu-id="e4112-108">You can use a period (.), (local), or `localhost` to indicate the local server.</span></span>  
  
5.  <span data-ttu-id="e4112-109">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="e4112-109">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="e4112-110">展开“数据库”、“系统数据库”、“msdb”、“安全性”和“角色”。</span><span class="sxs-lookup"><span data-stu-id="e4112-110">Expand Databases, System Databases, msdb, Security, and Roles.</span></span>  
  
7.  <span data-ttu-id="e4112-111">在“角色”节点中，右键单击“数据库角色”，再单击“新建数据库角色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4112-111">In the Roles node, right-click Database Roles, and click **New Database Role**.</span></span>  
  
8.  <span data-ttu-id="e4112-112">在“常规”页上，提供一个名称，还可以指定一个所有者、拥有的架构以及添加角色成员。</span><span class="sxs-lookup"><span data-stu-id="e4112-112">On the General page, provide a name and optionally, specify an owner and owned schemas and add role members.</span></span>  
  
9. <span data-ttu-id="e4112-113">还可以单击 **“权限”** ，配置对象权限。</span><span class="sxs-lookup"><span data-stu-id="e4112-113">Optionally, click **Permissions** and configure object permissions.</span></span>  
  
10. <span data-ttu-id="e4112-114">还可以单击 **“扩展属性”** ，配置任何扩展属性。</span><span class="sxs-lookup"><span data-stu-id="e4112-114">Optionally, click **Extended Properties** and configure any extended properties.</span></span>  
  
11. <span data-ttu-id="e4112-115">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e4112-115">Click **OK**.</span></span>  
  
  
