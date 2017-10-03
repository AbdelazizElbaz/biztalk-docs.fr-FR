---
title: "Nœud de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea02c2a-ee00-4f44-9086-83d7ac4a8832
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee662cb9cb6e86b85a7760daf45af832a447b5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-node"></a>Nœud de schéma

## <a name="overview"></a>Vue d'ensemble
Dans l’Éditeur BizTalk, le haut de la hiérarchie de schéma est toujours le **schéma** nœud, qui ne peut pas être renommé. Le **schéma** nœud correspond à la **schéma** élément dans la représentation de langage de schéma XML (XSD) de la définition du schéma.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **schéma** nœud est représenté par la chaîne \<schéma > dans l’arborescence de schéma.  
  
 En général, les propriétés de la **schéma** nœud correspondent aux attributs de la **schéma** élément dans la représentation XSD du schéma. Pour obtenir des informations générales sur les propriétés d’un nœud, consultez [propriétés d’un nœud](../core/node-properties.md). Pour plus d’informations de référence sur les propriétés de la **schéma** nœud, consultez la **propriétés de nœud de schéma** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Lorsque vous créez un schéma XML dans l’Éditeur BizTalk, le **schéma** nœud et l’autre **racine** nœud sont créées automatiquement.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 L’exemple suivant, en caractères gras, les lignes dans la représentation XSD du schéma qui correspondent à la  **\<schéma >** nœud dans l’arborescence du schéma.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
 [Propriétés de nœud](../core/node-properties.md)   
 [Définir les propriétés de nœud](../core/how-to-set-node-properties.md)