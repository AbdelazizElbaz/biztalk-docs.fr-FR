---
title: "Étape 8 : Créer un mappage avec le Mappeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, maps
- creating, maps
- maps, creating
- BizTalk Mapper
ms.assetid: 785426c7-5651-48be-b3f4-7f9d8051ba23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48e2578211d65ade2a50916e909c87a6fd84bf44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-create-a-map-with-biztalk-mapper"></a>Étape 8 : Créer un mappage avec le Mappeur BizTalk
Dans cette étape, vous utilisez le Mappeur BizTalk pour créer un mappage. Vous utilisez ce mappage pour créer des liens qui associent les données (champs) dans un document de demande de réapprovisionnement aux données dans une document de refus de la demande.  
  
### <a name="to-create-a-map"></a>Pour créer un mappage  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **les fichiers de mappage**.  
  
3.  Dans le **nom** , tapez **DoorbellMap** pour nommer la carte, puis cliquez sur **ajouter** pour démarrer le Mappeur BizTalk.  
  
4.  Dans le **schéma Source** volet (gauche), cliquez sur **ouvrir le schéma Source**.  
  
5.  Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **BTAHL7 projet**, développez **schémas**, cliquez sur **BTAHL7_Project.Doorbell**, puis cliquez sur **OK**.  
  
6.  Dans le **schéma de Destination** volet (à droite), cliquez sur **ouvrir le schéma de Destination**.  
  
7.  Dans le sélecteur de Type BizTalk, développez **BTAHL7 projet**, développez **schémas**, cliquez sur **BTAHL7Schemas.ADT_A04_22_GLO_DEF**, puis cliquez sur **OK**.  
  
8.  Dans le **schéma de Destination** volet (à droite), développez **ADT_A04_22_GLO_DEF**, développez **PID_PatientIdentification**, développez **PID.5_PatientName** .  
  
9. Dans le **schéma Source** volet (gauche), développez **DoorbellRoot**. Faites glisser le **LastName** au champ la **PN_0_FamilyName** champ dans le **schéma de Destination** volet.  
  
10. Dans le **schéma Source** volet, faites glisser le **FirstName** au champ la **PN_1_GivenName** champ dans le **schéma de Destination** volet.  
  
11. Dans le **schéma Source** volet, faites glisser le **MiddleName** au champ la **PN_2_MiddleInitialOrName** champ dans le **schéma de Destination** volet .  
  
12. Dans le **schéma de Destination** volet, développez **PID_3_PatientIdInternalId**.  
  
13. Dans le **schéma Source** volet, faites glisser le **SSN** au champ la **CM_PAT_ID_0_PatientID** dans les **schéma de Destination** volet.  
  
14. Dans le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
 Dans un scénario d’enrichissement de message classique, si toutes les informations sur les patients manquantes, vous serez effectuer un appel à une base de données des enregistrements du Patient dans votre orchestration et ajoutez les informations manquantes, puis utilisez les informations supplémentaires pour terminer le mappage. Par exemple, vous pouvez extraire l’adresse d’un patient à partir de la base de données des enregistrements de Patient, car il n’a pas fourni par le message d’événement de déclencheur de sonnette XML entrant.  
  
 Passez à [étape 9 : valider et générez le projet de la carte](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)