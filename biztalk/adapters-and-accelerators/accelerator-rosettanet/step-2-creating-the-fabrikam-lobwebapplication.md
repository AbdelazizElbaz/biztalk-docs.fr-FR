---
title: "Étape 2 : Création de Fabrikam LOBWebApplication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOBWebApplication
- LOBWebApplication
ms.assetid: 2ff8bd20-7fbc-4e16-b177-bb4afac7f7c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed64aac8ea0cf4073f3085f4491f607373d721b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-the-fabrikam-lobwebapplication"></a>Étape 2 : Création de Fabrikam LOBWebApplication
Dans cette étape, vous créez l’application métier utilisée par Fabrikam pour envoyer une demande PIP 3A2 à Contoso. Le projet LOBWebApplication est installé dans le [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel. Pour exécuter l’application Web, vous devez créer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] répertoire virtuel de Internet Information Services (IIS) et générer le projet LOBWebApplication.  
  
> [!NOTE]
>  Si vous terminé le didacticiel DoubleAction, il est inutile d’effectuer cette étape.  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a>Pour créer le répertoire virtuel LOBWebApplication  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet**.  
  
    > [!NOTE]
    >  Si vous avez déjà fait le didacticiel Double Action, vous aurez déjà créé le répertoire virtuel LOBWebApplication pour ce didacticiel. Dans ce cas, vous n’avez pas à effectuer ces étapes. Toutefois, avoir à modifier les autorisations pour le répertoire virtuel à partir de **exécuter des scripts** à **en lecture**.  
  
2.  Dans le Gestionnaire des Services Internet, développez **< nom_ordinateur > (ordinateur local)**, puis développez **Sites Web**.  
  
3.  Cliquez avec le bouton droit sur **Site web par défaut**, pointez sur **Nouveau**, puis cliquez sur **Répertoire virtuel**.  
  
4.  Sur le **Welcometo la page de l’Assistant Création de répertoire virtuel**, cliquez sur **suivant**.  
  
5.  Dans la page **Alias du répertoire virtuel** , dans la zone **Alias** , tapez **LOBWebApplication**, puis cliquez sur **Suivant**.  
  
6.  Sur le **répertoire de contenu du Site Web** , cliquez sur **Parcourir**, sélectionnez le  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBWebApplication** dossier, puis cliquez sur **OK**. Cliquez sur **Suivant**.  
  
7.  Sur le **autorisations d’accès de répertoire virtuel** , cliquez sur **suivant**.  
  
8.  Cliquez sur **Terminer** pour créer le répertoire virtuel.  
  
### <a name="excluding-lobwebapplication-from-sharepoint"></a>À l’exclusion de LOBWebApplication à partir de SharePoint  
  
1.  cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
    > [!NOTE]
    >  Si vous avez déjà fait le didacticiel Double Action, vous serez déjà avez exclu le répertoire virtuel LOBWebApplication SharePoint pour ce didacticiel. Dans ce cas, vous n’avez pas à effectuer ces étapes.  
  
2.  Sur le **Administration centrale** page, dans le **Configuration du serveur virtuel** section, sélectionnez **étendre ou mise à niveau le serveur virtuel**.  
  
3.  Si l'URL configurée sur l'ordinateur ne s'affiche pas, cliquez sur **Liste complète**.  
  
4.  Sélectionnez **Site Web par défaut**.  
  
5.  Dans la section **Gestion du serveur virtuel** , cliquez sur **Définir les chemins d'accès gérés**.  
  
6.  Dans le **ajouter un nouveau chemin** section, dans le **chemin d’accès** , tapez « / LOBWebApplication ». Pour **Type**, sélectionnez **Chemin d'accès exclu**, puis cliquez sur **OK**.  
  
### <a name="to-build-the-lobwebapplication-project"></a>Pour générer le projet LOBWebApplication  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  À partir de la **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **Project\Solution**.  
  
3.  Dans la boîte de dialogue Ouvrir un projet dans **Regarder dans**, atteindre  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\ SDK\LOBWebApplication** , sélectionnez le **LOBWebApplication.sln** solution, puis cliquez sur **ouvrir**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le nœud supérieur (http://localhost/LOBWebApplication), puis cliquez sur **ajouter une référence**.  
  
5.  Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir** et déplacer vers  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\bin**.  
  
6.  **Sélectionnez le Microsoft.Solutions.BTARN.ConfigurationManager.dll et Microsoft.Solutions.BTARN.Shared.dll** assemblys **puis cliquez sur OK.**  
  
7.  Sur le **générer** menu, cliquez sur **générer le Site Web**.  
  
### <a name="to-run-the-lobwebapplication-project"></a>Pour exécuter le projet LOBWebApplication  
  
1.  Dans l’Explorateur de solutions, cliquez sur **default.aspx**, puis sélectionnez **définir comme Page de démarrage**.  
  
2.  Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Test de la Solution](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)