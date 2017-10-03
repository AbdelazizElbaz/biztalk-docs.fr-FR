---
title: "Hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host instances, servers
- hosts, isolated
- host instances, relationships
- hosts, in-process hosts
- servers, hosts
- hosts, host instances
- hosts, relationships
- In-Process BizTalk Host groups
- hosts, about hosts
- hosts, untrusted
- host instances, hosts
- hosts, servers
- hosts
- servers, host instances
- Isolated Host Users group
- hosts, trusted
ms.assetid: d96537e0-e679-407a-8870-34a663acfed9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a1c61995bca06203208c057762db7f737afd6eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hosts"></a>Hôtes
L'objet Hôte BizTalk représente un ensemble logique de zéro ou plusieurs processus d'exécution dans lequel vous pouvez déployer des services, des pipelines et d'autres artefacts. L'objet Hôte représente également un regroupement d'instances d'exécution (zéro ou plusieurs) dans lequel les éléments déployés sont exécutés physiquement.  
  
 Après avoir créé un hôte (ou conteneur logique), vous pouvez lui ajouter des serveurs BizTalk Server (instances de l'hôte). Vous ne pouvez pas ajouter plusieurs fois un serveur BizTalk au même hôte. Une même instance de l'hôte peut être ajoutée à plusieurs hôtes.  
  
 Les éléments contenus dans les hôtes BizTalk, tels que les gestionnaires d'adaptateur, les emplacements de réception (y compris les pipelines) et les orchestrations, peuvent exécuter les fonctions suivantes :  
  
-   **Réception**. ces éléments effectuent le traitement initial des messages après leur récupération dans un emplacement de réception. Lorsqu’un ordinateur hôte contient un élément de réception, tel qu’un emplacement de réception ou d’un pipeline, il agit comme une limite de sécurité, et le message de décodage et le déchiffrement se produit dans un pipeline au sein de l’hôte.  
  
-   **Envoi de**. ces éléments effectuent le traitement final des messages avant leur transmission au port d'envoi. Lorsqu'un hôte contient un élément de réception, par exemple un emplacement de réception ou un pipeline, il agit comme une limite de sécurité, et le décodage ainsi que le déchiffrement du message sont réalisés dans un pipeline au sein de l'hôte.  
  
-   **Traitement**. ces éléments traitent des messages à partir des instructions contenues dans une orchestration.  
  
 Un hôte BizTalk peut contenir des éléments qui reçoivent, envoient et traitent des messages. Il est recommandé de créer des hôtes différents pour chaque fonction afin de générer des limites de sécurité et de faciliter la gestion. En particulier, il est recommandé que vous utilisez différents hôtes pour le traitement et de réception / d’envoi et de séparer les éléments approuvés et non approuvés.  
  
 L'illustration suivante représente la relation entre des serveurs, des hôtes et des instances d'hôte.  
  
 ![Hôtes, les instances d’hôte et les relations de serveur](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")  
Relation entre des hôtes, des instances d'hôte et des serveurs  
  
 Pour plus d’informations sur les Instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).  
  
 En fonction de la configuration physique et le type d’adaptateur hébergé, il existe deux types d’hôtes : ordinateurs hôtes et les hôtes isolés dans le processus.  
  
## <a name="in-process-hosts"></a>Hôtes de type In-process  
 Les hôtes In-process représentent des instances de service qu'un administrateur crée, supprime et contrôle entièrement avec Windows Management Instrumentation (WMI) et la console Administration de BizTalk.  
  
 Les hôtes In-process présentent les caractéristiques suivantes :  
  
-   Vous pouvez inscrire toute orchestration dans un hôte In-process.  
  
-   Un hôte In-process peut héberger tout gestionnaire d'envoi.  
  
-   Un hôte In-process peut héberger tous les gestionnaires de réception à l'exception de SOAP et HTTP :  
  
    -   FILE  
  
    -   FTP  
  
    -   MQSeries  
  
    -   MSMQ  
  
    -   POP3  
  
    -   SQL  
  
    -   Windows SharePoint Services  
  
-   Le premier hôte in-process vous créez dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le déploiement est le **hôte par défaut** et vous ne pouvez pas le supprimer. L'adaptateur Message Queuing BizTalk utilise cet hôte par défaut pour la configuration statique du gestionnaire. L'ajout d'un adaptateur crée automatiquement des ports de réception et d'envoi pour l'hôte par défaut.  
  
## <a name="isolated-hosts"></a>Hôtes isolés  
 Les hôtes isolés représentent des instances de service qu'un développeur de solutions crée, supprime et contrôle par programme. Un administrateur utilise WMI et la console Administration de BizTalk pour configurer ces hôtes (par exemple, pour configurer le compte de service de l'hôte et l'approbation par authentification).  
  
 Les hôtes isolés hébergent principalement les adaptateurs hôtes qui doivent être exécutés en dehors du processus normal d'exécution BizTalk Server. Par exemple, vous pouvez utiliser des hôtes isolés sur des adaptateurs d'hôtes pour des processus externes, tels que des extensions ISAPI et ASP.NET.  
  
 Les hôtes isolés présentent les caractéristiques suivantes :  
  
-   Vous ne pouvez pas inscrire d'orchestrations dans un hôte isolé.  
  
-   Un hôte isolé ne peut pas héberger de gestionnaires d'envoi.  
  
-   Un hôte isolé peut héberger uniquement les gestionnaires de réception associés aux adaptateurs HTTP/S et SOAP (adaptateurs de type isolés).  
  
-   Un hôte isolé ne peut pas héberger de suivi.  
  
-   Un hôte isolé ne peut pas être l'hôte par défaut.  
  
-   L’état d’un hôte isolé est toujours **état non disponible**. BizTalk Server n'a pas accès aux informations d'état pour les processus externes.  
  
> [!NOTE]
>  Les instances de l'hôte peuvent partager le même compte de service tant qu'elles partagent la même configuration de sécurité (approbation par authentification).  
  
## <a name="trusted-and-untrusted-hosts"></a>Hôtes approuvés et non approuvés  
 BizTalk Server autorise les hôtes identifiés comme approuvés par authentification à indiquer que l'expéditeur d'un message placé en file d'attente dans la base de données MessageBox est une entité différente de l'hôte approuvé lui-même. Les principales fonctions de l'approbation par authentification sont de permettre aux pipelines d'effectuer la conversion en PID et de transmettre ce PID aux services consommateurs pour son utilisation dans l'autorisation et la résolution du tiers sortant, et d'autoriser la transmission de l'ID de sécurité Windows de l'expéditeur (SSID) aux services consommateurs pour son utilisation dans l'autorisation des actions d'orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Instances d’hôte](../core/host-instances.md)   
 [Gestion des hôtes et des instances d’hôte BizTalk](../core/managing-biztalk-hosts-and-host-instances.md)  
 [Entités](../core/entities.md)