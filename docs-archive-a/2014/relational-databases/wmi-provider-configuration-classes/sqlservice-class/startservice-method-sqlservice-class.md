---
title: StartService 方法 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d91646da2ac2c9f636655ff6c65808ba115e28f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690432"
---
# <a name="startservice-method-sqlservice-class"></a><span data-ttu-id="29ed7-102">StartService 方法（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="29ed7-102">StartService Method (SqlService Class)</span></span>
  <span data-ttu-id="29ed7-103">尝试将服务置于启动状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-103">Attempts to place the service into its started state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ed7-104">语法</span><span class="sxs-lookup"><span data-stu-id="29ed7-104">Syntax</span></span>  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="29ed7-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="29ed7-105">Parts</span></span>  
 <span data-ttu-id="29ed7-106">对象</span><span class="sxs-lookup"><span data-stu-id="29ed7-106">*object*</span></span>  
 <span data-ttu-id="29ed7-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="29ed7-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="29ed7-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="29ed7-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="29ed7-109">一个指定下列启动状态之一的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="29ed7-109">A uint32 value that specifies one of the following startup states.</span></span>  
  
 <span data-ttu-id="29ed7-110">0</span><span class="sxs-lookup"><span data-stu-id="29ed7-110">0</span></span>  
 <span data-ttu-id="29ed7-111">成功。</span><span class="sxs-lookup"><span data-stu-id="29ed7-111">Success.</span></span> <span data-ttu-id="29ed7-112">已接受该请求。</span><span class="sxs-lookup"><span data-stu-id="29ed7-112">The request was accepted.</span></span>  
  
 <span data-ttu-id="29ed7-113">1</span><span class="sxs-lookup"><span data-stu-id="29ed7-113">1</span></span>  
 <span data-ttu-id="29ed7-114">。</span><span class="sxs-lookup"><span data-stu-id="29ed7-114">Not Supported.</span></span> <span data-ttu-id="29ed7-115">不支持该请求。</span><span class="sxs-lookup"><span data-stu-id="29ed7-115">The request is not supported.</span></span>  
  
 <span data-ttu-id="29ed7-116">2</span><span class="sxs-lookup"><span data-stu-id="29ed7-116">2</span></span>  
 <span data-ttu-id="29ed7-117">拒绝访问。</span><span class="sxs-lookup"><span data-stu-id="29ed7-117">Access Denied.</span></span> <span data-ttu-id="29ed7-118">用户没有相应的访问权限。</span><span class="sxs-lookup"><span data-stu-id="29ed7-118">The user did not have appropriate access.</span></span>  
  
 <span data-ttu-id="29ed7-119">3</span><span class="sxs-lookup"><span data-stu-id="29ed7-119">3</span></span>  
 <span data-ttu-id="29ed7-120">依赖的服务已运行。</span><span class="sxs-lookup"><span data-stu-id="29ed7-120">Dependent Services Running.</span></span> <span data-ttu-id="29ed7-121">由于其他正在运行的服务依赖于该服务，不能停止该服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-121">The service cannot be stopped because other services that are running are dependent on it.</span></span>  
  
 <span data-ttu-id="29ed7-122">4</span><span class="sxs-lookup"><span data-stu-id="29ed7-122">4</span></span>  
 <span data-ttu-id="29ed7-123">服务控制无效。</span><span class="sxs-lookup"><span data-stu-id="29ed7-123">Invalid Service Control.</span></span> <span data-ttu-id="29ed7-124">请求的控制代码无效或服务无法接受该控制代码。</span><span class="sxs-lookup"><span data-stu-id="29ed7-124">The requested control code is not valid, or it is unacceptable to the service.</span></span>  
  
 <span data-ttu-id="29ed7-125">5</span><span class="sxs-lookup"><span data-stu-id="29ed7-125">5</span></span>  
 <span data-ttu-id="29ed7-126">服务无法接受控制。</span><span class="sxs-lookup"><span data-stu-id="29ed7-126">Service Cannot Accept Control.</span></span> <span data-ttu-id="29ed7-127">由于服务的状态 (Win32_BaseService:State) 为 0、1 或 2，无法将请求的控制代码发送到该服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-127">The requested control code cannot be sent to the service because the state of the service (Win32_BaseService:State) is equal to 0, 1, or 2.</span></span>  
  
 <span data-ttu-id="29ed7-128">6</span><span class="sxs-lookup"><span data-stu-id="29ed7-128">6</span></span>  
 <span data-ttu-id="29ed7-129">服务不活动。</span><span class="sxs-lookup"><span data-stu-id="29ed7-129">Service Not Active.</span></span> <span data-ttu-id="29ed7-130">该服务尚未启动。</span><span class="sxs-lookup"><span data-stu-id="29ed7-130">The service has not been started.</span></span>  
  
 <span data-ttu-id="29ed7-131">7</span><span class="sxs-lookup"><span data-stu-id="29ed7-131">7</span></span>  
 <span data-ttu-id="29ed7-132">服务请求超时。</span><span class="sxs-lookup"><span data-stu-id="29ed7-132">Service Request Timeout.</span></span> <span data-ttu-id="29ed7-133">该服务未及时响应启动请求。</span><span class="sxs-lookup"><span data-stu-id="29ed7-133">The service did not respond to the start request in a timely fashion.</span></span>  
  
 <span data-ttu-id="29ed7-134">8</span><span class="sxs-lookup"><span data-stu-id="29ed7-134">8</span></span>  
 <span data-ttu-id="29ed7-135">未知故障。</span><span class="sxs-lookup"><span data-stu-id="29ed7-135">Unknown Failure.</span></span> <span data-ttu-id="29ed7-136">启动服务时出现未知故障。</span><span class="sxs-lookup"><span data-stu-id="29ed7-136">An unknown failure occurred when starting the service.</span></span>  
  
 <span data-ttu-id="29ed7-137">9</span><span class="sxs-lookup"><span data-stu-id="29ed7-137">9</span></span>  
 <span data-ttu-id="29ed7-138">找不到路径。</span><span class="sxs-lookup"><span data-stu-id="29ed7-138">Path Not Found.</span></span> <span data-ttu-id="29ed7-139">找不到指向服务可执行文件的目录路径。</span><span class="sxs-lookup"><span data-stu-id="29ed7-139">The directory path to the service executable was not found.</span></span>  
  
 <span data-ttu-id="29ed7-140">10</span><span class="sxs-lookup"><span data-stu-id="29ed7-140">10</span></span>  
 <span data-ttu-id="29ed7-141">服务已运行。</span><span class="sxs-lookup"><span data-stu-id="29ed7-141">Service Already Running.</span></span> <span data-ttu-id="29ed7-142">服务已在运行。</span><span class="sxs-lookup"><span data-stu-id="29ed7-142">The service is already running.</span></span>  
  
 <span data-ttu-id="29ed7-143">11</span><span class="sxs-lookup"><span data-stu-id="29ed7-143">11</span></span>  
 <span data-ttu-id="29ed7-144">服务数据库已锁定。</span><span class="sxs-lookup"><span data-stu-id="29ed7-144">Service Database Locked.</span></span> <span data-ttu-id="29ed7-145">要添加新服务的数据库已锁定。</span><span class="sxs-lookup"><span data-stu-id="29ed7-145">The database to add a new service is locked.</span></span>  
  
 <span data-ttu-id="29ed7-146">12</span><span class="sxs-lookup"><span data-stu-id="29ed7-146">12</span></span>  
 <span data-ttu-id="29ed7-147">服务依赖关系已删除。</span><span class="sxs-lookup"><span data-stu-id="29ed7-147">Service Dependency Deleted.</span></span> <span data-ttu-id="29ed7-148">已从系统中删除此服务依赖的依赖项。</span><span class="sxs-lookup"><span data-stu-id="29ed7-148">A dependency on which this service relies has been removed from the system.</span></span>  
  
 <span data-ttu-id="29ed7-149">13</span><span class="sxs-lookup"><span data-stu-id="29ed7-149">13</span></span>  
 <span data-ttu-id="29ed7-150">服务依赖关系错误。</span><span class="sxs-lookup"><span data-stu-id="29ed7-150">Service Dependency Failure.</span></span> <span data-ttu-id="29ed7-151">该服务无法从依赖的服务中找到所需的服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-151">The service failed to find the service needed from a dependent service.</span></span>  
  
 <span data-ttu-id="29ed7-152">14</span><span class="sxs-lookup"><span data-stu-id="29ed7-152">14</span></span>  
 <span data-ttu-id="29ed7-153">服务已禁用。</span><span class="sxs-lookup"><span data-stu-id="29ed7-153">Service Disabled.</span></span> <span data-ttu-id="29ed7-154">已从系统禁用该服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-154">The service has been disabled from the system.</span></span>  
  
 <span data-ttu-id="29ed7-155">15</span><span class="sxs-lookup"><span data-stu-id="29ed7-155">15</span></span>  
 <span data-ttu-id="29ed7-156">服务登录失败。</span><span class="sxs-lookup"><span data-stu-id="29ed7-156">Service Logon Failed.</span></span> <span data-ttu-id="29ed7-157">服务没有在该系统上运行所需的正确身份验证。</span><span class="sxs-lookup"><span data-stu-id="29ed7-157">The service does not have the correct authentication to run on the system.</span></span>  
  
 <span data-ttu-id="29ed7-158">16</span><span class="sxs-lookup"><span data-stu-id="29ed7-158">16</span></span>  
 <span data-ttu-id="29ed7-159">服务已标记为要删除。</span><span class="sxs-lookup"><span data-stu-id="29ed7-159">Service Marked For Deletion.</span></span> <span data-ttu-id="29ed7-160">正在从系统删除此服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-160">The service is being removed from the system.</span></span>  
  
 <span data-ttu-id="29ed7-161">17</span><span class="sxs-lookup"><span data-stu-id="29ed7-161">17</span></span>  
 <span data-ttu-id="29ed7-162">服务无线程。</span><span class="sxs-lookup"><span data-stu-id="29ed7-162">Service No Thread.</span></span> <span data-ttu-id="29ed7-163">该服务没有执行线程。</span><span class="sxs-lookup"><span data-stu-id="29ed7-163">There is no execution thread for the service.</span></span>  
  
 <span data-ttu-id="29ed7-164">18</span><span class="sxs-lookup"><span data-stu-id="29ed7-164">18</span></span>  
 <span data-ttu-id="29ed7-165">处于循环依赖关系状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-165">Status Circular Dependency.</span></span> <span data-ttu-id="29ed7-166">启动服务时存在循环依赖关系。</span><span class="sxs-lookup"><span data-stu-id="29ed7-166">There are circular dependencies when starting the service.</span></span>  
  
 <span data-ttu-id="29ed7-167">19</span><span class="sxs-lookup"><span data-stu-id="29ed7-167">19</span></span>  
 <span data-ttu-id="29ed7-168">处于名称重复状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-168">Status Duplicate Name.</span></span> <span data-ttu-id="29ed7-169">已有一个同名的服务在运行。</span><span class="sxs-lookup"><span data-stu-id="29ed7-169">There is a service running under the same name.</span></span>  
  
 <span data-ttu-id="29ed7-170">20</span><span class="sxs-lookup"><span data-stu-id="29ed7-170">20</span></span>  
 <span data-ttu-id="29ed7-171">处于名称无效状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-171">Status Invalid Name.</span></span> <span data-ttu-id="29ed7-172">该服务的名称中包含无效字符。</span><span class="sxs-lookup"><span data-stu-id="29ed7-172">There are characters that are not valid in the name of the service.</span></span>  
  
 <span data-ttu-id="29ed7-173">21</span><span class="sxs-lookup"><span data-stu-id="29ed7-173">21</span></span>  
 <span data-ttu-id="29ed7-174">处于参数无效状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-174">Status Invalid Parameter.</span></span> <span data-ttu-id="29ed7-175">向服务传递的参数无效。</span><span class="sxs-lookup"><span data-stu-id="29ed7-175">Parameters that are not valid have been passed to the service.</span></span>  
  
 <span data-ttu-id="29ed7-176">22</span><span class="sxs-lookup"><span data-stu-id="29ed7-176">22</span></span>  
 <span data-ttu-id="29ed7-177">处于服务帐户无效状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-177">Status Invalid Service Account.</span></span> <span data-ttu-id="29ed7-178">用来运行该服务的帐户无效或无权运行该服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-178">The account which this service is to run under is not valid, or it lacks the permissions to run the service.</span></span>  
  
 <span data-ttu-id="29ed7-179">23</span><span class="sxs-lookup"><span data-stu-id="29ed7-179">23</span></span>  
 <span data-ttu-id="29ed7-180">处于服务已存在状态。</span><span class="sxs-lookup"><span data-stu-id="29ed7-180">Status Service Exists.</span></span> <span data-ttu-id="29ed7-181">系统的服务数据库中已存在该服务。</span><span class="sxs-lookup"><span data-stu-id="29ed7-181">The service exists in the database of services available from the system.</span></span>  
  
 <span data-ttu-id="29ed7-182">24</span><span class="sxs-lookup"><span data-stu-id="29ed7-182">24</span></span>  
 <span data-ttu-id="29ed7-183">服务已暂停。</span><span class="sxs-lookup"><span data-stu-id="29ed7-183">Service Already Paused.</span></span> <span data-ttu-id="29ed7-184">该服务目前在系统中已暂停。</span><span class="sxs-lookup"><span data-stu-id="29ed7-184">The service is currently paused in the system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ed7-185">备注</span><span class="sxs-lookup"><span data-stu-id="29ed7-185">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ed7-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29ed7-186">See Also</span></span>  
 <span data-ttu-id="29ed7-187">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="29ed7-187">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
