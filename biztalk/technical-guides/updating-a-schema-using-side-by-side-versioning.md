---
title: "Mise à jour un schéma à l’aide du contrôle de version côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7360ec5-b5e9-40c7-9a7c-965fcc95ddb0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3d63b93f665e80f88e2d9e81b2337e7b198b3df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-a-schema-using-side-by-side-versioning"></a>Mise à jour un schéma à l’aide du contrôle de version côte à côte
Vous pouvez effectuer le contrôle de version côte à côte avec des schémas. Vous faire en ajoutant une nouvelle version du schéma à un assembly, la mise à niveau de la version du schéma, tout en laissant le schéma existant (et sa version) inchangée.  
  
 Si vous incrémentez une version de schéma, vous devez mettre à jour la référence au schéma pour les instances de pipeline et les composants de pipeline qui l’utilisent. Vous devez également mettre à jour les mappages qui font référence au schéma (ou créer de nouveaux mappages), ainsi que les orchestrations reposant sur le schéma.  
  
 Si vous annulez le déploiement d’un schéma, la version précédente du schéma, si elle est disponible, devient active.  
  
## <a name="schema-resolution-in-pipelines"></a>Résolution de schémas dans des Pipelines  
 Si vous ajoutez à une application un assembly qui inclut un nouveau schéma avec le même type de message en tant qu’un schéma existant dans le groupe BizTalk, le schéma avec le numéro de version plus récente sera utilisé lors de la résolution de schéma se produit dans les pipelines. Si un type de message fait référence à plusieurs types .NET, cette ambiguïté peut entraîner d’échec d’exécution du pipeline. En effet, la recherche de schémas utilise le type de message, l'espace de noms cible et le nom de la racine de l'instance. Ce type d’échec peut se produire pour les pipelines dans toute application qui utilise un schéma avec le même type de message que le nouveau schéma. Pour plus d’informations sur la résolution de schéma, consultez [résolution de schéma dans les composants de Pipeline](http://go.microsoft.com/fwlink/?LinkID=154207) (http://go.microsoft.com/fwlink/?LinkID=154207) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Le comportement de résolution de schéma pour le désassembleur XML peut nécessiter des modifications supplémentaires après l’ajout d’une nouvelle version d’un schéma côte à côte avec une version antérieure. Dans certains cas, vous voudrez coder en dur les références dans les propriétés du désassembleur de pipeline dans le Concepteur de Pipeline à des versions spécifiques des schémas. Cela vous permet d’éviter le comportement de résolution dynamique, dans lesquelles le désassembleur XML détermine quels schémas charger à l’aide du type de message dynamiquement détecté lors de l’exécution à partir du message contenu XML.  
  
## <a name="updating-a-schema-in-an-orchestration"></a>Mise à jour un schéma dans une Orchestration  
 Lorsque vous modifiez le schéma associé à envoyer plusieurs formes de réception dans une orchestration, vous pouvez apporter des modifications beaucoup plus facile en définissant la propriété de Type de Message pour le message associé à chaque envoi ou réception forme à parties multiples de Type de Message, au lieu de Schéma. Vous pouvez ensuite définir la propriété de Type pour la partie de message associée à chaque formes pour être le même schéma. Ce faisant, vous pouvez ensuite modifier le schéma en modifiant la propriété de Type pour chaque partie du message, au lieu de devoir modifier le Type de Message pour chaque forme. Pour plus d’informations sur les modifications plus facile par ce processus, consultez la [8 conseils et astuces pour une meilleure programmation de BizTalk](http://go.microsoft.com/fwlink/?LinkId=101594) le livre blanc (http://go.microsoft.com/fwlink/?LinkId=101594).  
  
## <a name="versioning-schemas"></a>Gestion des versions de schémas  
 BizTalk Server utilise un schéma à partir de la version la plus récente de l’assembly qui le contient. Cela signifie que si vous créez une nouvelle version d’un schéma, la nouvelle version remplace complètement toutes les versions précédentes du schéma. Cette opération est efficace lorsque les transactions sont de courte durée. Toutefois, les transactions dans la solution de gestion des processus d’entreprise sont de longue durées : une commande peut prendre jusqu'à une année à terminer.  
  
 Pour permettre l'emploi de plusieurs versions d'un schéma en cours d'utilisation, chaque schéma de la solution possède un numéro de version contenu dans son espace de noms. Pipelines BizTalk déterminent le type de message d’un message en fonction de l’espace de noms cible ainsi que le nom du nœud racine défini dans le schéma. Par exemple, l'espace de noms du schéma Order est le suivant :  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 Étant donné que l’espace de noms identifie le schéma et l’inscription de le permet de numéro de version de l’espace de noms unique pour le schéma, le nouveau schéma sera différent de la version antérieure. Ainsi, le nouveau schéma peut être utilisé sans remplacer l'ancienne version.  
  
 La modification de la version du schéma peut affecter les nombreuses parties de votre solution, donc cela doit être planifié à l’avance. Pour plus d’informations sur l’impact des modifications de version de schéma, consultez [résolution de schéma dans les composants de Pipeline](http://go.microsoft.com/fwlink/?LinkID=154207) (http://go.microsoft.com/fwlink/?LinkID=154207) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Lorsque vous modifiez la version des schémas dans une orchestration, utilisez les types de messages à parties multiples. Cette action entraîne une plus grande flexibilité lorsque les schémas de contrôle de version. Pour plus d’informations sur les avantages de l’utilisation de types de messages à parties multiples, consultez Conseil #1, « Toujours utiliser parties multiples Message Types » dans l’article MSDN Magazine [8 conseils et astuces pour une meilleure programmation BizTalk](http://go.microsoft.com/fwlink/?LinkId=101594) (http://go.microsoft.com /fwlink/ ? LinkId = 101594).  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md)