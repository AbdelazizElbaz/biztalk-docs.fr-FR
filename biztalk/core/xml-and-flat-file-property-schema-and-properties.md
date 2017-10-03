---
title: "Schéma de propriété de fichier plat et XML propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d917b82-62c6-489f-99a9-97e429b6f7c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb69a5375603d307c15a0bf884c924c0f6e6bb31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-and-flat-file-property-schema-and-properties"></a>Propriétés et schéma de propriété de fichier plat et XML
Le **http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties** espace de noms contient les propriétés que vous pouvez utiliser pour configurer les composants de pipeline assembleur de fichier plat et désassembleur de fichier plat. Ces propriétés sont décrites dans le tableau suivant.  

## <a name="properties-list"></a>Liste Propriétés
  
|Propriété|Type| Description|  
|--------------|----------|-----------------|  
|**FlatFileHeaderDocument**|xs:string|L’en-tête d’un fichier plat entrant peut être stocké avec cette propriété.|  
|**AllowUnrecognizedMessage**|xs:Boolean|Spécifie si les messages non reconnus doivent être traités par les composants XML.|  
|**ProcessingInstruction**|xs:string|Texte d’instructions de traitement des documents sortants.|  
|**DocumentSpecName**|xs:string|Schéma des composants XML à utiliser pour l'analyse ou la sérialisation des documents.<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms #  racine cibles uniques. Si plusieurs schémas ont le même espace de noms #  racine, la validation des instances de document risque de ne pas fonctionner comme prévu. L'espace de noms # racine doit être unique.  Si des schémas doivent avoir le même espace de noms #  racine, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML, ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur XML.  Cette opération fonctionne également si aucun espace de noms n'existe.|  
|**EnvelopeSpecName**|xs:string|Spécification de l’enveloppe des composants XML à utiliser pour l'analyse et la sérialisation des documents.<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms #  racine cibles uniques. Si plusieurs schémas ont le même espace de noms #  racine, la validation des instances de document risque de ne pas fonctionner comme prévu. L'espace de noms # racine doit être unique.  Si des schémas doivent avoir le même espace de noms #  racine, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML, ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur XML.  Cette opération fonctionne également si aucun espace de noms n'existe.|  
|**TargetCharset**|xs:string|Jeu de caractères des composants XML à utiliser pour le codage des messages de sortie.|  
|**SourceCharset**|xs:string|Jeu de caractères utilisé pour coder un document avant qu’il ne soit traité par le Désassembleur XML.|  
|**ProcessingInstructionOption**|xs:int|Indique comment les instructions de traitement sont ajoutées aux documents sortants. Pour plus d’informations sur la ProcessingInstructionOption, voir [d’Instructions de traitement dans le composant de Pipeline assembleur XML](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md).|  
|**AddXMLDeclaration**|xs:boolean|Spécifier si une déclaration XML doit être ajoutée à un document sortant.|  
|**HeaderSpecName**|xs:string|Spécifie un en-tête de document de fichier plat.|  
|**TrailerSpecName**|xs:string|Spécifie un code de fin de document de fichier plat.|  
|**PromotePropertiesOnly**|xs:boolean|Lorsque la valeur **True**, le composant désassembleur XML ne pas supprimer une enveloppe de message ou désassembler. Seule une promotion des propriétés est effectuée.|  
  
## <a name="see-also"></a>Voir aussi  
-  [Configuration du composant de Pipeline assembleur fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
-  [Configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
-  [Configuration du composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
-  [Configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
-  [Configurer les composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
-  **Les propriétés de contexte du message**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]