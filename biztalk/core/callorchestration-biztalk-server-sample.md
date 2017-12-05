---
title: CallOrchestration (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, calling
- examples, orchestrations
ms.assetid: 0c4194f0-c1e2-419a-8a1a-a3c96e8d2667
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf37bd2b4ceacfe38736cadd8343b4259db126e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="callorchestration-biztalk-server-sample"></a>CallOrchestration (exemple BizTalk Server)
L'exemple CallOrchestration illustre l'appel d'une orchestration BizTalk à partir d'une autre orchestration.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre l'appel d'une orchestration par une autre orchestration en procédant comme suit :  
  
1.  L'orchestration principale reçoit un message de bon de commande.  
  
2.  L'orchestration principale appelle l'orchestration secondaire pour déterminer le prix d'expédition correspondant au bon de commande.  
  
3.  L'orchestration secondaire calcule le prix d'expédition demandé et le renvoie à l'orchestration principale.  
  
4.  L'orchestration principale met à jour le message de bon de commande avec le prix d'expédition reçu.  
  
5.  L'orchestration principale place le message de bon de commande mis à jour dans un dossier à des fins d'inspection.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 La fonction principale de cet exemple est de présenter l'appel d'une orchestration à partir d'une autre orchestration. La possibilité d'appeler des orchestrations permet de diviser les processus d'entreprise en composants réutilisables. Vous pouvez factoriser vos processus les plus répandus en orchestrations distinctes pour que d'autres utilisateurs puissent les réutiliser.  
  
 Dans cet exemple, le **appeler Orchestration** forme dans receivePO.odx appelle findShippingPrice.odx et attend que l’orchestration imbriquée findShippingPrice.odx, pour calculer et retourner le prix d’expédition avant d’envoyer l’achat commande. L'orchestration findShippingPrice.odx utilise la logique suivante pour calculer le prix d'expédition :  
  
```  
If ( weight * shippingRate ) < minShippingPrice Then  
    shippingPrice = minShippingPrice  
Else  
    shippingPrice = weight * shippingRate  
End If  
```  
  
 Le fichier d'exemple de bon de commande entrant InputPO.xml spécifie un poids de 20, ce qui signifie que le message de bon de commande de sortie est passé de 10 à 20.  
  
> [!NOTE]
>  Vous ne pouvez pas appeler une transaction à long terme à partir d'une orchestration atomique.  
  
> [!NOTE]
>  La différence entre l’utilisation de la **appeler Orchestration** forme et **démarrer Orchestration** forme est que lors de l’appel d’une orchestration, l’appelant attend que l’orchestration imbriquée avant continuer. Lors du démarrage d'une orchestration à partir d'une autre orchestration, après que l'appelant démarre l'action, il passe à l'étape suivante du flux de processus. L'orchestration invoquée par l'appelant est exécutée indépendamment jusqu'à ce que le flux de processus soit terminé. Pour plus d’informations, consultez [comment configurer la forme d’Orchestration appeler](../core/how-to-configure-the-call-orchestration-shape.md). Consultez également [comment configurer la forme de démarrer l’Orchestration](../core/how-to-configure-the-start-orchestration-shape.md).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Orchestrations\CallOrchestration\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|CallOrchestration.btproj, CallOrchestration.sln|Fichiers projet et solution de l'exemple.|  
|CallOrchestrationBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|findShippingPrice.odx|Orchestration BizTalk qui sert d'orchestration secondaire, appelée à partir de l'orchestration principale, receivePO.odx.|  
|InputPO.xml|Exemple de fichier de bon de commande conforme au schéma défini dans le fichier PO.xsd.|  
|PO.xsd|Schéma définissant la structure des messages de bon de commande entrants comme l'exemple de fichier entrant InputPO.xml, ainsi que la promotion des propriétés pour les trois éléments du schéma.|  
|PropertySchema.xsd|Fichier de schéma de propriété qui prend part à la promotion des propriétés pour les trois éléments du schéma PO.xsd.|  
|receivePO.odx|Orchestration BizTalk qui sert d'orchestration principale dans l'exemple. Elle récupère les messages de bon de commande dans le dossier de réception, puis appelle l'autre orchestration, findShippingPrice.odx, pour le calcul et la mise à jour du prix d'expédition.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-callorchestration-sample"></a>Pour créer et initialiser l'exemple CallOrchestration  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Orchestrations\CallOrchestration\  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier CallOrchestration.  
  
    -   Compilation et déploiement du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], contenant les deux orchestrations, pour cet exemple.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-callorchestration-sample"></a>Pour exécuter l'exemple CallOrchestration  
  
1.  Placez une copie du fichier InputPO.xml dans le dossier In.  
  
2.  Observez le fichier de bon de commande XML mis à jour créé dans le dossier Out. Il contient le message de bon de commande d'origine, modifié de manière à inclure le prix d'expédition calculé, comme expliqué plus haut. Le format du nom de ce fichier est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le message .  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-callorchestration-sample"></a>Pour désinstaller l'exemple CallOrchestration  
  
1.  Dans une fenêtre de commande [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Orchestrations\CallOrchestration\  
  
2.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)