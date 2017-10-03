---
title: EnvelopeProcessing (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, envelopes
- flat files, processing
- examples, flat files
- examples, messages
- examples, envelopes
- envelopes, messages
- flat files, examples
- envelopes, examples
ms.assetid: b4cd979b-c7b4-446c-be29-c9f3169afa1f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee15dc6fffefd550a5b12c662d4df76ca09c1fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="envelopeprocessing-biztalk-server-sample"></a>EnvelopeProcessing (exemple BizTalk Server)
L'exemple EnvelopeProcessing illustre le traitement des messages et des enveloppes de message dans les pipelines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En outre, il indique comment traiter les messages de fichier plat dans des messages XML.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple configure le dossier EnvInput en tant qu'emplacement de réception. Lorsque vous placez un fichier (tel que le fichier d'exemple EnvelopeProcessing_in.txt) dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite les messages de ce fichier en procédant comme suit :  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère le fichier de message du dossier EnvInput de l'emplacement de réception.  
  
2.  Dans le pipeline de réception, le composant de pipeline Désassembleur de fichier plat supprime l'en-tête et le code de fin des messages de fichier plat et les convertit en messages individuels.  
  
3.  Dans la base de données MessageBox, les messages sont routés vers le port d'envoi à l'aide de filtres d'abonnement.  
  
4.  Dans le pipeline d'envoi du port d'envoi, le composant de pipeline Assembleur XML encapsule les messages dans des enveloppes XML, puis les place dans le dossier EnvOutput de l'adaptateur d'envoi.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 La conception de cet exemple devait répondre à deux exigences de base :  
  
-   Recevoir et traiter un message de fichier plat contenant un ou plusieurs bons de commande.  
  
-   Envoyer un message XML contenant un bon de commande et les informations d'expéditeur à un répertoire pour récupération par un système de traitement principal.  
  
 Pour répondre à ces exigences, une combinaison de schémas fichier plat/XML et de pipelines personnalisés a été utilisée. Ces critères de conception sont récapitulés dans le tableau suivant.  
  
|Élément de conception|Raison(s) sélectionnée(s)|  
|--------------------|--------------------------|  
|Pipeline de réception personnalisé|-Utilise le désassembleur de fichier plat et les schémas de fichier plat pour convertir des messages de commande d’achat entrant.|  
|Schémas de fichier plat pour l'en-tête, le corps et le code de fin du message|-Définit toutes les même caractéristiques d’enregistrement et champ (dont la structure) que les schémas XML et fournissent un mécanisme permettant de définir l’ensemble des caractéristiques de fichier plat requis pour convertir un message d’instance de fichier plat dans une instance XML équivalente message (ou vice versa).<br />-Schémas d’en-tête, corps et code de fin sont utilisés pour fractionner le corps en blocs discrets pour le traitement.|  
|Schéma d'enveloppe|-Utilisé pour encapsuler des bons de commande individuels avec les informations de l’en-tête.|  
|Filtre d'abonnement|-Le filtre d’abonnement réalise l’acheminement réel en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.|  
|Pipeline d'envoi personnalisé|-Utilise l’assembleur XML et une combinaison de schémas d’enveloppe et le corps pour convertir les messages de l’instance au format XML.|  
  
 Les points suivants s'appliquent à la conception de cet exemple :  
  
-   Le schéma de fichier plat (PO.xsd) contient des annotations étendues décrivant la structure du fichier plat de bon de commande. Ces fichiers peuvent être créés manuellement, mais un grand nombre peut être généré à l'aide de l'Assistant Fichier plat.  
  
-   Le schéma de fichier plat du bon de commande (PO.xsd) utilise la valeur Unqualified d'elementFormDefault. Cela produit des résultats corrects, mais avec des qualifications xmlns supplémentaires et inattendues. Pour éviter ce problème, utilisez la valeur Qualified d'elementFormDefault.  
  
-   Les schémas de fichier plat d'en-tête et de code de fin sont utilisés pour séparer les données d'en-tête et de code de fin du message. Les propriétés du schéma d'en-tête, de document et de code de fin du Désassembleur de fichier plat sont définies respectivement sur le schéma d'en-tête, le bon de commande et le schéma de code de fin.  
  
-   Le schéma d'enveloppe XML combine des éléments de l'en-tête et du bon de commande pour produire un message XML unique. Le schéma d’en-tête promeut le champ Source dans le champ SourceParty dans le **BTS.bts_system_properties** espace de noms ; le schéma d’enveloppe promeut cette même valeur, à l’origine de sa rétrogradation dans le message sortant.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 `<Samples Path>`\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|EnvelopeProcessing.btproj, EnvelopeProcessing.sln|Fichiers projet et solution de l'exemple.|  
|EnvelopeProcessing_in.txt|Exemple de fichier d'entrée.|  
|Header.xsd, PO.xsd, Trailer.xsd|Schéma pour l'en-tête, le corps et le code de fin du fichier plat, respectivement.|  
|XmlEnvelope.xsd|Schéma de l'enveloppe XML sortante.|  
|EnvReceivePipeline.btp, EnvSendPipeline.btp|Fichiers de pipeline de réception et d'envoi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec respectivement les composants de pipeline Désassembleur de fichier plat et Assembleur XML.|  
|EnvelopeProcessingBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez cet exemple comme base de votre propre solution de traitement de fichier plat. Vous pouvez étendre un grand nombre des éléments de conception utilisés dans le cadre de cet exemple pour répondre à vos besoins spécifiques. Voici quelques exemples :  
  
-   Améliorer l'exemple pour écrire une version de fichier plat de chaque bon de commande en plus de la version XML. Pour ce faire, créez un pipeline d'envoi personnalisé et utilisez l'Assembleur de fichier plat. Sur l'Assembleur de fichier plat, spécifiez les schémas d'en-tête, de bon de commande et de code de fin de fichier plat. Lorsqu'il est utilisé dans un port d'envoi, il génère des bons de commande individuels avec les informations d'en-tête et de code de fin.  
  
-   Améliorer l'enveloppe avec davantage d'informations du bon de commande. Pour écrire des informations supplémentaires dans le message sortant, vous devez promouvoir le nom « expédier à » ou d'autres champs à l'aide de Promotion rapide, ajouter des champs à l'enveloppe, puis promouvoir les champs d'enveloppe dans le même champ. Lorsque le message est traité par l'assembleur, les propriétés promues sont rétrogradées et copiées dans le message sortant.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-envelopeprocessing-sample"></a>Pour créer et initialiser l'exemple EnvelopeProcessing  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     *\<Exemples de chemin d’accès >*\Pipelines\AssemblerDisassembler\EnvelopeProcessing  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (EnvInput) et de sortie (EnvOutput) associés à cet exemple dans le dossier :  
  
         *\<Exemples de chemin d’accès >*\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  
  
    -   Compilation et déploiement du projet Visual Studio pour cet exemple.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
         Cet exemple affiche les avertissements suivants lors de la création et liaison des ports :  
  
        ```  
        Warning: Receive handler not specified for receive location "EnvelopeProcessing_RL"; updating with first receive handler with matching transport type.  
        Warning: Host not specified for orchestration "EnvelopeProcessing"; updating with first available host.  
        ```  
  
         Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
> [!NOTE]
>  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-envelopeprocessing-sample"></a>Pour exécuter l'exemple EnvelopeProcessing  
  
1.  Placez une copie du fichier EnvelopeProcessing_in.txt dans le dossier EnvInput.  
  
2.  Observez les trois fichiers .xml créés dans le dossier EnvOutput. Les noms de ces fichiers .xml sont basés sur le GUID de l'ID de message. Ils contiennent les messages extraits du fichier d'entrée et encapsulés dans des enveloppes.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Les scripts de configuration Setup.bat et Cleanup.bat dépendent des scripts Windows Management Instrumentation (WMI) d'administration suivants :  
  
-   Démarrage du port d'envoi\StartSendPort.vbs  
  
-   Activation de l'emplacement de réception\EnableRecLoc  
  
-   Suppression du port d'envoi\RemoveSendPort  
  
 Les fichiers de commandes d'installation et de désinstallation utilisent BTSTask comme suit :  
  
-   **BTSTask ImportBindings** pour appliquer le fichier de liaison et de créer l’application, les ports et les liaisons  
  
-   **BTSTask RemoveApp** à supprimer flatfilereceiveapplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)