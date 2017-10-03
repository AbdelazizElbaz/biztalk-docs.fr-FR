---
title: "Étape 2 : Définition et publication du vocabulaire pour Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vocabularies, creating
- vocabularies, publishing
- private process tutorial, creating vocabularies
ms.assetid: e23880c0-772c-48c6-a6b5-32eb951527c8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15937a1235cc1776be38fe2b0e5529c19d3f6fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-defining-and-publishing-the-vocabulary-for-contoso"></a>Étape 2 : Définition et publication du vocabulaire pour Contoso
Dans ce scénario, Contoso implémente une stratégie commerciale qui permet de s'assurer que le stock est toujours disponible en cas d'urgence. Vous créez des stratégies d’entreprise à l’aide de l’éditeur des règles d’entreprise dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Dans cette étape, vous créez le vocabulaire à utiliser quand vous définissez la stratégie commerciale.  
  
### <a name="to-add-a-new-vocabulary"></a>Pour ajouter un nouveau vocabulaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans la boîte de dialogue Ouvrir le magasin de règles, cliquez sur **OK**.  
  
3.  Dans le volet Explorateur de faits, sous l'onglet **Vocabulaires** , cliquez avec le bouton droit sur **Vocabulaires**, puis cliquez sur **Ajouter un nouveau vocabulaire**.  
  
4.  Nommez le vocabulaire **3A2PriceAvailabilityVocabulary**, puis appuyez sur **Entrée**.  
  
### <a name="to-define-a-constant-vocabulary-value"></a>Pour définir une valeur constante de vocabulaire  
  
1.  Dans l'Éditeur des règles d'entreprise, cliquez sur **3A2PriceAvailabilityVocabulary**, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **Ajouter une nouvelle définition**.  
  
2.  Dans la page **Assistant Définition de vocabulaire** , sélectionnez **Valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Valeur constante, plage de valeurs ou ensemble de valeurs** , dans la zone **Nom de la définition** , tapez **Quantité d'urgence nécessaire**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Définir une valeur constante** , dans la zone **Valeur** , tapez **800**, puis cliquez sur **Terminer**.  
  
### <a name="to-define-an-xml-document-get-element"></a>Pour définir l'élément 'Get' d'un document XML  
  
1.  Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Ajouter une nouvelle définition**.  
  
2.  Sur le **VocabularyDefinition Assistant** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
3.  Dans la page **Élément ou attribut de document XML** , dans la zone **Nom de la définition** , tapez **Quantité disponible**.  
  
4.  Cliquez sur **Parcourir** (en regard du champ **Schema** ), accédez au projet **ContosoPriceAndAvailability** dans votre dossier de solutions, sélectionnez le schéma **ContosoPriceAndAvailability.xsd** , puis cliquez sur **Ouvrir**.  
  
5.  Dans la boîte de dialogue Sélectionner une liaison, développez **rootPriceResponse**, développez **Products**, sélectionnez l'élément **NumberAvailable** , puis cliquez sur **OK**.  
  
6.  Dans la page **Élément ou attribut de document XML** , dans la zone **Type de document** , assurez-vous que la valeur est **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  Dans la section **Sélectionner une opération** , sélectionnez **Effectuer une opération "Get"**, puis cliquez sur **Terminer**.  
  
### <a name="to-define-an-xml-document-set-element"></a>Pour définir l'élément 'Set' d'un document XML  
  
1.  Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Ajouter une nouvelle définition**.  
  
2.  Sur le **VocabularyDefinition Assistant** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
3.  Dans la page **Élément ou attribut de document XML** , dans la zone **Nom de la définition** , tapez **Quantité disponible finale**.  
  
4.  Cliquez sur **Parcourir** (en regard du champ **Schema** ), accédez au projet **ContosoPriceAndAvailability** dans votre dossier de solutions, sélectionnez le schéma **ContosoPriceAndAvailability.xsd** , puis cliquez sur **Ouvrir**.  
  
5.  Dans le **sélectionnez une liaison** boîte de dialogue, développez **rootPriceResponse**, développez **produits**, puis sélectionnez le **NumberAvailable** élément. Cliquez sur **OK**.  
  
6.  Dans la page **Élément ou attribut de document XML** , dans la zone **Type de document** , assurez-vous que la valeur est **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  Dans la section **Sélectionner une opération** , sélectionnez **Effectuer une opération "Set"**, puis cliquez sur **Suivant**.  
  
8.  Dans la page **Indiquez le nom complet** , cliquez sur **Terminer**.  
  
### <a name="to-save-and-publish-the-vocabulary"></a>Pour enregistrer et publier le vocabulaire  
  
1.  Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Enregistrer**.  
  
2.  Cliquez avec le bouton droit sur le même nœud **Version 1.0** , puis cliquez sur **Publier**.  
  
    > [!NOTE]
    >  Laissez l'Éditeur des règles d'entreprise ouvert pour l'étape suivante du didacticiel.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Définition, la publication et le déploiement de la stratégie d’entreprise pour Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)