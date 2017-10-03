---
title: "Étape 7 : Création et configuration des Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
- private process tutorial, configuring ports
ms.assetid: c00344c6-506a-4560-a948-e5fed2b9fd58
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c93f7c07f92c7517dbc84403747da869e0d4ceb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-creating-and-configuring-ports"></a>Étape 7 : Création et configuration des Ports
Dans cette étape, vous créez et configurez les ports que vous utilisez pour communiquer avec les processus d’entreprise. Chaque port a un type, la direction et la propriété de liaison. Ces propriétés d’établir la direction et le modèle de communication, l’emplacement d’où le message est envoyé ou reçu, et comment la communication se produit.  
  
### <a name="to-create-a-logical-send-port"></a>Pour créer un port d’envoi logique  
  
1.  Dans Visual Studio, à partir de la boîte à outils, faites glisser le **Port** forme sur l’aire de conception d’orchestration et déposez-la sur la **Surface du Port** pour ouvrir le **Assistant Configuration du Port**.  
  
2.  Sur le **Assistant Configuration du Port** , cliquez sur **suivant**.  
  
3.  Sur le **propriétés de Port** page, dans le **nom** , tapez **ContosoSQLReqResponsePort**, puis cliquez sur **suivant**.  
  
4.  Sur le **sélectionner un Type de Port** page, dans le **nom du Type de Port** , tapez **ContosoSQLReqResponsePortName**.  
  
5.  Pour **modèle de Communication**, sélectionnez **demande-réponse**.  
  
6.  Pour **Restrictions d’accès**, sélectionnez **interne - limité au projet**, puis cliquez sur **suivant**.  
  
7.  Sur le **liaison de Port** page, sélectionnez **puis-je envoyer une demande et recevoir une réponse**, laissez le **liaison de Port** option la valeur **spécifier plus tard**, puis cliquez sur **suivant**.  
  
8.  Cliquez sur **Terminer** pour créer le port.  
  
### <a name="to-change-the-variable-type-for-the-orchestration-ports"></a>Pour modifier le type de variable pour les ports d’orchestration  
  
1.  Dans la vue Orchestration, développez **Types**, développez **Types de ports**, développez **ContosoSQLReqResponsePortName**, développez **Operation_1**, puis sélectionnez **demande**.  
  
2.  Dans la fenêtre Propriétés, sélectionnez le **Type de Message** propriétés, développez **schémas** puis cliquez sur  **\<sélectionner dans l’assembly référencé >**.  
  
3.  Dans la boîte de dialogue Sélectionner le Type d’artefact, cliquez sur **ContosoPriceAndAvailability**.  
  
4.  Dans le volet droit, sélectionnez **rootPriceRequest**, puis cliquez sur **OK**.  
  
5.  Dans Vue Orchestration, sous **Operation_1**, sélectionnez **réponse** pour le **ContosoSQLReqResponsePortName** type de port.  
  
6.  Dans la fenêtre Propriétés, sélectionnez le **Type de Message** propriétés, développez **schémas** puis cliquez sur \< **sélectionner dans l’assembly référencé >**.  
  
7.  Dans le **sélectionner le Type d’artefact** boîte de dialogue, cliquez sur **ContosoPriceAndAvailability**.  
  
8.  Dans le volet droit, sélectionnez **rootPriceResponse**, puis cliquez sur **OK**.  
  
### <a name="to-connect-the-ports-to-the-receive-shapes"></a>Pour connecter les ports aux formes réception  
  
1.  Sur l’aire de conception d’orchestration, sélectionnez la **Send_1** forme.  
  
2.  Dans la fenêtre Propriétés, sélectionnez le **Message** propriété, puis sélectionnez **Contoso3A2RequestMessage** dans la liste déroulante.  
  
3.  Se connecter le **ContosoSQLReqResponsePort** en activant la poignée verte en regard du **demande** étiquette et en le faisant glisser sur la poignée verte la **Send_1** forme.  
  
4.  Sur l’aire de conception d’orchestration, sélectionnez la **Receive_1** forme.  
  
5.  Dans la fenêtre Propriétés, sélectionnez le **Message** propriété, puis sélectionnez **Contoso3A2ResponseMessage** dans la liste déroulante.  
  
6.  Se connecter le **ContosoSQLReqResponsePort** en activant la poignée verte en regard du **réponse** étiquette et en le faisant glisser sur la poignée verte la **Receive_1** forme.  
  
7.  Dans le **fichier** Menu, cliquez sur **Enregistrer tout**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 8 : Création et déploiement de l’Orchestration Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)