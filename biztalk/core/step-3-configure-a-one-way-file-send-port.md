---
title: "Étape 3 : Configurer un Port d’envoi FILE unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c52c6b6b-6f9c-48f2-8732-450fe3a15eae
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceb055f0d4d41eb82eb79cb549b082212fd1bbd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-a-one-way-file-send-port"></a>Étape 3 : Configurer un Port d’envoi FILE unidirectionnel
Dans cette étape, vous configurez un port d’envoi FILE unidirectionnel qui consomme le message de réponse reçu de l’interface REST et le copie dans un emplacement de fichier.  
  
### <a name="to-configure-a-file-send-port"></a>Pour configurer un port d’envoi FILE  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel**.  
  
2.  Sous l’onglet Général, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **SendPortOutAzureMarketPlaceData**.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Gestionnaire d’envoi**|Sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline d’envoi**|Sélectionnez **PassThruTransmit**.|  
  
     Cliquez sur **configurer**.  
  
3.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Tapez un emplacement dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copie le message de réponse.|  
    |**Nom de fichier**|Conserver`%MessageID%.xml`|  
  
4.  Sur le **filtres** onglet, spécifiez le filtre pour utiliser tous les messages sont écrits dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de la boîte de Message par le port de réception que vous avez créé dans [étape 2 : configurer un Port d’envoi de WCF-WebHttp bidirectionnel](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).  
  
    |||  
    |-|-|  
    |**Propriété**|La valeur **BTS. SPName**|  
    |**Opérateur**|La valeur**==**|  
    |**Valeur**|La valeur`SendPortRESTAzureMarketPlace`|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)