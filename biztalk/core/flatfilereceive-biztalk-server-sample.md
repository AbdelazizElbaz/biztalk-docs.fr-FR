---
title: FlatFileReceive (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bd9e8d-6ed9-49c4-8437-c0c8b2a9a78d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db996437cce8cb6f89fb00b589fcbc95429e72f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="flatfilereceive-biztalk-server-sample"></a>FlatFileReceive (exemple BizTalk Server)
L'exemple FlatFileReceive illustre la manière dont vous pouvez utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour traiter un fichier plat en un fichier .xml équivalent.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple permet de configurer le dossier FFInput en tant qu'emplacement de réception. Lorsque vous placez un fichier tel que le fichier d'exemple FlatFileReceive_in.txt dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message contenu dans ce fichier comme décrit dans la procédure suivante :  
  
1.  Lecture du message à partir du fichier d'entrée dans le dossier de l'emplacement de réception FFInput.  
  
2.  Dans le pipeline de réception, le composant Désassembleur de fichier plat convertit le message au format de fichier plat en un message XML équivalent.  
  
3.  Dans la base de données MessageBox, le message est acheminé vers un port d'envoi FILE qui écrit le message XML dans un fichier se trouvant dans le dossier FFOutput de l'adaptateur d'envoi.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Dans cet exemple, la plus grande partie de la conception de base est imposée par l'exemple de message. Les messages de fichier plat doivent être désassemblés à l'aide du Désassembleur de fichier plat et d'un schéma de fichier plat au sein d'un pipeline de réception personnalisé. Ces critères de conception sont récapitulés dans le tableau suivant.  
  
|Élément de conception|Raison(s) sélectionnée(s)|  
|--------------------|--------------------------|  
|Pipeline de réception personnalisé|-Le pipeline personnalisé utilise le désassembleur de fichier plat et un schéma de fichier plat pour convertir en entrant des messages de commande d’achat. Le Désassembleur de fichier plat n'est pas un pipeline de réception en lui-même et ne peut donc pas être utilisé lors de la configuration d'un pipeline de réception dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management console.|  
|Schéma de fichier plat|-Définir tous les même caractéristiques d’enregistrement et champ (dont la structure) comme un schéma XML et fournissent un mécanisme permettant de définir l’ensemble des caractéristiques de fichier plat requis pour convertir un message d’instance de fichier plat dans une instance XML équivalente message (ou vice versa).|  
|Filtre d'abonnement|-Le filtre d’abonnement réalise l’acheminement réel en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.|  
|XMLTransmit|-Effectue l’assemblage de base de la sortie des messages XML quand cela est nécessaire. Le pipeline PassThruTransmit ne fournit aucune prise en charge supplémentaire.|  
  
 Ces éléments sont combinés afin de générer une solution qui accepte les messages de bon de commande au format de fichier plat dans l'emplacement de réception et qui les convertisse en représentations XML dans l'emplacement d'envoi.  
  
 Les considérations suivantes s’appliquent à la conception de cet exemple :  
  
-   Le schéma de fichier plat (PO.xsd) contient des annotations étendues décrivant la structure du fichier plat de bon de commande. Ces fichiers peuvent être créés manuellement, mais un grand nombre peut être généré à l'aide de l'Assistant Fichier plat.  
  
-   Le schéma de fichier plat utilise la valeur Unqualified de l'attribut elementFormDefault. Cette méthode permet d'obtenir des résultats corrects, mais avec des qualifications d'espace de noms (xmlns) XML supplémentaires et inattendues. Pour éviter ce problème, utilisez la valeur Qualified d'elementFormDefault.  
  
-   Le pipeline d'envoi utilisé est XmlTransmit. Utilisez le pipeline PassThruTransmit lorsque la rétrogradation des propriétés ou d'autres traitements de messagerie ne sont pas requis dans le port d'envoi.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileReceive\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|FFReceivePipeline.btp|Fichier du pipeline de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec le composant Désassembleur de fichier plat.|  
|FlatFileReceive.btproj, FlatFileReceive.sln|Fichiers projet et solution de l'exemple.|  
|FlatFileReceive_in.txt|Exemple de fichier d'entrée.|  
|FlatFileReceiveBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|PO.xsd|Schéma pour le fichier plat entrant.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez cet exemple comme base de votre propre solution de traitement de fichier plat. Vous pouvez étendre un grand nombre des éléments de conception utilisés dans le cadre de cet exemple pour répondre à vos besoins spécifiques.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileReceive  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (FFInput) et de sortie (FFOutput) associés à cet exemple dans le dossier :  
  
         *\<Exemples de chemin d’accès\>*\Pipelines\AssemblerDisassembler\FlatFileReceive  
  
    -   Compilation et déploiement du projet Visual Studio pour cet exemple.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
        > [!NOTE]
        >  Cet exemple affiche l’avertissement suivant lors de la création et la liaison des ports : `Warning: Receive handler not specified for receive location "FlatFileReceive_RL"; updating with first receive handler with matching transport type.` vous pouvez ignorer ces avertissements. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
> [!NOTE]
>  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
1.  Placez une copie du fichier FlatFileReceive_in.txt dans le dossier FFInput.  
  
2.  Observez le fichier .xml créé dans le dossier FFOutput. Le nom du fichier de sortie a pour base le GUID de l'ID du message. Ce fichier contient l'équivalent XML du fichier plat placé dans le dossier de réception.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Les scripts de configuration Setup.bat et Cleanup.bat dépendent des scripts Windows Management Instrumentation (WMI) d'administration suivants :  
  
-   Démarrage du port d'envoi\StartSendPort.vbs  
  
-   Activation de l'emplacement de réception\EnableRecLoc  
  
-   Suppression du port d'envoi\RemoveSendPort  
  
 Les fichiers de commandes d'installation et de désinstallation utilisent BTSTask comme suit :  
  
-   **BTSTask ImportBindings** pour appliquer le fichier de liaison et de créer l’application, les ports et les liaisons  
  
-   **BTSTask RemoveApp** à supprimer flatfilereceiveapplication.  
  
## <a name="see-also"></a>Voir aussi  
-  [Pipelines\AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
-  [Composant de pipeline Désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md)   
-  [Schémas de fichier plat](../core/flat-file-schemas.md)   
-  [Pipelines par défaut](../core/default-pipelines.md)   
-  **Exemples de scripts WMI**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [Référence de la ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
-  [FlatFileSend (exemple BizTalk Server)](../core/flatfilesend-biztalk-server-sample.md)