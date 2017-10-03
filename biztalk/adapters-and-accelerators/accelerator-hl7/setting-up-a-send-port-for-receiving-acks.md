---
title: "Configuration d’un Port d’envoi pour recevoir des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: bb683e72-36e2-4a8f-acc2-8b37ed23746f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81b33982273088e498e719fc074db5c454b0e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-a-send-port-for-receiving-acks"></a>Configuration d’un Port d’envoi pour recevoir des accusés de réception
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) peut recevoir des accusés de réception (ACK) sur un port d’envoi unidirectionnel. Lorsque vous configurez un port d’envoi unidirectionnel pour recevoir les accusés de réception sur la même connexion, vous devez associer cet envoi port de réception du port unidirectionnel.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]le programme d’installation crée un unidirectionnel port de réception (appelé **TwoWayAckReceivePort**) et l’emplacement de réception (appelé **TwoWayAckReceiveLocation**). L’emplacement de réception utilise le type de transport de protocole de couche inférieure minimale (MLLP), a un URI de « 127.0.0.1:65535 » et utilise le **BTAHL72XReceivePipeline**. Voici les paramètres requis pour la réception et le traitement d’un accusé de réception reçu un message envoyé par le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] , l’adaptateur d’envoi en mode bidirectionnel. Cet emplacement de réception ne doit pas être supprimé ou utilisée à d’autres fins. Ne jamais envoyer de données à cet emplacement de réception. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]permet à cet emplacement par de réception par défaut.  
  
 **TwoWayAckReceiveLocation**, qui le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Assistant installation crée, utilise le **BizTalkServerApplication** en tant que le Gestionnaire de réception. Toutefois, si vous choisissez de créer un nouvel hôte et l’utiliser en tant que le Gestionnaire de réception pour MLLP, puis vous devez procédez comme suit pour créer un nouveau **TwoWayAckReceiveLocation**:  
  
1.  Créer un unidirectionnel port de réception.  
  
2.  Créer un unidirectionnel MLLP l’emplacement de réception.  
  
3.  Spécifiez les valeurs appropriées pour les propriétés de transport MLLP.  
  
4.  Spécifiez le que gestionnaire de réception approprié.  
  
5.  Activez l'emplacement de réception  
  
### <a name="to-create-a-send-port-enabled-to-receive-an-ack-on-the-same-socket"></a>Pour créer un port d’envoi activé pour recevoir un accusé de réception sur le même socket  
  
1.  Ouvrez la Console Administration de BizTalk, puis **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **BizTalk Application 1**. Avec le bouton droit **Ports d’envoi**, pointez sur Nouveau, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **nom** , tapez le nom du port d’envoi.  
  
3.  Dans le **Transport** section, pour **Type**, sélectionnez **MLLP**.  
  
4.  Cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du Transport MLLP, tapez un nom de connexion et un hôte (par exemple, **localhost**).  
  
6.  Pour **activée de réponse de sollicitation**, sélectionnez **Oui**. Laissez **envoyer recevoir emplacement (URI) de l’accusé de réception** vide, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Lorsque vous laissez **soumettre un emplacement de réception** vide, BTAHL7 entre l’URI pour la valeur par défaut **TwoWayAckReceiveLocation**. Vous pouvez vérifier qu’après un clic sur **OK** à l’étape 6, en cliquant sur **Configuration** à nouveau. L’URI de **TwoWayAckReceiveLocation** (127.0.0.1:65535) devra être entré dans **envoyer recevoir emplacement (URI) de l’accusé de réception**.  
  
    > [!NOTE]
    >  Vous devez créer un port d’envoi pour vous abonner à l’accusé de réception reçu, ou l’accusé de réception s’affichent dans un état suspendu, car aucun abonnement ont été trouvées. Pour vous abonner à l’accusé de réception reçu par le port d’envoi, utilisez des filtres, par exemple,  **BTS. MessageType == \<* MessageType*> ** et  **BTS. ReceivePortName == \<* ReceivePort*> **. Pour les accusés de réception statiques, le type de message est **StaticAck**.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Types de schémas de Message de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Conditions d’erreur d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)