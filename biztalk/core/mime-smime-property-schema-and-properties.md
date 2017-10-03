---
title: "Propriétés et schéma de propriété MIME-SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26dd25b9-7eb8-4354-9929-dc1985dd1d77
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 882b25733a46b8b7b973c992d465132df4c47b75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-property-schema-and-properties"></a>Propriétés et schéma de propriété MIME-SMIME

## <a name="namespace-properties"></a>Propriétés Namespace
Le **http://schemas.microsoft.com/BizTalk/2003/mime-properties** espace de noms contient les propriétés que vous pouvez utiliser pour définir les propriétés de contexte de message et de partie pour le composant de pipeline Encodeur MIME/SMIME. L’Encodeur MIME/SMIME utilise ces propriétés pour générer les en-têtes MIME/SMIME appropriés dans le message qui est créé. Le tableau suivant décrit les propriétés de MIME/SMIME.  
  
|Propriété|Portée|Type| Description|  
|--------------|-----------|----------|-----------------|  
|**FileName**|Par partie de message|xs:string|Définit l’en-tête de nom de fichier de la partie MIME/SMIME.|  
|**ID de contenu**|Par partie de message|xs:string|Définit l’en-tête d’ID de contenu de la partie MIME/SMIME.|  
|**ContentDescription**|Par partie de message|xs:string|Définit l’en-tête de description de contenu de la partie MIME/SMIME.|  
|**ContentTransferEncoding**|Par partie de message|xs:string|Définit l’en-tête de codage du transfert de contenu de la partie MIME/SMIME générée.<br /><br /> Cette valeur remplace la **codage de transfert de contenu** valeur configurée dans le Concepteur de Pipeline. Pour un message à parties multiples, vous pouvez utiliser différents codages pour les différentes parties MIME/SMIME.|  
|**ContentLocation**|Par partie de message|xs:string|Définit l’en-tête d'emplacement de contenu de la partie MIME/SMIME générée.|  
|**IsMIMEEncoded**|Par partie de message|xs:boolean|Spécifie si le message est associé à une charge MIME/SMIME. Le composant MIME inscrit directement cette valeur, vous n’avez pas besoin de la définir.|  
  
 L’encodeur MIME/SMIME utilise également les propriétés suivantes à partir de la **système** espace de noms.  
  
|Propriété|Type| Description|  
|--------------|----------|-----------------|  
|ContentType|xs:string|Correspond à l’en-tête de type de contenu de la partie MIME/SMIME générée.|  
|FileName|xs:string|Correspond au nom du fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [Comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [MIME (exemple BizTalk Server)](../core/mime-biztalk-server-sample.md)   
 **Les propriétés de contexte du message**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]