---
title: "Comment ajouter des comptes à un affichage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- Add-Account command [BAM]
- managing [BAM], adding accounts to views
ms.assetid: 0875796c-82a4-4165-9bed-88e8ba466548
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 808d5395452733d43337e0883b306b7757a7da08
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-accounts-to-a-view"></a><span data-ttu-id="cc9fa-102">Ajout de comptes à une vue</span><span class="sxs-lookup"><span data-stu-id="cc9fa-102">How to Add Accounts to a View</span></span>
<span data-ttu-id="cc9fa-103">Les administrateurs utilisent la **-ajouter un compte** commande pour associer des utilisateurs à des vues BAM et protéger les vues de la feuille de calcul Excel BAM à partir de tout accès non autorisé.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-103">Administrators use the **add-account** command to associate users with BAM views and protect BAM Excel Spreadsheet views from unauthorized access.</span></span> <span data-ttu-id="cc9fa-104">Lorsque les vues BAM sont enregistrées par des utilisateurs, elles référencent une chaîne de connexion SQL masquée dans le classeur.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-104">When users save BAM views, the views reference a SQL connection string that is hidden within the workbook.</span></span> <span data-ttu-id="cc9fa-105">Le classeur est protégé, mais vous devez vous assurer que le document est également protégé.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-105">The workbook is protected, but you must ensure that the document is protected.</span></span>  
  
 <span data-ttu-id="cc9fa-106">Lorsque vous associez des utilisateurs à des vues BAM, vous limitez l'accès de ces vues aux seuls utilisateurs et groupes auxquels vous avez accordé des autorisations d'accès.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-106">When you associate users with BAM views, you restrict access to the views to only the users or groups to whom you grant access.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc9fa-107">Si vous utilisez des agrégations en temps réel (RTA), les utilisateurs ajoutés à **-ajouter un compte** ne voient pas accorder automatiquement des droits d’ouverture de session à l’ordinateur exécutant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-107">If you are using real-time aggregations (RTAs), users added with **add-account** are not automatically granted logon rights to the computer running SQL Server.</span></span> <span data-ttu-id="cc9fa-108">Dans ce cas, prévoyez d'établir un groupe d'utilisateurs Windows contenant tous les utilisateurs qui ont besoin d'afficher des vues d'agrégations RTA.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-108">If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs.</span></span> <span data-ttu-id="cc9fa-109">Accordez à ce groupe des droits de connexion SQL Server explicites au serveur SQL hébergeant la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-109">Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="cc9fa-110">Pour plus d’informations sur l’affichage des vues BAM, consultez [comment répertorier les vues BAM](../core/how-to-list-bam-views.md).</span><span class="sxs-lookup"><span data-stu-id="cc9fa-110">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-add-an-account-to-a-view"></a><span data-ttu-id="cc9fa-111">Pour ajouter des comptes à une vue</span><span class="sxs-lookup"><span data-stu-id="cc9fa-111">To add an account to a view</span></span>  
  
1.  <span data-ttu-id="cc9fa-112">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-112">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="cc9fa-113">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-113">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="cc9fa-114">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-114">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="cc9fa-115">Type **bm ajouter-account - AccountName :\<nom de compte\> -View :\<nom de la vue\>**.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-115">Type **bm add-account -AccountName:\<account name\> -View:\<view name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cc9fa-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="cc9fa-117">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-117">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9fa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc9fa-118">See Also</span></span>  
 <span data-ttu-id="cc9fa-119">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="cc9fa-119">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="cc9fa-120">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="cc9fa-120">BAM Management Utility</span></span>](../core/bam-management-utility.md)