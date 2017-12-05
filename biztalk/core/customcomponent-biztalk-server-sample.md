---
title: CustomComponent (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
- messages, streamed
- pipeline components [custom], configuring
ms.assetid: ed0da9f5-8cc7-4528-be8c-35b80744fd38
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fd774848dec1ae54541e749a0cc551bf7c42d49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="customcomponent-biztalk-server-sample"></a>CustomComponent (exemple BizTalk Server)
L'exemple CustomComponent présente la création et l'utilisation d'un composant de pipeline personnalisé qui modifie un message transmis. Cet exemple illustre également la configuration d'un composant de pipeline personnalisé dans le Concepteur de pipeline.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple implémente un composant de pipeline personnalisé qui peut ajouter des chaînes avant ou après le message d'entrée. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message en mode diffusion, ce qui signifie que le message entier n'est jamais chargé en mémoire. Le composant de pipeline personnalisé est présenté à l'aide de la séquence d'étapes suivante :  
  
1.  BizTalk récupère un message texte à partir d'un fichier dans un dossier spécifique.  
  
2.  Le message texte est envoyé via un pipeline de réception contenant le composant de pipeline personnalisé FixMsg. Vous configurez ce composant pour insérer une chaîne au début du message.  
  
3.  Vous envoyez le message texte obtenu via un pipeline d'envoi contenant le composant de pipeline personnalisé FixMsg. Vous configurez le composant pour ajouter une chaîne à la fin du message.  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] écrit le message texte obtenu dans un fichier dans un dossier spécifique.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Pipelines\CustomComponent\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|Input.txt|Exemple de fichier d'entrée.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \FixMsg :<br /><br /> AssemblyInfo.cs, FixMsg.csproj, FixMsg.sln|Fichiers de projet, de solution et d'informations de l'assembly pour la partie du composant de pipeline personnalisé de cet exemple.|  
|Dans le dossier \FixMsg :<br /><br /> FixMsg.cs|Implémente les interfaces de composant de pipeline.|  
|Dans le dossier \FixMsg :<br /><br /> FixMsgStream.cs|Implémente un wrapper pour le **System.IO.Stream** (classe), l’activation de traitement de flux de données.|  
|Dans le dossier \FixMsg :<br /><br /> FixMsgDescription.cs|Fournit des méthodes pour l'accès et l'affichage des ressources de l'interface utilisateur de composant dans le Concepteur de pipeline.|  
|Dans le dossier \FixMsg :<br /><br /> FixMsg.resx|Contient des descriptions de propriété, une icône et des messages d'erreur.|  
|Dans le dossier \PipelineComponentSample :<br /><br /> PipelineComponentSample.btproj, PipelineComponentSample.sln|Fichiers de projet et de solution pour la partie du projet BizTalk de cet exemple.|  
|Dans le dossier \PipelineComponentSample :<br /><br /> PipelineComponentSampleBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Dans le dossier \PipelineComponentSample :<br /><br /> FixMsgReceivePipeline.btp, FixMsgSendPipeline.btp|Pipelines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant le composant de pipeline personnalisé FixMsg, pour les pipelines de réception et d'envoi, respectivement.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-customcomponent-sample"></a>Pour créer et initialiser l'exemple CustomComponent  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Pipelines\CustomComponent  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier :  
  
         \<*Exemples de chemin d’accès*\>\Pipelines\CustomComponent  
  
    -   Compilation et déploiement des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :  
        >   
        >  `Warning: Receive handler not specified for receive location "PCReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "CustomComponent"; updating with first available host.`  
        >   
        >  Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Utilisez cette paire de clés pour signer les assemblys obtenus.  
  
> [!NOTE]
>  Pour annuler les modifications apportées par Setup.bat, arrêtez puis redémarrez l'instance de l'hôte à partir de la console MMC Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ensuite, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-customcomponent-sample"></a>Pour exécuter l'exemple CustomComponent  
  
1.  Collez une copie du fichier texte Input.txt dans le dossier In.  
  
2.  Observez le fichier texte créé dans le dossier Out. Ce fichier contient le fichier Input.txt avec un texte supplémentaire inséré au début (par le pipeline de réception) et à la fin (par le pipeline d'envoi). Le format du nom de ce fichier est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le message .  
  
## <a name="comments"></a>Commentaires  
 Pour afficher les pipelines préconfigurés dans le Concepteur de pipeline, procédez comme suit :  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur ReceivePipeline.btp pour ouvrir le pipeline de réception dans le Concepteur de pipeline. Notez que le composant FixMsg est placé dans le **Validate** étape du pipeline de réception.  
  
2.  Cliquez sur le composant FixMsg dans le **Validate** étape sur l’aire de conception. Dans la fenêtre Propriétés, vous pouvez voir les propriétés de configuration du composant de pipeline. Observez que la **PrependData** est définie sur **chaîne du pipeline de réception de données à ajouter dans**.  
  
3.  Dans l'Explorateur de solutions, double-cliquez sur SendPipeline.btp pour ouvrir le pipeline d'envoi dans le Concepteur de pipeline. Notez que le composant FixMsg est placé dans le **préassembler** étape du pipeline d’envoi.  
  
4.  Cliquez sur le composant FixMsg dans **préassembler** étape sur l’aire de conception. Notez que la **AppendData** est définie sur **chaîne du pipeline d’envoi de données à ajouter dans**.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)