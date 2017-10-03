---
title: Affichage des informations dans la Console Operations Manager | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6acdf425-4c36-4d89-9493-81b33481fe6d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 687932839c379ed9589a51baae0ae8562f4af705
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-information-in-the-operations-manager-console"></a>Affichage des informations dans la console Operations Manager
Utilisez les vues fournies avec le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack pour comprendre la disponibilité actuelle, la configuration, l’intégrité et les performances de votre environnement BizTalk Server. Un affichage peut contenir une très longue liste d'objets. Les boutons Étendue, Rechercher et Trouver de la barre d'outils Operations Manager vous permettent de trouver un objet ou un groupe d'objets spécifique. Pour plus d’informations, consultez Comment gérer les données d’analyse à l’aide d’étendue, rechercher et rechercher la rubrique dans l’aide de R2\2012 Operations Manager 2007.  
  
 Les affichages suivants sont répertoriés directement sous  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  nœud dans le volet analyse de la Console opérateur.  
  
-   **Vues de l’application**: administrateur A BizTalk est soucieux de surveillance de l’état et l’intégrité de divers artefacts de BizTalk Server et des applications telles que les orchestrations des ports d’envoi, emplacements de réception et ainsi de suite.  
  
-   **Vues de déploiement**: une administrateur informatique d’entreprise souhaite contrôler l’état de santé des divers déploiements enterprise les ordinateurs hébergeant le serveur SQL des bases de données, les ordinateurs hébergeant le service d’authentification unique, les ordinateurs d’instance hôte, IIS, services réseau et ainsi de suite.  
  
## <a name="application-views"></a>Vues de l’application  
 Vues de l’application contient les éléments décrits dans le tableau suivant.  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage de l’état de l’application|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’une application BizTalk. L’intégrité de l’application BizTalk dépend de l’intégrité de ses artefacts qui la constituent, telles que les Orchestrations, groupe de ports d’envoi, Port d’envoi, Port de réception et un emplacement de réception. Le volet Détails fournit les propriétés de l’application BizTalk hébergée.|  
|Affichage des États de groupe|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’un groupe BizTalk. L’intégrité d’un groupe BizTalk dépend de l’intégrité de l’hôte BizTalk et les applications BizTalk. Le volet Détails fournit les propriétés du groupe BizTalk.|  
|Affichage de l’état de l’hôte|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’un hôte BizTalk. L’intégrité d’un hôte BizTalk dépend de l’intégrité des instances des applications BizTalk hébergées. Le volet Détails fournit les propriétés de l’hôte BizTalk.|  
  
#### <a name="application-artifacts-views"></a>Vues artefacts de l’application  
 Vues artefacts de l’application contient les éléments décrits dans le tableau suivant.  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage des États des orchestrations|Affiche l’état de configuration et d’exécution de l’Orchestration pour l’application hébergée.|  
|Affichage de l’état de l’emplacement de réception|Affiche l’état de configuration et d’exécution de l’emplacement de réception pour l’application hébergée.|  
|Affichage de l’état des Ports de réception|Affiche l’état de configuration et d’exécution de Ports de réception pour l’application hébergée.|  
|Affichage des États de groupes de ports envoi|Affiche l’état de configuration et d’exécution du groupe de ports d’envoi pour l’application hébergée.|  
|Affichage des États de Port d’envoi|Affiche l’état de configuration et d’exécution du Port d’envoi pour l’application hébergée.|  
  
## <a name="deployment-views"></a>Vues de déploiement  
 Vues de déploiement contient les éléments décrits dans le tableau suivant.  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage des États de déploiement|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’un groupe de déploiement de BizTalk. L’intégrité du groupe de déploiement BizTalk dépend de l’intégrité de ses composants de serveur qui constituent de runtime telles que le rôle BAM, rôle de moteur de règle, rôle d’exécution BizTalk et l’hôte BizTalk. Le volet Détails fournit les propriétés du groupe de déploiement de BizTalk.|  
|Affichage des États des ordinateurs hôtes|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’un hôte BizTalk. L’intégrité d’un hôte BizTalk dépend de l’intégrité des instances des applications BizTalk hébergées. Le volet Détails fournit les propriétés de l’hôte BizTalk.|  
|Affichage des États de rôle de moteur de règle|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité d’un service de moteur de règles qui s’exécute sur les serveurs de l’exécution. Le volet Détails fournit les propriétés des serveurs runtime que le service du moteur de règles est installé.|  
|Affichage de l’état du rôle du runtime|Il s’agit d’une vue de tableau de bord qui affiche l’intégrité des serveurs de runtime qui ont le service de moteur de règles de runtime installé. L’intégrité d’un rôle d’exécution BizTalk dépend de l’intégrité de ses composants, tels que le Service d’authentification unique, de base de données de gestion, base de données MessageBox, base de données SSO et de base de données de suivi. Le volet Détails fournit les propriétés des serveurs de runtime.|  
  
### <a name="bam-component-views"></a>Vues du composant BAM  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage des États des alertes BAM|Affiche la vue de l’état du composant d’alertes BAM BizTalk.|  
|Affichage des États d’analyse BAM|Affiche la vue de l’état du composant d’analyse BAM BizTalk.|  
|Affichage des performances BAM|Le volet légende affiche le compteur de performance pour l’analyse BAM.|  
|Affichage de l’état du portail BAM|Affiche l’affichage des États du portail BAM.|  
|Affichage de l’état d’exécution BAM|Affiche l’affichage des États d’exécution BAM.|  
  
#### <a name="bam-alerts"></a>Alertes BAM  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage des États des alertes BAM|Affiche la liste des alertes BAM de BizTalk qui est un service de notification et générée lorsqu’un des services essentiels ne sont pas disponible.|  
  
##### <a name="runtime-component-views"></a>Vues du composant d’exécution  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage de l’état de Service d’application|Affiche l’intégrité de toutes les instances d’hôte dans un groupe BizTalk.|  
|Affichage des États de Performance de boîte de message|Le volet légende affiche le compteur de performance pour la taille des données de suivi boîte de Message.|  
|Affichage des performances des cartes de messagerie|Le volet légende affiche le compteur de performance pour MSMQ réception adaptateur octets reçus.|  
|Affichage des performances de messagerie|Le volet légende affiche le compteur de performances pour les emplacements de réception Active.|  
|Affichage des performances d’orchestration|Le volet légende affiche le compteur de performances pour les Orchestrations pouvant être exécutées.|  
|Affichage de l’utilisation des ressources serveur|Le volet légende affiche le compteur de performance de temps des temps d’inactivité du pourcentage de disque physique.|  
  
###### <a name="runtime-alerts"></a>Alertes du runtime  
  
### <a name="elements"></a>Éléments  
  
|Nom de la vue| Description|  
|---------------|-----------------|  
|Affichage des alertes de base|Affiche des alertes de base BizTalk.|  
|Affichage des alertes de messagerie|Affiche des alertes de messagerie BizTalk.|