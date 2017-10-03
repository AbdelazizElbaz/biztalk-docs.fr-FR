---
title: "Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MOSS, creating an application in
- Microsoft Office SharePoint Server
- MOSS
- Microsoft Office SharePoint Server, creating an application in
ms.assetid: 6e31c365-446c-4fe1-8538-fa6c869eed63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdc3ea5e41600aebcef1fda933735c418dec78c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site"></a>Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint
Ce didacticiel fournit des instructions détaillées sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft Office SharePoint Server pour présenter les données d’entreprise à partir d’un système SAP sur un portail SharePoint. Pour illustrer l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Office SharePoint Server, vous devez prendre en compte les deux entités courantes dans toute entreprise : clients et les commandes. Dans cet exemple, une application est créée dans Office SharePoint Server, qui utilise le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour effectuer les opérations suivantes :  
  
-   Récupérer une liste de clients à partir du système SAP basé sur une chaîne de recherche.  
  
-   Sélectionnez un client à partir de la liste et détails présentes pour le client.  
  
-   Récupérer les commandes pour le client sélectionné.  
  
 Pour extraire les données client à partir d’un système SAP, l’exemple utilise le document RFC SD_RFC_CUSTOMER_GET. Pour extraire des informations sur les commandes client pour un client spécifique, il utilise le document RFC BAPI_SALESORDER_GETLIST.  
  
> [!NOTE]
>  Certaines versions du système SAP exposent un RFC RFC_CUSTOMER_GET au lieu de SD_RFC_CUSTOMER_GET.  
  
> [!NOTE]
>  Avant de poursuivre le didacticiel, assurez-vous que vous avez installé tous les composants requis pour l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Office SharePoint Server. Pour plus d’informations sur la configuration requise, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation, généralement installé sur C:/Program Files/Microsoft  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] /Documents.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Publier les artefacts SAP comme Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)  
  
-   [Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)  
  
-   [Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)  
  
-   [Étape 4 : Tester votre Application SharePoint](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)