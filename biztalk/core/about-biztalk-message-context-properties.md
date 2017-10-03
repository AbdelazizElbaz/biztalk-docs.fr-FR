---
title: "À propos des propriétés de contexte de Message BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc700e43-a44c-482b-b91c-9f1d997a486a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49d802ad2ca50538c25182311c68604c26d5a832
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-biztalk-message-context-properties"></a>À propos des propriétés de contexte de message BizTalk
Lorsqu'un document est reçu par un adaptateur BizTalk Server, ce dernier crée un message BizTalk pour le document. Ce message contient le document qui a été reçu ainsi qu'un contexte de message. Le contexte de message constitue un conteneur pour diverses propriétés utilisées par BizTalk Server lors du traitement du document. Chaque propriété du contexte de message est composée de trois éléments : un nom, un espace de noms et une valeur. Par exemple, la propriété de contexte de message suivante décrit l'ID d'échange d'un document :  
  
```  
<Property Name="InterchangeID" Namespace="http://schemas.microsoft.com/BizTalk/2003/system-properties" Value="{AC07BF30-2F1A-42B0-8390-191EF38BA839}"/>  
```  
  
 Des propriétés de contexte de message sont ajoutées au contexte du message durant toute la durée de vie de ce dernier lorsqu'il transite par le serveur BizTalk Server.  
  
 BizTalk utilise deux types de propriétés de contexte de message. Voir ci-dessous :  
  
## <a name="property-fields"></a>Champs de propriété  
 Les champs de propriété sont des propriétés de contexte de message qui sont utilisées par le moteur de messagerie BizTalk en vue du routage de documents, du suivi des messages et de l'évaluation dans les orchestrations. Vous pouvez explicitement élever le champ du document correspondant à un contexte de message au rang de champ de propriété en modifiant le schéma du document dans l'Éditeur de schéma BizTalk Server disponible dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour écrire un champ en tant que champ de propriété dans le document correspondant à un contexte de message, le schéma de document doit être associé à un schéma de propriété. Les champs de propriété sont limités à 255 caractères. Le **IsPromoted** des champs de propriété dans le contexte du message est définie sur **True**.  
  
## <a name="distinguished-fields"></a>Champs distinctifs  
 Les champs distinctifs sont des propriétés de contexte de message qui ne requièrent pas de schéma de propriété distinct et sont uniquement accessibles depuis des orchestrations. Les champs distinctifs ne peuvent pas être utilisés à des fins de routage ou de suivi. Les champs distinctifs ne nécessitant pas un schéma de propriété distinct, leur évaluation par le moteur d'orchestration implique une charge inférieure à celle requise pour l'évaluation des champs de propriété. L'évaluation des champs de propriété requiert une requête XPath. Ce n'est pas le cas des champs distinctifs puisque le pipeline Désassembleur les renseigne dans le contexte et le moteur d'orchestration lit les valeurs mises en cache. Toutefois, si le moteur d'orchestration ne trouve pas la propriété dans le contexte, il lancera une requête XPath pour rechercher la valeur. Les champs distinctifs ne sont pas limités en taille. Le **IsPromoted** des champs distinctifs dans le contexte du Message est définie sur **False**.  
  
## <a name="summary-of-differences-between-property-fields-and-distinguished-fields"></a>Résumé des différences existant entre les champs de propriété et les champs distinctifs  
 Le tableau suivant résume les différences et similitudes que comportent les champs de propriété et les champs distinctifs :  
  
|**Attribute**|**Champ de propriété**|**Champ distinctif**|  
|-------------------|------------------------|-----------------------------|  
|Propriété IsPromoted|True|False|  
|Limitation en taille|255 caractères|Pas de limite|  
|Utilisé pour le routage|Oui|Non|  
|Utilisé pour le suivi|Oui|Non|  
|Utilisé dans une orchestration|Oui|Oui|  
|Requiert un schéma de propriété|Oui|Non|  
|Accessible par les pipelines et les ports|Oui|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md)