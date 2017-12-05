---
title: SendMail | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- SMTP adapters
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6cf0243eccb6a38dc121cfe06a60e30fa0c26c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sendmail"></a>SendMail
L'exemple SendMail montre comment utiliser l'adaptateur SMTP (Simple Mail Transfer Protocol) pour envoyer des messages électroniques à partir d'une orchestration Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les informations dynamiques utilisées pour envoyer les messages électroniques sont extraites d'un message XML à l'aide de la fonctionnalité de promotion de propriétés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple envoie un message électronique à l'aide d'informations obtenues à partir des propriétés promues à partir d'un message de bon de commande (PO) XML entrant, en procédant comme suit :  
  
1.  L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] extrait un message de PO XML entrant.  
  
2.  Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration promeut le **PONumber** et **messagerie** propriétés pour faciliter l’accès à l’avenir.  
  
3.  L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les valeurs des propriétés promues pour définir l'adresse de destination du port d'envoi dynamique et l'objet du message électronique.  
  
4.  L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie le message électronique construit via l'adaptateur SMTP.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\AdaptersUsage\SendMail\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AssemblyInfo.cs, SendMail.btproj, SendMail.sln|Fournit des fichiers d'informations de projet, de solution et d'assembly pour cet exemple.|  
|Cleanup.bat|Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.|  
|PropertySchema.xsd, PurchaseOrder.xsd|Fournit des schémas respectivement pour les propriétés que vous voulez promouvoir et pour le message de PO XML.|  
|ReceiveSend.odx|Fournit une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui traite le message de PO XML entrant et envoie un message électronique sur la base des informations figurant dans le message reçu.|  
|SendMailInput.xml|Contient un exemple de fichier d'entrée avec un bon de commande spécifié à l'aide de XML.|  
|Setup.bat|Crée et initialise l'exemple. **Remarque :** ce fichier d’installation crée et lie les ports, et ainsi de suite, à l’aide d’un mécanisme autre que la majeure partie de l’installation de fichiers pour les exemples du Kit de développement logiciel. Il ne nécessite pas de fichier .xml compagnon.|  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\AdaptersUsage\SendMail  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Crée le dossier d'entrée suivant pour cet exemple :  
  
         \<*Exemples de chemin d’accès*\>\AdaptersUsage\SendMail\In  
  
    -   compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;  
  
    -   Démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
        > [!NOTE]
        >  Avant de tenter d'exécuter cet exemple, vous devez confirmer que BizTalk n'a signalé aucune erreur durant le processus de création et d'initialisation.  
  
        > [!NOTE]
        >  Si vous choisissez d'ouvrir et de créer le projet dans cet exemple sans exécuter le fichier Setup.bat, vous devez d'abord créer une paire de clés de nom fort en utilisant l'utilitaire .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
        > [!NOTE]
        >  Pour annuler les modifications apportées par Setup.bat, exécutez le fichier Cleanup.bat et supprimez tous recevant, précédés de SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail de ports d’envoi. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
3.  Dans le **Administration de BizTalk Server** de la console, localisez le port de réception préfixé par SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail. Mettre à jour l’emplacement de réception pour ce port de réception pointer vers un répertoire sur votre système de fichiers à utiliser comme emplacement d’entrée.  
  
4.  À l’aide d’un programme tel que le bloc-notes, modifiez le fichier SendMailInput.xml afin que le **messagerie** élément spécifie une adresse électronique à laquelle vous souhaitez recevoir le message électronique généré par cet exemple.  
  
5.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
6.  Dans le **Administration de BizTalk Server** de la console, développez l’arborescence du groupe BizTalk.  
  
7.  Développez le **paramètres de plateforme** arborescence dans le volet gauche.  
  
8.  Développez le **cartes** dossier, cliquez sur le **SMTP** nœud, puis double-cliquez sur la ligne de l’adaptateur SMTP dans le volet droit.  
  
9. Dans le **SMTP - propriétés du Gestionnaire d’adaptateur** boîte de dialogue, cliquez sur **propriétés**.  
  
10. Dans le **propriétés du Transport SMTP** boîte de dialogue le **propriétés** onglet, entrez les valeurs appropriées pour le **nom du serveur SMTP** et **à partir de (courrier électronique adresse)** propriétés, puis cliquez sur **OK**.  
  
     Ces valeurs seront utilisées pour créer l'adresse électronique De pour tous les messages électroniques envoyés via cet adaptateur SMTP.  
  
    > [!NOTE]
    >  Si vous devez vous authentifier auprès de votre serveur SMTP, vous devez veiller à ce que l'adresse électronique De appartienne au même compte que celui que vous utilisez pour l'authentification.  
  
11. Arrêtez, puis redémarrez le service BizTalk (BizTalkServerApplication) de façon à ce que l'orchestration adopte ces modifications.  
  
### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Placez une copie du fichier modifié SendMailInput.xml dans le dossier d'entrée.  
  
2.  Observez l'arrivée d'un message électronique à l'adresse spécifiée au cours de la procédure précédente.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs- Utilisation](../core/adapter-samples-usage.md)