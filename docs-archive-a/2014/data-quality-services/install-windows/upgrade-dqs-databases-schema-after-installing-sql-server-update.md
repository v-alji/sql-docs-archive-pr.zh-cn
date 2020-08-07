---
title: 安装 SQL Server 更新后升级 DQS 数据库架构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 80a1714ea250cf7cf5d34bc9d208a42a64284308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587617"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a><span data-ttu-id="148cd-102">在安装 SQL Server 更新后升级 DQS 数据库架构</span><span class="sxs-lookup"><span data-stu-id="148cd-102">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>
  <span data-ttu-id="148cd-103">当你在先前配置的 DQS 实例上安装了 SQL Server 更新（补丁、修补程序或累积更新）后，你可能需要运行 DQSInstaller.exe 文件（带 **upgrade** 命令行参数）来升级 DQS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="148cd-103">After you have installed a SQL Server update (patch, hotfix, or cumulative update) on a previously configured DQS instance, you might have to upgrade the DQS databases schema by running the DQSInstaller.exe file with the **upgrade** command line parameter.</span></span> <span data-ttu-id="148cd-104">否则，当您尝试使用数据质量客户端连接到数据质量服务器时，可能会收到以下错误：</span><span class="sxs-lookup"><span data-stu-id="148cd-104">Otherwise, you might receive the following error while trying to connect to Data Quality Server using your Data Quality Client:</span></span>  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 <span data-ttu-id="148cd-105">升级 DQS 数据库架构不会影响 DQS 数据库（知识库、数据质量项目以及 DQS_STAGING_DATA 数据库中的已导出结果）中的现有数据。</span><span class="sxs-lookup"><span data-stu-id="148cd-105">Upgrading DQS databases schema does not impact your existing data in the DQS databases (knowledge bases, data quality projects, and exported results in the DQS_STAGING_DATA database).</span></span> <span data-ttu-id="148cd-106">但是，您必须先备份 DQS 数据库，然后才能升级 DQS 数据库架构，以防止在架构升级过程中出现任何意外数据损失。</span><span class="sxs-lookup"><span data-stu-id="148cd-106">However, you must back up your DQS databases before upgrading DQS databases schema to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="148cd-107">有关备份 DQS 数据库的信息，请参阅 [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="148cd-107">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="148cd-108">大多数 SQL Server 更新将要求升级到 DQS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="148cd-108">Most of the SQL Server updates will require an upgrade to the DQS databases schema.</span></span> <span data-ttu-id="148cd-109">有关要求升级到 DQS 数据库架构的 SQL Server 更新的信息，请参阅 [升级 DQS：在 Data Quality Services 中安装累积更新或修补程序](https://go.microsoft.com/fwlink/?LinkID=251565)中的步骤 1.A。</span><span class="sxs-lookup"><span data-stu-id="148cd-109">For information about the SQL Server updates that will require an upgrade to the DQS databases schema, see the chart in step 1.A in [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="148cd-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="148cd-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="148cd-111">您必须作为 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机上 Administrators 组的成员登录。</span><span class="sxs-lookup"><span data-stu-id="148cd-111">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="148cd-112">您的 Windows 用户帐户必须是安装了 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的 SQL Server 实例中 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="148cd-112">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-dqs-databases-schema"></a><span data-ttu-id="148cd-113">升级 DQS 数据库架构</span><span class="sxs-lookup"><span data-stu-id="148cd-113">To upgrade DQS databases schema</span></span>  
  
1.  <span data-ttu-id="148cd-114">（建议）首先备份 DQS 数据库，然后进行架构升级。</span><span class="sxs-lookup"><span data-stu-id="148cd-114">(Recommended) Back up your DQS databases before you proceed with the schema upgrade.</span></span> <span data-ttu-id="148cd-115">有关备份 DQS 数据库的信息，请参阅 [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="148cd-115">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="148cd-116">启动命令提示符。</span><span class="sxs-lookup"><span data-stu-id="148cd-116">Start Command Prompt.</span></span>  
  
3.  <span data-ttu-id="148cd-117">在命令提示符下，将目录更改为 DQSInstaller.exe 出现的位置。</span><span class="sxs-lookup"><span data-stu-id="148cd-117">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="148cd-118">如果您安装了 SQL Server 的默认实例，则 DQSInstaller.exe 文件将出现在 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn 下：</span><span class="sxs-lookup"><span data-stu-id="148cd-118">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  <span data-ttu-id="148cd-119">在命令提示符下，键入以下命令，再按 Enter：</span><span class="sxs-lookup"><span data-stu-id="148cd-119">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  <span data-ttu-id="148cd-120">安装程序会提示您在继续操作之前备份 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="148cd-120">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="148cd-121">如果已经备份了 DQS 数据库，请键入 `Y` 或 `Yes`，然后按 Enter 以继续升级。</span><span class="sxs-lookup"><span data-stu-id="148cd-121">If you have already backed up your DQS databases, type `Y` or `Yes` and press ENTER to continue with the upgrade.</span></span>  
  
6.  <span data-ttu-id="148cd-122">在成功升级 DQS 数据库架构之后，将显示一条完成消息。</span><span class="sxs-lookup"><span data-stu-id="148cd-122">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="148cd-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="148cd-123">Next Steps</span></span>  
 <span data-ttu-id="148cd-124">从数据质量客户端应用程序登录到升级后的数据质量服务器。</span><span class="sxs-lookup"><span data-stu-id="148cd-124">Log on to the upgraded Data Quality Server from a Data Quality Client application.</span></span>  
  
 <span data-ttu-id="148cd-125">有关安装 SQL Server 更新后升级 DQS 数据库架构以及相关故障排除步骤的详细信息，请参阅 [升级 DQS：在 Data Quality Services 中安装累积更新或修补程序更新](https://go.microsoft.com/fwlink/?LinkID=251565)。</span><span class="sxs-lookup"><span data-stu-id="148cd-125">For more information about upgrading DQS databases schema after installing SQL Server updates and associated troubleshooting steps, see [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148cd-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="148cd-126">See Also</span></span>  
 <span data-ttu-id="148cd-127">[安装 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="148cd-127">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="148cd-128">.NET Framework 更新后升级 SQLCLR 程序集</span><span class="sxs-lookup"><span data-stu-id="148cd-128">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
