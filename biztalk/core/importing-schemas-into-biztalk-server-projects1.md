---
title: "Importation de schémas dans BizTalk Server Projects1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing schemas
- orchestration variables, messages
- schemas, importing into BizTalk Server
- orchestration types, port types
ms.assetid: fa640195-a735-4201-a893-48f3405ddcb5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 719679dffa5bcffdeddcbcd889f847f147a705b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>Importation de schémas dans des projets BizTalk Server
Les informations suivantes décrivent l'importation des schémas dans un projet BizTalk Server.  
  
## <a name="importing-schemas"></a>Importation des schémas  
  
#### <a name="to-import-schemas"></a>Pour importer des schémas  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Cliquez sur **ajouter un adaptateur**, puis sélectionnez **ouvrir**.  
  
3.  Sélectionnez l’adaptateur**, J.D. Edwards OneWorld XE**.  
  
4.  Dans la liste déroulante, sélectionnez le port **SSOSendToJD Edwards OneWorld XE**, puis cliquez sur **suivant**.  
  
     Le myJ.D. Edwards OneWorld système logique apparaît dans le navigateur (ce système logique a été créé avec le SSOSendToJ.D. Port OneWorld XE Edwards).  
  
5.  Développez **myJ.D. Edwards OneWorld XESSO**.  
  
6.  Cliquez sur l’icône de flèche pour déplacer l’élément (ou faites simplement glisser) dans le **transmission** fenêtre, puis cliquez sur **OK**.  
  
     Les schémas sont ajoutés au projet SSOSchedule.  
  
7.  Dans l’Explorateur de solutions, développez **projet SSOSchedule**.  
  
8.  Avec le bouton droit **biztalkorchestration.odx**, puis cliquez sur **supprimer**.  
  
9. Dans l’Explorateur de solutions, double-cliquez sur **GetList.odx** pour examiner l’orchestration.  
  
## <a name="orchestration-types---port-types"></a>Types d'orchestration - Types de ports  
  
-   **PortTypeIn / / demande :** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeOut/Out/réponse :** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
-   **PortTypeInOut/InOut/demande :** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeInOut/InOut/réponse :** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## <a name="orchestration-variables---messages"></a>Variables d'orchestration - Messages  
  
-   **(Messagein) :** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **(Messageout) :** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)