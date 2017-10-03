---
title: "Résolution des problèmes de Internet Information Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f77084f1-5797-42ab-bbf6-fe815144232e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 222d034c2dee38f041bb53b3164869712201bc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-internet-information-services"></a>Dépannage des Services Internet (IIS)
Microsoft Internet Information Services (IIS) est très utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour ses diverses fonctionnalités, notamment les adaptateurs HTTP, SOAP et Windows SharePoint Services. Cette rubrique décrit certains des problèmes que vous pouvez rencontrer avec les services Internet (IIS), ainsi que leurs résolutions possibles.  
  
## <a name="known-issues"></a>Problèmes connus  
 Les erreurs présentées dans cette rubrique peuvent ne pas s'afficher si vous ne configurez pas Internet Explorer pour désactiver les messages d'erreur HTTP simplifiés.  
  
#### <a name="to-configure-internet-explorer-to-disable-friendly-http-error-messages"></a>Pour configurer Internet Explorer pour désactiver les messages d'erreur HTTP simplifiés  
  
1.  Sur le **outils** menu, cliquez sur **Options Internet**.  
  
2.  Sur le **avancé** sous l’onglet du **navigation** section, désactivez le **afficher des messages d’erreur HTTP simplifiés** case à cocher, puis cliquez sur **OK**.  
  
3.  Fermez Internet Explorer.  
  
#### <a name="http-404---file-not-found-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>L'erreur « HTTP 404 - Fichier introuvable » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Page introuvable  
  
 \- ou -  
  
 HTTP 404 - Fichier introuvable  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire pour les raisons suivantes :  
  
-   Le fichier recherché a été renommé.  
  
-   Le fichier recherché a été déplacé ou supprimé.  
  
-   Le fichier recherché est temporairement inaccessible en raison d'une maintenance, de mises à niveau ou d'autres causes inconnues.  
  
-   Le fichier recherché n'existe pas.  
  
-   IIS 6.0 : l'extension de service Web ou le type MIME approprié n'est pas activé.  
  
-   Un répertoire virtuel est mappé sur la racine d'un lecteur qui se trouve sur un autre serveur.  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes décrites dans la section Résolution de la Base de connaissances Microsoft l’article 248033, « principales causes du serveur IIS retourne l’erreur « HTTP 404 - Fichier introuvable » » disponible à l’adresse [http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033).  
  
#### <a name="cannot-find-server-or-dns-error-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>L'erreur « Impossible de trouver le serveur ou erreur DNS » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Impossible d'afficher la page  
  
 \- ou -  
  
 Impossible de trouver le serveur ou erreur DNS  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire pour les raisons suivantes :  
  
-   Vos paramètres de connexion Internet Explorer sont incorrects.  
  
-   Un pare-feu ou un serveur proxy incorrectement configuré, incompatible ou ne fonctionnant pas a été installé.  
  
-   Un fichier Hosts comporte une entrée incorrecte.  
  
-   Votre carte réseau ne fonctionne pas correctement ou des pilotes incompatibles ont été installés.  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes décrites dans la section Résolution de l’article 326155 de la Base de connaissances Microsoft « message d’erreur lorsque vous essayez d’accéder à un site Web dans Internet Explorer : « Impossible d’afficher la Page » » disponible à l’adresse [http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).  
  
#### <a name="401---access-denied-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>L'erreur « 401 Accès refusé » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 401 - Accès refusé  
  
##### <a name="cause"></a>Cause  
 IIS définit plusieurs erreurs 401 indiquant une cause plus précise de l'erreur. Ces codes d'erreur spécifiques s'affichent dans le navigateur :  
  
-   401.1 - Non autorisé : accès refusé en raison d'informations d'identification non valides.  
  
-   401.2 - Non autorisé : accès refusé en raison de la configuration du serveur.  
  
-   401.3 - Non autorisé : accès refusé en raison d'une liste de contrôle d'accès (ACL) définie sur la ressource requise.  
  
-   401.4 - Non autorisé : échec de l'autorisation en raison du filtre installé sur le serveur Web.  
  
-   401.5 - Non autorisé : échec de l'autorisation en raison d'une application ISAPI/CGI.  
  
-   401.7 – Accès refusé par la stratégie d'autorisation d'URL sur le serveur Web. Ce code d'erreur est spécifique à IIS 6.0.  
  
 Pour obtenir une liste complète des codes d’état IIS 7.0, consultez l’article 943891, de la Base de connaissances Microsoft « Codes d’état HTTP dans IIS 7.0 » disponible à l’adresse [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891).  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes de [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour résoudre les problèmes d’autorisation IIS.  
  
#### <a name="500---internal-server-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>L'erreur « 500 - Erreur interne au serveur » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 500 - Erreur interne au serveur  
  
##### <a name="cause"></a>Cause  
 Ce message d'erreur peut découler de divers problèmes côté serveur.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, procédez comme suit :  
  
-   Consultez le journal de l'application du serveur IIS pour obtenir des informations sur la cause de l'erreur.  
  
-   Consultez les fichiers journaux IIS ou HTTPERR pour obtenir des informations pouvant s'avérer utiles pour déterminer la cause de l'erreur. Les fichiers journaux IIS d'un ordinateur exécutant les systèmes d’exploitation [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.  
  
     Les fichiers journaux IIS d'un ordinateur exécutant Windows Server 2008 ou Windows Vista se trouvent par défaut dans le répertoire suivant :  
  
     C:\inetpub\logs\LogFiles\W3SVC1\  
  
     Les fichiers journaux HTTPERR sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%*system32LogFilesHTTPERR  
  
    > [!NOTE]
    >  Le fichier journal HTTPERR est disponible uniquement sur un ordinateur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou Windows Vista.  
  
#### <a name="service-unavailable-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>L'erreur « Service indisponible » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :  
  
 Service non disponible  
  
##### <a name="cause"></a>Cause  
 Cette erreur se produit généralement lorsque le pool d'applications (IIS 6.0 et IIS 7.0) pour la page Web est arrêté. Ceci survient généralement lorsque le pool d'applications ou l'application COM+ est configuré avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe spécifiés ne sont pas valides.  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes décrites dans la section « Paramètre IIS Application identité du processus hôte » de la rubrique [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour définir l’identité du processus hôte approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md)