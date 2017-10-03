---
title: Le traitement du Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing
- messages, pipelines
- routing, about routing
- adapters, about adapters
- routing, message types
- processing, messages
- messages, processing
- routing
- messages, routing
- pipelines, about pipelines
- message types
- messages, message types
- messages, adapters
ms.assetid: e6d1f969-20c9-41f6-85cb-46cf92656348
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 829fffc773bfc19100ad03448baf68b5846996f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-the-message"></a>Traitement du message
Tous les composants décrits jusqu'à présent jouent un rôle dans le traitement des messages lorsqu'ils passent dans BizTalk Server. Cette section fournit des détails supplémentaires sur l'interaction fonctionnelle de ces composants, et notamment, sur la réception d'un message. La figure suivante illustre la composition d'un port de réception et le flux d'un message dans le processus de réception.  
  
 Un *port de réception* se compose d'un ou de plusieurs emplacements de réception, et de plusieurs mappages, ou d'aucun. Les mappages sont des feuilles de styles XSLT (Extensible Stylesheet Language Transformations) qui servent à transformer les messages XML d'une structure ou d'un format dans un autre. Ils sont souvent utilisés dans le processus de réception pour normaliser les messages dans un format interne. Les emplacements de réception contrôlent les points de terminaison qui reçoivent les messages. Un emplacement de réception se compose de la configuration du point de terminaison d'un adaptateur de réception et d'un pipeline de réception.  
  
 ![Structure de port et le traitement de réception](../core/media/arch-message-processing.gif "arch_message_processing")  
  
## <a name="the-role-of-the-adapter"></a>Rôle de l'adaptateur  
 L'adaptateur de réception lance le processus de réception des messages en lisant un flux de données et en créant un message. Par exemple, l'adaptateur de fichier voit qu'un fichier a été placé dans son emplacement configuré et le lit dans un flux. L'adaptateur crée un message (une implémentation de l'interface Microsoft.BizTalk.Message.Interop.IBaseMessage), y ajoute une partie (une implémentation de l'interface Microsoft.BizTalk.Message.Interop.IBasePart) et fournit le flux de données en tant que contenu de la partie.  
  
 En outre, l'adaptateur écrit et procède à des promotions au sein des propriétés de contexte de message associées à l'emplacement, au type de l'adaptateur et aux autres éléments qui lui sont liés. Une fois le message et son contexte créés, l'adaptateur transmet le message au Gestionnaire des points de terminaison. Le message est ensuite traité via le pipeline de réception, lequel a été configuré pour l'emplacement de réception. Une fois que le message a été traité par le pipeline, un mappage peut être utilisé pour basculer le message dans le format désiré avant que le Gestionnaire des points de terminaison publie le message avec l'agent des messages.  
  
## <a name="the-role-of-the-pipeline"></a>Rôle du pipeline  
 Si l'adaptateur crée le message initial, la majeure partie du traitement appliqué à un message reçu se produit dans le pipeline de réception. Le traitement du pipeline porte sur le contenu et sur le contexte du message. Le contenu du message est généralement traité lors des étapes de décodage, de désassemblage et de validation, tandis que le contexte du message peut être géré à toutes les étapes. Un pipeline n'agit cependant pas nécessairement sur le contenu ou sur le contexte. Par exemple, le pipeline de transfert par défaut n'a aucun composant configuré et n'effectue aucun traitement sur le contenu ou le contexte du message. Pour des raisons de simplicité, ce document s'intéresse plus particulièrement aux composants de désassemblage dans la mesure où ils ont généralement le plus d'incidence sur le routage des messages.  
  
 Le travail du *désassembleur* est de traiter un message entrant provenant d'un adaptateur, de le désassembler en plusieurs messages, puis d'analyser les données des messages. Lorsqu'un message entrant comprend plusieurs petits messages, on parle d' *échange*. Le désassembleur de fichier plat et le désassembleur XML gèrent les échanges en permettant à un développeur de configurer les informations relatives au contenu d'habillage (autrement dit un schéma d'en-tête et de code de fin pour le désassembleur de fichier plat, et un schéma d'enveloppe pour le désassembleur XML) et le contenu de corps (potentiellement extensible). Par ailleurs, ces deux désassembleurs analysent le message d'origine dans le contenu XML. Un désassembleur personnalisé n'analyse pas nécessairement le contenu en XML si aucun autre traitement XML dans BizTalk Server n'est requis. Un exemple de scénario peut inclure une situation de routage simple dans laquelle les messages entrant dans le système à un emplacement de réception donné sont envoyés à un port d'envoi spécifique sans aucun mappage ni autre traitement XML.  
  
## <a name="routing-with-the-message-type"></a>Routage avec le type de message  
 L'une des propriétés de message les plus fréquemment utilisées dans le routage est le type du message. Lorsqu'un développeur crée un schéma pour définir la structure de messages, ce schéma définit le type de ces messages. Le type est déterminé par le nœud racine et l'espace de noms dans la définition de schéma. Par exemple, un document XML semblable au suivant aura le type de message http://tempuri.org/samples/MessageType#Message.  
  
```  
<Message xmlns=http://tempuri.org/samples/MessageType>  
<SomeOtherElement type="sample"/>  
</Message>  
```  
  
 Pour utiliser le type de message dans le routage, il doit être promu dans le contexte. Des désassembleurs sont utilisés pour promouvoir cette valeur dans le contexte de message et les composants du pipeline qui connaissent le mieux la structure du message. Les désassembleurs XML et de fichier plat promeuvent le type de message lorsqu'ils traitent les messages. Tout désassembleur personnalisé doit également promouvoir cette propriété pour garantir un routage approprié.  
  
 Il est important de noter qu'un message peut être dépourvu de type. Comme nous l'avons indiqué précédemment, les parties d'un message peuvent être constituées de toute donnée binaire et n'ont pas besoin d'un schéma définissant leur structure. Ce type de partie de message est généralement transmis à BizTalk Server sans que ce dernier effectue beaucoup de traitement. En revanche, les composants de pipeline personnalisé, les adaptateurs ou le code appelé à partir d'orchestrations peuvent interagir avec ces parties.  
  
 Les composants de pipeline, comme les adaptateurs, écrivent et promeuvent également les propriétés dans le contexte de message. En fait, les composants de pipeline constituent le mécanisme le plus couramment utilisé par la plupart des développeurs pour obtenir des propriétés dans le contexte de message. Les développeurs créent des schémas et peuvent promouvoir des propriétés dans le schéma. Ces informations sont stockées dans le schéma sous forme d'annotations qui peuvent ensuite être utilisées par les composants de pipeline. Tous les composants Désassembleur et Assembleur intégrés, Flatfile, XML et BizTalk Framework, utilisent le schéma de document pour extraire des informations sur les propriétés qui doivent être promues. En utilisant l'instruction de langage XML Path (XPath) des annotations, le désassembleur connaît l'emplacement des éléments à promouvoir dans le document. Au cours du processus de diffusion en continu dans le document, le désassembleur trouve les éléments correspondant à l'une des instructions XPath, et promeut ou écrit la valeur dans le contexte correspondant.  
  
 Des composants du pipeline personnalisé peuvent également être écrits pour gérer des propriétés d'obtention dans le contexte pour les données arbitraires d'un message reçu ou envoyé. Pour promouvoir une propriété dans le contexte et pour qu'elle soit utile au routage, ce qui est probablement la raison de la promotion de la valeur, un schéma de propriété comportant une définition de propriété doit être créé et déployé sur BizTalk Server. Avant de définir le schéma de propriété qui sera utilisé par des composants personnalisés, vous devez comprendre les différents types de propriétés promues. Les propriétés promues définies dans un schéma de propriété peuvent être de l'un des deux types de base suivants :  
  
-   [Microsoft.XLANGs.BaseTypes.MessageContextPropertyBase](http://msdn.microsoft.com/library/microsoft.xlangs.basetypes.messagecontextpropertybase.aspx) ou  
  
-   [Microsoft.XLANGs.BaseTypes.MessageDataPropertyBase](http://msdn.microsoft.com/library/microsoft.xlangs.basetypes.messagedatapropertybase.messagedatapropertybase.aspx)  
  
 Une propriété ayant le type de base MessageDataPropertyBase indique que la valeur de cette propriété provient du contenu du message. Il s'agit de la valeur par défaut des propriétés définies dans un schéma de propriété et la plus couramment utilisée. MessageContextPropertyBase indique une propriété qui doit faire partie du contexte de message, mais qui ne provient pas nécessairement directement des données de message. Les propriétés dont le type de base est MessageContextPropertyBase sont souvent promues par des adaptateurs et des désassembleurs, et incluent des propriétés communes comme le type de message et le type d'adaptateur.  
  
 Il est important de comprendre les différents types et de les utiliser correctement lors de la définition des propriétés. L'une des principales implications se produit en cas d'accès aux propriétés de contexte d'un message dans une orchestration. Si une propriété est identifiée comme un MessageDataPropertyBase, le Concepteur d'orchestration examine le schéma du message reçu et garantit qu'il définit une propriété promue correspondante. Si aucune propriété n'est trouvée dans le schéma lié à la propriété promue accédée, le Concepteur ne vous autorise pas à y accéder. D'un autre côté, si la propriété est définie en tant que MessageContextPropertyBase, le type de message importe peu et la propriété est accessible.  
  
 Dans les pipelines personnalisés, le mécanisme permettant de promouvoir ou d'écrire des propriétés est très similaire. Pour écrire des propriétés, vous utilisez un appel à la méthode IBaseMessageContext Write pour mettre la valeur dans le contexte. Pour les propriétés promues, vous utilisez la méthode IBaseMessageContext Promote à la place. Chacune de ces méthodes prend un nom de propriété, un espace de noms et une valeur. Pour les propriétés promues, le nom et l'espace de noms sont ceux de la propriété définie dans le schéma de propriété. Elles sont pour la plupart facilement accessibles en référençant l'assembly du schéma de propriété et en utilisant les propriétés sur la classe créée pour la propriété. Les champs distinctifs utilisent un espace de noms commun, http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields. L'expression XPath utilisée pour extraire la valeur sert généralement de nom.  
  
 Le code suivant montre un exemple de promotion et d'écriture des propriétés dans le contexte. Notez que dans cet exemple un champ distinctif est écrit dans le contexte. Ceci n'est utile que pour les orchestrations dans lesquelles le schéma de message identifie le champ distinctif pour que le Concepteur d'orchestration connaisse l'existence de ce champ. Il peut être utile d'écrire des propriétés dans le contexte pour en permettre l'utilisation par d'autres composants de pipeline côté réception ou envoi.  
  
```  
//create an instance of the property to be promoted  
SOAP.MethodName methodName = new SOAP.MethodName();  
  
//call the promote method on the context using the property class for name   
//and namespace  
pInMsg.Context.Promote(methodName.Name.Name, methodName.Name.Namespace,   
"theSOAPMethodName");  
  
//write a distinguished field to the context  
pInMsg.Context.Write("theDistinguishedProperty",   
"http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields",   
"theDistinguishedValue");  
```  
  
 Gardez les points suivants à l'esprit lorsque vous écrivez ou promouvez des valeurs dans le contexte :  
  
-   L'écriture d'une valeur dans le contexte avec le même nom et espace de noms que ceux qui ont été précédemment utilisés pour promouvoir la propriété rend caduque la promotion de cette propriété. L'écriture remplace essentiellement la promotion.  
  
-   L'écriture d'une valeur null dans le contexte supprime cette valeur car les propriétés ayant cette valeur ne sont pas autorisées.  
  
-   Les propriétés promues sont limitées à 256 caractères alors que les propriétés écrites n'ont aucune limitation de longueur.  
  
 Les propriétés promues sont utilisées dans le routage des messages et sont limitées en taille pour des raisons d'efficacité des tâches de comparaison et de stockage. Si les propriétés écrites n'ont aucune limite de taille, l'utilisation de valeurs excessivement grandes dans le contexte a un impact sur les performances car ces valeurs doivent quand même être traitées et transmises avec le message.  
  
 Lorsqu'un message est prêt à être envoyé à partir de BizTalk Server, il subit un processus complémentaire dans le port d'envoi. Des mappages sont appliqués aux messages avant l'exécution du pipeline d'envoi, permettant ainsi à un message d'être converti dans le format d'une application cliente ou spécifique avant d'être traité par le pipeline et envoyé via l'adaptateur. Dans le pipeline d'envoi, au lieu d'être promues dans le contexte de message, les propriétés sont rétrogradées du contexte dans le message.  
  
 ![Port d’envoi et de processus du pipeline d’envoi](../core/media/arch-message-processing-2.gif "arch_message_processing-2")  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)   
 [Comment BizTalk Server traite les Messages volumineux](../core/how-biztalk-server-processes-large-messages.md)