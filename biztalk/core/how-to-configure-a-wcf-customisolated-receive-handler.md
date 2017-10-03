---
title: "Pour configurer les Gestionnaire de réception WCF-CustomIsolated | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e90add2-1a5e-4509-a98c-b3c297b4213f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00e52daaaefc3f85537dc3c51f8700da30b74876
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-customisolated-receive-handler"></a>Configuration d'un gestionnaire de réception WCF-CustomIsolated
Vous devez configurer les propriétés du gestionnaire de réception pour que l'adaptateur WCF-CustomIsolated recherche m'extension de comportement personnalisée ailleurs que dans le fichier machine.config.  
  
## <a name="why-should-wcf-customisolated-adapter-look-up-custom-behavior-extensions-from-locations-other-than-machineconfig"></a>Pourquoi l'adaptateur WCF-CustomIsolated doit-il rechercher les extensions de comportement personnalisées aux emplacements autres que le fichier machine.config ?  
 Extensions de comportement utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont enregistrés dans le fichier machine.config. Avant de charger les extensions de comportement, l’adaptateur WCF-CustomIsolated recherche les extensions de comportement dans machine.config. Toutefois, celui-ci sert essentiellement à stocker les informations de configuration requises pour toutes les applications en cours d’exécution sur un ordinateur particulier. De même, les extensions de comportement personnalisées WCF peuvent être requises par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uniquement, et non par toutes les applications exécutées sur l'ordinateur. Ainsi, si le fichier machine.config stocke de fait les extensions de comportement personnalisées, il ne constitue pas un emplacement optimal.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les propriétés du gestionnaire d'adaptateur sont un emplacement supplémentaire à partir duquel l'adaptateur WCF-CustomIsolated peut rechercher les extensions de comportement personnalisées. Notez que cela ne remplace pas les extensions de comportement par ailleurs disponibles dans le fichier machine.config.  
  
### <a name="additional-considerations"></a>Considérations supplémentaires  
 Gardez les points suivants à l'esprit lors de la configuration des propriétés du gestionnaire de réception WCF-CustomIsolated :  
  
-   Les extensions de comportement personnalisées doivent être disponibles dans le fichier machine.config ou les propriétés du gestionnaire d'adaptateur. Elles ne doivent pas figurer aux deux emplacements.  
  
-   Si une extension de comportement personnalisée est déjà disponible dans le fichier machine.config et que vous tentez de définir la même extension de comportement dans les propriétés du gestionnaire d'adaptateur, une erreur est générée.  
  
-   Si une extension de comportement personnalisée est déjà définie dans les propriétés du gestionnaire d'adaptateur et que vous mettez à jour le fichier machine.config avec la même extension de comportement, une erreur d'exécution est générée et consignée dans le journal des événements. L'emplacement de réception est également désactivé.  
  
-   Les assemblys référencés dans l'extension de comportement personnalisée doivent figurer dans le GAC (Global Assembly Cache) avant la définition des propriétés du gestionnaire d'adaptateur.  
  
## <a name="configuring-the-adapter-handler-properties"></a>Configuration des propriétés du gestionnaire d'adaptateur  
 La procédure suivante permet de configurer un gestionnaire de réception WCF-CustomIsolated.  
  
#### <a name="to-configure-the-adapter-handler-properties"></a>Pour configurer les propriétés du gestionnaire d'adaptateur  
  
1.  Dans la Console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **WCF-CustomIsolated**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet le **nom d’hôte** , sélectionnez l’hôte auquel le Gestionnaire de réception sera associé, puis Cliquez sur **propriétés**.  
  
4.  Dans le **propriétés du Transport WCF-CustomIsolated** boîte de dialogue le **Extensions WCF** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Importer**|Importer un fichier de configuration WCF avec des extensions de comportement personnalisées WCF. Cliquez sur ce bouton pour ouvrir la **importer la configuration WCF** boîte de dialogue Parcourir et localiser un fichier de configuration WCF. Notez que le fichier doit être un fichier de configuration WCF valide. Pour plus d’informations sur le schéma de configuration WCF, consultez « Windows Communication Foundation Configuration Schema » à [http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953).|  
    |**Exporter**|Exporter l'extension de comportement personnalisée WCF vers un fichier de configuration WCF. Cliquez sur ce bouton pour ouvrir la **exporter la configuration WCF** boîte de dialogue Parcourir et d’enregistrer le fichier de configuration WCF.|  
    |**Désactiver**|Effacer l'extension de comportement personnalisée WCF existante dans les propriétés du gestionnaire d'adaptateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-CustomIsolated](../core/configuring-the-wcf-customisolated-adapter.md)