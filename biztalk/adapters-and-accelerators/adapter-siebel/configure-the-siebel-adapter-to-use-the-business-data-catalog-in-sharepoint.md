---
title: "Configurer l’adaptateur Siebel pour intégrer le système Siebel avec les données d’entreprise catalogue et SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49b575e8-5f33-4e6e-a914-95d357671ab5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d02e14b8c996acbfb07f9d422aee70cb0d94fa59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-siebel-adapter-to-integrate-the-siebel-system-with-the-business-data-catalog-and-sharepoint"></a>Configurer l’adaptateur Siebel pour intégrer le système Siebel avec les données d’entreprise catalogue et SharePoint
Le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], ce qui génère un service WCF pour les artefacts LOB. Ce service WCF est hébergé dans un environnement d’hébergement telles que Microsoft Internet Information Services (IIS). L’éditeur de définition de catalogue de données métier utilise l’URL où le service WCF est hébergé pour obtenir la Description langage WSDL (Web Services) pour le service WCF. À l’aide de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes disponibles pour le service WCF. Ces méthodes peuvent être utilisées pour établir des entités et l’association entre les entités.  
  
 L’éditeur de définition de catalogue de données métier permet de créer un fichier de définition d’application (fichier XML) qui consomment Microsoft Office SharePoint Server. Une fois que le fichier de définition d’application est importé dans Microsoft Office SharePoint Server, vous pouvez créer des composants WebPart pour présenter les informations à partir d’applications d’entreprise. Pour plus d’informations, consultez « Création de composants WebPart » dans [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) dans [didacticiel 1 : présentation sur un SharePoint Site de données à partir de système Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
## <a name="tutorial"></a>Didacticiel  
 Pour illustrer l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Microsoft Office SharePoint Server, le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] inclut un didacticiel qui fournit des instructions détaillées pour présenter les données à partir d’un système Siebel sur un site SharePoint. Consultez [didacticiel 1 : présentation des données à partir d’un système Siebel sur un Site SharePoint](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez l’adaptateur Siebel avec SharePoint](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)