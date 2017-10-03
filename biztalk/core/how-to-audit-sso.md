---
title: "Comment auditer l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], auditing
- SSO, auditing
- auditing [SSO]
- SSO database, auditing
ms.assetid: dc6d0726-fc31-4af2-9a23-8df9e3fc5836
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abea3028c2ec9fd2131b8fd17247476b6fdfa6f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-audit-sso"></a><span data-ttu-id="b18ee-102">Comment auditer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b18ee-102">How to Audit SSO</span></span>
<span data-ttu-id="b18ee-103">Le composant logiciel enfichable MMC ou la ligne de commande permet de définir les niveaux d'audit positif et négatif.</span><span class="sxs-lookup"><span data-stu-id="b18ee-103">You can use the MMC Snap-In or the command line to set both the positive and negative auditing levels.</span></span> <span data-ttu-id="b18ee-104">Les résultats de l'audit sont stockés dans les journaux des événements et des audits de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b18ee-104">Results of the auditing are stored in both the event logs and the audit logs of the database.</span></span>  
  
 <span data-ttu-id="b18ee-105">Les administrateurs SSO peuvent définir les niveaux d'audit positifs et négatifs selon leurs stratégies d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b18ee-105">SSO administrators can set the positive and negative audit levels that suit their corporate policies.</span></span> <span data-ttu-id="b18ee-106">Vous pouvez définir des audits positifs et négatifs sur l'un des niveaux suivants :</span><span class="sxs-lookup"><span data-stu-id="b18ee-106">You can set positive and negative audits to one of the following levels:</span></span>  
  
 <span data-ttu-id="b18ee-107">0 = Aucun</span><span class="sxs-lookup"><span data-stu-id="b18ee-107">0 = None</span></span>  
  
 <span data-ttu-id="b18ee-108">1 = Faible</span><span class="sxs-lookup"><span data-stu-id="b18ee-108">1 = Low</span></span>  
  
 <span data-ttu-id="b18ee-109">2 = Moyen</span><span class="sxs-lookup"><span data-stu-id="b18ee-109">2 = Medium</span></span>  
  
 <span data-ttu-id="b18ee-110">3 = Élevé.</span><span class="sxs-lookup"><span data-stu-id="b18ee-110">3 = High.</span></span> <span data-ttu-id="b18ee-111">Ce niveau émet plusieurs messages d’audit que possible.</span><span class="sxs-lookup"><span data-stu-id="b18ee-111">This level issues as many audit messages as possible.</span></span>  
  
 <span data-ttu-id="b18ee-112">La valeur par défaut pour l’audit positif est 0 (aucun), et la valeur par défaut pour l’audit négatif est 1(low).</span><span class="sxs-lookup"><span data-stu-id="b18ee-112">The default value for positive auditing is 0 (none), and the default value for negative auditing is 1(low).</span></span>  
  
 <span data-ttu-id="b18ee-113">Pour modifier le niveau d'audit de la base de données, vous devez mettre à jour la base de données SSO à l'aide d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="b18ee-113">To change the database level auditing, you must update the SSO database using an XML file.</span></span> <span data-ttu-id="b18ee-114">Voici un exemple de fichier XML pour la mise à jour de la base de données SSO :</span><span class="sxs-lookup"><span data-stu-id="b18ee-114">A sample XML file for updating the SSO database is:</span></span>  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### <a name="to-audit-single-sign-on-using-the-mmc-snap-in"></a><span data-ttu-id="b18ee-115">Pour activer l'audit de l'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="b18ee-115">To audit Single Sign-On using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b18ee-116">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="b18ee-116">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b18ee-117">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="b18ee-117">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b18ee-118">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b18ee-118">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b18ee-119">Sur le **propriétés système** boîte de dialogue, cliquez sur le **Audits** onglet.</span><span class="sxs-lookup"><span data-stu-id="b18ee-119">On the  **System Properties** dialog box, click the **Audits** tab.</span></span>  
  
5.  <span data-ttu-id="b18ee-120">Entrez les paramètres appropriés, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b18ee-120">Enter the appropriate settings, and click **OK**.</span></span>  
  
### <a name="to-audit-single-sign-on-using-the-command-line"></a><span data-ttu-id="b18ee-121">Pour activer l'audit de l'authentification unique de l'entreprise à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b18ee-121">To audit Single Sign-On using the command line</span></span>  
  
1.  <span data-ttu-id="b18ee-122">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="b18ee-122">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b18ee-123">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b18ee-123">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b18ee-124">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b18ee-124">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b18ee-125">Type **ssoconfig-auditlevel \<positive >\<négatif >**, où  **\<positive >** est le niveau de l’audit lorsque actions réussissent et  **\<négatif >** est le niveau de cas d’échouent des actions d’audit.</span><span class="sxs-lookup"><span data-stu-id="b18ee-125">Type **ssoconfig –auditlevel \<positive>\<negative>**, where **\<positive>** is the level of auditing when actions succeed, and **\<negative>** is the level of auditing when actions fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b18ee-126">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b18ee-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-audit-the-sso-database"></a><span data-ttu-id="b18ee-127">Pour activer l'audit de la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="b18ee-127">To audit the SSO database</span></span>  
  
1.  <span data-ttu-id="b18ee-128">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="b18ee-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b18ee-129">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b18ee-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b18ee-130">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b18ee-130">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b18ee-131">Type **ssomanage-updatedb \<mise à jour de fichier >**, où  **\<mise à jour de fichier >**est le chemin d’accès et le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="b18ee-131">Type **ssomanage –updatedb \<update file>**, where **\<update file>**is the path and name of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b18ee-132">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b18ee-132">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18ee-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b18ee-133">See Also</span></span>  
 <span data-ttu-id="b18ee-134">[Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="b18ee-134">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="b18ee-135">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b18ee-135">Using SSO</span></span>](../core/using-sso.md)