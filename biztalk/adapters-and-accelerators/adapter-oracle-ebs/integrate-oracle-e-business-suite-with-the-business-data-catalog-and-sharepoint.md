---
title: "Intégration d’Oracle E-Business Suite avec le catalogue de données métiers et SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 311f605d-78b4-41a0-b231-1a00a879f637
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ddcdc04c211d4b458c08730de097422d0735ee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="integrate-oracle-e-business-suite-with-the-business-data-catalog-and-sharepoint"></a>Intégration d’Oracle E-Business Suite avec le catalogue de données métiers et SharePoint
Le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], ce qui génère un service WCF pour les artefacts LOB. Ce service WCF est hébergé dans un environnement d’hébergement telles que Microsoft Internet Information Services (IIS). L’éditeur de définition de catalogue de données métier utilise l’URL où le service WCF est hébergé pour obtenir la Description langage WSDL (Web Services) pour le service WCF. À l’aide de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes disponibles pour le service WCF. Ces méthodes peuvent être utilisées pour établir des entités et l’association entre les entités.  
  
 L’éditeur de définition de catalogue de données métier permet de créer un fichier de définition d’application (fichier XML) qui consomment Microsoft Office SharePoint Server. Une fois que le fichier de définition d’application est importé dans Microsoft Office SharePoint Server, vous pouvez créer des composants WebPart pour présenter les informations à partir d’applications d’entreprise. Pour plus d’informations, consultez « Création de composants WebPart » à l’étape 3 : créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite dans [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
## <a name="tutorial"></a>Didacticiel  
 Pour illustrer l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec Microsoft Office SharePoint Server, le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] inclut un didacticiel qui fournit des instructions détaillées pour présenter des données à partir d’Oracle E-Business Suite sur un site SharePoint. Consultez [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
## <a name="see-also"></a>Voir aussi  
[Utilisez l’adaptateur Oracle E-Business Suite avec SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)