---
title: 将基于策略的管理方面状态复制到 XML 文件中 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7be2332d9a2507a079d85a3424bda3a387609ca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689333"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a><span data-ttu-id="4621e-102">将基于策略的管理方面状态复制到 XML 文件中</span><span class="sxs-lookup"><span data-stu-id="4621e-102">Copy a Policy-Based Management Facet State to an XML File</span></span>
  <span data-ttu-id="4621e-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中将基于策略的管理方面的状态复制到 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="4621e-103">This topic describes how to how to copy the state of a Policy-Based Management facet to an XML file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4621e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4621e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4621e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4621e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4621e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="4621e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4621e-107">**若要将方面状态复制到 XML 文件中，请使用：**</span><span class="sxs-lookup"><span data-stu-id="4621e-107">**To copy a facet state to an XML file, using:**</span></span>  
  
     [<span data-ttu-id="4621e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4621e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4621e-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="4621e-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4621e-110">Security</span><span class="sxs-lookup"><span data-stu-id="4621e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4621e-111">权限</span><span class="sxs-lookup"><span data-stu-id="4621e-111">Permissions</span></span>  
 <span data-ttu-id="4621e-112">本主题中的过程要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="4621e-112">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4621e-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4621e-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a><span data-ttu-id="4621e-114">将方面状态复制到 XML 文件中</span><span class="sxs-lookup"><span data-stu-id="4621e-114">To copy a facet state to an XML file</span></span>  
  
1.  <span data-ttu-id="4621e-115">在对象资源管理器中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例、实例对象、数据库或数据库对象，然后单击“Facet”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4621e-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="4621e-116">在 "**查看方面-**_object_name_ " 对话框中，单击 "将**当前状态导出为策略**"。</span><span class="sxs-lookup"><span data-stu-id="4621e-116">In the **View Facets -**_object_name_ dialog box, click **Export Current State as Policy**.</span></span>  
  
3.  <span data-ttu-id="4621e-117">在“导出为策略”\*\*\*\* 对话框中，键入该文件的路径和名称；或者使用“浏览”按钮 **(...)** 查找该文件，然后键入该 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="4621e-117">In the **Export as Policy** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the file, and then type the name of the XML file.</span></span> <span data-ttu-id="4621e-118">有关此对话框中可用选项的详细信息，请参阅 [Export As Policy Dialog Box](export-as-policy-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="4621e-118">For more information on the available options in this dialog box, see [Export As Policy Dialog Box](export-as-policy-dialog-box.md)</span></span>  
  
4.  <span data-ttu-id="4621e-119">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4621e-119">When finished, click **OK**.</span></span>  
  
  
