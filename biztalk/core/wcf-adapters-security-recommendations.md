---
title: "Recommandations de sécurité pour les adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF adapters, security
- security, WCF adapters
ms.assetid: bbaaca56-9ad5-4122-a8e9-6e975d308230
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ea0334e2d6164091e54321de8e1dccab5c07bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapters-security-recommendations"></a>Recommandations de sécurité pour les adaptateurs WCF
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les adaptateurs WCF pour publier (recevoir) et utiliser (envoyer) les services WCF. Nous vous recommandons de respecter les informations suivantes pour la sécurisation et le déploiement des adaptateurs WCF dans votre environnement.  
  
 Pour plus d’informations sur les adaptateurs WCF, consultez [adaptateurs WCF](../core/wcf-adapters.md). Pour plus d’informations sur les services WCF, consultez [à l’aide des Services WCF](../core/using-wcf-services.md)s.  
  
## <a name="security-recommendations-for-all-wcf-adapters"></a>Recommandations de sécurité pour tous les adaptateurs WCF  
  
-   Vous pouvez utiliser l'authentification unique de l'entreprise (SSO) dans les scénarios où vous devez effectuer le mappage du contenu de l'utilisateur frontal vers les informations d'identification stockées dans le système principal.  
  
-   Certains services ne doivent pas publier de métadonnées. Si vous désactivez la publication des métadonnées, vous réduisez la surface d'attaque de votre service et limitez les risques de divulgation d'informations involontaire. Pour plus d’informations sur les problèmes de sécurité liés aux métadonnées, consultez « Security Considerations with Metadata » à [http://go.microsoft.com/fwlink/?LinkId=196671](http://go.microsoft.com/fwlink/?LinkId=196671).  
  
-   Les combinaisons de liaisons de point de terminaison des métadonnées et de liaisons de points de terminaison de service ne sont pas toutes valides. Dans certains cas, les configurations de liaison d'un point de terminaison des métadonnées doivent être conformes aux configurations de liaison de son point de terminaison de service. Par exemple, lorsque les métadonnées sont utilisées depuis le même emplacement que l'emplacement de réception, le point de terminaison des métadonnées ne peut pas être configuré avec un mode de sécurité impliquant le transport HTTP si l'emplacement de réception utilise un mode de sécurité basé sur HTTPS.  
  
    > [!NOTE]
    >  Lors de la publication des métadonnées via le transport HTTP pour un point de terminaison de service avec le même emplacement mais nécessitant un mode de sécurité qui s’appuie sur le transport HTTPS, dans le fichier Web.config que l’Assistant Publication WCF BizTalk génère, vous devez définir les deux le **httpsGetEnabled** et **httpGetEnabled** attributs **true**.  
  
-   Les adaptateurs WCF exploitent les fonctions de sécurité de Windows Communication Foundation (WCF) pour communiquer. Il est important de comprendre les capacités et limitations de WCF en termes de sécurité. Pour plus d’informations sur les fonctionnalités de sécurité de WCF, consultez « Windows Communication Foundation Security » à [http://go.microsoft.com/fwlink/?LinkId=87806](http://go.microsoft.com/fwlink/?LinkId=87806).  
  
## <a name="security-recommendations-for-the-isolated-wcf-adapters"></a>Recommandations de sécurité pour les adaptateurs WCF isolés  
  
-   Pour obtenir des recommandations de sécurité pour la publication de services Web, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
-   Les adaptateurs WCF isolés tels que les adaptateurs WCF-CustomIsolated, WCF-BasicHttp et WCF-WSHttp exploitent le protocole Hypertext Transfer Protocol (HTTP) pour envoyer et recevoir des messages depuis et vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez donc suivre les recommandations de sécurité pour sécuriser les services Internet (IIS).  
  
-   Lorsque vous créez un pool d'applications pour l'emplacement de réception d'un WCF isolé, vous devez le configurer pour qu'il s'exécute sous un compte qui est membre du groupe [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] pour l'hôte isolé qui exécute l'adaptateur de réception WCF, ainsi que du groupe Internet Information Services Worker Process (groupe IIS_WPG). Vous devez ensuite configurer l'instance d'hôte pour que l'adaptateur de réception WCF puisse utiliser ce compte. Si vous remplacez le compte du groupe IIS_WPG, vous devez vous assurer de mettre également à jour l'instance d'hôte pour qu'elle s'exécute sous le nouveau compte.  
  
## <a name="security-recommendations-for-the-wcf-custom-adapter"></a>Recommandations de sécurité pour l'adaptateur WCF-Custom  
  
-   Si un emplacement de réception WCF-Custom se produit à utiliser le pilote du noyau HTTP (HTTP.sys) tels que les **httpsTransport** élément de liaison pour les communications Secure Sockets Layer (SSL), l’emplacement de réception doit disposer d’un certificat inscrit pour chaque socket (combinaison adresse IP/port). Utilisez l'outil HttpCfg.exe pour lier un certificat SSL à un port sur l'ordinateur. Pour plus d’informations, consultez « Comment à : configurer un Port avec un certificat SSL » à [http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384).  
  
## <a name="security-recommendations-for-the-wcf-netmsmq-adapter"></a>Recommandations de sécurité pour l'adaptateur WCF-NetMsmq  
  
-   Pour utiliser l’adaptateur WCF-NetMsmq, vous devez configurer les paramètres de sécurité MSMQ pour l’adaptateur WCF-NetMsmq de la même façon que pour les [netMsmqBinding](http://go.microsoft.com/fwlink/?LinkId=87813). Pour plus d’informations sur la façon de configurer les paramètres de sécurité MSMQ pour la **netMsmqBinding**, consultez « Troubleshooting Queued Messaging » à l’adresse [http://go.microsoft.com/fwlink/?LinkId=87816](http://go.microsoft.com/fwlink/?LinkId=87816).  
  
## <a name="wcf-adapters-use-the-chaintrust-mode-to-validate-certificates"></a>Les adaptateurs WCF utilisent le mode ChainTrust pour valider les certificats.  
  
-   Étant donné que WCF standard adaptateurs de réception utilisent le [ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960) mode pour valider les certificats de client et le service, vous devez installer la chaîne de certificats d’autorité de certification pour valider les certificats X.509. Pour modifier ce comportement par défaut, vous pouvez utiliser WCF-Custom ou l’adaptateur WCF-CustomIsolated.  
  
## <a name="security-auditing-for-the-wcf-adapters"></a>Audit de sécurité pour les adaptateurs WCF  
  
-   Les adaptateurs WCF n'utilisent pas les fonctions d'audit de sécurité WCF par défaut. Il existe différentes façons d'activer les fonctions d'audit de sécurité WCF pour les adaptateurs WCF. Pour plus d’informations sur les fonctionnalités d’audit de sécurité WCF, consultez « Auditing Security Events » à [http://go.microsoft.com/fwlink/?LinkId=88975](http://go.microsoft.com/fwlink/?LinkId=88975).  
  
-   Pour utiliser la sécurité WCF avec l’adaptateur de réception WCF-Custom, les fonctionnalités d’audit, vous pouvez configurer le **ServiceSecurityAuditBehavior** pour les emplacements de réception.  
  
-   Pour les adaptateurs WCF In-process, vous pouvez activer les compteurs de performance via le fichier BTSNTSvc.exe.config. Pour les adaptateurs WCF isolés, vous pouvez activer le suivi WCF en modifiant le fichier Web.config que l'Assistant Publication de services WCF BizTalk crée dans le dossier de l'application Web. Pour modifier le fichier de configuration BTSNtSvc.exe.config ou Web.config, ouvrez-le, puis configurez le suivi WCF, comme décrit dans l'exemple de configuration suivant :  
  
    > [!NOTE]
    >  Le fichier BTSNTSvc.exe.config est toujours situé dans le même répertoire que le fichier BTSNTSvc.exe (généralement, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
    > [!NOTE]
    >  Une fois le fichier BTSNTSvc.exe.config modifié, vous devez redémarrer les instances d'hôte exécutant les emplacements de réception WCF In-process.  
  
    ```  
    <configuration>  
        <system.serviceModel>  
          <diagnostics performanceCounters="All" />  
          <behaviors>  
            <serviceBehaviors>  
              <behavior name="ServiceBehaviorConfiguration">  
                <serviceSecurityAudit  
                          auditLogLocation="Application"  
                          suppressAuditFailure="true"  
                          serviceAuthorizationAuditLevel="SuccessOrFailure"  
    messageAuthenticationAuditLevel="SuccessOrFailure" />  
              </behavior>  
            </serviceBehaviors>  
          </behaviors>  
          <services>  
            <service name="Microsoft.BizTalk.Adapter.Wcf.Runtime.BizTalkServiceInstance" behaviorConfiguration="ServiceBehaviorConfiguration">  
            </service>  
          </services>        
        </system.serviceModel>  
    </configuration>  
    ```  
  
-   Vous pouvez également utiliser un compteur de performances lié à la sécurité tel que Security Calls Not Authorized pour gérer les adaptateurs WCF. Pour plus d’informations sur l’activation des compteurs de performance WCF, consultez [compteurs de Performance des adaptateurs WCF](../core/wcf-adapters-performance-counters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la sécurité](../core/planning-for-security.md)