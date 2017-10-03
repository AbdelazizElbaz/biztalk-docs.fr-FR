---
title: "À l’aide de liens de rôle dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role links
- roles, links
- roles
- roles, about roles
- role links, about role links
- role links, properties
- role links, initializing
ms.assetid: 0cf85544-12c9-4541-8925-61a6e946cce0
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e3c4e4a4c3a99fb6e1962299d440717eaa8d51b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-role-links-in-orchestrations"></a>Utilisation des liens de rôle dans des orchestrations
Les liens de rôle correspondent à des abstractions pour les interactions entre votre orchestration et vos partenaires commerciaux. Les liens de rôle vous permettent de choisir dynamiquement avec quel partenaire commercial interagir, en fonction de la résolution du partenaire commercial, du contenu du message ou des résultats d'une recherche dans une base de données, tout en maintenant intact votre processus d'entreprise global.  
  
 Imaginons un scénario interentreprises dans lequel sont impliqués plusieurs acheteurs, un seul fournisseur et plusieurs agences d'expédition pour le fournisseur. Lorsqu'un acheteur envoie une bon de commande au fournisseur, celui-ci sait, grâce à la résolution de tiers, quel acheteur lui envoie le bon de commande, et lui applique la remise appropriée. De plus, en fonction des marchandises commandées, le fournisseur peut déterminer au moment de l'exécution quelle agence d'expédition se chargera de la livraison. Chaque agence d'expédition peut utiliser un protocole de transport qui lui est propre, cependant le fournisseur peut utiliser le même processus d'entreprise au moment de l'exécution pour gérer toutes les agences d'expédition et déterminer avec quelle agence interagir. Si une agence d'expédition met à jour son protocole de transport ultérieurement (de FTP à HTTP, par exemple), le fournisseur a seulement besoin d'utiliser l'Explorateur BizTalk ou la console Administration de BizTalk Server pour mettre à jour le porte d'envoi associé à cette agence d'expédition spécifique. Le fournisseur n'a pas besoin de modifier son processus d'entreprise, qui réside dans l'orchestration.  
  
## <a name="roles"></a>Rôles  
 Il existe deux rôles dans une orchestration :  
  
-   un rôle "implémentations" pour recevoir et traiter des messages (ce rôle est également connu sous le nom de fournisseur) ;  
  
-   un rôle "utilisations" pour envoyer des messages (ce rôle est également connu sous le nom de consommateur).  
  
## <a name="role-links"></a>Liens de rôle  
 Un lien de rôle peut inclure un rôle consommateur ou fournisseur, ou un de chaque. Le rôle consommateur utilise les services fournis par le rôle fournisseur. Lorsque vous définissez un lien de rôle avec l'un de ces rôles ou les deux, le rôle complémentaire est supposé être rempli par le partenaire avec lequel vous établissez un lien.  
  
 Un lien de rôle a un **SourceParty** propriété, un **DestinationParty** propriété et un rôle initiateur. Rôle initiateur est le rôle sur lequel la première communication se produit, et par conséquent, qui déclenche le lien de rôle en définissant la valeur de la **DestinationParty** propriété.  
  
 Si le rôle initiateur est un consommateur pour envoyer des messages, vous définissez explicitement la **DestinationParty** , propriété (une fois et une seule fois) dans votre orchestration. Pour ce faire, vous définissez la valeur de la **DestinationParty** dans les **Expression** forme, comme dans l’exemple suivant, où ConfirmOrder est le nom d’un lien de rôle et PartnerName et OrganizationName sont paramètres d’un tiers :  
  
```  
ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
```  
  
 Si le rôle initiateur est un fournisseur pour la réception des messages, le **DestinationParty** propriété est automatiquement initialisée par le récepteur. Le **DestinationParty** est défini sur le fournisseur lui-même. Le **SourceParty** propriété est en lecture seule et est fournie via un composant de pipeline approuvé pour résoudre le nom du tiers en fonction de l’identificateur de sécurité (SID) de l’expéditeur ou sur un certificat associé au tiers. L’hôte qui exécute le composant de pipeline doit être marquée comme **approuvé par authentification**. Vous pouvez obtenir la valeur de la **SourceParty** dans les **Expression** forme à l’aide de l’exemple de code suivant :  
  
 `PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);`  
  
## <a name="role-link-types"></a>Types de liens de rôle  
 Un lien de rôle est une instance d'un type de lien de rôle, composée d'un ou de deux rôles. Lorsque vous utilisez un type de lien de rôle, tenez compte des éléments suivants :  
  
-   Vous ne pouvez faire référence à un type de port donné qu’une seule fois au sein d'un type de lien de rôle unique.  
  
-   Dans la mesure où une définition de type de lien de rôle comprend des types de ports, l'étendue du type de port doit englober celle de tous les types de liens de rôle qui l'utilisent.  
  
-   Lorsque vous utilisez les services BAS (Business Activity Services), le schéma de paramètres structurés doit être défini dans le même assembly BizTalk assembly que le type de lien de rôle auquel il est associé. Dans la mesure où le schéma est associé au type de lien de rôle et non aux rôles individuels qui composent ce type de lien de rôle, si les tiers qui jouent les différents rôles partagent l'assembly contenant le type de lien de rôle, les deux tiers verront les mêmes schémas de paramètres structurés. Si les deux tiers utilisent le même type de lien de rôle mais doivent avoir des schémas de paramètres différents, un assembly distinct doit être créé pour chaque tiers. Le type de lien de rôle doit alors être dupliqué dans chaque assembly.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment créer des liens de rôle dans les Orchestrations](../core/how-to-create-role-links-in-orchestrations.md)  
  
-   [L’utilisation de la forme de lien de rôle](../core/how-to-use-the-role-link-shape.md)  
  
-   [Comment utiliser l’Assistant lien de rôle](../core/how-to-use-the-role-link-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline résolution du tiers](../core/how-to-configure-the-party-resolution-pipeline-component.md)   
 [L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md)