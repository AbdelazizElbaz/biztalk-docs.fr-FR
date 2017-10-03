---
title: "Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, receive ports
- receive ports, MQSeries adapters
- MQSeries adapters, send ports
- configuring [MQSeries adapters], send ports
- configuring [MQSeries adapters], receive ports
- send ports, MQSeries adapters
- configuring [MQSeries adapters], receive locations
- MQSeries adapters, receive locations
- receive locations, MQSeries adapters
ms.assetid: 552aacde-9ec0-4459-b369-073676b6f926
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c31a15615d74a2ca1471559aa25772725821889
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-mqseries-adapter-receive-locations-and-send-ports"></a>Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi
Vous pouvez configurer l'adaptateur MQSeries pour les emplacements de réception et les ports d'envoi.  
  
## <a name="to-configure-receive-locations-and-send-ports"></a>Pour configurer les emplacements de réception et les ports d'envoi  
 **Pour créer le port de réception et l’emplacement de réception :**  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application dans laquelle vous souhaitez créer un emplacement de réception.  
  
2.  Avec le bouton droit le **Ports de réception** nœud, cliquez sur **nouveau,** et pointez sur **Port de réception unidirectionnel**.  
  
3.  Entrez les valeurs appropriées dans le **propriétés de Port** boîte de dialogue. Pour plus d’informations sur la **propriétés de Port** boîte de dialogue, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
4.  Dans la console Administration de BizTalk Server, cliquez sur le **Port de réception** nœud que vous avez créé et puis cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis cliquez sur **nouveau** dans le volet droit.  
  
6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section ensuite **Type**, sélectionnez **MQSeries** dans la liste déroulante. liste, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport MQSeries** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Taille de lot**|Définir la taille maximale d'un lot de messages, en Ko. **Remarque :** si le **prise en charge des transactions** pour l’emplacement de réception est définie sur **Oui**; chaque lot de messages est envoyé à la base de données MessageBox dans le contexte d’un Microsoft Transaction de Distributed Transaction Coordinator (MSDTC). La transaction MSDTC qui est créée pour un lot de messages reste ouverte jusqu'à ce que chaque message du lot conservé dans la base de données MessageBox soit placé dans la file d'attente d'abonné appropriée. Par conséquent, la durée de cette transaction MSDTC augmente proportionnellement les **taille maximale du lot** paramètre est augmenté. Dans la mesure où un grand nombre de transactions MSDTC ouvertes simultanément risquant d’affecter les performances globales, les **taille maximale du lot** paramètre ne doit pas être défini à une valeur très élevée lors de la prise en charge de la transaction est activée.|  
    |**Traitement ordonné**|Définir MQSeries afin de conserver l'ordre des messages au fur et à mesure de leur réception depuis la file d'attente MQSeries. **Remarque :** pour conserver le message de commande pour une file d’attente spécifique, une seule instance d’hôte BizTalk peut recevoir les messages à partir de cette file d’attente MQSeries. <br /><br /> **Valeur par défaut :** False|  
    |**File d’attente**|Champ renseigné avec les informations à partir de la **définition file d’attente** boîte de dialogue. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Transactionnelle**|L'adaptateur commence une transaction DTC (Microsoft Distributed Transaction Coordinator) entre BizTalk Server et le serveur MQSeries. Lorsque la valeur **non**, il n’existe aucune garantie de remise des messages.<br /><br /> **Valeur par défaut :** False|  
  
8.  Dans le **propriétés du Transport MQSeries** boîte de dialogue, cliquez sur **OK** pour remplir le **adresse (URI)** zone le **propriétés d’emplacement de réception**boîte de dialogue.  
  
9. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
 **Pour créer le port d’envoi :**  
  
1.  Dans la console Administration de BizTalk Server, créez un port d'envoi statique. Consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md) pour plus d’informations. Configurez toutes les options de port d’envoi et spécifiez **MQSeries** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport MQSeries** boîte de dialogue zone, procédez comme suit :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Taille de fragmentation**|Définit la taille des fragments, en Ko, des messages envoyés entre l'adaptateur et MQSAgent|  
    |**Application associée SSO**|Définir l'application associée à authentification unique. L’ID utilisateur et un mot de passe de l’authentification unique sont utilisés pour le **MQMD_UserIdentifier**et le **MQIIH_Authenticator** (ou **MQCIH_Authenticator**) propriété respectivement.<br /><br /> **Valeur par défaut :** vide|  
    |**Conversion de données**|Convertit le message en page de code ANSI du serveur MQSeries pour Windows Server.<br /><br /> Sélectionnez **Oui** pour effectuer cette conversion Unicode en ANSI.<br /><br /> **Valeur par défaut :** N°|  
    |**Commandée**|Définir MQSeries afin de conserver l'ordre des messages lors de leur envoi vers la file d'attente MQSeries.<br /><br /> Sélectionnez **Oui** pour conserver l’ordre des messages. **Remarque :** vous devez définir le **accusé de réception** propriété dans votre orchestration pour **transmis** pour le port d’envoi. <br /><br /> **Valeur par défaut :** N°|  
    |**Définition de la file d’attente**|Rempli avec les informations à partir de la **définition file d’attente** boîte de dialogue ou directement dans le champ. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Segmentation autorisée**|Utiliser la segmentation du gestionnaire de file d'attente MQSeries si un message individuel dépasse la longueur maximale autorisée pour les messages de file d'attente MQSeries. Si vous sélectionnez **Oui**, MQSeries place les messages segmentés dans la file d’attente.<br /><br /> **Valeur par défaut :** N°|  
    |**Prise en charge des transactions**|L’adaptateur commence une transaction DTC entre BizTalk Server et MQSeries Server. Lorsque la valeur **non**, il n’existe aucune garantie de remise des messages.<br /><br /> **Valeur par défaut :** Oui **Remarque :** ne configurez pas de ports d’envoi avec différents **prise en charge des transactions** paramètres pour envoyer des messages à la même file d’attente MQSeries. **Remarque :** à l’exception des scénarios de test, cette propriété doit toujours être définie à la valeur par défaut de **Oui**. Définition de cette propriété sur la valeur **non** dans une production environnement peut provoquer des problèmes inattendus.|  
  
     L'illustration suivante montre comment configurer ces propriétés.  
  
     ![Boîte de dialogue Propriétés du Transport MQSeries](../core/media/bts-dev-mqsendtransportprops.gif "BTS_Dev_MQSendTransportProps")  
  
4.  Cliquez sur le bouton de sélection (**...** ) situé à droite de la **définition file d’attente** à cocher pour définir la file d’attente. Vous pouvez utiliser la **exporter** boîte de dialogue, tout comme vous avez pouvez passer avec l’emplacement de réception, pour créer la file d’attente immédiatement ou exporter un script définissant la file d’attente.  
  
5.  Cliquez sur **OK** dans chaque boîte de dialogue pour la fermer et enregistrer les paramètres.  
  
 **Pour inscrire le port d’envoi, de démarrer le port d’envoi et activer l’emplacement de réception :**  
  
1.  Cliquez sur le port d’envoi, sur **Enlist** pour inscrire le port d’envoi.  
  
2.  Cliquez sur le port d’envoi, sur **Démarrer** pour démarrer le port d’envoi.  
  
3.  Cliquez sur l’emplacement de réception, sur **activer** pour activer l’emplacement de réception.  
  
4.  Consultez le journal des événements pour vous assurer de l'absence d'erreurs BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer l’adaptateur MQSeries envoyer et recevoir des gestionnaires](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md)   
 [Configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md)