---
title: "Résolution des problèmes Enterprise Single Sign-On | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb54af9f-a6ef-46c1-b987-2019cff3f837
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 450b2df7ec043dfd4bc775cfec7acdec0fb3ca1f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-enterprise-single-sign-on"></a>Résolution des problèmes Enterprise Single Sign-On
Cette rubrique fournit des informations sur les problèmes connus susceptibles de se produire lors de l'utilisation de l'authentification unique (SSO) de l'entreprise.  
  
 Quand vous commencerez à résoudre les problèmes liés à votre environnement SSO, il pourra être judicieux que vous passiez en revue les points du tableau suivant pour vous assurer que tous les composants fonctionnent correctement :  
  
|Question|Commentaires|  
|--------------|--------------|  
|Quelque chose dans le journal des événements de l'application se rapporte-t-il au système SSO ?|Les messages SSO du journal des événements peuvent vous aider à identifier le problème que pose le système SSO. La source des messages provenant du système SSO est ENTSSO. **Important :** la plupart des événements et erreurs de l’authentification unique s’affichent en tant qu’avertissements dans le journal des événements, pas comme des erreurs. Le système SSO génère un avertissement lorsque le problème touche un client unique du service SSO, et génère des erreurs lorsque l'ensemble du système SSO (tous les clients) est concerné.|  
|Le service SSO est-il correctement installé ?<br /><br /> Démarre-t-il normalement ?<br /><br /> Sous quel compte de service le service SSO est-il exécuté ?|Assurez-vous que le service SSO est correctement installé et que le compte de service est membre du groupe des administrateurs SSO.|  
|Où se trouve la base de données d'authentification unique ?|Utilisez la ligne de commande **ssoconfig -showdb**. Pour plus d’informations sur cette commande, consultez [comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md).|  
|Quel serveur SSO est utilisé ?|Utilisez la ligne de commande **ssomanage -showserver**. Pour plus d’informations sur cette commande, consultez [comment définir le serveur SSO](../core/how-to-set-the-sso-server.md).|  
|Qu'est-ce que le compte de l'administrateur SSO ?|Utilisez la ligne de commande **ssomanage –displaydb**. Pour plus d’informations sur cette commande, consultez [comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md).|  
|Est-ce que tout a bien été activé ?|Utilisez la ligne de commande **ssomanage –displaydb**. Pour plus d’informations sur cette commande, consultez [comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md).|  
|Les applications associées existent-elles ?|Utilisez la ligne de commande **ssomanage –listapps all**. Pour plus d’informations sur cette commande, consultez [comment répertorier les Applications associées](../core/how-to-list-affiliate-applications.md).|  
|L'application associée semble-t-elle correcte ?<br /><br /> Quels comptes utilisent cette application ?|Utilisez la ligne de commande **ssomanage-displayapp***\<nom de l’application\>*. Pour plus d’informations sur cette commande, consultez [comment répertorier les propriétés d’une Application associée](../core/how-to-list-the-properties-of-an-affiliate-application.md).|  
|Existe-t-il des mappages pour cette application associée ?|Utilisez la ligne de commande **ssomanage – listmappings***\<nom de l’application\>*. Pour plus d’informations sur cette commande, consultez [comment répertorier des mappages utilisateur](../core/how-to-list-user-mappings.md).|  
|Quels comptes sont membres des groupes SSO ?|Vérifiez l'appartenance aux groupes SSO de tous les comptes.|  
|L'application COM+ du serveur SSO s'exécute-t-elle correctement ?|Vérifiez le serveur SSO de l'application COM+. **Remarque :** vous pouvez également vérifier le journal des événements pour plus d’informations, telles que les événements et les messages d’avertissement.|  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="entsso-service-fails-to-start"></a>Le service ENTSSO ne démarre pas  
  
##### <a name="problem"></a>Problème  
 Le service ENTSSO ne démarre pas.  
  
##### <a name="cause"></a>Cause  
 Si le service ENTSSO n'est pas exécuté sous un compte d'administrateur SSO valide, il ne démarrera pas.  
  
##### <a name="resolution"></a>Résolution  
 Spécifiez un compte d'administrateur SSO valide pour le service ENTSSO et redémarrez ce dernier à partir du composant logiciel enfichable Gestionnaire de contrôle des services (SCM).  
  
#### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a>Échec du démarrage des services BizTalk dépendant du service de l'authentification unique de l'entreprise (ENTSSO) après un redémarrage.  
  
##### <a name="problem"></a>Problème  
 BTSSvc$BizTalkServerApplication possède une dépendance vis-à-vis du service de l'authentification unique de l'entreprise (ENTSSO) et risque d'expirer lors du démarrage ou après un redémarrage.  
  
##### <a name="cause"></a>Cause  
 Le service de l'authentification unique de l'entreprise prend approximativement 3 minutes pour démarrer.  
  
##### <a name="resolution"></a>Résolution  
 Configurez le service « Groupe BizTalk des services BizTalk : BizTalkServerApplication » avec l'option de type de démarrage Automatique (début différé). Le démarrage du service sera ainsi initié après la fin de l'exécution des routines de démarrage des services automatiques.  
  
#### <a name="cannot-access-an-affiliate-application"></a>Impossible d'accéder à une application associée  
  
##### <a name="problem"></a>Problème  
 Le service SSO de l'entreprise désactive une application associée si le compte d'administrateur d'application qui lui correspond n'est pas valide.  
  
##### <a name="cause"></a>Cause  
 Le compte d'administrateur de l'application SSO n'est pas valide.  
  
##### <a name="resolution"></a>Résolution  
 Assurez-vous que le compte d'administrateur de l'application SSO est valide avant de créer une application associée. Vous devez ensuite activer l'application associée pour utiliser l'application.  
  
#### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a>Une erreur RPC se produit lors de la connexion à un ordinateur client  
  
##### <a name="problem"></a>Problème  
 Lorsqu’un utilisateur exécute une commande comme **ssomanage - displayapp***\<applicationname\>*, où l’ordinateur tente de se connecter à un serveur SSO distant pour récupérer les informations, l’erreur suivante : erreur : 0x800706BA : le serveur RPC n’est pas disponible.  
  
##### <a name="cause"></a>Cause  
 Cette erreur se produit quand l'utilisateur ne spécifie pas les informations de serveur correctes ou quand le service SSO n'est pas disponible sur le serveur distant.  
  
##### <a name="resolution"></a>Résolution  
  
-   Suivez les étapes de [comment définir le serveur SSO](../core/how-to-set-the-sso-server.md) pour vous assurer que vous êtes connecté au serveur SSO approprié.  
  
-   Assurez-vous que le service SSO est activé et qu'il s'exécute sur le serveur SSO auquel vous vous connectez.  
  
#### <a name="master-secret-is-missing-or-corrupt"></a>Le secret principal est manquant ou corrompu  
  
##### <a name="problem"></a>Problème  
 Le secret principal est manquant ou corrompu. Il est normalement généré lors de la configuration. S'il est manquant, l'un des messages suivants s'affiche dans le journal des événements au moment du démarrage du service SSO de l'entreprise.  
  
 MessageId=10520  
  
 Severity=Warning  
  
 SSO_WARN_NO_SECRETS  
  
 MessageId=10565  
  
 Severity=Error  
  
 SSO_ERROR_SECRET_VALIDATE_FAILED  
  
 MessageId=10521  
  
 Severity=Error  
  
 SSO_ERROR_SECRETS_NOT_LOADED  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si un secret a été généré pendant que le service SSO de l'entreprise était exécuté avec un certain compte de service, et que ce compte a ensuite été modifié. Le secret est stocké dans le registre sous une forme chiffrée et son chiffrement est réalisé à l'aide d'une clé en fonction de l'identité du compte de service (sous lequel ENTSSO est exécuté).  
  
##### <a name="resolution"></a>Résolution  
 Remplacez le compte de service sous lequel ENTSSO est exécuté par le compte de service utilisé lorsque le secret principal a été créé.  
  
 Pour modifier le compte du service ENTSSO :  
  
1.  Sauvegardez le secret principal. Pour plus d’informations, consultez [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
2.  Arrêtez les services SSO de l'entreprise.  
  
3.  Modifiez le compte du service.  
  
4.  Redémarrez SSO et ignorez les erreurs du journal des événements relevant l'éventuelle corruption d'un secret.  
  
5.  Restaurez le secret principal. Pour plus d’informations, consultez [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de l’authentification unique de l’entreprise](../core/implementing-enterprise-single-sign-on.md)