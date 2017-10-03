---
title: "Génération XML ou schéma dans PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- generating XML
- XML, generating
ms.assetid: adfe2936-0dc2-42d2-b26a-718f8cc57eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a7fbd164f7c0d380f6ee0c0fda59098203f7585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-xml-or-schema-in-peoplesoft"></a>Génération de code XML ou de schémas dans PeopleSoft
La procédure suivante explique comment utiliser PeopleSoft Enterprise pour créer un fichier XML et déclencher un événement PeopleSoft. Pour cela, vous devez modifier l'environnement PeopleSoft. La modification active un fichier XML qui est envoyé au dossier dont vous définissez dans votre orchestration qu'il doit être surveillé. Vous importez ensuite le fichier XML dans BizTalk Server et vous générez un schéma.  
  
> [!NOTE]
>  Lorsque vous associez l'emplacement au nœud MSEXTERNAL, tous les changements apportés à la valeur d'emplacement génèrent un document XML, ce qui déclenche un événement. Après avoir inscrit et démarré votre orchestration, vous pouvez parcourir les écrans PeopleSoft jusqu'à l'écran LOCATION. Si vous modifiez la valeur de l'emplacement et que vous enregistrez cette modification, un fichier XML correspondant s'affiche dans votre répertoire \out.  
  
### <a name="to-generate-xml-or-schema-in-peoplesoft"></a>Pour générer un fichier XML ou un schéma XSD dans PeopleSoft  
  
1.  Dans l’application PeopleSoft, pointez sur **configurer l’aspect financier**, pointez sur **chaîne logistique**, pointez sur **des définitions communes**, pointez sur **emplacement**, puis sélectionnez **emplacement**.  
  
2.  Sur le **emplacement** écran, entrez les informations suivantes :  
  
    -   **ID de l’ensemble :** entrez **partage**.  
  
    -   **Code de l’emplacement :** entrer un code qui commence par `WKLOC`.  
  
     ![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")  
  
3.  Cliquez sur **recherche**, puis cliquez sur **historique des corrections** à placer l’écran en **modifier** mode.  
  
     ![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")  
  
4.  Apportez une modification à un champ à l’écran, puis cliquez sur **enregistrer**.  
  
5.  Pointez sur **PeopleTools**, pointez sur **Integration Broker**, pointez sur **moniteur**, puis sélectionnez **surveiller le Message**.  
  
     ![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")  
  
6.  Assurez-vous que **Type de canal** est **Message d’Instance**, puis cliquez sur **Actualiser**.  
  
7.  Dans le **fait** colonne, cliquez sur le numéro.  
  
8.  Faites défiler vers le bas de la liste et cliquez sur le **détails** lien sur un **LOCATION_SYNC** message.  
  
     ![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")  
  
9. Cliquez sur **afficher XML** sur un **MSEXTERNAL** nœud.  
  
     ![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")  
  
     Copiez et collez le contenu du fichier XML dans un fichier accessible depuis votre projet BizTalk Server.  
  
     ![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")  
  
10. Mémorisez l'emplacement du fichier pour le référencer dans BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe b : à l’aide de l’Application PeopleSoft](../core/appendix-b-using-the-peoplesoft-application.md)