---
title: 模型方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0b93b43383a4b0e5bf19d7c6be9c415d7c91e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691590"
---
# <a name="model-methods"></a><span data-ttu-id="48f33-102">模型方法</span><span class="sxs-lookup"><span data-stu-id="48f33-102">Model Methods</span></span>
  <span data-ttu-id="48f33-103">可以使用这些方法来管理模型。</span><span class="sxs-lookup"><span data-stu-id="48f33-103">You can use these methods to manage models.</span></span>  
  
|<span data-ttu-id="48f33-104">方法</span><span class="sxs-lookup"><span data-stu-id="48f33-104">Method</span></span>|<span data-ttu-id="48f33-105">操作</span><span class="sxs-lookup"><span data-stu-id="48f33-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|<span data-ttu-id="48f33-106">在共享数据源上生成默认模型。</span><span class="sxs-lookup"><span data-stu-id="48f33-106">Generates a default model on top of a shared data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|<span data-ttu-id="48f33-107">检索与模型项关联的用户权限。</span><span class="sxs-lookup"><span data-stu-id="48f33-107">Retrieves the user permissions that are associated with the model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|<span data-ttu-id="48f33-108">检索与模型项关联的策略。</span><span class="sxs-lookup"><span data-stu-id="48f33-108">Retrieves the policies that are associated with a model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|<span data-ttu-id="48f33-109">返回当前用户的模型的语义段。</span><span class="sxs-lookup"><span data-stu-id="48f33-109">Returns the semantic piece of a model for the current user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|<span data-ttu-id="48f33-110">删除与模型项关联的策略并导致模型项从其父项继承策略。</span><span class="sxs-lookup"><span data-stu-id="48f33-110">Deletes the policies that are associated with a model item and causes the model item to inherit the policies from its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|<span data-ttu-id="48f33-111">列出与模型中实体关联的钻取报表。</span><span class="sxs-lookup"><span data-stu-id="48f33-111">Lists drillthrough reports that are associated with an entity in a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|<span data-ttu-id="48f33-112">返回模型项子元素的数组。</span><span class="sxs-lookup"><span data-stu-id="48f33-112">Returns an array of model item child elements.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|<span data-ttu-id="48f33-113">返回支持的模型项类型的列表。</span><span class="sxs-lookup"><span data-stu-id="48f33-113">Returns a list of supported model item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|<span data-ttu-id="48f33-114">列出用户可用的模型和透视。</span><span class="sxs-lookup"><span data-stu-id="48f33-114">Lists models and perspectives that are available to the user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|<span data-ttu-id="48f33-115">基于对数据源架构的更改更新现有模型。</span><span class="sxs-lookup"><span data-stu-id="48f33-115">Updates an existing model based on changes to the data source schema.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|<span data-ttu-id="48f33-116">删除与指定模型中的模型项关联的所有策略。</span><span class="sxs-lookup"><span data-stu-id="48f33-116">Deletes all policies that are associated with model items in the specified model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|<span data-ttu-id="48f33-117">将一组钻取报表与某个模型关联。</span><span class="sxs-lookup"><span data-stu-id="48f33-117">Associates a set of drillthrough reports together with a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|<span data-ttu-id="48f33-118">设置模型项的安全策略。</span><span class="sxs-lookup"><span data-stu-id="48f33-118">Sets security policies on a model item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48f33-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48f33-119">See Also</span></span>  
 <span data-ttu-id="48f33-120">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="48f33-120">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="48f33-121">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="48f33-121">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="48f33-122">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="48f33-122">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="48f33-123">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="48f33-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
