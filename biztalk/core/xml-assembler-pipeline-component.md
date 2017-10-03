---
title: Composant de Pipeline assembleur XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: 3adfd603-0577-49c2-ae9d-445d62fed385
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22348b61ca32567190fa99e103fe536f5199af58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-assembler-pipeline-component"></a>Composant de Pipeline assembleur XML
Le composant de pipeline Assembleur XML associe l'assemblage et la sérialisation XML en un composant. Sa fonction première est de remettre les propriétés de contexte de message dans les enveloppes et les documents.  
  
 Les actions suivantes se produisent dans le composant Assembleur XML après la réception d’un lot de messages formant un échange :  
  
1.  L’Assembleur crée l’enveloppe en utilisant la spécification d’enveloppe indiquée.  
  
2.  Le composant place les propriétés de contenu dans les instances de message en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés au message.  
  
3.  Le composant ajoute le message à l’enveloppe.  
  
4.  Le composant place les propriétés de contenu dans l’enveloppe en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés aux enveloppes.  
  
> [!NOTE]
>  Le composant de pipeline Assembleur XML ne renseigne pas les champs d’attribut absents, mais il alimente les champs d’élément vides lorsque les champs sont facultatifs et ne sont associés à aucune valeur fixe ou par défaut.  
  
 Pour plus d’informations sur la configuration du composant de pipeline Assembleur XML, consultez [comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Encodage de caractères dans le composant de Pipeline assembleur XML](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)  
  
-   [Dans le composant de Pipeline assembleur XML, les Instructions de traitement](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)  
  
-   [Messages non reconnus dans le composant de Pipeline assembleur XML](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)  
  
-   [Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)  
  
-   [Mise en œuvre de Structure de document dans le composant de Pipeline assembleur XML](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)