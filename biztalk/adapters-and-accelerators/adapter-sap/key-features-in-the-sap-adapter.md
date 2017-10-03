---
title: "Les fonctionnalités de l’adaptateur SAP clés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, deprecated features
- features, technology-related
- adapters, new features
- features, deprecated
- features, metadata-related
- librfc32u.dll
- tRFC server
- features, new
- adapters, new and deprecated features
- queued tRFC client calls
- features, operations-related
- RFC server
ms.assetid: 30e3140c-447f-42ba-a3b0-13ae66e78b0c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b34a695e34f617f6444b728e92cb544f91448c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-features-in-the-sap-adapter"></a>Fonctionnalités clés de l’adaptateur SAP
Cette section répertorie les fonctionnalités nouvelles et déconseillées dans [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
> [!NOTE]
>  Cette rubrique a été utilisée à partir de la version précédente de [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] aide.  
  
## <a name="features-in-the-sap-adapter"></a>Fonctionnalités de l’adaptateur SAP  
 Voici les fonctionnalités introduites dans les versions précédentes de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="technology-related-features"></a>Fonctionnalités liées à la technologie  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|À l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SQL Server Reporting Services (SSRS).|Les programmes clients peuvent désormais utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] pour importer des données à partir d’un serveur principal SAP dans un projet SSRS et de générer des rapports de données. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SSRS, consultez [utiliser le fournisseur de données pour SAP avec SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md). Pour plus d’informations sur SSRS, consultez [SQL Server Reporting Services](https://msdn.microsoft.com/library/ms159106.aspx).|  
|Prise en charge pour appeler les requêtes définies dans un système SAP|Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose une opération, EXECQUERY, ce qui peut être utilisé pour exécuter des requêtes définies dans un système SAP. Pour plus d’informations sur la façon d’utiliser la fonctionnalité EXECQUERY, voir [prise en charge pour l’exécution des requêtes de SAP

] (https://msdn.microsoft.com/library/dd788118.aspx). |  
| Prise en charge pour l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft Office SharePoint Server (MOSS) | Vous pouvez utiliser les adaptateurs de présenter des données à partir du système SAP sur un portail MOSS. Pour plus d’informations, consultez [utiliser l’adaptateur SAP avec SharePoint](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md). |  
  
### <a name="metadata-related-features"></a>Fonctionnalités de métadonnées  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|**DataTypesBehavior** propriété de liaison|Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] fournit une propriété de liaison complexe, **DataTypesBehavior**, qui permet à l’adaptateur aux clients de contrôler le comportement de l’adaptateur lorsque des valeurs spéciales sont rencontrées dans le système SAP. Pour obtenir une explication détaillée sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).|  
  
### <a name="operations-related-features"></a>Liées aux opérations de fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge pour l’appel des programmes externes requis par une commande RFC|Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] fournit une propriété de liaison, **RfcAllowStartProgram** qui peut être définie pour activer la bibliothèque cliente RFC appeler des programmes externes, si elle existe, requis par un RFC particulier. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).|  
|Prise en charge pour l’envoi de plusieurs IDOC dans un seul appel|L’adaptateur SAP prend désormais en charge l’envoi IDOC plusieurs du même type dans un appel à une carte.|  
  
### <a name="other-features"></a>Autres fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Nouvelle façon d’utiliser l’adaptateur dans[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]|Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-SAP dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port WCF SAP, vous devez d’abord ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour plus d’informations, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).|  
  
## <a name="deprecated-features-in-the-sap-adapter"></a>Fonctionnalités déconseillées dans l’adaptateur SAP  
 Les sections suivantes répertorient les fonctionnalités qui ont été prises en charge dans la version précédente de l’adaptateur, mais qui ne sont pas pris en charge dans la version actuelle de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="enablebusinessobjects-binding-property-deprecated"></a>Propriété de liaison EnableBusinessObjects déconseillée  
 Cette propriété de liaison a été déconseillée dans [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Cette propriété de liaison a été utilisée pour déterminer si le nœud BAPI s’affichent lors de la génération de métadonnées lors de l’utilisation [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)