---
title: "Schémas de message pour les Types d’enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RECORD types, message schemas for
- RECORD types, support for
ms.assetid: 637c42f2-eed0-4941-a6cd-7e03d01088b8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9022274041e06ad8ccc3f5243715d44d2b64282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-record-types"></a>Schémas de message pour les Types d’enregistrements
Types d’enregistrements Oracle sont les types de données structurées PL/SQL qui se composent d’une ou plusieurs des types de base de données simple ou structuré. Types d’enregistrements sont principalement utilisées dans les procédures stockée PL/SQL et des fonctions pour envoyer et recevoir des données hiérarchiques.  
  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les types d’enregistrement de la manière suivante :  
  
-   Types d’enregistrements sont exposés en tant que types complexes.  
  
-   Types d’enregistrement peuvent être imbriqué (enregistrement d’un enregistrement).  
  
-   Types d’enregistrement peuvent être déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.  
  
-   Types d’enregistrements peuvent être déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL ; par exemple, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.  
  
 Lorsqu’un paramètre de type d’enregistrement est utilisé dans une procédure stockée ou une fonction, il est compatible avec l’espace de noms de cette opération. Le code XML suivant montre la structure d’un type d’enregistrement dans un message :  
  
```  
<[REC_PARAM_NAME]>  
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
 [REC_PARAM_NAME] est le nom du paramètre d’enregistrement.  
  
 [Nom_champ] est le nom d’un champ dans le type d’enregistrement.  
  
 [OPERATION_NAMESPACE] est l’espace de noms de la procédure stockée ou fonction dans laquelle le paramètre d’enregistrement est utilisé.  
  
 Le code XML suivant montre la structure d’un paramètre de type d’enregistrement avec un champ de type enregistrement imbriqué :  
  
```  
<[REC_PARAM_NAME]>    
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  <[REC_PARAM_NAME2]>  
    <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
    <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME2]>  
    …  
  </[REC_PARAM_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)