---
title: rskeymgmt 实用工具 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], encryption
- joining report server instances [SQL Server]
- report server scale-out deployments [Reporting Services]
- cryptography [Reporting Services]
- multiple report server instances
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], scale-out deployments
- encryption [Reporting Services]
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 53f1318d-bd2d-4c08-b19f-c8b698b5b3d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae4bdd6656cf5b29f8fd40fcf730f49a6de8f32e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691568"
---
# <a name="rskeymgmt-utility-ssrs"></a><span data-ttu-id="63fd2-102">rskeymgmt 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="63fd2-102">rskeymgmt Utility (SSRS)</span></span>
  <span data-ttu-id="63fd2-103">提取、还原、创建以及删除对称密钥，该密钥用于保护敏感报表服务器数据免受未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="63fd2-103">Extracts, restores, creates, and deletes the symmetric key used to protect sensitive report server data against unauthorized access.</span></span> <span data-ttu-id="63fd2-104">此实用工具还用于将报表服务器实例加入扩展部署。</span><span class="sxs-lookup"><span data-stu-id="63fd2-104">This utility is also used to join report server instances in a scale-out deployment.</span></span> <span data-ttu-id="63fd2-105">报表服务器扩展部署是指共享单个报表服务器数据库的多个报表服务器实例  。</span><span class="sxs-lookup"><span data-stu-id="63fd2-105">A *report server scale-out deployment* refers to multiple report server instances that share a single report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fd2-106">语法</span><span class="sxs-lookup"><span data-stu-id="63fd2-106">Syntax</span></span>  
  
```  
  
      rskeymgmt {-?}  
{-eextract}  
{-aapply}  
{-ddeleteall}  
{-srecreatekey}  
{-rremoveinstancekey}  
{-jjoinfarm}  
{-iinstance}  
{-ffile}  
{-pencryptionpassword}  
{-mremotecomputer}  
{-ninstancenameofremotecomputer}  
{-uadministratoruseraccount}  
{-vadministratorpassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="63fd2-107">参数</span><span class="sxs-lookup"><span data-stu-id="63fd2-107">Arguments</span></span>  
 <span data-ttu-id="63fd2-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="63fd2-108">**-?**</span></span>  
 <span data-ttu-id="63fd2-109">显示 **rskeymgmt** 参数的语法。</span><span class="sxs-lookup"><span data-stu-id="63fd2-109">Displays the syntax of **rskeymgmt** arguments.</span></span>  
  
 <span data-ttu-id="63fd2-110">**-e**</span><span class="sxs-lookup"><span data-stu-id="63fd2-110">**-e**</span></span>  
 <span data-ttu-id="63fd2-111">提取为报表服务器数据加密和解密所用的对称密钥，以便将其复制到文件中。</span><span class="sxs-lookup"><span data-stu-id="63fd2-111">Extracts the symmetric key used to encrypt and decrypt data for the report server instance so that you can copy it to a file.</span></span>  
  
 <span data-ttu-id="63fd2-112">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-112">This argument does not take a value.</span></span> <span data-ttu-id="63fd2-113">但是，您必须在命令行中包含其他参数，才能完成提取。</span><span class="sxs-lookup"><span data-stu-id="63fd2-113">However, you must include additional arguments on the command line to complete the extraction.</span></span> <span data-ttu-id="63fd2-114">您必须指定的参数包括 `-f` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="63fd2-114">The arguments that you must specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="63fd2-115">**-a**</span><span class="sxs-lookup"><span data-stu-id="63fd2-115">**-a**</span></span>  
 <span data-ttu-id="63fd2-116">使用受密码保护的备份文件中提供的副本替换现有对称密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-116">Replaces an existing symmetric key with a copy that you provide in a password protected backup file.</span></span> <span data-ttu-id="63fd2-117">这将会更新对称密钥的所有实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-117">All instances of the symmetric key are updated.</span></span>  
  
 <span data-ttu-id="63fd2-118">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-118">This argument does not take a value.</span></span> <span data-ttu-id="63fd2-119">但是，您必须在命令行中包含其他参数，才能选择包含要应用的密钥的文件。</span><span class="sxs-lookup"><span data-stu-id="63fd2-119">However, you must include additional arguments on the command line to select the file that contains the key to be applied.</span></span> <span data-ttu-id="63fd2-120">您可以指定的参数包括 `-f` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="63fd2-120">The arguments that you can specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="63fd2-121">**-d**</span><span class="sxs-lookup"><span data-stu-id="63fd2-121">**-d**</span></span>  
 <span data-ttu-id="63fd2-122">删除报表服务器数据库中的所有对称密钥实例和所有加密数据。</span><span class="sxs-lookup"><span data-stu-id="63fd2-122">Deletes all symmetric key instances and all encrypted data in a report server database.</span></span> <span data-ttu-id="63fd2-123">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-123">This argument does not take a value.</span></span>  
  
 `-s`  
 <span data-ttu-id="63fd2-124">生成新的对称密钥，并使用新密钥重新加密所有已加密的内容。</span><span class="sxs-lookup"><span data-stu-id="63fd2-124">Generates a new symmetric key and re-encrypts all encrypted content using the new key.</span></span> <span data-ttu-id="63fd2-125">重新生成对称密钥的所有实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-125">All instances of the symmetric key are regenerated.</span></span>  
  
 `-j`  
 <span data-ttu-id="63fd2-126">配置远程报表服务器实例，以共享本地报表服务器实例所用的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="63fd2-126">Configures a remote report server instance to share the report server database that is used by the local report server instance.</span></span>  
  
 <span data-ttu-id="63fd2-127">-r\*\* installationID\*\*  \*\*</span><span class="sxs-lookup"><span data-stu-id="63fd2-127">**-r**  *installationID*</span></span>  
 <span data-ttu-id="63fd2-128">删除特定报表服务器实例的对称密钥信息，从而从扩展部署中删除报表服务器。</span><span class="sxs-lookup"><span data-stu-id="63fd2-128">Removes the symmetric key information for a specific report server instance, thereby removing the report server from a scale-out deployment.</span></span> <span data-ttu-id="63fd2-129">*installationID* 是 RSReportserver.config 文件中的 GUID 值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-129">The *installationID* is a GUID value that can be found in the RSReportserver.config file.</span></span>  
  
 <span data-ttu-id="63fd2-130">`-f`  *文件*</span><span class="sxs-lookup"><span data-stu-id="63fd2-130">`-f`  *file*</span></span>  
 <span data-ttu-id="63fd2-131">指定一个指向存储对称密钥备份副本的文件的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="63fd2-131">Specifies a fully qualified path to the file that stores a backup copy of the symmetric keys.</span></span>  
  
 <span data-ttu-id="63fd2-132">对于 **rskeymgmt -e**，对称密钥将写入你指定的文件中。</span><span class="sxs-lookup"><span data-stu-id="63fd2-132">For **rskeymgmt -e**, the symmetric key is written to the file you specify.</span></span>  
  
 <span data-ttu-id="63fd2-133">对于 **rskeymgmt -a**，存储在该文件中的对称密钥值将应用于报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-133">For **rskeymgmt -a**, the symmetric key value stored in the file is applied to the report server instance.</span></span>  
  
 <span data-ttu-id="63fd2-134">`-p`  *权限*</span><span class="sxs-lookup"><span data-stu-id="63fd2-134">`-p`  *password*</span></span>  
 <span data-ttu-id="63fd2-135">（`-f` 必需）指定用于备份或应用对称密钥的密码。</span><span class="sxs-lookup"><span data-stu-id="63fd2-135">(Required for `-f`) Specifies the password used to back up or apply a symmetric key.</span></span> <span data-ttu-id="63fd2-136">该值不能为空。</span><span class="sxs-lookup"><span data-stu-id="63fd2-136">This value cannot be empty.</span></span>  
  
 `-i`  
 <span data-ttu-id="63fd2-137">指定本地报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-137">Specifies a local report server instance.</span></span> <span data-ttu-id="63fd2-138">如果已在默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中安装了报表服务器，则此参数是可选的（`-i` 的默认值为 MSSQLSERVER）。</span><span class="sxs-lookup"><span data-stu-id="63fd2-138">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-i` is MSSQLSERVER).</span></span> <span data-ttu-id="63fd2-139">如果已按命名实例的形式安装报表服务器，则 `-i` 为必需项。</span><span class="sxs-lookup"><span data-stu-id="63fd2-139">If you installed the report server as a named instance, `-i` is required.</span></span>  
  
 `-m`  
 <span data-ttu-id="63fd2-140">指定远程计算机名称，该计算机将承载加入报表服务器扩展部署的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-140">Specifies the name of the remote computer that hosts the report server instance you are joining to the report server scale-out deployment.</span></span> <span data-ttu-id="63fd2-141">请使用网络中标识该计算机的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="63fd2-141">Use the name of the computer that identifies it on your network.</span></span>  
  
 `-n`  
 <span data-ttu-id="63fd2-142">指定远程计算机上报表服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="63fd2-142">Specifies the name of the report server instance on a remote computer.</span></span> <span data-ttu-id="63fd2-143">如果已在默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中安装了报表服务器，则此参数是可选的（`-n` 的默认值为 MSSQLSERVER）。</span><span class="sxs-lookup"><span data-stu-id="63fd2-143">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-n` is MSSQLSERVER).</span></span> <span data-ttu-id="63fd2-144">如果已按命名实例的形式安装报表服务器，则 `-n` 为必需项。</span><span class="sxs-lookup"><span data-stu-id="63fd2-144">If you installed the report server as a named instance, `-n` is required.</span></span>  
  
 <span data-ttu-id="63fd2-145">`-u`  *用户帐户*</span><span class="sxs-lookup"><span data-stu-id="63fd2-145">`-u`  *useraccount*</span></span>  
 <span data-ttu-id="63fd2-146">指定要加入扩展部署的远程计算机上的管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="63fd2-146">Specifies the administrator account on the remote computer that you are joining to the scale-out deployment.</span></span> <span data-ttu-id="63fd2-147">如果未指定帐户，则使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="63fd2-147">If an account is not specified, the credentials of the current user are used.</span></span>  
  
 <span data-ttu-id="63fd2-148">`-v`  *权限*</span><span class="sxs-lookup"><span data-stu-id="63fd2-148">`-v`  *password*</span></span>  
 <span data-ttu-id="63fd2-149">（`-u` 必需）指定要加入扩展部署的远程计算机上管理员帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="63fd2-149">(Required for `-u`) Specifies the password of an administrator account on the remote computer that you want to join to the scale-out deployment.</span></span>  
  
 <span data-ttu-id="63fd2-150">**-t**  *trace*</span><span class="sxs-lookup"><span data-stu-id="63fd2-150">**-t**  *trace*</span></span>  
 <span data-ttu-id="63fd2-151">将错误消息输出到跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="63fd2-151">Outputs error messages to the trace log.</span></span> <span data-ttu-id="63fd2-152">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-152">This argument does not take a value.</span></span> <span data-ttu-id="63fd2-153">有关详细信息，请参阅 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd2-153">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="63fd2-154">权限</span><span class="sxs-lookup"><span data-stu-id="63fd2-154">Permissions</span></span>  
 <span data-ttu-id="63fd2-155">只有本地管理员才能运行此工具，并且必须在承载报表服务器的计算机本地运行。</span><span class="sxs-lookup"><span data-stu-id="63fd2-155">You must be a local administrator to run the tool, and you must run it locally on the computer that hosts the report server.</span></span> <span data-ttu-id="63fd2-156">rskeymgmt 实用工具用于本地报表服务器 Windows 实例。该实用工具不能连接到远程报表服务器 Windows 服务实例，因此无法用于管理远程报表服务器实例的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-156">The rskeymgmt utility works with the local Report Server Windows instance (the utility cannot connect to remote instances of the Report Server Windows service so it cannot be used to manage the encryption keys of a remote report server instance).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63fd2-157">如果使用 `-u` 和 `-v` 参数，请务必指定在远程计算机中具有管理员权限的帐户。</span><span class="sxs-lookup"><span data-stu-id="63fd2-157">If you are using the `-u` and `-v` arguments, be sure to specify an account that has administrator permissions on the remote computer.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="63fd2-158">示例</span><span class="sxs-lookup"><span data-stu-id="63fd2-158">Examples</span></span>  
 <span data-ttu-id="63fd2-159">以下示例阐释了 **rskeymgmt**的使用方法。</span><span class="sxs-lookup"><span data-stu-id="63fd2-159">The following examples illustrate ways of using **rskeymgmt**.</span></span> <span data-ttu-id="63fd2-160">这些示例将说明如何提取、还原以及删除加密密钥，并显示如何配置报表服务器扩展部署。</span><span class="sxs-lookup"><span data-stu-id="63fd2-160">The following examples show how to extract, restore, and delete encryption keys, and how to configure a report server scale-out deployment.</span></span>  
  
#### <a name="extracting-encryption-keys"></a><span data-ttu-id="63fd2-161">提取加密密钥</span><span class="sxs-lookup"><span data-stu-id="63fd2-161">Extracting Encryption Keys</span></span>  
 <span data-ttu-id="63fd2-162">此示例显示如何创建加密密钥备份副本，并将其保存到软盘中密码保护的文件中。</span><span class="sxs-lookup"><span data-stu-id="63fd2-162">This example shows how to create a backup copy of the encryption key and save it to a password-protected file on a floppy disk.</span></span> <span data-ttu-id="63fd2-163">如果报表服务器是作为命名实例安装的，则添加 `-i` 参数。</span><span class="sxs-lookup"><span data-stu-id="63fd2-163">If the report server is installed as a named instance, add the `-i` argument.</span></span>  
  
```  
rskeymgmt -e -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="restoring-encryption-keys"></a><span data-ttu-id="63fd2-164">还原加密密钥</span><span class="sxs-lookup"><span data-stu-id="63fd2-164">Restoring Encryption Keys</span></span>  
 <span data-ttu-id="63fd2-165">此示例显示如何替换加密密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-165">This example shows how to replace the encryption key.</span></span> <span data-ttu-id="63fd2-166">您必须指定密钥备份副本的位置以及该文件的解锁密码。</span><span class="sxs-lookup"><span data-stu-id="63fd2-166">You must specify the location of the backup copy of the key and the password that unlocks the file.</span></span>  
  
```  
rskeymgmt -a -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="deleting-encryption-keys-and-encrypted-content"></a><span data-ttu-id="63fd2-167">删除加密密钥和加密的内容</span><span class="sxs-lookup"><span data-stu-id="63fd2-167">Deleting Encryption Keys and Encrypted Content</span></span>  
 <span data-ttu-id="63fd2-168">此示例显示如何删除报表服务器中存储的所有加密密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-168">This example shows how to delete all encryption keys stored in a report server.</span></span> <span data-ttu-id="63fd2-169">如果安装的是报表服务器扩展部署，则将删除部署中包括的所有报表服务器实例的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-169">If your installation is a report server scale-out deployment, the encryption keys for all report server instances that are included in the deployment will be deleted.</span></span> <span data-ttu-id="63fd2-170">删除加密密钥还会删除报表服务器数据库中现有的全部已加密值。</span><span class="sxs-lookup"><span data-stu-id="63fd2-170">Deleting an encryption key also deletes any existing encrypted values in the report server database.</span></span> <span data-ttu-id="63fd2-171">有关加密内容的详细信息，请参阅[存储加密的报表服务器数据（SSRS 配置管理器）](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd2-171">For more information about encrypted content, see [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md).</span></span>  
  
```  
rskeymgmt -d  
```  
  
#### <a name="joining-a-remote-report-server-named-instance-to-a-scale-out-deployment"></a><span data-ttu-id="63fd2-172">将远程报表服务器命名实例加入扩展部署</span><span class="sxs-lookup"><span data-stu-id="63fd2-172">Joining a Remote Report Server Named Instance to a Scale-out Deployment</span></span>  
 <span data-ttu-id="63fd2-173">此示例显示如何将远程计算机上安装的报表服务器实例添加到报表服务器扩展部署中。</span><span class="sxs-lookup"><span data-stu-id="63fd2-173">This example shows how to add a report server instance that is installed on a remote computer to a report server scale-out deployment.</span></span> <span data-ttu-id="63fd2-174">您必须在已配置为使用共享数据库的某台计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="63fd2-174">You must run the command on one of the computers that is already configured to use the shared database.</span></span> <span data-ttu-id="63fd2-175">命令参数指定了要加入到扩展部署的远程报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-175">The command arguments specify the remote report server instance you want to join to the scale-out deployment.</span></span>  
  
```  
rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="63fd2-176">报表服务器扩展部署是指多个报表服务器实例共享同一报表服务器数据库的部署模型。</span><span class="sxs-lookup"><span data-stu-id="63fd2-176">A report server scale-out deployment refers to a deployment model where multiple report server instances share the same report server database.</span></span> <span data-ttu-id="63fd2-177">任何报表服务器实例，只要将其对称密钥存储在一个报表服务器数据库中，就可以使用该数据库。</span><span class="sxs-lookup"><span data-stu-id="63fd2-177">A report server database can be used by any report server instance that stores its symmetric keys in the database.</span></span> <span data-ttu-id="63fd2-178">例如，如果报表服务器数据库包含三个报表服务器实例的密钥信息，则所有这三个实例均被视为同一扩展部署的成员。</span><span class="sxs-lookup"><span data-stu-id="63fd2-178">For example, if a report server database contains key information for three report server instances, all three instances are considered to members of the same scale-out deployment.</span></span>  
  
#### <a name="joining-report-server-instances-on-the-same-computer"></a><span data-ttu-id="63fd2-179">联接同一台计算机上的报表服务器实例</span><span class="sxs-lookup"><span data-stu-id="63fd2-179">Joining Report Server Instances on the Same Computer</span></span>  
 <span data-ttu-id="63fd2-180">可以从安装在同一台计算机上的多个报表服务器实例创建扩展部署。</span><span class="sxs-lookup"><span data-stu-id="63fd2-180">You can create a scale-out deployment from multiple report server instances that are installed on the same computer.</span></span> <span data-ttu-id="63fd2-181">如果要联接本地安装的报表服务器实例，请不要设置 `-u` 和 `-v` 参数。</span><span class="sxs-lookup"><span data-stu-id="63fd2-181">Do not set the `-u` and `-v` arguments if you are joining report server instances that are installed locally.</span></span> <span data-ttu-id="63fd2-182">仅当联接远程计算机中的实例时才需使用 `-u` 和 `-v` 参数。</span><span class="sxs-lookup"><span data-stu-id="63fd2-182">The `-u` and `-v` arguments are used only when you are joining an instance from a remote computer.</span></span> <span data-ttu-id="63fd2-183">如果指定这些参数，您将收到以下错误：“用户凭据不能用于本地连接”。</span><span class="sxs-lookup"><span data-stu-id="63fd2-183">If you specify the arguments, you will get the following error: "User credentials cannot be used for local connections."</span></span>  
  
 <span data-ttu-id="63fd2-184">以下示例说明了使用多个本地实例创建扩展部署的语法。</span><span class="sxs-lookup"><span data-stu-id="63fd2-184">The following example illustrates the syntax for creating a scale-out deployment using multiple local instances.</span></span> <span data-ttu-id="63fd2-185">在此示例中，<`initializedinstance`> 是已初始化为使用 Report Server 数据库的实例的名称，而 <`newinstance`> 是要添加到部署中的实例的名称：</span><span class="sxs-lookup"><span data-stu-id="63fd2-185">In this example, <`initializedinstance`> is the name of an instance that is already initialized to use the report server database, and <`newinstance`> is the name of the instance that you want to add to the deployment:</span></span>  
  
```  
rskeymgmt -j -i <initializedinstance> -m <computer name> -n <newinstance>  
```  
  
#### <a name="removing-encryption-keys-for-a-single-report-server-in-a-scale-out-deployment"></a><span data-ttu-id="63fd2-186">删除扩展部署中单个报表服务器的加密密钥</span><span class="sxs-lookup"><span data-stu-id="63fd2-186">Removing Encryption Keys for a Single Report Server in a Scale-out Deployment</span></span>  
 <span data-ttu-id="63fd2-187">此示例显示如何删除报表服务器扩展部署中单个报表服务器的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-187">This example shows how to remove the encryption keys for a single report server in a report server scale-out deployment.</span></span> <span data-ttu-id="63fd2-188">将从报表服务器数据库中删除密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-188">The keys are removed from the report server database.</span></span> <span data-ttu-id="63fd2-189">一旦报表服务器实例的密钥被删除，该报表服务器实例便不再能访问该数据库中的加密数据，这就意味着已将其从扩展部署中有效删除。</span><span class="sxs-lookup"><span data-stu-id="63fd2-189">Once the keys for that report server instance are removed, that report server instance can no longer access encrypted data in the database, effectively removing it from the scale-out deployment.</span></span>  
  
 <span data-ttu-id="63fd2-190">从扩展部署中删除报表服务器实例要求您指定安装 ID。</span><span class="sxs-lookup"><span data-stu-id="63fd2-190">Removing a report server instance from a scale-out deployment requires you to specify an installation ID.</span></span> <span data-ttu-id="63fd2-191">安装 ID 是 GUID，它存储在要删除其加密密钥的报表服务器实例的 RSReportserver.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="63fd2-191">The installation ID is a GUID stored in the RSReportserver.config file of the report server instance for which you want to remove encryption keys.</span></span> <span data-ttu-id="63fd2-192">您必须在要从扩展部署中删除的计算机上运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="63fd2-192">You must run the following command on the computer that you want to remove from the scale-out deployment.</span></span> <span data-ttu-id="63fd2-193">如果报表服务器作为命名实例安装，则可使用 `-i` 参数指定实例。</span><span class="sxs-lookup"><span data-stu-id="63fd2-193">If the report server is installed as a named instance, use the `-i` argument to specify the instance.</span></span> <span data-ttu-id="63fd2-194">有关详细信息，请参阅 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd2-194">For more information, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
```  
rskeymgmt -r <installationID>  
```  
  
## <a name="file-location"></a><span data-ttu-id="63fd2-195">文件位置</span><span class="sxs-lookup"><span data-stu-id="63fd2-195">File Location</span></span>  
 <span data-ttu-id="63fd2-196">Rskeymgmt.exe 位于\*\* \<*drive*> ： \PROGRAM Files\Microsoft sql Server\110\Tools\Binn**或 At \*\* \<*drive*> ： \Program FILES (x86) \microsoft SQL Server\110\Tools\Binn**。</span><span class="sxs-lookup"><span data-stu-id="63fd2-196">Rskeymgmt.exe is located at **\<*drive*>:\Program Files\Microsoft SQL Server\110\Tools\Binn** or at **\<*drive*>:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="63fd2-197">可以在文件系统的任何文件夹中运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="63fd2-197">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63fd2-198">备注</span><span class="sxs-lookup"><span data-stu-id="63fd2-198">Remarks</span></span>  
 <span data-ttu-id="63fd2-199">报表服务器对存储的凭据和连接信息进行加密。</span><span class="sxs-lookup"><span data-stu-id="63fd2-199">A report server encrypts stored credentials and connection information.</span></span> <span data-ttu-id="63fd2-200">公钥和对称密钥可用于对数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="63fd2-200">A public key and a symmetric key are used to encrypt data.</span></span> <span data-ttu-id="63fd2-201">要运行报表服务器，报表服务器数据库必须具有有效的密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-201">A report server database must have valid keys in order for the report server to run.</span></span> <span data-ttu-id="63fd2-202">你可以使用 **rskeymgmt** 来备份、删除或还原密钥。</span><span class="sxs-lookup"><span data-stu-id="63fd2-202">You can use **rskeymgmt** to back up, delete, or restore the keys.</span></span> <span data-ttu-id="63fd2-203">如果无法还原密钥，此工具将为您提供一种方法，以删除不再使用的加密内容。</span><span class="sxs-lookup"><span data-stu-id="63fd2-203">If the keys cannot be restored, this tool provides a way to delete encrypted content that can no longer be used.</span></span>  
  
 <span data-ttu-id="63fd2-204">**rskeymgmt** 实用工具用于管理在安装或初始化期间定义的密钥集。</span><span class="sxs-lookup"><span data-stu-id="63fd2-204">The **rskeymgmt** utility is used to manage the key set that is defined during Setup or during initialization.</span></span> <span data-ttu-id="63fd2-205">它通过远程过程调用 (RPC) 端点连接到本地报表服务器 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="63fd2-205">It connects to the local Report Server Windows service through a Remote Procedure Call (RPC) endpoint.</span></span> <span data-ttu-id="63fd2-206">必须运行报表服务器 Windows 服务才能使用此实用工具。</span><span class="sxs-lookup"><span data-stu-id="63fd2-206">The Report Server Windows service must be running in order for this utility to work.</span></span>  
  
 <span data-ttu-id="63fd2-207">有关加密密钥的详细信息，请参阅[配置和管理加密密钥（SSRS 配置管理器）](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)和[初始化报表服务器（SSRS 配置管理器）](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd2-207">For more information about the encryption keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) and [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fd2-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63fd2-208">See Also</span></span>  
 <span data-ttu-id="63fd2-209">[&#40;SSRS Configuration Manager 配置本机模式报表服务器扩展部署&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="63fd2-209">[Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="63fd2-210">[Reporting Services 报表服务器（本机模式）](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="63fd2-210">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="63fd2-211">[报表服务器命令提示实用工具 &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="63fd2-211">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="63fd2-212">配置和管理加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="63fd2-212">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
