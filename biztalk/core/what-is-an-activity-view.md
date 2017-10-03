---
title: "Qu'est-ce qu'une vue d'activité ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], Activity view [Tracking Profile Editor]
- activities [BAM], definitions
- Tracking Profile Editor, Activity view
- Activity view [Tracking Profile Editor]
ms.assetid: ae6bcdc8-e426-4148-b83d-08a1a5e99ca3
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fd27a4de6b2ac86f94b105aabe679df3c88c06d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-activity-view"></a>Qu'est-ce qu'une vue d'activité ?
Une vue d'activité contient la définition d'activité BAM importée que vous créez avec le complément BAM pour Excel. La définition d'activité BAM constitue un résumé des besoins en suivi qui sont les vôtres concernant votre processus d'entreprise. Une activité peut s'étendre sur plusieurs orchestrations et ports. Vous devez importer une fois la définition d'activité et la mapper à chaque artefact d'orchestration ou de messagerie qui correspond à une partie quelconque de la définition.  
  
 Le lien de vue d'activité figure dans le volet gauche de l'interface utilisateur de l'Éditeur de modèle de suivi.  
  
## <a name="activity-view-elements"></a>Éléments de vue d'activité  
 La vue d'activité affiche la structure globale du modèle de suivi dans une arborescence et inclut les éléments suivants :  
  
-   Milestones  
  
-   Éléments de données pour l'activité  
  
-   Sources d'événement  
  
-   Sources de données  
  
 **Étapes majeures**: étapes majeures sont des objets qui définissent un point dans un processus donné. On peut y accéder de trois manières différentes :  
  
-   Vous pouvez faire glisser une forme depuis une planification d'orchestration et l'heure de fin de l'exécution de cette forme est signalée par l'analyse BAM comme la valeur d'étape majeure.  
  
-   Vous pouvez faire glisser une propriété de messagerie d'une représentation schématique sur la droite vers une étape majeure cible.  
  
-   Vous pouvez faire glisser un nœud de schéma de charge de message qui contient une valeur d'étape majeure.  
  
    > [!NOTE]
    >  Les nœuds de schéma de type DATETIME ONLY sont évalués au moment de l'exécution. En cas de problème de conversion au moment de l'exécution, une erreur de suivi est consignée dans le journal des événements.  
  
 **Éléments de données**: éléments de données sont des objets qui définissent un élément particulier à partir d’un schéma XML pour une instance de message, un système ou une propriété promue. Pour accéder à un élément de données, vous devez développer le schéma et localiser et sélectionner l'élément qui vous intéresse, puis faire glisser ce dernier vers le dossier de type d'élément de données approprié. Des informations relatives aux éléments de données (XPath par exemple) sont stockées dans le profil.  
  
> [!NOTE]
>  L'Éditeur de modèle de suivi ne prend en charge que les éléments de donnée qui possèdent une représentation zéro-à-un tel que cela est défini dans le schéma de message d'un champ de données particulier. Des erreurs peuvent se produire dans le suivi d'orchestration en cas d'éléments de données ayant des représentations un-à-plusieurs. Aucune donnée n'est alors stockée dans la base de données d'importation principale BAM. Si aucune erreur ne se produit, il ne peut y avoir aucune garantie quant à l'élément de données qui est suivi.  
  
> [!NOTE]
>  Les développeurs BAM doivent être conscients du fait que les propriétés sont renseignées conformément aux règles de processus de BizTalk Server et non conformément à l'analyse BAM.  
>   
>  Dans l'adaptateur SMTP par exemple, les propriétés de contexte telles que SMTPServer, CC et From ne contiennent aucune valeur tant qu'elles ne sont pas explicitement renseignées. Une fois qu'elles sont renseignées, leurs valeurs apparaissent dans la base de données d'importation principale BAM et sont disponibles pour le suivi.  
  
## <a name="activity-view-context-menus"></a>Menus contextuels de vue d'activité  
 Les menus contextuels des actions disponibles pour la vue d'activité varient dynamiquement selon le nœud sélectionné dans la Vue Orchestration. Par exemple, si vous sélectionnez un nœud de dossier d'activité, le menu contextuel contiendra les éléments de menu contextuel correspondant à ce dossier.  
  
 Pour associer des événements et des données aux éléments dans l'activité d'entreprise, vous devez les faire glisser du volet d'événement source à droite vers le nœud d'événement ou de données de la vue d'activité.  
  
 Pour accéder aux menus contextuels des nœuds dans la vue d'activité, il suffit de cliquer avec le bouton droit sur les nœuds dans l'arborescence. La capture d'écran suivante affiche le nœud racine de vues d'activité. Les tableaux suivants répertorient les éléments des menus contextuels correspondant aux différents nœuds d'une vue d'activité.  
  
 **Nœud de racine d’arborescence de la définition activité**  
  
 ![](../core/media/activityviewcontextmenu.gif "activityviewcontextmenu")  
  
|Élément de menu|Utilisation|  
|---------------|-----------|  
|Nouvelle Continuation|Insère un nouveau dossier Continuation dans l'arborescence d'activité. Vous mappez la valeur de ce dossier à partir du segment source d’une continuation.<br /><br /> Utilisé avec un dossier ContinuationID pour fournir un moyen de transférer le traitement vers plusieurs composants renseignant la même activité. Parmi ces composants on peut par exemple trouver des orchestrations BizTalk, des ports, des BufferedEventStreams et des DirectEventStreams. **Remarque :** les noms de dossier Continuation peuvent contenir un maximum de 127 caractères.|  
|Nouveau ContinuationID|Insère un dossier ContinuationID dans l'arborescence d'activité. Vous mappez ce dossier à un segment de prolongement d'une continuation. Par exemple, si l'orchestration A se prolonge vers l'orchestration B, ce dossier doit être mappé à un élément issu de l'orchestration B.<br /><br /> Utilisé avec un dossier Continuation pour fournir un moyen de transférer le traitement vers plusieurs composants renseignant la même activité. Parmi ces composants on peut par exemple trouver des orchestrations BizTalk, des ports, des BufferedEventStreams et des DirectEventStreams. **Remarque :** les noms des dossiers ContinuationID peuvent contenir un maximum de 127 caractères.|  
|Nouvelle relation|Insère un nouveau dossier Relationship dans l'arborescence d'activité. Utilisé pour publier la relation entre les activités qui forment une vue. **Remarque :** noms des dossiers Relationship peuvent contenir un maximum de 128 caractères. Ils incluent notamment le nom du serveur et le nom de la base de données de gestion BizTalk.|  
|Nouvelle Document Reference URL|Insère un nouveau dossier Document Reference URL dans l'arborescence d'activité. Utilisé pour définir une URL de référence à un emplacement qui contient un document associé à cette activité. **Remarque :** les noms de dossier Document Reference URL peuvent contenir un maximum de 128 caractères.|  
  
 **Nœud de propriété**  
  
|Élément de menu|Utilisation|  
|---------------|-----------|  
|Associer aux données sélectionnées|Utilisé pour créer une association entre une charge de message ou un élément de données de propriété de contexte et le dossier d'élément de données d'activité BAM.|  
  
 **Nœud d’événement**  
  
|Élément de menu|Utilisation|  
|---------------|-----------|  
|Associer à la fin de l'action sélectionnée|Utilisé pour créer une association entre une forme d’orchestration, charge de message DateTime ou élément de données de propriété de contexte DateTime et le dossier étape majeure d’activité BAM.|  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md)   
 [Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md)   
 [Composants de l’éditeur](../core/components-of-the-tpe.md)