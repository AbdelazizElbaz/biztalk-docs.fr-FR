---
title: Commande AddResource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b09bd8d-5e07-4443-b626-60401a158540
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 875a087fa3afe7515aee2c406cbc47551bea1f4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="addresource-command"></a>Commande AddResource
Les rubriques de cette section contiennent des informations d'ordre technique relatives aux paramètres de la commande AddResource. Les paramètres que vous utilisez avec cette commande varient en fonction du type d’artefact que vous souhaitez ajouter. Pour obtenir la liste complète des types d’artefacts, utilisez la **ListTypes** de commande, comme décrit dans [commande ListTypes](../core/listtypes-command.md).  
  
 Pour obtenir de l'aide sur l'ajout d'un type d'artefact particulier, tapez la commande suivante :  
  
 **BTSTask AddResource /Type :**\<*nom de type* \> **/ ?**  
  
> [!NOTE]
>  Si l’objet que vous ajoutez possède un nom de chemin d’accès très long, y compris le nom de fichier, l’opération d’ajout de l’artefact à une application peut échouer. Un chemin d’accès ne peut pas dépasser 260 caractères.  
>   
>  Si une opération d'ajout échoue, toutes les actions lancées pendant cette opération sont annulées à l'exception de l'ajout des assemblys (ils ne sont pas supprimés du Global Assembly Cache s'ils ont été ajoutés par cette commande) et de l'entrée de données (elles ne sont pas supprimées du Registre Windows lorsqu'elles existent).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Commande AddResource : assembly BizTalk](../core/addresource-command-biztalk-assembly.md)  
  
-   [Commande AddResource : liaison BizTalk](../core/addresource-command-biztalk-binding.md)  
  
-   [Commande AddResource : assembly .NET](../core/addresource-command-net-assembly.md)  
  
-   [Commande AddResource : artefact BAM](../core/addresource-command-bam-artifact.md)  
  
-   [Commande AddResource : certificat](../core/addresource-command-certificate.md)  
  
-   [Commande AddResource : composant COM](../core/addresource-command-com-component.md)  
  
-   [Commande AddResource : fichier](../core/addresource-command-file.md)  
  
-   [Commande AddResource : script de prétraitement](../core/addresource-command-preprocessing-script.md)  
  
-   [Commande AddResource : script de post-traitement](../core/addresource-command-postprocessing-script.md)  
  
-   [Commande AddResource : stratégie](../core/addresource-command-policy.md)  
  
-   [Commande AddResource : répertoire virtuel](../core/addresource-command-virtual-directory.md)