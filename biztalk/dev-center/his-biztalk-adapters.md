---
title: Les adaptateurs BizTalk inclus dans Host Integration Server | Documents Microsoft
description: "Vue d’ensemble des adaptateurs BizTalk pour héberger des Applications, fichiers de l’ordinateur hôte, DB2 et WebSphere MQ inclus avec son"
author: MandiOhlinger
manager: anneta
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mandia
ms.openlocfilehash: 26f2bf48c9a1268aace041776ff3895c8f3b3aa5
ms.sourcegitcommit: 75d35f6f230f0846c29a4b146c6d5b074e60b13c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="biztalk-adapters-for-host-systems"></a>Adaptateurs BizTalk pour les systèmes hôtes


## <a name="biztalk-adapter-for-host-applications"></a>Adaptateur BizTalk pour héberger des Applications

L’adaptateur Microsoft BizTalk pour héberger des Applications est conçu pour BizTalk Server. Il est basé sur la technologie de Microsoft Transaction Integrator (TI) pour le traitement de Windows-Initiated, ce qui permet un accès efficace au macroordinateur IBM zSeries existant (CICS et IMS) ou des programmes de serveur iSeries (RPG) de milieu de gamme. 

Les outils de conception TI sont intégrés à Visual Studio et des solutions BizTalk Server, permettant aux développeurs d’informatique être hautement productif lorsque vous définissez le proxy client et la création du schéma XSD. Pour les administrateurs de BizTalk Server, le gestionnaire TI existant, le composant logiciel enfichable Microsoft Management Console (MMC), a été amélioré pour améliorer la prise en charge et de prendre en charge les scénarios de déploiement de solutions de BizTalk Server à distance requis.

Consultez [l’adaptateur BizTalk pour héberger des Applications](https://msdn.microsoft.com/library/dn148497(BTS.80).aspx). 

## <a name="biztalk-adapter-for-host-files"></a>Adaptateur BizTalk pour fichiers hôtes
L’adaptateur Microsoft BizTalk pour les fichiers de l’hôte est un adaptateur de données avancée qui permet aux organisations informatiques d’accéder et d’intégrer les informations stockées dans les systèmes de fichiers hôtes, y compris zSeries fichiers VSAM de macroordinateur datasets et de milieu de gamme iSeries physiques. 

Outils de conception Visual Studio permettent de définir un mappage de métadonnées des fichiers de programme décrit hôte, qui est ensuite exporté au format XSD pour une utilisation avec l’adaptateur BizTalk au sein d’une solution BizTalk Server. La configuration d’Assistants sont intégrées dans les outils d’administration de BizTalk Server, ce qui permet aux professionnels informatiques définir statiques et ports d’envoi dynamiques et de sollicitation-réponse des ports, basés sur un ensemble de commandes SQL (SELECT, INSERT, UPDATE, DELETE simplifié de réception ). 

L’adaptateur BizTalk est basé sur le fournisseur de données Microsoft .NET Framework pour les fichiers d’hôte qui mappe SQL vers des membres et des jeux de données non relationnelles hôte. Cela facilite non programmeurs lire et écrire des sources de données de fichier hôte.

Consultez [l’adaptateur BizTalk pour fichiers hôtes](https://msdn.microsoft.com/library/dn150042(BTS.80).aspx).

## <a name="biztalk-adapter-for-db2"></a>Adaptateur BizTalk pour DB2
L’adaptateur Microsoft BizTalk pour DB2 est une carte de base de données relationnelle qui permet aux informaticiens accéder aux données vitales stockées dans les serveurs de base de données IBM DB2 sur l’hôte distant informatique plates-formes, IBM mainframe zSeries et iSeries de milieu de gamme (DB2/400) et IBM DB2 Universal Database (UDB) sur les plateformes ouverts. 

À l’aide des commandes SQL standard et un Assistant de configuration intégrée à des outils d’administration de BizTalk Server, les professionnels de l’informatique peuvent créer des solutions qui lisent et écrivent dans DB2 sans recourir à de programmation de base de données. Ports de réception de l’adaptateur DB2, qui est basé sur le fournisseur de données Microsoft .NET Framework pour DB2 et prend en charge un large éventail de fonctions, y compris les ports d’envoi dynamique et statique avec sollicitation-réponse.

Consultez [l’adaptateur BizTalk pour DB2](https://msdn.microsoft.com/library/dn150160(BTS.80).aspx).

## <a name="biztalk-adapter-for-websphere-mq"></a>Adaptateur BizTalk pour WebSphere MQ
L’adaptateur Microsoft BizTalk pour WebSphere MQ (basé sur le Client) utilise le Client IBM WebSphere MQ (Base-Client) et IBM WebSphere MQ étendue transactionnelle (Extended-Client) d’API Client pour communiquer avec les gestionnaires de file d’attente MQSeries à distance. L’adaptateur permet à BizTalk Server de communiquer directement avec les gestionnaires de file d’attente MQSeries déployés sur les systèmes d’exploitation non Windows, sans avoir à déployer et gérer WebSphere MQ pour Windows Server, pour échanger des messages avec line-of-business efficacement applications de l’entreprise. 

Lorsqu’il est utilisé avec le Client de Base, l’adaptateur permet le traitement des messages non transactionnels, ce qui garantit seulement la remise de messages. Il incombe à l’application sur l’extrémité de réception pour traiter les messages en double. Lorsqu’il est utilisé avec le Client de l’étendue, l’adaptateur fournit pour garantir qu’une seule fois et-uniquement-une fois la remise de messages de traitement des messages transactionnels.

Consultez [l’adaptateur BizTalk pour WebSphere MQ](https://msdn.microsoft.com/library/dn191830(BTS.80).aspx).
