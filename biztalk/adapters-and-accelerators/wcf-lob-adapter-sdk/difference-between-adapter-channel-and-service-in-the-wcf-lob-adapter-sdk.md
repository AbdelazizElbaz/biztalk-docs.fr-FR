---
title: "Différence entre le canal de l’adaptateur et le service dans WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e377568887d3d626e288fc47f82714b189d44b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="difference-between-adapter-channel-and-service-in-the-wcf-lob-adapter-sdk"></a>Différence entre le canal de l’adaptateur et le service dans WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] chacun d’eux fournit un ensemble d’API qui peut être utilisé pour exposer les fonctionnalités d’application à l’utilisation des applications sur le même ordinateur ou sur un réseau. Pour choisir le framework plus approprié, vous devez prendre en compte les propriétés de l’application du système cible que vous exposez, ainsi que les exigences d’entreprise pour la fonctionnalité exposée. Cette rubrique fournit des instructions qui vous permet de choisir le framework approprié.  
  
## <a name="when-to-write-an-adapter"></a>Lorsque d’écrire un adaptateur  
 Envisagez d’écrire un adaptateur à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] lorsque :  
  
-   Le système cible est un existant, non -*Web services activés* système  
  
-   Le système cible est dynamique et peut être amélioré avec les nouvelles opérations  
  
-   Le système cible a une grande quantité de métadonnées  
  
-   Il existe un grand nombre divers d’utilisateurs pour les données du système cible  
  
-   Applications consommatrices ont besoin des fonctionnalités de découverte de métadonnées application riche  
  
 Par exemple, si le système cible contient des centaines d’opérations de gestion des demandes de remboursement de soins de santé et les opérations sont dynamiques (ce qui signifie que les utilisateurs peuvent ajouter de nouvelles opérations qui effectuent des tâches supplémentaires), il est judicieux d’exposer cette fonctionnalité à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Cela garantit que les nouvelles opérations sont détectables par les applications à l’aide de l’adaptateur. Avec [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], vous devrez modifier le contrat de service, car elle est statique.  
  
## <a name="when-to-write-a-service"></a>Quand un Service d’écriture  
 Utilisez le *modèle de Service WCF* pour créer un service lorsque :  
  
-   Le système cible est statique et a un ensemble fixe d’opérations  
  
-   Le système cible a peu ou pas de métadonnées  
  
-   Les développeurs de service ont connaissance de l’application doit être exposée  
  
-   Une nouvelle application est exposée.  
  
-   Vous créez des adaptateurs de transport générique  
  
 Par exemple, si le système cible contient 20 opérations pour la gestion des équipes sportives, vous pouvez exposer les opérations comme un contrat statique à l’aide de [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. En procédant ainsi, vous évitez d’implémenter les fonctionnalités de métadonnées inutiles et vous pouvez réduire potentiellement des temps de développement.  
  
## <a name="when-to-write-a-channel"></a>Lorsque d’écrire un canal  
 Utilisez le *modèle de canal WCF* pour créer un canal lorsque :  
  
-   Création d’un protocole de câble. Exemples de protocoles de transmission de protocole WS-ReliableMessaging.  
  
-   Envoyer/recevoir des messages WCF via un transport autre que ceux qui sont inclus dans WCF (TCP, HTTP, canaux nommés, MSMQ et PeerChannel). Par exemple, vous pouvez écrire un transport UDP, TIBCO ou un transport de messagerie Service JMS (Java).  
  
-   Intégration avec un système qui n’est pas exposé comme un service Web.  Dans ce cas, votre transport agit comme un adaptateur adaptation des messages WCF au format de message du système existant ou d’API, ce qui permet un client WCF pour communiquer directement avec le système existant. Ceci est le transport TCP amélioration des Services Web (WSE) 3.0.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [Comprendre le système métier avec le SDK de l’adaptateur WCF LOB](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)