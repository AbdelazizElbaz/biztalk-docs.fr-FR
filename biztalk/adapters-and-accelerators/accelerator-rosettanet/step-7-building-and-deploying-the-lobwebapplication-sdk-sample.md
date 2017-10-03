---
title: "Étape 7 : Création et déploiement de l’exemple du Kit de développement LOBWebApplication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- double action tutorial, deploying solutions
ms.assetid: f61de666-ebda-4831-9669-598e9284e4c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa2504ebf80537e81e9ef0ee2f72e1e7afeb716d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-building-and-deploying-the-lobwebapplication-sdk-sample"></a>Étape 7 : Création et déploiement de l’exemple du Kit de développement LOBWebApplication
Dans cette étape, vous créez l'application métier utilisée par Fabrikam pour envoyer des demandes PIP (Partner Interface Process) à Contoso. Vous pouvez trouver le projet LOBWebApplication dans les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] dossier SDK. Pour exécuter l’application Web, vous devez créer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] répertoire virtuel de Internet Information Services (IIS), puis générer le projet LOBWebApplication.  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a>Pour créer le répertoire virtuel LOBWebApplication  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
2.  Dans la fenêtre Gestionnaire des Services Internet, développez **< nom_ordinateur > (ordinateur local)**, puis développez **Sites Web**.  
  
3.  Cliquez avec le bouton droit sur **Site web par défaut**, pointez sur **Nouveau**, puis cliquez sur **Répertoire virtuel**.  
  
4.  Sur le **Welcometo l’Assistant de création de répertoire virtuel** , cliquez sur **suivant**.  
  
5.  Dans la page **Alias du répertoire virtuel** , dans la zone **Alias** , tapez **LOBWebApplication**, puis cliquez sur **Suivant**.  
  
6.  Dans la page **Répertoire de contenu du site Web** , cliquez sur **Parcourir**. Dans la boîte de dialogue Rechercher un dossier, déplacer vers   ***\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBWebApplication**, et puis cliquez sur **OK**. Cliquez sur **Suivant**.  
  
7.  Dans la page **Autorisations d'accès au répertoire virtuel** , décochez l'option **Lecture**, sélectionnez **Exécuter les scripts (tels que ASP)**, puis cliquez sur **Suivant**.  
  
8.  Dans la page **Vous avez terminé l'Assistant Création de répertoire virtuel** , cliquez sur **Terminer** pour créer le répertoire virtuel.  
  
### <a name="to-exclude-the-lobwebapplication-web-site-from-the-sharepoint-configuration"></a>Pour exclure le site web LOBWebApplication de la configuration de SharePoint  
  
1.  cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
2.  Dans la page web **Administration centrale** , dans la section **Configuration du serveur virtuel** , sélectionnez **Étendre ou mettre à niveau le serveur virtuel**.  
  
3.  Si l'URL configurée sur l'ordinateur ne s'affiche pas, cliquez sur **Liste complète**.  
  
4.  Dans la page **Liste des serveurs virtuels** , cliquez sur **Site web par défaut**.  
  
5.  Dans la section **Gestion du serveur virtuel** , cliquez sur **Définir les chemins d'accès gérés**.  
  
6.  Dans la section **Ajouter un nouveau chemin d'accès** , dans la zone **Chemin d'accès** , tapez **/LOBWebApplication**.  
  
7.  Pour **Type**, sélectionnez **Chemin d'accès exclu**, puis cliquez sur **OK**.  
  
### <a name="to-build-the-lobwebapplication-project"></a>Pour générer le projet LOBWebApplication  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft Visual Studio 2008**, puis cliquez sur **Microsoft Visual Studio 2008**.  
  
2.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.  
  
3.  Dans la boîte de dialogue Ouvrir un projet, accédez au   ***\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBWebApplication**, sélectionnez le **LOBWebApplication.sln** fichier solution, puis cliquez sur **ouvrir**.  
  
4.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **http://localhost/LOBWebApplication**, puis cliquez sur **Ajouter une référence**.  
  
5.  Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**. Dans la boîte de dialogue Ajouter une référence, accédez au   ***\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\Bin** dossier.  
  
6.  Dans le dossier Bin, sélectionnez les assemblys **Microsoft.Solutions.BTARN.ConfigurationManager.dll** et **Microsoft.Solutions.BTARN.Shared.dll** , puis cliquez sur **Open.**  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une référence** .  
  
8.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **Solution 'LOBWebApplication'** , puis cliquez sur **Générer la solution**.  
  
9. Cliquez avec le bouton droit sur **default.aspx**, puis cliquez sur **Définir comme page de démarrage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Test du didacticiel Double Action](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)