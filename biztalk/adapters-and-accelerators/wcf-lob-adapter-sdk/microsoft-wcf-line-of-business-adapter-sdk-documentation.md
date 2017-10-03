---
title: "Documentation de Microsoft Windows Communication Foundation ligne d’entreprise Adapter SDK | Documents Microsoft"
description: "Des liens rapides vers installer prise en main, planifier et concevoir, développer et la résolution des problèmes WCF LOB Adapter SDK dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a2b098c-ef41-4cc0-8063-1fd043f1176f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8472fb56beab8f6d86ff33bebb9171d09d503ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-windows-communication-foundation-line-of-business-adapter-sdk-documentation"></a>Documentation de Microsoft Windows Communication Foundation ligne d’entreprise Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation inclut des ressources pour vous aider à développer, déployer et utiliser des cartes créées avec la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  

## <a name="about-the-sdk"></a>Sur le Kit de développement  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une collection d’un moteur d’exécution et outils qui permettent aux développeurs de carte créent orientée des interfaces à des systèmes métier existantes à l’aide de WCF. Le Kit de développement logiciel vise à faciliter le développement uniforme d’adaptateurs réutilisables orientés métadonnées, basé sur WCF qui permettent aux applications d’entreprise, bases de données et plateformes de messagerie d’intégrer les uns des autres.  
  
 Ce kit de développement basé sur WCF met en évidence un adaptateur à un système métier en tant qu’une liaison WCF. Pour un consommateur d’adaptateur, l’adaptateur est accessible comme un service WCF ; le consommateur n’a pas à apprendre un nouveau modèle de programmation. La même carte développée peut être réutilisée dans plusieurs applications .NET, y compris les applications .NET personnalisées, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], SharePoint et Microsoft SQL Server Integration Services (SSIS) via un shim ADO.NET adaptateur développeur – fourni. En outre, l’adaptateur fournit les métadonnées Parcourir, rechercher et fonctionnalité de récupération ; le consommateur de l’adaptateur peut générer de manière sélective les contrats WCF qui reflètent la modélisation de type dynamique du système LOB.  
 
## <a name="readme"></a>Fichier Lisezmoi
![Icône de ressources de communauté](../../adapters-and-accelerators/adapter-oracle-database/media/community.gif "Communauté") [Lisezmoi et la confidentialité](../../adapters-and-accelerators/wcf-lob-adapter-sdk/readme-and-privacy-in-the-wcf-lob-adapter-sdk.md) décrit les composants inclus dans le Kit de développement et également votre explique les options de confidentialité. 

## <a name="install"></a>Install
![Icône de mise en route](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [installer WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/install-the-wcf-lob-adapter-sdk.md) répertorie les étapes pour installer et désinstaller le SDK, supprimer des adaptateurs personnalisés et effectuer un installation sans assistance. 

## <a name="get-started"></a>Prise en main
![Icône de mise en route](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [prise en main l’avec WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md) inclut des informations utiles pour les utilisateurs qui découvrent le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], y compris la documentation conceptuelle et des didacticiels. 
  
## <a name="plan-and-design"></a>Planification et conception 
![Icône Architecture de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-database/media/4af6a1c5-948f-4bf7-bb56-4d63a47f4825.gif "4af6a1c5-948f-4bf7-bb56-4d63a47f4825") [planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md) décrit quand utiliser un adaptateur, un canal ou un service . Découvrez également les modèles de messagerie pris en charge, vous concevez un URI, compréhension des transactions et bien plus encore.

## <a name="develop-and-create"></a>Développer et créer
![Icône de développement d’adaptateurs](../../adapters-and-accelerators/adapter-oracle-database/media/44af70c9-cab1-4201-9912-d115cbc7e16f.gif "44af70c9-cab1-4201-9912-d115cbc7e16f") [développer ou créez votre adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/develop-or-create-your-adapter-using-the-wcf-lob-adapter-sdk.md) répertorie quelques-unes des meilleures pratiques, fournit des instructions sur le contrôle de version, l’authentification et bien plus encore.

## <a name="gac-and-deploy"></a>GAC et déployer
![Icône exemples d’adaptateurs](../../adapters-and-accelerators/adapter-sap/media/2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a.gif "2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a") après avoir créé votre adaptateur, l’étape suivante consiste à ajouter dans le GAC, mettre à jour le fichier machine.config et créer un package de déploiement. [Déploiement d’un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-adapter-using-the-wcf-lob-adapter-sdk.md) inclut ces informations.

## <a name="troubleshoot"></a>Dépanner
![Icône de résolution des problèmes de carte](../../adapters-and-accelerators/adapter-oracle-database/media/383a7392-2eb9-485d-b6a8-0187cd5c709d.gif "383a7392-2eb9-485d-b6a8-0187cd5c709d") [dépanner l’adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md) répertorie les étapes pour activer le traçage, utilisent compteurs de performance et génération WSDL.

