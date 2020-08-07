---
title: 将 sqlcmd 与脚本变量结合使用
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server], sqlcmd utility
- variables [SQL Server], scripts
- scripting variables [SQL Server]
- sqlcmd utility, scripts
- setvar command
ms.assetid: 793495ca-cfc9-498d-8276-c44a5d09a92c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443cb400dc099726ba75bfcec2d38cee4ee2dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589507"
---
# <a name="use-sqlcmd-with-scripting-variables"></a><span data-ttu-id="32695-102">将 sqlcmd 与脚本变量结合使用</span><span class="sxs-lookup"><span data-stu-id="32695-102">Use sqlcmd with Scripting Variables</span></span>
  <span data-ttu-id="32695-103">脚本中使用的变量称为脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-103">Variables that are used in scripts are called scripting variables.</span></span> <span data-ttu-id="32695-104">使用脚本变量，一个脚本可以应用于多个方案中。</span><span class="sxs-lookup"><span data-stu-id="32695-104">Scripting variables enable one script to be used in multiple scenarios.</span></span> <span data-ttu-id="32695-105">例如，如果需要对多台服务器运行单个脚本，则可以用脚本变量来表示服务器名称，而不必为每台服务器修改脚本。</span><span class="sxs-lookup"><span data-stu-id="32695-105">For example, if you want to run one script against multiple servers, instead of modifying the script for each server, you can use a scripting variable for the server name.</span></span> <span data-ttu-id="32695-106">通过更改脚本变量表示的服务器名称，可以在不同的服务器上运行同一脚本。</span><span class="sxs-lookup"><span data-stu-id="32695-106">By changing the server name supplied to the scripting variable, the same script can be executed on different servers.</span></span>  
  
 <span data-ttu-id="32695-107">可以使用 **setvar** 命令显式定义脚本变量，也可以使用 **sqlcmd-v** 选项隐式定义脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-107">Scripting variables can be defined explicitly by using the **setvar** command, or implicitly by using the **sqlcmd-v** option.</span></span>  
  
 <span data-ttu-id="32695-108">本主题还包含有关使用 **SET**在 Cmd.exe 命令提示符下定义环境变量的示例。</span><span class="sxs-lookup"><span data-stu-id="32695-108">This topic also includes examples defining environmental variables at the Cmd.exe command prompt by using **SET**.</span></span>  
  
## <a name="setting-scripting-variables-by-using-the-setvar-command"></a><span data-ttu-id="32695-109">使用 setvar 命令设置脚本变量</span><span class="sxs-lookup"><span data-stu-id="32695-109">Setting Scripting Variables by Using the setvar Command</span></span>  
 <span data-ttu-id="32695-110">**setvar** 命令用于定义脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-110">The **setvar** command is used to define scripting variables.</span></span> <span data-ttu-id="32695-111">内部存储使用 **setvar** 命令定义的变量。</span><span class="sxs-lookup"><span data-stu-id="32695-111">Variables that are defined by using the **setvar** command are stored internally.</span></span> <span data-ttu-id="32695-112">不应将脚本变量与使用 **SET**在命令提示符下定义的环境变量相混淆。</span><span class="sxs-lookup"><span data-stu-id="32695-112">Scripting variables should not be confused with environment variables that are defined at the command prompt by using **SET**.</span></span> <span data-ttu-id="32695-113">如果脚本引用的变量不是环境变量，或不是使用 **setvar**定义的变量，则会返回错误消息，并将停止执行脚本。</span><span class="sxs-lookup"><span data-stu-id="32695-113">If a script references a variable that is not an environment variable or is not defined by using **setvar**, an error message is returned and the execution of the script will stop.</span></span> <span data-ttu-id="32695-114">有关详细信息，请参阅 **sqlcmd 实用工具** 中的 [-b](../../tools/sqlcmd-utility.md)选项。</span><span class="sxs-lookup"><span data-stu-id="32695-114">For more information, see the **-b** option in [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="32695-115">变量优先级（从低到高）</span><span class="sxs-lookup"><span data-stu-id="32695-115">Variable Precedence (Low to High)</span></span>  
 <span data-ttu-id="32695-116">如果有多类变量具有相同的名称，则使用优先级最高的变量。</span><span class="sxs-lookup"><span data-stu-id="32695-116">If more than one type of variable has the same name, the variable with the highest precedence is used.</span></span>  
  
1.  <span data-ttu-id="32695-117">系统级环境变量</span><span class="sxs-lookup"><span data-stu-id="32695-117">System level environmental variables</span></span>  
  
2.  <span data-ttu-id="32695-118">用户级环境变量</span><span class="sxs-lookup"><span data-stu-id="32695-118">User level environmental variables</span></span>  
  
3.  <span data-ttu-id="32695-119">启动**SET X=Y**之前在命令提示符下设置的命令 shell ( **SET X=Y**)</span><span class="sxs-lookup"><span data-stu-id="32695-119">Command shell (**SET X=Y**) set at command prompt before starting **sqlcmd**</span></span>  
  
4.  <span data-ttu-id="32695-120">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="32695-120">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="32695-121">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="32695-121">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32695-122">若要查看环境变量，请在“控制面板”  中打开“系统”  ，然后单击“高级”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="32695-122">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="implicitly-setting-scripting-variables"></a><span data-ttu-id="32695-123">隐式设置脚本变量</span><span class="sxs-lookup"><span data-stu-id="32695-123">Implicitly Setting Scripting Variables</span></span>  
 <span data-ttu-id="32695-124">使用具有相关 **sqlcmd** 变量的选项启动 **sqlcmd** 时， **sqlcmd** 变量将被隐式设置为使用该选项指定的值。</span><span class="sxs-lookup"><span data-stu-id="32695-124">When you start **sqlcmd** with an option that has a related **sqlcmd** variable, the **sqlcmd** variable is set implicitly to the value that is specified by using the option.</span></span> <span data-ttu-id="32695-125">在下面的示例中，启动 `sqlcmd` 时使用了 `-l` 选项。</span><span class="sxs-lookup"><span data-stu-id="32695-125">In the following example, `sqlcmd` is started with the `-l` option.</span></span> <span data-ttu-id="32695-126">这会隐式设置 SQLLOGINTIMEOUT 变量。</span><span class="sxs-lookup"><span data-stu-id="32695-126">This implicitly sets the SQLLOGINTIMEOUT variable.</span></span>  
  
 `c:\> sqlcmd -l 60`  
  
 <span data-ttu-id="32695-127">你还可以使用 **-v** 选项对脚本中的脚本变量进行设置。</span><span class="sxs-lookup"><span data-stu-id="32695-127">You can also use the **-v** option to set a scripting variable that exists in a script.</span></span> <span data-ttu-id="32695-128">在下面的脚本（文件名为 `testscript.sql`）中， `ColumnName` 是一个脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-128">In the following script (the file name is `testscript.sql`), `ColumnName` is a scripting variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT x.$(ColumnName)`  
  
 `FROM Person.Person x`  
  
 <span data-ttu-id="32695-129">`WHERE c.` BusinessEntityID `< 5;`</span><span class="sxs-lookup"><span data-stu-id="32695-129">`WHERE c.`BusinessEntityID `< 5;`</span></span>  
  
 <span data-ttu-id="32695-130">然后，您可以使用 `-v` 选项指定要返回的列名称：</span><span class="sxs-lookup"><span data-stu-id="32695-130">You can then specify the name of the column that you want returned by using the `-v` option:</span></span>  
  
 `sqlcmd -v ColumnName ="FirstName" -i c:\testscript.sql`  
  
 <span data-ttu-id="32695-131">若要使用同一个脚本返回其他列，请更改 `ColumnName` 脚本变量的值。</span><span class="sxs-lookup"><span data-stu-id="32695-131">To return a different column by using the same script, change the value of the `ColumnName` scripting variable.</span></span>  
  
 `sqlcmd -v ColumnName ="LastName" -i c:\testscript.sql`  
  
## <a name="guidelines-for-scripting-variable-names-and-values"></a><span data-ttu-id="32695-132">有关脚本变量名和变量值的原则</span><span class="sxs-lookup"><span data-stu-id="32695-132">Guidelines for Scripting Variable Names and Values</span></span>  
 <span data-ttu-id="32695-133">为脚本变量命名时，请考虑以下原则：</span><span class="sxs-lookup"><span data-stu-id="32695-133">Consider the following guidelines when you name scripting variables:</span></span>  
  
-   <span data-ttu-id="32695-134">变量名不能包含空格字符或引号。</span><span class="sxs-lookup"><span data-stu-id="32695-134">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="32695-135">变量名不能与变量表达式（如 *$(var)*）具有相同的形式。</span><span class="sxs-lookup"><span data-stu-id="32695-135">Variable names must not have the same form as a variable expression, such as *$(var)*.</span></span>  
  
-   <span data-ttu-id="32695-136">脚本变量不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="32695-136">Scripting variables are case-insensitive</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32695-137">如果没有为 **sqlcmd** 环境变量分配任何值，则将删除该变量。</span><span class="sxs-lookup"><span data-stu-id="32695-137">If no value is assigned to a **sqlcmd** environment variable, the variable is removed.</span></span> <span data-ttu-id="32695-138">使用不包含值的 **:setvar VarName** 可以清除该变量。</span><span class="sxs-lookup"><span data-stu-id="32695-138">Using **:setvar VarName** without a value clears the variable.</span></span>  
  
 <span data-ttu-id="32695-139">为脚本变量指定值时，请考虑以下原则：</span><span class="sxs-lookup"><span data-stu-id="32695-139">Consider the following guidelines when you specify values for scripting variables:</span></span>  
  
-   <span data-ttu-id="32695-140">如果字符串值包含空格，必须给使用 **setvar** 或 **-v** 选项定义的变量值加上引号。</span><span class="sxs-lookup"><span data-stu-id="32695-140">Variable values that are defined by using **setvar** or the **-v** option must be enclosed by quotation marks if the string value contains spaces.</span></span>  
  
-   <span data-ttu-id="32695-141">如果引号属于变量值的一部分，则必须对其进行转义。</span><span class="sxs-lookup"><span data-stu-id="32695-141">If quotation marks are part of the variable value, they must be escaped.</span></span> <span data-ttu-id="32695-142">例如：:`setvar MyVar "spac""e"`。</span><span class="sxs-lookup"><span data-stu-id="32695-142">For example: :`setvar MyVar "spac""e"`.</span></span>  
  
## <a name="guidelines-for-cmdexe-set-variable-values-and-names"></a><span data-ttu-id="32695-143">有关 Cmd.exe SET 变量值和变量名的原则</span><span class="sxs-lookup"><span data-stu-id="32695-143">Guidelines for Cmd.exe SET Variable Values and Names</span></span>  
 <span data-ttu-id="32695-144">使用 SET 定义的变量是 Cmd.exe 环境的一部分并可以通过 **sqlcmd**进行引用。</span><span class="sxs-lookup"><span data-stu-id="32695-144">Variables that are defined by using SET are part of the Cmd.exe environment and can be referenced by **sqlcmd**.</span></span> <span data-ttu-id="32695-145">遵循以下指南：</span><span class="sxs-lookup"><span data-stu-id="32695-145">Consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="32695-146">变量名不能包含空格字符或引号。</span><span class="sxs-lookup"><span data-stu-id="32695-146">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="32695-147">变量值可包含空格或引号。</span><span class="sxs-lookup"><span data-stu-id="32695-147">Variable values may contain spaces or quotation marks.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="32695-148">sqlcmd 脚本变量</span><span class="sxs-lookup"><span data-stu-id="32695-148">sqlcmd Scripting Variables</span></span>  
 <span data-ttu-id="32695-149">将 **sqlcmd** 定义的变量称为脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-149">Variables that are defined by **sqlcmd** are known as scripting variables.</span></span> <span data-ttu-id="32695-150">下表列出了 **sqlcmd** 脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-150">The following table lists **sqlcmd** scripting variables.</span></span>  
  
|<span data-ttu-id="32695-151">变量</span><span class="sxs-lookup"><span data-stu-id="32695-151">Variable</span></span>|<span data-ttu-id="32695-152">相关选项</span><span class="sxs-lookup"><span data-stu-id="32695-152">Related option</span></span>|<span data-ttu-id="32695-153">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-153">R/W</span></span>|<span data-ttu-id="32695-154">默认</span><span class="sxs-lookup"><span data-stu-id="32695-154">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="32695-155">SQLCMDUSER\*</span><span class="sxs-lookup"><span data-stu-id="32695-155">SQLCMDUSER\*</span></span>|<span data-ttu-id="32695-156">-U</span><span class="sxs-lookup"><span data-stu-id="32695-156">-U</span></span>|<span data-ttu-id="32695-157">R</span><span class="sxs-lookup"><span data-stu-id="32695-157">R</span></span>|<span data-ttu-id="32695-158">""</span><span class="sxs-lookup"><span data-stu-id="32695-158">""</span></span>|  
|<span data-ttu-id="32695-159">SQLCMDPASSWORD\*</span><span class="sxs-lookup"><span data-stu-id="32695-159">SQLCMDPASSWORD\*</span></span>|<span data-ttu-id="32695-160">-P</span><span class="sxs-lookup"><span data-stu-id="32695-160">-P</span></span>|--|<span data-ttu-id="32695-161">""</span><span class="sxs-lookup"><span data-stu-id="32695-161">""</span></span>|  
|<span data-ttu-id="32695-162">SQLCMDSERVER\*</span><span class="sxs-lookup"><span data-stu-id="32695-162">SQLCMDSERVER\*</span></span>|<span data-ttu-id="32695-163">sqlcmd</span><span class="sxs-lookup"><span data-stu-id="32695-163">-S</span></span>|<span data-ttu-id="32695-164">R</span><span class="sxs-lookup"><span data-stu-id="32695-164">R</span></span>|<span data-ttu-id="32695-165">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="32695-165">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="32695-166">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="32695-166">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="32695-167">-H</span><span class="sxs-lookup"><span data-stu-id="32695-167">-H</span></span>|<span data-ttu-id="32695-168">R</span><span class="sxs-lookup"><span data-stu-id="32695-168">R</span></span>|<span data-ttu-id="32695-169">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="32695-169">"ComputerName"</span></span>|  
|<span data-ttu-id="32695-170">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="32695-170">SQLCMDDBNAME</span></span>|<span data-ttu-id="32695-171">-d</span><span class="sxs-lookup"><span data-stu-id="32695-171">-d</span></span>|<span data-ttu-id="32695-172">R</span><span class="sxs-lookup"><span data-stu-id="32695-172">R</span></span>|<span data-ttu-id="32695-173">""</span><span class="sxs-lookup"><span data-stu-id="32695-173">""</span></span>|  
|<span data-ttu-id="32695-174">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32695-174">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="32695-175">-l</span><span class="sxs-lookup"><span data-stu-id="32695-175">-l</span></span>|<span data-ttu-id="32695-176">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-176">R/W</span></span>|<span data-ttu-id="32695-177">"8"（秒）</span><span class="sxs-lookup"><span data-stu-id="32695-177">"8" (seconds)</span></span>|  
|<span data-ttu-id="32695-178">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32695-178">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="32695-179">-t</span><span class="sxs-lookup"><span data-stu-id="32695-179">-t</span></span>|<span data-ttu-id="32695-180">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-180">R/W</span></span>|<span data-ttu-id="32695-181">"0" = 无限期等待</span><span class="sxs-lookup"><span data-stu-id="32695-181">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="32695-182">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="32695-182">SQLCMDHEADERS</span></span>|<span data-ttu-id="32695-183">-H</span><span class="sxs-lookup"><span data-stu-id="32695-183">-h</span></span>|<span data-ttu-id="32695-184">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-184">R/W</span></span>|<span data-ttu-id="32695-185">"0"</span><span class="sxs-lookup"><span data-stu-id="32695-185">"0"</span></span>|  
|<span data-ttu-id="32695-186">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="32695-186">SQLCMDCOLSEP</span></span>|<span data-ttu-id="32695-187">-S</span><span class="sxs-lookup"><span data-stu-id="32695-187">-s</span></span>|<span data-ttu-id="32695-188">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-188">R/W</span></span>|<span data-ttu-id="32695-189">" "</span><span class="sxs-lookup"><span data-stu-id="32695-189">" "</span></span>|  
|<span data-ttu-id="32695-190">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="32695-190">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="32695-191">-w</span><span class="sxs-lookup"><span data-stu-id="32695-191">-w</span></span>|<span data-ttu-id="32695-192">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-192">R/W</span></span>|<span data-ttu-id="32695-193">"0"</span><span class="sxs-lookup"><span data-stu-id="32695-193">"0"</span></span>|  
|<span data-ttu-id="32695-194">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="32695-194">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="32695-195">-a</span><span class="sxs-lookup"><span data-stu-id="32695-195">-a</span></span>|<span data-ttu-id="32695-196">R</span><span class="sxs-lookup"><span data-stu-id="32695-196">R</span></span>|<span data-ttu-id="32695-197">"4096"</span><span class="sxs-lookup"><span data-stu-id="32695-197">"4096"</span></span>|  
|<span data-ttu-id="32695-198">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="32695-198">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="32695-199">-M</span><span class="sxs-lookup"><span data-stu-id="32695-199">-m</span></span>|<span data-ttu-id="32695-200">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-200">R/W</span></span>|<span data-ttu-id="32695-201">"0"</span><span class="sxs-lookup"><span data-stu-id="32695-201">"0"</span></span>|  
|<span data-ttu-id="32695-202">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="32695-202">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="32695-203">-y</span><span class="sxs-lookup"><span data-stu-id="32695-203">-y</span></span>|<span data-ttu-id="32695-204">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-204">R/W</span></span>|<span data-ttu-id="32695-205">"256"</span><span class="sxs-lookup"><span data-stu-id="32695-205">"256"</span></span>|  
|<span data-ttu-id="32695-206">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="32695-206">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="32695-207">-y</span><span class="sxs-lookup"><span data-stu-id="32695-207">-Y</span></span>|<span data-ttu-id="32695-208">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-208">R/W</span></span>|<span data-ttu-id="32695-209">"0" = 无限制</span><span class="sxs-lookup"><span data-stu-id="32695-209">"0" = unlimited</span></span>|  
|<span data-ttu-id="32695-210">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="32695-210">SQLCMDEDITOR</span></span>||<span data-ttu-id="32695-211">R/W</span><span class="sxs-lookup"><span data-stu-id="32695-211">R/W</span></span>|<span data-ttu-id="32695-212">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="32695-212">"edit.com"</span></span>|  
|<span data-ttu-id="32695-213">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="32695-213">SQLCMDINI</span></span>||<span data-ttu-id="32695-214">R</span><span class="sxs-lookup"><span data-stu-id="32695-214">R</span></span>|<span data-ttu-id="32695-215">""</span><span class="sxs-lookup"><span data-stu-id="32695-215">""</span></span>|  
  
 <span data-ttu-id="32695-216">\*使用 **： Connect**时，将设置 SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDSERVER。</span><span class="sxs-lookup"><span data-stu-id="32695-216">\* SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect** is used.</span></span>  
  
 <span data-ttu-id="32695-217">R 表示在程序初始化过程中只能设置一次值。</span><span class="sxs-lookup"><span data-stu-id="32695-217">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="32695-218">R/W 表示可以使用 **setvar** 命令重置值，并且后续命令将使用新值。</span><span class="sxs-lookup"><span data-stu-id="32695-218">R/W indicates that the value can be reset by using the **setvar** command and subsequent commands will use the new value.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="32695-219">示例</span><span class="sxs-lookup"><span data-stu-id="32695-219">Examples</span></span>  
  
### <a name="a-using-the-setvar-command-in-a-script"></a><span data-ttu-id="32695-220">A.</span><span class="sxs-lookup"><span data-stu-id="32695-220">A.</span></span> <span data-ttu-id="32695-221">在脚本中使用 setvar 命令</span><span class="sxs-lookup"><span data-stu-id="32695-221">Using the setvar command in a script</span></span>  
 <span data-ttu-id="32695-222">许多 **sqlcmd** 选项可以通过在脚本内使用 **setvar** 命令进行控制。</span><span class="sxs-lookup"><span data-stu-id="32695-222">Many **sqlcmd** options can be controlled in a script by using the **setvar** command.</span></span> <span data-ttu-id="32695-223">在下面的示例中，创建了一个脚本 `test.sql` ，其中 `SQLCMDLOGINTIMEOUT` 变量设置为 `60` 秒，另一个脚本变量 `server`设置为 `testserver`。</span><span class="sxs-lookup"><span data-stu-id="32695-223">In the following example, the script `test.sql` is created in which the `SQLCMDLOGINTIMEOUT` variable is set to `60` seconds and another scripting variable, `server`, is set to `testserver`.</span></span> <span data-ttu-id="32695-224">以下是 `test.sql`中的代码。</span><span class="sxs-lookup"><span data-stu-id="32695-224">The following code is in `test.sql`.</span></span>  
  
 `:setvar SQLCMDLOGINTIMEOUT 60`  
  
 `:setvar server "testserver"`  
  
 `:connect $(server) -l $(SQLCMDLOGINTIMEOUT)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `The script is then called by using sqlcmd:`  
  
 `sqlcmd -i c:\test.sql`  
  
### <a name="b-using-the-setvar-command-interactively"></a><span data-ttu-id="32695-225">B.</span><span class="sxs-lookup"><span data-stu-id="32695-225">B.</span></span> <span data-ttu-id="32695-226">交互式使用 setvar 命令</span><span class="sxs-lookup"><span data-stu-id="32695-226">Using the setvar command interactively</span></span>  
 <span data-ttu-id="32695-227">下面的示例说明了如何使用 `setvar` 命令交互式设置脚本变量。</span><span class="sxs-lookup"><span data-stu-id="32695-227">The following example shows how to set a scripting variable interactively by using the `setvar` command.</span></span>  
  
 `sqlcmd`  
  
 `:setvar  MYDATABASE AdventureWorks2012`  
  
 `USE $(MYDATABASE);`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'`  
  
 `1>`  
  
### <a name="c-using-command-prompt-environment-variables-within-sqlcmd"></a><span data-ttu-id="32695-228">C.</span><span class="sxs-lookup"><span data-stu-id="32695-228">C.</span></span> <span data-ttu-id="32695-229">在 sqlcmd 中使用命令提示符环境变量</span><span class="sxs-lookup"><span data-stu-id="32695-229">Using command prompt environment variables within sqlcmd</span></span>  
 <span data-ttu-id="32695-230">在下例中，设置了四个环境变量 `are` 然后从 `sqlcmd`加以调用。</span><span class="sxs-lookup"><span data-stu-id="32695-230">In the following example, four environment variables `are` set and then called from `sqlcmd`.</span></span>  
  
 `C:\>SET tablename=Person.Person`  
  
 `C:\>SET col1=FirstName`  
  
 `C:\>SET col2=LastName`  
  
 `C:\>SET title=Ms.`  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> SELECT TOP 5 $(col1) + ' ' + $(col2) AS Name`  
  
 `2> FROM $(tablename)`  
  
 `3> WHERE Title ='$(title)'`  
  
 `4> GO`  
  
### <a name="d-using-user-level-environment-variables-within-sqlcmd"></a><span data-ttu-id="32695-231">D.</span><span class="sxs-lookup"><span data-stu-id="32695-231">D.</span></span> <span data-ttu-id="32695-232">在 sqlcmd 中使用用户级环境变量</span><span class="sxs-lookup"><span data-stu-id="32695-232">Using user-level environment variables within sqlcmd</span></span>  
 <span data-ttu-id="32695-233">在下面的示例中，在命令提示符下设置了用户级环境变量 `%Temp%` ，并将其传递给了 `sqlcmd` 输入文件。</span><span class="sxs-lookup"><span data-stu-id="32695-233">In the following example the user-level environmental variable `%Temp%` is set at the command prompt and passed to the `sqlcmd` input file.</span></span> <span data-ttu-id="32695-234">若要获取用户级环境变量，请在“控制面板”  中双击“系统”  。</span><span class="sxs-lookup"><span data-stu-id="32695-234">To obtain the user-level environment variable, in **Control Panel**, double-click **System**.</span></span> <span data-ttu-id="32695-235">单击 **“高级”** 选项卡，再单击 **“环境变量”** 。</span><span class="sxs-lookup"><span data-stu-id="32695-235">Click the **Advance** tab, and then click **Environment Variables**.</span></span>  
  
 <span data-ttu-id="32695-236">下列代码位于输入文件 `c:\testscript.txt`:</span><span class="sxs-lookup"><span data-stu-id="32695-236">The following code is in the input file `c:\testscript.txt`:</span></span>  
  
 `:OUT $(MyTempDirectory)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName`  
  
 `FROM AdventureWorks2012.Person.Person`  
  
 <span data-ttu-id="32695-237">`WHERE BusinessEntityID` `< 5;`</span><span class="sxs-lookup"><span data-stu-id="32695-237">`WHERE BusinessEntityID` `< 5;`</span></span>  
  
 <span data-ttu-id="32695-238">以下是在命令提示符下输入的代码：</span><span class="sxs-lookup"><span data-stu-id="32695-238">This following code is entered at the command prompt:</span></span>  
  
 `C:\ >SET MyTempDirectory=%Temp%\output.txt`  
  
 `C:\ >sqlcmd -i C:\testscript.txt`  
  
 <span data-ttu-id="32695-239">以下是发送给输出文件 C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt 的结果。</span><span class="sxs-lookup"><span data-stu-id="32695-239">The following result is sent to the output file C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt.</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `FirstName`  
  
 `--------------------------------------------------`  
  
 `Gustavo`  
  
 `Catherine`  
  
 `Kim`  
  
 `Humberto`  
  
 `(4 rows affected)`  
  
### <a name="e-using-a-startup-script"></a><span data-ttu-id="32695-240">E.</span><span class="sxs-lookup"><span data-stu-id="32695-240">E.</span></span> <span data-ttu-id="32695-241">使用启动脚本</span><span class="sxs-lookup"><span data-stu-id="32695-241">Using a startup script</span></span>  
 <span data-ttu-id="32695-242">将在 **sqlcmd** 启动时执行 **sqlcmd** 启动脚本。</span><span class="sxs-lookup"><span data-stu-id="32695-242">A **sqlcmd** startup script is executed when **sqlcmd** is started.</span></span> <span data-ttu-id="32695-243">下面的示例设置了环境变量 `SQLCMDINI`。</span><span class="sxs-lookup"><span data-stu-id="32695-243">The following example sets the environment variable `SQLCMDINI`.</span></span> <span data-ttu-id="32695-244">下面是 `init.sql.`</span><span class="sxs-lookup"><span data-stu-id="32695-244">This is the contents of `init.sql.`</span></span>  
  
 `SET NOCOUNT ON`  
  
 `GO`  
  
 `DECLARE @nt_username nvarchar(128)`  
  
 `SET @nt_username = (SELECT rtrim(convert(nvarchar(128), nt_username))`  
  
 `FROM sys.dm_exec_sessions WHERE spid = @@SPID)`  
  
 `SELECT  @nt_username + ' is connected to ' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('servername'))) +`  
  
 `' (' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('productversion'))) +`  
  
 `')'`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH 100`  
  
 `SET NOCOUNT OFF`  
  
 `GO`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH`  
  
 <span data-ttu-id="32695-245">这将在 `init.sql` 启动时调用 `sqlcmd` 文件。</span><span class="sxs-lookup"><span data-stu-id="32695-245">This calls the `init.sql` file when `sqlcmd` is started.</span></span>  
  
 `C:\> SET sqlcmdini=c:\init.sql`  
  
 `>1 Sqlcmd`  
  
 <span data-ttu-id="32695-246">这是输出。</span><span class="sxs-lookup"><span data-stu-id="32695-246">This is the output.</span></span>  
  
 `>1 < user > is connected to < server > (9.00.2047.00)`  
  
> [!NOTE]  
>  <span data-ttu-id="32695-247">**-X** 选项禁用启动脚本功能。</span><span class="sxs-lookup"><span data-stu-id="32695-247">The **-X** option disables the startup script feature.</span></span>  
  
### <a name="f-variable-expansion"></a><span data-ttu-id="32695-248">F.</span><span class="sxs-lookup"><span data-stu-id="32695-248">F.</span></span> <span data-ttu-id="32695-249">变量扩展</span><span class="sxs-lookup"><span data-stu-id="32695-249">Variable expansion</span></span>  
 <span data-ttu-id="32695-250">下面的示例演示了以 **sqlcmd** 变量的形式处理数据。</span><span class="sxs-lookup"><span data-stu-id="32695-250">The following example shows working with data in the form of a **sqlcmd** variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `CREATE TABLE AdventureWorks2012.dbo.VariableTest`  
  
 `(`  
  
 `Col1 nvarchar(50)`  
  
 `);`  
  
 `GO`  
  
 <span data-ttu-id="32695-251">在 `Col1` （包含值 `dbo.VariableTest` ）的 `$(tablename)`中插入一行。</span><span class="sxs-lookup"><span data-stu-id="32695-251">Insert one row into `Col1` of `dbo.VariableTest` that contains the value `$(tablename)`.</span></span>  
  
 `INSERT INTO AdventureWorks2012.dbo.VariableTest(Col1)`  
  
 `VALUES('$(tablename)');`  
  
 `GO`  
  
 <span data-ttu-id="32695-252">在 `sqlcmd` 提示符下，如果没有将任何变量设置为 `$(tablename)`，则以下语句将返回该行。</span><span class="sxs-lookup"><span data-stu-id="32695-252">At the `sqlcmd` prompt, when no variable is set equal to `$(tablename)`, the following statements return the row.</span></span>  
  
 `C:\> sqlcmd`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>2 GO`  
  
 `>3 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>4 GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `>1 Col1`  
  
 `>2 ------------------`  
  
 `>3 $(tablename)`  
  
 `>4`  
  
 `>5 (1 rows affected)`  
  
 <span data-ttu-id="32695-253">假设将变量 `MyVar` 设置为 `$(tablename)`。</span><span class="sxs-lookup"><span data-stu-id="32695-253">Given the variable `MyVar` is set to `$(tablename)`.</span></span>  
  
 `>6 :setvar MyVar $(tablename)`  
  
 <span data-ttu-id="32695-254">这些语句返回该行，并且还返回了消息：“未定义‘tablename’脚本变量”。</span><span class="sxs-lookup"><span data-stu-id="32695-254">These statements return the row and also return the message "'tablename' scripting variable not defined."</span></span>  
  
 `>6 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>7 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>2 GO`  
  
 <span data-ttu-id="32695-255">这些语句返回该行。</span><span class="sxs-lookup"><span data-stu-id="32695-255">These statements return the row.</span></span>  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(MyVar)';`  
  
 `>2 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(MyVar)';`  
  
 `>2 GO`  
  
## <a name="see-also"></a><span data-ttu-id="32695-256">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32695-256">See Also</span></span>  
 <span data-ttu-id="32695-257">[使用 sqlcmd 实用工具](sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="32695-257">[Use the sqlcmd Utility](sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="32695-258">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="32695-258">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="32695-259">命令提示实用工具参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="32695-259">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](../../tools/command-prompt-utility-reference-database-engine.md)  
  
  
