---
title: "Étape 4 : Créer les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- creating, schemas
- schemas, creating
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ce9ea850632327e257909e1c7d4b60117865e46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-create-the-schemas"></a>Étape 4 : Créer les schémas
Dans cette étape, vous créez un nouveau projet (**BTAHL7 projet**) qui contient les artefacts de ce projet : les schémas, mappage et orchestration. Vous créez ensuite un schéma (**Doorbell.xsd**) pour le message entrant de codée au format XML, puis sélectionnez un schéma existant (**ADT_A04_22_GLO_DEF.xsd**) pour le message sortant encodé HL7. Ces schémas vous permet de définir la structure des messages qui vous exchange au sein de l’orchestration.  
  
### <a name="to-create-the-schemas"></a>Pour créer les schémas  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.  
  
3.  Dans le **modèles** volet, cliquez sur **projet BTAHL7 vide**.  
  
4.  Dans le **nom** , tapez **BTAHL7 projet** comme nom du projet.  
  
5.  Dans le **Solution** champ, sélectionnez **ajouter à la Solution**.  
  
6.  Dans le **emplacement** champ, vérifiez que  **\<* lecteur*\>: \Tutorial\BTAHL7V22Common** est le chemin d’accès.  
  
7.  Cliquez sur **OK** pour ouvrir le nouveau projet.  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions. Il ajoute le dossier du projet et crée des fichiers d’également le \< *lecteur*\>: \Tutorial\\**BTAHL7V22Common** dossier du projet.  
  
8.  Dans l’Explorateur de solutions, cliquez sur le **BTAHL7 projet** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
9. Dans l’ajouter un nouvel élément - projet de BTAHL7 boîte de dialogue, dans le **catégories** volet, cliquez sur **fichiers de schéma**et dans le **modèles** volet, cliquez sur **schéma**.  
  
10. Dans le **nom** , tapez **Doorbell.xsd** pour nommer le schéma.  
  
11. Cliquez sur **ajouter** pour ouvrir le schéma vide dans l’Éditeur BizTalk.  
  
12. Dans le  **\<schéma\>**  d’arborescence, cliquez sur le **racine** nœud, puis cliquez sur **renommer**.  
  
13. Type **DoorbellRoot** comme nouveau nom, puis appuyez sur **entrée**.  
  
14. Avec le bouton droit le **DoorbellRoot** nœud, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant** pour ajouter les champs suivants (Répétez cette étape pour chaque champ. élément) :  
  
    -   **Prénom**  
  
    -   **MiddleName**  
  
    -   **LastName**  
  
    -   **SSN**  
  
15. Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
16. Dans l’ajouter un nouvel élément - projet de BTAHL7 boîte de dialogue, dans le **catégories** volet, cliquez sur **BTAHL7 schémas**, puis cliquez sur **ajouter**.  
  
17. Dans la boîte de dialogue Sélecteur de schémas HL7, dans le **classe de Message** boîte, sélectionnez **V2.X**et dans le **détails du schéma** volet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Version**|Sélectionnez le numéro de version du message HL7. Dans ce didacticiel, utilisez **2.2**.|  
    |**Type de message**|Sélectionnez le type de message HL7. Dans ce didacticiel, utilisez **ADT**.|  
    |**Événement déclencheur**|Sélectionnez la valeur de l’événement déclencheur pour le message HL7. Dans ce didacticiel, utilisez **A04**.|  
  
18. Cliquez sur **Terminer** pour ajouter le schéma ADT_A04_22_GLO_DEF.xsd (inscrire un Patient) à votre projet. Fermez la boîte de dialogue Sélecteur de schémas HL7.  
  
19. Dans l’Explorateur de solutions, sous **BTAHL7 projet**, avec le bouton droit **références** puis cliquez sur **ajouter une référence**.  
  
20. Dans la boîte de dialogue Ajouter une référence sur le **projets** onglet, sélectionnez le **BTAHL7V22Common** de projet, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Cette opération ajoute une référence au projet d’origine afin que [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] reconnaît les schémas HL7 correctement.  
  
21. Dans l’Explorateur de solutions, sous **BTAHL7 projet**, avec le bouton droit **références** puis cliquez sur **ajouter une référence**.  
  
22. Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** onglet. Dans le **Regarder dans** zone, atteindre \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator pour le didacticiel de bout en HL7\SDK\End \Tutorial_BTAHL7Drop\Bin. Cliquez sur **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
 Passez à [étape 5 : promouvoir les propriétés d’un schéma](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)