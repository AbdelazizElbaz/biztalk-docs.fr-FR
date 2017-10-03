---
title: Comment configurer le composant de Pipeline assembleur XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], configuring
- messages, XML documents
- messages, envelopes
- configuring, pipeline components
- pipeline components, XML Assembler
ms.assetid: 6d883819-a1d4-4ad0-b08f-fcd7583134d6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cf69d5bd982571aefcf794d6ad32b0e69499470
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-xml-assembler-pipeline-component"></a>Comment configurer le composant de Pipeline assembleur XML
Le composant de pipeline Assembleur XML permet de placer les documents XML dans des enveloppes XML avant l'envoi d'un message à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-properties-for-the-xml-assembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Assembleur XML  
  
1.  Faites glisser le composant de pipeline Assembleur XML dans l'étape d'assemblage d'un pipeline d'envoi.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ajoutez les instructions de traitement**|**Ajouter**: valeur de **ajouter le texte des instructions de traitement** s’ajoute aux préexistant sur les instructions de traitement dans le message.<br /><br /> **Créer :** valeur **ajouter le texte des instructions de traitement** entré dans le champ doit remplacer ou remplacer toutes les instructions du message de traitement existantes.<br /><br /> Si **créer un nouveau** est sélectionnée, le **ajouter le texte des instructions de traitement** doit comporter des instructions de traitement valides.<br /><br /> **Ignorer**: si le traitement d’instructions existent dans le message, il est supprimé.<br /><br /> Valeur par défaut : **Append**|  
    |**Ajouter le texte des instructions de traitement**|Spécifie les instructions de traitement XML à ajouter au début du document XML cible. **Remarque :** texte doit être conforme aux normes des instructions de traitement XML W3C l’instruction de traitement. <br /><br /> Valeur par défaut : Aucun|  
    |**Ajouter une déclaration XML**|Lorsque **True**, ajoute une déclaration XML semblable au suivant dans le document sortant : `<?xml version='1.0' encoding='UTF-8'>`. L’encodage est déterminé par le document cible défini au moment de l’exécution.<br /><br /> Valeur par défaut : **True**|  
    |**Schémas de document**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md). **Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** propriété. <br /><br /> Valeur par défaut : regroupement vide|  
    |**Schémas d’enveloppe**|Indique l'espace de noms et le nom de type du ou des schémas à appliquer à l'enveloppe. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md). **Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas d’enveloppe** propriété. <br /><br /> Valeur par défaut : regroupement vide|  
    |**Conserver la marque d’ordre d’octet**|Indiquer si une marque d'ordre de tri doit être ajoutée aux documents générés par le composant Assembleur.<br /><br /> Valeur par défaut : **True**|  
    |**Étendue des instructions de traitement**|Indiquer si les instructions de traitement sont définies au niveau de l'enveloppe externe ou du document.<br /><br /> Valeur par défaut : **Document**|  
    |**Jeu de caractères cible**|Spécifie le jeu de caractères cible utilisé pour le codage des messages sortants.<br /><br /> Valeur par défaut : Aucun|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)