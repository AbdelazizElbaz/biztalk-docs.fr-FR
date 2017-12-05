---
title: MIME (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, MIME/SMIME Encoder [pipeline component]
- examples, send pipelines
- MIME/SMIME Encoder [pipeline component], send pipelines
- MIME/SMIME Encoder [pipeline component], examples
- examples, MIME/SMIME Encoder [pipeline component]
ms.assetid: f76c720d-3798-4f15-a5f9-885ddf421d57
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec6e6e290761ba6d1be2ed08c8519e96c2846fa7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mime-biztalk-server-sample"></a>MIME (exemple BizTalk Server)
L'exemple MIME illustre l'exécution du codage MIME dans un pipeline d'envoi.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple permet de configurer le dossier MIMEIn en tant qu'emplacement de réception. Lorsque vous placez un fichier tel que le fichier d'exemple ImageInput.gif dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message contenu dans ce fichier comme suit :  
  
1.  Il récupère le fichier de message du dossier MIMEIn de l'emplacement de réception.  
  
2.  Dans le pipeline de réception, il transmet le message sans modification.  
  
3.  Dans la base de données MessageBox, il achemine le message au pipeline d'envoi  
  
4.  Dans le pipeline d'envoi, il exécute le codage MIME et place le fichier dans le dossier MIMEOut de l'adaptateur d'envoi.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Pipelines\MIME\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|ImageInput.GIF|Exemple de fichier d'entrée.|  
|SampleMimeEncoding.btproj<br /><br /> SampleMimeEncoding.sln|Fichiers projet et solution de l'exemple.|  
|SampleMimeEncodingBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|SendMimePipeline.btp|Fichier du pipeline d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec le composant Encodeur MIME.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple MIME.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Pipelines\MIME  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   création des dossiers d'entrée (MIMEIn) et de sortie (MIMEOut) associés à cet exemple dans le dossier :  
  
         \<*Exemples de chemin d’accès*\>\Pipelines\MIME  
  
    -   compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
        > [!NOTE]
        >  Cet exemple affiche l’avertissement suivant lors de la création et la liaison des ports :  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "MIMEReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Si vous exécutez cet exemple à partir d’un emplacement autre qu’où il est installé, vous devez d’abord ajouter une référence à la **Microsoft.BizTalk.Pipeline.Components** assembly.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de l'utilitaire.NET Framework Strong Name (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu. Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple MIME.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Placez une copie du fichier ImageInput.gif dans le dossier MIMEIn.  
  
2.  Observez le fichier texte créé dans le dossier MIMEOut. Le nom du fichier texte a pour base le GUID de l'ID du message. Ce fichier inclut le contenu MIME du fichier d'entrée ImageInput.gif.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)