---
title: "Comment utiliser les Types de Message à parties multiples | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi-part message types, parts
- multi-part message types, creating
- multi-part message types, type modifiers
- messages
- multi-part message types, deleting
- orchestrations, messages
- deleting, multi-part messages
- multi-part message types, about multi-part message types
- orchestrations, type modifier
- messages, multi-parts
- creating, multi-part messages
- messages, about messages
ms.assetid: 009a39bd-cfc4-42d9-918c-88ac24bfc370
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4e4a07b88e832d99f586d10cdf8af4dbea3af3e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-multi-part-message-types"></a>Comment utiliser les Types de Message à parties multiples
Chaque message possède un type de message à parties multiples (description de la structure du message qui est composée de zéro partie ou plus). Les parties sont déterminées par les schémas de langage XSD (XML Schema Definition) ou les classes .NET. Vous avez la possibilité de définir vos propres types de messages à parties multiples ou d'utiliser les classes .NET et schémas existants.  
  
 Vous pouvez accéder directement à des parties de messages ou les affecter à partir de votre orchestration. Vous avez également la possibilité d'utiliser des éléments distincts des parties de message exposées en tant que champs distinctifs ou champs de propriété. Pour plus d’informations, consultez [à l’aide des champs distinctifs et les propriétés de Message](../core/using-distinguished-fields-and-property-fields.md).  
  
> [!NOTE]
>  Un type de message à parties multiples ne contient pas forcément plusieurs parties.  
  
> [!NOTE]
>  Une partie de message peut être définie par le type .NET **XmlDocument**, qui peut être utilisé pour contenir un document XML arbitraire, type de prise en charge de sérialisation personnalisée par n’importe quel type .NET qui est sérialisable XML, ou un .NET.  
  
## <a name="add-a-multi-part-message-type"></a>Ajouter un type de message à parties multiples  
  
1.  Dans le **Vue Orchestration** fenêtre, développez le **Types** nœud.  
  
2.  Avec le bouton droit **Types Message à parties multiples** puis cliquez sur **nouveau Type de Message de parties multiples**.  
  
     Le **Types Message à parties multiples** dossier se développe, s’il était réduit et un nouveau type de message à parties multiples est ajouté avec la partie de message par défaut.  
  
3.  Nommez ce type ainsi que la partie du message fournie.  
  
     Si votre type de message à parties multiples nécessite plus d’une partie de message, vous pouvez ajouter des parties supplémentaires en affectant un nom pour le \<nouveau\> partie de message.  
  
4.  Associez chaque partie du message à un type, comme une classe .NET ou un schéma.  
  
## <a name="remove-a-multi-part-message-type"></a>Supprimer un type de message à parties multiples  
  
-   Dans le **Vue Orchestration** (fenêtre), avec le bouton droit le multi-part message type que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  La suppression d'un type de message à parties multiples de votre orchestration supprime également les informations sur le type dans les messages qui l'utilisent.  
  
    > [!NOTE]
    >  Les éléments apparaissant en lecture seule sont définis dans une autre orchestration.  
  
## <a name="remove-a-part-from-a-multi-part-message-type"></a>Supprimer un composant d’un type de message à parties multiples  
  
-   Dans le **Vue Orchestration** fenêtre, avec le bouton droit de la partie que vous souhaitez supprimer, cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  Vous ne pouvez pas supprimer la partie de message d’un type de message si le **corps du Message** est définie sur true. Vous devez d’abord définir le **corps du Message** propriété sur True pour une autre des parties du type de message.  
  
## <a name="set-the-type-modifier-for-a-multi-part-message-type"></a>Définir le modificateur de type pour un type de message à parties multiples  
  
-   Dans le **propriétés** fenêtre, définissez la propriété suivante :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Modificateur de type**|Détermine l'étendue du type de message à parties multiples :<br /><br /> -   **Privé :**l’accès à ce type de message à parties multiples est limité au module contenant.<br />-   **Public :**l’accès à ce type de message à parties multiples n’est pas limité.<br />-   **Interne —**accès à ce type de message à parties multiples est limité aux modules dans le même projet.|  
  
## <a name="add-parts-to-an-existing-multi-part-message"></a>Ajouter des parties à un message à parties multiples existant  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'ajouter des parties à un message XLANG à parties multiples, mais également de faire référence à une partie du message par un index supérieur au nombre initialement déclaré de parties existantes. Cette fonction peut s'avérer particulièrement utile pour l'envoi et la réception de messages SMTP ayant un nombre variable de pièces jointes. Cette fonctionnalité est implémentée comme indiqué ci-dessous :  
  
-   À partir de votre projet, ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.  
  
-   Créez une variable (par exemple *xlangPart*) de type **Microsoft.XLANGs.BaseTypes.XLANGMessage**.  
  
-   Appelez *xlangPart***. AddPart(...)**  en utilisant les arguments appropriés à partir d’une forme Expression.  
  
    > [!NOTE]
    >  Les parties ajoutées sont de type **XmlDocument** afin que vous ne pouvez pas ajouter une partie de message mis en forme personnalisé à l’aide de la **AddPart()** (méthode).  
  
> [!NOTE]
>  Si un message à parties multiples contenant supérieur au nombre de parties déclarés est reçu, les lectures du moteur d’orchestration combien dénombre les parties contenues dans le message, construit ensuite les types de parties propres pour les parties qui correspondant au nombre de parties du message déclaré type et constructions **XmlDocument** parties pour les parties restantes.  
  
## <a name="see-also"></a>Voir aussi  
 **Méthode IBaseMessage.AddPart (COM)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
 [Ressources XSD sur le Web](../core/xsd-resources-on-the-web.md)   
 [À l’aide des champs distinctifs et les champs de propriété](../core/using-distinguished-fields-and-property-fields.md)   
 [Utilisation de messages passant par des orchestrations](../core/using-messages-in-orchestrations.md)