---
title: "Instructions pour la résolution des problèmes d’autorisation des Services Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e29543e9-9b87-437b-ac91-8f1cce01fab4
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68fc866a2a1f2c51a0649cf8a01ef03164b9a913
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-resolving-web-services-permissions-problems"></a>Instructions pour la résolution des problèmes d'autorisation liés aux services Web
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite pleinement les services Web dans le cadre de l'utilisation de l'adaptateur SOAP et lors de la publication d'orchestrations en tant que services Web. Cette rubrique propose des recommandations d'ordre général pour limiter les problèmes d'autorisation liés aux services Web, ainsi que des procédures à suivre pour résoudre les éventuels problèmes de ce type liés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="general-guidelines"></a>Règles générales  
  
-   **Configuration des comptes d’utilisateur**: Assurez-vous que l’identité du processus IIS application hôte associée au répertoire virtuel qui héberge le service Web est définie sur un compte d’utilisateur spécifique et assurez-vous que ce compte d’utilisateur est ajouté aux groupes suivants :  
  
    -   utilisateurs d'hôtes BizTalk isolés (domaine ou groupe local) ;  
  
    -   IIS_WPG (groupe local).  
  
     L'appartenance à ces 2 groupes est requise pour accorder au service Web créé par l'Assistant Publication du Service Web BizTalk les droits appropriés pour publier un message de requête SOAP dans la base de données MessageBox de BizTalk, qui active ensuite l'orchestration d'abonnement. Pour plus d’informations sur la détermination ou la définition de l’identité du processus IIS application hôte, consultez le **l’identité du processus de hôte d’Application IIS pour le paramètre** section de [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md).  
  
-   **Définition des autorisations sur le dossier spécifié par la variable d’environnement TEMP**: Vérifiez que l’identité de processus de l’hôte de l’application IIS du répertoire virtuel qui héberge le service Web est en lecture et en écriture sur le dossier spécifié par le Variable d’environnement TEMP. Pour déterminer le dossier spécifié par la variable d'environnement TEMP, ouvrez une invite de commandes sur le serveur BizTalk Server, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
    ```  
    echo %TEMP%  
    ```  
  
     Le dossier spécifié par la variable d'environnement TEMP est l'emplacement où le service Web subit une compilation juste-à-temps (JIT) dans un fichier dll (bibliothèque de liens dynamiques). Il doit donc être accessible en lecture et en écriture par ce compte d'utilisateur.  
  
-   **Envoie des informations d’identification dans l’appel de méthode SOAP**: Assurez-vous que le client du service Web envoie des informations d’identification dans l’appel de méthode SOAP. Par défaut, IIS 7.0 dans [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] requiert une authentification Windows. Lors du test d'un service Web avec Internet Explorer, les informations d'identification de l'utilisateur connecté sont automatiquement envoyées. C'est la raison pour laquelle le service Web peut fonctionner depuis Internet Explorer mais échouer avec un autre client. Si le client de service Web n'ajoute pas les informations d'identification à l'appel de méthode SOAP, une exception SOAP est générée illustrant une erreur d'authentification. Pour plus d’informations sur l’envoi des informations d’identification dans une méthode SOAP appel consultez l’exemple de code disponible dans [comment utiliser les classes System.Net nouvelles pour créer un client HTTP](http://support.microsoft.com/kb/303436).  
  
-   **Résolution des erreurs d’appel de service Web**: si les erreurs se produisent lors de l’appel d’un service Web, vérifiez le journal des applications ou message de service et des événements suivi d’instance via l’Administration de BizTalk Server **Hub du groupe**page. Pour plus d’informations sur les causes possibles de l’erreur, consultez [analyse de BizTalk Server](../core/monitoring-biztalk-server.md) et [à l’aide de la Page Hub du groupe](../core/using-the-group-hub-page.md).  
  
-   **Collecte des informations de débogage**: pour obtenir des informations de débogage détaillées, suivez les étapes décrites dans la rubrique [débogage de Services Web publiés](../core/debugging-published-web-services.md) si les étapes ci-dessus ne résolvent pas le problème.  
  
## <a name="known-issues"></a>Problèmes connus  
 Pour plus d’informations sur les problèmes connus avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] liés aux autorisations des services Web, consultez « Vous ne pouvez pas appeler une orchestration est exposée comme un service Web sur un serveur qui est en cours d’exécution BizTalk Server » à [http://go.microsoft.com/ fwlink / ? LinkId = 196379](http://go.microsoft.com/fwlink/?LinkId=196379).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’autorisations BizTalk Server](../core/troubleshooting-biztalk-server-permissions.md)   
 [Instructions pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md)