---
title: "Comprendre la sécurité WCF sur la carte créée avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1ee402b-ffda-42c1-8d85-d7cbe073a307
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf0c62c3d0c37c1f69cb944112ff832dade5ec4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-wcf-security-on-the-adapter-created-with-the-wcf-lob-adapter-sdk"></a>Comprendre la sécurité WCF sur la carte créée avec WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] étend la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal et s’appuie sur l’infrastructure de messagerie et de l’API qu’il fournit.  Un adaptateur WCF LOB ont besoin d’établir une connexion à des systèmes cibles, et par conséquent, il est nécessaire de configurer l’adaptateur avec l’authentification et d’autres informations de sécurité nécessaires pour établir les connexions du système cible.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]est une plateforme de programmation distribuée basée sur les messages SOAP qui peuvent transiter de différents nœuds, SOAP intermédiaires, les pare-feu et potentiellement en route de l’Internet à partir du système de métier à l’adaptateur et une session sur le client. Cela peut présenter un nombre de menaces de sécurité différent pour votre adaptateur et le scénario de déploiement.  
  
 Sécurité lit une partie importante de toute solution d’architecture enterprise. Vous pouvez tirer parti de la confidentialité, l’intégrité, l’authentification et les fonctionnalités d’autorisation fournies dans le modèle de sécurité WCF pour aider à sécuriser l’adaptateur contre les menaces de sécurité. Vous devez également envisager le transport et la sécurité au niveau du message entre l’adaptateur et le système cible pour protéger la communication entre ces deux entités. Bien que WCF fournit un riche ensemble de WS-*, spécifications de mise en œuvre de ces fonctions avancées de sécurité normes dans votre carte varient selon les fonctionnalités fournies par le système métier-.  
  
 Pour plus d’informations sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] sécurité, y compris une vue d’ensemble, les concepts, les scénarios courants et les meilleures pratiques, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)