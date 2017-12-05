---
title: "Créer une orchestration BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c637ae-f94f-40f8-8ce7-73a7b7df9f8f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6223ab8d8aa3c8d1c20559a88257dd0dccaa22e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="create-a-biztalk-server-orchestration"></a>Créer une orchestration BizTalk Server
> [!NOTE]
>  Ce didacticiel s’applique uniquement à BizTalk Server.  
  
 Créez une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui, une fois déployée, reçoit un message de bon de commande JSON, le transforme en facture XML, puis envoie une facture JSON.  
  
## <a name="define-message-and-message-types"></a>Définir les messages et les types de messages  
 Cette solution fonctionne avec deux messages de base - les bons de commande et les factures. Nous avons déjà généré le schéma du bon de commande d'un message JSON en utilisant l' Assistant Schéma de JSON. L'exemple fourni pour ce didacticiel dispose déjà du schéma pour le message de la facture. Nous utilisons ces schémas pour créer les types de messages dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
1.  Ajoutez une orchestration au projet BizTalk et ouvrez la vue Orchestration.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`PurchaseOrder`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BTSJSON. Bon de commande*, où *BTSJSON* est le nom de votre projet BizTalk.|  
  
5.  Répétez l'étape précédente pour créer un nouveau type de message pour le message de la facture. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`InvoiceMsg`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BTSJSON. Facture*.|  
  
## <a name="set-up-the-orchestration"></a>Configurer l'orchestration  
 Dans cette étape, vous ajoutez des ports et des formes de message pour créer une orchestration.  
  
### <a name="add-message-shapes"></a>Ajouter des formes de messages  
 Ouvrez le fichier d'orchestration dans l'Explorateur de solutions, puis ajoutez les formes de messages suivantes.  
  
-   Ajouter une forme réception, définissez son nom sur **ReceivePO**et le type de message **PurchaseOrder**.  
  
-   Ajoutez une forme envoi, définissez son nom sur **SendInvoice**et le type de message **InvoiceMsg**.  
  
-   Ajoutez une forme construire un Message et définissez la **Messages construits** propriété de la forme construire un Message à **InvoiceMsg**.  
  
-   Ajoutez une forme Transformer dans la forme Construire un message. Double-cliquez sur la forme Transformer et dans le **transformer la Configuration** boîte de dialogue, sélectionnez le **mappage existant** option et sélectionnez **BTSJSON. POToInvoice** carte. Ce mappage est fourni dans le cadre de l'exemple. Dans la boîte de dialogue, définissez **Source** à **PurchaseOrder** et **Destination** à **InvoiceMsg**. Cliquez sur **OK**.  
  
### <a name="add-ports"></a>ajouter des ports  
 Ajoutez deux ports à l'orchestration – un pour la réception des messages et un pour l'envoi des messages. Utilisez les propriétés suivantes pour les ports :  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *ReceiveJSONPO*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|ResponseOut|-Définissez **identificateur** à *SendJSONInvoice*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
 Connectez les ports et la forme de message, comme indiqué dans la capture d'écran ci-dessous, puis enregistrez les modifications apportées au projet.  
  
 ![Orchestration pour traiter les messages JSON](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)