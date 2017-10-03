---
title: "Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario (Pull) avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d5bbfed-f2cb-4caa-91e2-58f0bdb3b3c5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486133586a3db8669a58aae59c3ec67a4f561999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-create-an-orchestration-for-dynamic-send-port-for-interact-store-and-forward-pull-scenario"></a>Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant
Avant de commencer les étapes décrites dans cette section, vous devez effectuer les étapes décrites dans le [étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md) section.  
  
### <a name="to-create-an-orchestration"></a>Pour créer une Orchestration  
  
1.  Créez la forme réception qui s’abonne à tous les messages du type de message Sw-ExchangeSnFRequest.  
  
2.  Ajoutez une forme Expression pour obtenir toutes les valeurs requises à partir du message ExchangeRequestSnF. Reportez-vous à l’exemple suivant de la forme Expression :  
  
    ```  
    ExchangeSnFRequestDoc=ExchangeSnFRequest;  
    AcquireQueuePath="/Sw-ExchangeSnFRequest/Sw-SnFRequest/Sw-SnFOpRequest/Sw-AcquireSnFRequest/";  
  
    QueueNameNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath + "SwInt-Queue");  
    SessionModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-SessionMode");  
    ForceAcquireNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-ForceAcquire");  
    OrderByNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-OrderBy");  
    RecoveryModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-RecoveryMode");  
  
    QueueName=QueueNameNode.InnerText;  
    SessionMode=SessionModeNode.InnerText;  
    ForceAcquire=ForceAcquireNode.InnerText;  
    OrderBy=OrderByNode.InnerText;  
    RecoveryMode=RecoveryModeNode.InnerText;  
  
    MessageFormat="InteractMessage";  
    IsPull=true;  
    ```  
  
3.  Construire un message de type PullSnFRequest et l’URL pour l’envoi dynamique. Consultez l’exemple d’attribution forme de construire un Message :  
  
    ```  
    PullMessage = new System.Xml.XmlDocument();  
    PullMessage.LoadXml(@"<Sw-PullSnFRequest/>");  
    PullRequest = PullMessage;  
  
    DynamicPull(Microsoft.XLANGs.BaseTypes.Address) = "INTERACT://<machine  
     name>/" + QueueName + "/" + SessionMode + "/" + ForceAcquire + "/" +   
    OrderBy + "/" + RecoveryMode + "/" + MessageFormat;  
    ```  
  
4.  Dans cet exemple, PullMessage est un message de type Sw-PullSnFRequest.  
  
5.  Ajoutez une forme envoi pour envoyer le PullMessage (requête de tirage).  
  
6.  Ajouter un port requête-réponse pour l’envoi du message par extraction de données et pour recevoir une réponse par extraction de données avec la liaison dynamique.  
  
7.  Connectez la forme envoi le port créé à l’étape précédente.  
  
8.  Ajoutez une forme réception pour recevoir le PullResponse (message de type PullSnFResponse), puis connectez-vous la forme réception avec le port créé précédemment.  
  
9. Envoyer la réponse dans le dossier correspondant à l’aide d’une forme envoi.  
  
10. Si vous voulez extraire tous les messages, ajoutez toutes ces activités (envoi d’une requête de tirage et recevoir une réponse) dans une boucle.  
  
11. Ajoutez une forme Expression CheckQueueEmpty à conserver débrancher jusqu'à ce que le délai de la file d’attente est vide. Consultez l’exemple suivant de la forme Expression :  
  
    ```  
    PullResponseDoc=PullResponse;  
    PullResponseNode=PullResponseDoc.SelectSingleNode("/SwPullSnFResponse/  
    SwGbl-Status/SwGbl-StatusAttributes/SwGbl-Code");  
    if(PullResponseNode !=null && PullResponseNode.InnerText=="Sw.SnF.QueueEmpty")  
    {  
        IsPull=false;  
    }  
    ```  
  
12. Ceci permettra de définir la IsPull = false, une fois que la file d’attente est vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md)