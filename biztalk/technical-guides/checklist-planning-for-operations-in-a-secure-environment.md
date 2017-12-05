---
title: "Liste de vérification : Planification des opérations dans un environnement sécurisé de | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d6464df-6736-46e2-a0c7-cc2a256c5144
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c99c14f16df3f6b98555a4006706eb7804f24a34
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="checklist-planning-for-operations-in-a-secure-environment"></a>Liste de vérification : Planification des opérations dans un environnement sécurisé
En cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement sécurisé nécessite des étapes supplémentaires pour le déploiement et la configuration. Alors que les installations du système d’exploitation par défaut ne sont pas en compte, mais les scénarios où les stratégies de sécurité restrictives ont été appliqués, prenez en compte les informations de cette section. Le niveau de restriction appliquée aux serveurs peut-être varier, mais les informations ci-dessous doivent couvrir la plupart des cas et qu’il seraient un un bon point de départ.  
  
-   [Considérations de sécurité pour les ordinateurs exécutant BizTalk Server](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_BTSSec)  
  
-   [Considérations de sécurité pour les ordinateurs exécutant SQL Server](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_SQLServSec)  
  
-   [Considérations de sécurité supplémentaires](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_AddSec)  
  
<a name="BKMK_BTSSec"></a>   
## <a name="security-considerations-for-computers-running-biztalk-server"></a>Considérations de sécurité pour les ordinateurs exécutant BizTalk Server  
 Le tableau suivant propose les paramètres liés à la sécurité sur les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="user-rights-assignment"></a>Attribution des droits utilisateur  
 Pour démarrer le composant logiciel enfichable MMC de l’attribution des droits utilisateur, cliquez sur **Démarrer**, cliquez sur **outils d’administration**, puis cliquez sur **stratégie de sécurité locale**. Dans le **stratégie de sécurité locale** MMC enfichable, développez **paramètres de sécurité**, développez **stratégies locales**, puis cliquez sur **attribution des droits utilisateur**.  
  
|Paramètre de stratégie|Valeurs|Référence et les détails|  
|--------------------|------------|---------------------------|  
|Ouvrir une session en tant que service|Utilisateurs d'applications BizTalk|Requis pour exécuter les Instances d’hôte BizTalk. Pour plus d’informations sur les différents comptes d’utilisateurs, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
|Ouvrir une session en tant que service|Compte de Service de mise à jour RuleEngine|Requis pour exécuter le Service de mise à jour RuleEngine. Pour plus d’informations sur les différents comptes d’utilisateurs, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
|Ouvrir une session en tant que service|Compte de Service d’authentification unique|Requis pour exécuter le Service d’authentification unique de l’entreprise. Pour plus d’informations sur les différents comptes d’utilisateurs, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
  
### <a name="system-services"></a>Services système  
 Pour démarrer le composant logiciel enfichable MMC Services, cliquez sur **Démarrer**, cliquez sur **exécuter**et dans le **exécuter** boîte de dialogue, tapez `services.msc` et appuyez sur ENTRÉE.  
  
|Nom du service|Type de démarrage<sup>1</sup>|Détails|Utilisateur<sup>2</sup>|Permissions|Détails|  
|------------------|------------------------------|-------------|----------------------|-----------------|-------------|  
|Application système COM+|Automatique|Requis par BizTalk Server pour s’exécuter correctement|(par défaut)|||  
|Client DHCP|Automatique|Requis même si les adresses IP sont statiques|(par défaut)|||  
|Coordinateur de transactions distribuées|Automatique|Requis par BizTalk Server pour s’exécuter correctement|Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||||Compte de Service des hôtes BizTalk|Contrôle total|Requis pour démarrer des hôtes BizTalk|  
||||Service réseau|Contrôle total|Requis par IIS|  
|HTTP SSL<sup>3</sup>|Automatique|Requis par IIS|(par défaut)|||  
|Les Services IPSEC<sup>3</sup>|Automatique|IPSEC augmente la sécurité du réseau si utilisé|(par défaut)|||  
|Accès réseau|(par défaut)||Service local|Contrôle total||  
|Fournisseur de la prise en charge de la sécurité NTLM<sup>3</sup>|Automatique|Requis pour l’authentification Kerberos pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans SQL|(par défaut)|||  
|Gestionnaire de connexions d’accès à distance|(par défaut)||Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||||Compte de Service des hôtes BizTalk|Contrôle total|Requis pour démarrer des hôtes BizTalk|  
||||Service réseau|Contrôle total|Requis par IIS|  
|Localisateur de procédure distante (RPC) d’appel|Automatique|Requis par BizTalk Server|(par défaut)|||  
|Service de découverte automatique de Proxy WinHTTP Web|(par défaut)||Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||||Compte de Service des hôtes BizTalk|Contrôle total|Requis pour démarrer des hôtes BizTalk|  
  
 <sup>1</sup> la valeur (valeur par défaut) signifie que les paramètres par défaut appliqués par la stratégie de sécurité ne sont pas modifiés  
  
 <sup>2</sup> la valeur (valeur par défaut) signifie que les autorisations d’utilisateur par défaut pour le service n’ont pas été modifiées  
  
### <a name="registry-settings"></a>Paramètres du Registre  
 Pour démarrer l’Éditeur du Registre, cliquez sur **Démarrer**, cliquez sur **exécuter**et dans le **exécuter** boîte de dialogue, tapez `regedit` et appuyez sur ENTRÉE.  
  
|Clé|Utilisateur|Permissions|Détails|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|Service réseau|Contrôle total|Requis par le Service Client DHCP|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|Service réseau|Contrôle total|Requis par le Service Client DHCP|  
  
<a name="BKMK_SQLServSec"></a>   
## <a name="security-considerations-for-computers-running-sql-server"></a>Considérations de sécurité pour les ordinateurs exécutant SQL Server  
 Le tableau suivant propose les paramètres liés à la sécurité sur les ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
### <a name="user-rights-assignment"></a>Attribution des droits utilisateur  
 Pour démarrer le composant logiciel enfichable MMC de l’attribution des droits utilisateur, cliquez sur **Démarrer**, cliquez sur **outils d’administration**, puis cliquez sur **stratégie de sécurité locale**. Dans le **stratégie de sécurité locale** MMC enfichable, développez **paramètres de sécurité**, développez **stratégies locales**, puis cliquez sur **attribution des droits utilisateur**.  
  
|Paramètre de stratégie|Valeurs|Référence et les détails|  
|--------------------|------------|---------------------------|  
|Agir en tant que partie du système d'exploitation|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Ajuster les quotas de mémoire pour un processus|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Outrepasser le contrôle de parcours|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Créer des objets globaux|Compte de service SQL Server|Requis par le service SSIS. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Permettre aux comptes d’utilisateur et d’ordinateur d’être approuvés pour la délégation|Nom du Cluster de serveurs SQL Server Service compte, les serveurs SQL Server, BizTalk Server, SQL Server|Requis par BizTalk Server. Nom du serveur est dans l’écran \<nom_serveur\>$. Pour plus d’informations, consultez [Comment : activer l’authentification Kerberos sur un Cluster de basculement SQL Server](http://go.microsoft.com/fwlink/?LinkId=157417) (http://go.microsoft.com/fwlink/?LinkId=157417).|  
|Ouvrir une session en tant que service|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Ouvrir une session en tant que service|Compte de Service d’authentification unique|Requis pour exécuter le Service d’authentification unique de l’entreprise. Pour plus d’informations sur les différents comptes d’utilisateurs, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
|Ouvrez une session en tant que traitement par lots|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
|Remplacer un jeton de niveau processus|Compte de Service SQL Server Agent, compte de Service SQL Server|Requis pour exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations, consultez [configuration des comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkId=157415) (http://go.microsoft.com/fwlink/?LinkId=157415).|  
  
### <a name="system-services"></a>Services système  
 Pour démarrer le composant logiciel enfichable MMC Services, cliquez sur **Démarrer**, cliquez sur **exécuter**et dans le **exécuter** boîte de dialogue, tapez `services.msc` et appuyez sur ENTRÉE.  
  
|Nom du service|Type de démarrage<sup>1</sup>|Détails|Utilisateur<sup>2</sup>|Permissions|Détails|  
|------------------|------------------------------|-------------|----------------------|-----------------|-------------|  
|Client DHCP|Automatique|Requis même si les adresses IP sont statiques|(par défaut)|||  
|Coordinateur de transactions distribuées|Manuel|Démarrage du service géré par le Service de Cluster|Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||||Service réseau|Contrôle total|Requis par IIS|  
|HTTP SSL<sup>3</sup>|Automatique|Requis par IIS|(par défaut)|||  
|Les Services IPSEC<sup>3</sup>|Automatique|IPSEC augmente la sécurité du réseau si utilisé|(par défaut)|||  
|Accès réseau|(par défaut)||Service local|Contrôle total||  
|Fournisseur de la prise en charge de la sécurité NTLM<sup>3</sup>|Automatique|Requis pour l’authentification Kerberos pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans SQL|(par défaut)|||  
|Gestionnaire de connexions d’accès à distance|(par défaut)||Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||||Service réseau|Contrôle total|Requis par IIS|  
|Server|Automatique|Utilisé pour les ressources de partage de fichiers en cluster|Service réseau|Contrôle total||  
|Service de découverte automatique de Proxy WinHTTP Web|(par défaut)||Compte de Service d’authentification unique|Contrôle total|Requis pour démarrer le service d’authentification unique|  
||Service de publication World Wide Web|Automatique|Requis par SQL Server Reporting Services|(par défaut)||  
  
 <sup>1</sup> la valeur (valeur par défaut) signifie que les paramètres par défaut appliqués par la stratégie de sécurité ne sont pas modifiés  
  
 <sup>2</sup> la valeur (valeur par défaut) signifie que les autorisations d’utilisateur par défaut pour le service n’ont pas été modifiées  
  
### <a name="registry-settings"></a>Paramètres du Registre  
 Pour démarrer l’Éditeur du Registre, cliquez sur **Démarrer**, cliquez sur **exécuter**et dans le **exécuter** boîte de dialogue, tapez `regedit` et appuyez sur ENTRÉE.  
  
|Clé|Utilisateur|Permissions|Détails|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|Service réseau|Contrôle total|Requis par le Service Client DHCP|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|Service réseau|Contrôle total|Requis par le Service Client DHCP|  
  
<a name="BKMK_AddSec"></a>   
## <a name="additional-security-considerations"></a>Considérations de sécurité supplémentaires  
 Le tableau suivant propose les autres relatives à la sécurité des paramètres importants pour votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
|Objet affecté|Modifier|Référence et les détails|  
|-----------------------|------------|---------------------------|  
|Compte de Service d’authentification unique|Accorder l’autorisation contrôle total sur le Cluster dans le Gestionnaire du Cluster|Cette modification n’est requise pour l’authentification unique afin de fonctionner correctement|  
|Nom du Cluster de serveurs SQL Server Service compte, les serveurs SQL Server, BizTalk Server, SQL Server|Approbation pour la délégation dans Active Directory|Obligatoire pour une authentification Kerberos. Pour plus d’informations, consultez [Comment : activer l’authentification Kerberos sur un Cluster de basculement SQL Server](http://go.microsoft.com/fwlink/?LinkId=157417) (http://go.microsoft.com/fwlink/?LinkId=157417).|  
|Compte de service SQL Server|Accorder l’autorisation de créer des entrées de nom principal de service|Obligatoire pour une authentification Kerberos. Pour plus d’informations, consultez [comment utiliser l’authentification Kerberos dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=157420) (http://go.microsoft.com/fwlink/?LinkId=157420).|  
|Nœuds de SQL Server, nom du cluster SQL|Créer des entrées de nom principal de service pour l’utilisateur de compte de Service SQL Server|Obligatoire pour une authentification Kerberos. Pour plus d’informations, consultez [comment utiliser l’authentification Kerberos dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=157420) (http://go.microsoft.com/fwlink/?LinkId=157420).|  
|Ressource de cluster de nom réseau SQL|L’inscription DNS doit réussir, activer l’authentification Kerberos|Requis pour une authentification Kerberos|  
|Configuration surface d’exposition SQL Server|Activer la connexion administrateur directe à distance|Requis par le Service SQL Browser pour fonctionner correctement ce qui est requis par les Clients de SQL (BizTalk/ASP.NET) afin de localiser correctement une instance nommée de SQL Server|  
|Groupe utilisateurs d’applications BizTalk|L’autorisation GRANT Execute sur **sp_help_jobhistory** dans **msdb** base de données|Requis par[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Listes de contrôle pour d’autres tâches importantes](~/technical-guides/checklists-for-other-important-tasks.md)