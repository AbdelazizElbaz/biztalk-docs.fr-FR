---
title: "Nœuds racines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2161f877-835e-434d-a8d1-2426f977d60e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2070982a6bca09e8bffb2bcc88e5997360c86851
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="root-nodes"></a>Nœuds racine
Dans l’Éditeur BizTalk, les nœuds enfants de la **schéma** nœud sont appelés **racine** nœuds. **Racine** nœuds sont un type spécial de **enregistrement** nœud, et avoir quelques propriétés supplémentaires que regular **enregistrement** nœuds. Le **racine** nœud représente le type de document décrit par le schéma et peut être renommé selon les besoins. Par exemple, vous pouvez renommer la **racine** nœud afin qu’il décrive le type de message que le schéma représente, tel que purchaseOrder, orderAcknowledgment ou shipNotice.  
  
 Lorsque vous créez un schéma XML dans l’Éditeur BizTalk, le **schéma** nœud et l’autre **racine** nœud sont créées automatiquement. Vous pouvez créer d’autres **racine** nœuds en tant qu’enfants de le **schéma** nœud ; cela vous permet de créer une bibliothèque de schémas dans une représentation de langage XML Schema definition (XSD) unique. Vous pouvez par exemple créer une bibliothèque de schémas pour décrire les différents schémas de messages connexes pour envoyer des bons de commande et appeler les différents nœuds racine purchaseOrder, orderAcknowledgment et shipNotice.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 L’exemple suivant affiche les lignes dans la représentation XSD du schéma qui correspondent à la **racine** nœud dans l’arborescence du schéma.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="Root">  
        <xs:complexType />   
    </xs:element>  
</xs:schema>  
```  
  
 **Racine** nœuds dans l’Éditeur BizTalk représentent l’élément principal d’une instance XML correspondante du message en question. Par exemple, si le **racine** nœud d’un schéma particulier est renommé en purchaseOrder, la représentation XSD correspondante présente la structure de haut niveau suivante.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="">  
        <xs:complexType>   
            ...  
        </xs:complexType>   
    </xs:element>  
</xs:schema>  
```  
  
 Un message d'instance XML correspondant doit présenter la structure de base suivante.  
  
```  
<?xml version="1.0"?>  
<purchaseOrder ...>  
    ...  
</purchaseOrder>  
```  
  
> [!NOTE]
>  Nœuds racine ne peuvent pas avoir **champ** attributs. **Champ** attributs attaché à la **racine** nœud ne sont pas enregistrées avec le schéma.  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud enregistrement**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)