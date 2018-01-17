---
title: "Création de Segments de Z déclaré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z objects, creating segments
- segments, creating Z segments [Z objects]
- Z segments, creating
- creating, Z segments [Z objects]
ms.assetid: afd1b7b7-089e-4c6a-a063-e708431bb888
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae9148547f527d29238b6080cd499be8da7b7e6
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-declared-z-segments"></a>Création de Segments de Z déclaré
Vous pouvez créer des segments Z déclarés à tout niveau d’un schéma (contrairement à non déclaré Z des segments, qui doit être la dernière partie d’un message multipartie, suivant le corps).  
  
### <a name="to-create-a-z-segment-in-biztalk-editor"></a>Pour créer un segment de Z dans l’Éditeur BizTalk  
  
1.  Dans l’Explorateur de solutions de Visual Studio, cliquez sur le schéma auquel vous souhaitez ajouter un segment de Z, puis cliquez sur **ouvrir**.  
  
2.  Dans l’Éditeur BizTalk, cliquez sur le nœud portant le nom du schéma, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
3.  Nom de l’enregistrement en commençant le nom avec trois caractères alphanumériques, en majuscules, avec le premier chiffre en cours à « Z ». (La balise de segment Z doit contenir trois caractères.) Pour ce faire, insérez un trait de soulignement (_) et puis ajoutez une brève description du segment. La description doit être une série de mots, sans espaces, avec la première lettre de chaque mot en majuscules. Le dernier mot doit être « Segment ». (Un exemple est « ZPP_PatientPreferencesSegment.) Appuyez sur **Entrée**.  
  
4.  Dans le volet Propriétés, tapez les propriétés souhaitées pour le segment Z, y compris **Data Structure Type** (nom de schéma ou XSD : anyType), **Max Occurs**, et **Min Occurs**.  
  
    > [!NOTE]
    >  Si vous entrez un type de structure de données pour l’enregistrement, vous ne serez pas en mesure d’ajouter un élément de champ enfant.  
  
5.  Dans l’Éditeur BizTalk, cliquez sur le nom du segment Z, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.  
  
6.  Tapez le nom du champ, en commençant le nom avec les trois premiers chiffres du nom du segment, suivi d’un point et le numéro du champ, suivi d’un trait de soulignement et une brève description du champ. La description doit être une série de mots, sans espaces, avec la première lettre de chaque mot en majuscules. Appuyez sur **Entrée**.  
  
7.  Dans le volet Propriétés, tapez les propriétés souhaitées pour le segment Z, y compris **Type de données**, **Nillable**, **fixe**, **Max Occurs**, et **Min Occurs**.  
  
8.  Pour créer un champ avec les composants, créez le champ en tant qu’enregistrement et puis créer un élément enfant de cet enregistrement pour chaque composant. Pour créer un champ avec les sous-composants, créez le champ et les composants sous forme d’enregistrements et les sous-composants en tant qu’enfant éléments. Notez que les sous-composants ne peut pas être des types de données composites. Par exemple, pour le segment nommé ZPP_PatientPreferencesSegment, vous pouvez créer un champ ZPP.1_Dietary et un composant PD.1 Allergies avec un sous-composant PD.1.1_FoodGroupAllergy. Le sous-composant PD.1.1_FoodGroupAllergy devrait être un type de données simple.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [Gestion des segments Z non déclarés](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)