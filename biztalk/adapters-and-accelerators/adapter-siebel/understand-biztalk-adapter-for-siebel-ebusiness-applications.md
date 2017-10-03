---
title: "Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- features of Siebel adapters
- adapters, features
- adapter, overview
ms.assetid: 3249fb74-9ca1-4b81-971d-5151a2e354fe
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad8aecf0faa0a9a0117feaf91e5fa91203fa63f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-biztalk-adapter-for-siebel-ebusiness-applications"></a>Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications
Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet un accès par programmation orientée service pour pouvoir interagir avec un système externe. Les cartes présentent les avantages suivants aux clients :  
  
-   **Expérience de conception cohérente**. Les adaptateurs fournissent une phase de conception commune et convivial pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.  
  
-   **Diverses options de programmation**. Les adaptateurs fournissent un choix de modèle de programmation y compris Windows Communication Foundation (WCF) des services Web ADO.NET, modèle de service de modèle de canal, WCF ou BizTalk pris en charge les modèles.  
  
-   **Uniforme d’expérience sur LOB**. Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.  
  
 Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de Services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux de Windows Communication Foundation (WCF). Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. La documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \<lecteur d’installation > : \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
 Pour effectuer des opérations sur un système Siebel, les clients de l’adaptateur doivent avoir accès aux services d’entreprise exposée par le système Siebel. Une application Siebel expose des données en tant que composants d’entreprise et des objets métier. Un Siebel *composant d’entreprise* est une entité logique qui associe les colonnes à partir d’une ou plusieurs tables dans une structure unique. Un Siebel *objet métier* implémente un modèle d’entreprise à relier à un ensemble de composants d’entreprise reliés entre eux. Avec la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)], de surface de clients de l’adaptateur Siebel des objets métier et des composants d’entreprise.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] inclut également le [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]). Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fournit une interface ADO à un système Siebel en étendant les interfaces ADO.NET.  
  
 Cette section traite des fonctionnalités de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [Fonctionnalités clés de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [Limitations de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [Sur le fournisseur de données pour Siebel](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)