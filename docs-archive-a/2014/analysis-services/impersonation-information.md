---
title: 模拟信息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9226fdbe8656aecf0f9173976c67ee386040d6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687327"
---
# <a name="impersonation-information"></a><span data-ttu-id="d877a-102">模拟信息</span><span class="sxs-lookup"><span data-stu-id="d877a-102">Impersonation Information</span></span>
  <span data-ttu-id="d877a-103">使用 **“模拟信息”** 页可以指定 Analysis Services 将用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="d877a-103">Use the **Impersonation Information** page to specify the credentials that Analysis Services will use to connect to the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d877a-104">选项</span><span class="sxs-lookup"><span data-stu-id="d877a-104">Options</span></span>  
 <span data-ttu-id="d877a-105">**使用特定 Windows 用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="d877a-105">**Use a specific Windows user name and password**</span></span>  
 <span data-ttu-id="d877a-106">选择此选项将使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象使用指定 Windows 用户帐户的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="d877a-106">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of a specified Windows user account.</span></span> <span data-ttu-id="d877a-107">指定凭据将用于执行处理、ROLAP 查询、外部绑定、本地多维数据集、挖掘模型、远程分区、链接对象以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="d877a-107">The specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="d877a-108">但是，对于数据挖掘扩展插件 (DMX) OPENQUERY 语句，则忽略此选项，并且将使用当前用户的凭据而不是指定用户帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="d877a-108">However, for Data Mining Extensions (DMX) OPENQUERY statements, this option is ignored and the credentials of the current user will be used.</span></span>  
  
 <span data-ttu-id="d877a-109">**用户名**</span><span class="sxs-lookup"><span data-stu-id="d877a-109">**User name**</span></span>  
 <span data-ttu-id="d877a-110">键入所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象将使用的用户帐户的域和名称。</span><span class="sxs-lookup"><span data-stu-id="d877a-110">Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="d877a-111">使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="d877a-111">Use the following format:</span></span>  
  
 <span data-ttu-id="d877a-112">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="d877a-112">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="d877a-113">只有选定了 **“使用特定名称和密码”** ，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="d877a-113">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="d877a-114">**密码**</span><span class="sxs-lookup"><span data-stu-id="d877a-114">**Password**</span></span>  
 <span data-ttu-id="d877a-115">键入所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象将使用的用户帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="d877a-115">Type the password of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="d877a-116">只有选定了 **“使用特定名称和密码”** ，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="d877a-116">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="d877a-117">**使用服务帐户**</span><span class="sxs-lookup"><span data-stu-id="d877a-117">**Use the service account**</span></span>  
 <span data-ttu-id="d877a-118">选择此选项将使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象使用与管理该对象的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务相关联的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="d877a-118">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="d877a-119">服务帐户凭据将用于处理、ROLAP 查询、远程分区、链接对象以及从目标到源的同步。</span><span class="sxs-lookup"><span data-stu-id="d877a-119">The service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="d877a-120">但是，对于数据挖掘扩展插件 (DMX) OPENQUERY 语句、本地多维数据集和挖掘模型，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="d877a-120">However, for Data Mining Extensions (DMX) OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used.</span></span> <span data-ttu-id="d877a-121">外部绑定不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="d877a-121">This option is not supported for out-of-line bindings.</span></span>  
  
 <span data-ttu-id="d877a-122">**使用当前用户的凭据**</span><span class="sxs-lookup"><span data-stu-id="d877a-122">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="d877a-123">选择此选项将使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象使用当前用户的安全凭据来处理外部绑定、DMX OPENQUERY、本地多维数据集和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d877a-123">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span> <span data-ttu-id="d877a-124">处理、ROLAP 查询、远程分区、链接对象以及从目标到源的同步不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="d877a-124">This option is not supported for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="d877a-125">**从此**</span><span class="sxs-lookup"><span data-stu-id="d877a-125">**Inherit**</span></span>  
 <span data-ttu-id="d877a-126">选择此选项可以使用服务器管理员通过 `DataSourceImpersonation` 数据库属性设置的、在数据库级别定义的模拟行为。</span><span class="sxs-lookup"><span data-stu-id="d877a-126">Select this option to use the impersonation behavior, defined at the database level, which has been set by the server administrator using the `DataSourceImpersonation` database property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d877a-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d877a-127">See Also</span></span>  
 <span data-ttu-id="d877a-128">[多维模型中的数据源](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d877a-128">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d877a-129">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="d877a-129">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
