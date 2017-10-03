---
title: "Implémentation d’un mécanisme de déclenchement externe du lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5633a448-cc29-4931-a3ad-206ae25c989b
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e88b6962cc0c83ab0ac4971f481b9ac1f185ca02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-an-external-batch-release-mechanism"></a>Implémentation d'un mécanisme externe de déclenchement d'un lot
Vous pouvez activer le déclenchement d'un lot à l'aide d'un déclencheur externe. Le déclenchement peut être activé automatiquement par une application sectorielle principale lorsqu'un seuil spécifique est atteint. Ce mécanisme s’ajoute automatiquement le déclenchement du lot par une planification ou un nombre de documents informatisés ou de caractères de déclenchement ou déclencher manuellement le lot en cliquant sur le **remplacer** situé dans le **lot Configuration** page de l’onglet d’accord unidirectionnel.  
  
 Pour implémenter un déclencheur externe, vous devez configurer un port et un emplacement de réception pour le traitement de OverrideControlMessage. L'emplacement de réception utilise le pipeline de réception `Edi.BatchControlMessageRecvPipeline`. Ce pipeline est également utilisé par l'emplacement de réception BatchControlMessageRecvLoc, que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour traiter les messages de remplacement manuel. Toutefois, BatchControlMessageRecvLoc est un emplacement de réception SQL tandis que l'emplacement de réception que vous configurez pour un déclencheur externe peut utiliser un autre type d'adaptateur.  
  
 Un déclenchement externe est exécuté par un message de contrôle XML. Pour déclencher le lot, l'application principale achemine le message de contrôle vers l'emplacement de réception. Vous pouvez modifier le message de contrôle pour activer, remplacer ou arrêter le lot. Consultez la procédure suivante de création du message de contrôle.  
  
 Pour activer le déclencheur externe, vous devez sélectionner le **déclencheur externe** propriété dans le **Configuration de lot** page de la **propriétés de l’accord** boîte de dialogue zone pour X12 ou EDIFACT. Cette propriété indique qu'un message de déclenchement externe est nécessaire pour le déclenchement du lot. Le **remplacer** bouton, **arrêter** bouton, et **Activation** des contrôles de plage restent valides si la **déclencheur externe** a de propriété été sélectionné.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-a-receive-location-for-the-external-batch-release-trigger-message"></a>Pour créer un emplacement de réception pour le message de déclenchement externe du lot  
  
1.  Dans la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port de réception unidirectionnel. Pour obtenir des instructions sur la création d’un port de réception, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
2.  Créez un emplacement de réception unidirectionnel dans le port de réception.  
  
3.  Sélectionnez le type de transport. Vous pouvez sélectionner un type quelconque pour cet emplacement de réception. Une solution courante consiste à sélectionner le type FILE et à entrer un dossier pour la réception du fichier.  
  
4.  Pour le pipeline de réception, sélectionnez `BatchControlMessageRecvPipeline`.  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-create-the-external-batch-release-trigger-message"></a>Pour créer le message de déclenchement externe du lot  
  
1.  Dans le Bloc-notes, créez un fichier et nommez celui-ci avec une extension .xml.  
  
2.  Ajoutez le fragment de code suivant au fichier :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ControlMessage xmlns="http://SQLControlMessage.IssueSelect">  
      <PAM_Control xmlns="http://SQLControlMessage.IssueSelect">  
        <DestinationParty>[Party ID]</DestinationParty>  
        <EdiMessageType>[0 for X12\HIPAA|1 for Edifact]</EdiMessageType>  
        <ActionType>EdiBatchOverride</ActionType>  
        <ActionDateTime>[yyyy-mm-ddThh:mm:ss.sss]</ActionDateTime>  
        <UsedOnce>0</UsedOnce>  
        <BatchId>[Batch ID]</BatchId>  
        <BatchName>[Batch Name]</BatchName>  
        <DestinationPartyName>[Destination Party/Partner name]</DestinationPartyName>  
        <SenderPartyName>[Sender Party/Partner name]</SenderPartyName>  
        <AgreementName>[Agreement Name]</AgreementName>  
        <ReceiverPartyNameType>[Receiver Party/Partner name]</ReceiverPartyNameType>  
        <ToBeBatched>1</ToBeBatched>  
      </PAM_Control>  
    </ControlMessage>  
    ```  
  
     Remplacez les valeurs du fragment ci-dessus comme suit :  
  
    -   Spécifiez le type d'action. En règle générale, les **ActionType** doit avoir la valeur **EdiBatchOverride** pour remplacer les paramètres de lot définis dans l’accord. Vous pouvez également définir cette option **EdiBatchTerminate** pour arrêter le lot via un déclencheur externe.  
  
        > [!NOTE]
        >  Il est déconseillé d'utiliser un déclencheur externe pour activer un lot. Par conséquent, vous ne devez pas spécifier **ActionType** en tant que **ActionType**.  
  
    -   Déterminez l'ID et le nom du lot. Pour ce faire, ouvrez le **propriétés de l’accord** boîte de dialogue, puis sur l’onglet d’accord unidirectionnel, cliquez sur **Configuration de lot**. Cliquez sur l’onglet du lot devant être remplacée et entrez la valeur de **nom** et **ID de lot** champs dans le **BatchName** et **BatchID**nœuds du message de contrôle.  
  
    -   Spécifiez le nom du tiers de destination. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Parties** nœud et à partir de la **tiers et profils d’entreprise** page, obtenir le nom du tiers/partenaire qui recevra le par lot échanges. Entrez le nom dans la **ReceiverPartyNameType** nœud du message de contrôle.  
  
    -   Spécifiez le nom du tiers expéditeur. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Parties** nœud et à partir de la **tiers et profils d’entreprise** page, obtenir le nom du tiers/partenaire qui enverra les échanges traités par lot . Entrez le nom dans la **SenderPartyName** nœud du message de contrôle.  
  
    -   Spécifiez le nom de l'accord. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Parties** nœud et à partir de la **tiers et profils d’entreprise** page, dans le **accords** section, avec le bouton droit de l’accord contenant la configuration de lot devant être remplacée à l’aide du message de contrôle, puis cliquez sur **propriétés**. Dans le **propriétés de l’accord** boîte de dialogue le **général** sous l’onglet dans le **propriétés générales** page, copiez la valeur à partir de la **nom** champ dans le **paramètres de l’accord** section, puis collez-le dans le **AgreementName** nœud du message de contrôle.  
  
    > [!NOTE]
    >  Il n'est pas nécessaire de spécifier un ID de tiers de destination. Cet élément est requis dans le message de contrôle uniquement à des fins de compatibilité descendante.  
  
3.  Enregistrez le fichier.  
  
### <a name="to-enable-the-external-release-trigger"></a>Pour activer le déclencheur externe  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Parties** nœud et à partir de la **tiers et profils d’entreprise** page, dans le **accords** section, avec le bouton droit de l’accord contenant la configuration de lot devant être remplacée à l’aide du message de contrôle, puis cliquez sur **propriétés**. Dans le **propriétés de l’accord** boîte de dialogue, sous l’onglet d’accord unidirectionnel, cliquez sur **Configuration de lot**.  
  
2.  Dans le **Configuration de lot** , cliquez sur l’onglet du lot pour lequel vous voulez avoir un déclencheur externe, puis, sous la **Release** section, sélectionnez **déclencheur externe** .  
  
3.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des lots EDI](../core/configuring-edi-batches.md)   
 [Comment créer un emplacement de réception](../core/how-to-create-a-receive-location.md)