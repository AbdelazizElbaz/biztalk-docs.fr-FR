---
title: "Comment créer un nouveau nœud de passerelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: gateway nodes, creating
ms.assetid: e7c5f9a7-a58e-4661-9cb5-2414e31a57a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b371243d58389415349d5a88c05b7bf312e70ef9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-gateway-node"></a>Création d'un nœud de passerelle
Suivez ces instructions pour créer et configurer un nouveau nœud de passerelle dans PeopleSoft Enterprise.  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a>Pour créer et configurer un nouveau nœud de passerelle  
  
1.  Dans PeopleSoft, dans le volet gauche, cliquez sur le **définitions des nœuds** lien.  
  
2.  Cliquez sur le **ajouter une nouvelle valeur** onglet.  
  
3.  Dans le **nom de nœud** , entrez `MSEXTERNAL`, puis cliquez sur **ajouter**.  
  
4.  Cliquez sur le **nœud** onglet et entrez les informations suivantes :  
  
    1.  **Description :** Entrez une description pour le nœud.  
  
    2.  **Type de nœud :** sélectionnez **externe**.  
  
    3.  **Type de routage :** sélectionnez **implicite**.  
  
     ![](../core/media/psadapter-34-task-gatewaynodeconnector.gif "PSAdapter_34_Task_GatewayNodeConnector")  
  
5.  Cliquez sur le **connecteurs** onglet et entrez les informations suivantes :  
  
    1.  **ID de passerelle :** entrez `LOCAL`.  
  
    2.  **ID de connecteur :** entrez `HTTPTARGET`.  
  
     ![](../core/media/psadapter-35-task-gatewayhttptarget.gif "PSAdapter_35_Task_GatewayHTTPTarget")  
  
6.  Cliquez sur le **recherche** icône.  
  
7.  Sous **ID de connecteur**, cliquez sur le **HTTPTARGET** lien.  
  
     ![](../core/media/psadapter-36-task-gatewayconnectorid.gif "PSAdapter_36_Task_GatewayConnectorID")  
  
8.  Sur le **propriétés** , entrez les informations suivantes :  
  
    1.  **En-tête :** entrez `Y`.  
  
    2.  **HTTPPROPERTY :** entrez `POST`.  
  
    3.  **PrimaryURL :** Entrez l’adresse IP et le port de l’ordinateur cible (l’ordinateur de développement).  
  
    > [!NOTE]
    >  Le **Port de réception** a été définie précédemment.  
  
     ![](../core/media/psadapter-37-task-gatewaynodereceiveport.gif "PSAdapter_37_Task_GatewayNodeReceivePort")  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)