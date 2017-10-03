---
title: "Étape 3 : Définition, publication et déploiement de la stratégie d’entreprise pour Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, deploying
- policies, publishing
- private process tutorial, creating policies
- policies, creating
ms.assetid: 529b16d8-226b-4046-a95d-64162ebd59a3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbdd1133145aada8b1a1abf0ccdde25547b7fed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-defining-publishing-and-deploying-the-business-policy-for-contoso"></a>Étape 3 : Définition, la publication et le déploiement de la stratégie d’entreprise pour Contoso
Dans cette étape, vous créez une stratégie d’entreprise qui réserve une quantité définie d’unités pour chaque produit Contoso fabrique à utiliser en cas d’urgence.  
  
### <a name="to-add-a-new-policy"></a>Pour ajouter une nouvelle stratégie  
  
1.  Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.  
  
2.  Nommez la nouvelle stratégie **3A2PriceAvailabilityPolicy**, puis appuyez sur **entrée**.  
  
### <a name="to-add-a-policy-rule-to-enforce-the-emergency-quantity-needs"></a>Pour ajouter une règle de stratégie afin d’appliquer la quantité d’urgence doit  
  
1.  Avec le bouton droit **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **ajouter une nouvelle règle**.  
  
2.  Nommez la règle **règle fournir d’urgence - quantité épuisé**, puis appuyez sur **entrée**.  
  
3.  Dans l’éditeur des règles d’entreprise, dans le volet droit, cliquez sur **Conditions** sous le volet IF, pointez sur **prédicats**, puis cliquez sur le **inférieur ou égal** prédicat.  
  
4.  Dans le volet Explorateur de faits, développez **vocabulaires**, développez **3A2PriceAvailabilityVocabulary**, développez **Version 1.0 - publiée**, sélectionnez **quantité Disponible**et faites-le glisser vers le `argument1` espace réservé sur l’aire de compositeur.  
  
5.  Répétez l’étape 4 en faisant glisser **quantité d’urgence nécessaire** sur la `argument2` espace réservé.  
  
6.  Sélectionnez **Final quantité disponible**et faites-le glisser sur **Actions** dans le volet THEN.  
  
### <a name="to-add-a-policy-to-revise-the-number-available-field-in-the-response"></a>Pour ajouter une stratégie pour modifier le champ nombre disponibles dans la réponse  
  
1.  Avec le bouton droit **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **ajouter une nouvelle règle**.  
  
2.  Nommez la nouvelle règle **d’urgence fournir règle - quantité disponible**, puis appuyez sur **entrée**.  
  
3.  Dans l’éditeur des règles d’entreprise, dans le volet droit, cliquez droit **Conditions** sous le volet IF, pointez sur **prédicats**, puis cliquez sur le **supérieur** prédicat.  
  
4.  Dans le volet Explorateur de faits, développez **vocabulaires**, développez **3A2PriceAvailabilityVocabulary**, développez **Version 1.0 - publiée**, sélectionnez **quantité Disponible**et faites-le glisser sur le `argument1` espace réservé sur l’aire de compositeur.  
  
5.  Répétez cette étape même en faisant glisser **quantité d’urgence nécessaire** sur la `argument2` espace réservé.  
  
6.  Sélectionnez **Final quantité disponible**et faites-le glisser sur **Actions** dans le volet THEN.  
  
7.  Dans le volet Explorateur de faits, développez **Version 1.0 - publiée** sous **fonctions**et faites glisser le `Subtract` de fonction sur le **0** argument suivant pour  **Dernière quantité disponible** dans le volet THEN.  
  
8.  Faites glisser **quantité disponible** (sous **3A2PriceAvailabilityVocabulary**) et déposez-le sur le `value1` espace réservé dans le volet THEN.  
  
9. Faites glisser **quantité d’urgence nécessaire**et déposez-la sur la `value2` espace réservé dans le volet THEN.  
  
### <a name="to-save-publish-and-deploy-the-business-policy"></a>Pour enregistrer, publier et déployer la stratégie d’entreprise  
  
1.  Dans le volet Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **enregistrer**.  
  
2.  Cliquez sur ce même nœud, puis cliquez sur **publier**.  
  
3.  Cliquez sur ce même nœud, puis cliquez sur **déployer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Création du projet de HeaderHelper](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)