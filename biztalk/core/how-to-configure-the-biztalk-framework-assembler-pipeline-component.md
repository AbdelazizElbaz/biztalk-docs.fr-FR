---
title: Comment configurer le composant de Pipeline assembleur BizTalk Framework | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Assembler
- BizTalk Framework Assembler [pipeline component], configuring
ms.assetid: 2fd51047-b9dd-4b98-a968-45d69148664e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8337f5dcb2133d2a219d055751835b4ed14d379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-biztalk-framework-assembler-pipeline-component"></a>Configuration du composant de pipeline Assembleur BizTalk Framework
### <a name="to-configure-the-properties-for-the-biztalk-framework-assembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Assembleur BizTalk Framework  
  
1.  Faites glisser le composant de pipeline Assembleur BizTalk Framework dans la phase d'assemblage du pipeline d'envoi.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, définissez les valeurs de propriété suivantes.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ajouter le texte des instructions de traitement**|Permet aux documents XML assemblés de contenir des instructions de traitement en tant que valeur de cette propriété. Cela permet également aux documents de contenir des instructions pour les applications. **Remarque :** texte doit être conforme aux normes des instructions de traitement XML W3C l’instruction de traitement. <br /><br /> Valeur par défaut : ajouter|  
    |**Ajouter une déclaration XML**|Ajoute une déclaration XML à un message sortant. Lorsque la valeur est true, la déclaration XML suivante est ajoutée au message sortant : `<?xml version='1.0' encoding='UTF8'>`. Le codage spécifié dépend de l’encodage utilisé par l’assembleur BizTalk Framework, qui respecte les propriétés d’exécution spécifiques détenant les informations de codage.<br /><br /> Valeur par défaut : **True**|  
    |**Adresse de réception de remise**|Spécifie l'adresse à laquelle l'accusé de réception du document BizTalk Framework sera envoyé. **Avertissement :** lors de l’utilisation de l’assembleur BizTalk Framework avec les accusés de réception activés, il est probable que le traitement des accusés de réception peut être retardé en ce qui provoque un blocage. Le blocage se produit lorsque plusieurs accusés de réception sont traités dans des lots distincts pour un message unique. Pour éviter ce problème, vous devez configurer la taille de lot sur 1 pour l'emplacement du port de l'adresse de l'accusé de réception entré.|  
    |**Type adresse accusé de réception**|Spécifie le type de l'adresse à laquelle l'accusé de réception du document BizTalk Framework devra être envoyé.<br /><br /> Valeur par défaut : biz : **Remarque :** le préfixe biz : a été utilisé pour désigner les identificateurs d’organisation des points de terminaison source et de destination dans Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]et pour l’interopérabilité avec ces systèmes. Ce préfixe est utilisé par défaut. Par exemple, tapez = « biz : NomOrganisation », (src &#124; dest) = « Party1 ».|  
    |**Accusé de réception envoyé par heure**|Spécifie la durée (en minutes) passée laquelle l'accusé de réception du document BizTalk Framework doit être reçu.<br /><br /> Valeur par défaut : 30|  
    |**Adresse de destination**|Spécifie l'adresse de destination.<br /><br /> Valeur par défaut : Aucun|  
    |**Type d’adresse de destination**|Spécifie le type de l'adresse de destination.<br /><br /> Valeur par défaut : biz : **Remarque :** le préfixe biz : a été utilisé pour désigner les identificateurs d’organisation des points de terminaison source et de destination dans [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]et pour l’interopérabilité avec ces systèmes. Ce préfixe est utilisé par défaut. Par exemple, tapez = « biz : NomOrganisation », (src &#124; dest) = « Party1 ».|  
    |**Schémas de document**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md). **Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** propriété. <br /><br /> Valeur par défaut : regroupement vide|  
    |**Rubrique de document**|Indique une référence URI qui identifie uniquement l'usage général du document BizTalk Framework.<br /><br /> Valeur par défaut : Aucun|  
    |**Schémas d’enveloppe**|Indique l'espace de noms et le nom de type du ou des schémas à appliquer à l'enveloppe. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md). **Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas d’enveloppe** propriété. <br /><br /> Valeur par défaut : BTF2Schemas.btf2_envelope|  
    |**Générer accusé de réception de demande**|Indique si la requête d'accusé de réception du document BizTalk Framework doit être générée. Cette option permet de garantir la fiabilité de la messagerie de BizTalk Framework.<br /><br /> Valeur par défaut : **True**|  
    |**Durée de vie (en minutes) du message**|Spécifie la durée de validité (en minutes) du message.<br /><br /> Valeur par défaut : 30|  
    |**Instructions de traitement**|Définit la manière dont les instructions de traitement XML sont gérées dans le document d'instance XML.<br /><br /> **Ajouter**: la valeur de **ajouter le texte des instructions de traitement** s’ajoute aux préexistant sur les instructions de traitement dans le message.<br /><br /> **Créer nouveau**: la valeur de **ajouter le texte des instructions de traitement** entré dans le champ doit remplacer ou remplacer toutes les instructions du message de traitement existantes.<br /><br /> Si **créer un nouveau** est sélectionnée, **ajouter le texte des instructions de traitement** doit comporter des instructions de traitement valides.<br /><br /> **Ignorer**: si le traitement d’instructions existent dans le message, il est supprimé.<br /><br /> Valeur par défaut : **Append**|  
    |**Adresse source**|Spécifie l'adresse source.<br /><br /> Valeur par défaut : Aucun|  
    |**Type d’adresse source**|Spécifie le type de l'adresse source.<br /><br /> Valeur par défaut : biz : **Remarque :** le préfixe biz : a été utilisé pour désigner les identificateurs d’organisation des points de terminaison source et de destination dans [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]et pour l’interopérabilité avec ces systèmes. Ce préfixe est utilisé par défaut. Par exemple, tapez = « biz : NomOrganisation », (src &#124; dest) = « Party1 ».|  
    |**Jeu de caractères cible**|Spécifier le jeu de caractères cible utilisé pour le codage des messages sortants.<br /><br /> Valeur par défaut : Aucun|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur BizTalk Framework](../core/biztalk-framework-assembler-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)