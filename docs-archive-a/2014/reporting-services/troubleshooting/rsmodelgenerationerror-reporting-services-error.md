---
title: rsModelGenerationError - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 713de57f0f2957983966f8ef0345bb374c311781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587156"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a><span data-ttu-id="0d2e0-102">rsModelGenerationError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="0d2e0-102">rsModelGenerationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="0d2e0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0d2e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d2e0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0d2e0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="0d2e0-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0d2e0-105">Event ID</span></span>|<span data-ttu-id="0d2e0-106">rsRenderingError</span><span class="sxs-lookup"><span data-stu-id="0d2e0-106">rsRenderingError</span></span>|  
|<span data-ttu-id="0d2e0-107">事件源</span><span class="sxs-lookup"><span data-stu-id="0d2e0-107">Event Source</span></span>|<span data-ttu-id="0d2e0-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="0d2e0-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="0d2e0-109">组件</span><span class="sxs-lookup"><span data-stu-id="0d2e0-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="0d2e0-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="0d2e0-110">Message Text</span></span>|<span data-ttu-id="0d2e0-111">生成模型时出错。</span><span class="sxs-lookup"><span data-stu-id="0d2e0-111">An error occurred while generating model.</span></span> <span data-ttu-id="0d2e0-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span><span class="sxs-lookup"><span data-stu-id="0d2e0-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d2e0-113">说明</span><span class="sxs-lookup"><span data-stu-id="0d2e0-113">Explanation</span></span>  
 <span data-ttu-id="0d2e0-114">不能生成报表模型。</span><span class="sxs-lookup"><span data-stu-id="0d2e0-114">The report model could not be generated.</span></span> <span data-ttu-id="0d2e0-115">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 SP1 及更低版本中，如果 System.Data.DataSet 对象无法处理数据库架构中的表或关系（例如，如果在表中的同一列上定义了两个外键），最有可能会显示此错误。</span><span class="sxs-lookup"><span data-stu-id="0d2e0-115">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 and earlier versions, this error is most likely displayed when the System.Data.DataSet object cannot handle a table or relationship within the database schema, such as when, for example, two foreign keys are defined on the same column within a table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d2e0-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="0d2e0-116">User Action</span></span>  
 <span data-ttu-id="0d2e0-117">若要确定导致出现此消息的具体原因，请查看报表服务器日志文件，该文件位于 \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles。</span><span class="sxs-lookup"><span data-stu-id="0d2e0-117">To determine the specific reason that caused this message to appear, review the report server log files, which are located at \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="0d2e0-118">仅内部</span><span class="sxs-lookup"><span data-stu-id="0d2e0-118">Internal-Only</span></span>  
  
