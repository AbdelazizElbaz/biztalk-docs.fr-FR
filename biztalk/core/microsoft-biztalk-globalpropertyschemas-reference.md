---
title: "Référence Microsoft.BizTalk.GlobalPropertySchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2acf3083-a0a9-483f-88bf-8023d9933e1e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1300dbcdb0bcc1534bbc0de2ab693ae49793867
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="microsoftbiztalkglobalpropertyschemas-reference"></a>Référence Microsoft.BizTalk.GlobalPropertySchemas
Le **Microsoft.BizTalk.GlobalPropertySchemas** espace de noms contient des schémas de propriété pour les propriétés qui utilisent des différents composants de BizTalk Server. Cet espace de noms contient des propriétés système que le moteur BizTalk utilise, des propriétés spécifiques au transport que chaque transport utilise pour gérer la configuration ainsi que des propriétés de configuration de composants de pipeline.  

## <a name="namespace-schemas"></a>Schémas de Namespace  

 Le tableau suivant présente les schémas de propriété globale inclus dans le **Microsoft.BizTalk.GlobalPropertySchemas** espace de noms.  
  
|Schéma de propriété|Composant et description|  
|---------------------|----------------------------------|  
|bts-btf2-properties.xsd|Schéma de propriété.|  
|btf2-endpoints-header.xsd<br /><br /> btf2-envelope.xsd<br /><br /> btf2-manifest-header.xsd<br /><br /> btf2-process-header.xsd<br /><br /> btf2-properties-header.xsd<br /><br /> btf2-receipt-header.xsd<br /><br /> btf2-services-header.xsd|Schémas définissant les constructions BizTalk Framework. Ces schémas sont spécifiques aux composants de pipeline Assembleur et Désassembleur BizTalk Framework.|  
|bts-system-properties.xsd|Il s’agit d'un schéma de propriété système. Le moteur BizTalk utilise la plupart des propriétés de ce schéma. Vous pouvez utiliser certaines propriétés pour le routage des messages. Pour plus d’informations sur les propriétés que vous pouvez utiliser pour le routage des messages, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|  
|bts-endpoint-properties.xsd|Il s’agit d’un schéma de propriété interne.|  
|bts-mime-properties.xsd<br /><br /> bts-xmlnorm-properties.xsd|Il s’agit des schémas de propriété pour les composants de pipeline : composants de pipeline MIME, XML, fichier plat et assembleur BizTalk Framework et désassembleur.|  
|bts-legacy-properties.xsd|BizTalk utilise ce schéma pour la mise à niveau [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] jusqu'à des applications de BizTalk Server.|  
|bts-messagetracking-properties.xsd|Le moteur de suivis utilise ce schéma.|  
|bts-file-properties.xsd<br /><br /> bts-ftp-properties.xsd<br /><br /> bts-http-properties.xsd<br /><br /> bts-pop3-properties.xsd<br /><br /> bts-smtp-properties.xsd<br /><br /> soap-encoding_1__1.xsd<br /><br /> soap-envelope_1__1.xsd<br /><br /> bts-soap-properties.xsd<br /><br /> bts-WindowsSharePointServices-properties.xsd|Il s'agit des schémas de propriété spécifiques au transport. Les transports utilisent ces schémas pour acheminer des informations et des configurations spécifiques au transport. Pour plus d’informations sur les transports, consultez [à l’aide des adaptateurs](../core/using-adapters.md).|  
|XLANGsBizTalkProperties.xsd|Le moteur d’orchestration utilise ce schéma.|  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des références aux espaces de noms BizTalk comprises dans les projets BizTalk](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)