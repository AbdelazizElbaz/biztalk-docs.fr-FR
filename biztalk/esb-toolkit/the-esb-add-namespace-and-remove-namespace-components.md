---
title: "L’architecture ESB ajouter Namespace et supprimer des composants de Namespace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21df1b21-b73c-4e31-a234-49a1a6b53cc7
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bcbe519cfd8c6796569da4de87f59fa6a16d8a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-add-namespace-and-remove-namespace-components"></a>L’architecture ESB ajouter Namespace et supprimer des composants de Namespace
De nombreuses sociétés étaient premiers de technologies XML au moment normes ont toujours émergentes et partage de documents a été rare. Par conséquent, ils n’appliquent pas strictement la configuration requise pour inclure des espaces de noms racine unique, qui est généralement le cas aujourd'hui.  
  
 Toutefois, Microsoft BizTalk Server effectue d’identification de document basée sur une combinaison de l’espace de noms du nœud racine et le nom du nœud racine, afin que les documents ne dotés d’aucun espace de noms pour le nœud racine sont difficiles à identifier si plusieurs autre document types utilisent le même nom de nœud racine.  
  
 Les composants Namespace d’ajouter et supprimer les Namespace résolvent ce problème en rendant possible d’ajouter des espaces de noms aux documents lorsqu’ils sont reçus et pour supprimer l’espace de noms à partir des documents avant qu’ils soient remis. Par conséquent, les documents peuvent résider dans l’espace de noms par défaut (ou dans un espace de noms commune à plusieurs types de document différent) quand ils sont envoyés et reçus, mais se trouvent dans un espace de noms racine unique temporaire au cours du traitement au sein d’ESB BizTalk.  
  
 Les composants sont également utiles lors de l’intégration des systèmes hérités qui utilisent une définition de Type de Document (DTD) au lieu d’une définition de schéma XML ou qui utilisent des analyseurs XML hérités qui ne peut pas créer des documents qui contiennent un espace de noms racine.  
  
## <a name="installation"></a>Installation  
 L’installation du noyau ESB installe automatiquement le **ajouter le Namespace** et **supprimer le Namespace** composants dans le dossier composants de Pipeline BizTalk Server.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Le composant d’ajouter le Namespace ajoute un espace de noms spécifié dans un document XML. Le composant peut ajouter uniquement un espace de noms à un document. À l’aide du composant d’ajouter le Namespace sur un document qui a déjà un espace de noms du nœud racine n’est pas un scénario pris en charge, car un espace de noms unique est tout ce qui est requis.  
  
 Les composants ne sont pas les espaces de noms et ne sont pas conservent à une des valeurs de l’espace de noms. Toutefois, le composant d’ajouter le Namespace compare l’espace de noms demandé dans l’espace de noms existant du message et retourne simplement le message d’origine au pipeline si elles correspondent.  
  
 Les développeurs incluent le composant Namespace d’ajouter dans un pipeline de réception ou d’un pipeline d’envoi et définissez les propriétés appropriées. La validation suivante est effectuée au moment de l’exécution :  
  
-   Le **XPaths** propriété ou le **NamespaceBase** propriété doit contenir une valeur.  
  
-   Le **séparateur** propriété peut contenir uniquement des caractères valides (telles que  **/**  ou  **\\** ) ou une chaîne vide.  
  
-   Le **NamespacePrefix** valeur de propriété ne peut pas être une des valeurs réservées (**ns0** à **ns6**) et doivent être alphanumériques.  
  
 Toute variation de ces règles entraîne le composant lève une exception au moment de l’exécution, de suspendre le message (marqué comme **suspendu : peut être repris**) et d’écrire une entrée de journal des événements Windows.  
  
 Le composant de supprimer le Namespace supprime tous les espaces de noms racine à partir d’un document XML. Le nombre d’espaces de noms que le composant peut supprimer d’un document unique est limité par la mémoire physique disponible pour contenir le nœud actuel au cours du traitement. Toutefois, le composant utilise le message de pipeline BizTalk Server 2009 standard des processus de diffusion en continu et charge uniquement le nœud actuel dans le document en mémoire au lieu de charger l’intégralité du document.  
  
 Le composant Namespace de supprimer également code à nouveau le document à l’encodage spécifié (**ascii, unicode/utf16,** ou **utf8**) et peuvent la supprimer la marque d’ordre d’octet (BOM) à partir du début du flux de données, si Obligatoire.  
  
## <a name="using-the-add-namespace-and-remove-namespace-components"></a>À l’aide de l’ajouter Namespace et supprimer des composants de Namespace  
 Les développeurs peuvent utiliser le composant de Namespace d’ajouter dans les circonstances suivantes :  
  
-   Le message entrant n’a aucun espace de noms racine.  
  
-   Le message entrant utilise des données de l’élément ou attribut pour décrire le type de message.  
  
-   Les données qui décrit le type de message sont cohérentes et disponible à l’aide de requêtes XPath.  
  
 Les composants Namespace d’ajouter et supprimer les Namespace peuvent résider dans n’importe quelle étape d’un pipeline de réception ou d’un pipeline d’envoi. Vous pouvez chaîner les instances du composant si nécessaire, comme si vous utilisez le composant de supprimer le Namespace suivi par le composant d’ajouter le Namespace pour modifier l’espace de noms racine d’un document.  
  
 Si vous disposez de plusieurs emplacements de réception qui nécessitent l’utilisation de ces composants, vous pouvez créer un pipeline unique et utiliser le serveur BizTalk « par l’instance » configuration des composants pour définir les propriétés du composant pour chaque instance de l’envoi ou de pipeline de réception. À l’aide de BizTalk Server 2009, vous pouvez définir des propriétés sur une base par instance pour les pipelines, ce qui signifie que vous pouvez réutiliser un pipeline unique entre plusieurs emplacements de réception et peut-être les propriétés du composant différent pour chaque instance. Il s’agit d’un paramètre d’exécution qui permet aux administrateurs d’effectuer la modification à l’aide de la Console Administration de BizTalk Server sans nécessiter de modifications à du code ou de redéploiement.  
  
## <a name="component-properties"></a>Propriétés du composant  
 Le composant d’ajouter le Namespace expose les cinq propriétés publiques :  
  
-   **NamespacePrefix**. Ceci est le préfixe de l’espace de noms, inséré entre le **xmlns :** partie et égal suivant signe (=). Pour éviter les conflits avec des préfixes d’espace de noms de BizTalk schéma standards, évitez d’utiliser les valeurs **ns0** via **ns9**.  
  
-   **NamespaceBase**. Voici la section statique de l’espace de noms fait précéder le résultat généré par les valeurs de la **séparateur** et **XPaths** propriétés.  
  
-   **ExtractionNodeXPath**. Il s’agit d’une instruction XPath qui se résout en un seul élément dans le document qui contient les valeurs d’élément ou d’attribut à utiliser pour les parties de l’espace de noms générés.  
  
-   **XPath**. Il s’agit d’une barre verticale (**&#124;** ) liste délimitée de requêtes XPath utilisées pour extraire les composants qui associent pour former l’espace de noms.  
  
-   **Séparateur**. Il s’agit de séparateur à utiliser entre les segments de l’espace de noms. La valeur la plus courante est une barre oblique ( **/**  ), mais elle peut être une chaîne vide, si nécessaire.  
  
> [!NOTE]
>  Tous les nœuds XML, tels que les noms d’élément et d’attribut, respectent la casse.  
  
 Le composant de supprimer le Namespace expose deux propriétés publiques :  
  
-   **Encodage**. Il s’agit le codage du message de sortie, une des valeurs suivantes : **ascii, unicode/utf16,** ou **utf8**.  
  
-   **RemoveByteOrderMark**. Il s’agit d’une propriété booléenne qui indique si le composant doit supprimer la marque d’ordre (généralement **0xEFBB, 0xBFFFFE,** ou **0xFEFF**) à partir du début du flux de document XML.  
  
 Pour obtenir un exemple d’utilisation de ces composants, consultez [installer et exécuter l’exemple de composant Namespace](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).