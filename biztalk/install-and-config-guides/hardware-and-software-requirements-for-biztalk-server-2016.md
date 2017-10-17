---
title: "Configurations matérielle et logicielle requises pour BizTalk Server 2016 | Documents Microsoft"
description: "Répertorie les composants logiciels requis et la version prise en charge pour installer BizTalk Server 2016"
ms.custom: 
ms.prod: biztalk-server
ms.date: 10/09/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6120afd-310e-4155-8c23-aadb5b9a1a35
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63993b544aead238d28623ab291887535e2f06ab
ms.sourcegitcommit: 85e816bcdeb3d66ea5018cf88aea7059f74f7d80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2017
---
# <a name="hardware-and-software-requirements-for-biztalk-server-2016"></a>Configurations logicielle et matérielle requises pour BizTalk Server 2016

## <a name="hardware-requirements"></a>Configuration matérielle
Le tableau suivant stipule la configuration matérielle minimale requise pour votre ordinateur BizTalk Server. Dans un environnement de production, le volume de trafic peut nécessiter une configuration matérielle supérieure pour vos serveurs. 

| Ressource  |Configuration minimale requise |
| --- | --- |
|Ordinateur et processeur | Un ordinateur avec un processeur compatible Intel Pentium de : <ul><li>1 GHz ou plus pour un seul processeur</li><li>900 MHz ou plus pour deux processeurs</li><li>700 MHz ou plus pour quatre processeurs</li></ul> **REMARQUE** : les processeurs Hyper-threading et à double noyau sont pris en charge.<br/><br/>Pour les versions 64 bits de BizTalk Server, l'exécution d'un système d'exploitation de 64 bits sur un système x64 bits est requise. Les ordinateurs utilisant l'UC compatibles avec les architectures de processeur AMD64 (x86-64) et EM64T (Extended Memory 64-bit Technology) sont considérés comme des systèmes x64.<br/><br/>BizTalk Server n'est pas pris en charge sur les systèmes Itanium. |
|Mémoire | 2 Go ou plus|
|Disque dur  |10 Go d’espace disponible sur le disque dur pour une installation complète, y compris le système d’exploitation et tous les logiciels prérequis. Le disque dur doit être au format NTFS.|

> [!TIP] 
> La configuration matérielle répertoriée correspond au minimum nécessaire. Chaque environnement est différent et il est très probable que votre environnement nécessite plus. Consultez [Recommandations pour l’installation, le dimensionnement, le déploiement et la maintenance d’une solution BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). 


## <a name="software-requirements--supported-versions"></a>Configuration logicielle requise et les versions prises en charge

| Logiciel  |   Versions |  Requis pour | 
| --- | --- | --- | 
| Microsoft Windows | <ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1 </li></ul> | | 
| Internet Information Services (IIS)   | La version fournie avec le système d'exploitation.<br/><br/> L’[article 224609](https://support.microsoft.com/kb/224609) de la Base de connaissances répertorie les versions IIS. | Fournit une infrastructure évolutive pour les applications web et est requis pour EDI, BAM et l’adaptateur SharePoint. |
| Windows Identity Foundation | Inclus avec le système d’exploitation en tant que **fonctionnalité**. | Ce paramètre est facultatif. <br/><br/>Utilisé par le modèle CSOM (Client Side Object Model) Windows SharePoint Services, qui est automatiquement installé lorsque vous installez BizTalk Server. | 
| Microsoft SharePoint  | <ul><li>SharePoint Services 2016</li><li>SharePoint Services 2013 SP1</li><li>SharePoint Services Online</li></ul>  | Ce paramètre est facultatif. <br/><br/>Si vous prévoyez de recevoir ou d’envoyer des messages à partir de SharePoint Services, un ordinateur SharePoint Services est requis. Il peut être installé sur le même ordinateur que BizTalk Server, mais de préférence sur un autre ordinateur. |
| Microsoft Office  | <ul><li>Microsoft Office Excel 2016</li><li>Microsoft Office Excel 2013</li></ul>**REMARQUE** : BizTalk Server prend en charge uniquement les versions 32 bits d’Office.  | Ce paramètre est facultatif. <br/><br/>Requis par BAM (Business Activity Monitoring) pour afficher une vue en temps réel des processus d'entreprise. | 
| Microsoft .NET Framework  | <ul><li>.NET framework 4.7 (en commençant par [CU2](https://support.microsoft.com/kb/4021095))</li><li>.NET Framework 4.6.*x* </li></ul>**Remarque**: les projets BizTalk créés dans Visual Studio requièrent la cible de génération Visual Studio soit définie pour votre version de .NET Framework. | Requis pour tous les composants gérés de BizTalk Server. | 
| Microsoft Visual Studio |Visual Studio 2015 | Ce paramètre est facultatif. <br/><br/>Fournit un environnement de développement pour la construction d’applications BizTalk Server. Il est recommandé d'utiliser l'édition Intégrale, mais les éditions Premium et Professionnelle sont également prises en charge. Requis pour les outils et kit de développement de BizTalk Server. |
| Microsoft Visual C++ 2013 Redistributable Package | Les versions x86 et x64 sont nécessaires. Téléchargez-la à la page [Packages redistribuables Visual C++ pour Visual Studio 2013](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package).    | Obligatoire.<br/><br/>Le package redistribuable Microsoft Visual C++ installe les composants d’exécution des bibliothèques Visual C++ requis pour exécuter des applications développées avec Visual C++ sur un ordinateur non doté de Visual C++.<br/><br/>**Remarque**: <br/> La version 2013 est requise, même si Visual Studio 2015 est utilisé.|
| Microsoft SQL Server  | <ul><li>Microsoft SQL Server 2016</li><li>Microsoft SQL Server 2014 SP1</li></ul> | Requis pour le moteur d’exécution BizTalk Server, EDI et BAM. <br/><br/>Pour des performances optimales, Microsoft recommande d'utiliser SQL Server Enterprise Edition. Pour utiliser pleinement le kit SDK BizTalk Server ou déployer des applications BizTalk Server à partir de Visual Studio, installez les outils de développement SQL Server. <br/><br/>Autres considérations : <ul><li>Pour utiliser des groupes de disponibilité AlwaysOn (AG) SQL Server, utilisez SQL Server 2016 et les versions plus récentes. Seul SQL Server 2016 AlwaysOn AG prend en charge MSDTC. MSDTC est nécessaire pour BizTalk Server. </li><li>L’agrégation en temps réel (RTA) de BAM n’est pas prise en charge dans SQL Server Standard Edition. Pour utiliser l’agrégation RTA de BAM, installez SQL Server Enterprise Edition.</li><li>Il n’est pas recommandé d’utiliser SQL Server Express Edition. Cette édition n'inclut pas certaines fonctionnalités requises par BizTalk Server.</li><li>BizTalk Server prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l’exception des classements binaires. Les classements binaires ne sont pas pris en charge.</li></ul> |  |
| Messagerie de base de données SQL Server  | Version fournie avec SQL Server. [Configurez la messagerie de base de données SQL Server](https://msdn.microsoft.com/library/hh245116(v=sql.130).aspx).| Ce paramètre est facultatif. <br/><br/>Requis pour utiliser les alertes BAM. | 
| SQL XML | SQL XML 4.0 avec Service Pack 1. [Téléchargez SqlXml 4.0 Service Pack 1 (SP1)](https://www.microsoft.com/en-us/download/details.aspx?id=30403). | Requis pour le moteur d’exécution BizTalk Server, les outils d’administration et l’analyse BAM. <br/><br/> SQLXML active la prise en charge de XML pour votre base de données SQL Server. Il permet aux développeurs d'établir un pont entre XML et les données relationnelles. Vous pouvez créer une vue XML de vos données relationnelles existantes et l’utiliser comme s’il s’agissait d’un fichier XML. <br/><br/>**Remarque**: <br/>le fichier CAB redistribuable l’installe automatiquement pour vous. SQL XML peut avoir sa propre configuration logicielle requise (telle que `.NET Framework 3.5` et `.NET Framework 2.0`), qui n’est pas incluse dans le fichier CAB. Si le serveur BizTalk Server a accès à Internet, la configuration logicielle requise pour SQL XML peut être installée automatiquement. Si le serveur BizTalk Server n’a pas accès à Internet, installez manuellement la configuration logicielle requise pour SQL XML.| 
| WinSCP | WinSCP version 5.7.7. [Téléchargez WinSCP](http://winscp.net).| Requis pour utiliser l’adaptateur SFTP. |
|Systèmes métier et d’entreprise | [Prise en charge des systèmes d’entreprise et de métier (LOB)](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions prises en charge. | Requis lors de l’utilisation des adaptateurs dans BizTalk Adapter Pack. <br/><br/> [Pack d’adaptateurs BizTalk](../adapters-and-accelerators/biztalk-adapter-pack.md) répertorie les adaptateurs système disponibles. |

## <a name="service-pack-and-cumulative-update-support"></a>Service Pack et prise en charge de la mise à jour cumulative

L’ensemble des Service Packs, des mises à jour cumulatives, des mises à jour de sécurité et des correctifs sont pris en charge sur un serveur BizTalk Server. Vous êtes vivement invité à installer la dernière mise à jour pour Windows, SQL Server, Visual Studio et tout autre programme installé. Les Service Packs des produits Microsoft sont pris en charge selon le support de base du produit en question. Consultez l’[index de la politique de support](http://go.microsoft.com/fwlink/p/?LinkID=151890) pour BizTalk Server, SQL Server, Visual Studio et d’autres programmes Microsoft.

[Service Pack et liste de mise à jour cumulative pour BizTalk Server](https://support.microsoft.com/help/2555976)

 ## <a name="next-step"></a>Étape suivante
 
 [Prérequis d’installation et de configuration](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2016.md)
