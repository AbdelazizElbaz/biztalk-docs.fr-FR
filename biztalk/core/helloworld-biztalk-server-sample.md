---
title: HelloWorld (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, messages
ms.assetid: 4416029a-ca76-45a4-b66c-b44cb71ded58
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a5e8057837012d27a877117a169c2cd04fa3d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="helloworld-biztalk-server-sample"></a>HelloWorld (exemple BizTalk Server)
L'exemple HelloWorld illustre l'utilisation des orchestrations BizTalk pour convertir un message XML (un bon de commande) en un type de message lié mais distinct (une facture).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple configure le **dans** dossier comme emplacement de réception. Lorsque vous placez un fichier, tel que le fichier d’exemple **SamplePOInput.xml**, dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message en procédant comme suit :  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère le message de bon de commande XML dans le dossier de l'emplacement de réception.  
  
2.  L'orchestration utilise le fichier de mappage pour créer une facture XML à partir du bon de commande XML.  
  
3.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]place le message de facture XML résultant dans l’adaptateur d’envoi **hors** dossier.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Dans un scénario d'échange de messages intersociétés, il est souvent nécessaire de convertir les messages entrants reçus des partenaires commerciaux dans un format reconnu par les applications internes. Cet exemple utilise un **réception** mettre en forme un **transformer** mettre en forme et un **envoyer** forme pour obtenir ce résultat. Le **transformer** forme joue un rôle important dans cet exemple, car il est où la conversion de format de message se produit. Vous faites glisser un **transformer** mettre en forme dans votre orchestration et de configurer le message source, le nom de la carte et le message de destination pour celle-ci. Lors de l'exécution, le message source est mappé au message de destination à l'aide du mappage que vous avez désigné.  
  
 Pour plus d’informations sur la **transformer** mettre en forme, consultez [comment configurer la forme transformer](../core/how-to-configure-the-transform-shape.md). Pour plus d’informations sur la création d’un mappage, consultez [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*> \Orchestrations\HelloWorld\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|HelloOrchestration.odx|Orchestration qui coordonne la conversion du bon de commande en facture.|  
|HelloWorld.btproj, HelloWorld.sln|Fichiers projet et solution de l'exemple.|  
|HelloWorldBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|InvoiceSchema.xsd, POSchema.xsd|Schémas des messages de facture et de bon de commande, respectivement.|  
|POToInvoice.btm|Mappage pour la conversion du bon de commande en facture.|  
|SamplePOInput.xml|Exemple de fichier d'entrée.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-helloworld-sample"></a>Pour créer et initialiser l'exemple HelloWorld  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Orchestrations\HelloWorld  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   création des dossiers d'entrée (In) et de sortie (Out) de l'exemple dans le dossier suivant :  
  
         \<*Exemples de chemin d’accès*> \Orchestrations\HelloWorld  
  
    -   compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;  
  
    -   Création et liaison à l'orchestration de l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi. Inscrit et démarre l’orchestration.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple. Pour ce faire, consultez les journaux des événements.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-helloworld-sample"></a>Pour exécuter l'exemple HelloWorld  
  
1.  Collez une copie du fichier SamplePOInput.xml dans le **dans** dossier.  
  
2.  Observez le fichier .xml créé dans le **hors** dossier. Ce fichier contient la facture XML construite à partir du fichier d’entrée SamplePOInput.xml. Le format du nom de ce fichier est \< *MessageID*> .xml, où  *\<MessageID >* est le GUID généré pour identifier de façon unique le message.  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-helloworld-sample"></a>Pour désinstaller l'exemple HelloWorld  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Orchestrations\HelloWorld\  
  
2.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)