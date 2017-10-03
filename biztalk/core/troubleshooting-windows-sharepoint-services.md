---
title: "Dépannage de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9acf9a0d-2c92-4227-80f8-b2d0cca0c232
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51243216f2adb73454477252c7b54358df229610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-windows-sharepoint-services"></a>Dépannage de Windows SharePoint Services
Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est utilisé par l'adaptateur Windows SharePoint Services. Cette rubrique décrit certains des problèmes rencontrés avec Windows SharePoint Services et leurs résolutions possibles.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="login-failed-for-user-nt-authoritynetwork-service-error-occurs-when-attempting-to-create-content-database"></a>L'erreur Échec de la connexion pour l'utilisateur 'NT AUTHORITY\NETWORK SERVICE' se produit lors d'une tentative de création de la base de données de contenu  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez de créer une base de données de contenu à l'aide du site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Échec de la connexion pour l'utilisateur 'NT AUTHORITY\NETWORK SERVICE'  
  
##### <a name="cause"></a>Cause  
 Ce problème se produit lorsque le propriétaire de la base de données à laquelle vous vous connectez est différent de l'identité de pool d'applications sous laquelle Windows SharePoint Services s'exécute.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, effectuez l’une des opérations suivantes :  
  
-   Octroyez au compte SERVICE RÉSEAU les autorisations de création de base de données dans SQL Server.  
  
-   Modifiez le compte d'identité du pool d'applications en un compte doté des autorisations de création de base de données dans SQL Server.  
  
#### <a name="service-unavailable-error-occurs-when-accessing-the-sharepoint-central-administration-web-site"></a>L'erreur « Service non disponible » se produit lors de l'accès au site Web Administration centrale de SharePoint  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'ouvrir le site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Service non disponible  
  
##### <a name="cause"></a>Cause  
 Cette erreur se produit généralement lorsque le pool d'applications (IIS 6.0 ou IIS 7.0) ou l'application COM+ hôte (IIS 5.x) du site Web Administration centrale de SharePoint est arrêté. Cela survient généralement lorsque le pool d'applications ou l'application COM+ est configurée avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe spécifiés ne sont pas valides.  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes décrites dans la section « Paramètre IIS Application identité du processus hôte » de la rubrique [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour définir l’identité du processus hôte approprié.  
  
#### <a name="cannot-connect-to-the-configuration-database-error-occurs-when-attempting-to-extend-and-create-a-content-database"></a>L'erreur « Impossible de se connecter à la base de données de configuration » se produit lors d'une tentative d'extension et de création d'une base de données de contenu  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'étendre et de créer une base de données de contenu à l'aide du site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Impossible de se connecter à la base de données de configuration  
  
##### <a name="cause"></a>Cause  
 Ce problème se produit lorsque le compte utilisé par le pool d'applications qui exécute le site Web Administration centrale de SharePoint ne dispose pas des autorisations requises pour la base de données SQL Server.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, effectuez l’une des opérations suivantes :  
  
-   Octroyez au compte utilisé par le pool d'applications du site Web Administration centrale de SharePoint les autorisations de création de base de données dans SQL Server.  
  
-   Modifiez le compte d'identité du pool d'applications en un compte doté des autorisations de création de base de données dans SQL Server.  
  
#### <a name="the-sharepoint-timer-service-service-failed-to-start-error-is-generated-in-the-application-log-after-rebooting-server"></a>Une erreur est générée dans le journal de l'application après le redémarrage du serveur indiquant que le démarrage du service du minuteur SharePoint a échoué  
  
##### <a name="problem"></a>Problème  
 Après le redémarrage du serveur, une erreur s'affiche dans les journaux d'événements indiquant que  
  
 le démarrage du service du minuteur SharePoint a échoué  
  
 L'erreur suivante peut également s'afficher lors de l'ouverture du site Web Administration centrale de SharePoint indiquant que  
  
 la connexion à la base de données de configuration WSS STS_Config n'a pas pu être établie.  
  
##### <a name="cause"></a>Cause  
 Cette erreur se produit lorsque le service du minuteur SharePoint ne parvient pas à contacter la base de données [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] après le redémarrage. Ce service permet d'envoyer des notifications et d'exécuter des tâches planifiées pour [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. Cette erreur se produit généralement lorsque le compte utilisé pour exécuter le service est configuré avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe ne sont plus valides.  
  
##### <a name="resolution"></a>Résolution  
 Assurez-vous que le nom d'utilisateur et le mot de passe spécifiés pour le compte de connexion du service du minuteur SharePoint sont corrects et que le service a été démarré.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer un serveur virtuel Windows SharePoint Services](http://support.microsoft.com/kb/832769)   
 [Comment sauvegarder et restaurer des installations de Windows SharePoint Services qui utilisent Microsoft SQL Server 2000 Desktop Engine (Windows)](http://support.microsoft.com/kb/833797)   
 [Vous recevez un message d’erreur « Impossible de se connecter à la base de données de configuration » lorsque vous vous connectez à votre site Web Windows SharePoint Services](http://support.microsoft.com/kb/823287)   
 [Le message d’erreur « Service non disponible » s’affiche lorsque vous parcourez un Site Web de Windows SharePoint Services](http://support.microsoft.com/kb/823552)   
 [Le message d’erreur « La base de données < nom_base_de_données > existe déjà » s’affiche lorsque vous gérez votre base de données de contenu de Windows SharePoint Services](http://support.microsoft.com/kb/828815)