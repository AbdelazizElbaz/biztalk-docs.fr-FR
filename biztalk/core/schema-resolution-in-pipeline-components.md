---
title: "Résolution de schéma dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, schema resolution
- pipeline components, schema resolution
- schemas, pipeline components
ms.assetid: 35a79a6f-788b-4ca1-8483-36dcba5ae580
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 897c25ecb64a3038a6992b9c4caf927ba3e2d805
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="schema-resolution-in-pipeline-components"></a>Résolution de schéma dans les composants de Pipeline
Les composants de pipeline Désassembleur et Assembleur utilisent des schémas XSD pour traiter les messages. Les schémas contiennent des informations telles que la liste des propriétés promues, des champs distinctifs, des annotations pour les messages de fichier plat et des annotations pour les enveloppes XML.  
  
 Les composants Désassembleur et Assembleur standard prennent en charge la récupération des schémas déployés en utilisant le nom du type de schéma et le type de message. Certains composants procèdent à la récupération en utilisant à la fois le nom du type de schéma et le type de message, tandis que d'autres (par exemple, le Désassembleur de fichier plat) n’utilisent que le type de schéma.  
  
 Les composants de pipeline qui reçoivent des messages XML déterminent le type de message en examinant l'élément racine du message et l'espace de noms. Par exemple, le type du message XML suivant est « http://MyDocument.org#MyDocument ».  
  
```  
<ns0:MyDocument xmlns:ns0="http://MyDocument.org">  
  
</ns0:MyDocument>  
```  
  
 Si un schéma n’a pas un espace de noms défini pour ce dernier, le type de message est «\<**rootNode**\>». Par exemple, si l’exemple XML précédent n’était associé à aucun espace de noms, le type de message serait « MyDocument ».  
  
 Les composants de pipeline standard utilisent le type de message pour récupérer le schéma approprié de la base de données. Les pipelines de réception et d'envoi XML par défaut déterminent toujours quels schémas charger à l'aide du type de message dynamiquement détecté au moment de l'exécution à partir du contenu XML du message (sauf si le composant de pipeline a été configuré de façon à accepter les messages non reconnus). Le désassembleur XML peut supprimer l’enveloppe du message en utilisant ce mécanisme ; toutefois, l'assembleur XML ne peut pas créer d’enveloppe pour un message sortant sans connaître le schéma d’enveloppe à utiliser.  
  
 Vous spécifiez le schéma d’enveloppe dans les propriétés de configuration de l’Assembleur XML au sein du Concepteur de pipeline.  
  
## <a name="how-schemas-are-resolved"></a>Résolution des schémas  
 En supposant que vous ne spécifiez pas le schéma directement dans le Désassembleur XML, les schémas sont résolus de la manière suivante :  
  
1.  Une recherche non qualifiée est d'abord effectuée sur les schémas déployés à l'aide du nom du nœud racine et de l'espace de noms (par exemple, http://MonEspaceDeNoms#MaRacine). Si une correspondance unique est trouvée, le schéma est résolu. Si plusieurs correspondances sont trouvées et diffèrent uniquement par leur numéro de version et qu'une seule soit active, cette version est utilisée et le schéma est résolu. Si le même schéma est actif dans plusieurs applications, plusieurs schémas actifs sont trouvés et la recherche continue à l'étape 2 ci-dessous.  
  
2.  S’il existe plusieurs correspondances qui l’étape 1 ne peut pas résoudre, la recherche est qualifiée par l’assembly que ne s’exécute dans le pipeline. Si un schéma unique est trouvé dans le même assembly ne s’exécute dans le pipeline, puis le schéma est résolu.  
  
3.  S'il n'y a toujours aucune correspondance, l'éditeur est utilisé pour résoudre le schéma. La recherche est affinée par l'utilisation du nœud racine, de l'espace de noms et du jeton de clé publique. Si un schéma unique est trouvé à l'aide de cette recherche, le schéma est résolu.  
  
4.  Le schéma ne peut être résolu. Un message d'erreur indiquant qu'aucun schéma unique n'a été trouvée est renvoyé.  
  
 Pour d’autres considérations, y compris l’effet du classement SQL Server et de respect de la casse sur la résolution de schéma, consultez [Namespace gestion](../core/namespace-management.md).  
  
 Pour créer une enveloppe dans l’Assembleur XML ou un en-tête et un code de fin dans l’Assembleur de fichier plat, vous pouvez effectuer l'une des opérations suivantes :  
  
-   Créez un pipeline d'envoi personnalisé et spécifiez le schéma d’enveloppe dans les propriétés de configuration de l’Assembleur XML. Ces opérations sont effectuées au sein même du Concepteur de pipeline.  
  
-   Dans la console Administration de BizTalk Server, spécifiez XMLTransmit comme propriété de pipeline d’envoi sur un port d’envoi. Cliquez sur les points de suspension pour configurer les propriétés de pipeline et spécifiez le schéma pour l'enveloppe dans la propriété EnvelopeDocSpecNames.  
  
 La résolution de schéma par type de message peut ne pas fonctionner si plusieurs versions d’un même schéma sont intentionnellement ou accidentellement déployées dans la base de données (par exemple dans un déploiement côte à côte ou si plusieurs scénarios n'ont pas de type de message unique). Si la résolution de schéma par type de message échoue, une erreur « d’ambiguïté de schéma » est ajoutée au journal des événements. Pour garantir le succès d’une résolution de schéma par type de message, effectuez l'une des procédures suivantes :  
  
-   Définissez les schémas dans le même projet BizTalk que votre pipeline personnalisé.  
  
-   Signez l’assembly avec des schémas possédant la même clé que l'assembly contenant les pipelines.  
  
-   Spécifiez explicitement les schémas dans les composants de pipeline (les noms de type de message doivent être uniques dans toute la base de données de gestion BizTalk).  
  
> [!IMPORTANT]
>  Lorsque les schémas d’un même assembly partagent un type de message, vous ne devez pas les inclure dans le même assembly de composant de pipeline en raison des limitations liées à la résolution des ambiguïtés ; créez plutôt une référence à ces schémas externes. La résolution des ambiguïtés ne fonctionne pas lorsque les schémas et les composants de pipeline se trouvent dans le même assembly, même si les noms de type de schéma sont explicitement spécifiés dans les composants de pipeline dans les pipelines personnalisés.  
  
> [!NOTE]
>  Composants de pipeline personnalisés qui utilisent **IPipelineContext** pour obtenir les schémas déployés doit-elle obtenir les schémas par type de schéma uniquement si le nom de type de schéma n’est pas spécifié pour le composant en cours d’exécution et obtenir des schémas par type de message uniquement Si les informations de type de schéma ne sont pas disponibles lorsque le composant est exécuté.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de pipeline](../core/pipeline-components.md)