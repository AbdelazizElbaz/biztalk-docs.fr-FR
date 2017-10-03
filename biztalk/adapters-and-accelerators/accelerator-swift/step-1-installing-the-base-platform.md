---
title: "Étape 1 : Installation de la plate-forme de Base | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- platforms
- installing, base platform
- base platform
ms.assetid: 27da386f-90c7-414f-a4e3-e909f0c18371
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b7551972c14de0bcbd36532d76e3706a762cf48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-installing-the-base-platform"></a>Étape 1 : Installation de la plate-forme de Base
Pour la plateforme de base, vous devez installer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] et [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] Service Pack 2 sur chaque serveur en utilisant les options d’installation par défaut. Suivez ces recommandations :  
  
## <a name="pre-installation"></a>Avant l’Installation  
  
-   Désactiver tous les logiciels antivirus lors de l’installation du logiciel. Certains logiciels antivirus peuvent empêcher les composants logiciels requis d’installer correctement.  
  
-   Assurez-vous que vous entrez les informations de licence appropriées (nombre maximal de connexions que vous avez achetées par serveur). Performances du système peuvent être affectées par le nombre de connexions disponibles.  
  
-   Assurez-vous que vous avez installé tous les logiciels requis pour un [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] installation. Pour plus d’informations, consultez les Instructions d’Installation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041). [Guide d’installation de BizTalk 2013 R2 Accelerator pour SWIFT](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1).  
  
-   Avant de les installer sur vos serveurs de production, testez toutes les mises à jour critiques dans un environnement hors connexion.  
  
-   Assurez-vous que vous installez tous les correctifs applicables pour tous les produits que vous installez dans le cadre de votre déploiement. Pour plus d’informations, consultez les sources suivantes :  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Aide en ligne  
  
    -   Instructions d’Installation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Site Web à l’adresse [http://go.microsoft.com/fwlink/?linkid=48685](http://go.microsoft.com/fwlink/?linkid=48685).  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Site Web du centre de téléchargement à [http://go.microsoft.com/fwlink/?linkid=48686](http://go.microsoft.com/fwlink/?linkid=48686).  
  
    -   [!INCLUDE[btsWinUpdate](../../includes/btswinupdate-md.md)]Site Web à l’adresse [http://go.microsoft.com/fwlink/?linkid=48687](http://go.microsoft.com/fwlink/?linkid=48687).  
  
-   Pour éviter les attaques de virus, installez la plateforme à partir d’un CD et déconnectez chaque serveur à partir d’Internet en débranchant les câbles et la désactivation de toutes les cartes réseau.  
  
-   Mettre en forme une nouvelle partition en utilisant le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] système de fichiers NTFS.  
  
## <a name="active-directory"></a>Active Directory  
  
-   Créez un utilisateur de domaine appelé **Admin** et l’ajouter à la variable locale **administrateurs** groupe sur tous les ordinateurs de votre déploiement. Au moment de l’installation, ouvrez une session les serveurs de déploiement à l’aide de ce compte de domaine.  
  
-   Ne pas configurer toutes les cartes réseau ou joindre des domaines pour l’instant. Ce guide décrit comment configurer ces paramètres ultérieurement lorsque vous commencez le processus de déploiement.  
  
## <a name="internal-web-servers-mrsr-site"></a>Serveurs Web interne (site MRSR)  
  
-   Assurez-vous que les Internet Information Services (IIS) est installé uniquement sur le serveurs de site MRSR.  
  
-   Assurez-vous qu’Internet Information Services (IIS) n’est pas installé sur l’Internet Security and Acceleration (ISA) Server.  
  
-   Assurez-vous que le service Message Queuing (MSMQ) est installé uniquement sur le serveurs de site MRSR. Si les serveurs de messagerie BizTalk seront également être utilisés en tant que les serveurs de site MRSR, n’installez pas MSMQ sur ces serveurs.