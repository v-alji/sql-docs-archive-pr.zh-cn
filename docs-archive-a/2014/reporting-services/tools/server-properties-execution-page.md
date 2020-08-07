---
title: 服务器属性（“执行”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ec8725a0cec9e15cb6d8402f8d654320c38471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587712"
---
# <a name="server-properties-execution-page"></a><span data-ttu-id="8ac7f-102">服务器属性（“执行”页）</span><span class="sxs-lookup"><span data-stu-id="8ac7f-102">Server Properties (Execution Page)</span></span>
  <span data-ttu-id="8ac7f-103">使用此页可设置报表执行的超时值。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-103">Use this page to set a timeout value for report execution.</span></span> <span data-ttu-id="8ac7f-104">此值将应用于当前报表服务器实例处理的所有报表。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-104">This value applies to all reports that are processed by the current report server instance.</span></span> <span data-ttu-id="8ac7f-105">您可以针对单个报表覆盖此值。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-105">You can override this value for individual reports.</span></span> <span data-ttu-id="8ac7f-106">您指定的值必须适合报表服务器上发生的所有报表处理，并适合在报表服务器检索报表中所使用的数据时针对数据库服务器执行的查询处理。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-106">The value you specify must accommodate all report processing that occurs on the report server, plus query processing performed on the database server when the report server retrieves data that is used in the report.</span></span>  
  
 <span data-ttu-id="8ac7f-107">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器实例，右键单击报表服务器名称，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="8ac7f-108">单击 **“执行”** 将此页打开。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-108">Click **Execution** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ac7f-109">选项</span><span class="sxs-lookup"><span data-stu-id="8ac7f-109">Options</span></span>  
 <span data-ttu-id="8ac7f-110">**不对报表执行时间设置超时**</span><span class="sxs-lookup"><span data-stu-id="8ac7f-110">**Do not timeout report execution**</span></span>  
 <span data-ttu-id="8ac7f-111">允许报表服务器在不受限制的时间内完成报表处理。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-111">Allow a report server unlimited time to complete report processing.</span></span>  
  
 <span data-ttu-id="8ac7f-112">**将报表执行时间限制为(以秒计)**</span><span class="sxs-lookup"><span data-stu-id="8ac7f-112">**Limit report execution to the following number of seconds**</span></span>  
 <span data-ttu-id="8ac7f-113">针对报表执行设置时间约束。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-113">Set a time constraint on report execution.</span></span> <span data-ttu-id="8ac7f-114">在请求报表时将对该时间段开始计时。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-114">The time period starts when the report is requested.</span></span> <span data-ttu-id="8ac7f-115">如果在报表处理全部完成之前该时间段就已结束，那么报表服务器将取消该处理和所有对外部数据源的处理中的查询。</span><span class="sxs-lookup"><span data-stu-id="8ac7f-115">If the time period ends before the report is fully processed, the report server cancels the process and any in-process queries to external data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac7f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ac7f-116">See Also</span></span>  
 <span data-ttu-id="8ac7f-117">[设置报表服务器属性 (Management Studio)](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8ac7f-117">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="8ac7f-118">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8ac7f-118">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="8ac7f-119">[设置报表处理属性](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8ac7f-119">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="8ac7f-120">[为报表和共享数据集处理设置超时值 (SSRS)](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ac7f-120">[Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span></span>  
 [<span data-ttu-id="8ac7f-121">Management Studio 中报表服务器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="8ac7f-121">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
