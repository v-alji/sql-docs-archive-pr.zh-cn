---
title: 将 PowerPivot 解决方案部署到 SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588711"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a><span data-ttu-id="4648f-102">将 PowerPivot 解决方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="4648f-102">Deploy PowerPivot Solutions to SharePoint</span></span>
  <span data-ttu-id="4648f-103">使用以下说明可手动部署两个解决方案包，这两个解决方案包将 PowerPivot 功能添加到 SharePoint Server 2010 环境。</span><span class="sxs-lookup"><span data-stu-id="4648f-103">Use the following instructions to manually deploy two solution packages that add PowerPivot features to a SharePoint Server 2010 environment.</span></span> <span data-ttu-id="4648f-104">部署解决方案是在 SharePoint 2010 服务器上配置 PowerPivot for SharePoint 所必需的步骤。</span><span class="sxs-lookup"><span data-stu-id="4648f-104">Deploying the solutions is a required step for configuring PowerPivot for SharePoint on a SharePoint 2010 server.</span></span> <span data-ttu-id="4648f-105">若要查看所需步骤的完整列表，请参阅[在管理中心中管理和配置 PowerPivot 服务器](power-pivot-server-administration-and-configuration-in-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="4648f-105">To view the complete list of required steps, see [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md).</span></span>  
  
 <span data-ttu-id="4648f-106">或者，您可以使用 PowerPivot 配置工具来部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-106">Alternatively, you can use the PowerPivot Configuration Tool to deploy the solutions.</span></span> <span data-ttu-id="4648f-107">对于单服务器部署来说，使用配置工具更为容易且效率更高，但如果您喜欢使用熟悉的工具或者同时配置多个功能，则最好使用管理中心和 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4648f-107">Using the configuration tool is easier and more efficient for a single server installation, but you might want to use Central Administration and PowerShell if you prefer using a familiar tool or if you are configuring multiple features at the same time.</span></span> <span data-ttu-id="4648f-108">有关使用配置工具的详细信息，请参阅[PowerPivot 配置工具](power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4648f-108">For more information about using the configuration tool, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
 <span data-ttu-id="4648f-109">在部署解决方案之前，必须首先使用 SQL Server 2012 安装介质安装 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="4648f-109">Before deploying the solutions, you must first install PowerPivot for SharePoint using the SQL Server 2012 installation media.</span></span> <span data-ttu-id="4648f-110">SQL Server 安装程序将会安装您要部署的解决方案包。</span><span class="sxs-lookup"><span data-stu-id="4648f-110">SQL Server Setup installs the solution packages that you are about to deploy.</span></span>  
  
 <span data-ttu-id="4648f-111">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="4648f-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="4648f-112">先决条件：验证 Web 应用程序是否使用经典模式身份验证</span><span class="sxs-lookup"><span data-stu-id="4648f-112">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>](#bkmk_classic)  
  
 [<span data-ttu-id="4648f-113">步骤 1：部署场解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-113">Step 1: Deploy the Farm Solution</span></span>](#bkmk_farm)  
  
 [<span data-ttu-id="4648f-114">步骤 2: 将 PowerPivot Web 应用程序解决方案部署到管理中心</span><span class="sxs-lookup"><span data-stu-id="4648f-114">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>](#deployCA)  
  
 [<span data-ttu-id="4648f-115">步骤 3：将 PowerPivot Web 应用程序解决方案部署到其他 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="4648f-115">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>](#deployUI)  
  
 [<span data-ttu-id="4648f-116">重新部署或收回解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-116">Redeploy or retract the Solution</span></span>](#retract)  
  
 [<span data-ttu-id="4648f-117">关于 PowerPivot 解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-117">About the PowerPivot Solutions</span></span>](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> <span data-ttu-id="4648f-118">先决条件：确认 Web 应用程序使用经典模式身份验证</span><span class="sxs-lookup"><span data-stu-id="4648f-118">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>  
 <span data-ttu-id="4648f-119">只有使用 Windows 经典模式身份验证的 Web 应用程序才支持 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="4648f-119">PowerPivot for SharePoint is only supported for web applications that use Windows-classic mode authentication.</span></span> <span data-ttu-id="4648f-120">若要检查应用程序是否使用经典模式，请从**sharepoint 2010 命令行管理**程序中运行以下 PowerShell cmdlet， `http://<top-level site name>` 并将替换为您的 sharepoint 站点的名称：</span><span class="sxs-lookup"><span data-stu-id="4648f-120">To check whether the application uses Classic mode, run the following PowerShell cmdlet from the **SharePoint 2010 Management Shell**, replacing `http://<top-level site name>` with the name of your SharePoint site:</span></span>  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 <span data-ttu-id="4648f-121">返回值应为 **false**。</span><span class="sxs-lookup"><span data-stu-id="4648f-121">The return value should be **false**.</span></span> <span data-ttu-id="4648f-122">如果为**true**，则不能使用此 web 应用程序访问 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="4648f-122">If it is **true**, you cannot access PowerPivot data with this web application.</span></span>  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a><span data-ttu-id="4648f-123">步骤1：部署场解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-123">Step 1: Deploy the Farm Solution</span></span>  
 <span data-ttu-id="4648f-124">本节向您演示如何使用 PowerShell 部署解决方案，但您也可以使用 PowerPivot 配置工具完成此任务。</span><span class="sxs-lookup"><span data-stu-id="4648f-124">This section shows you how to deploy solutions using PowerShell, but you can also use the PowerPivot Configuration Tool to complete this task.</span></span> <span data-ttu-id="4648f-125">有关详细信息，请参阅[PowerPivot for SharePoint 2010 &#40;PowerPivot 配置工具&#41;中配置或修复](../configure-repair-powerpivot-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="4648f-125">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="4648f-126">在您 PowerPivot for SharePoint 安装后，此任务只需要执行一次。</span><span class="sxs-lookup"><span data-stu-id="4648f-126">This task only needs to be performed once, after you install PowerPivot for SharePoint.</span></span>  
  
1.  <span data-ttu-id="4648f-127">在安装了 PowerPivot for SharePoint 的服务器上，使用 "以**管理员身份运行**" 选项打开 SharePoint 2010 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="4648f-127">On a server that has an installation of PowerPivot for SharePoint, open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="4648f-128">运行以下 cmdlet 以便添加场解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-128">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="4648f-129">该 cmdlet 返回解决方案的名称、其解决方案 ID 和 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="4648f-129">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="4648f-130">在下一步骤中，您将部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-130">In the next step, you will deploy the solution.</span></span>  
  
3.  <span data-ttu-id="4648f-131">运行下一个 cmdlet 以便部署场解决方案：</span><span class="sxs-lookup"><span data-stu-id="4648f-131">Run the next cmdlet to deploy the farm solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a><span data-ttu-id="4648f-132">步骤2：将 PowerPivot Web 应用程序解决方案部署到管理中心</span><span class="sxs-lookup"><span data-stu-id="4648f-132">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>  
 <span data-ttu-id="4648f-133">在您部署了场解决方案后，必须将 Web 应用程序解决方案部署到管理中心。</span><span class="sxs-lookup"><span data-stu-id="4648f-133">After you deploy the farm solution, you must deploy the Web application solution to Central Administration.</span></span> <span data-ttu-id="4648f-134">此步骤将 PowerPivot 管理面板添加到管理中心。</span><span class="sxs-lookup"><span data-stu-id="4648f-134">This step adds the PowerPivot Management Dashboard to Central Administration.</span></span>  
  
1.  <span data-ttu-id="4648f-135">使用 **“以管理员身份运行”** 选项打开 SharePoint 2010 Management Shell。</span><span class="sxs-lookup"><span data-stu-id="4648f-135">Open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="4648f-136">运行以下 cmdlet 以创建对管理中心的引用：</span><span class="sxs-lookup"><span data-stu-id="4648f-136">Run the following cmdlet to create a reference to Central Administration:</span></span>  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  <span data-ttu-id="4648f-137">运行以下 cmdlet 以便添加场解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-137">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     <span data-ttu-id="4648f-138">该 cmdlet 返回解决方案的名称、其解决方案 ID 和 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="4648f-138">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="4648f-139">在下一步骤中，您将部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-139">In the next step, you will deploy the solution.</span></span>  
  
4.  <span data-ttu-id="4648f-140">运行下一个 cmdlet 以将 Web 应用程序解决方案部署到管理中心。</span><span class="sxs-lookup"><span data-stu-id="4648f-140">Run the next cmdlet to install the web application solution to Central Administration.</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 <span data-ttu-id="4648f-141">现在，Web 应用程序解决方案已部署到管理中心，您可以使用管理中心完成所有其余配置步骤。</span><span class="sxs-lookup"><span data-stu-id="4648f-141">Now that the web application solution is deployed to Central Administration, you can use Central Administration to complete all remaining configuration steps.</span></span>  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a><span data-ttu-id="4648f-142">步骤3：将 PowerPivot Web 应用程序解决方案部署到其他 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="4648f-142">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>  
 <span data-ttu-id="4648f-143">在上一个任务中，您将 Powerpivotwebapp.wsp 部署到了管理中心。</span><span class="sxs-lookup"><span data-stu-id="4648f-143">In the previous task, you deployed Powerpivotwebapp.wsp to Central Administration.</span></span> <span data-ttu-id="4648f-144">在本节中，您可以在支持 PowerPivot 数据访问的每个现有 Web 应用程序上都部署 powerpivotwebapp.wsp。</span><span class="sxs-lookup"><span data-stu-id="4648f-144">In this section, you deploy the powerpivotwebapp.wsp on each existing web application that supports PowerPivot data access.</span></span> <span data-ttu-id="4648f-145">如果您在以后添加更多的 Web 应用程序，请确保对于这些附加的 Web 应用程序都重复执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="4648f-145">If you add more web applications later, be sure to repeat this step for those additional web applications.</span></span>  
  
1.  <span data-ttu-id="4648f-146">在管理中心的“系统设置”中，单击 **“管理场解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="4648f-146">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="4648f-147">单击 " **powerpivotwebapp.wsp**"。</span><span class="sxs-lookup"><span data-stu-id="4648f-147">Click **powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="4648f-148">单击 **“部署解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="4648f-148">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="4648f-149">在 **"部署到？**" 中，选择要为其添加 PowerPivot 功能支持的 SharePoint web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4648f-149">In **Deploy To?**, select the SharePoint web application for which you want to add PowerPivot feature support.</span></span>  
  
5.  <span data-ttu-id="4648f-150">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="4648f-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="4648f-151">对也要支持 PowerPivot 数据访问的其他 SharePoint Web 应用程序重复此过程。</span><span class="sxs-lookup"><span data-stu-id="4648f-151">Repeat for other SharePoint web applications that will also support PowerPivot data access.</span></span>  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a><span data-ttu-id="4648f-152">重新部署或收回解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-152">Redeploy or retract the Solution</span></span>  
 <span data-ttu-id="4648f-153">尽管 SharePoint 管理中心提供解决方案收回，但您无需收回 powerpivotwebapp.wsp 文件，除非您在系统地排除安装或修补程序部署问题。</span><span class="sxs-lookup"><span data-stu-id="4648f-153">Although SharePoint Central Administration provides solution retraction, you do not need to retract the powerpivotwebapp.wsp file unless you are systematically troubleshooting an installation or patch deployment problem.</span></span>  
  
1.  <span data-ttu-id="4648f-154">在 SharePoint 2010 管理中心的“系统设置”中，单击 **“管理场解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="4648f-154">In SharePoint 2010 Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="4648f-155">单击 **Powerpivotwebapp.wsp**。</span><span class="sxs-lookup"><span data-stu-id="4648f-155">Click **Powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="4648f-156">单击 **“收回解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="4648f-156">Click **Retract Solution**.</span></span>  
  
 <span data-ttu-id="4648f-157">如果你遇到跟踪回场解决方案的服务器部署问题，则可以通过在 PowerPivot 配置工具中运行 "**修复**" 选项来重新部署它。</span><span class="sxs-lookup"><span data-stu-id="4648f-157">If you encounter server deployment issues that you trace back to the farm solution, you can redeploy it by running the **Repair** option in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="4648f-158">应优先通过工具进行修复操作，因为这样只需执行较少的步骤。</span><span class="sxs-lookup"><span data-stu-id="4648f-158">Repair operations via the tool is preferred because it requires fewer steps on your part.</span></span> <span data-ttu-id="4648f-159">有关详细信息，请参阅[PowerPivot for SharePoint 2010 &#40;PowerPivot 配置工具&#41;中配置或修复](../configure-repair-powerpivot-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="4648f-159">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="4648f-160">如果您仍想要重新部署所有解决方案，则请确保按照下面的顺序进行重新部署：</span><span class="sxs-lookup"><span data-stu-id="4648f-160">If you still want to re-deploy all solutions, be sure to do so in this order:</span></span>  
  
1.  <span data-ttu-id="4648f-161">从使用它的所有 SharePoint Web 应用程序中收回 PowerPivot Web 应用程序解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-161">Retract the PowerPivot Web application solution from all SharePoint web applications that use it.</span></span>  
  
2.  <span data-ttu-id="4648f-162">收回 PowerPivot 场解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-162">Retract the PowerPivot farm solution.</span></span>  
  
3.  <span data-ttu-id="4648f-163">重新部署 PowerPivot 场解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-163">Redeploy the PowerPivot farm solution.</span></span>  
  
4.  <span data-ttu-id="4648f-164">将 PowerPivot Web 应用程序解决方案重新部署到所有 SharePoint Web 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="4648f-164">Redeploy the PowerPivot Web application solution to all SharePoint web applications.</span></span>  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a><span data-ttu-id="4648f-165">关于 PowerPivot 解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-165">About the PowerPivot Solutions</span></span>  
 <span data-ttu-id="4648f-166">PowerPivot for SharePoint 使用两个解决方案包将其应用程序页和程序文件部署到场中和单独的 Web 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="4648f-166">PowerPivot for SharePoint uses two solution packages to deploy its application pages and program files to the farm and to individual web applications.</span></span>  
  
-   <span data-ttu-id="4648f-167">场解决方案是全局的。</span><span class="sxs-lookup"><span data-stu-id="4648f-167">The farm solution is global.</span></span> <span data-ttu-id="4648f-168">该解决方案仅需部署一次就会变得自动可用于您以后添加到场中的任何新的 PowerPivot for SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="4648f-168">It is deployed once and then becomes automatically available to any new PowerPivot for SharePoint servers that you add to the farm later.</span></span>  
  
-   <span data-ttu-id="4648f-169">Web 应用程序解决方案是特定于应用程序的，且必须部署到场中的每个 Web 应用程序，包括管理中心 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4648f-169">The web application solution is application-specific and must be deployed to each web application in the farm, including the Central Administration web application.</span></span>  
  
 <span data-ttu-id="4648f-170">每个解决方案的部署方式都是不同的。</span><span class="sxs-lookup"><span data-stu-id="4648f-170">Each solution is deployed differently.</span></span>  <span data-ttu-id="4648f-171">场解决方案会在第一个 PowerPivot for SharePoint 实例安装后部署一次。</span><span class="sxs-lookup"><span data-stu-id="4648f-171">The farm solution is deployed once, after the first PowerPivot for SharePoint instance is installed.</span></span> <span data-ttu-id="4648f-172">若要部署场解决方案，可使用 PowerPivot 配置工具或 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4648f-172">To deploy the farm solution, you use the PowerPivot Configuration Tool or PowerShell cmdlets.</span></span>  
  
 <span data-ttu-id="4648f-173">首先，会将 Web 应用程序部署到管理中心，然后会将后续解决方案部署到支持对 PowerPivot 数据的请求的任何其他 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4648f-173">The web application solution is initially deployed to Central Administration, followed by subsequent solution deployments to any additional web applications that will support requests for PowerPivot data.</span></span> <span data-ttu-id="4648f-174">若要将 web 应用程序解决方案部署到管理中心，必须使用 PowerPivot 配置工具或 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4648f-174">To deploy the web application solution to Central Administration, you must use the PowerPivot Configuration Tool or PowerShell cmdlet.</span></span> <span data-ttu-id="4648f-175">对于所有其他 Web 应用程序，您可以使用管理中心或 PowerShell 手动部署 Web 应用程序解决方案。</span><span class="sxs-lookup"><span data-stu-id="4648f-175">For all other web applications, you can deploy the web application solution manually using Central Administration or PowerShell.</span></span>  
  
|<span data-ttu-id="4648f-176">解决方案</span><span class="sxs-lookup"><span data-stu-id="4648f-176">Solution</span></span>|<span data-ttu-id="4648f-177">说明</span><span class="sxs-lookup"><span data-stu-id="4648f-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4648f-178">Powerpivotfarm.wsp</span><span class="sxs-lookup"><span data-stu-id="4648f-178">Powerpivotfarm.wsp</span></span>|<span data-ttu-id="4648f-179">将 Microsoft.AnalysisServices.SharePoint.Integration.dll 添加到全局程序集中。</span><span class="sxs-lookup"><span data-stu-id="4648f-179">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="4648f-180">将 Microsoft.AnalysisServices.ChannelTransport.dll 添加到全局程序集中。</span><span class="sxs-lookup"><span data-stu-id="4648f-180">Adds Microsoft.AnalysisServices.ChannelTransport.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="4648f-181">安装功能和资源文件，并且注册内容类型。</span><span class="sxs-lookup"><span data-stu-id="4648f-181">Installs features and resources files, and registers content types.</span></span><br /><br /> <span data-ttu-id="4648f-182">为 PowerPivot 库和数据馈送库添加库模板。</span><span class="sxs-lookup"><span data-stu-id="4648f-182">Adds library templates for PowerPivot Gallery and Data Feed libraries.</span></span><br /><br /> <span data-ttu-id="4648f-183">为服务应用程序配置、PowerPivot 管理面板、数据刷新和 PowerPivot 库添加应用程序页。</span><span class="sxs-lookup"><span data-stu-id="4648f-183">Adds application pages for service application configuration, PowerPivot Management Dashboard, data refresh, and PowerPivot Gallery.</span></span>|  
|<span data-ttu-id="4648f-184">“powerpivotwebapp.wsp”</span><span class="sxs-lookup"><span data-stu-id="4648f-184">Powerpivotwebapp.wsp</span></span>|<span data-ttu-id="4648f-185">将 Microsoft.AnalysisServices.SharePoint.Integration.dll 资源文件添加到 Web 前端上的 Web 服务器扩展插件文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4648f-185">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll resources files to the web server extensions folder on the Web front-end.</span></span><br /><br /> <span data-ttu-id="4648f-186">将 PowerPivot Web 服务添加到 Web 前端。</span><span class="sxs-lookup"><span data-stu-id="4648f-186">Adds PowerPivot Web service to the Web-front end.</span></span><br /><br /> <span data-ttu-id="4648f-187">为 PowerPivot 库添加缩略图生成。</span><span class="sxs-lookup"><span data-stu-id="4648f-187">Adds thumbnail image generation for PowerPivot Gallery.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4648f-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4648f-188">See Also</span></span>  
 <span data-ttu-id="4648f-189">[升级 PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="4648f-189">[Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="4648f-190">[管理中心中的 PowerPivot 服务器管理和配置](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="4648f-190">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 [<span data-ttu-id="4648f-191">使用 Windows PowerShell 配置 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="4648f-191">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
