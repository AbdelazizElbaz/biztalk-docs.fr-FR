---
title: "Étape 1 : Configurer un fichier de l’emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df591263-964a-4ad8-bc3a-a553de8dae4f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78f8bccc187bf310b8426fc3d5fee36add44a9f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-a-file-receive-location"></a>Étape 1 : Configurer un fichier de l’emplacement de réception
Dans cette rubrique, vous allez configurer un emplacement de réception FILE qui consomme le message de requête factice que vous déposez dans un dossier pour appeler le port d’envoi.  
  
> [!NOTE]
>  Ce didacticiel suppose que vous utilisez l’application par défaut (**BizTalk Application 1**) pour créer la solution. Vous pouvez également créer une autre application et effectuer les mêmes étapes pour celle-ci.  
  
### <a name="to-configure-a-file-receive-location"></a>Pour configurer un emplacement de réception FILE  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel Port de réception**.  
  
2.  Sous l’onglet Général, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ReceivePortRestAzureMarketPlace**.|  
    |**Activer le routage des messages ayant échoué**|(désactivé)|  
  
3.  Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.  
  
4.  Dans la boîte de dialogue ReceiveLocation1 - Propriétés d'emplacement de réception, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ReceiveLocationAzureMarketPlace**.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Gestionnaire de réception**|Sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline de réception**|Sélectionnez **PassThruReceive**.|  
  
5.  Cliquez sur **configurer**.  
  
6.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Tapez un emplacement dans lequel vous déposerez le message de requête factice.|  
    |**Nom de fichier**|Conserver`*.xml`|  
  
7.  Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)