---
title: "Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e439e5bf-94b3-4582-bacc-b058e6eb8e17
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75aea1f23236d448f6efaa451d45663352fb3083
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-adapter-metadata-to-a-biztalk-project"></a>Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk
L'Assistant Ajouter les métadonnées de l'adaptateur vous permet d'ajouter des métadonnées d'adaptateur à un projet BizTalk. Ces données sont les schémas, types de messages et types de ports requis pour communiquer avec un adaptateur à partir d'une orchestration. Servez-vous de cet Assistant avec les adaptateurs d'applications, tels que FTP, pour intégrer les schémas correspondant à ces adaptateurs d'applications au système. Notez que les adaptateurs de transport tels que HTTP n'utilisent généralement pas de schémas.  
  
 La procédure ci-dessous présente les étapes requises pour ajouter des métadonnées pour un adaptateur.  
  
### <a name="to-add-adapter-metadata-to-a-biztalk-project"></a>Pour ajouter des métadonnées d'adaptateur à un projet BizTalk  
  
1.  Dans votre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés - \<**  *nom du projet*  **\>**  boîte de dialogue le **modèles** section, Sélectionnez **ajouter un adaptateur**, puis cliquez sur **ouvrir**.  
  
3.  Dans l’Assistant Ajout de métadonnées d’adaptateur, sur le **sélectionner un adaptateur** page, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Liste des adaptateurs|Sélectionner l'adaptateur inscrit à ajouter au projet. |  
    |SQL Server|Entrer le nom du serveur de base de données BizTalk.|  
    |Base de données|Affiche la liste des bases de données de gestion BizTalk pour le serveur sélectionné.|  
    |Port|Ce paramètre est facultatif. Afficher la liste des ports créés et enregistrés dans la base de données de gestion BizTalk. Seuls les ports configurés pour fonctionner avec l'adaptateur sélectionné sont affichés.|  
  
     Cliquez sur **Suivant**.  
  
    > [!NOTE]
    >  Vous essayez d’ajouter des schémas générés qui contiennent des caractères que le **System.XML.XMLConvert** classe ne prend pas en charge les résultats dans une erreur de compilation.  
  
4.  Si vous utilisez un adaptateur statique, sur le **sélectionner les Services à importer** page, sélectionnez un ensemble de services disponibles à partir de l’arborescence, puis cliquez sur **Terminer**.  
  
     - Ou -  
  
     Si vous utilisez un adaptateur dynamique, suivez la procédure de l'interface utilisateur personnalisée pour terminer l'Assistant.  
  
 Une fois la procédure terminée, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] affiche les fichiers .odx et .xsd dans l'Explorateur de solutions.