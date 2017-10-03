---
title: "Configurer l’adaptateur SAP pour intégrer SAP avec les données d’entreprise catalogue et SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ec105c9-0ced-4a45-bc0d-eb72c1ef5d9d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9de78148af79cc8668d01c220799187770c7df4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sap-adapter-to-integrate-sap-with-the-business-data-catalog-and-sharepoint"></a>Configurer l’adaptateur SAP pour intégrer SAP avec les données d’entreprise catalogue et SharePoint
Le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], ce qui génère un service WCF pour les artefacts LOB. Ce service WCF est hébergé dans un environnement d’hébergement telles que Microsoft Internet Information Services (IIS). L’éditeur de définition de catalogue de données métier utilise l’URL où le service WCF est hébergé pour obtenir la Description langage WSDL (Web Services) pour le service WCF. À l’aide de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes disponibles pour le service WCF. Ces méthodes peuvent être utilisées pour établir des entités et l’association entre les entités.  
  
 L’éditeur de définition de catalogue de données métier permet de créer un fichier de définition d’application (fichier XML) qui consomment Microsoft Office SharePoint Server. Une fois que le fichier de définition d’application est importé dans Microsoft Office SharePoint Server, vous pouvez créer des composants WebPart pour présenter les informations à partir d’applications d’entreprise. Pour plus d’informations, consultez « Création de composants WebPart » dans [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) dans [didacticiel 1 : présentation des données à partir d’un système SAP sur un SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).  
  
## <a name="tutorial"></a>Didacticiel  
 Pour illustrer l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft Office SharePoint Server, le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] inclut un didacticiel qui fournit des instructions détaillées pour présenter les données à partir d’un système SAP sur un site SharePoint. Consultez [didacticiel 1 : présentation des données à partir d’un système SAP sur un Site SharePoint](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).  
  
## <a name="see-also"></a>Voir aussi  
[Utilisez l’adaptateur SAP avec SharePoint](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)