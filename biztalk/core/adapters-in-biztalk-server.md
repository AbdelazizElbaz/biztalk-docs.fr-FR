---
title: Adaptateurs dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters
- adapters, about adapters
- adapters, list of BizTalk adapters
- adapters, features
ms.assetid: 8fd279fb-2c68-4de4-a586-5a8e42a685ff
caps.latest.revision: "48"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d65d7304547df50ac14128717526fa7d55880775
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapters-in-biztalk-server"></a>Adaptateurs dans BizTalk Server
L'un des principaux objectifs de conception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est de faciliter l'échange de documents entre des partenaires commerciaux. Pour atteindre cet objectif, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut plusieurs adaptateurs qui fournissent la connectivité entre BizTalk Server et les partenaires commerciaux à l'aide de protocoles de données et formats de document communément reconnus. Cette rubrique définit les adaptateurs et leur utilité.  
  
## <a name="what-is-an-adapter"></a>Qu'est-ce qu'un adaptateur ?  
 Un adaptateur est un composant logiciel qui simplifie l'envoi et la réception de messages dans BizTalk Server via un mécanisme de remise conforme à une norme communément reconnue, telle que SMTP, POP3, FTP ou Microsoft Message Queuing (MSMQ). Avec l'évolution de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la nécessité d'avoir des adaptateurs capables d'établir rapidement la connectivité avec les applications et technologies communément utilisées est devenue plus prégnante.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]inclut les adaptateurs suivants, qui sont désignées en tant que les adaptateurs « natifs » ou « intégrés » : fichier, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP, Windows Sharepoint Services et les sept adaptateurs WCF (WCF-WSHttp, WCF-BasicHttp, WCF-NetTcp, WCF-NetMsmq, WCF-NetNamedPipe, WCF-Custom et WCF-CustomIsolated). Les adaptateurs natifs sont installés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également créer des adaptateurs personnalisés pour vos solutions spécifiques à l'aide de l'infrastructure d'adaptateurs BizTalk.  
  
 Chaque adaptateur natif est associé à un emplacement de réception conçu pour écouter les messages d'un transport spécifique à une adresse donnée. Une fois le message reçu par l'emplacement de réception, il est transmis à l'adaptateur. L'adapter associe le flux de données au message (généralement dans le corps du message), ajoute les métadonnées appartenant au point de terminaison depuis lequel les données ont été reçues, puis transmet le message au moteur de messagerie BizTalk.  
  
 Par défaut, lorsque vous exécutez l'Assistant Configuration de BizTalk, celui-ci installe les adaptateurs natifs et crée un gestionnaire d'adaptateur avec une configuration par défaut pour chacun.  
  
 La console Administration de BizTalk Server permet de modifier la configuration par défaut des gestionnaires d'adaptateur et d'ajouter, supprimer et modifier les ports d'envoi et emplacements de réception pour les adaptateurs. Pour plus d'informations sur ces processus, consultez les rubriques correspondantes de la section Voir aussi.  
  
## <a name="why-use-an-adapter"></a>Pourquoi utiliser un adaptateur ?  
 L'utilisation des adaptateurs simplifie considérablement le transfert des messages via BizTalk Server. Si votre infrastructure existante utilise un transport pour lequel un adaptateur BizTalk correspondant existe, le processus d'envoi ou de réception des messages via BizTalk Server est aussi simple que la configuration de l'adaptateur approprié pour envoyer ou recevoir des messages via le mécanisme de transport correspondant.  
  
## <a name="summary-of-functionality-supported-by-biztalk-native-adapters"></a>Résumé des fonctionnalités prises en charge par les adaptateurs natifs BizTalk  
 Le tableau suivant indique la principale caractéristique des adaptateurs natifs individuels et si ceux-ci incluent les fonctionnalités suivantes :  
  
-   **Prise en charge de la transaction.** capacité à envoyer et recevoir des documents sous le contexte d'une transaction DTC (Distributed Transaction Coordinator). Cette fonctionnalité est requise pour assurer la livraison chronologique des messages et garantir que les documents ne sont pas dupliqués ou perdus.  
  
-   **Prise en charge la communication bidirectionnelle (requête-réponse ou sollicitation-réponse).** capacité à envoyer un document et traiter un message de réponse de la destination, ou à recevoir un document et envoyer un message de réponse à la source.  
  
-   **Dans l’ordre de réception prise en charge.** capacité à publier des documents reçus dans la base de données MessageBox de BizTalk dans l'ordre exact de réception des documents.  
  
-   **Authentification unique activée.** capacité à utiliser l'authentification unique dans le cadre de l'envoi ou de la réception de documents avec l'adaptateur.  
  
-   **Processus d’hébergement** le processus dans lequel l’adaptateur s’exécute. *BizTalk IP* s’exécute au sein du processus BTSNTSvc.exe, tandis que *IIS OOP* sont exécutées en dehors du processus BizTalk Server dans le processus Internet Information Server (IIS).  
  
|Adaptateur|Caractéristique principale|Prise en charge des transactions|Prise en charge de la communication bidirectionnelle|Prise en charge de la réception chronologique|Activation de l'authentification unique|Processus d'hébergement|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|---------------------|  
|Fichier|Facile à utiliser.|Non|Non|Non|Non|BizTalk IP|  
|FTP|Largement utilisé pour les communications interentreprises.|Non|Non|Non|Oui|BizTalk IP|  
|HTTP (s)|Largement utilisé pour les communications interentreprises.|Non|Requête/réponse et sollicitation/réponse|Non|Oui|IIS OOP|  
|SOAP|Prend en charge l'utilisation des services Web.|Non|Requête/réponse et sollicitation/réponse|Non|Oui|IIS OOP|  
|MSMQ|Prend en charge la livraison garantie unique des messages entre BizTalk Server et Microsoft Message Queuing.|Oui|Non|Oui|Non|BizTalk IP|  
|MQSeries|Prend en charge la livraison garantie unique des messages entre BizTalk Server et IBM WebSphere MQ pour les plateformes Windows.|Oui|Non|Oui|Oui|BizTalk IP|  
|Windows SharePoint Services|Permet l'échange de messages XML et binaires entre BizTalk Server et les bibliothèques de documents SharePoint.|Non|Non|Non|Non|BizTalk IP|  
|POP3|Prend en charge la réception de documents par message électronique.|Non|Non|Non|Non|BizTalk IP|  
|SMTP|Prend en charge l'envoi de documents par message électronique.|Non|Non|Non|Non|BizTalk IP|  
|Custom|Prend en charge votre système.|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|BizTalk IP|  
|WCF-WSHttp|Prend en charge les normes WS-* via le transport HTTP.|Oui, les transactions sont prises en charge sur WsHTTP (WS-transactions uniquement)|Requête/réponse et sollicitation/réponse|Non|Oui|IIS OOP|  
|WCF-BasicHttp|Communique avec des clients et services Web basés sur des fichiers ASMX, ainsi que d'autres services conformes à la norme WS-I Basic Profile 1.1 via HTTP ou HTTPS.|Non|Requête/réponse et sollicitation/réponse|Non|Oui|IIS OOP|  
|WCF-NetTcp|Prend en charge les normes WS-* via le transport TCP.|Oui|Requête/réponse et sollicitation/réponse|Non|Oui|BizTalk IP|  
|WCF-NetMsmq|Prend en charge la mise en file d'attente via le transport Microsoft Message Queuing (MSMQ).|Oui|Non|Oui|Oui|BizTalk IP|  
|WCF-NetNamedPipe|Fournit un transport rapide pour la communication interprocessus sur le même ordinateur (pour les applications WCF uniquement).|Oui|Requête/réponse et sollicitation/réponse|Non|Oui|BizTalk IP|  
|WCF-Custom|permet d'utiliser des fonctionnalités d'extensibilité WCF.|Oui.|Oui.|Oui, dès lors que la liaison prend en charge cette fonctionnalité.|Oui.|BizTalk IP|  
|WCF-CustomIsolated|permet d'utiliser des fonctionnalités d'extensibilité WCF sur le transport HTTP.|Oui.|Oui.|Non.|Oui.|IIS OOP|  
  
## <a name="line-of-business-adapters"></a>Adaptateurs sectoriels  
 La liste suivante répertorie les adaptateurs sectoriels fournis par Microsoft.  
  
|Adaptateur| Description|Versions prises en charge|  
|-------------|-----------------|------------------------|  
|PeopleSoft Enterprise|Permet l'échange de messages d'interface de composant entre BizTalk Server et un système PeopleSoft.|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards OneWorld XE|Permet l'échange de messages commerciaux entre BizTalk Server et un système JD Edwards OneWorld.|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards EnterpriseOne|Permet l'échange de messages commerciaux entre BizTalk Server et un système JD Edwards EnterpriseOne.|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Rendezvous|Permet l'échange de messages au format de données XML et binaires entre BizTalk Server et TIBCO Rendezvous.|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Enterprise Message Service|Permet l'échange de messages au format de données XML et binaires entre BizTalk Server et un serveur TIBCO EMS et fournit une infrastructure d'applications étroitement intégrée et fiable.|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
  
 Vous pouvez également utiliser les adaptateurs inclus dans [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour vous connecter à divers systèmes sectoriels. Pour plus d’informations sur [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez [http://go.microsoft.com/fwlink/p/?LinkID=188849](http://go.microsoft.com/fwlink/p/?LinkID=188849)  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques pour sécuriser les adaptateurs](../core/best-practices-for-securing-adapters.md)   
 [Création et suppression de gestionnaires d’adaptateur](../core/creating-and-deleting-adapter-handlers.md)   
 [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)