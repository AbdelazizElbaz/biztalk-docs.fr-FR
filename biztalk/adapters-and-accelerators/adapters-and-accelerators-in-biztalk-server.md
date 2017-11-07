---
title: "Adaptateurs et des accélérateurs dans BizTalk Server | Documents Microsoft"
description: "Vue d’ensemble de tous les adaptateurs et les accélérateurs dans BizTalk, y compris les adaptateurs intégrés, BAP, HL7, Swift, RosettaNet, FileAct et InterAct"
caps.latest.revision: "3"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7f26a1-e47b-4323-b9f0-58842c55a6f8
ms.author: mandia
ms.openlocfilehash: 30afb33621ed50af010c45edfb2643a24feaf91a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="adapters-and-accelerators-in-biztalk-server"></a>Adaptateurs et des accélérateurs dans BizTalk Server
 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]inclut différents adaptateurs et les accélérateurs vous permettant de créer des applications qui reçoivent des données et envoient des données à différents services et LOB systèmes. 
 
Cette section décrit les différents adaptateurs et les accélérateurs disponibles avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

## <a name="out-of-the-box-adapters"></a>Adaptateurs out of box
Lorsque vous installez BizTalk Server, vous installez également les adaptateurs intégrés qui sont prêtes à être utilisées. Certaines de ces cartes incluent le fichier, FTP, MQ Series, Service Bus, Logic Apps, POP3, SharePoint et bien plus encore.

**[À l’aide des adaptateurs](../core/using-adapters.md) répertorie tous les et vous montre également comment utiliser chaque adaptateur.**
 
## <a name="biztalk-adapter-pack"></a>Module adaptateur de BizTalk
Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] est inclus avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les adaptateurs WCF pour se connecter votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Oracle, SAP, Siebel et SQL Server. Vous pouvez également créer vos propres adaptateurs WCF à l’aide de la [!INCLUDE[afproductnameshort_md](../includes/afproductnameshort-md.md)]. 

**Consultez [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md) pour installer et configurer ces adaptateurs, parcourez les didacticiels et des scénarios, créer des applications en utilisant les différents adaptateurs et obtenir une bonne idée de comment basé sur WCF services traite les messages.**

## <a name="adapters-for-enterprise-applications"></a>Adaptateurs pour les Applications d’entreprise
Ces adaptateurs sont fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Utiliser ces adaptateurs pour connecter votre serveur BizTalk Server avec JD Edwards EnterpriseOne, JD Edwards OneWorld, PeopleSoft Enterprise, TIBCO Enterprise Message Service et TIBCO Rendezvous.

**Consultez [l’adaptateur BizTalk pour les Applications d’entreprise](biztalk-adapters-for-enterprise-applications.md) pour installer et configurer ces adaptateurs, parcourez les didacticiels et des scénarios, créer des applications avec les adaptateurs différents et bien plus encore.** 


## <a name="fileact-and-interact"></a>FileAct et interagir
Le [!INCLUDE[swift_adapter_md](../includes/swift-adapter-md.md)] sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et fournir la connectivité entre votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] et la société de télécommunication financières Interbank (SWIFT) dans le monde Secure IP réseau (SIPN). 

L’adaptateur FileAct fournit exchange sécurisée et fiable des fichiers et des informations relatives à ces fichiers. 

L’adaptateur InterAct fournit exchange sécurisée et fiable des messages financières structurés individuels. 

**Consultez [FileAct et InterAct](../adapters-and-accelerators/fileact-interact/microsoft-biztalk-server-fileact-and-interact-adapters-documentation.md) pour installer et configurer ces adaptateurs, parcourir des didacticiels et des scénarios et obtenir une bonne compréhension de l’architecture.** 

## <a name="hl7"></a>HL7

Le [!INCLUDE[btaBTAHL7NoNumber_md](../includes/btabtahl7nonumber-md.md)] est inclus avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et assure la connectivité entre votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] et applications de soins de santé ordinateur basées sur la norme sept de niveau d’intégrité (HL7).

**Consultez [HL7](../adapters-and-accelerators/accelerator-hl7/microsoft-biztalk-accelerator-for-hl7-documentation.md) pour installer et configurer l’adaptateur, parcourir plusieurs didacticiels et des scénarios, découvrez comment l’adaptateur fonctionne et utiliser les différentes fonctionnalités, y compris les schémas, accusés de réception, le traitement par lot, la validation et bien plus encore.**

## <a name="rosettanet"></a>RosettaNet
BizTalk Accelerator pour RosettaNet (BTARN) est fourni avec BizTalk Server et rationalise le développement et le déploiement de solutions d’intégration basée sur les normes RosettaNet. BTARN prend en charge l’infrastructure RNIF (RosettaNet Implementation) ; qui est une infrastructure d’application réseau ouverte qui permet à des partenaires commerciaux exécuter de façon collaborative RosettaNet PIP (PIP). 

**Consultez [RosettaNet](../adapters-and-accelerators/accelerator-rosettanet/microsoft-biztalk-accelerator-for-rosettanet-documentation.md) pour en savoir plus sur cet accélérateur et l’utiliser avec vos solutions BizTalk Server.** 

## <a name="swift"></a>SWIFT
Le [!INCLUDE[btaA4SWIFTNoVersion_md](../includes/btaa4swiftnoversion-md.md)] est inclus avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et assure la connectivité entre votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] et la société pour Worldwide Interbank financières télécommunication (SWIFT) de formats de message.

À l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], clients, partenaires et les intégrateurs système peuvent simplifier le développement, le déploiement et la prise en charge des solutions d’intégration pour les principaux services financiers infrastructure et vos processus d’application.

**Consultez [SWIFT](../adapters-and-accelerators/accelerator-swift/microsoft-biztalk-accelerator-for-swift-documentation.md) pour installer et configurer l’adaptateur, des didacticiels pas à pas et utiliser la réparation de message, réponse FIN et les artefacts FRR et bien plus encore.**

## <a name="get-some-help"></a>Obtenir de l’aide 
Obtenir de l’aide et aider les autres dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] forums [http://go.microsoft.com/fwlink/p/?LinkId=87695](http://go.microsoft.com/fwlink/p/?LinkId=87695).