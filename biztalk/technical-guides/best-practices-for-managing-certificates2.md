---
title: Meilleures pratiques pour la gestion Certificates2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71fa00cc-2e0c-46b3-ae62-f130a5b5f4f5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb6550a5e7b3604d4bb99507299cce5262e210e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="best-practices-for-managing-certificates"></a>Méthodes conseillées pour la gestion des certificats
Cette section fournit les meilleures pratiques pour la gestion des certificats dans votre environnement Microsoft BizTalk Server.  
  
## <a name="assess-and-plan-your-use-of-certificates"></a>Évaluer et planifier l’utilisation de certificats  
 **Effectuer une analyse du modèle de votre environnement**  
  
-   Réalisez une analyse du modèle des menaces de votre environnement pour déterminer si les certificats de signature ou de chiffrement permettent de réduire les menaces potentielles.  
  
 **Créez un plan pour les certificats de clé publique avec les partenaires**  
  
-   Créer un plan pour envoyer des certificats de clé publique à et recevoir des certificats de clé publique provenant de partenaires. Si vous n'utilisez pas de certificats de signature pour la résolution du tiers, le certificat public peut être joint au message et il n'est pas nécessaire que votre système en inclue une copie.  
  
 **Établissez des instructions avec des partenaires pour l’envoi de clés publiques**  
  
-   Dans le contrat de niveau de service (SLA) passé avec vos partenaires, établissez des instructions pour l'envoi des clés publiques, afin qu'ils vous avertissent lorsque leurs certificats expirent ou sont révoqués.  
  
## <a name="install-certificates"></a>Installer des certificats  
 **Télécharger la liste de révocation de certificats à des intervalles définis**  
  
-   Téléchargez la liste de révocation des certificats de votre autorité de certification à intervalles définis. Il est recommandé d'effectuer cette opération une fois par semaine. Les listes de révocation des certificats sont téléchargées automatiquement si une autorité de certification existe pour le domaine auquel les serveurs BizTalk sont joints.  
  
 **Vérifier les certificats de signature**  
  
-   Assurez-vous de contrôler la présence de certificats de signature dans la liste de révocation de certificats. Pour plus d’informations sur la façon de vérifier la signature des certificats, consultez [comment configurer le composant de Pipeline décodeur MIME/SMIME](http://go.microsoft.com/fwlink/?LinkId=155145) (http://go.microsoft.com/fwlink/?LinkId=155145) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 **Gérer les certificats avec des partenaires**  
  
-   Utilisez la gestion des certificats dans le cadre de vos méthodes de gestion des partenaires. Lorsque vous ajoutez ou supprimez un tiers de l'environnement BizTalk Server, il est recommandé d'ajouter ou de supprimer le certificat associé à ce tiers.  
  
 **Supprimer les certificats avant de supprimer une instance d’hôte**  
  
-   Avant de supprimer une instance d'hôte de BizTalk Server, supprimez les certificats dans le magasin personnel du compte sous lequel l'instance de l'hôte est exécutée.  
  
## <a name="configure-biztalk-server-to-use-certificates-for-mimesmime"></a>Configurer BizTalk Server pour utiliser des certificats pour MIME/SMIME  
 **Éviter les attaques de déni de service pour les signatures numériques**  
  
-   Déterminez ce que vous voulez faire avec des messages lorsque BizTalk Server ne peut pas valider la signature numérique. Définition de la propriété de l’authentification sur le port de réception permettra d’éviter les attaques de déni de service.  
  
    > [!NOTE]  
    >  L’authentification - supprimer les messages et l’authentification - conserver les messages des indicateurs sur le port de réception nécessitent que le composant de pipeline Résolution du tiers est configuré correctement et que les parties sont définis dans BizTalk Server. Pour plus d’informations, consultez [composant de Pipeline résolution tiers](http://go.microsoft.com/fwlink/?LinkId=155146) (http://go.microsoft.com/fwlink/?LinkId=155146) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 **Créez des emplacements de réception pour les messages chiffrés et**  
  
-   Si vous envisagez de recevoir des messages MIME chiffrés de la part de certains partenaires et des messages non chiffrés de la part d'autres partenaires, créez des emplacements de réception distincts dans les différents hôtes pour les messages chiffrés et non chiffrés. Lorsque vous n'attendez que les messages MIME chiffrés, configurez l’option Autoriser les messages non-MIME dans le composant de pipeline MIME/SMIME décoder sur non.  
  
## <a name="configure-a-biztalk-adapter-to-use-certificates"></a>Configuration d’un adaptateur BizTalk pour utiliser des certificats  
 **Testez votre connexion au site Web cible**  
  
-   Si vous utilisez SSL, vérifiez que vous pouvez vous connecter au site Web cible avec Microsoft Internet Explorer® avant d’essayer de se connecter au site Web cible avec les transports HTTP ou SOAP. Vérifiez qu’aucune boîte de dialogue n’est affichées dans Internet Explorer, lorsque vous vous connectez au site Web cible. BizTalk Server ne dispose d’aucun mécanisme permettant de s’interfacer avec les boîtes de dialogue peut s’afficher lors de la connexion au site web cible. Une boîte de dialogue peut être affichée par Internet Explorer si le nom du site Web cible ne correspond pas à celui spécifié pour le site Web dans le certificat SSL ou si l’autorité de Certification racine pour le certificat SSL n’est pas dans la Certification de racine de confiance approprié Magasin d’autorités.  
  
 **Utilisez l’outil de diagnostic SSL pour analyser les problèmes de connexion SSL**  
  
-   Cet outil est un composant en option de l'ensemble d'outils de diagnostic IIS. Vous pouvez télécharger les outils de diagnostic IIS depuis la [outils de diagnostic de Internet Information Services](http://go.microsoft.com/fwlink/?LinkID=64426) page (http://go.microsoft.com/fwlink/?LinkID=64426).  
  
## <a name="exporting-a-certificate-from-one-biztalk-group-to-another"></a>Exportation d’un certificat à partir d’un groupe de BizTalk à un autre  
 **Assurez-vous qu’un certificat importé est utilisé pour son usage prévu**  
  
-   Si vous importez un certificat dans un groupe, le certificat importé doit avoir une propriété d’utilisation qui est cohérente avec l’utilisation prévue. Pour vérifier la propriété d’utilisation, double-cliquez sur le certificat dans le **Console de gestion des certificats** de l’interface, puis cliquez sur le **détails** onglet de la **certificat** boîte de dialogue. Puis cliquez sur le **tous les** est définie sur le **afficher** liste déroulante, puis cliquez sur pour sélectionner le **utilisation de la clé** et/ou **utilisation améliorée de la clé** champs Pour vérifier l’utilisation prévue. Si BizTalk Server tente d’utiliser un certificat pour que son rôle prévu, une erreur d’exécution se produira.