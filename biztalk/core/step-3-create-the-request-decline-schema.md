---
title: "Étape 3 : Créer le schéma de refus de demande | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1ce166c-1be1-4ef4-9d00-3da7038d4ada
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ff343c58e836bc0738f0200016308eb7a4d90b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-the-request-decline-schema"></a>Étape 3 : création du schéma de refus de demande
![Étape 3 sur 5](../core/media/step-3of5.gif "Step_3of5")  
  
 **Durée :** 7 minutes  
  
 **Objectif :** dans cette étape, vous créez le schéma du message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] renvoie à l’entrepôt si le processus d’entreprise rejette la demande de réapprovisionnement de stock.  
  
 **Objectif :** le schéma définit les données et la structure du message de refus de demande. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le schéma pour identifier et interagir avec les données du message.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md).  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-the-request-decline-schema"></a>Pour créer le schéma de refus de demande  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Modèles installés**|Cliquez sur **les fichiers de schéma**, puis cliquez sur **schéma**.|  
    |**Nom**|Tapez `RequestDecline.xsd`.|  
  
3.  Cliquez sur **Ajouter**.  
  
4.  Dans l’Éditeur BizTalk, à partir de l’arborescence du schéma, cliquez sur le **racine** nœud pour le sélectionner.  
  
5.  Dans le volet Propriétés, modifiez la valeur de la **nom de nœud** propriété `DeclineReq`, puis appuyez sur ENTRÉE.  
  
6.  Dans l’arborescence du schéma, cliquez sur le **DeclineReq** nœud **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.  
  
7.  Type `ReqID` comme nouveau nom pour l’élément et appuyez sur ENTRÉE.  
  
8.  Ajouter un deuxième élément de champ enfant nommé `GrandTotal`.  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous créez le schéma du message que renvoie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'entrepôt si le processus d'entreprise rejette le message de demande de stock.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez le mappage nécessaire à l'orchestration pour créer le message de refus de demande en reformatant le message de demande.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)  
 [Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md)   
 [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)   
 [Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md)   
 [Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md)