---
title: "Recommandations de sécurité pour un déploiement BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, security
- Windows Server 2003 Security Configuration Wizard (SCW)
- user accounts, security
- permissions
- access control
- security, deploying
- channel level encryption
- security, permissions
ms.assetid: 033fff11-d989-46ba-83ed-5063f7cd7818
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fad4f4a734f396b3ffec726b65fe19d62ee0f5ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-recommendations-for-a-biztalk-server-deployment"></a>Recommandations de sécurité pour un déploiement BizTalk Server
Cette section fournit des recommandations générales sur la sécurisation de votre environnement Microsoft BizTalk Server.  
  
## <a name="topology-level-recommendations"></a>Recommandations en matière de topologie  
 **Utilisez le chiffrement au niveau du canal.** Par défaut, les flux de données réseau entre les différents composants de BizTalk Server apparaissent en clair. Si la falsification ou la détection de données lors du transfert des messages entre des ordinateurs constitue un problème, il est recommandé d'utiliser le chiffrement au niveau du canal, tel que le protocole IPSec (Internet Protocol Security) ou SSL (Secure Sockets Layer). Par défaut, BizTalk Server ne configure pas le chiffrement au niveau du canal. Aussi, les données critiques (clés de chiffrement, mots de passe, etc.) ne sont-elles pas affichées en clair. La base de données SSO gère les informations personnelles en les stockant sous forme chiffrée à l'aide d'un secret principal (clé de chiffrement) fourni par le serveur de secret principal. Par défaut, elle reçoit, stocke et transmet les informations personnelles sous forme chiffrée.  
  
 Pour plus d’informations sur le protocole SSL, consultez [http://go.microsoft.com/fwlink/p/?LinkId=189708](http://go.microsoft.com/fwlink/p/?LinkId=189708).  
  
 **Permettent de garantir la sécurité physique des serveurs.** Vous devez également prendre en considération la sécurité physique des serveurs, des périphériques, des réseaux, des câbles, de l'alimentation et des autres composants. Vous devez placer vos ordinateurs dans un environnement sécurisé et limiter l'accès aux ordinateurs contenant des informations vitales pour l'entreprise, telles que les bases de données.  
  
 **Installez uniquement les composants que vous allez utiliser.** Si vous devez installer Internet Information Services (IIS) dans votre environnement (sur des ordinateurs situés dans le réseau de périmètre ou exécutant des adaptateurs HTTP et SOAP), il n'est pas indispensable d'installer les sous-composants FTP (File Transport Protocol), WebDAV et SMTP (Simple Mail Transfer Protocol) d'IIS. De même, veillez à installer et configurer les seules fonctionnalités BizTalk Server requises pour votre environnement. Par exemple, configurez uniquement l'adaptateur Message Queuing de BizTalk si vous en avez l'utilité. Cela permet de réduire la surface d'attaque potentielle de votre environnement.  
  
Si vous utilisez Internet Explorer, nous vous recommandons de que vous activez la sécurité renforcée d’Internet Explorer.  
  
 **Installer les service packs et mises à jour**. Nous vous recommandons de toujours installer les derniers service packs de produit et les mises à jour Microsoft sur tous les serveurs qui ont [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] ressources, y compris [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)].  
  
 **N’enregistrez pas les mots de passe en texte clair dans des scripts ou des fichiers de liaison.** Vous devez enregistrer les scripts dans des emplacements dotés de listes de contrôle d'accès discrétionnaire performantes afin que seuls les administrateurs BizTalk Server soient autorisés à afficher, modifier et exécuter ceux-ci. Lorsque les scripts et les fichiers de liaison sont associés à des mots de passe, veillez à masquer ces derniers dès que vous utilisez les scripts à des fins de configuration ou de déploiement. Ne laissez pas les mots de passe de ces fichiers en texte clair.  
  
 **Répertorie les utilisez contrôle d’accès discrétionnaire (DACL).** Veillez à octroyer l'accès à une ressource aux seuls utilisateurs et comptes qui en ont l'utilité, et à n'accorder à ceux-ci que les autorisations minimales nécessaires à l'exécution de leurs tâches. Placez les scripts de configuration dans des emplacements dotés de listes de contrôle d'accès discrétionnaire et n'insérez aucun mot de passe en texte clair dans les scripts. Vérifiez que les répertoires temporaires des comptes de service utilisés par BizTalk Server disposent de listes de contrôle d'accès discrétionnaire afin que seuls le compte de service et les administrateurs BizTalk y aient accès.  
  
 Lorsque vous utilisez des adaptateurs personnalisés, nous vous recommandons de stocker les composants d’extension de carte dans un emplacement avec discrétionnaire pour que seuls les administrateurs de BizTalk Server aient des autorisations en écriture à ces composants.  
  
 **Ne placez pas les serveurs BizTalk Server dans le réseau de périmètre.** Quelle que soit la taille de votre société, le fait de placer BizTalk Server dans le réseau de périmètre expose les serveurs aux attaques directes d'Internet et aux attaques d'autres serveurs du réseau de périmètre potentiellement compromis. Dans la mesure où BizTalk Server communique avec les bases de données Microsoft SQL Server dans le domaine de données, un utilisateur malveillant peut exploiter un serveur BizTalk compromis afin de falsifier des données de configuration et de traitement vitales pour l'entreprise.  
  
## <a name="biztalk-server-groups-and-accounts"></a>Groupes et comptes BizTalk Server  
 **Utiliser des comptes avec des droits d’utilisateur et les autorisations minimales.** Tous les comptes du système BizTalk Server doivent disposer des droits d'utilisateur minimaux dont ils ont besoin pour effectuer leurs tâches. Par exemple, les comptes de service que vous utilisez dans les serveurs de traitement ne doivent pas disposer de droits administratifs sous BizTalk Server, SQL Server ou Windows Server. Pour plus d’informations sur les autorisations de sécurité minimales et les droits de l’utilisateur a besoin d’un compte effectuer une tâche dans BizTalk Server, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md). Pour plus d’informations sur les groupes et les comptes utilisés par BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
 **Utiliser des comptes différents pour différentes fonctions.** Pour préserver la sécurité de votre environnement BizTalk Server, il est recommandé de créer différents comptes de service pour chaque instance d'hôte exécutée. Vous bénéficiez ainsi d'une meilleure disponibilité lors des mises à jour de mot de passe. Nous recommandons qu’un compte de service n’est pas un membre de plusieurs groupes Windows pour BizTalk Server.  
  
 En outre, nous vous recommandons d’utiliser les différents groupes Windows pour chaque hôte BizTalk et que les comptes de service qui sont membres d’un groupe ne soient pas membres du groupe Windows pour un autre hôte. Chaque hôte BizTalk bénéficie ainsi d'une isolation de sécurité renforcée.  
  
 Il est conseillé de créer un groupe Windows pour l'hôte de suivi uniquement, et d'utiliser un compte de service de ce groupe pour l'instance de l'hôte de suivi. N'utilisez pas ce compte de service pour d'autres services. De même, n'utilisez pas un compte d'administrateur BizTalk pour l'instance de l'hôte de suivi.  
  
 **Utilisez différents hôtes pour différentes fonctions.** Il est recommandé de créer un hôte uniquement à des fins de suivi. Les hôtes chargés du suivi disposent d'un accès en lecture/écriture aux tables de suivi de la base de données MessageBox, ainsi que d'un accès aux tables de la base de données des suivis. Par conséquent, les objets exécutés sur ce type d'hôte bénéficient également d'un accès en lecture/écriture à ces tables. Pour bloquer l'accès aux données de suivi potentiellement sensibles à partir d'éléments utilisateur tels que les pipelines et les orchestrations, il est recommandé de créer un hôte dédié au suivi, qui ne traite, n'envoie ni ne reçoit de messages.  
  
 En outre, il est conseillé d'utiliser différents hôtes pour le traitement, la réception et l'envoi des messages. Vous pouvez ensuite isoler les comptes de service qui doivent accéder aux certificats privés de votre société. Moins il y a de code exécuté sous ces comptes, moins ceux-ci sont susceptibles d'être compromis en raison de vulnérabilités, ce qui permet de réduire le risque que les certificats privés soient compromis.  
  
 **Modifier les mots de passe régulièrement.** Vous devez modifier régulièrement le mot de passe des comptes de service. Si plusieurs comptes de service sont associés aux instances de votre hôte, vous devez modifier le mot de passe de chacun d'eux.  
  
> [!CAUTION]
>  Les mots de passe du compte de service pour l'instance d'un hôte sont modifiés dans la console Administration de BizTalk. La modification du mot de passe du compte de service d'une instance d'hôte dans la console de gestion de l'ordinateur peut être à l'origine de problèmes de configuration.  
  
 **Limitez l’appartenance au groupe d’administrateurs BizTalk.** Les administrateurs BizTalk Server disposent de droits d'utilisateur sur l'environnement BizTalk Server, notamment de l'accès à la plupart des données (chiffrées ou non). Par conséquent, une configuration incorrecte résultant d'une erreur d'un administrateur BizTalk peut exposer des failles de sécurité critiques. Un administrateur BizTalk inexpérimenté peut gravement endommager le système, notamment compromettre totalement la confidentialité, l'intégrité et la disponibilité des données clientes.  
  
 Lorsque les développeurs déploient directement des orchestrations vers des ordinateurs situés dans l'environnement de production, les administrateurs de domaine doivent leur octroyer des droits administratifs BizTalk. Une telle mesure est déconseillée pour le motif évoqué plus haut.  
  
 **Limitez l’appartenance au groupe Administrateurs COM +.** Pour diverses raisons liées à l'architecture, l'administrateur COM+ dispose de droits d'utilisateur en tant qu'administrateur dans plusieurs composants BizTalk Server. Pour des raisons pratiques, vous devez partir du principe que l'administrateur COM+ d'un ordinateur est également un administrateur BizTalk, et devez limiter l'appartenance à ce groupe sur les serveurs de production BizTalk.  
  
 **Donner aux utilisateurs l’accès uniquement aux ordinateurs qui exécutent les services à que dont ils ont besoin d’accéder.** Seuls quelques comptes ont besoin d'accéder à tous les ordinateurs. Les instances de l'hôte BizTalk conservent les informations personnelles en mémoire. Il peut s'agir de données critiques telles que des mots de passe ou des informations sur l'entreprise. Une stratégie d'utilisateur local très stricte doit être configurée sur ces ordinateurs. Par exemple, accordez uniquement des droits d'ouverture de session locale sur ces ordinateurs aux personnes qui en ont besoin pour assurer la gestion du déploiement. Cela permet d'atténuer les menaces résultant de l'accès au fichier d'échange et des vidages sur incident.  
  
 **Limiter les autorisations du groupe utilisateurs avec pouvoir, ou le supprimer.** Les autorisations par défaut du groupe Utilisateurs avancés accordent aux membres de ce groupe des droits d'utilisateur permettant de modifier les paramètres pour l'ensemble de l'ordinateur, notamment les assemblys BizTalk inscrits dans le GAC (Global Assembly Cache). Chaque ordinateur inclut un GAC qui contient les assemblys partagés par une ou plusieurs applications. Il est conseillé de supprimer l'autorisation de modification des assemblys du groupe Utilisateurs avancés. Vous pouvez également supprimer ce dernier des serveurs BizTalk de production.  
  
 
## <a name="see-also"></a>Voir aussi  
 [Contrôle d’accès pour les groupes et comptes de Service](../core/access-control-for-groups-and-service-accounts.md)   
 [Contrôle d’accès pour les rôles d’administration](../core/access-control-for-administrative-roles.md)   
 [Autorisations de sécurité minimales](../core/minimum-security-user-rights.md)   
 [Planification de la sécurité](../core/planning-for-security.md)