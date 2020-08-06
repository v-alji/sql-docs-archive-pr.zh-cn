---
title: 配置事件通知的对话安全设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], security
ms.assetid: 12afbc84-2d2a-4452-935e-e1c70e8c53c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d83bfe63c3a9b24c2be8d08916dd2384c59edc93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589474"
---
# <a name="configure-dialog-security-for-event-notifications"></a><span data-ttu-id="34e98-102">配置事件通知的对话安全模式</span><span class="sxs-lookup"><span data-stu-id="34e98-102">Configure Dialog Security for Event Notifications</span></span>
  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="34e98-103">对话安全模式。</span><span class="sxs-lookup"><span data-stu-id="34e98-103">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="34e98-104">必须按照 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 对话完全安全模式手动配置对话安全模式。</span><span class="sxs-lookup"><span data-stu-id="34e98-104">Dialog security must be manually configured according to the [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog full-security model.</span></span> <span data-ttu-id="34e98-105">完全安全模式可以为在远程服务器之间发送的消息启用加密和解密功能。</span><span class="sxs-lookup"><span data-stu-id="34e98-105">The full-security model enables encryption and decryption of messages that are sent to and from remote servers.</span></span> <span data-ttu-id="34e98-106">虽然事件通知单向发送，但其他消息（例如错误）也会从相反的方向返回。</span><span class="sxs-lookup"><span data-stu-id="34e98-106">Although event notifications are sent in one direction, other messages, such as errors, are also returned in the opposite direction.</span></span>  
  
## <a name="configuring-dialog-security-for-event-notifications"></a><span data-ttu-id="34e98-107">配置事件通知的对话安全模式</span><span class="sxs-lookup"><span data-stu-id="34e98-107">Configuring Dialog Security for Event Notifications</span></span>  
 <span data-ttu-id="34e98-108">下面的步骤中介绍了针对事件通知实现对话安全模式所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="34e98-108">The process required to implement dialog security for event notification is described in the following steps.</span></span> <span data-ttu-id="34e98-109">这些步骤包括同时在源服务器和目标服务器中执行的操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-109">These steps include actions to take on both the source server and the target server.</span></span> <span data-ttu-id="34e98-110">源服务器是创建事件通知的服务器。</span><span class="sxs-lookup"><span data-stu-id="34e98-110">The source server is the server on which the event notification is being created.</span></span> <span data-ttu-id="34e98-111">目标服务器是接收事件通知消息的服务器。</span><span class="sxs-lookup"><span data-stu-id="34e98-111">The target server is the server that receives the event notification message.</span></span> <span data-ttu-id="34e98-112">在继续执行下一个步骤之前，必须针对源服务器和目标服务器完成每一个步骤中的操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-112">You must complete the actions in each step for both the source server and the target server before you continue to the next step.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34e98-113">所有证书的创建都必须使用有效的开始日期和过期日期。</span><span class="sxs-lookup"><span data-stu-id="34e98-113">All certificates must be created with valid start and expiration dates.</span></span>  
  
 <span data-ttu-id="34e98-114">**步骤 1：建立 TCP 端口号和目标服务名称。**</span><span class="sxs-lookup"><span data-stu-id="34e98-114">**Step 1: Establish a TCP port number and target service name.**</span></span>  
  
 <span data-ttu-id="34e98-115">建立源服务器和目标服务器接收消息所用的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="34e98-115">Establish the TCP port on which both the source server and the target server will receive messages.</span></span> <span data-ttu-id="34e98-116">同时，必须确定目标服务的名称。</span><span class="sxs-lookup"><span data-stu-id="34e98-116">You must also determine the name of the target service.</span></span>  
  
 <span data-ttu-id="34e98-117">**步骤 2：配置数据库级身份验证的加密和证书共享。**</span><span class="sxs-lookup"><span data-stu-id="34e98-117">**Step 2: Configure encryption and certificate sharing for database-level authentication.**</span></span>  
  
 <span data-ttu-id="34e98-118">同时在源服务器和目标服务器中完成下列操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-118">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="34e98-119">源服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-119">Source server</span></span>|<span data-ttu-id="34e98-120">目标服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-120">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="34e98-121">选择或创建一个数据库以包含事件通知和主密钥。</span><span class="sxs-lookup"><span data-stu-id="34e98-121">Choose or create a database to hold the event notification and master key.</span></span>|<span data-ttu-id="34e98-122">选择或创建一个数据库以包含主密钥。</span><span class="sxs-lookup"><span data-stu-id="34e98-122">Choose or create a database to hold the master key.</span></span>|  
|<span data-ttu-id="34e98-123">如果没有用于源数据库的主密钥，则 [创建主密钥](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34e98-123">If no master key exists for the source database, [create a master key](/sql/t-sql/statements/create-master-key-transact-sql).</span></span> <span data-ttu-id="34e98-124">源数据库和目标数据库都需要主密钥来保护它们各自的证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-124">A master key is required on both the source and target databases to help secure their respective certificates.</span></span>|<span data-ttu-id="34e98-125">如果没有用于目标数据库的主密钥，则创建主密钥。</span><span class="sxs-lookup"><span data-stu-id="34e98-125">If no master key exists for the target database, create a master key.</span></span>|  
|<span data-ttu-id="34e98-126">为源数据库[创建登录名](/sql/t-sql/statements/create-login-transact-sql) 和相应的 [用户](/sql/t-sql/statements/create-user-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="34e98-126">[Create a login](/sql/t-sql/statements/create-login-transact-sql) and a corresponding [user](/sql/t-sql/statements/create-user-transact-sql) for the source database.</span></span>|<span data-ttu-id="34e98-127">为目标数据库创建登录名和相应的用户。</span><span class="sxs-lookup"><span data-stu-id="34e98-127">Create a login and a corresponding user for the target database.</span></span>|  
|<span data-ttu-id="34e98-128">为源数据库的用户[创建证书](/sql/t-sql/statements/create-certificate-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="34e98-128">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) that is owned by the user of the source database.</span></span>|<span data-ttu-id="34e98-129">创建属于目标数据库的用户的证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-129">Create a certificate that is owned by the user of the target database.</span></span>|  
|<span data-ttu-id="34e98-130">在目标服务器可以访问的文件中[备份证书](/sql/t-sql/statements/backup-certificate-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="34e98-130">[Back up the certificate](/sql/t-sql/statements/backup-certificate-transact-sql) to a file that can be accessed by the target server.</span></span>|<span data-ttu-id="34e98-131">将证书备份到可以由源服务器访问的文件。</span><span class="sxs-lookup"><span data-stu-id="34e98-131">Back up the certificate to a file that can be accessed by the source server.</span></span>|  
|<span data-ttu-id="34e98-132">[创建用户](/sql/t-sql/statements/create-user-transact-sql)，指定目标数据库的用户和 WITHOUT LOGIN。</span><span class="sxs-lookup"><span data-stu-id="34e98-132">[Create a user](/sql/t-sql/statements/create-user-transact-sql), specifying the user of the target database, and WITHOUT LOGIN.</span></span> <span data-ttu-id="34e98-133">此用户将拥有要通过备份文件创建的目标数据库证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-133">This user will own the target database certificate to be created from the backup file.</span></span> <span data-ttu-id="34e98-134">用户不必映射到登录名，因为此用户的唯一目的是拥有在下面的步骤 3 中创建的目标数据库证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-134">The user does not have to be mapped to a login, because the only purpose of this user is to own the target database certificate created in step 3 that follows.</span></span>|<span data-ttu-id="34e98-135">创建用户，指定源数据库的用户和 WITHOUT LOGIN。</span><span class="sxs-lookup"><span data-stu-id="34e98-135">Create a user, specifying the user of the source database, and WITHOUT LOGIN.</span></span> <span data-ttu-id="34e98-136">此用户将拥有要通过备份文件创建的源数据库证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-136">This user will own the source database certificate to be created from the backup file.</span></span> <span data-ttu-id="34e98-137">用户不必映射到登录名，因为此用户的唯一目的是拥有在下面的步骤 3 中创建的源数据库证书。</span><span class="sxs-lookup"><span data-stu-id="34e98-137">The user does not have to be mapped to a login, because the only purpose of this user is to own the source database certificate created in step 3 that follows.</span></span>|  
  
 <span data-ttu-id="34e98-138">**步骤 3：共享证书并授予数据库级身份验证的权限。**</span><span class="sxs-lookup"><span data-stu-id="34e98-138">**Step 3: Share certificates and grant permissions for database-level authentication.**</span></span>  
  
 <span data-ttu-id="34e98-139">同时在源服务器和目标服务器中完成下列操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-139">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="34e98-140">源服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-140">Source server</span></span>|<span data-ttu-id="34e98-141">目标服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-141">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="34e98-142">通过目标证书的备份文件[创建证书](/sql/t-sql/statements/create-certificate-transact-sql) ，将目标数据库用户指定为所有者。</span><span class="sxs-lookup"><span data-stu-id="34e98-142">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) from the backup file of the target certificate, specifying the target database user as the owner.</span></span>|<span data-ttu-id="34e98-143">通过源证书的备份文件创建证书，将源数据库用户指定为所有者。</span><span class="sxs-lookup"><span data-stu-id="34e98-143">Create a certificate from the backup file of the source certificate, specifying the source database user as the owner.</span></span>|  
|<span data-ttu-id="34e98-144">向源数据库用户[授予权限](/sql/t-sql/statements/grant-transact-sql) 以创建事件通知。</span><span class="sxs-lookup"><span data-stu-id="34e98-144">[Grant permission](/sql/t-sql/statements/grant-transact-sql) to create the event notification to the source database user.</span></span> <span data-ttu-id="34e98-145">有关此权限的详细信息，请参阅 [CREATE EVENT NOTIFICATION (Transact-SQL)](/sql/t-sql/statements/create-event-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34e98-145">For more information about this permission, see [CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-notification-transact-sql).</span></span>|<span data-ttu-id="34e98-146">向目标数据库用户授予对现有事件通知 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 的 REFERENCES 权限，请访问 `https://schemas.microsoft.com/SQL/Notifications/PostEventNotification`。</span><span class="sxs-lookup"><span data-stu-id="34e98-146">Grant REFERENCES permission to the target database user on the existing event notifications [!INCLUDE[ssSB](../../includes/sssb-md.md)] contract: `https://schemas.microsoft.com/SQL/Notifications/PostEventNotification`.</span></span>|  
|<span data-ttu-id="34e98-147">为目标服务[创建远程服务绑定](/sql/t-sql/statements/create-remote-service-binding-transact-sql) 并指定目标数据库用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="34e98-147">[Create a remote service binding](/sql/t-sql/statements/create-remote-service-binding-transact-sql) to the target service and specify the credentials of the target database user.</span></span> <span data-ttu-id="34e98-148">远程服务绑定可以保证，源数据库用户所拥有的证书中的公钥将验证发送到目标服务器的消息。</span><span class="sxs-lookup"><span data-stu-id="34e98-148">The remote service binding guarantees that the public key in the certificate owned by the source database user will authenticate messages that are sent to the target server.</span></span>|<span data-ttu-id="34e98-149">向目标数据库用户[授予](/sql/t-sql/statements/grant-transact-sql) CREATE QUEUE、CREATE SERVICE 和 CREATE SCHEMA 权限。</span><span class="sxs-lookup"><span data-stu-id="34e98-149">[Grant](/sql/t-sql/statements/grant-transact-sql) CREATE QUEUE, CREATE SERVICE, and CREATE SCHEMA permissions to the target database user.</span></span>|  
||<span data-ttu-id="34e98-150">如果仍未以目标数据库用户身份连接到数据库，则立即执行此操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-150">If not already connected to the database as the target database user, do so now.</span></span>|  
||<span data-ttu-id="34e98-151">[创建队列](/sql/t-sql/statements/create-queue-transact-sql) 以接收事件通知消息，并 [创建服务](/sql/t-sql/statements/create-service-transact-sql) 以传递消息。</span><span class="sxs-lookup"><span data-stu-id="34e98-151">[Create a queue](/sql/t-sql/statements/create-queue-transact-sql) to receive the event notification messages and [create a service](/sql/t-sql/statements/create-service-transact-sql) to deliver the messages.</span></span>|  
||<span data-ttu-id="34e98-152">向源数据库用户[授予 SEND 权限](/sql/t-sql/statements/grant-transact-sql) ，此权限将针对目标服务。</span><span class="sxs-lookup"><span data-stu-id="34e98-152">[Grant SEND permission](/sql/t-sql/statements/grant-transact-sql) on the target service to the source database user.</span></span>|  
|<span data-ttu-id="34e98-153">向目标服务器提供源数据库的 Service Broker 标识符。</span><span class="sxs-lookup"><span data-stu-id="34e98-153">Provide the service broker identifier of the source database to the target server.</span></span> <span data-ttu-id="34e98-154">此标识符可以通过查询 **sys.databases** 目录视图的 [service_broker_guid](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列而获得。</span><span class="sxs-lookup"><span data-stu-id="34e98-154">This identifier can be obtained by querying the **service_broker_guid** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span> <span data-ttu-id="34e98-155">对于服务器级事件通知，请使用 **msdb**的 Service Broker 标识符。</span><span class="sxs-lookup"><span data-stu-id="34e98-155">For a server-level event notification, use the service broker identifier of **msdb**.</span></span>|<span data-ttu-id="34e98-156">向源服务器提供目标数据库的 Service Broker 标识符。</span><span class="sxs-lookup"><span data-stu-id="34e98-156">Provide the service broker identifier of the target database to the source server.</span></span>|  
  
 <span data-ttu-id="34e98-157">**步骤 4：创建路由并设置服务器级身份验证。**</span><span class="sxs-lookup"><span data-stu-id="34e98-157">**Step 4: Create routes and set up server-level authentication.**</span></span>  
  
 <span data-ttu-id="34e98-158">同时在源服务器和目标服务器中完成下列操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-158">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="34e98-159">源服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-159">Source server</span></span>|<span data-ttu-id="34e98-160">目标服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-160">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="34e98-161">为目标服务[创建路由](/sql/t-sql/statements/create-route-transact-sql) ，并指定目标数据库的 Service Broker 标识符和一致的 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="34e98-161">[Create a route](/sql/t-sql/statements/create-route-transact-sql) to the target service, and specify the service broker identifier of the target database and the agreed-upon TCP port number.</span></span>|<span data-ttu-id="34e98-162">创建到源服务的路由，并指定源数据库的 Service Broker 标识符和一致的 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="34e98-162">Create a route to the source service, and specify the service broker identifier of the source database and the agreed-upon TCP port number.</span></span> <span data-ttu-id="34e98-163">若要指定源服务，请使用下面提供的服务： `https://schemas.microsoft.com/SQL/Notifications/EventNotificationService`。</span><span class="sxs-lookup"><span data-stu-id="34e98-163">To specify the source service, use the following supplied service: `https://schemas.microsoft.com/SQL/Notifications/EventNotificationService`.</span></span>|  
|<span data-ttu-id="34e98-164">切换到 **master** 数据库以配置服务器级身份验证。</span><span class="sxs-lookup"><span data-stu-id="34e98-164">Switch to the **master** database to configure server-level authentication.</span></span>|<span data-ttu-id="34e98-165">切换到 **master** 数据库以配置服务器级身份验证。</span><span class="sxs-lookup"><span data-stu-id="34e98-165">Switch to the **master** database to configure server-level authentication.</span></span>|  
|<span data-ttu-id="34e98-166">如果没有用于 **master** 数据库的主密钥，则 [创建主密钥](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34e98-166">If no master key exists for the **master** database, [create a master key](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>|<span data-ttu-id="34e98-167">如果没有用于 **master** 数据库的主密钥，则创建主密钥。</span><span class="sxs-lookup"><span data-stu-id="34e98-167">If no master key exists for the **master** database, create a master key.</span></span>|  
|<span data-ttu-id="34e98-168">[创建证书](/sql/t-sql/statements/create-certificate-transact-sql) ，以对数据库进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="34e98-168">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) that authenticates the database.</span></span>|<span data-ttu-id="34e98-169">创建证书，以对数据库进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="34e98-169">Create a certificate that authenticates the database.</span></span>|  
|<span data-ttu-id="34e98-170">在目标服务器可以访问的文件中[备份证书](/sql/t-sql/statements/backup-certificate-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="34e98-170">[Back up the certificate](/sql/t-sql/statements/backup-certificate-transact-sql) to a file that can be accessed by the target server.</span></span>|<span data-ttu-id="34e98-171">将证书备份到可以由源服务器访问的文件。</span><span class="sxs-lookup"><span data-stu-id="34e98-171">Back up the certificate to a file that can be accessed by the source server.</span></span>|  
|<span data-ttu-id="34e98-172">[创建端点](/sql/t-sql/statements/create-endpoint-transact-sql)，并指定一致的 TCP 端口号 FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*) 和身份验证证书的名称。</span><span class="sxs-lookup"><span data-stu-id="34e98-172">[Create an endpoint](/sql/t-sql/statements/create-endpoint-transact-sql), and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.</span></span>|<span data-ttu-id="34e98-173">创建端点，并指定一致的 TCP 端口号 FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*) 和身份验证证书的名称。</span><span class="sxs-lookup"><span data-stu-id="34e98-173">Create an endpoint, and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.</span></span>|  
|<span data-ttu-id="34e98-174">[创建登录名](/sql/t-sql/statements/create-login-transact-sql)，并指定目标服务器的登录名。</span><span class="sxs-lookup"><span data-stu-id="34e98-174">[Create a login](/sql/t-sql/statements/create-login-transact-sql), and specify the login of the target server.</span></span>|<span data-ttu-id="34e98-175">创建登录名，并指定源服务器的登录名。</span><span class="sxs-lookup"><span data-stu-id="34e98-175">Create a login, and specify the login of the source server.</span></span>|  
|<span data-ttu-id="34e98-176">向目标验证器登录名[授予 CONNECT 权限](/sql/t-sql/statements/grant-transact-sql) ，此权限针对端点。</span><span class="sxs-lookup"><span data-stu-id="34e98-176">[Grant CONNECT permission](/sql/t-sql/statements/grant-transact-sql) on the endpoint to the target authenticator login.</span></span>|<span data-ttu-id="34e98-177">向源验证器登录名授予对端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="34e98-177">Grant CONNECT permission on the endpoint to the source authenticator login.</span></span>|  
|<span data-ttu-id="34e98-178">[创建用户](/sql/t-sql/statements/create-user-transact-sql)，并指定目标验证器登录名。</span><span class="sxs-lookup"><span data-stu-id="34e98-178">[Create a user](/sql/t-sql/statements/create-user-transact-sql), and specify the target authenticator login.</span></span>|<span data-ttu-id="34e98-179">创建用户，并指定源验证器登录名。</span><span class="sxs-lookup"><span data-stu-id="34e98-179">Create a user, and specify the source authenticator login.</span></span>|  
  
 <span data-ttu-id="34e98-180">**步骤 5：共享服务器级身份验证证书并创建事件通知。**</span><span class="sxs-lookup"><span data-stu-id="34e98-180">**Step 5: Share certificates for server-level authentication and create the event notification.**</span></span>  
  
 <span data-ttu-id="34e98-181">同时在源服务器和目标服务器中完成下列操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-181">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="34e98-182">源服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-182">Source server</span></span>|<span data-ttu-id="34e98-183">目标服务器</span><span class="sxs-lookup"><span data-stu-id="34e98-183">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="34e98-184">通过目标证书的备份文件[创建证书](/sql/t-sql/statements/create-certificate-transact-sql) ，将目标验证器用户指定为所有者。</span><span class="sxs-lookup"><span data-stu-id="34e98-184">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) from the backup file of the target certificate, specifying the target authenticator user as the owner.</span></span>|<span data-ttu-id="34e98-185">通过源证书的备份文件创建证书，将源验证器用户指定为所有者。</span><span class="sxs-lookup"><span data-stu-id="34e98-185">Create a certificate from the backup file of the source certificate, specifying the source authenticator user as the owner.</span></span>|  
|<span data-ttu-id="34e98-186">切换到在其中创建事件通知的源数据库，如果仍未以源数据库用户身份连接，则立即执行此操作。</span><span class="sxs-lookup"><span data-stu-id="34e98-186">Switch to the source database on which to create the event notification, and if you are not already connected as the source database user, do so now.</span></span>|<span data-ttu-id="34e98-187">切换到目标数据库以接收事件通知消息。</span><span class="sxs-lookup"><span data-stu-id="34e98-187">Switch to the target database to receive event notification messages.</span></span>|  
|<span data-ttu-id="34e98-188">[创建事件通知](/sql/t-sql/statements/create-event-notification-transact-sql)，并指定目标数据库的 Broker Service 和标识符。</span><span class="sxs-lookup"><span data-stu-id="34e98-188">[Create the event notification](/sql/t-sql/statements/create-event-notification-transact-sql), and specify the broker service and identifier of the target database.</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="34e98-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34e98-189">See Also</span></span>  
 <span data-ttu-id="34e98-190">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-190">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="34e98-191">[BACKUP CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/backup-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-191">[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql) </span></span>  
 <span data-ttu-id="34e98-192">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-192">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="34e98-193">[加密层次结构](../security/encryption/encryption-hierarchy.md) </span><span class="sxs-lookup"><span data-stu-id="34e98-193">[Encryption Hierarchy](../security/encryption/encryption-hierarchy.md) </span></span>  
 <span data-ttu-id="34e98-194">[实现事件通知](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="34e98-194">[Implement Event Notifications](event-notifications.md) </span></span>  
 <span data-ttu-id="34e98-195">[CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-195">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="34e98-196">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-196">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="34e98-197">[CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-197">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="34e98-198">[CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-198">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="34e98-199">[CREATE REMOTE SERVICE BINDING (Transact-SQL)](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-199">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="34e98-200">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-200">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="34e98-201">[CREATE ROUTE (Transact SQL)](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-201">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="34e98-202">[CREATE QUEUE (Transact SQL)](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-202">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="34e98-203">[CREATE SERVICE (Transact SQL)](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-203">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="34e98-204">[CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34e98-204">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 [<span data-ttu-id="34e98-205">CREATE EVENT NOTIFICATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="34e98-205">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
  