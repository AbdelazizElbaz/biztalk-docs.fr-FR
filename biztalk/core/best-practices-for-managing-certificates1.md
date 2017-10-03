---
title: Meilleures pratiques pour la gestion Certificates1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, certificates
- certificates, security
- security, certificates
- certificates, best practices
- best practices, security
- security, best practices
ms.assetid: cd182df4-0fcd-409c-9221-89f92e069f07
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e72d87530e5d080bd98ed55c2d29ca9554430375
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-managing-certificates"></a>Méthodes conseillées pour la gestion des certificats
Cette section présente les meilleures pratiques relatives à la gestion des certificats dans votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Effectuer une analyse du modèle de votre environnement**  
  
     Réalisez une analyse du modèle des menaces de votre environnement pour déterminer si les certificats de signature ou de chiffrement permettent de réduire les menaces potentielles.  
  
-   **Créez un plan pour les certificats de clé publique avec les partenaires**  
  
     Créez une stratégie pour l'envoi et la réception des certificats de clé publique avec les partenaires. Si vous n'utilisez pas de certificats de signature pour la résolution du tiers, le certificat public peut être joint au message et il n'est pas nécessaire que votre système en inclue une copie.  
  
-   **Télécharger la liste de révocation de certificats à des intervalles définis**  
  
     Téléchargez la liste de révocation des certificats de votre autorité de certification à intervalles définis. Il est recommandé d'effectuer cette opération une fois par semaine. Les listes de révocation des certificats sont téléchargées automatiquement si une autorité de certification existe pour le domaine auquel les serveurs BizTalk sont joints.  
  
-   **Établissez des instructions avec des partenaires pour l’envoi de clés publiques**  
  
     Dans le contrat de niveau de service (SLA) passé avec vos partenaires, établissez des instructions pour l'envoi des clés publiques, afin qu'ils vous avertissent lorsque leurs certificats expirent ou sont révoqués.  
  
-   **Vérifier les certificats de signature**  
  
     Assurez-vous de contrôler la présence de certificats de signature dans la liste de révocation de certificats. Pour plus d’informations sur la façon de vérifier la signature des certificats, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
-   **Éviter les attaques de déni de service pour les signatures numériques**  
  
     Déterminez ce que vous voulez faire des messages lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas valider la signature numérique. Définition de la **authentification** propriété sur le port de réception permettra d’éviter les attaques de déni de service.  
  
    > [!NOTE]
    >  Le **authentification - supprimer les messages** et **authentification - conserver les messages** des indicateurs sur le port de réception nécessitent que le composant de pipeline Résolution du tiers est configuré correctement, et que les parties sont défini dans BizTalk Server. Pour plus d’informations sur la configuration du composant de pipeline Résolution du tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).  
  
-   **Créez des emplacements de réception pour les messages chiffrés et**  
  
     Si vous envisagez de recevoir des messages MIME chiffrés de la part de certains partenaires et des messages non chiffrés de la part d'autres partenaires, créez des emplacements de réception distincts dans les différents hôtes pour les messages chiffrés et non chiffrés. Lorsque vous n'attendez que les messages MIME chiffrés, configurez le **autoriser les messages non-MIME** option dans le composant de pipeline MIME/SMIME décoder à **non**.  
  
-   **Gérer les certificats avec des partenaires**  
  
     Utilisez la gestion des certificats dans le cadre de vos méthodes de gestion des partenaires. Lorsque vous ajoutez ou supprimez un tiers de l'environnement BizTalk Server, il est recommandé d'ajouter ou de supprimer le certificat associé à ce tiers.  
  
-   **Supprimer les certificats avant de supprimer une instance d’hôte**  
  
     Avant de supprimer une instance d'hôte de BizTalk Server, supprimez les certificats dans le magasin personnel du compte sous lequel l'instance de l'hôte est exécutée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)   
 [Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)