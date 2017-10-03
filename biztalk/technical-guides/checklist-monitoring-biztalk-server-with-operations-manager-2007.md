---
title: "Liste de vérification : Analyse de BizTalk Server avec Operations Manager 2007 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e1f7f57-1501-473f-af5f-15f3e1ddaf8e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 810ede830f7142181c4bec1f727cbc496049ce03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-monitoring-biztalk-server-with-operations-manager-2007"></a>Liste de vérification : Analyse de BizTalk Server avec Operations Manager 2007
Cette rubrique répertorie les étapes que vous pouvez suivre lors de la préparation surveiller votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
|Étape|Référence|  
|----------|---------------|  
|Vérifiez que vous disposez des autorisations appropriées pour installer et configurer le logiciel sur votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou les ordinateurs.|[Droits d’utilisateur de sécurité minimales](http://go.microsoft.com/fwlink/?LinkID=154374) (http://go.microsoft.com/fwlink/?LinkID=154374)|  
|Installez l’agent Operations Manager 2007 sur chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur que vous souhaitez surveiller et faites-le pointer vers le serveur Operations Manager 2007.|Reportez-vous à [déploiement d’Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkId=110030) (http://go.microsoft.com/fwlink/?LinkId=110030)|  
|Téléchargez et importez la version appropriée des packs d’administration pour les éléments suivants :<br /><br /> -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)](obligatoire)<br />-Enterprise Single Sign-On (obligatoire)<br />-Windows Base OS (Server) (facultatif)<br />-Microsoft Windows Server Cluster (si les clusters sont utilisés, facultatif)<br />-SQL Server 2008, SQL Server 2005 (facultatif)<br />-Internet Information Services (IIS) 2008, 2003 IIS (facultatif)<br />-Message Queuing (MSMQ) 3.0 (facultatif)|-Télécharger les Packs d’administration [catalogue des packs d’administration System Center](http://go.microsoft.com/fwlink/?LinkId=203227) (http://go.microsoft.com/fwlink/?LinkId=203227).<br />-Permet d’importer le Pack d’administration en suivant les instructions à [comment importer un Pack d’administration dans Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=98348) (http://go.microsoft.com/fwlink/?LinkID=98348).|  
|Lire les meilleures pratiques pour l’utilisation d’Operations Manager 2010 pour surveiller [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|[Meilleures pratiques pour l’analyse d’Operations Manager 2007](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)|  
|Activer ou désactiver la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] selon le cas de règles de pack d’administration.|[Meilleures pratiques pour l’analyse d’Operations Manager 2007](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)|  
|Ajouter des ordinateurs autonomes dotés de Enterprise Single Sign-On (SSO) à la liste des ordinateurs surveillés par le Pack d’administration de BizTalk Server.|[Comment ajouter des ordinateurs d’authentification unique de l’entreprise à la liste des ordinateurs analysés par le Pack d’administration de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=157263) (http://go.microsoft.com/fwlink/?LinkId=157263).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de BizTalk Server avec System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)