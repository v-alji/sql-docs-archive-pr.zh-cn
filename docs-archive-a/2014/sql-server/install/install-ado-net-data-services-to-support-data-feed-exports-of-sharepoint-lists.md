---
title: 安装 ADO.NET Data Services 以支持 SharePoint 列表的数据馈送导出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579965"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a><span data-ttu-id="2e2dc-102">安装 ADO.NET Data Services 以支持 SharePoint 列表的数据馈送导出</span><span class="sxs-lookup"><span data-stu-id="2e2dc-102">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>
  <span data-ttu-id="2e2dc-103">ADO.NET Data Services 是 SharePoint 列表的数据馈送导出所必需的。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-103">ADO.NET Data Services is required for a data feed export of SharePoint lists.</span></span> <span data-ttu-id="2e2dc-104">SharePoint 2010 在 SharePoint Prerequisite Installer 程序中不包括此组件，因此您必须手动安装它。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-104">SharePoint 2010 does not include this component in the SharePoint Prerequisite Installer program, so you must install it manually.</span></span>  
  
 <span data-ttu-id="2e2dc-105">如果没有此先决条件，当您使用导出为数据馈送的 SharePoint 列表时，您将获得以下错误：“DTD 出于安全原因已在此 XML 文档中禁用。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-105">Without this prerequisite, you will get the following error when you attempt to use a SharePoint list that was exported as a data feed: "For security reasons DTD is prohibited in this XML document.</span></span> <span data-ttu-id="2e2dc-106">若要启用 DTD 处理，请将 XmlReaderSettings 的 ProhibitDtd 属性设置为 false，并将设置传递到 XmlReader.Create 方法。“</span><span class="sxs-lookup"><span data-stu-id="2e2dc-106">To enable DTD processing set the ProhibitDtd property on XmlReaderSettings to false and pass the settings into XmlReader.Create method."</span></span>  
  
 <span data-ttu-id="2e2dc-107">使用以下说明在您想要允许列表作为数据馈送导出的每个 SharePoint 服务器上安装 ADO.NET Data Services。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-107">Use the following instructions to install ADO.NET Data Services on every SharePoint server for which you want to allow lists to be exported as data feeds.</span></span>  
  
### <a name="download-and-install-adonet-data-services"></a><span data-ttu-id="2e2dc-108">下载和安装 ADO.NET Data Services</span><span class="sxs-lookup"><span data-stu-id="2e2dc-108">Download and install ADO.NET Data Services</span></span>  
  
1.  <span data-ttu-id="2e2dc-109">请参阅 sharepoint 2010 的硬件和软件要求文档、 [ (sharepoint 2010) 的硬件和软件要求](https://go.microsoft.com/fwlink/?LinkId=169734)</span><span class="sxs-lookup"><span data-stu-id="2e2dc-109">Go to the hardware and software requirements documentation for SharePoint 2010, [Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)</span></span>  
  
2.  <span data-ttu-id="2e2dc-110">在 "**访问适用的软件**" 中，找到与 (Windows SERVER 2008 SP2 或 windows Server 2008 R2) 的操作系统相对应的 ADO.NET Data Services 3.5 的链接。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-110">In **Access to applicable software**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using (either Windows Server 2008 SP2 or Windows Server 2008 R2).</span></span>  
  
3.  <span data-ttu-id="2e2dc-111">单击该链接并且运行安装该服务的安装程序。</span><span class="sxs-lookup"><span data-stu-id="2e2dc-111">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2dc-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e2dc-112">See Also</span></span>  
 [<span data-ttu-id="2e2dc-113">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="2e2dc-113">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
