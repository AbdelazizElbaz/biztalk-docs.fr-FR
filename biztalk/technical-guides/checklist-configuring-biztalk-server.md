---
title: "Liste de vérification : Configuration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adfb5a5e-2a23-4f6c-865f-a3300bf3d01d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11c1348ef4ce34676cd206c08530f66f20730378
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-configuring-biztalk-server"></a>Liste de vérification : Configuration de BizTalk Server
Procédez comme suit lors de la préparation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour une utilisation dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement de production.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Configurer les hôtes BizTalk et les instances d’hôte.|Séparez les envoi, réception, traitement et le suivi des fonctionnalités dans plusieurs hôtes. Cela fournit une grande souplesse lors de la configuration de la charge de travail et vous permet d’arrêter un ordinateur hôte sans affecter les autres hôtes. Pour plus d’informations, consultez [configuration des hôtes et des Instances d’hôte](../technical-guides/configuring-hosts-and-host-instances.md).|  
|Assurez-vous que vous respectez et comprenez les limites pratiques d’utilisation de mémoire pour une instance d’hôte BizTalk.|[Nombre maximal pratiques d’utilisation de la mémoire d’une Instance de l’hôte BizTalk 32 bits](../technical-guides/configuring-hosts-and-host-instances.md#BKMK_MemLimit)|  
|Configurer un hôte de suivi dédié.|Utilisez un hôte dédié qui ne fait rien, mais le suivi de l’hôte. Cela empêche l’hébergement de suivi d’ayant une incidence sur les performances d’autres artefacts de BizTalk en cours d’exécution sur le même hôte. Il vous permet également d’arrêter les autres hôtes sans interférer avec le suivi. L’hôte de suivi doit être exécuté sur au moins deux ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (pour assurer la redondance dans les cas un tombe en panne). Pour plus d’informations, consultez [configuration d’un hôte dédié de suivi](../technical-guides/configuring-a-dedicated-tracking-host.md).|  
|Définition de connexions simultanées de cartes basées sur HTTP de WCF, HTTP et SOAP|[Appliquer les paramètres de Configuration IIS](../technical-guides/apply-iis-configuration-settings.md)|  
|Implémenter une stratégie de mise à niveau et le contrôle de version d’application BizTalk.|-Si vous avez besoin prendre en charge les orchestrations longues, et/ou vous devez effectuer des déploiements d’applications BizTalk sans temps d’arrêt des applications BizTalk, puis vous devez implémenter et entraîner un solide, de bout en bout [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stratégie de contrôle de version pour le scénarios de contrôle de version différents.<br />-Si vous avez besoin prendre en charge les orchestrations longues, les déploiements côte à côte ou mises à niveau sans temps mort, vous devez implémenter une stratégie de packaging qui inclut la factorisation et le versioning des assemblys.<br /><br /> Pour plus d’informations, consultez [mise à niveau et les stratégies de contrôle de version pour les Applications](../technical-guides/upgrading-and-versioning-strategies-for-applications.md).|  
|Déploiements d’applications BizTalk Server script.|Les déploiements d’applications BizTalk doivent être écrites lorsque cela est possible. Les étapes détaillées, vous devez documenter tout ce que vous ne pas générer de script. Pour plus d'informations, consultez :<br /><br /> -   [À l’aide de Scripts pour déployer des Applications](../technical-guides/using-scripts-to-deploy-applications.md)<br />-   [Gestion des Applications](../technical-guides/managing-applications.md)|  
|Prédéfinir les processus pour soumettre à nouveau des messages et le redémarrage de flux de travail.|Établir et une procédure pour rechercher les instances de service suspendues et prendre les mesures appropriées. Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements, doit être effectué dans le cadre de la maintenance quotidienne de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Pour plus d’informations sur l’exécution de vérifications de la maintenance quotidienne, consultez [liste de vérification : réalisation de vérifications de Maintenance quotidienne](../technical-guides/checklist-performing-daily-maintenance-checks.md).|  
|Définir les chemins d’accès de l’escalade de verrous pour les problèmes qui peuvent être rencontrés dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.|-Déterminez les rôles et responsabilités<br />-Définir les chemins d’accès et le traitement des demandes<br />-Définir les chemins d’accès lorsque cela est nécessaire pour les scénarios de « situation critique » et de processus de « court-circuit »<br />-Définir un chemin d’accès de l’escalade de verrous pour le fournisseur émet, y compris d’autres logiciels Microsoft fournisseurs, les fournisseurs de matériel (par exemple, les commutateurs de serveurs, réseaux SAN)|  
|Respecter certaines considérations lors de l’utilisation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un système d’exploitation de Windows 64 bits|[Considérations lors de l’utilisation de BizTalk Server sur un système d’exploitation Windows 64 bits](../technical-guides/considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system.md)|  
|Les meilleures pratiques pour respecter [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres.|[Meilleures pratiques pour les paramètres de BizTalk Server](../technical-guides/best-practices-for-biztalk-server-settings.md)|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration des ordinateurs hôtes et les Instances d’hôte](../technical-guides/configuring-hosts-and-host-instances.md)  
  
-   [Configuration d’un hôte de suivi dédié](../technical-guides/configuring-a-dedicated-tracking-host.md)  
  
-   [Appliquer les paramètres de Configuration IIS](../technical-guides/apply-iis-configuration-settings.md)  
  
-   [La mise à niveau et les stratégies de contrôle de version pour les Applications](../technical-guides/upgrading-and-versioning-strategies-for-applications.md)  
  
-   [À l’aide de Scripts pour déployer des Applications](../technical-guides/using-scripts-to-deploy-applications.md)  
  
-   [Considérations lors de l’utilisation de BizTalk Server sur un système d’exploitation Windows 64 bits](../technical-guides/considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system.md)  
  
-   [Meilleures pratiques pour les paramètres de BizTalk Server](../technical-guides/best-practices-for-biztalk-server-settings.md)