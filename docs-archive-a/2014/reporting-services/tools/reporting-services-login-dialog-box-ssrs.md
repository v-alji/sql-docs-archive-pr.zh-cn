---
title: “Reporting Services 登录”对话框 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691575"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a><span data-ttu-id="f244f-102">“Reporting Services 登录”对话框 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f244f-102">Reporting Services Login Dialog Box (SSRS)</span></span>
  <span data-ttu-id="f244f-103">使用 **“Reporting Services 登录”** 对话框可以提供向报表服务器发布报表时要使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="f244f-103">Use the **Reporting Services Login** dialog box to provide credentials to publish reports to the report server.</span></span>  
  
-   <span data-ttu-id="f244f-104">**注意**如果这是你首次将报表发布到 Report Server，因为设置了为项目设置**TargetServerURL**部署属性，请验证你指定的服务器名称是否类似于 `http://localhost/reportserver` ，而不是 `http://localhost/reports` 。</span><span class="sxs-lookup"><span data-stu-id="f244f-104">**Note** If this is the first time you have published a report to a report server since set you set the deployment property **TargetServerURL** for a project, verify that the server name you specified is similar to `http://localhost/reportserver`, and not `http://localhost/reports`.</span></span> <span data-ttu-id="f244f-105">在本地服务器上指定 `reports` 目录而不是 `reportserver` 目录将间接打开此对话框。</span><span class="sxs-lookup"><span data-stu-id="f244f-105">Specifying the `reports` directory on the local server instead of the `reportserver` directory indirectly causes this dialog box to open.</span></span> <span data-ttu-id="f244f-106">有关设置 TargetServerURL 的详细信息，请参阅[设置部署属性 (Reporting Services)](set-deployment-properties-reporting-services.md)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f244f-106">For more information about setting **TargetServerURL**, see [Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f244f-107">选项</span><span class="sxs-lookup"><span data-stu-id="f244f-107">Options</span></span>  
 <span data-ttu-id="f244f-108">**Server**</span><span class="sxs-lookup"><span data-stu-id="f244f-108">**Server**</span></span>  
 <span data-ttu-id="f244f-109">显示报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="f244f-109">Displays the name of the report server.</span></span> <span data-ttu-id="f244f-110">例如，`http://localhost/reportserver`。</span><span class="sxs-lookup"><span data-stu-id="f244f-110">For example, `http://localhost/reportserver`.</span></span> <span data-ttu-id="f244f-111">如果报表服务器使用的不是默认端口 80，则需要包含端口号。</span><span class="sxs-lookup"><span data-stu-id="f244f-111">For report servers that use a different port than default port 80, include the port number.</span></span> <span data-ttu-id="f244f-112">例如，`http://localhost:81/reportserver`。</span><span class="sxs-lookup"><span data-stu-id="f244f-112">For example, `http://localhost:81/reportserver`.</span></span>  
  
 <span data-ttu-id="f244f-113">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f244f-113">**User name**</span></span>  
 <span data-ttu-id="f244f-114">键入登录 Web 服务时要使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="f244f-114">Type the user name to log in to the Web service.</span></span>  
  
 <span data-ttu-id="f244f-115">**密码**</span><span class="sxs-lookup"><span data-stu-id="f244f-115">**Password**</span></span>  
 <span data-ttu-id="f244f-116">键入登录 Web 服务时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="f244f-116">Type the password to log in to the Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f244f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f244f-117">See Also</span></span>  
 <span data-ttu-id="f244f-118">[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f244f-118">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="f244f-119">[为报表数据源指定凭据和连接信息](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)[报表设计器 F1 帮助](report-designer-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="f244f-119">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Report Designer F1 Help](report-designer-f1-help.md)</span></span>  
  
  
