---
title: Prise en charge des Types de colonnes Windows SharePoint Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], supported column types
- Windows SharePoint Services adapters, supported column types
ms.assetid: 14992f52-9d18-4321-9152-83c8a37751bc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5328c5dade3f02c480b58c36ff2cfdf9a5e7493
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="supported-windows-sharepoint-services-column-types"></a>Types de colonnes Windows SharePoint Services pris en charge
Cette rubrique décrit les types de colonnes Windows SharePoint Services pris en charge par l'adaptateur Windows SharePoint Services. Les valeurs de ces types de colonnes peuvent être définies dans le message.  
  
> [!NOTE]
>  Les colonnes calculées ne sont pas mises à jour par l'adaptateur.  
  
## <a name="supported-types"></a>Types pris en charge  
 Le tableau suivant répertorie les types de colonnes pris en charge :  
  
|Type d'IU|Type de modèle d'objet SharePoint|Exemple|Commentaires|  
|-------------|----------------------------------|------------|--------------|  
|Ligne de texte unique|SPFieldType.Text|ligne unique|Aucune|  
|Plusieurs lignes de texte|SPFieldType.Note|ligne 1<br /><br /> ligne 2<br /><br /> ligne 3|Aucune|  
|Liste déroulante de choix|SPFieldType.Choice|Choix_A|Choix_A parmi les choix disponibles (Choix_A, Choix_B et Choix_C)|  
|Cases d'option de choix|SPFieldType.Choice|#Choix_B;#Choix_C;#|Choix_B et Choix_C sont activés. Choix_A est désactivé (les choix disponibles étant Choix_A, Choix_B et Choix_C). Utilisez ;# comme séparateur.|  
|Number|SPFieldType.Number|123.456|Aucune|  
|Devise USD (ou autre)|SPFieldType.Currency|100.00|Aucune|  
|Lookup|SPFieldType.Lookup|1|Le nombre est l'identificateur d'élément dans la liste référencée.|  
|OuiNon|SPFieldType.Boolean|1|1=Oui<br /><br /> 0=Non|  
|Lien hypertexte ou image|SPFieldType.URL|http://www.microsoft.com, Site Web Microsoft|L'URL est séparée du texte affiché par le caractère « , ». Le texte « Site Web Microsoft » est un lien hypertexte pointant vers http://www.microsoft.com.|  
|Date et heure|SPFieldType.DateTime|2005-02-11T10:05:04|Date et heure telles que définies par la norme XML pour xs:dateTime. Basées sur le modèle SSAA-MM-JJThh:mm:ss où SS représente le siècle, AA l'année, MM le mois et JJ le jour, précédés par un caractère de début négatif (-) facultatif pour indiquer un nombre négatif. Si le caractère négatif est omis, les date/heure sont supposées positives (+). Le T représente le séparateur date/heure. hh, mm et ss représentent les heures, les minutes et les secondes respectivement. Cette représentation peut être immédiatement suivie d'un « Z » pour indiquer l'heure UTC ou le fuseau horaire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer Windows SharePoint Services emplacement de réception](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [Comment configurer un gestionnaire d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)   
 [Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Expressions de l’adaptateur de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md)