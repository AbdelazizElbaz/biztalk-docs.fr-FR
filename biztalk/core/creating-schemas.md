---
title: "Création de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20b88194-b400-4ebc-8882-d493fbf30e0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac019276923467fe2d95f5a0a0b4a7b53513e9c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-schemas"></a>Création de schémas
Vous pouvez utiliser l’Éditeur BizTalk pour créer deux types de schémas : les schémas et les schémas de propriété de message.  
  
> [!NOTE]
>  Il existe plusieurs types de schémas de message, dont les schémas de message XML, les schémas de message de fichier plat et les schémas d'enveloppe.  
  
 Les schémas de message définissent la structure et limitent le contenu des messages que vous pensez envoyer à vos partenaires commerciaux ou applications, ou recevoir de ces derniers. Schémas de message sont les plus courants de schémas que vous utiliserez avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]créer des schémas de message XML pour les documents d’entreprise et les enveloppes utilisées pour les contenir et via l’utilisation de l’Extension de fichier plat à l’Éditeur BizTalk, il peut créer des schémas de message de fichier plat, y compris des schémas pour les en-têtes, corps et codes de fin.  
  
 Les schémas de propriété sont un type de schéma particulier. Les schémas de propriété fournissent un modèle de validation pour les données de champ et/ou d'enregistrement promues depuis un message d'instance vers ce que l’on appelle le contexte de message. L'objectif des schémas de propriété est de fournir une définition formelle, fortement typée des données à promouvoir pendant l’exécution.  
  
 La promotion de propriété fournit un mécanisme centralisé pour l'extraction d'éléments d'information clés, que vous définissez, à partir d'un message d'instance et pour les rendre plus accessibles aux composants BizTalk Server qui gèrent le message lors de sa transmission via BizTalk Server. La mise en correspondance d’une instance de message avec un abonnement constitue une utilisation courante des propriétés promues, permettant au message d’être correctement acheminé pour être traité.  
  
 Cette section décrit les méthodes selon lesquelles vous pouvez créer différents types de schémas dans BizTalk Server et présente les sujets connexes qui appartiennent à plusieurs types de schémas.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)  
  
-   [Gestion des nœuds dans un schéma](../core/managing-the-nodes-within-a-schema.md)  
  
-   [Promotion des propriétés](../core/promoting-properties.md)