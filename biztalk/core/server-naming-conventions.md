---
title: "Conventions d’affectation de noms de serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, naming conventions
- naming conventions, servers
- installation, naming conventions
ms.assetid: 98989c15-51d7-4a67-b054-abe6993a98a6
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a54e61a9ec37754158697a57a3f310d9edb90ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="server-naming-conventions"></a>Conventions d'attribution de noms de serveur
Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant décrit les serveurs dans le diagramme dans la rubrique [grand Distributed Architecture](../core/large-distributed-architecture.md), ainsi que leurs fonctions.  
  
|Nom du serveur dans le diagramme|Fonction| Description|  
|----------------------------|--------------|-----------------|  
|FW4|Pare-feu|Serveur de Threat Management Gateway (TMG) 2010 Forefront entre Internet et le réseau de périmètre.|  
|HTTP (réception)|Serveur Web|Serveur Web qui reçoit les messages pour l'adaptateur HTTP. Aucun composant BizTalk Server n'est installé sur ce serveur. Des pages ASP.NET relaient les messages au domaine des interfaces de service. Vous pouvez utiliser le proxy inverse entre FW4 et FW3 plutôt que des pages ASP.NET. Dans ce cas, vous n'avez pas besoin de ce serveur.|  
|Exchange (envoi/réception)|Serveur de messagerie|Serveur de messagerie utilisé par BizTalk Server pour envoyer et recevoir des messages SMTP. L'adaptateur POP3 lit les messages reçus.|  
|FTP (envoi/réception)|Serveur Web|Représente le serveur FTP (File Transport Protocol) à partir duquel BizTalk envoie et reçoit des messages. Il peut s'agir d'un serveur distant.|  
|SQL|SQL Server|Serveur de base de données SQL Server utilisé par l'adaptateur SQL.|  
|Fichier|Serveur de fichiers|Serveur qui dispose d'un répertoire de fichiers dans lequel l'adaptateur FILE dans le domaine des interfaces de service place et extrait des fichiers.|  
|FW3|Pare-feu|Forefront Threat Management Gateway (TMG) 2010 de serveur qui protège le service de domaine des interfaces à partir du réseau de périmètre et domaine de l’entreprise.|  
|Traitement|Serveur de traitement|Ce serveur traite les messages. Il inclut le moteur d'exécution BizTalk Server, le moteur de règles d'entreprise et le service d'authentification unique de l'entreprise (SSO). Il inclut également des assemblys, des instances d'hôte, des orchestrations, des schémas et des mappages BizTalk. Un serveur de traitement donné peut inclure des instances d'hôtes différents.|  
|Gestionnaire de réception<br /><br /> (hôte isolé)|Serveur de réception/d'envoi|Serveur BizTalk Server dédié à la réception des messages des adaptateurs HTTP et SOAP. Un serveur de réception/d'envoi donné peut inclure des instances d'hôtes différents.|  
|Gestionnaire de réception<br /><br /> (hôte de type In-process)|Serveur de réception/d'envoi|Serveur BizTalk Server dédié à la réception des messages des adaptateurs SQL, FTP, EDI, FILE, POP3 et BizTalk Message Queuing. Un serveur de réception/d'envoi donné peut inclure des instances d'hôtes différents.|  
|Gestionnaire d'envoi|Serveur de réception/d'envoi|Serveur BizTalk Server dédié à l'envoi des messages pour tous les adaptateurs. Un serveur donné peut inclure des instances d'hôtes différents utilisées pour l'envoi des messages.|  
|FW2|Pare-feu|Serveur de Threat Management Gateway (TMG) 2010 Forefront protégeant le domaine des services à partir des interfaces de service et les domaines d’entreprise (services d’opération).|  
|Hôte de suivi|Serveur de suivi|Serveur qui inclut une instance de l'hôte BizTalk utilisé pour le suivi.|  
|Outils d’administration|Serveur d'administration|Serveur qui inclut le moteur d'exécution BizTalk Server, la console Administration de BizTalk Server et les outils de déploiement.|  
|Serveur de secret principal|Serveur de secret principal|Serveur d'authentification unique qui gère la clé de secret principal pour l'ensemble de l'environnement. Il n'y a pas d'autres composants BizTalk Server sur cet ordinateur.|  
|FW1|Pare-feu|Serveur de Threat Management Gateway (TMG) 2010 de Forefront protégeant le domaine de données et les interfaces de service et les domaines des services.|  
|MessageBox 1<br /><br /> MessageBox 2<br /><br /> MessageBox « n »|Serveur de données|Serveur SQL Server qui contient les bases de données MessageBox. Il peut y avoir un serveur SQL Server différent pour chaque base de données MessageBox.|  
|AUTHENTIFICATION UNIQUE|Serveur de données|Serveur SQL Server qui contient la base de données SSO que l'authentification unique de l'entreprise utilise pour stocker les ID et informations de connexion des utilisateurs sous forme chiffrée pour la connexion à d'autres systèmes, et pour le stockage sous forme chiffrée du formulaire des informations de configuration pour les adaptateurs utilisés par BizTalk Server.|  
|Sauvegarde/restauration pour l'envoi de journaux|Serveur de données|Serveur SQL Server utilisé pour restaurer les sauvegardes de base de données produites par les bases de données BizTalk Server.|  
|Analyse BizTalk|Serveur de données|Serveur d'analyse qui contient la base de données d'analyse BizTalk.|  
  
 Le tableau suivant décrit les autres serveurs dans le diagramme dans la rubrique [grande Architecture distribuée avec les Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md) et leurs fonctions par rapport au diagramme dans la rubrique [grande Architecture distribuée](../core/large-distributed-architecture.md).  
  
|Nom du serveur|Fonction| Description|  
|-----------------|--------------|-----------------|  
|Portail BAM|Portail BAM|Serveur qui contient le portail BAM. Celui-ci permet aux utilisateurs finaux d'accéder aux bases de données BAM pour analyser les indicateurs de performance clé et d'autres informations sur leurs processus d'entreprise.|  
|Service de notification<br /><br /> Configuration de Windows SharePoint Services<br /><br /> Contenu de Windows SharePoint Services<br /><br /> Schémas en étoile BAM<br /><br /> Importation principale BAM<br /><br /> Archives BAM<br /><br /> Analyse BAM (OLAP)|Serveur de données des travailleurs de l'information|Serveur SQL Server qui contient les bases de données utilisées par l'analyse BAM. Vous pouvez utiliser plusieurs serveurs SQL Server pour ces bases de données.|  
|Clients des travailleurs de l'information|Clients des travailleurs de l'information|Ordinateurs clients utilisés par les travailleurs de l'information pour l'analyse BAM.|  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture distribuée](../core/large-distributed-architecture.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)