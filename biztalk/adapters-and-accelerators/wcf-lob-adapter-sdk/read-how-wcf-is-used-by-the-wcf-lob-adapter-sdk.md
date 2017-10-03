---
title: "Lisez comment WCF est utilisé par WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 183dd134-7273-4767-bad0-c42ae125985e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb84124213df8cf1bd401ab80db25586f5ca4534
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk"></a>Lisez comment WCF est utilisé par WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] étend la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal et varie selon le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] runtime pour fournir les services de messagerie base requis pour exposer les fonctionnalités de l’adaptateur et d’échanger des informations. 
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure pour l’écriture d’adaptateurs, les surfaces [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et les compléter avec des éléments de carte courants tels que les métadonnées et le regroupement de connexions. Il comprend également des outils de support pour améliorer l’expérience de telles que la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour les applications .NET et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications et le [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)].  
  
 Il incombe à le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] pour exposer des services à un large éventail d’utilisation des applications, pour gérer le flux de messages entre différents points de terminaison et pour fournir un kit de développement et des outils pour personnaliser, configurer et surveiller des flux de messages. Par exemple, un développeur peut personnaliser le comportement d’un [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en étendant son canal avec les gestionnaires de messages personnalisés.  
  
 La relation entre la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] est indiqué dans l’illustration d’architecture de haut niveau suivante.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/asdk-wcf.gif "ASDK_WCF")  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est construit sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] comme une extension de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal. Il fournit un modèle d’objet spécifique à un domaine et simplifiée et les outils pour la création d’adaptateurs comme personnalisé [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux. Adaptateurs construits à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sont signalées comme personnalisé [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons.  
  
 La figure suivante illustre l’échange de messages sortants à l’aide d’une liaison de carte donnée.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/58609452-d09e-4dbd-b470-c92a29977858.gif "58609452-d09e-4dbd-b470-c92a29977858")  
  
 La figure suivante illustre l’échange de messages entrants à l’aide d’une liaison de carte donnée.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/b62d5040-7e40-4edd-ac7b-69768131c51b.gif "b62d5040-7e40-4edd-ac7b-69768131c51b")  
  
 Pour plus d’informations sur la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal, consultez [vue d’ensemble du modèle de canal](https://msdn.microsoft.com/library/ms729840.aspx).  
  
## <a name="wcf-services-and-the-wcf-lob-adapter-sdk"></a>Les Services WCF et WCF LOB Adapter SDK  
 Lors du développement d’un type [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, la première étape consiste à créer le contrat pour le service qui est partagé avec le monde extérieur qui explique comment communiquer avec le service. Ce contrat spécifie essentiellement de la collection et la structure des messages requis pour accéder aux opérations offertes par le service.  
  
 Une fois que ce contrat est exposé en tant que service, le [Service Model Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx) peut être utilisé pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour l’utiliser. Le contrat fournit des informations sur un ensemble statique d’opérations et les messages qui ne doivent pas changer. 
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a410af83-ee3b-46d0-9afd-d32970f5ba0a.gif "a410af83-ee3b-46d0-9afd-d32970f5ba0a")  
  
 Par contre, les cartes intégrées à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournissent un ensemble dynamique de métadonnées sur la collection d’opérations et les données qui sont disponibles dans un système line-of-business. Le système métier-a souvent trop d’opérations à être décrites dans un contrat et peuvent avoir des opérations ajoutées pour répondre aux besoins de nouvelles.  
  
 Par exemple, un système métier-peut fournir compte des opérations de gestion. Après avoir identifié la nécessité de rationaliser la création de nouveaux comptes clients, la société met à jour le système métier-pour inclure la nouvelle opération. Un adaptateur créé à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] expose cette opération dans les métadonnées, il fournit aux clients.  
  
 Au moment du design, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]-carte génère des contrats dynamiquement en fonction des besoins du système line-of-business.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2f4d896a-14d9-43f4-8cdc-f816c5eab46d.gif "2f4d896a-14d9-43f4-8cdc-f816c5eab46d")  
  
 Fournit de l’ASDK [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils pour le consommateur de l’adaptateur générer des contrats dynamiques au moment du design.  
  
 Lors de l’exécution, lorsque le message transite dans l’adaptateur écrit à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], l’adaptateur doit souvent prendre une série d’actions sur le message de réception. Ces actions incluent :  
  
-   Recherche de métadonnées se rapportant au message  
  
-   Ouverture du message  
  
-   Interprétation du message  
  
-   Appeler les fonctions appropriées dans le système de métier  
  
 Dans le cas d’un [!INCLUDE[nextref_btsWinCommFoundation_md](../../includes/nextref-btswincommfoundation-md.md)] service, messages simplement passent sans être résolu via les métadonnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur BizTalk pour base de données Oracle et le Kit de développement logiciel de l’adaptateur LOB WCF](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)