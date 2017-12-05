---
title: FlatFileSend (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52dd0018-e272-40db-a26a-509d444d7106
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a9e967a8127a07b561e950b084bf799b0e2a4ee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="flatfilesend-biztalk-server-sample"></a>FlatFileSend (exemple BizTalk Server)
L'exemple FlatFileSend illustre la manière dont vous pouvez utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour traiter un fichier XML en un fichier plat équivalent.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple permet de configurer le dossier FFInput en tant qu'emplacement de réception. Lorsque vous placez un fichier tel que le fichier d'exemple FlatFileSend_in.xml dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message contenu dans ce fichier comme indiqué dans la procédure suivante :  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lit le message à partir du fichier d'entrée dans le dossier de l'emplacement de réception FFInput.  
  
2.  Le message est transmis via un pipeline de réception XML.  
  
3.  Dans la base de données MessageBox, le message est acheminé vers un port d'envoi FILE qui dispose d'un pipeline d'envoi configuré avec un composant Assembleur de fichier plat. Ce dernier convertit le message XML en une représentation de fichier plat équivalente à l'aide d'un schéma de fichier plat.  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] écrit le message converti dans un fichier texte situé dans le dossier FFOutput de l'adaptateur de réception.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Dans cet exemple, la plus grande partie de la conception de base est imposée par l'exemple de message. Les messages de fichier plat doivent être assemblés à l'aide de l'Assembleur de fichier plat et un schéma de fichier plat doit l'être au sein d'un pipeline d'envoi personnalisé. Ces critères de conception sont récapitulés dans le tableau suivant.  
  
|Élément de conception|Raison(s) sélectionnée(s)|  
|--------------------|--------------------------|  
|Pipeline d'envoi personnalisé|-Le pipeline personnalisé utilise l’assembleur de fichier plat et un schéma de fichier plat pour convertir les messages de l’instance au format de fichier plat ; l’assembleur de fichier plat n’est pas lui-même un pipeline et ne peut pas être utilisé lors de la configuration d’un pipeline d’envoi dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console de gestion.|  
|Schéma de fichier plat|-Définir tous les même caractéristiques d’enregistrement et champ (dont la structure) comme un schéma XML et fournit un mécanisme pour définir l’ensemble des caractéristiques de fichier plat requis pour convertir un message d’instance XML dans un message de fichier plat (ou vice versa).|  
|Filtre d'abonnement|-Le filtre d’abonnement réalise l’acheminement réel en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.|  
|XMLReceive|-Effectue le traitement des messages XML entrants. Dans le cadre de cet exemple, une représentation XML d'un bon de commande est utilisée comme message source.|  
  
 Ces éléments sont combinés afin de générer une solution qui accepte les messages de bon de commande au format XML dans l'emplacement de réception et qui les convertisse en bon de commande de fichier plat dans l'emplacement d'envoi.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileSend  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|FlatFileSend.btproj, FlatFileSend.sln|Fichiers projet et solution de l'exemple.|  
|FlatFileSendBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|FlatFileSend_in.xml|Exemple de fichier d'entrée.|  
|PO.xsd|Schéma pour le fichier plat sortant.|  
|SendPipeline.btp|Fichier du pipeline d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec le composant Assembleur de fichier plat.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez cet exemple comme base de votre propre solution de traitement de fichier plat. Vous pouvez étendre un grand nombre des éléments de conception utilisés dans le cadre de cet exemple pour répondre à vos besoins spécifiques.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileSend  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (FFInput) et de sortie (FFOutput) associés à cet exemple dans le dossier :  
  
         *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileSend  
  
    -   compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et la liaison des ports : `Warning: Receive handler not specified for receive location "FlatFileSend_RL"; updating with first receive handler with matching transport type. Warning: Host not specified for orchestration "FlatFileSend"; updating with first available host.` vous pouvez ignorer ces avertissements. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
> [!NOTE]
>  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
1.  Placez une copie du fichier FlatFileSend_in.xml dans le dossier FFInput.  
  
2.  Observez le fichier texte créé dans le dossier FFOutput. Le nom du fichier texte est basé sur le GUID de l’ID de message. Ce fichier contient le fichier plat équivalent au fichier d'entrée XML FlatFileSend_in.xml.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Les scripts de configuration Setup.bat et Cleanup.bat dépendent des scripts Windows Management Instrumentation (WMI) d'administration suivants :  
  
-   Démarrage du port d'envoi\StartSendPort.vbs  
  
-   Activation de l'emplacement de réception\EnableRecLoc  
  
-   Suppression du port d'envoi\RemoveSendPort  
  
 Les fichiers de commandes d'installation et de désinstallation utilisent BTSTask comme suit :  
  
-   **BTSTask ImportBindings** pour appliquer le fichier de liaison et de créer l’application, les ports et les liaisons  
  
-   **BTSTask RemoveApp** à supprimer flatfilesendapplication.  
  
## <a name="see-also"></a>Voir aussi  
-  [Schémas de fichier plat](../core/flat-file-schemas.md)   
-  [Pipelines par défaut](../core/default-pipelines.md)   
-  [Pipelines\AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
-  **Exemples de scripts WMI**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [Référence de la ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
-  [FlatFileReceive (exemple BizTalk Server)](../core/flatfilereceive-biztalk-server-sample.md)