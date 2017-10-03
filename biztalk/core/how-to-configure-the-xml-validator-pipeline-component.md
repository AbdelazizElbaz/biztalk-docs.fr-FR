---
title: Comment configurer le composant de Pipeline valideur XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Validator [pipeline component]
- send pipelines, validating
- pipeline components, XML Validator
- receive pipelines, validating
ms.assetid: 3b3becaf-703c-4399-a5ed-e7082e31e6e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 821ad6a1353c0aa29866fd36fe84a7ea6317690b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-xml-validator-pipeline-component"></a>Comment configurer le composant de Pipeline valideur XML
Vous pouvez utiliser le composant de pipeline Valideur XML dans n'importe quelle étape d'un pipeline d'envoi ou de réception (à l’exception de l’assemblage et du désassemblage).  
  
### <a name="to-configure-the-properties-for-the-xml-validator-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Valideur XML  
  
1.  Faites glisser le composant de pipeline Valideur XML dans l'étape Valider d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, définissez les éléments suivants.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Schémas de document**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md). Si aucun schéma n’est spécifié, la détection de schéma d’exécution est réalisée à l’aide d’espace de noms cible du message et les informations de nom d’élément racine. **Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** propriété. <br /><br /> Valeur par défaut : regroupement vide|  
    |Traitement des échanges récupérables|Si la valeur « false » est spécifiée, l'échange entier est validé en tant qu'unité (en cas d'échec d'un message, l'échange entier est suspendu).<br /><br /> Si la valeur « true » est spécifiée, les messages sont extraits de l'échange individuellement par le valideur avec la possibilité d'une propagation de certains d'entre eux via la messagerie et d'une suspension des autres.<br /><br /> Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline valideur XML](../core/xml-validator-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)