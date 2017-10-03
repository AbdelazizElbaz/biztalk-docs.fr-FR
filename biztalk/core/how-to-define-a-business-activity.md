---
title: "La définition d’une activité d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business activities, creating [Excel add-in]
- monitoring business activities [BAM], creating business activities [Excel add-in]
- monitoring business activities [BAM], Excel add-in
ms.assetid: 305e3718-46b4-45df-bd52-f7ae36621576
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74cb0bb6f2bd0a5f92f6029dda65d55d219bcc12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-a-business-activity"></a>Définition d'une activité d'entreprise
Pour indiquer les données à collecter pour les rapports, vous devez définir une activité BAM. Une activité BAM contient la liste des étapes majeures et des éléments de données sur lesquels portera le suivi effectué par l'analyse BAM. La procédure suivante explique comment créer une activité à l'aide du complément Excel BAM.  
  
> [!NOTE]
>  Une fois qu'une activité a été déployée, les actions que vous pouvez effectuer sur celle-ci sont restreintes. Par exemple, vous pouvez supprimer des éléments d'une activité mais dans ce cas, votre administrateur devra annuler le déploiement de tous les ensembles des activités et des vues BAM, puis les redéployer. Ceci peut causer une interruption de l'affichage et une perte de données si l'administrateur n'effectue pas de sauvegarde et de restauration des données.  
  
### <a name="to-create-a-business-activity"></a>Pour créer un activité d'entreprise  
  
1.  Ouvrez Microsoft Excel.  
  
2.  Dans la barre d’outils, cliquez sur le **BAM** élément de menu, puis cliquez sur **activité BAM**.  
  
     Le **entreprise Assistant activité BAM** s’affiche.  
  
3.  Cliquez sur **nouvelle activité**.  
  
     Le **nouvelle activité** boîte de dialogue s’affiche.  
  
4.  Tapez un nom descriptif pour l’activité dans le **nom de l’activité** zone de texte.  
  
> [!NOTE]
>  Une activité doit comporter au moins un élément d'activité.  
  
#### <a name="to-create-a-new-item"></a>Pour créer un élément  
  
1.  Cliquez sur **un nouvel élément**.  
  
2.  Dans le **nouvel élément d’activité** boîte de dialogue le **nouvel élément d’activité** , tapez un nom descriptif pour l’élément d’activité.  
  
3.  À partir de la **le type d’élément** menu déroulant, sélectionnez un type de cet élément. Les valeurs possibles sont :  
  
    |Type d’élément| Description|  
    |---------------|-----------------|  
    |Étape majeure commerciale|Valeur de date et heure. Par exemple, la date d'approbation d'un bon de commande.|  
    |Données d'entreprise - Texte|Chaîne de caractères alphanumériques. Par exemple, destinataire : code ville, Département/Province et Code Postal.|  
    |Données d'entreprise - Entier|Valeur de nombre entier. Par exemple, le nombre total d'achats.|  
    |Données d'entreprise - Décimal|Valeur décimale. Par exemple, le montant total en euros du bon de commande.|  
  
     Si vous sélectionnez l’élément de type « Données entreprise-texte », vous devez entrer le nombre maximal de caractères pour la chaîne dans le **longueur maximale** boîte.  
  
    > [!NOTE]
    >  Pour plus d'informations sur la création de ces éléments, voir la rubrique « Gestion des partenaires et analyse de l'activité d'entreprise » du didacticiel de Microsoft BizTalk Server.  
  
4.  Répétez les étapes 1 à 3 pour ajouter le nombre d'éléments nécessaires à cette activité.  
  
5.  Dès que l'exécution de l'Assistant Activité BAM est terminée, l'Assistant Vue BAM démarre automatiquement.  
  
 Pour plus d’informations sur l’utilisation de cet Assistant, consultez [définition d’une vue BAM](../core/defining-a-bam-view.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’une vue BAM](../core/defining-a-bam-view.md)   
 [Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md)