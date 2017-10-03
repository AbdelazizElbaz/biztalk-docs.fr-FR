---
title: "Schéma de message pour les opérations de liste de choix | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picklist operations, message schemas for
- picklist operations, message actions
- picklist operations, message
ms.assetid: c0b62a8c-5a68-47ea-8676-1580601b5ec9
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d72a16e99e38649a6fb8d74178d2b5da1d059dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schema-for-picklist-operations"></a>Schéma de message pour les opérations de liste de choix
Listes de choix sont les types de champ spécial dans des composants d’entreprise. Elles représentent une collection de valeurs à partir de laquelle un utilisateur peut choisir une valeur unique pour l’attribution. Listes de choix sont de types différents. Pour plus d’informations sur les listes de choix et leurs types, reportez-vous à la documentation de Siebel.  
  
 Un des types de liste de choix, listes déroulantes délimitées statiques, sont signalées par les adaptateurs comme une liste de choix énumérée type dans les métadonnées générées par l’adaptateur au moment du design. Contient un ensemble statique de valeurs qui doivent être spécifiés pour le type de liste déroulante au moment de l’exécution.  Lors de la spécifier une valeur pour une liste de choix limitée statique, vous devez toujours spécifier une valeur qui appartient au jeu.  
  
 L’exemple suivant montre le schéma d’un type de liste de choix limitée statique :  
  
```  
<element name="[FIELD_NAME]RequiredPickListType" nillable="true" type="ns1:[FIELD_NAME]RequiredPickListType" />  
<simpleType name="[FIELD_NAME]RequiredPickListType">  
<restriction base="string">  
  <enumeration value="value1" />  
  <enumeration value="value2" />  
  …  
</restriction>  
</simpleType>  
```  
  
 [Nom_champ] = nom de champ de liste de choix dans le composant de gestion  
  
 Ce qui suit représente l’expérience de proxy de type statique de liste déroulante liée :  
  
```  
[BC]InsertRecord[] insertRecs = new [BC]InsertRecord[1];  
insertRecs[0] = new [BC]InsertRecord();  
insertRecs[0].[BC_STATIC_PICKLIST_FIELD] = [BC_PICKLIST_FIELD_NAME]OptionalPickListType.value1;  
```  
  
 [BC_STATIC_PICKLIST_FIELD] = un champ statique de liste déroulante liée dans la BC  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)