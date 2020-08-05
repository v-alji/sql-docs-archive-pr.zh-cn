---
title: 使用基于策略的管理方面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a356550796cc682b2292defffd6565b7fea0783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580168"
---
# <a name="working-with-policy-based-management-facets"></a><span data-ttu-id="36f49-102">使用基于策略的管理方面</span><span class="sxs-lookup"><span data-stu-id="36f49-102">Working with Policy-Based Management Facets</span></span>
  <span data-ttu-id="36f49-103">基于策略的管理方面是一组与管理领域相关的逻辑属性。</span><span class="sxs-lookup"><span data-stu-id="36f49-103">A Policy-Based Management facet is a set of logical properties that are related to an area of management interest.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="36f49-104">包括几个预定义的方面。</span><span class="sxs-lookup"><span data-stu-id="36f49-104">includes several predefined facets.</span></span> <span data-ttu-id="36f49-105">例如，将默认关闭的功能定义为属性的外围应用配置器方面。</span><span class="sxs-lookup"><span data-stu-id="36f49-105">For example, the Surface Area Configuration facet defines, as properties, the features that are off by default.</span></span>  
  
 <span data-ttu-id="36f49-106">在管理许多类似的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境时，您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的一个实例中配置一个方面，将该方面的状态复制到文件中，然后将该文件作为策略导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的另一个实例中。</span><span class="sxs-lookup"><span data-stu-id="36f49-106">When you manage many similar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environments, you can configure a facet in one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copy the state of the facet to a file, and then import that file into another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a policy.</span></span> <span data-ttu-id="36f49-107">将状态转换为策略后，可以将该策略应用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他实例、实例对象、数据库或数据库对象。</span><span class="sxs-lookup"><span data-stu-id="36f49-107">When the state has been converted to a policy, the policy can be applied to other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance objects, databases, or database objects.</span></span>  
  
 <span data-ttu-id="36f49-108">本主题说明如何将方面状态复制到 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="36f49-108">This topic describes how to copy the state of a facet to an XML file.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="36f49-109">权限</span><span class="sxs-lookup"><span data-stu-id="36f49-109">Permissions</span></span>  
 <span data-ttu-id="36f49-110">本主题中的过程要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="36f49-110">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
## <a name="viewing-and-copying-facet-states"></a><span data-ttu-id="36f49-111">查看和复制方面状态</span><span class="sxs-lookup"><span data-stu-id="36f49-111">Viewing and Copying Facet States</span></span>  
 [<span data-ttu-id="36f49-112">查看 SQL Server 对象的基于策略的管理分面</span><span class="sxs-lookup"><span data-stu-id="36f49-112">View the Policy-Based Management Facets on a SQL Server Object</span></span>](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [<span data-ttu-id="36f49-113">将基于策略的管理分面状态复制到 XML 文件中</span><span class="sxs-lookup"><span data-stu-id="36f49-113">Copy a Policy-Based Management Facet State to an XML File</span></span>](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="36f49-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36f49-114">See Also</span></span>  
 [<span data-ttu-id="36f49-115">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="36f49-115">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
