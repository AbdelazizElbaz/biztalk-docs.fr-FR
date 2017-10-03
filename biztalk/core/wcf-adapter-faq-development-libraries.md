---
title: "FAQ sur les adaptateurs WCF : Les bibliothèques de développement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d05b635a-d46d-4f7d-896b-8ed7a799e80f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee15769d5b6fb41edece8e30702f14acf1992a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-development-libraries"></a>FAQ relatif à l'adaptateur WCF : bibliothèques de développement
## <a name="when-does-it-make-more-sense-to-use-the-wcf-adapters-vs-a-wcf-custom-binding-to-communicate-with-an-external-application-or-system"></a>Dans quelles circonstances l'utilisation des adaptateurs WCF plutôt que d'une liaison WCF personnalisée est-elle plus appropriée pour communiquer avec une application ou un système externe ?  
 Les adaptateurs WCF [!INCLUDE[prague](../includes/prague-md.md)] offrent deux nouvelles méthodes d'intégration d'un système externe avec BizTalk Server à l'aide de WCF.  
  
-   Vous pouvez écrire le code d'un client/service WCF et utiliser les adaptateurs WCF [!INCLUDE[prague](../includes/prague-md.md)] pour gérer la communication.  
  
-   Vous pouvez également développer une nouvelle liaison WCF personnalisée à l'aide de l'infrastructure WCF .NET et l'utiliser à la place de l'adaptateur WCF pour gérer la communication.  
  
 L'utilisation d'adaptateurs WCF avec BizTalk Server permet de développer un code de client WCF et d'appeler BizTalk Server en tant que service WCF distant, ou d'écrire un service WCF et de configurer BizTalk Server pour l'exposer en tant que service WCF. Vous pouvez également écrire l'intégralité d'une nouvelle liaison WCF personnalisée pour gérer la communication.  
  
 L'avantage d'écrire un code de service ou de client WCF standard et d'utiliser les adaptateurs [!INCLUDE[prague](../includes/prague-md.md)] standard plutôt que d'écrire une liaison WCF personnalisée est que cette dernière est plus difficile à développer. Le client ou le service WCF qui en résulte existe en dehors de l'univers de gestion (surveillance, configuration et déploiement) de BizTalk Server. L'avantage d'écrire votre propre liaison personnalisée et de l'héberger à l'aide d'un adaptateur WCF BizTalk personnalisé est que cette liaison peut être étroitement intégrée à ces fonctions de gestion de BizTalk Server. Le coût de développement d'une liaison en termes de prise en charge de l'infrastructure est bien plus élevé que celui du développement d'un service.  
  
 Il est important de comprendre que les deux méthodes offrent l'opportunité d'intégrer la base de données BizTalk MessageBox interne de façon transactionnelle, avec des performances similaires. Ce qui différencie ces deux méthodes, c’est leur niveau de complexité.  
  
 Lors de l'utilisation de WCF, vous devez d'abord tenter d'écrire un service et un client personnalisés, puis utiliser les adaptateurs WCF BizTalk standard pour les connecter. Les bibliothèques .NET Framework et WCF sont spécialement conçues pour faciliter cette tâche. Pour créer le service WCF, développez votre interface personnalisée, définissez les attributs appropriés, puis implémentez le code du contrat. WCF s'occupe de l'intégralité du processus, des métadonnées à la sérialisation des objets. Une fois le service WCF écrit, vous pouvez configurer en quelques étapes un adaptateur WCF via un port d'envoi pour communiquer avec le service. Vous pouvez même configurer les transactions afin que le nouveau service puisse participer à un échange transactionnel de messages avec la base de données BizTalk MessageBox interne.  
  
 Côté réception, vous pouvez configurer BizTalk Server afin qu'un emplacement de réception soit identique à un service WCF sur le réseau. Cette opération permet d'écrire un code de client WCF standard, et donc d'utiliser les transactions lorsque vous appelez ce service. Le fait d'utiliser un adaptateur BizTalk WCF standard en tant que passerelle configurable directement du client WCF vers le code de service WCF simplifie le développement. Un adaptateur WCF fournit une passerelle transactionnelle performante vers BizTalk Server à partir de l'environnement des services WCF.  
  
 En résumé, pour communiquer avec un système externe, vous pouvez écrire un service WCF pour interagir avec celui-ci, puis écrire un code pour communiquer avec le service WCF. Une méthode plus complexe consiste à écrire une nouvelle liaison personnalisée et à intégrer [!INCLUDE[prague](../includes/prague-md.md)] à l'aide de l'un des adaptateurs WCF personnalisés. Cette méthode est plus stricte que l'utilisation du service WCF. L'écriture d'une nouvelle liaison personnalisée est un exercice de développement plus précis et plus complexe. Cette méthode a l'avantage de garantir une solution étroitement intégrée où le développement, la configuration et l'administration de BizTalk Server s'effectuent uniformément. Si les fonctionnalités de l'adaptateur sont développées en tant que service et client WCF externes, la configuration doit être externe à l'environnement BizTalk Server, sans prise en charge de l'infrastructure associée.  
  
## <a name="what-are-the-differences-between-the-wcf-adapters-and-the-adapters-in-the-biztalk-adapter-pack"></a>Quelles sont les différences entre les adaptateurs WCF et ceux du pack d'adaptateurs BizTalk ?  
 Les adaptateurs WCF sont les sept adaptateurs livrés avec la version [!INCLUDE[prague](../includes/prague-md.md)] :  
  
-   WCF-Custom  
  
-   WCF-CustomIsolated  
  
-   WCF-NetTcp  
  
-   WCF-BasicHttp  
  
-   WCF-WsHttp  
  
-   WCF-NetNamedPipe  
  
-   WCF-NetMsmq  
  
 Le [BizTalk Adapter Pack](http://www.microsoft.com/biztalk/en/us/adapter-pack.aspx) est une version post-BizTalk Server qui fournit une solution unique pour connecter facilement et en toute sécurité les données de métier (LOB) à partir de toutes les applications .NET personnalisées, entreprise basé sur SQL Server solution d’analyse décisionnelle, ou une Application d’entreprise Office (OBA). Les trois adaptateurs disponibles dans cette version sont Siebel, SAP et Oracle DB La licence du Pack d'adaptateurs est incluse dans les éditions Entreprise, Développeur et Standard de [!INCLUDE[prague](../includes/prague-md.md)], mais ne l'est pas dans l'Édition Agence. Les utilisateurs qui ont déjà acheté [!INCLUDE[prague](../includes/prague-md.md)] avec Software Assurance peuvent également accéder au Pack d'adaptateurs BizTalk.  
  
## <a name="what-is-the-recommended-order-for-deciding-to-use-the-biztalk-server-adapter-framework-the-wcf-lob-adapter-sdk-or-the-net-framework"></a>Quel est le meilleur choix parmi l’infrastructure d’adaptateurs BizTalk Server, le Kit de développement logiciel de l’adaptateur WCF LOB et .NET Framework ?  
 L'utilisation de l'infrastructure d'adaptateurs BizTalk est déconseillée car elle n'est pas basée sur un WCF .NET standard. Dans la mesure où, d'un point de vue stratégique, votre solution doit inclure WCF, quelle est la meilleure façon de procéder ? L'option la plus simple consiste à écrire un client et un service WCF, puis à utiliser un adaptateur WCF pour les associer. Si le programme est externe à BizTalk Server, vous pouvez ensuite écrire une liaison WCF personnalisée avec .NET Framework.  
  
 Vous ne devez choisir le Kit de développement logiciel de l'adaptateur LOB WCF que si vous tentez de résoudre un problème d'intégration LOB essentiellement lié aux métadonnées. Le Kit de développement logiciel de l'adaptateur LOB WCF permet également de créer une liaison WCF, notamment pour la prise en charge des métadonnées. Ces métadonnées sont nécessaires par exemple lorsque le système avec lequel vous communiquez ne possède pas de type de document fixe. BizTalk Server envoie ou reçoit des documents XML et les métadonnées décrivent la disposition des données dans le document, afin que le système cible puisse les utiliser.  
  
## <a name="what-are-the-differences-between-the-biztalk-adapter-framework-and-the-wcf-lob-adapter-sdk"></a>Quelles sont les différences entre l'infrastructure d'adaptateurs BizTalk et le Kit de développement logiciel de l'adaptateur WCF LOB ?  
 L'infrastructure d'adaptateurs BizTalk permet de créer des adaptateurs WCF personnalisés lorsqu'aucun des sept adaptateurs WCF standard n'est conforme aux exigences en matière de communication. L'infrastructure d'adaptateurs fournit une prise en charge enrichie des métadonnées pour prendre en charge les applications LOB, et partage les mêmes méthodes de configuration et de gestion standard que les adaptateurs WCF standard.  
  
 Le Kit de développement logiciel de l'adaptateur LOB WCF permet d'écrire une liaison personnalisée pour un système cible avec d'importants besoins liés aux métadonnées. L'objectif du Kit de développement logiciel de l'adaptateur LOB WCF est de faciliter le développement uniforme d'adaptateurs WCF réutilisables orientés métadonnées, qui permettent aux applications et aux bases de données de l'entreprise de s'intégrer mutuellement. Comme l'utilisation du Kit de développement logiciel de l'adaptateur LOB WCF génère une liaison WCF, la même solution développée peut être réutilisée dans plusieurs applications .NET, y compris les applications .NET personnalisées, [!INCLUDE[prague](../includes/prague-md.md)], Microsoft Office SharePoint® Server et Microsoft SQL Server Integration Services. De plus, le Kit de développement logiciel de l'adaptateur LOB WCF fournit un modèle objet de métadonnées commun pour exposer les métadonnées du système cible, afin que les utilisateurs de l'adaptateur puissent rechercher, atteindre et récupérer les contrats WCF à partir de l'adaptateur. Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).  
  
 Si l'infrastructure d'adaptateurs BizTalk et le Kit de développement logiciel de l'adaptateur WCF LOB ont pour point commun de faciliter le développement des adaptateurs personnalisés, ils ont également des différences :  
  
-   Le Kit de développement logiciel de l'adaptateur WCF LOB est une version plus récente, basée sur les classes .NET Framework 3.0. À l'instar de l'infrastructure d'adaptateurs BizTalk antérieure, il fournit de nombreuses fonctionnalités enrichies liées au traitement des métadonnées et à la gestion de la connexion ; cependant, l'adaptateur qui en résulte n'est pas lié à l'architecture BizTalk Server.  
  
-   Un adaptateur écrit à l'aide du Kit de développement logiciel de l'adaptateur WCF LOB est exposé en tant que liaison personnalisée, et peut donc être appelé par chaque application WCF cliente. Il peut également être étendu en tant que canal WCF. Un adaptateur écrit à l'aide de l'infrastructure d'adaptateurs BizTalk peut uniquement être appelé par BizTalk Server.  
  
 Il n'existe aucune prise en charge explicite d'outil de développement pour l'infrastructure d'adaptateurs BizTalk. Pour le Kit de développement logiciel de l'adaptateur WCF LOB, l'Assistant Génération du code de l'adaptateur vous guide dans la procédure de collecte des informations requises pour l'utilisation de l'adaptateur personnalisé, puis génère les fichiers dont vous aurez besoin pour votre projet d'adaptateur personnalisé.