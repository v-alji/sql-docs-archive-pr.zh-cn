---
title: "\"包角色\" 对话框 UI 参考 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690747"
---
# <a name="package-roles-dialog-box-ui-reference"></a><span data-ttu-id="0ab06-102">“包角色”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="0ab06-102">Package Roles Dialog Box UI Reference</span></span>
  <span data-ttu-id="0ab06-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的“包角色”\*\*\*\* 对话框，指定具有包读取访问权限的数据库级角色以及具有包写入访问权限的数据库级角色。</span><span class="sxs-lookup"><span data-stu-id="0ab06-103">Use the **Package Roles** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to specify the database-level roles that have read access to the package and the database-level roles that have write access to the package.</span></span> <span data-ttu-id="0ab06-104">数据库级角色仅适用于  msdb 数据库中存储的包[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ab06-104">Database-level roles apply only to packages that are stored in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** database.</span></span>  
  
 <span data-ttu-id="0ab06-105">若要了解有关 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 数据库级角色及其权限的详细信息，请参阅 [Integration Services 角色（SSIS 服务）](security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab06-105">To learn more about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] database-level roles and their permissions, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>  
  
 <span data-ttu-id="0ab06-106">该对话框中列出的角色是 **msdb** 系统数据库的当前数据库角色。</span><span class="sxs-lookup"><span data-stu-id="0ab06-106">The roles listed in the dialog box are the current database roles of the **msdb** system database.</span></span> <span data-ttu-id="0ab06-107">如果未选择任何角色，将应用默认的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 角色。</span><span class="sxs-lookup"><span data-stu-id="0ab06-107">If no roles are selected, the default [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] roles apply.</span></span> <span data-ttu-id="0ab06-108">默认情况下，读取者角色包括 **db_ssisadmin**、 **db_ssisoperator**以及创建包的用户。</span><span class="sxs-lookup"><span data-stu-id="0ab06-108">By default, the reader role includes **db_ssisadmin**, **db_ssisoperator**, and the user who created the package.</span></span> <span data-ttu-id="0ab06-109">作为以上任一角色的成员的用户或创建该包的用户，可以枚举、查看、导出和运行包。</span><span class="sxs-lookup"><span data-stu-id="0ab06-109">A user who is a member of one of these roles or created the packages can enumerate, view, export, and run packages.</span></span> <span data-ttu-id="0ab06-110">默认情况下，写入者角色包括 **db_ssisadmin** 和创建包的用户。</span><span class="sxs-lookup"><span data-stu-id="0ab06-110">By default, the writer role includes **db_ssisadmin** and the user who created the package.</span></span> <span data-ttu-id="0ab06-111">作为此角色的成员的用户和创建该包的用户，可以导入、删除和更改包。</span><span class="sxs-lookup"><span data-stu-id="0ab06-111">A user who is a member of this role and the user who created the packages can import, delete, and change packages.</span></span>  
  
 <span data-ttu-id="0ab06-112">**sysssispackages** 表中的 **ownersid** 列列出了创建包的用户的唯一安全标识符。</span><span class="sxs-lookup"><span data-stu-id="0ab06-112">The **ownersid** column in the **sysssispackages** table lists the unique security identifier of the user who created the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ab06-113">选项</span><span class="sxs-lookup"><span data-stu-id="0ab06-113">Options</span></span>  
 <span data-ttu-id="0ab06-114">**包名称**</span><span class="sxs-lookup"><span data-stu-id="0ab06-114">**Package Name**</span></span>  
 <span data-ttu-id="0ab06-115">指定包的名称。</span><span class="sxs-lookup"><span data-stu-id="0ab06-115">Specify the name of the package.</span></span>  
  
 <span data-ttu-id="0ab06-116">**读者角色**</span><span class="sxs-lookup"><span data-stu-id="0ab06-116">**Reader Role**</span></span>  
 <span data-ttu-id="0ab06-117">从列表中选择一个角色。</span><span class="sxs-lookup"><span data-stu-id="0ab06-117">Select a role in the list.</span></span>  
  
 <span data-ttu-id="0ab06-118">**写入者角色**</span><span class="sxs-lookup"><span data-stu-id="0ab06-118">**Writer Role**</span></span>  
 <span data-ttu-id="0ab06-119">从列表中选择一个角色</span><span class="sxs-lookup"><span data-stu-id="0ab06-119">Select a role in the list</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab06-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ab06-120">See Also</span></span>  
 <span data-ttu-id="0ab06-121">[数据库级别的角色](../relational-databases/security/authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="0ab06-121">[Database-Level Roles](../relational-databases/security/authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="0ab06-122">安全性概述 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="0ab06-122">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
