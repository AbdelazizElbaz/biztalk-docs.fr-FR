---
title: Le Message BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, properties
- messages, about messages
ms.assetid: 6048c191-b495-4fdc-b547-e3e322340a49
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4fd150a0b93cac10c4d1f79a526846629c62e67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-biztalk-server-message"></a>Messages BizTalk Server
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est un moteur central de traitement des messages. Pour comprendre les détails de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est important de comprendre ce que sont les messages et la façon dont ils sont représentés, stockés et traités par BizTalk Server. La manière dont BizTalk Server traite les messages vous sera plus claire une fois que vous aurez compris ce qu'est un message.  
  
 Dans BizTalk Server, chaque message est considéré comme comportant de zéro à plusieurs parties. Dans le cas des messages comportant au moins une partie, l'une de ces parties est identifiée comme le corps du message. Chaque partie se compose de blocs binaires de données qui peuvent représenter un document XML, un fichier plat, une classe .NET sérialisée ou tout autre flux binaire de données. Le corps du message sert à identifier le type du message pouvant être utilisé pour le routage.  
  
 Il est important de comprendre que dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tous les messages sont immuables. Cela signifie qu'une fois qu'un message est construit, il ne peut pas être modifié. Un message est considéré comme construit une fois qu'il a été placé dans la base de données MessageBox. Si des modifications sont apportées au  message, un nouveau message doit être créé. C'est ce dernier qui est utilisé par la suite. Ceci est particulièrement évident dans le Concepteur d'orchestration. Les règles de compilation vous obligent à respecter des consignes de création de messages strictes. Si vous ne lez appliquez pas, vous ne pouvez pas utiliser le message. En outre, les règles vous interdisent de modifier un message en dehors de son bloc de construction. Si vous modifiez un message, vous devez créer un bloc de construction qui crée un message du même type, copier le message d'origine dans le nouveau, puis apporter vos modifications dans le nouveau message avant de quitter le bloc de construction.  
  
## <a name="message-properties"></a>Propriétés du message  
 Outre les parties qui composent un message, chaque message dans le système a un jeu de propriétés en même temps que ce qui est appelé le *contexte de message*. Ces propriétés peuvent être des valeurs extraites du message lui-même ou associées à celui-ci. Par exemple, les adaptateurs placent des propriétés dans le contexte associé à la réception du message. Il peut s'agir entre autres de l'emplacement de réception du message et le type d'adaptateur utilisé pour recevoir le message. Propriétés peuvent être écrites dans le contexte, ou *promues* dans le contexte. La différence entre ces deux options est que les propriétés promues peuvent être utilisées en tant que critères dans le routage de messages alors que les propriétés écrites ne le peuvent pas.  
  
 Ce concept d'écriture ou de promotion des valeurs est quelque peu semblable au concept de promotion des propriétés dans l'Éditeur BizTalk. Dans ce dernier, un élément ou un attribut d'un schéma peut être marqué comme propriété promue ou champ distinctif. Les éléments marqués avec les annotations PropertyField dans votre schéma de message entraînent le placement d'une propriété promue dans le contexte par le désassembleur de pipeline. Les éléments marqués avec les annotations DistinguishedField dans votre schéma de message entraînent le placement d'une propriété écrite dans le contexte par le désassembleur de pipeline.  
  
 La conception pour les propriétés promues en main de la conception de *corrélation des messages*: la capacité de lier un message reçu à une instance d’orchestration en cours d’exécution. Dans le cas de la corrélation, il n'est pas nécessaire de définir une propriété ou un ensemble de propriétés qui fait la liaison entre les messages de l'orchestration. Par exemple, dans un processus d'achat, vous devez mettre en corrélation des messages en fonction de l'ID de bon de commande (PurchaseOrderID). Cependant, dans de nombreux cas, le nom du champ ou de l'attribut figurant dans les messages ne correspond pas. Un schéma de bon de commande peut comporter un élément nommé POId, alors qu'un schéma de facture peut comporter un élément nommé OrderID. Dans cette situation, le développeur doit pouvoir abstraire de la source d'une valeur le nom de la propriété à corréler pour corréler des messages en fonction d'une propriété nommée, telle que PurchaseOrderID. Les schémas de propriété prennent en charge cette abstraction.  
  
 A *schéma de propriété* vous permet de définir les propriétés promues dans un emplacement commun et demandez-lui de référencés par d’autres schémas. À l'instar d'autres schémas, un schéma de propriété comporte un espace de noms. Cependant, contrairement aux autres, il ne peut comporter que des éléments définis (à savoir des éléments qui ne sont ni des enregistrements ni des attributs). Chaque élément défini dans le schéma de propriété possède un nom et un type. Comme il est possible que le schéma de propriété doive être référencé par plusieurs schémas et comme les informations contenues dans le schéma de propriété doivent être disponibles pour les composants lors de l'exécution, le schéma de propriété doit être déployé sur BizTalk Server, comme c'est le cas de tous les autres schémas. Outre les étapes de déploiement de schéma habituelles, les informations relatives aux propriétés promues sont extraites et stockées dans la table bts_documentSpec de la base de données de gestion.  
  
 Après avoir créé un schéma de propriété, les éléments et les attributs avec le même type (par exemple, entier) peut être promu en tant qu’une des propriétés nommées dans le schéma de propriété.  
  
 **Pour exécuter l’exemple de cas ci-dessus, un développeur effectue les étapes suivantes pour définir la propriété partagée nécessaire pour la corrélation.**  
  
1.  Créer un schéma de propriété et définir un élément de type xs:int nommé PurchaseOrderId.  
  
2.  Créer un schéma PurchaseOrder et ajouter un élément ou un attribut de type xs:int nommé POId.  
  
3.  À l'aide de la commande Afficher les promotions dans l'Éditeur BizTalk, le développeur ajoute le champ POId à la liste des propriétés promues et indique qu'il doit être promu en tant que propriété PurchaseOrderId définie dans le schéma de propriété en sélectionnant la propriété nommée PurchaseOrderId dans la liste.  
  
4.  Créer un schéma Invoice et ajouter un élément ou un attribut de type xs:int nommé OrderId.  
  
5.  À l'aide de la commande Afficher les promotions dans l'Éditeur BizTalk, le développeur ajoute le champ OrderId à la liste des propriétés promues et indique qu'elle doit être promue en tant que propriété PurchaseOrderId définie dans le schéma de propriété en sélectionnant la propriété nommée PurchaseOrderId dans la liste.  
  
 Cette définition existant désormais dans les schémas de document, les composants de pipeline sont en mesure de promouvoir en tant que propriété nommée OrderId et POId afin qu'elles puissent être utilisées pour le routage et la corrélation. Pour plus de détails sur ce processus de promotion, voir la rubrique « Traitement des messages » dans ce document.  
  
 Un des avantages que présentent les propriétés promues est que la valeur de l'élément promu est disponible dans le contexte du message. Cela signifie que l'extraction de cette valeur est peu coûteuse, car le message n'a pas à être chargé en mémoire pour qu'il fasse l'objet d'une instruction XPath. En effet, l'instruction s'effectue par le biais d'un simple jeu de propriétés et d'une clé. Ce type de comportement est souhaitable dans des situations autres que le routage des messages et motive la création de champs distinctifs. Lorsque des propriétés sont promues dans le contexte d'un message, des champs distinctifs sont écrits dans le contexte du message. Cependant, contrairement aux propriétés promues, il n'existe pas de schéma de propriété pour les champs distinctifs. C'est pour cette raison que les champs distinctifs ne peuvent pas être utilisés pour le routage et, de ce fait, ne sont pas disponibles en tant que critères de filtre dans un port d'envoi ou une forme Réception d'une orchestration. En revanche, les champs distinctifs peuvent être utilisés dans des orchestrations pour lire ou écrire des valeurs provenant du contexte de message plutôt que charger le message en mémoire et y extraire la valeur.  
  
 Les prédicats peuvent non seulement servir à promouvoir ou à écrire des propriétés dans le contexte de message, ils peuvent aussi être ajoutés au contexte. Des prédicats de message sont utilisés comme mesure de sécurité dans BizTalk Server. Ils fournissent les informations contextuelles relatives au message. Ces informations doivent correspondre aux valeurs spécifiées pour tout hôte vers lequel le message doit être acheminé. Cette mesure de sécurité vous permet de configurer votre environnement BizTalk Server de sorte à autoriser des hôtes spécifiques pour qu'ils soient les seuls en mesure de recevoir et de traiter des messages donnés. Par exemple, dans la console Administration de BizTalk Server, vous pouvez activer l'empreinte d'un certificat sur un hôte pour que celui-ci puisse chiffrer et déchiffrer des messages. La configuration de cette propriété crée une propriété d'application pour l'hôte dans la base de données MessageBox. Les messages sécurisés reçus et déchiffrés avec cette empreinte sont ensuite acheminés uniquement vers les hôtes sur lesquels l'empreinte est configurée.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)