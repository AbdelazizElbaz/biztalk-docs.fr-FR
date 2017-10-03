---
title: "Problèmes connus de l’Installation, la Configuration et déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1c08eb-d647-4a4a-b9a3-c4d84e8d4b82
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda1bd5c8167bbf9f6049b3620c0c949950b1e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-in-installation-configuration-and-deployment"></a>Problèmes connus rencontrés lors de l'installation, de la configuration et du déploiement
## <a name="some-biztalk-edias2-artifacts-are-still-active-after-unconfiguring"></a>Certains artefacts d'EDI/AS2 BizTalk sont toujours actifs après annulation de la configuration  
  
##### <a name="problem"></a>Problem (Problème)  
 Après que vous avez annulé la configuration de la fonction EDI/AS2 BizTalk de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], certains artefacts de BizTalk Server liés au traitement EDI et AS2 restent actifs dans le contexte de la configuration de groupe BizTalk. Ces derniers incluent des pipelines EDI et AS2 ainsi que l'orchestration du traitement par lots. Vous pouvez donc continuer à effectuer un traitement EDI et AS2 de base, même après avoir annulé la configuration de la fonction EDI/AS2 BizTalk.  
  
##### <a name="cause"></a>Cause  
 Il y a des ports actifs associés au traitement EDI et AS2. Certains artefacts continuent de fonctionner tandis que ces ports restent actifs.  
  
##### <a name="resolution"></a>Résolution  
 Pour désactiver tous les artefacts EDI/AS2, vous devez désactiver, arrêter ou supprimer les ports associés au traitement EDI et AS2.  
  
## <a name="if-the-biztalk-server-computer-or-sql-server-computer-is-renamed-after-biztalk-server-configuration-the-configuration-wizard-will-fail"></a>Si l’ordinateur BizTalk Server ou l’ordinateur SQL Server est renommé après la configuration de BizTalk Server, l’Assistant Configuration échoue  
  
##### <a name="problem"></a>Problem (Problème)  
 Ce problème peut se manifester de différentes manières :  
  
-   La configuration de BizTalk Server charge la page Vue d'ensemble correctement, mais lorsqu'il tente de configurer une fonctionnalité, les options associées ne s'affichent pas à l'écran.  
  
-   L'Assistant Configuration ne peut pas se connecter au serveur SQL Server.  
  
-   Les tentatives d'annulation de la configuration opèrent sur certaines fonctionnalités, mais pas sur toutes.  
  
##### <a name="cause"></a>Cause  
 La configuration de BizTalk Server stocke le nom de réseau de l'ordinateur. Lorsque l'ordinateur est renommé, la configuration de BizTalk Server et l'Assistant Configuration ne peuvent pas localiser le serveur BizTalk Server. Un problème semblable se produit si l'ordinateur SQL Server est renommé après la configuration de BizTalk Server.  
  
##### <a name="resolution"></a>Résolution  
 Ne renommez pas l'ordinateur BizTalk Server ou l'ordinateur SQL Server. Si un serveur doit être renommé, annulez la configuration des fonctionnalités de BizTalk avant de renommer l’ordinateur. Une fois l'ordinateur renommé, reconfigurez les fonctionnalités de BizTalk Server.  
  
## <a name="the-biztalk-server-business-rules-configuration-wizard-fails"></a>Échec de l’Assistant Configuration des règles d’entreprises de BizTalk Server  
  
### <a name="problem"></a>Problem (Problème)  
  
-   L'Assistant Configuration des règles d'entreprise échoue avec l'erreur « La configuration a échoué pour certains composants et aucun paramètre n'a été appliqué pour ces composants ».  
  
-   Sur les ordinateurs BizTalk Server pour lesquels le moteur de règles d'entreprise a déjà été configuré, le service de mise à jour du moteur de règles ne parvient pas à démarrer et ne peut pas être démarré manuellement.  
  
 Lorsque ce problème se produit, une erreur similaire à ce qui suit peut être générée dans le journal de l'application de l'ordinateur BizTalk Server :  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
### <a name="cause"></a>Cause  
 Le Centre de protection Microsoft contre les programmes malveillants a publié un fichier de signature qui permet de se prémunir contre une menace possible de SettingsModifier:Win32/PossibleHostsFileHijack. Ce fichier de signature mis à jour peut entraîner la mise à jour du fichier HOSTS local par les logiciels Microsoft de détection des programmes malveillants tels que Windows Defender en vue d'atténuer la menace de SettingsModifier:Win32/PossibleHostsFileHijack. Ces modifications peuvent empêcher le démarrage du service de mise à jour du moteur de règles BizTalk Server.  
  
### <a name="resolution"></a>Résolution  
 Mettez à jour le fichier HOSTS local pour inclure la ligne suivante :  
  
```  
127.0.0.1         localhost  
```  
  
 Le fichier HOSTS se trouve dans le répertoire %systemroot%\drivers\etc\.  
  
> [!NOTE]
>  Pour plus d’informations sur la mise à jour des signatures du Centre de protection Microsoft contre les programmes malveillants en vue de se prémunir contre une menace possible de SettingsModifier:Win32/PossibleHostsFileHijack, consultez la page [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221).  
  
## <a name="enlistment-of-an-orchestration-fails-if-referenced-assemblies-are-missing-from-the-gacmgmt-db"></a>L'inscription d'une orchestration échoue si les assemblys référencés sont absents de la base de données GAC/Mgmt  
  
##### <a name="problem"></a>Problem (Problème)  
 L'inscription d'une orchestration échoue si les références (C# assemblys faisant référence aux orchestrations) sont absents de la base de données GAC/Mgmt. Durant le redéploiement, il peut être nécessaire d'inscrire l'orchestration en fonction de son état actuel. Si des références sont absentes, le déploiement échoue également.  
  
##### <a name="cause"></a>Cause  
 Les assemblys référencés sont absents de la base de données GAC/Mgmt.  
  
##### <a name="resolution"></a>Résolution  
 Ajoutez les assemblys référencés à GAC ou ajoutez-les comme ressources, afin qu'ils soient stockés dans la base de données Mgmt et qu'ils soient accessibles lors de l'inscription de l'orchestration.  

## <a name="community-blog-biztalk-2013-r2-bugs-issues--quirks"></a>Blog de la Communauté : Bogues, problèmes et quirks relatifs à BizTalk 2013 R2

[BizTalk Server 2013 R2 – Bogues, problèmes et quirks connus](https://cdijkgraaf.wordpress.com/2016/08/12/biztalk-2013-r2-known-bugs-issues-quirks/)
  
## <a name="additional-configuration-topics"></a>Rubriques de configuration supplémentaires  
  
 [Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)  
  
 [Configuration de BizTalk Server sur une machine virtuelle Azure](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
  [Configuration de BizTalk Server dans un cluster](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)
  
 [Sécurisation d’un déploiement BizTalk Server](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  