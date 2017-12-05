---
title: "Étape 4 : Créer le mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7f1f6d-0e57-4a65-b91d-c81fcc832961
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fcbce54a488cb687ad0fb2c7a1931243c8cd882
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-create-the-map"></a>Étape 4 : création du mappage
![L’étape 4 de 5](../core/media/step-4of5.gif "Step_4of5")  
  
 **Durée :** 6 minutes  
  
 **Objectif :** dans cette étape, vous créez un mappage qui transforme le message de demande de message RequestDecline.  
  
 **Objectif :** le mappage garantit que le numéro d’ID de demande et le total général sont inclus dans le message de refus de demande renvoyé au système de l’inventaire de l’entrepôt. Le Mappeur BizTalk permet de lier les champs dans un message entrant aux champs définis pour le message sortant. Cette opération est nécessaire car ces deux messages n'ont pas la même structure de schéma.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 2 : création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) et [étape 3 : créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md).  
  
## <a name="procedures"></a>Procédures  
 Le mappage dépend des schémas Request et RequestDecline.  Avant d'utiliser les schémas sur un mappage, vous devez compiler le projet avec le schéma.  
  
#### <a name="to-compile-the-eaischemas-project"></a>Pour compiler le projet EAISchemas  
  
-   Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **Build**.  
  
#### <a name="to-create-the-map"></a>Pour créer le mappage  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Modèles installés**|Cliquez sur **les fichiers de mappage**, puis cliquez sur **carte**.|  
    |**Nom**|Type **MapToReqDecline.btm**.|  
  
3.  Cliquez sur **Ajouter**.  
  
     La figure suivante illustre le schéma source, le schéma de destination et la grille du Mappeur.  
  
     ![Mappage MapToReqDenied](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")  
  
4.  Dans le **schéma Source** volet, cliquez sur **ouvrir le schéma Source**.  
  
5.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez **EAISchemas**, développez **schémas**, cliquez sur **EAISchemas.Request**, puis cliquez sur  **OK**.  
  
6.  Dans le **schéma Source** volet, avec le bouton droit  **\<schéma\>**, puis cliquez sur **développer le nœud d’arborescence**.  
  
7.  Dans le **schéma de Destination** volet, cliquez sur **ouvrir le schéma de Destination**.  
  
8.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez **EAISchemas**, développez **schémas**, cliquez sur **EAISchemas.RequestDecline**, puis Cliquez sur **OK**.  
  
9. Dans le **schéma de Destination** volet, avec le bouton droit  **\<schéma\>**, puis cliquez sur **développer le nœud d’arborescence**.  
  
10. Dans le **schéma Source** volet, faites glisser le **ReqID** au champ la **ReqID** dans les **schéma de Destination** volet. Une ligne reliant les deux éléments apparaît.  
  
11. Dans le **schéma Source** volet, faites glisser le **GrandTotal** au champ la **GrandTotal** champ dans le **schéma de Destination** volet pour mapper les données à partir d’un schéma à l’autre.  
  
12. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer votre travail.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez créé un mappage qui transforme le message Request en message RequestDecline.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créez le projet EAISchemas.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)   
 [Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md)   
 [Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md)   
 [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)   
 [Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)