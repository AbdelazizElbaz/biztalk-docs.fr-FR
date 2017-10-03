---
title: "La gestion des hôtes BizTalk et les Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [hosts]
- hosts, managing
- managing [hosts], about managing hosts
ms.assetid: 7f329804-ca44-4799-8a5d-38b3146d8e5e
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e60981f69bc3ff71bdd8581659f9cdd20f87467
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-hosts-and-host-instances"></a>Gestion des hôtes et des instances d'hôte BizTalk
Un hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est un ensemble logique composé de zéro, d'un ou de plusieurs processus d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans lesquels  vous déployez des éléments tels que des gestionnaires d'adaptateur, des emplacements de réception (y compris des pipelines) et des orchestrations. Pour plus d’informations sur les ordinateurs hôtes, consultez [hôtes](../core/hosts.md).  
  
 Une instance d'hôte désigne le processus où s'effectuent le traitement, la réception et la transmission du message. Vous installez une instance d'hôte sur chaque serveur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour laquelle un ou plusieurs hôtes sont mappés vers ce serveur. Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).  
  
 Les hôtes présentent les caractéristiques suivantes :  
  
-   Les hôtes sont les conteneurs logiques des objets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Chaque serveur ne peut contenir qu'une seule instance d'un hôte spécifique.  
  
-   Vous pouvez mapper un hôte vers plusieurs serveurs.  
  
 Les instances d'hôte présentent les caractéristiques suivantes :  
  
-   Les instances d'hôte sont les conteneurs physiques des objets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Vous pouvez créer une instance d'hôte en mappant un serveur vers un hôte.  
  
-   Plusieurs instances (d'hôtes différents) peuvent exister sur un serveur lorsque vous faites appel à l'équilibrage de charge ou au basculement.  
  
 L'illustration suivante représente la relation entre des serveurs, des hôtes et des instances d'hôte.  
  
 ![Hôtes, les instances d’hôte et les relations de serveur](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")  
Relation entre des hôtes, des instances d'hôte et des serveurs  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment créer un environnement d’hébergement de BizTalk Server](../core/how-to-create-a-biztalk-server-hosting-environment.md)  
  
-   [Comment créer un nouvel hôte](../core/how-to-create-a-new-host.md)  
  
-   [Comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md)  
  
-   [Comment supprimer un ordinateur hôte](../core/how-to-delete-a-host.md)  
  
-   [L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md)  
  
-   [Comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)  
  
-   [Comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)  
  
-   [Comment supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md)  
  
-   [Comment modifier les propriétés de l’Instance hôte](../core/how-to-modify-host-instance-properties.md)