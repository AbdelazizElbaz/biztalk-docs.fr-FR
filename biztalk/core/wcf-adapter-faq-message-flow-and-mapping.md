---
title: "FAQ sur les adaptateurs WCF : Flux de messages et mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 907e5c6a-a095-4b3a-9362-506832b6bc8c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58909b0d0cb0a126dd84e21809ca8e8f3941d758
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-message-flow-and-mapping"></a>FAQ sur les adaptateurs WCF : Flux de messages et mappage
## <a name="what-is-the-message-flow-within-the-wcf-and-biztalk-systems"></a>Qu'est-ce que le flux de messages dans les systèmes WCF et BizTalk ?  
 Voici une description du flux d'un message WCF entrant vers BizTalk Server :  
  
1.  Un message WCF arrive à un emplacement de réception et BizTalk Server instancie un service WCF hébergé.  
  
2.  Le service d'exécution WCF instancie la pile de canaux du service et ses écouteurs de canal. Une pile de canaux est une séquence d'étapes qui gèrent différentes tâches de traitement. Chaque pile de canaux est constituée d'au moins un canal de transport (le plus souvent, un encodeur de message) et éventuellement d'un ou plusieurs canaux de protocole. Le canal de transport lit le flux de messages entrant à l'arrivée. Il invoque un encodeur pour interpréter le message et générer un objet message WCF. À ce stade, chaque canal de protocole peut opérer sur le message WCF par ordre.  
  
3.  Le message WCF est reçu par un écouteur qui le transfère via la pile de canaux WCF configurée et le distribue à l'instance de service appropriée. Le message WCF est converti (mappé) en message BizTalk. Les en-têtes de message WCF sont écrits dans le contexte du message BizTalk, tandis que le corps du message WCF est écrit dans le corps du message BizTalk. Le mappage détermine quelle partie du message WCF devient le corps du message BizTalk : enveloppe, corps ou sous-élément.  
  
4.  Les composants de pipeline configurés dans l'emplacement de réception traitent le message BizTalk.  
  
5.  Le message BizTalk est stocké dans la base de données MessageBox.  
  
 Voici une description du flux d'un message WCF sortant de BizTalk Server :  
  
1.  Un message BizTalk est reçu par un port d'envoi conformément à son abonnement.  
  
2.  Les composants de pipeline configurés dans le port d'envoi traitent le message BizTalk.  
  
3.  Une pile de canaux WCF est instanciée et le message BizTalk est converti (mappé) en message WCF sur la base du contrat visible externe du service.  
  
4.  La pile de canaux WCF transmet le message WCF au service WCF externe.  
  
## <a name="how-is-a-wcf-message-converted-mapped-into-a-biztalk-message"></a>Comment un message WCF est-il converti (mappé) en message BizTalk ?  
 Pour comprendre le mappage, il convient d'examiner la structure d'un message WCF et d'un message BizTalk.  
  
 Un message WCF est basé sur la structure de message SOAP et constitué de propriétés, d'en-têtes et d'un corps de message.  
  
-   Le **propriétés du message** sont des objets Common Language Runtime (CLR) qui sont attachés à l’objet du Message. Elles sont internes à la pile WCF et à l'application de l'utilisateur à chaque extrémité de la communication. Elles ne sont jamais directement transférées entre le client et le serveur.  
  
-   **En-têtes de message**, cependant, peuvent être transférés entre client et serveur. Il peut y avoir plusieurs en-têtes dans un message, mais il n'y a qu'un seul corps de message. Contrairement aux en-têtes, le corps de message est transmis. Les en-têtes et le corps de message sont définis sous la forme d'un ensemble d'informations XML.  
  
-   Le **corps** message WCF est le contenu principal du message pour lequel les propriétés et en-têtes fournissent plus d’informations.  
  
 Un message BizTalk présente une structure différente.  
  
-   Chaque message inclut un ensemble unique de propriétés de contexte. Chaque propriété de contexte est constituée d'une paire de nom/valeur d'espace de noms. Les propriétés de contexte peuvent être promues ou écrites. Si elles sont promues, elles peuvent faire partie des règles de routage exécutées au sein de BizTalk Server.  
  
-   Les données d'un message dans BizTalk Server peuvent inclure plusieurs flux. Un message BizTalk est à parties multiples car chaque flux peut être lu indépendamment. L'une des parties du message est appelée corps.  
  
 La communication pouvant être bidirectionnelle, l'adaptateur WCF permet la configuration de la conversion ou du mappage particulier pour les sens entrant et sortant de l'échange du message. Cela concerne les emplacements de réception et les ports d'envoi dans BizTalk Server.  
  
 Les adaptateurs WCF BizTalk prennent en charge diverses permutations de la conversion lors de l'exécution entre ces deux structures de message. Mappage est contrôlé via la **Messages** onglet dans le **propriétés du Transport** boîte de dialogue pour un adaptateur WCF. Par exemple, la conversion la plus évidente (par défaut) est celle qui transforme le corps d'un message WCF entrant en corps du message BizTalk. Pour plus d’informations sur les modes de mappage, consultez [http://go.microsoft.com/fwlink/?LinkID=119792](http://go.microsoft.com/fwlink/?LinkID=119792).  
  
## <a name="how-can-you-preserve-the-complete-incoming-wcf-message-inside-the-biztalk-message"></a>Comment conserver le message WCF entrant complet au sein du message BizTalk ?  
 Une des options de corps de message BizTalk entrantes est la **enveloppe** option. Elle permet de placer le message SOAP contenu dans l'élément soap:Envelope dans le corps du message BizTalk entrant. Le message BizTalk qui en résulte contient les balises d'enveloppe, tous les en-têtes et le corps.  
  
## <a name="how-can-you-extract-specific-elements-of-the-incoming-wcf-message-into-a-biztalk-message-or-map-elements-of-an-outgoing-biztalk-message-to-an-outgoing-wcf-message"></a>Comment extraire des éléments spécifiques du message WCF entrant dans un message BizTalk ou mapper les éléments d'un message BizTalk sortant dans un message WCF sortant ?  
 Pour mapper une section d'un corps de message WCF ou BizTalk, utilisez l'option Chemin d'accès ou Modèle. Celles-ci permettent d'entrer une expression XPath pour extraire des parties spécifiques du corps du message. La syntaxe XPath complète n'est pas prise en charge dans ce cas car l'extraction est transmise par flux et le lecteur doit toujours avancer. C’est pourquoi, dans le **Messages** onglet, elle est appelée « Chemin – contenu localisé par le chemin du corps » au lieu de « XPath – contenu localisé par le chemin du corps ».  
  
 Au niveau de la réception, utilisez une expression de chemin spécifiant la lecture des données depuis le message WCF. Pour un message entrant, l'élément spécifique extrait par la déclaration de chemin est remplacé pour le contenu du message BizTalk. L'adaptateur utilise cette expression de chemin pour localiser et extraire les données souhaitées pour le message BizTalk.  
  
 Au niveau de l'envoi, utilisez un modèle pour créer un message WCF à partir du message BizTalk. L'option de modèle pour les messages sortants est conçue pour permettre l'opposé de l'option XPath. Dans la configuration d'adaptateur WCF, l'extrait de code XML est utilisé comme base de la structure du message sortant. Le contenu du message BizTalk est inséré lors de l'exécution dans cette structure.  
  
 Pour un message sortant, vous devez également choisir le type de l'élément écrit à l'aide du paramètre Codage de nœud (XML, Base64, Chaîne ou Hexadécimal). Cette option est très utile pour extraire un flux de données binaires contenu dans un message WCF. L'utilisation de cette fonctionnalité indique à l'adaptateur WCF d'utiliser les appels ReadContextAsBase64 sur le lecteur de corps du message WCF. Cet appel permet aux données binaires d'être lues directement via l'API XmlReader. Grâce à cette fonctionnalité, les données binaires peuvent être déplacées directement du transport WCF vers la base de données MessageBox de BizTalk. En écrivant un chemin d'accès au nœud contenant les données binaires, vous pouvez extraire et placer celles-ci dans le message BizTalk.  
  
## <a name="how-do-you-access-wcf-message-properties-within-an-incoming-wcf-message"></a>Comment accéder aux propriétés d'un message WCF entrant ?  
 Pour accéder aux propriétés d'un message WCF entrant avant qu'il ne soit transformé en message BizTalk, vous pouvez utiliser un composant de canal WCF personnalisé ou un point d'extensibilité de modèle de service avec un comportement WCF Par exemple, un **IDispatchMessageInspector** objet. Les adaptateurs BizTalk WCF-Custom et WCF-CustomIsolated offrent un moyen simple pour votre application à la puissance des comportements WCF à l’aide de la **comportement** onglet dans le **propriétés du Transport** boîte de dialogue Ces adaptateurs.  
  
 Pour que les propriétés d'un message WCF soient accessibles à l'adaptateur WCF, celles-ci doivent d'abord être écrites dans le corps ou l'en-tête du message sous forme de contenu. Les en-têtes sont copiés dans le contexte du message BizTalk automatiquement. Si vous souhaitez une valeur de propriété promue, vous pouvez utiliser un composant de pipeline BizTalk personnalisé pour promouvoir la propriété de message WCF dans le contexte de message BizTalk depuis le **IComponent : Execute** (méthode). L'utilisation des comportements WCF personnalisés avec les adaptateurs personnalisés WCF permet de tirer parti de l'extensibilité de WCF et de BizTalk pour accroître la puissance et la flexibilité de votre solution. L'adaptateur WCF permet de combiner l'extensibilité de BizTalk et de WCF pour résoudre votre problème.  
  
 Un raccourci est disponible dans l'adaptateur WCF pour ce cas de propriété commune. Plutôt que de tirer parti de l'extensibilité, vous pouvez simplement faire en sorte que l'extension WCF crée une propriété « connue » qui soit comprise par l'adaptateur WCF.  
  
 Pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk, le message WCF doit contenir un ensemble de paires de valeurs constituées de noms de propriété et d'espaces de noms. Cela permet aux adaptateurs WCF de reconnaître que les valeurs d'en-tête doivent être écrites ou promues.  
  
 Un adaptateur WCF attend les propriétés suivantes dans les messages WCF pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk :  
  
-   Pour promouvoir les valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** et la valeur **liste < KeyValuePair\<XmlQualifiedName, objet\>>**. À l’aide de cette paire, les adaptateurs extraient l’espace de noms, le nom et la valeur de la **XmlQualifiedName** de l’objet et les utilisent pour promouvoir les valeurs d’en-tête.  
  
-   Pour écrire, mais pas la promotion, les valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** et la valeur **Liste < KeyValuePair\<XmlQualifiedName, objet\>>.** À l'aide de cette paire, les adaptateurs WCF écrivent les valeurs dans le contexte du message.  
  
> [!NOTE]
>  Les propriétés promues doivent également être spécifiées dans le schéma de propriété BizTalk pour être acceptées par le moteur d'exécution BizTalk.  
  
## <a name="you-have-an-existing-orchestration-or-send-port-etc-that-expects-a-biztalk-multipart-message-how-can-you-get-a-multipart-message-in-the-wcf-scenario"></a>Une orchestration (ou un port d'envoi, etc.) attend un message à parties multiples BizTalk. Comment obtenir un message à parties multiples dans le scénario WCF ?  
 Un message à parties multiples BizTalk est constitué d'une ou plusieurs parties de message. Toutefois, un message à parties multiples est un concept étranger à WCF. Comme WCF n'utilise pas les messages à parties multiples, les adaptateurs WCF BizTalk ne les utilisent pas davantage. Cela pose problème si vous avez une orchestration ou un pipeline BizTalk écrit pour générer ou consommer des messages à parties multiples.  
  
 Si vous devez placer un message à parties multiples dans BizTalk Server à l'aide d'un message WCF entrant et des adaptateurs WCF, affichez vos données à parties multiples dans votre message WCF. Développez un composant de pipeline BizTalk personnalisé pour traiter le flux XML entrant (message WCF) et créer le message à parties multiples BizTalk approprié pour votre application. Ces étapes peuvent être effectuées dans l'ordre inverse au niveau de l'envoi le cas échéant.