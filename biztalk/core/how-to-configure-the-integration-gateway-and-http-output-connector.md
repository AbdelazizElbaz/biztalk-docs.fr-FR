---
title: "Comment configurer la passerelle d’intégration et d’un connecteur de sortie HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Integration Gateway
- gateway nodes, creating
- HTTP Output Connector
ms.assetid: a02ee533-07a8-42fa-a72a-7e5359b18f40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acfa52be85a664432af95af0ca292e9cc394c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-integration-gateway-and-http-output-connector"></a>Configuration de la passerelle d'intégration et du connecteur de sortie HTTP
Suivez ces instructions pour configurer la passerelle d'intégration et le connecteur de sortie HTTP.  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a>Pour créer et configurer un nouveau nœud de passerelle  
  
1.  Ouvrez l'application PeopleSoft dans un navigateur Web.  
  
2.  Recherchez **PeopleTools**, sélectionnez **Integration Broker**, puis sélectionnez **passerelles**.  
  
3.  Dans le **recherche par** , tapez `LOCAL`, puis cliquez sur **recherche**.  
  
     ![](../core/media/psadapter-31-task-gatewaysearch.gif "PSAdapter_31_Task_GatewaySearch")  
  
4.  Entrez `machine-name/PSIGW/PeopleSoftListeningConnector` dans les **URL de la passerelle** entrée.  
  
     ![](../core/media/psadapter-32-task-gatewayurl.gif "PSAdapter_32_Task_GatewayURL")  
  
5.  Cliquez sur **Actualiser**, puis cliquez sur **enregistrer**.  
  
6.  Cliquez sur le **propriétés** de liens pour **HTTPTARGET** pour afficher la combinaison propriétés/valeur de cet ID.  
  
     Vous pouvez indiquer l'URL à cet endroit ou dans le Nœud de définition. Pour les besoins de cette présentation, définissez l'URL au niveau du Nœud.  
  
     ![](../core/media/psadapter-33-task-gatewaynodelevel.gif "PSAdapter_33_Task_GatewayNodeLevel")  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)